# Soal Ujian ITS Networking (IT101) — Form B

> [!IMPORTANT]
> **35 soal** berhasil diekstrak dari `272-1463-ENU-INF-101-ENU--Form-B.res`.
> Form B merupakan variasi soal dari Form A untuk ujian ITS Networking (IT101).

---

## Domain 1: Networking Fundamentals

### Q1 — Network Types
**Soal:** Your company's computers exchange data through a set of routed private Wi-Fi networks at a single geographic location. What type of network is this an example of?

**Jawaban:** WLAN / LAN (Local Area Network / Wireless Local Area Network)

---

### Q2 — Internet of Things (IoT) (True/False)
**Soal:** For each statement about the Internet of Things (IoT), select **True** or **False**.

| # | Statement | Jawaban |
|---|-----------|---------|
| 1 | IoT devices have IP addresses. | ✅ **True** |
| 2 | IoT devices require human interaction to communicate with a network. | ❌ **False** |
| 3 | A smart thermostat and a lightbulb that can be switched on by using an app are examples of IoT devices. | ✅ **True** |

**Penjelasan:** IoT devices memiliki IP address, dapat berkomunikasi tanpa interaksi manusia, dan contohnya adalah smart thermostat/lightbulb (walaupun di solusi ada catatan membingungkan tentang smartphone, opsi ini biasanya True).

---

### Q3 — Virtualization & Hypervisor (True/False)
**Soal:** For each statement about using a Type 2 hypervisor and virtual machines, select **True** or **False**.

| # | Statement | Jawaban |
|---|-----------|---------|
| 1 | If you reboot one virtual machine, all the other virtual machines on the server reboot at the same time. | ❌ **False** |
| 2 | You can reboot the host machine without it having any effect on the other virtual machines on the same physical server. | ❌ **False** |
| 3 | If you need to reboot one virtual machine, you must first reboot the physical server. | ❌ **False** |

**Penjelasan:** Guest VM independen satu sama lain (reboot satu VM tidak mempengaruhi yang lain). Namun, reboot Host OS akan men-suspend atau mematikan semua Guest VM.

---

### Q4 — Cloud Migration
**Soal:** CompanyPro plans to migrate all of their servers to the cloud. Which **two** administrative responsibilities will be eliminated? (Choose 2.)

**Penjelasan:** Sama dengan Form A. Migrasi ke cloud menghilangkan tanggung jawab atas hardware fisik dan keamanan fisik fasilitas.
**Objective:** 1.2 Define cloud and virtualization concepts
**Ref:** https://docs.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility

---

### Q5 — Extending Internal Networks
**Soal:** Which technology can you use to extend an internal network across shared or public networks?

**Jawaban:** VPN (Virtual Private Network)

---

### Q6 — VPN Purpose
**Soal:** What does a VPN provide?

**Jawaban:** Koneksi aman/terenkripsi (secure connection) melalui jaringan publik (internet).

---

### Q7 — VPN Terms (Match)
**Soal:** Move each VPN term to the correct definition.

| Definition | VPN Type |
|------------|----------|
| Allows a remote user to connect to a private network from anywhere on the internet | **Remote-Access VPN** |
| Securely connects two portions of a private network or two private networks | **Site-to-Site VPN** |
| Creates an unencrypted connection between two network devices | **GRE Tunnel** |

---

### Q8 — Protecting Internal Network
**Soal:** You are helping a friend set up a public-facing web server in their home office. Your friend wants to protect the internal network from intrusion. What should you do?

**Jawaban:** Membangun Perimeter Network / DMZ (Demilitarized Zone).

---

### Q9 — VPN True/False
**Soal:** Remote users need to connect to your network through a server running Windows Server that is deployed on your perimeter network. For each statement, select **True** or **False**.

| # | Statement | Jawaban |
|---|-----------|---------|
| 1 | You can use a VPN to enable users to make a secure connection to your network through the Internet. | ✅ **True** |
| 2 | If users connect to the Internet through dial-up connections, the server must also connect through a dial-up connection. | ❌ **False** |
| 3 | You can use RAS Gateway to configure a VPN connection for Windows 10 clients that is active whenever the client connects to the Internet. | ✅ **True** |

---

### Q10 — Broadest Area Network
**Soal:** Which type of network covers the broadest area?

**Jawaban:** WAN (Wide Area Network)

---

### Q11 — LAN to WAN Connection
**Soal:** Which hardware is required to properly connect a LAN to a WAN?

**Jawaban:** Router
**Objective:** 2.2 Define the characteristics of wide area networks
**Ref:** https://www.open.edu/openlearncreate/mod/oucontent/view.php?id=130530&printable=1

---

### Q12 — Wireless Authentication
**Soal:** Which wireless authentication method provides the highest level of security involving an authentication server?

**Jawaban:** WPA2/WPA3 Enterprise (biasanya menggunakan 802.1X/RADIUS server).
**Ref:** https://www.techtarget.com/searchnetworking/feature/Wireless-encryption-basics-Understanding-WEP-WPA-and-WPA2

---

### Q13 — Weak Wireless Encryption
**Soal:** Which wireless encryption type is the most susceptible to interception and decryption?

**Jawaban:** WEP (Wired Equivalent Privacy)
**Objective:** 2.3 Understand media types

---

## Domain 2: Network Infrastructure

### Q14 — Internet Network Topology
**Soal:** Which network topology is the internet designed around?

**Jawaban:** Mesh topology

---

### Q15 — Multilayer Switch Feature
**Soal:** In addition to switching, which feature is specific to a multilayer switch?

**Jawaban:** Routing (Layer 3 switching)

---

### Q16 — Switch Behavior (True/False)
**Soal:** For each statement about switches, select **True** or **False**.

| # | Statement | Jawaban |
|---|-----------|---------|
| 1 | A switch sends unicast frames to only one destination port. | ✅ **True** |
| 2 | A switch floods ports if it does not know where to send a frame. | ✅ **True** |
| 3 | A switch sends broadcast frames to only the uplink port. | ❌ **False** |

---

### Q17 — Workgroup Network Device
**Soal:** Which network device interconnects computers in a workgroup, can be remotely configured, and provides the best throughput?

**Jawaban:** Managed Switch

---

### Q18 — Dynamic Routing Advantage
**Soal:** What is an advantage of dynamic routing?

**Jawaban:** Fault tolerance / kemampuan beradaptasi otomatis terhadap perubahan topologi.

---

### Q19 — Fault Tolerant Routing
**Soal:** Which routing option is fault tolerant?

**Jawaban:** Dynamic routing
**Objective:** 2.2 Understand routers
**Ref:** http://technet.microsoft.com/en-us/library/cc957844.aspx

---

### Q20 — Cable for Manufacturing Floor
**Soal:** You need to run four Ethernet network drops on your company's manufacturing floor. Each drop is approximately 125 feet/38 meters. Each drop passes near heavy manufacturing equipment. You need to ensure that interference is reduced. Which cable type should you use?

**Jawaban:** STP (Shielded Twisted Pair) atau Fiber Optic

---

### Q21 — Long Distance Cable
**Soal:** You need to install a network cable between two locations that are approximately six miles/ten kilometers from each other. Which cable should you use?

**Jawaban:** Single-mode Fiber Optic

---

## Domain 3: Network Protocols & Services

### Q22 — IP Address Types (Match)
**Soal:** Move the appropriate address types to the correct ranges.

| Range | Address Type |
|-------|-------------|
| 127.0.0.0 – 127.255.255.255 | **Loopback** |
| 192.168.0.0 – 192.168.255.255 | **Private** |
| 224.0.0.0 – 239.255.255.255 | **Multicast** |

---

### Q23 — Transport Layer Protocol
**Soal:** Which protocol operates at the transport layer of the TCP model?

**Jawaban:** TCP atau UDP

---

### Q24 — IPv4 Address Composition
**Soal:** What does each IPv4 address consist of?

**Jawaban:** Network ID dan Host ID (atau 32 bits, terbagi dalam 4 octet).

---

### Q25 — Port Numbers (Match)
**Soal:** Move the appropriate TCP port numbers to the correct services.

| Port | Service |
|------|---------|
| 21 | **FTP** |
| 25 | **SMTP** |
| 443 | **HTTPS** |

---

### Q26 — Teredo Tunneling
**Soal:** What is a feature of the Teredo tunneling protocol?

**Jawaban:** Memungkinkan paket IPv6 untuk ditransmisikan melalui jaringan IPv4, bahkan saat berada di belakang perangkat NAT.

---

### Q27 — Ping Protocol
**Soal:** Which protocol does the ping utility use to test communication with a remote host?

**Jawaban:** ICMP (Internet Control Message Protocol)

---

### Q28 — Top-Level Domain
**Soal:** What is the top-level domain of ftp.sunsetweb.org?

**Jawaban:** .org

---

### Q29 — Internal to Internet Config
**Soal:** You need to configure a router to enable internal clients with private IPv4 addresses to access the internet and navigate to multiple websites. What should you configure?

**Jawaban:** NAT (Network Address Translation) atau lebih spesifik PAT (Port Address Translation).

---

## Domain 5: Network Troubleshooting

### Q30 — Cable Testing Tool
**Soal:** Which network hardware tool should you use to determine whether a UTP cable is capable of 1000Mbps full-duplex transmission?

**Jawaban:** Cable Certifier / Network Cable Tester
**Objective:** 5.2 Use appropriate hardware troubleshooting tools
**Ref:** https://www.computerhope.com/jargon/c/cabletest.htm

---

### Q31 — Isolating Cable in Bundle
**Soal:** You need to know where the jack is plugged into the patch panel. However, there are no labels. In the main distribution frame (MDF), you discover a bundle of 35 cables. Which tool should you use to isolate the correct cable?

**Jawaban:** Tone generator and probe (Toner probe / Fox and Hound).
**Objective:** 5.2 Use appropriate hardware troubleshooting tools
**Ref:** https://www.techwalla.com/articles/how-to-use-a-cable-toner

---

### Q32 — Firewall Listening Ports
**Soal:** You are setting up a network computer game. You need to open up ports on your firewall so your friends can join the network. Which command displays the ports that your computer is listening for?

**Jawaban:** `netstat -a` atau `netstat -an`

---

### Q33 — Linux Network Connections
**Soal:** In Linux, which command-line tool should you use to list a host's active incoming connections?

**Jawaban:** **netstat**

| Option | Keterangan |
|--------|------------|
| netstat | ✅ **Benar** — digunakan untuk informasi koneksi jaringan |
| dig | ❌ Salah — untuk DNS queries |
| host | ❌ Salah — untuk DNS lookups |
| ip addr | ❌ Salah — untuk informasi alamat IP, bukan koneksi |

**Ref:** https://technet.microsoft.com/en-us/library/bb490947.aspx

---

### Q34 — IP Configuration Analysis (Dropdown)
**Soal:** Refer to the image. Complete the statements about IP address configuration.

Pilihan:
- The IP address of the wireless adapter is configured ____ (manually/by DHCP)
- The IP address of the Ethernet adapter is configured ____ (manually/by DHCP)

---

### Q35 — Traceroute Analysis (Dropdown)
**Soal:** Refer to the scenario and image. Complete the statements about traceroute.

Pilihan:
- Each hop in the trace route is a ____
- The trace route completed ____

---

> [!WARNING]
> File ini berisi soal ujian sertifikasi Certiport yang dilindungi hak cipta. Konten ini diekstrak untuk keperluan analisis teknis saja.
