[comptia-network-plus-n10-009-learning-path.md](https://github.com/user-attachments/files/29178632/comptia-network-plus-n10-009-learning-path.md)
# CompTIA Network+ (N10-009) — Comprehensive Learning Path

> **Target Exam:** N10-009 | **Last Updated:** 2025  
> **Prerequisites:** None (recommended: 9 months networking experience or A+)

---

## Table of Contents

1. [Exam Overview & Study Strategy](#1-exam-overview--study-strategy)
2. [Domain 1: Networking Fundamentals (24%)](#2-domain-1-networking-fundamentals-24)
3. [Domain 2: Network Implementations (19%)](#3-domain-2-network-implementations-19)
4. [Domain 3: Network Operations (16%)](#4-domain-3-network-operations-16)
5. [Domain 4: Network Security (19%)](#5-domain-4-network-security-19)
6. [Domain 5: Network Troubleshooting (22%)](#6-domain-5-network-troubleshooting-22)
7. [Practice Questions & Scenarios](#7-practice-questions--scenarios)
8. [Exam Day Tips](#8-exam-day-tips)
9. [Resources & Labs](#9-resources--labs)

---

## 1. Exam Overview & Study Strategy

### Exam Facts
| Detail | Value |
|---|---|
| Questions | 90 max (multiple choice + PBQs) |
| Time | 90 minutes |
| Passing Score | 720/900 |
| Cost | ~$370 USD |
| Validity | 3 years |

### Study Plan (12 weeks recommended)

| Week | Focus |
|---|---|
| 1–2 | Domain 1: Fundamentals — OSI model, topologies, IP addressing |
| 3–4 | Domain 2: Implementations — Routing, switching, wireless |
| 5–6 | Domain 3: Operations — Monitoring, docs, policies |
| 7–8 | Domain 4: Security — Threats, hardening, firewalls |
| 9–10 | Domain 5: Troubleshooting — Methodology + scenarios |
| 11 | PBQ practice + full-length exams |
| 12 | Review weak areas + exam day prep |

### Key Acronyms to Know Cold
- **OSI:** Please Do Not Throw Sausage Pizza Away (7→1)
- **TCP/IP:** Application, Transport, Internet, Link (4-layer)
- **PoE:** Power over Ethernet
- **STP:** Spanning Tree Protocol
- **NAC:** Network Access Control
- **RADIUS/TACACS+:** Remote authentication protocols
- **SNMP:** Simple Network Mgmt Protocol
- **SLAAC:** Stateless Address Autoconfiguration

---

## 2. Domain 1: Networking Fundamentals (24%)

### 2.1 The OSI Model — Your Mental Map

Every networking question maps back here. **Memorize this table:**

| Layer | Number | Data Unit | Protocol Examples | Device |
|---|---|---|---|---|
| Application | 7 | Data | HTTP, HTTPS, FTP, SMTP, DNS | — |
| Presentation | 6 | Data | SSL/TLS, JPEG, GIF | — |
| Session | 5 | Data | NetBIOS, RPC, SMB | — |
| Transport | 4 | Segment | TCP, UDP | — |
| Network | 3 | Packet | IP, ICMP, ARP, OSPF | Router |
| Data Link | 2 | Frame | Ethernet, 802.11, PPP | Switch, Bridge |
| Physical | 1 | Bits | 1000BASE-T, DSL, RS-232 | Hub, Repeater, Modem |

> **Real-world example:** When you visit `https://google.com`, your browser (Layer 7) sends an HTTPS request. TLS encrypts it (Layer 6). A TCP session opens (Layer 5). TCP segments are created (Layer 4). The segments become IP packets with source/dest IP (Layer 3). The packet is placed in Ethernet frames with MAC addresses (Layer 2). The frame is transmitted as electrical signals (Layer 1).

### 2.2 TCP vs UDP

| Feature | TCP | UDP |
|---|---|---|
| Connection | Connection-oriented (3-way handshake) | Connectionless |
| Reliability | Guaranteed delivery via ACKs | No guarantee |
| Ordering | In-sequence delivery | No ordering |
| Speed | Slower (overhead) | Fast (low overhead) |
| Use Cases | Web, email, file transfer | VoIP, video streaming, DNS, DHCP |
| Port Examples | 80 (HTTP), 443 (HTTPS), 22 (SSH) | 53 (DNS), 67/68 (DHCP), 123 (NTP) |

**3-Way Handshake:** SYN → SYN-ACK → ACK
**Graceful Teardown:** FIN → ACK → FIN → ACK

### 2.3 IP Addressing

#### IPv4 Address Classes (legacy but tested)

| Class | Range | Default Mask | Purpose |
|---|---|---|---|
| A | 1.0.0.0 – 126.255.255.255 | /8 | Large orgs |
| B | 128.0.0.0 – 191.255.255.255 | /16 | Medium orgs |
| C | 192.0.0.0 – 223.255.255.255 | /24 | Small orgs |
| D | 224.0.0.0 – 239.255.255.255 | — | Multicast |
| E | 240.0.0.0 – 255.255.255.255 | — | Experimental |

#### Private IP Ranges (RFC 1918)
- **Class A:** 10.0.0.0/8 (10.0.0.0 – 10.255.255.255)
- **Class B:** 172.16.0.0/12 (172.16.0.0 – 172.31.255.255)
- **Class C:** 192.168.0.0/16 (192.168.0.0 – 192.168.255.255)

#### Special IPv4 Addresses
- **127.0.0.1** — Loopback (localhost)
- **169.254.0.0/16** — APIPA (automatic private IP when DHCP fails)
- **0.0.0.0/8** — "This network" (used as default route: 0.0.0.0/0)
- **224.0.0.1** — All hosts on subnet (multicast)
- **224.0.0.2** — All routers on subnet (multicast)
- **240.0.0.0/4** — Reserved (future use)

#### Subnetting Cheatsheet

| Prefix | Subnet Mask | Hosts (usable) | Classful |
|---|---|---|---|
| /24 | 255.255.255.0 | 254 | C |
| /25 | 255.255.255.128 | 126 | — |
| /26 | 255.255.255.192 | 62 | — |
| /27 | 255.255.255.224 | 30 | — |
| /28 | 255.255.255.240 | 14 | — |
| /29 | 255.255.255.248 | 6 | — |
| /30 | 255.255.255.252 | 2 | Point-to-point link |
| /16 | 255.255.0.0 | 65534 | B |
| /8 | 255.0.0.0 | 16M+ | A |

**Quick subnet formula:** Usable hosts = 2^(32 - prefix) - 2 (subtract network & broadcast)

> **Real-world example:** A /26 network (255.255.255.192) gives 62 usable IPs. An office with 50 devices would use this. The subnet mask tells devices: "anything within the same /26 goes directly via ARP; anything outside goes to the default gateway."

#### IPv6 Essentials

| Feature | Detail |
|---|---|
| Address length | 128 bits (8 groups of 16-bit hex) |
| Notation | `2001:0db8:85a3:0000:0000:8a2e:0370:7334` |
| Shorthand | Omit leading zeros: `2001:db8:85a3:0:0:8a2e:370:7334` |
| Double colon | `::` = one or more all-zero groups (use once!) |
| Loopback | `::1` |
| Link-local | `fe80::/10` (automatic, not routable) |
| Global unicast | `2000::/3` |
| Unique local | `fc00::/7` (equivalent to RFC 1918) |
| Multicast | `ff00::/8` |

**IPv6 address types:**
- **Unicast** — One-to-one
- **Multicast** — One-to-many
- **Anycast** — One-to-nearest (same address on multiple devices)

### 2.4 Network Topologies

| Topology | Pros | Cons | Exam Tip |
|---|---|---|---|
| Star | Easy to troubleshoot, scalable | Single point of failure at hub/switch | Most common topology |
| Bus | Cheap, simple | Hard to troubleshoot, single cable fails everything | Legacy (thinnet/thicknet) |
| Ring | Deterministic, predictable | One node breaks the ring | Token Ring / FDDI |
| Mesh | Highly redundant | Expensive, complex cabling | WAN backbone |
| Hybrid | Flexible, combines best of each | Complex mgmt | Modern enterprise networks |

### 2.5 Cabling and Connectors

#### Copper Cabling

| Standard | Speed | Max Distance | Connector | Notes |
|---|---|---|---|---|
| Cat 5e | 1 Gbps | 100m | RJ-45 | Minimum for modern networks |
| Cat 6 | 1 Gbps (10 Gbps to 55m) | 100m | RJ-45 | Tighter specs than 5e |
| Cat 6a | 10 Gbps | 100m | RJ-45 | Shielded options |
| Cat 7 | 10 Gbps | 100m | GG-45 / TERA | Shielded, not widely adopted |
| Cat 8 | 25/40 Gbps | 30m | RJ-45 | Data center only |

**T568A vs T568B wiring:**
- **T568B** (most common): white-orange/orange/white-green/blue/white-blue/green/white-brown/brown
- **T568A:** white-green/green/white-orange/blue/white-blue/orange/white-brown/brown
- **Straight-through:** Same pinout both ends (PC ↔ switch)
- **Crossover:** T568A one end, T568B other (PC ↔ PC, switch ↔ switch) — **modern NICs auto-MDIX negates this**

#### Fiber Optic

| Type | Core Size | Distance | Connector | Light Source |
|---|---|---|---|---|
| Multimode (MM) | 50µm or 62.5µm | Up to 2km | LC, SC, ST, MTRJ | LED |
| Singlemode (SM) | 9µm | Up to 100km+ | LC, SC | Laser |

**Connector quick reference:**
- **LC** — Small (looks like a smaller SC) — most common modern connector
- **SC** — Square snap-in (push-pull)
- **ST** — Round, bayonet-style (twist-lock)
- **MTRJ** — Small, duplex (two fibers in one connector)

> **Real-world example:** A data center uses LC-to-LC singlemode fiber for server-to-switch connections at 100 Gbps. An office building uses Cat 6a copper for desktop connections.

### 2.6 Ethernet Standards (IEEE 802.3)

| Standard | Speed | Cable | Max Distance |
|---|---|---|---|
| 10BASE-T | 10 Mbps | Cat 3+ | 100m |
| 100BASE-TX | 100 Mbps | Cat 5 | 100m |
| 1000BASE-T | 1 Gbps | Cat 5e | 100m |
| 10GBASE-T | 10 Gbps | Cat 6a | 100m |
| 1000BASE-SX | 1 Gbps | MM fiber | 550m |
| 1000BASE-LX | 1 Gbps | SM fiber | 5km |
| 10GBASE-SR | 10 Gbps | MM fiber | 400m |
| 10GBASE-LR | 10 Gbps | SM fiber | 10km |

### 2.7 Network Devices

| Device | OSI Layer | Function |
|---|---|---|
| **Hub** | 1 (Physical) | Repeats signal out all ports; half-duplex; collision domain = all ports |
| **Switch** | 2 (Data Link) | Forwards frames by MAC address; collision domain = per port |
| **Router** | 3 (Network) | Forwards packets by IP address; connects different networks |
| **Access Point (AP)** | 2 (Data Link) | Bridges wireless ↔ wired |
| **Firewall** | 3–7 | Filters traffic by rules (stateful inspection, NGFW) |
| **Load Balancer** | 4–7 | Distributes traffic across multiple servers |
| **Proxy** | 7 (Application) | Acts as intermediary for client requests |
| **IDS/IPS** | 3–7 | Monitors for threats (IDS = alert, IPS = block) |
| **Modem** | 1–2 | Modulates/demodulates signals (cable, DSL, fiber ONT) |

**Key difference — Collision vs Broadcast Domain:**
- **Hub:** 1 collision domain per hub
- **Switch:** 1 collision domain per port (each port is separate)
- **Router:** 1 broadcast domain per interface (router stops broadcasts)

### 2.8 ARP — Address Resolution Protocol

**Purpose:** Resolves IP → MAC address  
**Process:**
1. Device sends broadcast: "Who has 192.168.1.10? Tell 192.168.1.5"
2. Target responds with its MAC address (unicast)
3. Both devices cache the mapping (ARP table — `arp -a`)

> **Real-world issue:** ARP cache poisoning = attacker sends forged ARP replies to redirect traffic through their machine (Man-in-the-Middle attack).

### 2.9 DHCP — Dynamic Host Configuration Protocol

**DORA Process:**
1. **D**iscover (client broadcast: "I need an IP")
2. **O**ffer (DHCP server offers an IP)
3. **R**equest (client requests that specific IP)
4. **A**ck (server confirms)

**DHCP Options (important for exam):**
- **Option 3:** Default gateway
- **Option 6:** DNS server
- **Option 51:** Lease time
- **Option 150:** TFTP server (VoIP)
- **Option 66:** TFTP server (PXE boot)

> **Real-world example:** An APIPA address (169.254.x.x) means DHCP failed — no server responded. `ipconfig /renew` forces a new DORA cycle.

### 2.10 DNS — Domain Name System

**Record Types:**
| Record | Purpose | Example |
|---|---|---|
| A | IPv4 hostname → IP | `google.com → 142.250.80.14` |
| AAAA | IPv6 hostname → IP | `google.com → 2607:f8b0::...` |
| CNAME | Alias → canonical name | `www → @ (apex)` |
| MX | Mail server priority | Priority 10 → mail.google.com |
| TXT | Text data (SPF, DKIM, DMARC) | `"v=spf1 include:_spf.google.com ~all"` |
| PTR | Reverse lookup (IP → hostname) | `14.80.250.142.in-addr.arpa → google.com` |
| SRV | Service location | `_sip._tcp.example.com` |
| NS | Authoritative name server | `ns1.example.com` |
| SOA | Start of Authority (zone info) | Primary NS, admin email, serial |

**DNS Resolution Steps:**
1. Check local cache → `ipconfig /displaydns`
2. Check hosts file → `C:\Windows\System32\drivers\etc\hosts`
3. Query recursive resolver → ISP DNS or 8.8.8.8
4. Root server → TLD server → Authoritative server → Response

> **Real-world issue:** DNS cache poisoning (spoofed DNS responses redirect users to fake sites). DNSSEC mitigates this via digital signatures on DNS records.

### 2.11 Port Numbers to Memorize for Exam

| Port | Protocol | Service |
|---|---|---|
| 20/21 | TCP | FTP (20=data, 21=control) |
| 22 | TCP | SSH |
| 23 | TCP | Telnet (unencrypted) |
| 25 | TCP | SMTP |
| 53 | **UDP**/TCP | DNS (primary: UDP, zone transfer: TCP) |
| 67/68 | UDP | DHCP (67=server, 68=client) |
| 69 | UDP | TFTP |
| 80 | TCP | HTTP |
| 110 | TCP | POP3 |
| 123 | UDP | NTP |
| 137–139 | TCP/UDP | NetBIOS |
| 143 | TCP | IMAP |
| 161/162 | UDP | SNMP (161=queries, 162=traps) |
| 389 | TCP/UDP | LDAP |
| 443 | TCP | HTTPS |
| 445 | TCP | SMB (Windows file sharing) |
| 514 | UDP | Syslog |
| 636 | TCP | LDAPS (LDAP over SSL) |
| 993 | TCP | IMAPS (IMAP over SSL) |
| 995 | TCP | POP3S (POP3 over SSL) |
| 1433 | TCP | Microsoft SQL |
| 1521 | TCP | Oracle DB |
| 1723 | TCP | PPTP (VPN, legacy) |
| 2049 | TCP/UDP | NFS |
| 3128 | TCP | Proxy (Squid default) |
| 3306 | TCP | MySQL |
| 3389 | TCP | RDP |
| 5060/5061 | UDP/TCP | SIP (5060=UDP, 5061=TLS) |
| 8080 | TCP | HTTP Alt (proxy/cache) |
| 8443 | TCP | HTTPS Alt |

---

## 3. Domain 2: Network Implementations (19%)

### 3.1 Routing Protocols

#### Dynamic Routing Protocol Comparison

| Protocol | Type | Metric | Algorithm | Speed | VLSM Support |
|---|---|---|---|---|---|
| **RIP** | Distance vector | Hop count (max 15) | Bellman-Ford | Slow | No (RIPv2: yes) |
| **EIGRP** | Hybrid (Cisco proprietary, now open) | Composite (bandwidth, delay, load, reliability) | DUAL | Fast | Yes |
| **OSPF** | Link state | Cost (based on bandwidth) | SPF/Dijkstra | Fast | Yes |
| **BGP** | Path vector | Path attributes | Best path selection | Slow convergence | Yes |

#### Administrative Distance (Trustworthiness)

| Route Source | AD |
|---|---|
| Connected | 0 |
| Static | 1 |
| EIGRP (summary) | 5 |
| BGP (eBGP) | 20 |
| OSPF | 110 |
| RIP | 120 |
| BGP (iBGP) | 200 |

**Default route:** `0.0.0.0/0` — used when no specific route matches.

> **Real-world example:** BGP is the routing protocol of the internet. When you visit a website, BGP routers across ISPs exchange routing information to find the best path between your ISP and the web server's network.

### 3.2 Switching Concepts

#### VLANs (Virtual LANs)
- **Purpose:** Logically separate networks on the same physical switch
- **Tagging:** 802.1Q adds a 4-byte tag to Ethernet frames
- **Native VLAN:** VLAN 1 (default, untagged traffic)
- **Trunk port:** Carries multiple VLANs (tagged)
- **Access port:** Carries one VLAN (untagged)

> **Real-world example:** An office has separate VLANs: VLAN 10 (Accounting), VLAN 20 (Engineering), VLAN 30 (Guest Wi-Fi). A router-on-a-stick or Layer 3 switch routes between them. Guest Wi-Fi has no access to internal VLANs.

#### STP — Spanning Tree Protocol (802.1D)
- **Purpose:** Prevents switching loops by blocking redundant paths
- **Port states:** Blocking → Listening → Learning → Forwarding (≈30–50s convergence)
- **RSTP (802.1w):** Fast convergence (3 states: Discarding, Learning, Forwarding)
- **Key concept:** Root bridge election (lowest bridge ID = priority + MAC)

#### Link Aggregation
- **802.3ad / LACP:** Combine multiple physical links into one logical link
- **Benefits:** Increased bandwidth + redundancy

### 3.3 Wireless Networking (802.11)

| Standard | Frequency | Max Speed (theoretical) | Range (indoor) |
|---|---|---|---|
| 802.11a | 5 GHz | 54 Mbps | ~35m |
| 802.11b | 2.4 GHz | 11 Mbps | ~40m |
| 802.11g | 2.4 GHz | 54 Mbps | ~40m |
| 802.11n (Wi-Fi 4) | 2.4/5 GHz | 600 Mbps | ~70m |
| 802.11ac (Wi-Fi 5) | 5 GHz | 1.3+ Gbps | ~35m |
| 802.11ax (Wi-Fi 6) | 2.4/5 GHz | 9.6 Gbps | ~70m |
| 802.11be (Wi-Fi 7) | 2.4/5/6 GHz | 46 Gbps | ~70m |

#### Wireless Security

| Protocol | Encryption | Authentication | Status |
|---|---|---|---|
| WEP | RC4 (weak) | Shared key | **Broken — never use** |
| WPA | TKIP/RC4 | PSK or 802.1X | Deprecated, weak |
| WPA2 | AES/CCMP | PSK or 802.1X | Current minimum standard |
| WPA3 | AES/GCMP-256 | SAE (Simultaneous Authentication of Equals) | Recommended |

**Wireless authentication modes:**
- **Open:** No auth (guest networks often use captive portal)
- **PSK (Personal):** Pre-shared key (home/small office)
- **802.1X (Enterprise):** RADIUS server authenticates users individually

#### Important Wireless Concepts
- **SSID:** Network name (broadcast in beacon frames)
- **BSSID:** MAC address of the AP
- **Channel overlap:** 2.4 GHz channels 1, 6, 11 are non-overlapping
- **MU-MIMO:** Multi-user MIMO (Wi-Fi 5 Wave 2+)
- **OFDMA:** Subdivides channels (Wi-Fi 6)
- **Roaming:** Client moves between APs (same SSID)
- **Bandwidth:** 20 MHz (default), 40 MHz, 80 MHz, 160 MHz (wider = faster but fewer channels)

### 3.4 WAN Technologies

| Technology | Speed | Medium | Notes |
|---|---|---|---|
| T1/DS1 | 1.544 Mbps | Copper | 24 channels × 64 Kbps |
| T3/DS3 | 44.736 Mbps | Copper/Fiber | 28 T1s |
| E1 (Europe) | 2.048 Mbps | Copper | 32 channels × 64 Kbps |
| SONET (OC-3) | 155.52 Mbps | Fiber | |
| SONET (OC-192) | 10 Gbps | Fiber | |
| DSL | 1–100 Mbps | Copper phone line | Asymmetric (ADSL) or symmetric (SDSL) |
| Cable broadband | 10–1000 Mbps | Coaxial (HFC) | Shared bandwidth |
| Fiber (FTTH) | 1–10 Gbps | Fiber | GPON, Active Ethernet |
| MPLS | Varies | Any transport | Labels instead of IP routing |
| Metro Ethernet | 10 Mbps – 100 Gbps | Fiber | Extends LAN across metro area |
| Satellite | 12–100 Mbps | RF (space) | High latency (600ms+) |

**VPN Types:**
- **Site-to-site:** Connects two office networks (IPsec tunnel)
- **Remote access:** Individual connects to corporate network (SSL VPN via browser or IPsec client)
- **SSL VPN:** Uses TLS (port 443) — no client needed
- **IPsec VPN:** Two modes — Transport (end-to-end) and Tunnel (gateway-to-gateway)
- **Split tunnel:** Only corporate traffic goes through VPN; internet traffic goes direct
- **Full tunnel:** All traffic goes through VPN

### 3.5 Network Virtualization

| Technology | Purpose |
|---|---|
| **Hypervisor** | Runs VMs (Type 1 = bare metal like ESXi, Type 2 = hosted like VirtualBox) |
| **vSwitch** | Virtual switch inside hypervisor (connects VMs) |
| **VXLAN** | Extends VLAN across Layer 3 networks (24-bit VNI = 16M segments) |
| **SDN** | Separates control plane (software) from data plane (hardware) |
| **NFV** | Runs network functions (firewall, load balancer) as VMs |
| **Virtual NIC** | Software NIC presented to a VM |

### 3.6 Cloud Concepts

| Deployment Model | Description |
|---|---|
| **Public** | Services offered over public internet (AWS, Azure, GCP) |
| **Private** | Dedicated to one organization |
| **Hybrid** | Mix of public + private with connectivity between |
| **Community** | Shared by several organizations with common goals |
| **Multicloud** | Multiple public cloud providers |

**Service Models:**
- **IaaS:** You manage OS, runtime, apps (AWS EC2)
- **PaaS:** You manage apps only (Heroku, Google App Engine)
- **SaaS:** You use the app (Gmail, Office 365)

**VDI (Virtual Desktop Infrastructure):** Desktops run on servers, accessed via thin client or software (VMware Horizon, Citrix)

---

## 4. Domain 3: Network Operations (16%)

### 4.1 Monitoring & Management

#### SNMP — Simple Network Management Protocol

| Version | Security | Notes |
|---|---|---|
| v1 | Community string (plain text) | **Legacy, avoid** |
| v2c | Community string (plain text) | Read/write community strings |
| v3 | User-based auth + encryption | **Use this** (authPriv, authNoPriv, noAuthNoPriv) |

**SNMP Components:**
- **Manager (NMS):** Central monitoring system (SolarWinds, PRTG, Nagios)
- **Agent:** Software on managed device (router, switch, server)
- **MIB:** Management Information Base — database of OIDs (Object Identifiers)
- **OID:** Unique identifier for each monitored value

**SNMP Operations:**
- **GET:** Manager requests value from agent
- **WALK:** Manager retrieves subtree of values
- **TRAP:** Agent sends unsolicited alert to manager
- **INFORM:** Agent sends confirmed alert to manager

#### Syslog
- **Facility:** Categorizes the source (kernel, mail, auth, etc.)
- **Severity levels (0–7):** Emergency (0), Alert (1), Critical (2), Error (3), Warning (4), Notice (5), Informational (6), Debug (7)
- **Format:** `<PRI>TIMESTAMP HOSTNAME APP[PID]: MESSAGE`

> **Real-world example:** `syslog-ng` on a Linux server collects logs from 50 switches. A switch interface going down generates a `<2>Jun 21 14:30:00 switch01 snmpd[1234]: Link DOWN: GigabitEthernet0/1` entry.

**Logging levels (Cisco):** Emergency (0) → Alert (1) → Critical (2) → Error (3) → Warning (4) → Notification (5) → Informational (6) → Debug (7)

### 4.2 Network Documentation

| Document | Purpose |
|---|---|
| **Physical topology diagram** | Cable paths, device locations, patch panels |
| **Logical topology diagram** | IP subnets, VLANs, routing protocols |
| **Wiring diagram** | Patch panel → switch port mapping |
| **Rack diagram** | Equipment position in racks |
| **Network baseline** | Normal performance metrics (for comparison when troubleshooting) |
| **SOP** | Standard Operating Procedures |
| **Change management records** | Who changed what and when |
| **Asset management** | Inventory of all network devices |

#### Performance Metrics

| Metric | Description | Good Value |
|---|---|---|
| Bandwidth | Max data rate | Depends on need |
| Throughput | Actual data transfer rate | As close to bandwidth as possible |
| Latency | Time from source to destination | < 10ms LAN, < 100ms WAN |
| Jitter | Variation in latency | < 30ms for VoIP |
| Packet loss | % of lost packets | < 1% acceptable |
| Utilization | % of bandwidth used | Keep < 70% average |
| Error rate | CRC errors, collisions | Near 0 |
| MTTR | Mean Time To Repair | Minimize |
| MTBF | Mean Time Between Failures | Maximize |

### 4.3 High Availability

| Concept | Description |
|---|---|
| **FHRP (First Hop Redundancy Protocol)** | HSRP (Cisco), VRRP (open), GLBP — virtual default gateway |
| **Load balancing** | Distributes traffic across multiple links/servers |
| **NIC teaming** | Multiple NICs act as one |
| **UPS** | Uninterruptible Power Supply (runtime vs surge protection) |
| **Redundant power supply** | Dual PSUs in switches/servers |
| **Generator** | Long-term backup power |
| **Failover** | Automatic switch to backup component |
| **Active/Active** | Both devices handle traffic simultaneously |
| **Active/Passive** | Primary handles traffic; standby activates on failure |
| **Hot standby** | Backup is fully operational (ready in seconds) |
| **Warm standby** | Backup needs brief initialization (minutes) |
| **Cold standby** | Backup needs full setup (hours) |

> **Real-world example:** Two ISPs and two routers run BGP for automatic failover. If ISP-A goes down, BGP withdraws the route and traffic flows through ISP-B within seconds.

### 4.4 Incident Response & Change Management

**Incident Response Process:**
1. **Preparation** — Tools, playbooks, team
2. **Detection** — Alert from monitoring system
3. **Containment** — Isolate affected system (quarantine VLAN, block IP)
4. **Eradication** — Remove root cause (patch, remove malware)
5. **Recovery** — Restore from backup, return to production
6. **Lessons learned** — Post-incident review, update policies

**Change Management Process:**
1. **RFC (Request for Change)** — Document: what, why, risk, rollback plan
2. **Approval** — CAB (Change Advisory Board) reviews
3. **Change window** — Scheduled downtime (maintenance window)
4. **Implementation** — Execute change
5. **Verification** — Confirm change works as expected
6. **Rollback plan** — If verification fails, revert

> **Real-world example:** An admin follows change management before updating a core switch firmware. The RFC documents the procedure, backout plan, and is approved by CAB. Change happens Saturday 2 AM. After verification, the ticket is closed.

### 4.5 Configuration & Lifecycle Management

- **Baseline configuration:** Standard config template for each device type
- **Firmware management:** Regular updates, testing before production
- **Backup configs:** Save running-config → startup-config → external backup
- **Archiving:** Keep config history for rollback
- **Patch management:** Regular update cycle with testing
- **Decommissioning:** Erase configs, wipe data, dispose responsibly

---

## 5. Domain 4: Network Security (19%)

### 5.1 Common Threats

| Threat | Description | Mitigation |
|---|---|---|
| **DoS/DDoS** | Overwhelm resource | Rate limiting, traffic filtering, scrubbing centers |
| **Spoofing** | Fake source IP/MAC | Source guard, IPsec, port security |
| **Man-in-the-Middle (MITM)** | Intercept traffic | Encryption (HTTPS, VPN), strong authentication |
| **ARP poisoning** | Fake ARP replies | Dynamic ARP Inspection (DAI) |
| **DNS poisoning** | Fake DNS responses | DNSSEC |
| **Rogue AP** | Unauthorized wireless AP | Wireless intrusion prevention (WIPS) |
| **Evil twin** | Fake AP with legitimate SSID | Use WPA3-Enterprise, certificate validation |
| **VLAN hopping** | Jump between VLANs | Disable DTP, set all ports as access or explicitly trunk |
| **Ransomware** | Encrypts files for ransom | Backups, email filtering, least privilege |
| **Phishing** | Social engineering via email | User training, email security gateway |
| **Social engineering** | Manipulate people for access | Policies, training, verification procedures |
| **Insider threat** | Malicious/disgruntled employee | Least privilege, monitoring, separation of duties |

### 5.2 Security Appliances

| Appliance | Function |
|---|---|
| **Stateful firewall** | Tracks connection state; allows return traffic automatically |
| **NGFW (Next-Gen Firewall)** | Stateful + application awareness + IPS + SSL inspection |
| **Proxy** | Intercepts client requests; can filter content, cache, anonymize |
| **Web application firewall (WAF)** | Protects web apps from SQLi, XSS, etc. |
| **IDS / IPS** | IDS = detect & alert; IPS = detect & block inline |
| **UTM** | All-in-one (firewall, IPS, antivirus, web filtering) |
| **VPN concentrator** | Terminates many VPN tunnels |
| **NAC** | Checks device compliance before granting network access |
| **Honeypot** | Decoy system to attract attackers |

### 5.3 Firewall Architectures

| Type | Description |
|---|---|
| **Screened subnet (DMZ)** | Public-facing servers between two firewalls (or firewall zones) |
| **3-leg firewall** | One firewall with three interfaces: inside, outside, DMZ |
| **Defense in depth** | Multiple overlapping security layers (firewall + IPS + endpoint) |
| **East-west traffic** | Traffic between servers in same data center (micro-segmentation) |

**ACL (Access Control List):**
- **Standard:** Filters by source IP only (numbered 1–99, 1300–1999)
- **Extended:** Filters by source/dest IP, port, protocol (numbered 100–199, 2000–2699)
- **Implicit deny:** All ACLs have "deny all" at the end

> **Real-world ACL:** `access-list 101 permit tcp 192.168.1.0 0.0.0.255 any eq 80` — allows internal network to browse web.

### 5.4 Authentication & Authorization

| Protocol | Transport | Function |
|---|---|---|
| **RADIUS** | UDP (1812/1813) | AAA for network devices (Wi-Fi, VPN) |
| **TACACS+** | TCP (49) | Cisco AAA (separate auth, authz, acct) |
| **LDAP** | TCP (389) | Directory services (Active Directory) |
| **Kerberos** | UDP/TCP (88) | Ticket-based auth (Windows domain) |
| **SAML** | HTTP | SSO for web apps |
| **OAuth/OpenID Connect** | HTTP | Delegated authorization (Google/Facebook login) |

**802.1X — Port-based NAC:**
- **Supplicant:** End device (laptop)
- **Authenticator:** Switch or AP
- **Authentication server:** RADIUS

**MFA (Multi-Factor Authentication):**
- Something you **know** (password)
- Something you **have** (phone, token, smart card)
- Something you **are** (fingerprint, retina)
- Somewhere you **are** (geolocation)

### 5.5 Network Hardening

| Technique | Purpose |
|---|---|
| **Disable unnecessary services** | Reduce attack surface |
| **Port security** | Limit MAC addresses per switch port |
| **DHCP snooping** | Block rogue DHCP servers |
| **Dynamic ARP Inspection** | Validate ARP packets |
| **IP source guard** | Prevent IP spoofing |
| **Private VLANs** | Isolate ports within same VLAN |
| **Storm control** | Limit broadcast/multicast/unknown-unicast traffic |
| **BPDU guard** | Disable port if spanning tree BPDU received (prevents rogue switch) |
| **Root guard** | Prevent port from becoming root bridge |
| **Change default passwords** | Common attack vector |
| **Patch management** | Fix known vulnerabilities |
| **Network segmentation** | Limit blast radius of a breach |

**Port security violation modes:**
- **Protect:** Drops traffic from unknown MAC (no log)
- **Restrict:** Drops traffic + logs + SNMP trap
- **Shutdown:** Disables port (errdisable) — most secure

### 5.6 Remote Access Security

- **VPN:** Encrypted tunnel (IPsec, SSL/TLS)
- **RDP over VPN:** Never expose RDP (3389) directly to internet
- **SSH instead of Telnet:** SSH encrypts all traffic
- **Jump box / Bastion host:** Single hardened entry point for admin access
- **Out-of-band management:** Separate management network (iLO, iDRAC, IPMI)
- **Console server:** Serial access to devices (e.g., OpenGear, Cisco 2500 series)

### 5.7 Physical Security

| Control | Description |
|---|---|
| **Door locks** | Electronic, biometric, or keyed |
| **Mantrap** | Two interlocking doors |
| **CCTV** | Video surveillance |
| **Access badges** | RFID proximity cards |
| **Server locks** | Rack locks, cable locks |
| **Smart locker** | Controlled equipment access |
| **Environmental** | HVAC, fire suppression, humidity control |

---

## 6. Domain 5: Network Troubleshooting (22%)

### 6.1 Troubleshooting Methodology

**CompTIA's 7-Step Methodology:**

```
1. Identify the problem
   └─ Gather information (user reports, symptoms, logs)
   └─ Duplicate the problem if possible
   └─ Determine scope (one user? one device? whole network?)

2. Establish a theory of probable cause
   └─ Question the obvious (is it plugged in? powered on?)
   └─ Think through layers (Physical → Data Link → Network → ...)

3. Test the theory to determine the cause
   └─ If theory confirmed → determine next steps
   └─ If theory not confirmed → re-establish new theory

4. Establish a plan of action and identify potential effects
   └─ What's the rollback plan? Change control needed?

5. Implement the solution or escalate

6. Verify full system functionality
   └─ Ask user: "Is it working now?"
   └─ Check related systems weren't affected

7. Document findings, actions, and outcomes
   └─ Update knowledge base, close ticket
```

### 6.2 Troubleshooting Tools

#### Command-Line Tools

| Command | OS | Function |
|---|---|---|
| `ping` | All | Tests basic connectivity (ICMP echo) |
| `tracert` (Windows) / `traceroute` (Linux/Mac) | All | Shows path to destination (ICMP TTL) |
| `ipconfig` (Windows) / `ifconfig` (Linux) | All | IP configuration |
| `nslookup` / `dig` | All | DNS queries |
| `arp -a` | All | View ARP cache |
| `netstat -an` | All | Active connections & listening ports |
| `pathping` | Windows | ping + traceroute combined with latency stats |
| `route print` (Windows) / `route -n` (Linux) | All | View routing table |
| `tcpdump` / `tshark` | Linux | Packet capture (CLI) |
| `nmap` | All | Port scanning, OS detection |
| `iperf3` | All | Bandwidth throughput testing |

#### Hardware Tools

| Tool | Function |
|---|---|
| **Cable tester** | Tests continuity, wiring map, shorts |
| **TDR (Time Domain Reflectometer)** | Locates cable breaks/faults (copper) |
| **OTDR (Optical TDR)** | Locates breaks in fiber, measures length |
| **Toner & probe** | Identifies specific cable in a bundle |
| **Loopback plug** | Tests NIC/port by looping TX to RX |
| **Multimeter** | Measures voltage, continuity, resistance |
| **Wi-Fi analyzer** | Measures signal strength, channel interference |
| **Spectrum analyzer** | Identifies interference sources (RF) |
| **Protocol analyzer** | Full packet capture & decode (Wireshark) |
| **PoE tester** | Verifies PoE voltage/wattage |

### 6.3 Common Network Issues & Solutions

#### Physical Layer Issues

| Symptom | Potential Cause | Solution |
|---|---|---|
| No connectivity | Damaged cable, wrong cable type | Replace cable, use correct type |
| Intermittent drops | Loose connection, interference | Re-seat connectors, replace cable |
| Link light off | Power issue, bad port | Check power, test known-good port |
| Data errors (CRC) | Crosstalk, cable too long, bad termination | Replace/rerun cable, check length |
| Bent pins in RJ-45 | Physical damage | Re-terminate connector |
| Wrong cable type (straight vs crossover) | Mismatched devices | Auto-MDIX handles most cases now |
| Attenuation | Cable too long (>100m) | Add switch/repeater, use fiber |

#### Data Link Layer Issues

| Symptom | Potential Cause | Solution |
|---|---|---|
| Can't reach specific VLAN | Trunk misconfig, native VLAN mismatch | Verify allowed VLANs on trunk |
| Slow performance | Broadcast storm, STP loop | Configure STP, portfast, storm control |
| Duplicate MAC / IP | Misconfigured device | Find and reconfigure or remove rogue device |
| Switch port flapping | Bad cable, duplex mismatch | Fix cable, set auto-negotiation |
| Connectivity only when jiggling cable | Bad termination or female port | Re-terminate, replace cable |

#### Network Layer Issues

| Symptom | Potential Cause | Solution |
|---|---|---|
| Can ping by IP but not name | DNS issue | Check DNS server, hosts file |
| Can't reach internet | Wrong default gateway, no route | Verify gateway IP and routing table |
| Intermittent connectivity | Duplicate IP, IP conflict | Use DHCP reservations, check `arp -a` |
| One-way traffic | Misconfigured firewall ACL | Review ACLs, check logs |
| Can't reach external network | NAT misconfigured | Verify NAT rules on router/firewall |
| Traceroute shows `* * *` at specific hop | Firewall blocking ICMP | Usually normal (admin blocks ICMP) |

#### Transport Layer Issues

| Symptom | Potential Cause | Solution |
|---|---|---|
| Specific app won't work | Port blocked by firewall | Allow port in firewall rule |
| TCP connections timeout | Firewall not allowing return traffic | Check stateful firewall rules |
| Application slow | TCP window scaling, congestion | Check window size, QoS settings |
| Connection refused | Service not running on port | Start service, check bindings |

#### DNS Issues

| Symptom | Potential Cause | Solution |
|---|---|---|
| "Server not found" in browser | DNS resolution failed | `nslookup` to test, check DNS server config |
| Wrong site loads | DNS cache poisoning | Flush DNS cache, implement DNSSEC |
| Can ping by hostname internally but not websites | DNS resolver config missing | Set proper DNS server (e.g., 8.8.8.8) |
| Old info appearing | Stale DNS cache | `ipconfig /flushdns` |

#### Wireless Issues

| Symptom | Potential Cause | Solution |
|---|---|---|
| Intermittent disconnects | Channel interference, signal weak | Change channel, move AP, add AP |
| Slow speeds | Too many clients, co-channel interference | Add APs, use 5 GHz band |
| Can connect but no internet | Wrong gateway/DNS on DHCP scope | Fix DHCP scope options |
| Can see SSID but can't connect | Wrong security type or password | Verify PSK or 802.1X config |
| Hidden SSID not appearing | Client doesn't probe for hidden networks | Manually configure SSID on client |
| Authentication errors | RADIUS server unreachable | Check RADIUS server and shared secret |
| Roaming drops | Sticky client, weak overlap | Adjust AP power, enable fast roaming (802.11r) |

> **Real-world example:** Users in the conference room report slow Wi-Fi. A spectrum analyzer shows channel 6 is congested with 8 neighboring APs. You change the APs to channels 1 and 11 (5 GHz band for high-density areas), and speeds improve immediately.

### 6.4 Troubleshooting Scenarios (PBQ-Style)

#### Scenario 1: Office Can't Reach Internet
- Users can ping each other within the office (192.168.1.0/24)
- Can't ping 8.8.8.8
- Can't browse websites
- **Check order:**
  1. Can you ping the default gateway (192.168.1.1)? If no → switch/router issue
  2. Can you ping an external IP (8.8.8.8)? If yes → DNS issue
  3. `ipconfig /all` — verify gateway and DNS settings
  4. Check firewall logs — is outbound traffic blocked?
  5. `tracert 8.8.8.8` — where does the path stop?
  6. Check ISP status

#### Scenario 2: VoIP Phones Not Working
- Phones register but calls drop intermittently
- Data traffic is fine
- **Check order:**
  1. QoS — is voice traffic prioritized? (DSCP EF = 46)
  2. Jitter and latency — VoIP needs < 150ms latency, < 30ms jitter
  3. Bandwidth — is the WAN link saturated?
  4. PoE — is the switch providing enough power?
  5. VLAN — is voice VLAN configured correctly?
  6. DHCP options — Option 150 (TFTP server) correct?

#### Scenario 3: Cannot RDP to Server (3389)
- Server is on VLAN 50, user is on VLAN 10
- `ping` to server works
- Telnet to 3389 fails (or `Test-NetConnection` on Windows)
- **Check order:**
  1. Is RDP enabled on the server?
  2. Is Windows Firewall allowing 3389 on the server?
  3. Is there a firewall ACL between VLANs blocking 3389?
  4. Is the RDP service running?
  5. Check if server has enough available sessions (licensing)

#### Scenario 4: New Switch Not Communicating
- New switch connected to core switch
- Port shows up/up but no traffic passes
- **Check order:**
  1. Is port in the correct VLAN on both ends?
  2. Trunk configuration — are allowed VLANs correct?
  3. Native VLAN mismatch
  4. STP — is port in blocking state? (show spanning-tree)
  5. Port security — is the switch MAC being dropped?
  6. Duplex mismatch — both end set to auto-negotiate?

#### Scenario 5: Client Gets 169.254.x.x IP
- `ipconfig` shows 169.254.x.x (APIPA)
- **Check order:**
  1. Is the DHCP server running?
  2. Is the client on the correct VLAN that has DHCP?
  3. Is DHCP snooping blocking the DHCP offer?
  4. Is there a rogue DHCP server causing issues?
  5. Is the switchport in the correct access VLAN?
  6. Is the DHCP scope exhausted? (check lease count)

---

## 7. Practice Questions & Scenarios

### 7.1 Multiple Choice Questions

**Q1:** A network technician receives a report that users in the Sales department cannot access the corporate file server. Users in other departments have no issues. Which troubleshooting step should the technician take FIRST?

a) Reboot the file server  
b) Check if the Sales VLAN is configured correctly on the switch  
c) Replace the network cable on the file server  
d) Run `ipconfig /renew` on all Sales computers  

<details>
<summary>Answer</summary>
**b) Check if the Sales VLAN is configured correctly on the switch** — The scope (only Sales affected) suggests a VLAN or routing issue specific to that department.
</details>

**Q2:** Which of the following is the PRIMARY benefit of using VLANs in a network?

a) Increase available bandwidth  
b) Improve security through network segmentation  
c) Reduce the number of switches needed  
d) Eliminate the need for routing  

<details>
<summary>Answer</summary>
**b) Improve security through network segmentation** — VLANs logically separate traffic, reducing broadcast domains and improving security.
</details>

**Q3:** A user reports that their computer has an IP address of 169.254.25.100. What is the MOST likely cause?

a) The computer has a static IP configured  
b) The DHCP server is unavailable  
c) The DNS server is down  
d) The default gateway is misconfigured  

<details>
<summary>Answer</summary>
**b) The DHCP server is unavailable** — 169.254.x.x is APIPA, assigned when DHCP fails.
</details>

**Q4:** A network engineer needs to connect two switches across a distance of 5 km. Which cable type is MOST appropriate?

a) Cat 6a copper  
b) Multimode fiber  
c) Singlemode fiber  
d) Cat 8 copper  

<details>
<summary>Answer</summary>
**c) Singlemode fiber** — Only singlemode fiber supports 5 km distances (multimode maxes out at ~2 km; copper maxes at 100m).
</details>

**Q5:** A company wants to provide secure remote access for employees. Which protocol combination provides encrypted authentication AND encrypted data transmission?

a) Telnet with SSH  
b) RADIUS with LDAP  
c) IPsec with SSL/TLS  
d) SNMPv2c with community strings  

<details>
<summary>Answer</summary>
**c) IPsec with SSL/TLS** — Both provide encrypted data transmission. Telnet is unencrypted; RADIUS and LDAP don't encrypt the data stream; SNMPv2c sends community strings in plain text.
</details>

**Q6:** A switch configuration includes the following: `switchport port-security maximum 1` `switchport port-security violation shutdown`. What is the effect?

a) Allows one MAC address; shuts down the port if exceeded  
b) Limits the port to one packet per second  
c) Allows unlimited MACs but logs violations  
d) Shuts down the switch if more than one MAC is seen  

<details>
<summary>Answer</summary>
**a) Allows one MAC address; shuts down the port if exceeded** — Port security limits MACs per port; shutdown mode disables the port (errdisable) on violation.
</details>

**Q7:** Which of the following is a characteristic of UDP?

a) Guaranteed delivery  
b) Sequence numbers  
c) Connectionless communication  
d) Windowing and flow control  

<details>
<summary>Answer</summary>
**c) Connectionless communication** — UDP is connectionless (no handshake, no ACKs, no ordering).
</details>

**Q8:** A network admin needs to implement a solution that prevents unauthorized devices from connecting to the wired network until they pass a security compliance check. Which technology should be used?

a) 802.1X  
b) 802.11ac  
c) 802.3ad  
d) 802.1Q  

<details>
<summary>Answer</summary>
**a) 802.1X** — Port-based NAC that authenticates devices before granting network access.
</details>

**Q9:** Which of the following is used to prevent switching loops?

a) OSPF  
b) STP  
c) VLAN  
d) NAT  

<details>
<summary>Answer</summary>
**b) STP (Spanning Tree Protocol)** — Prevents loops in redundant switched networks.
</details>

**Q10:** An office has a 192.168.1.0/24 network with 10 usable IPs remaining. Which subnet mask would create the MOST additional subnets while still supporting at least 20 hosts per subnet?

a) /24  
b) /25  
c) /26  
d) /27  

<details>
<summary>Answer</summary>
**d) /27** — /27 = 255.255.255.224 = 30 hosts per subnet (6 subnets from /24). /26 = 62 hosts but only 2 subnets. /25 = 126 hosts but 2 subnets. /28 = 14 hosts, not enough. /27 is the smallest that meets "at least 20 hosts."
</details>

### 7.2 Performance-Based Question (PBQ) Examples

**PBQ 1: Network Topology**

You are given a diagram showing:
- 1 Router connected to ISP
- 2 Switches (Switch-A and Switch-B) connected to the router
- 10 PCs connected to Switch-A
- 1 Server connected to Switch-B
- 1 Printer connected to Switch-A

Tasks:
1. Identify which devices are in the same broadcast domain
2. Identify collision domains
3. If a PC sends a broadcast, which devices receive it?

<details>
<summary>Answer</summary>
1. All devices on Switch-A are in the same broadcast domain; all devices on Switch-B are in a separate broadcast domain (router separates broadcast domains).
2. Each switch port is its own collision domain (20 total = 12 switch ports in use + 1 router port + 1 uplink port).
3. Only devices connected to Switch-A (all 10 PCs + printer) and Switch-A itself receive the broadcast. Router does not forward broadcasts.
</details>

**PBQ 2: Cable Selection**

Match the scenario to the correct cable type:

| Scenario | Cable |
|---|---|
| A. Connect a desktop to a wall jack 50m away | 1. Cat 6a |
| B. Connect two data centers 40km apart | 2. Singlemode fiber |
| C. Connect server to switch at 10 Gbps, 30m | 3. Cat 5e |
| D. Connect a PoE security camera (100m, 1 Gbps) | 4. Cat 6 |

<details>
<summary>Answer</summary>
A → 3 (Cat 5e supports 1 Gbps to 100m for desktop use)  
B → 2 (Single mode fiber supports long distances)  
C → 1 (Cat 6a supports 10 Gbps to 100m)  
D → 4 (Cat 6 supports 1 Gbps to 100m with PoE)
</details>

---

## 8. Exam Day Tips

### Before the Exam
- **Sleep well** — 8 hours minimum
- **Eat lightly** — protein, not sugar
- **Arrive early** — 30 minutes before
- **Bring:** Two forms of ID (one photo), confirmation email
- **No:** Phone, smartwatch, bags, notes, calculator (on-screen)

### During the Exam
- **Flag tough questions** — skip and return later
- **PBQs:** Do them last (they take the most time)
- **Read twice** — CompTIA loves negative questions ("Which is NOT...")
- **Process of elimination** — remove two wrong answers, pick the best of two
- **Watch for "BEST" or "MOST"** — more than one answer may be technically correct
- **Time management:** ~1 minute per question; PBQs get 3–5 minutes

### Topics That Frequently Trip People Up
- Subnetting (practice until it's instant)
- STP port states and roles
- OSI layer identification for protocols
- Wireless standards (frequencies, speeds)
- Firewall rules (implicit deny)
- Port numbers (especially obscure ones)
- DNS record types
- SNMP versions and security
- Authentication protocols (RADIUS vs TACACS+)
- Crossover vs straight-through cable use cases

### After the Exam
- If you pass — congratulations! Download your certificate from CompTIA.
- If you fail — review your score report, study weak domains, retake after 14 days.

---

## 9. Resources & Labs

### Free Resources
- **Professor Messer** — Free N10-009 video series (YouTube)
- **CompTIA N10-009 Objectives PDF** — Official exam objectives
- **Subnetting Practice:** subnettingpractice.com
- **Wireshark** — Packet analysis tool (wireshark.org)
- **Packet Tracer** — Cisco network simulator (free with Cisco NetAcad account)

### Recommended Study Tools
- **Packet Tracer** — Practice routing, switching, VLANs, ACLs
- **GNS3 / EVE-NG** — Advanced network emulation (real router images)
- **Wireshark** — See how protocols actually work on the wire
- **VirtualBox** — Build virtual networks with Linux VMs
- **AWS Free Tier** — Practice cloud networking (VPC, subnets, security groups)

### Home Lab Ideas
- Buy 2–3 used Cisco switches (e.g., 2960s, $20–50 each on eBay)
- Buy 1 used Cisco router (e.g., 1841 or 891)
- Connect and configure: VLANs, trunking, STP, inter-VLAN routing, ACLs
- Add a Raspberry Pi as a DHCP/DNS server, web server, or syslog server

### Exam Registration
- **Website:** certmetrics.com/comptia
- **Options:** In-person (Pearson VUE) or online proctored
- **Voucher discounts:** Check your school, employer, or CompTIA Academic Marketplace

---

> **Final word:** Network+ is the most practical entry-level cert in IT. It teaches you how the internet actually works — from electrons flowing through copper to BGP routing across continents. Master these concepts, and you understand the backbone of every modern business. **Good luck.**
