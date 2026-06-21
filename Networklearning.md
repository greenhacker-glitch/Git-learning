<p align="center">
  <img src="https://img.shields.io/badge/CompTIA-Network%2B-00529B?style=for-the-badge&logo=comptia&logoColor=white" alt="CompTIA Network+"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Exam-N10--009-blue?style=flat-square" alt="Exam Code"/>
  <img src="https://img.shields.io/badge/Questions-Up%20to%2090-green?style=flat-square" alt="Questions"/>
  <img src="https://img.shields.io/badge/Time-90%20Minutes-orange?style=flat-square" alt="Time"/>
  <img src="https://img.shields.io/badge/Passing%20Score-720%2F900-red?style=flat-square" alt="Passing Score"/>
</p>

---

# 📚 CompTIA Network+ Learning Path

> A structured, step-by-step guide to mastering the **CompTIA Network+ (N10-009)** certification — from fundamentals to troubleshooting.

---

## 📋 Table of Contents

| # | Phase | Description |
|---|-------|-------------|
| 1 | 🌐 [Networking Fundamentals](#-phase-1--networking-fundamentals) | OSI model, protocols, IP addressing |
| 2 | ⚙️ [Network Implementations](#%EF%B8%8F-phase-2--network-implementations) | Switching, routing, wireless, WAN |
| 3 | 📊 [Network Operations & Monitoring](#-phase-3--network-operations--monitoring) | Documentation, monitoring, metrics |
| 4 | 🔒 [Network Security](#-phase-4--network-security) | Threats, hardening, VPNs, access control |
| 5 | 🔧 [Network Troubleshooting](#-phase-5--network-troubleshooting) | Methodology, tools, common issues |
| — | 📖 [Resources](#-recommended-resources) | Books, videos, practice exams, labs |
| — | 💡 [Study Tips](#-study-tips) | Exam strategy and quick references |

---

## 🌐 Phase 1 — Networking Fundamentals

<table>
<tr>
<td width="70%">

### OSI Model
> Memorize all **7 layers**, what each does, and which protocols/devices live there.

| Layer | Name | Key Protocols/Devices |
|:-----:|------|----------------------|
| **7** | Application | HTTP, FTP, SMTP, DNS |
| **6** | Presentation | SSL/TLS, JPEG, ASCII |
| **5** | Session | NetBIOS, PPTP |
| **4** | Transport | TCP, UDP |
| **3** | Network | IP, ICMP, Routers |
| **2** | Data Link | Ethernet, MAC, Switches |
| **1** | Physical | Cables, Hubs, NICs |

### TCP/IP Model
Maps directly to the OSI model in **4 layers**:

| TCP/IP Layer | OSI Equivalent |
|:------------:|:--------------:|
| Application | Layers 5–7 |
| Transport | Layer 4 |
| Internet | Layer 3 |
| Network Access | Layers 1–2 |

</td>
<td width="30%">

### 📌 Key Protocols

- ✅ HTTP / HTTPS
- ✅ DNS
- ✅ DHCP
- ✅ FTP / SFTP
- ✅ SMTP / POP3 / IMAP
- ✅ SNMP
- ✅ SSH / Telnet
- ✅ ICMP

### 🔌 Must-Know Ports

| Port | Protocol |
|:----:|----------|
| 21 | FTP |
| 22 | SSH |
| 23 | Telnet |
| 25 | SMTP |
| 53 | DNS |
| 67/68 | DHCP |
| 80 | HTTP |
| 110 | POP3 |
| 143 | IMAP |
| 443 | HTTPS |
| 993 | IMAPS |
| 995 | POP3S |
| 3389 | RDP |

</td>
</tr>
</table>

### 🧮 IP Addressing

| Topic | What to Learn |
|-------|--------------|
| **IPv4 Subnetting** | CIDR notation, VLSM, subnet masks, network/broadcast addresses |
| **IPv6 Basics** | Address types (link-local, global, unique-local), dual-stack, tunneling |
| **NAT** | Static, dynamic, PAT (port address translation) |

---

## ⚙️ Phase 2 — Network Implementations

<table>
<tr>
<td width="50%">

### 🔀 Switching

- **VLANs** — logical segmentation, VLAN IDs 1–4094
- **Trunking** — 802.1Q tagging between switches
- **STP** — Spanning Tree Protocol, prevent loops
- **LACP** — Link Aggregation for bandwidth
- **MAC Address Tables** — how switches learn & forward

### 🚦 Routing

- **Static Routing** — manually configured routes
- **Dynamic Routing** — auto-learned via protocols
- **OSPF** — link-state, fast convergence
- **EIGRP** — Cisco proprietary, hybrid
- **BGP** — path-vector, internet backbone
- **Administrative Distance** — trust hierarchy

</td>
<td width="50%">

### 📡 Wireless

| Standard | Frequency | Max Speed |
|----------|:---------:|:---------:|
| 802.11a | 5 GHz | 54 Mbps |
| 802.11b | 2.4 GHz | 11 Mbps |
| 802.11g | 2.4 GHz | 54 Mbps |
| 802.11n | 2.4/5 GHz | 600 Mbps |
| 802.11ac | 5 GHz | 6.9 Gbps |
| 802.11ax | 2.4/5/6 GHz | 9.6 Gbps |

**Also learn:**
- Channel selection & interference
- Site surveys & heat maps
- WPA2 vs WPA3 encryption

### 🌍 WAN Technologies

- **MPLS** — label-switched paths
- **SD-WAN** — software-defined WAN
- **Broadband** — cable, DSL, fiber
- **Leased Lines** — dedicated bandwidth
- **PPPoE** — Point-to-Point over Ethernet

</td>
</tr>
</table>

---

## 📊 Phase 3 — Network Operations & Monitoring

<table>
<tr>
<td width="50%">

### 📝 Network Documentation

- Network diagrams (logical & physical)
- IP Address Management (IPAM)
- Asset management & inventory
- Change management procedures

### 📈 Monitoring Tools

| Tool | Purpose |
|------|---------|
| **SNMP** | Device polling & traps |
| **Syslog** | Centralized log aggregation |
| **NetFlow** | Traffic analysis |
| **SIEM** | Security event correlation |

</td>
<td width="50%">

### 📉 Performance Metrics

| Metric | Description |
|--------|-------------|
| **Bandwidth** | Maximum capacity |
| **Throughput** | Actual transfer rate |
| **Latency** | Round-trip delay |
| **Jitter** | Variation in latency |
| **Packet Loss** | Dropped packets % |

### 💾 Backup & Recovery

- Snapshots & incremental backups
- Disaster recovery planning
- Redundancy concepts (failover, clustering)
- RPO & RTO objectives

</td>
</tr>
</table>

---

## 🔒 Phase 4 — Network Security

<table>
<tr>
<td width="50%">

### ⚠️ Common Threats

| Threat | Description |
|--------|-------------|
| **DoS / DDoS** | Overwhelm resources |
| **MITM** | Intercept communication |
| **Phishing** | Social engineering |
| **VLAN Hopping** | Bypass VLAN segmentation |
| **ARP Spoofing** | Redirect traffic via fake ARP |

</td>
<td width="50%">

### 🛡️ Security Hardening

| Control | Purpose |
|---------|---------|
| **Port Security** | Limit MAC per port |
| **802.1X** | Port-based authentication |
| **NAC** | Network Access Control |
| **Firewalls** | Stateful vs stateless filtering |
| **IDS/IPS** | Detect & prevent intrusions |

</td>
</tr>
<tr>
<td width="50%">

### 🔐 VPN Technologies

- **Site-to-Site** — connects entire networks
- **Client-to-Site** — remote access
- **IPsec** — Layer 3 encryption (AH, ESP)
- **SSL/TLS VPN** — browser-based access
- **Split Tunneling** — partial traffic routing

</td>
<td width="50%">

### 🎫 Access Control

| Method | Description |
|--------|-------------|
| **RADIUS** | AAA over UDP 1812/1813 |
| **TACACS+** | Cisco AAA over TCP 49 |
| **LDAP** | Directory authentication |
| **MFA** | Multi-factor (something you have/know/are) |

</td>
</tr>
</table>

---

## 🔧 Phase 5 — Network Troubleshooting

### 📋 Methodology

```
┌─────────────┐    ┌──────────────┐    ┌─────────────┐    ┌──────────────┐
│  1. IDENTIFY │───▶│ 2. ESTABLISH │───▶│  3. TEST    │───▶│ 4. IMPLEMENT │
│    the issue │    │    theory    │    │  the theory │    │   solution   │
└─────────────┘    └──────────────┘    └─────────────┘    └──────┬───────┘
                                                                 │
┌─────────────┐    ┌──────────────┐                               │
│ 6. DOCUMENT │◀───│  5. VERIFY   │◀──────────────────────────────┘
│   findings  │    │ functionality│
└─────────────┘    └──────────────┘
```

### 🧰 Essential Tools

| Tool | Command Example | Purpose |
|------|----------------|---------|
| **ping** | `ping 8.8.8.8` | Test connectivity |
| **traceroute** | `traceroute google.com` | Map packet path |
| **nslookup** | `nslookup domain.com` | DNS lookup |
| **dig** | `dig domain.com A` | Detailed DNS query |
| **netstat** | `netstat -an` | Active connections |
| **arp** | `arp -a` | ARP cache table |
| **tcpdump** | `tcpdump -i eth0` | Packet capture (CLI) |
| **Wireshark** | GUI-based | Deep packet analysis |
| **nmap** | `nmap -sV 192.168.1.0/24` | Network scanning |

### 🐛 Common Issues & Fixes

| Issue | Symptoms | Fix |
|-------|----------|-----|
| **DNS Failure** | Can ping IP, not hostname | Check DNS server config |
| **DHCP Exhaustion** | APIPA addresses (169.254.x.x) | Expand scope, check leases |
| **Duplex Mismatch** | Slow speeds, collisions | Force matching duplex on both ends |
| **Asymmetric Routing** | Intermittent connectivity | Check routing tables both directions |
| **MTU Black Hole** | Large packets drop | Adjust MTU, enable PMTUD |

---

## 📖 Recommended Resources

<table>
<tr>
<td width="50%">

### 📕 Books

- 📘 **CompTIA Network+ Study Guide** — *Todd Lammle (Sybex)*
- 📗 **CompTIA Network+ Certification All-in-One Exam Guide** — *Mike Meyers*
- 📙 **CompTIA Network+ Review Guide** — *Bill Ferguson*

</td>
<td width="50%">

### 🎥 Video Courses

- 🎬 **Professor Messer** — Free YouTube course ⭐
- 🎬 **Jason Dion** — Udemy (with practice exams)
- 🎬 **CBT Nuggets** — In-depth training

</td>
</tr>
<tr>
<td width="50%">

### 🧪 Hands-On Labs

- 🖥️ **Cisco Packet Tracer** — Free network simulator
- 🖥️ **GNS3** — Advanced network emulation
- 🖥️ **Boson NetSim** — Exam-focused labs

</td>
<td width="50%">

### 📝 Practice Exams

- ✅ **Jason Dion's Practice Exams** — Udemy ⭐
- ✅ **Boson ExSim** — Most realistic questions
- ✅ **ExamCompass** — Free online quizzes

</td>
</tr>
</table>

---

## 💡 Study Tips

<table>
<tr>
<td width="50%">

### 🎯 Subnetting Mastery

> Drill subnetting until you can calculate in **under 60 seconds**.
>
> 🌐 Practice at: `subnettingpractice.com`

</td>
<td width="50%">

### 💻 Command Line Proficiency

> Know every tool listed above, its flags, and
> when to use each one. Hands-on > memorization.

</td>
</tr>
<tr>
<td width="50%">

### 📝 Exam Format

> - Up to **90 questions**
> - **90 minutes** time limit
> - Mix of multiple-choice & **PBQs**
> - Passing score: **720 / 900**

</td>
<td width="50%">

### 📅 Study Schedule

> - **Weeks 1–3:** Fundamentals & IP addressing
> - **Weeks 4–6:** Implementations & routing
> - **Weeks 7–8:** Operations & security
> - **Weeks 9–10:** Troubleshooting & review
> - **Week 11:** Practice exams & weak areas

</td>
</tr>
</table>

---

<p align="center">

### 🏆 Good Luck on Your Network+ Journey!

<img src="https://img.shields.io/badge/You've%20got%20this!-💪-brightgreen?style=for-the-badge" alt="You got this!"/>

</p>
