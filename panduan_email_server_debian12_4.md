# KONFIGURASI DNS + MAIL SERVER + WEBMAIL
## Khusus Debian 12 (Bookworm) — VMware

```
=================================================
INFORMASI SERVER
DOMAIN      : maulahn.net
MAIL SERVER : mail.maulahn.net
IP SERVER   : 11.11.11.1/24
OS          : Debian 12 (Bookworm)

INTERFACE   :
  ens33     → Bridge (Internet / akses keluar)
  ens34     → Host-only / Custom VMnet (DNS & Mail Server)
=================================================
```

---

## ⚠️ PENTING SEBELUM MULAI — SETTING VMWARE

VM Debian ini menggunakan **dua Network Adapter**:

| Adapter | Mode VMware | Interface | Fungsi |
|---|---|---|---|
| Network Adapter 1 | **Bridged** | `ens33` | Akses internet (dapat IP dari router/DHCP) |
| Network Adapter 2 | **Host-only** atau **Custom VMnet** | `ens34` | Jaringan internal (IP statis `11.11.11.1`) |

Agar Windows bisa mengakses webmail dan DNS server:
- PC Windows juga harus terhubung ke **VMnet yang sama** dengan `ens34`
- Di VMware Workstation: Edit → Virtual Network Editor → pastikan VMnet untuk ens34 ada dan Windows pakai adapter di VMnet yang sama
- Set IP Windows di VMnet itu ke subnet `11.11.11.x` (misal: `11.11.11.2`)

---

## PRE-REQUISITE — KONFIGURASI DUA INTERFACE DI DEBIAN 12

Jalankan semua perintah sebagai **root**.

```bash
# Cek nama interface yang aktif
ip a
# Pastikan ens33 dan ens34 keduanya muncul
```

```bash
nano /etc/network/interfaces
```

Ubah isinya menjadi:

```
source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

# ens33 - Bridge - dapat IP otomatis dari internet/router
auto ens33
iface ens33 inet dhcp

# ens34 - Host-only - IP statis untuk DNS & Mail Server
auto ens34
iface ens34 inet static
    address 11.11.11.1
    netmask 255.255.255.0
```

> ℹ️ `ens34` tidak perlu gateway karena hanya untuk jaringan lokal internal VMware.

```bash
systemctl restart networking
ip a
# Pastikan ens33 dapat IP dari DHCP dan ens34 punya IP 11.11.11.1
```

---

## STEP 1 — INSTALL DNS SERVER (BIND9)

```bash
apt update && apt upgrade -y
apt install bind9 bind9utils dnsutils -y
```

Edit file zona:

```bash
nano /etc/bind/named.conf.local
```

Tambahkan di baris **paling bawah**:

```
zone "maulahn.net" {
    type master;
    file "/etc/bind/db.maulahn";
};

zone "11.11.11.in-addr.arpa" {
    type master;
    file "/etc/bind/db.11";
};
```

---

## STEP 2 — KONFIGURASI FORWARD ZONE

```bash
cp /etc/bind/db.local /etc/bind/db.maulahn
nano /etc/bind/db.maulahn
```

**Hapus semua isi lama**, ganti seluruhnya dengan:

```
$TTL    604800
@       IN      SOA     ns.maulahn.net. root.maulahn.net. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.maulahn.net.
@       IN      A       11.11.11.1
ns      IN      A       11.11.11.1
mail    IN      A       11.11.11.1
@       IN      MX      10 mail.maulahn.net.
```

---

## STEP 3 — KONFIGURASI REVERSE ZONE

```bash
cp /etc/bind/db.127 /etc/bind/db.11
nano /etc/bind/db.11
```

**Hapus semua isi lama**, ganti seluruhnya dengan:

```
$TTL    604800
@       IN      SOA     ns.maulahn.net. root.maulahn.net. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.maulahn.net.
1       IN      PTR     mail.maulahn.net.
```

Validasi dan restart BIND9:

```bash
named-checkconf
named-checkzone maulahn.net /etc/bind/db.maulahn
named-checkzone 11.11.11.in-addr.arpa /etc/bind/db.11
systemctl restart bind9
systemctl status bind9
```

> ✅ Tidak boleh ada error. Jika ada, periksa kembali isi file zone (titik dan spasi sangat sensitif).

---

## STEP 4 — SET DNS LOKAL DI SERVER DEBIAN 12

> ⚠️ **Masalah dengan dua interface:** Karena `ens33` menggunakan DHCP,
> setiap kali `dhclient` memperbarui IP, file `/etc/resolv.conf` bisa
> **tertimpa otomatis** dan nameserver `127.0.0.1` hilang.
> Gunakan cara berikut agar pengaturan DNS tetap permanen.

```bash
nano /etc/resolv.conf
```

Hapus semua isi lama, ganti dengan:

```
nameserver 127.0.0.1
```

Kunci file agar tidak bisa ditimpa oleh DHCP:

```bash
chattr +i /etc/resolv.conf
```

> ℹ️ `chattr +i` membuat file menjadi **immutable** (tidak bisa diubah siapapun,
> termasuk DHCP client). Jika suatu saat perlu mengedit lagi, jalankan
> `chattr -i /etc/resolv.conf` untuk membuka kuncinya.

Test DNS:

```bash
nslookup mail.maulahn.net
nslookup maulahn.net
ping -c 3 mail.maulahn.net
```

> ✅ Kedua `nslookup` harus mengembalikan IP `11.11.11.1`.

---

## STEP 5 — INSTALL MAIL SERVER (POSTFIX + DOVECOT)

```bash
apt install postfix dovecot-imapd dovecot-pop3d -y
```

Saat dialog muncul:

| Pertanyaan | Jawaban |
|---|---|
| General type of mail configuration | **Internet Site** |
| System mail name | **mail.maulahn.net** |

---

## STEP 6 — KONFIGURASI POSTFIX

```bash
nano /etc/postfix/main.cf
```

Cari baris yang sudah ada dan **sesuaikan nilainya**, atau tambahkan jika belum ada.
Pastikan baris-baris berikut ada dan benar:

```
myhostname = mail.maulahn.net
mydomain = maulahn.net
myorigin = /etc/mailname
inet_interfaces = all
inet_protocols = ipv4
mydestination = mail.maulahn.net, maulahn.net, localhost.localdomain, localhost

# WAJIB: Format Maildir agar kompatibel dengan Dovecot
home_mailbox = Maildir/

# SMTP Authentication via Dovecot SASL
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, defer_unauth_destination
```

> ⚠️ Jika baris `smtpd_recipient_restrictions` sudah ada di file, hapus atau komentari (`#`)
> agar tidak konflik dengan `smtpd_relay_restrictions`.

```bash
systemctl restart postfix
systemctl status postfix
```

---

## STEP 7 — KONFIGURASI DOVECOT

### 7a. Lokasi mailbox (harus cocok dengan Postfix)

```bash
nano /etc/dovecot/conf.d/10-mail.conf
```

Cari semua baris yang mengandung `mail_location`. Di Debian 12, file ini berisi
**beberapa baris `mail_location`** — sebagian dikomentari, sebagian tidak.
Dovecot akan menggunakan baris yang **paling bawah dan tidak dikomentari**.

Pastikan kondisi akhirnya seperti ini:

```
# Baris ini aktifkan (hapus # jika ada):
mail_location = maildir:~/Maildir

# Baris ini nonaktifkan (tambahkan # di depan):
#mail_location = mbox:~/mail:INBOX=/var/mail/%u
```

> ⚠️ Jika ada dua baris `mail_location` yang aktif (tanpa #), yang paling bawah
> yang dipakai. Pastikan hanya `maildir:~/Maildir` yang aktif, sisanya dikomentari.

### 7b. Izinkan plaintext authentication (untuk lab/testing lokal)

```bash
nano /etc/dovecot/conf.d/10-auth.conf
```

Cari dan ubah dua baris berikut:

```
# Ubah dari yes ke no:
disable_plaintext_auth = no

# Pastikan mengandung plain dan login:
auth_mechanisms = plain login
```

### 7c. Aktifkan SASL socket untuk Postfix

```bash
nano /etc/dovecot/conf.d/10-master.conf
```

Di dalam file, cari bagian ini (sudah ada tapi dikomentari):

```
  # Postfix smtp-auth
  #unix_listener /var/spool/postfix/private/auth {
  #  mode = 0666
  #}
```

**Hapus tanda `#` dan tambahkan `user` dan `group`**, sehingga menjadi:

```
  # Postfix smtp-auth
  unix_listener /var/spool/postfix/private/auth {
    mode = 0666
    user = postfix
    group = postfix
  }
```

> ⚠️ Jangan membuat blok `service auth {}` baru. Blok ini sudah ada di dalam file,
> cukup **uncomment** dan edit bagian Postfix smtp-auth yang ada.

```bash
systemctl restart dovecot
systemctl status dovecot
```

---

## STEP 8 — BUAT USER EMAIL

```bash
adduser user1
adduser user2
```

Saat ditanya password, ketik `1` lalu Enter (atau password apapun yang kamu mau).
Pertanyaan lain (Full Name, dll.) cukup tekan Enter.

Jika ingin set password secara otomatis tanpa prompt:

```bash
echo "user1:1" | chpasswd
echo "user2:1" | chpasswd
```

---

## STEP 9 — TEST SMTP — KIRIM EMAIL VIA TELNET

```bash
apt install telnet -y
telnet mail.maulahn.net 25
```

Ketik perintah berikut **satu per satu**, tekan Enter setiap baris:

```
HELO maulahn.net
MAIL FROM:user2@maulahn.net
RCPT TO:user1@maulahn.net
DATA
Subject: Test Email Pertama

Halo ini pesan test dari user2 kepada user1.
.
QUIT
```

> ✅ Setiap perintah harus dibalas kode `250 Ok`.
> Kode `354` muncul setelah `DATA` — itu normal, artinya siap menerima isi pesan.

---

## STEP 10 — TEST POP3 — CEK EMAIL VIA TELNET

```bash
telnet mail.maulahn.net 110
```

```
user user1
pass 1
list
retr 1
quit
```

> ✅ `list` menampilkan daftar email. `retr 1` menampilkan isi email pertama.
> Jika `list` kosong, berarti email dari Step 9 belum terkirim — cek `tail -f /var/log/mail.log`.

---

## STEP 11 — INSTALL WEBMAIL (APACHE + MARIADB + ROUNDCUBE)

```bash
apt install mariadb-server apache2 roundcube roundcube-mysql -y
```

Saat installer bertanya:

| Pertanyaan | Jawaban |
|---|---|
| Configure database for roundcube with dbconfig-common? | **Yes** |
| MySQL application password for roundcube | ketik `123` lalu Enter |

---

## STEP 12 — KONFIGURASI APACHE UNTUK ROUNDCUBE

> ℹ️ **Perhatian Debian 12:** Saat roundcube diinstall, Debian otomatis membuat
> `/etc/apache2/conf-available/roundcube.conf` yang membuat roundcube hanya bisa
> diakses di path `/roundcube`. Kita perlu **menonaktifkannya** agar VirtualHost
> kita yang aktif.

```bash
# Nonaktifkan conf bawaan roundcube dari Debian
a2disconf roundcube

# Buat VirtualHost baru
cd /etc/apache2/sites-available
nano roundcube.conf
```

Isi file `roundcube.conf` dengan:

```apache
<VirtualHost *:80>
    ServerName mail.maulahn.net
    ServerAdmin webmaster@maulahn.net
    DocumentRoot /usr/share/roundcube

    <Directory /usr/share/roundcube>
        Options +FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/roundcube_error.log
    CustomLog ${APACHE_LOG_DIR}/roundcube_access.log combined
</VirtualHost>
```

Aktifkan konfigurasi:

```bash
a2ensite roundcube.conf
a2dissite 000-default.conf
a2enmod rewrite
systemctl reload apache2
systemctl status apache2
```

---

## STEP 13 — KONFIGURASI ROUNDCUBE

> ⚠️ **Perhatian Roundcube 1.6 (Debian 12):**
> Roundcube 1.6 sudah tidak menggunakan `smtp_server` dan `smtp_port` (deprecated).
> Gantinya menggunakan `smtp_host` dengan format `host:port`.
> Selain itu, Debian 12 otomatis mengisi `smtp_host = 'localhost:587'` di config bawaan —
> ini **harus diubah** ke port 25 karena Postfix kita hanya listen di port 25.

```bash
nano /etc/roundcube/config.inc.php
```

### Langkah 13a — Perbaiki smtp_host bawaan Debian

Cari baris ini di dalam file (sudah ada, bawaan Debian):

```php
$config['smtp_host'] = 'localhost:587';
```

Ubah **port 587 menjadi 25**:

```php
$config['smtp_host'] = 'localhost:25';
```

### Langkah 13b — Tambahkan config di bagian paling bawah file

```php
// SMTP Authentication (gunakan credentials login user)
$config['smtp_user'] = '%u';
$config['smtp_pass'] = '%p';

// Perbaiki "From" agar tampil @maulahn.net bukan @localhost
$config['mail_domain'] = 'maulahn.net';

// Tampilan
$config['product_name'] = 'Webmail Maulahn';
$config['timezone'] = 'Asia/Jakarta';
```

> ℹ️ Untuk `imap_host` dan `default_port`, Roundcube 1.6 di Debian 12 sudah
> mengisi nilai defaultnya (`localhost:143`) secara otomatis — tidak perlu ditambahkan lagi.

Verifikasi config SMTP sudah benar:

```bash
grep -E "smtp_host|smtp_user|smtp_pass|mail_domain" /etc/roundcube/config.inc.php
```

Output yang diharapkan:

```
$config['smtp_host'] = 'localhost:25';   ← pastikan port 25, bukan 587
$config['smtp_user'] = '%u';
$config['smtp_pass'] = '%p';
$config['mail_domain'] = 'maulahn.net';
```

```bash
systemctl restart apache2
```

---

## STEP 14 — RESTART SEMUA SERVICE (URUTAN PENTING)

```bash
systemctl restart bind9
systemctl restart dovecot
systemctl restart postfix
systemctl restart apache2
```

Verifikasi semua berjalan:

```bash
systemctl is-active bind9 dovecot postfix apache2
```

> ✅ Semua harus menampilkan `active`.

---

## STEP 15 — KONFIGURASI DI KOMPUTER WINDOWS

Karena server menggunakan `ens34` (Host-only) untuk jaringan DNS/mail,
**PC Windows harus terhubung ke VMnet yang sama dengan ens34**.

### Langkah 1 — Set IP Windows di VMnet yang sama

1. Buka **Control Panel** → Network and Sharing Center
2. Klik adapter yang terhubung ke VMnet Host-only (biasanya bernama **VMware Network Adapter VMnetX**)
3. Pilih **IPv4** → **Properties**
4. Set IP statis:
   - **IP Address:** `11.11.11.2`
   - **Subnet Mask:** `255.255.255.0`
   - **Default Gateway:** *(kosongkan)*
   - **Preferred DNS:** `11.11.11.1`
5. Klik **OK**

### Langkah 2 — Test koneksi dari Windows ke Server

Buka **Command Prompt** di Windows:

```
ping 11.11.11.1
nslookup mail.maulahn.net 11.11.11.1
```

> ✅ Kedua perintah harus berhasil sebelum membuka browser.

### Langkah 3 — Jika tidak mau set IP statis (alternatif cepat)

Edit file HOSTS Windows sebagai Administrator:

1. Buka Notepad as **Administrator**
2. File → Open → `C:\Windows\System32\drivers\etc\hosts`
3. Tambahkan di paling bawah:
   ```
   11.11.11.1   maulahn.net
   11.11.11.1   mail.maulahn.net
   ```
4. Simpan

---

## STEP 16 — UJI AKSES WEBMAIL

Buka browser di Windows:

```
http://mail.maulahn.net
```

Login:
- **Username:** `user1`
- **Password:** `1`

> ✅ Jika berhasil, tampil halaman login Roundcube.
> Setelah login, inbox harus menampilkan email test yang dikirim di Step 9.

Uji kirim email di Roundcube:
- Compose → To: `user2@maulahn.net` → kirim
- Login sebagai `user2`, cek inbox

---

## RINGKASAN ALUR KONFIGURASI

```
[BIND9 DNS]          → Resolve nama mail.maulahn.net ke 11.11.11.1
     ↓
[Postfix SMTP :25]   → Terima dan kirim email, format Maildir
     ↓
[Dovecot IMAP :143]  → Baca email dari ~/Maildir
[Dovecot POP3 :110]  → Ambil email dari ~/Maildir
     ↓
[Roundcube + Apache] → Webmail di http://mail.maulahn.net
     ↓
[Postfix SASL ←→ Dovecot auth] → Autentikasi kirim email via webmail
```

---

## TROUBLESHOOTING

```bash
# Log Postfix & mail (jika rsyslog terinstall)
tail -f /var/log/mail.log

# Jika /var/log/mail.log tidak ada, gunakan journald:
journalctl -u postfix -n 30 -f

# Log Apache Roundcube
tail -f /var/log/apache2/roundcube_error.log
tail -f /var/log/apache2/error.log

# Log Dovecot
journalctl -u dovecot -n 30

# Log BIND9
journalctl -u bind9 -n 30
```

| Gejala | Penyebab | Solusi |
|---|---|---|
| `ping mail.maulahn.net` gagal | DNS tidak aktif atau resolv.conf tertimpa DHCP | Cek `cat /etc/resolv.conf`, pastikan ada `nameserver 127.0.0.1`, jalankan `chattr +i /etc/resolv.conf` |
| `ip a` tidak tampilkan `ens34` | Interface belum aktif | `ifup ens34` atau `systemctl restart networking` |
| Windows tidak bisa ping `11.11.11.1` | Windows tidak terhubung ke VMnet yang sama dengan ens34 | Set IP Windows ke `11.11.11.2/24` di adapter VMnet yang tepat |
| Telnet port 25 ditolak | Postfix tidak jalan | `systemctl restart postfix` |
| Inbox Roundcube kosong padahal email sudah terkirim | `mail_location` di Dovecot masih mbox bukan maildir | Edit `10-mail.conf`: aktifkan `mail_location = maildir:~/Maildir`, nonaktifkan baris mbox, restart dovecot |
| `retr 1` kosong / error login POP3 | `disable_plaintext_auth = yes` atau `mail_location` salah | Edit `10-auth.conf` dan `10-mail.conf`, restart dovecot |
| Email tidak masuk Maildir | `home_mailbox` belum diset di Postfix | Tambahkan `home_mailbox = Maildir/` di `main.cf`, restart postfix |
| **Roundcube "SMTP Error: Connection to server failed"** | `smtp_host` masih pakai port 587 bawaan Debian | Edit `config.inc.php`: ubah `smtp_host` dari `localhost:587` ke `localhost:25`, restart apache2 |
| Roundcube kirim email tapi "From" tampil `user@localhost` | `mail_domain` belum diset | Tambahkan `$config['mail_domain'] = 'maulahn.net';` di `config.inc.php` |
| Browser tidak bisa buka URL | DNS atau koneksi VMnet salah | Lakukan Step 15 dari awal |
| Apache tampilkan halaman default | Site belum diaktifkan | `a2ensite roundcube.conf && a2dissite 000-default.conf && systemctl reload apache2` |
| Roundcube hanya bisa diakses di `/roundcube` | Conf bawaan Debian belum dimatikan | `a2disconf roundcube && systemctl reload apache2` |
| `/var/log/mail.log` tidak ditemukan | rsyslog tidak terinstall | `apt install rsyslog -y && systemctl restart rsyslog` |

---

## RINGKASAN PORT

| Service | Port | Protokol | Keterangan |
|---|---|---|---|
| DNS | 53 | UDP/TCP | Resolusi nama domain |
| SMTP | 25 | TCP | Kirim/terima email |
| POP3 | 110 | TCP | Ambil email (telnet test) |
| IMAP | 143 | TCP | Roundcube baca email |
| HTTP | 80 | TCP | Akses webmail |
