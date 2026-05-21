# Soal Ujian ITS Networking (IT101) — Form A

> [!IMPORTANT]
> **36 soal** berhasil diekstrak dari `272-1462-ENU-INF-101-ENU--Form-A.res`.
> Data didekompresi dari blok gzip dalam file ITSFFRES. Beberapa soal memiliki jawaban benar yang teridentifikasi melalui tag `<SOLUTION>`.

---

## Domain 1: Networking Fundamentals

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

### Q2 — Network Types
**Soal:** A financial institution operates multiple branches across different states. Each branch uses its own local switching infrastructure, but financial records are accessed through encrypted links over service-provider networks. Which type of network best describes the connectivity between the branches?

**Jawaban:** WAN (Wide Area Network)
**Objective:** IT101-1.1-04
**Ref:** https://www.extratechs.com.au/blog/lan-vs-wan-vs-can-vs-pan-vs-wlan

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

### Q4 — Cloud Migration
**Soal:** CompanyPro plans to migrate all of their servers to the cloud. Which **two** administrative responsibilities will be eliminated? (Choose 2.)

**Penjelasan:** Migrasi ke cloud menghilangkan tanggung jawab hardware fisik (server maintenance, physical security).
**Objective:** 1.2 Define cloud and virtualization concepts
**Ref:** https://docs.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility

---

### Q5 — VPN Definition
**Soal:** What is a VPN?

**Jawaban:** Virtual Private Network — jaringan privat virtual yang mengenkripsi koneksi melalui internet.

---

### Q6 — Tunneling Protocol
**Soal:** Which network element uses a tunneling protocol to encapsulate data for transmission?

**Jawaban:** VPN

---

### Q7 — VPN Terms (Match)
**Soal:** Move each VPN term to the correct definition.

| Definition | VPN Type |
|------------|----------|
| Allows a remote user to connect to a private network from anywhere on the internet | **Remote-Access VPN** |
| Securely connects two portions of a private network or two private networks | **Site-to-Site VPN** |
| Creates an unencrypted connection between two network devices | **GRE Tunnel** |

---

### Q8 — Perimeter Network
**Soal:** What is the primary purpose of a perimeter network?

**Jawaban:** DMZ — menyediakan lapisan keamanan tambahan antara jaringan internal dan internet.

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

### Q10 — NAT/PAT
**Soal:** Small office, 15 computers, one public IP. Which routing function should you enable?

**Jawaban:** NAT (Network Address Translation)

---

## Domain 1.4: Wireless Networking

### Q11 — Wireless Security Weakness
**Soal:** Which statement describes a weakness of wireless networks?

**Ref:** https://www.portnox.com/cybersecurity-101/wireless-network-security-risks/

---

### Q12 — SSID
**Soal:** On a wireless router, what is an SSID?

**Jawaban:** Service Set Identifier — nama jaringan wireless yang digunakan untuk mengidentifikasi jaringan.
**Objective:** 1.4 Understand wireless networking
**Ref:** http://www.microsoft.com/athome/organization/wirelesssetup.aspx

---

## Domain 2: Network Infrastructure

### Q13 — Network Topology
**Soal:** Which physical network topology provides fault-tolerant communication by providing redundant communication paths?

**Jawaban:** Mesh topology

---

### Q14 — VLAN Trunk Port
**Soal:** Which type of port supports VLAN traffic between two switches?

**Jawaban:** Trunk port

---

### Q15 — VLAN Purpose
**Soal:** What is a reason to incorporate VLANs into a network?

**Jawaban:** Segmentasi jaringan — meningkatkan keamanan dan mengurangi broadcast domain.

---

### Q16 — Switch Behavior (True/False)
**Soal:** For each statement about switches, select **True** or **False**.

| # | Statement | Jawaban |
|---|-----------|---------|
| 1 | A switch sends unicast frames to only one destination port. | ✅ **True** |
| 2 | A switch floods ports if it does not know where to send a frame. | ✅ **True** |
| 3 | A switch sends broadcast frames to only the uplink port. | ❌ **False** |

---

### Q17 — Dynamic Routing
**Soal:** What is an advantage of dynamic routing?

**Jawaban:** Otomatis menyesuaikan rute ketika topologi berubah (fault tolerance).

---

### Q18 — Static Routing
**Soal:** How is a router's static routing table updated?

**Jawaban:** Secara manual oleh network administrator.

---

### Q19 — Fault Tolerant Routing
**Soal:** Which routing option is fault tolerant?

**Jawaban:** Dynamic routing
**Objective:** 2.2 Understand routers
**Ref:** http://technet.microsoft.com/en-us/library/cc957844.aspx

---

### Q20 — STP vs UTP Cable
**Soal:** What is a justification for using STP cable instead of UTP cable?

**Jawaban:** STP memberikan perlindungan terhadap EMI (Electromagnetic Interference).

---

### Q21 — Media Type EMI/RFI
**Soal:** Which media type is least susceptible to external interference including EMI and RFI?

**Jawaban:** Fiber optic cable

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

### Q23 — Network Protocols (Match)
**Soal:** Move the appropriate protocols to the correct descriptions.

| Description | Protocol |
|-------------|----------|
| Connectionless, message-based protocol with best-effort service | **UDP** |
| Connection-oriented protocol with guaranteed service | **TCP** |
| Resolves a MAC address to an IP address | **ARP** |

---

### Q24 — DHCP Failure
**Soal:** Your router's DHCP is not functioning. Which address indicates the DHCP is NOT working?

**Jawaban:** 169.254.x.x (APIPA address)

---

### Q25 — IPv4 Multicast Range
**Soal:** In which range are IPv4 multicast addresses?

**Jawaban:** 224.0.0.0 – 239.255.255.255
**Objective:** 3.2 Understand IPv4
**Ref:** http://technet.microsoft.com/en-us/library/cc754783

---

### Q26 — IPv6 Loopback
**Soal:** Which option represents an IPv6 loopback address?

**Jawaban:** ::1

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

### Q28 — DNS Records
**Soal:** Which service uses PTR and A records?

**Jawaban:** DNS (Domain Name System)

---

### Q29 — DHCP Lease Expiration
**Soal:** What happens when a client's DHCP-issued address expires?

**Jawaban:** Client attempts to renew the lease; jika gagal, client kehilangan IP dan mendapat APIPA address.

---

## Domain 5: Network Troubleshooting

### Q30 — Fiber Testing Tool
**Soal:** The fiber network connection is 550 meters with attenuation on the line. Which tool should you use?

**Jawaban:** OTDR (Optical Time-Domain Reflectometer)
**Objective:** 5.2 Use appropriate hardware troubleshooting tools
**Ref:** https://www.flukenetworks.com/expertise/learn-about/otdr

---

### Q31 — Copper Cable Troubleshooting
**Soal:** Computer connected through patch panel getting lower-than-expected speeds. Which **two** actions to identify the issue? (Choose 2.)

**Jawaban:** Cable tester dan check patch panel connections.
**Objective:** 5.2 Use appropriate hardware troubleshooting tools
**Ref:** https://electricalconnection.com.au/solving-common-cabling-problems/

---

### Q32 — DNS Resolution Utility
**Soal:** Which utility to determine whether DNS is properly resolving FQDNs to IP addresses?

**Jawaban:** nslookup

---

### Q33 — FQDN vs IP Ping
**Soal:** Ping by FQDN fails but ping by IP succeeds. Why?

**Jawaban:** DNS resolution is not working properly — masalah ada di DNS, bukan konektivitas jaringan.

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

### Q35 — IP Configuration Analysis (Dropdown)
**Soal:** Refer to the image. Complete the statements about IP address configuration.

Pilihan:
- The IP address of the wireless adapter is configured ____ (manually/by DHCP)
- The IP address of the Ethernet adapter is configured ____ (manually/by DHCP)

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
