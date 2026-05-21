# Soal Ujian ITS Networking (IT101) — Gabungan (Form A & B)

> [!IMPORTANT]
> **63 soal unik** berhasil digabungkan dari Form A dan Form B.
> Soal yang sama persis telah dihapus secara otomatis.

### Q1 — Client-Server Networks (True/False)
**Soal:** For each statement about client-server networks, select **True** or **False**.

| # | Statement | Jawaban |
|---|-----------|---------|
| 1 | A client-server network has centralized administration. | ✅ **True** |
| 2 | A client-server network requires each computer to share its resources. | ❌ **False** |
| 3 | A client-server network requires users to have a user account on every computer they need to use. | ❌ **False** |

**Penjelasan:** Statement 2 & 3 adalah karakteristik peer-to-peer networks, bukan client-server networks.
**Objective:** 1.1 Define Network Concepts

---

---

### Q2 — Network Types
**Soal:** A financial institution operates multiple branches across different states. Each branch uses its own local switching infrastructure, but financial records are accessed through encrypted links over service-provider networks. Which type of network best describes the connectivity between the branches?

**Jawaban:** WAN (Wide Area Network)
**Objective:** IT101-1.1-04
**Ref:** https://www.extratechs.com.au/blog/lan-vs-wan-vs-can-vs-pan-vs-wlan

---

---

### Q3 — Hypervisors (True/False)
**Soal:** For each statement about hypervisors, select **True** or **False**.

| # | Statement | Jawaban |
|---|-----------|---------|
| 1 | A Type 1 hypervisor runs directly on system hardware. | ✅ **True** |
| 2 | A Type 2 hypervisor runs directly on system hardware. | ❌ **False** |
| 3 | A Type 1 hypervisor is also known as a bare-metal hypervisor. | ✅ **True** |

**Penjelasan:** Type-1 (bare-metal) hypervisor berjalan langsung di hardware host. Type-2 (hosted) berjalan di atas OS konvensional.
**Ref:** https://en.wikipedia.org/wiki/Hypervisor

---

---

### Q4 — Cloud Migration
**Soal:** CompanyPro plans to migrate all of their servers to the cloud. Which **two** administrative responsibilities will be eliminated? (Choose 2.)

**Penjelasan:** Migrasi ke cloud menghilangkan tanggung jawab hardware fisik (server maintenance, physical security).
**Objective:** 1.2 Define cloud and virtualization concepts
**Ref:** https://docs.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility

---

---

### Q5 — VPN Definition
**Soal:** What is a VPN?

**Jawaban:** Virtual Private Network — jaringan privat virtual yang mengenkripsi koneksi melalui internet.

---

---

### Q6 — Tunneling Protocol
**Soal:** Which network element uses a tunneling protocol to encapsulate data for transmission?

**Jawaban:** VPN

---

---

### Q7 — VPN Terms (Match)
**Soal:** Move each VPN term to the correct definition.

| Definition | VPN Type |
|------------|----------|
| Allows a remote user to connect to a private network from anywhere on the internet | **Remote-Access VPN** |
| Securely connects two portions of a private network or two private networks | **Site-to-Site VPN** |
| Creates an unencrypted connection between two network devices | **GRE Tunnel** |

---

---

### Q8 — Perimeter Network
**Soal:** What is the primary purpose of a perimeter network?

**Jawaban:** DMZ — menyediakan lapisan keamanan tambahan antara jaringan internal dan internet.

---

---

### Q9 — WAN (True/False)
**Soal:** For each statement about wide area networks (WANs), select **True** or **False**.

| # | Statement | Jawaban |
|---|-----------|---------|
| A | The Internet is a WAN. | ✅ **True** |
| B | An intranet is a WAN. | ❌ **False** |
| C | All devices connected to a WAN must be located within the same city. | ❌ **False** |

**Penjelasan:** Internet adalah koleksi WAN. Intranet hanya ada dalam LAN/private network. WAN tidak terbatas pada satu kota.

---

---

### Q10 — NAT/PAT
**Soal:** Small office, 15 computers, one public IP. Which routing function should you enable?

**Jawaban:** NAT (Network Address Translation)

---

## Domain 1.4: Wireless Networking

---

### Q11 — Wireless Security Weakness
**Soal:** Which statement describes a weakness of wireless networks?

**Ref:** https://www.portnox.com/cybersecurity-101/wireless-network-security-risks/

---

---

### Q12 — SSID
**Soal:** On a wireless router, what is an SSID?

**Jawaban:** Service Set Identifier — nama jaringan wireless yang digunakan untuk mengidentifikasi jaringan.
**Objective:** 1.4 Understand wireless networking
**Ref:** http://www.microsoft.com/athome/organization/wirelesssetup.aspx

---

## Domain 2: Network Infrastructure

---

### Q13 — Network Topology
**Soal:** Which physical network topology provides fault-tolerant communication by providing redundant communication paths?

**Jawaban:** Mesh topology

---

---

### Q14 — VLAN Trunk Port
**Soal:** Which type of port supports VLAN traffic between two switches?

**Jawaban:** Trunk port

---

---

### Q15 — VLAN Purpose
**Soal:** What is a reason to incorporate VLANs into a network?

**Jawaban:** Segmentasi jaringan — meningkatkan keamanan dan mengurangi broadcast domain.

---

---

### Q16 — Switch Behavior (True/False)
**Soal:** For each statement about switches, select **True** or **False**.

| # | Statement | Jawaban |
|---|-----------|---------|
| 1 | A switch sends unicast frames to only one destination port. | ✅ **True** |
| 2 | A switch floods ports if it does not know where to send a frame. | ✅ **True** |
| 3 | A switch sends broadcast frames to only the uplink port. | ❌ **False** |

---

---

### Q17 — Dynamic Routing
**Soal:** What is an advantage of dynamic routing?

**Jawaban:** Otomatis menyesuaikan rute ketika topologi berubah (fault tolerance).

---

---

### Q18 — Static Routing
**Soal:** How is a router's static routing table updated?

**Jawaban:** Secara manual oleh network administrator.

---

---

### Q19 — Fault Tolerant Routing
**Soal:** Which routing option is fault tolerant?

**Jawaban:** Dynamic routing
**Objective:** 2.2 Understand routers
**Ref:** http://technet.microsoft.com/en-us/library/cc957844.aspx

---

---

### Q20 — STP vs UTP Cable
**Soal:** What is a justification for using STP cable instead of UTP cable?

**Jawaban:** STP memberikan perlindungan terhadap EMI (Electromagnetic Interference).

---

---

### Q21 — Media Type EMI/RFI
**Soal:** Which media type is least susceptible to external interference including EMI and RFI?

**Jawaban:** Fiber optic cable

---

## Domain 3: Network Protocols & Services

---

### Q22 — IP Address Types (Match)
**Soal:** Move the appropriate address types to the correct ranges.

| Range | Address Type |
|-------|-------------|
| 127.0.0.0 – 127.255.255.255 | **Loopback** |
| 192.168.0.0 – 192.168.255.255 | **Private** |
| 224.0.0.0 – 239.255.255.255 | **Multicast** |

---

---

### Q23 — Network Protocols (Match)
**Soal:** Move the appropriate protocols to the correct descriptions.

| Description | Protocol |
|-------------|----------|
| Connectionless, message-based protocol with best-effort service | **UDP** |
| Connection-oriented protocol with guaranteed service | **TCP** |
| Resolves a MAC address to an IP address | **ARP** |

---

---

### Q24 — DHCP Failure
**Soal:** Your router's DHCP is not functioning. Which address indicates the DHCP is NOT working?

**Jawaban:** 169.254.x.x (APIPA address)

---

---

### Q25 — IPv4 Multicast Range
**Soal:** In which range are IPv4 multicast addresses?

**Jawaban:** 224.0.0.0 – 239.255.255.255
**Objective:** 3.2 Understand IPv4
**Ref:** http://technet.microsoft.com/en-us/library/cc754783

---

---

### Q26 — IPv6 Loopback
**Soal:** Which option represents an IPv6 loopback address?

**Jawaban:** ::1

---

---

### Q27 — IPv4 Address Classes (Match)
**Soal:** Move each IP address to the correct IPv4 address class.

| Class | First Octet Range |
|-------|------------------|
| Class A | 1-126 |
| Class B | 128-191 |
| Class C | 192-223 |
| Class D | 224-239 (Multicast) |

---

---

### Q28 — DNS Records
**Soal:** Which service uses PTR and A records?

**Jawaban:** DNS (Domain Name System)

---

---

### Q29 — DHCP Lease Expiration
**Soal:** What happens when a client's DHCP-issued address expires?

**Jawaban:** Client attempts to renew the lease; jika gagal, client kehilangan IP dan mendapat APIPA address.

---

## Domain 5: Network Troubleshooting

---

### Q30 — Fiber Testing Tool
**Soal:** The fiber network connection is 550 meters with attenuation on the line. Which tool should you use?

**Jawaban:** OTDR (Optical Time-Domain Reflectometer)
**Objective:** 5.2 Use appropriate hardware troubleshooting tools
**Ref:** https://www.flukenetworks.com/expertise/learn-about/otdr

---

---

### Q31 — Copper Cable Troubleshooting
**Soal:** Computer connected through patch panel getting lower-than-expected speeds. Which **two** actions to identify the issue? (Choose 2.)

**Jawaban:** Cable tester dan check patch panel connections.
**Objective:** 5.2 Use appropriate hardware troubleshooting tools
**Ref:** https://electricalconnection.com.au/solving-common-cabling-problems/

---

---

### Q32 — DNS Resolution Utility
**Soal:** Which utility to determine whether DNS is properly resolving FQDNs to IP addresses?

**Jawaban:** nslookup

---

---

### Q33 — FQDN vs IP Ping
**Soal:** Ping by FQDN fails but ping by IP succeeds. Why?

**Jawaban:** DNS resolution is not working properly — masalah ada di DNS, bukan konektivitas jaringan.

---

---

### Q34 — Linux Network Connections
**Soal:** In Linux, which command-line tool to list active incoming connections?

**Jawaban:** **netstat**

| Option | Keterangan |
|--------|------------|
| netstat | ✅ **Benar** — digunakan untuk informasi koneksi jaringan |
| dig | ❌ Salah — untuk DNS queries |
| host | ❌ Salah — untuk DNS lookups |
| ip addr | ❌ Salah — untuk informasi alamat IP, bukan koneksi |

**Ref:** https://technet.microsoft.com/en-us/library/bb490947.aspx

---

---

### Q35 — IP Configuration Analysis (Dropdown)
**Soal:** Refer to the image. Complete the statements about IP address configuration.

Pilihan:
- The IP address of the wireless adapter is configured ____ (manually/by DHCP)
- The IP address of the Ethernet adapter is configured ____ (manually/by DHCP)

---

---

### Q36 — Traceroute Analysis (Dropdown)
**Soal:** Refer to the scenario and image. Complete the statements about traceroute.

Pilihan:
- Each hop in the trace route is a ____
- The trace route completed ____

---

> [!NOTE]
> **Catatan:** Beberapa soal (terutama multiple choice) tidak menampilkan pilihan jawaban secara lengkap karena pilihan tersebut di-render secara dinamis oleh engine Certiport, bukan disimpan sebagai teks statis dalam file resource. Soal yang bertipe True/False dan Match/Drag-Drop cenderung memiliki jawaban yang lebih lengkap.

> [!WARNING]
> File ini berisi soal ujian sertifikasi Certiport yang dilindungi hak cipta. Konten ini diekstrak untuk keperluan analisis teknis saja.

---

### Q37 — Network Types
**Soal:** Your company's computers exchange data through a set of routed private Wi-Fi networks at a single geographic location. What type of network is this an example of?

**Jawaban:** WLAN / LAN (Local Area Network / Wireless Local Area Network)

---

---

### Q38 — Internet of Things (IoT) (True/False)
**Soal:** For each statement about the Internet of Things (IoT), select **True** or **False**.

| # | Statement | Jawaban |
|---|-----------|---------|
| 1 | IoT devices have IP addresses. | ✅ **True** |
| 2 | IoT devices require human interaction to communicate with a network. | ❌ **False** |
| 3 | A smart thermostat and a lightbulb that can be switched on by using an app are examples of IoT devices. | ✅ **True** |

**Penjelasan:** IoT devices memiliki IP address, dapat berkomunikasi tanpa interaksi manusia, dan contohnya adalah smart thermostat/lightbulb (walaupun di solusi ada catatan membingungkan tentang smartphone, opsi ini biasanya True).

---

---

### Q39 — Virtualization & Hypervisor (True/False)
**Soal:** For each statement about using a Type 2 hypervisor and virtual machines, select **True** or **False**.

| # | Statement | Jawaban |
|---|-----------|---------|
| 1 | If you reboot one virtual machine, all the other virtual machines on the server reboot at the same time. | ❌ **False** |
| 2 | You can reboot the host machine without it having any effect on the other virtual machines on the same physical server. | ❌ **False** |
| 3 | If you need to reboot one virtual machine, you must first reboot the physical server. | ❌ **False** |

**Penjelasan:** Guest VM independen satu sama lain (reboot satu VM tidak mempengaruhi yang lain). Namun, reboot Host OS akan men-suspend atau mematikan semua Guest VM.

---

---

### Q40 — Extending Internal Networks
**Soal:** Which technology can you use to extend an internal network across shared or public networks?

**Jawaban:** VPN (Virtual Private Network)

---

---

### Q41 — VPN Purpose
**Soal:** What does a VPN provide?

**Jawaban:** Koneksi aman/terenkripsi (secure connection) melalui jaringan publik (internet).

---

---

### Q42 — Protecting Internal Network
**Soal:** You are helping a friend set up a public-facing web server in their home office. Your friend wants to protect the internal network from intrusion. What should you do?

**Jawaban:** Membangun Perimeter Network / DMZ (Demilitarized Zone).

---

---

### Q43 — VPN True/False
**Soal:** Remote users need to connect to your network through a server running Windows Server that is deployed on your perimeter network. For each statement, select **True** or **False**.

| # | Statement | Jawaban |
|---|-----------|---------|
| 1 | You can use a VPN to enable users to make a secure connection to your network through the Internet. | ✅ **True** |
| 2 | If users connect to the Internet through dial-up connections, the server must also connect through a dial-up connection. | ❌ **False** |
| 3 | You can use RAS Gateway to configure a VPN connection for Windows 10 clients that is active whenever the client connects to the Internet. | ✅ **True** |

---

---

### Q44 — Broadest Area Network
**Soal:** Which type of network covers the broadest area?

**Jawaban:** WAN (Wide Area Network)

---

---

### Q45 — LAN to WAN Connection
**Soal:** Which hardware is required to properly connect a LAN to a WAN?

**Jawaban:** Router
**Objective:** 2.2 Define the characteristics of wide area networks
**Ref:** https://www.open.edu/openlearncreate/mod/oucontent/view.php?id=130530&printable=1

---

---

### Q46 — Wireless Authentication
**Soal:** Which wireless authentication method provides the highest level of security involving an authentication server?

**Jawaban:** WPA2/WPA3 Enterprise (biasanya menggunakan 802.1X/RADIUS server).
**Ref:** https://www.techtarget.com/searchnetworking/feature/Wireless-encryption-basics-Understanding-WEP-WPA-and-WPA2

---

---

### Q47 — Weak Wireless Encryption
**Soal:** Which wireless encryption type is the most susceptible to interception and decryption?

**Jawaban:** WEP (Wired Equivalent Privacy)
**Objective:** 2.3 Understand media types

---

## Domain 2: Network Infrastructure

---

### Q48 — Internet Network Topology
**Soal:** Which network topology is the internet designed around?

**Jawaban:** Mesh topology

---

---

### Q49 — Multilayer Switch Feature
**Soal:** In addition to switching, which feature is specific to a multilayer switch?

**Jawaban:** Routing (Layer 3 switching)

---

---

### Q50 — Workgroup Network Device
**Soal:** Which network device interconnects computers in a workgroup, can be remotely configured, and provides the best throughput?

**Jawaban:** Managed Switch

---

---

### Q51 — Cable for Manufacturing Floor
**Soal:** You need to run four Ethernet network drops on your company's manufacturing floor. Each drop is approximately 125 feet/38 meters. Each drop passes near heavy manufacturing equipment. You need to ensure that interference is reduced. Which cable type should you use?

**Jawaban:** STP (Shielded Twisted Pair) atau Fiber Optic

---

---

### Q52 — Long Distance Cable
**Soal:** You need to install a network cable between two locations that are approximately six miles/ten kilometers from each other. Which cable should you use?

**Jawaban:** Single-mode Fiber Optic

---

## Domain 3: Network Protocols & Services

---

### Q53 — Transport Layer Protocol
**Soal:** Which protocol operates at the transport layer of the TCP model?

**Jawaban:** TCP atau UDP

---

---

### Q54 — IPv4 Address Composition
**Soal:** What does each IPv4 address consist of?

**Jawaban:** Network ID dan Host ID (atau 32 bits, terbagi dalam 4 octet).

---

---

### Q55 — Port Numbers (Match)
**Soal:** Move the appropriate TCP port numbers to the correct services.

| Port | Service |
|------|---------|
| 21 | **FTP** |
| 25 | **SMTP** |
| 443 | **HTTPS** |

---

---

### Q56 — Teredo Tunneling
**Soal:** What is a feature of the Teredo tunneling protocol?

**Jawaban:** Memungkinkan paket IPv6 untuk ditransmisikan melalui jaringan IPv4, bahkan saat berada di belakang perangkat NAT.

---

---

### Q57 — Ping Protocol
**Soal:** Which protocol does the ping utility use to test communication with a remote host?

**Jawaban:** ICMP (Internet Control Message Protocol)

---

---

### Q58 — Top-Level Domain
**Soal:** What is the top-level domain of ftp.sunsetweb.org?

**Jawaban:** .org

---

---

### Q59 — Internal to Internet Config
**Soal:** You need to configure a router to enable internal clients with private IPv4 addresses to access the internet and navigate to multiple websites. What should you configure?

**Jawaban:** NAT (Network Address Translation) atau lebih spesifik PAT (Port Address Translation).

---

## Domain 5: Network Troubleshooting

---

### Q60 — Cable Testing Tool
**Soal:** Which network hardware tool should you use to determine whether a UTP cable is capable of 1000Mbps full-duplex transmission?

**Jawaban:** Cable Certifier / Network Cable Tester
**Objective:** 5.2 Use appropriate hardware troubleshooting tools
**Ref:** https://www.computerhope.com/jargon/c/cabletest.htm

---

---

### Q61 — Isolating Cable in Bundle
**Soal:** You need to know where the jack is plugged into the patch panel. However, there are no labels. In the main distribution frame (MDF), you discover a bundle of 35 cables. Which tool should you use to isolate the correct cable?

**Jawaban:** Tone generator and probe (Toner probe / Fox and Hound).
**Objective:** 5.2 Use appropriate hardware troubleshooting tools
**Ref:** https://www.techwalla.com/articles/how-to-use-a-cable-toner

---

---

### Q62 — Firewall Listening Ports
**Soal:** You are setting up a network computer game. You need to open up ports on your firewall so your friends can join the network. Which command displays the ports that your computer is listening for?

**Jawaban:** `netstat -a` atau `netstat -an`

---

---

### Q63 — Linux Network Connections
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

---
