# CompTIA A+ 220-1201 — Week 1 Day 3 Notes

---

## Videos Watched
- ✅ 2.1 Common Network Ports
- ✅ 2.2 Wireless Network Technologies
- ✅ 2.3 Network Services

---

## Key Concepts

### 2.1 Common Network Ports

> Important for firewall rules and port-based security. You need to know the port number, protocol (TCP/UDP), and what the protocol is used for.

#### Email Protocols
| Protocol | Port | Description |
|---|---|---|
| **SMTP** | TCP/25 | Simple Mail Transfer Protocol — sends email |
| **POP3** | TCP/110 | Post Office Protocol v3 — downloads email to one device |
| **IMAP4** | TCP/143 | Internet Message Access Protocol v4 — access email from multiple devices |

#### File Transfer
| Protocol | Port | Description |
|---|---|---|
| **FTP** | TCP/20 (data), TCP/21 (control) | File Transfer Protocol — list, add, delete files. Requires authentication |
| **SMB/CIFS** | TCP/445 | Server Message Block — Microsoft file and printer sharing. Also called Common Internet File System |

#### Remote Access
| Protocol | Port | Description |
|---|---|---|
| **SSH** | TCP/22 | Secure Shell — encrypted remote login. Looks and acts like Telnet but encrypted |
| **Telnet** | TCP/23 | Telecommunication Network — remote login but NO encryption, data sent in the clear |
| **RDP** | TCP/3389 | Remote Desktop Protocol — graphical remote access to Windows machines |

#### Web
| Protocol | Port | Description |
|---|---|---|
| **HTTP** | TCP/80 | Hypertext Transfer Protocol — web browsing, unencrypted |
| **HTTPS** | TCP/443 | HTTP Secure — web browsing with encryption |

#### Network Services
| Protocol | Port | Description |
|---|---|---|
| **DNS** | UDP/53 | Domain Name System — converts domain names to IP addresses. Critical resource with multiple servers for redundancy |
| **DHCP** | UDP/67, UDP/68 | Dynamic Host Configuration Protocol — automatically assigns IP address, subnet mask and other options |
| **LDAP** | TCP/389 | Lightweight Directory Access Protocol — commonly used in Microsoft Active Directory |

#### Legacy Windows (NetBIOS)
| Protocol | Port | Description |
|---|---|---|
| **NetBT** | UDP/137 | NetBIOS Name Service — older Windows name resolution |
| **NetBT** | TCP/139 | NetBIOS Session Service — older Windows file sharing |
| **SMB direct** | TCP/445 | Modern Windows file sharing without NetBIOS |

#### Full Port Reference Table
| Port | Protocol | Service |
|---|---|---|
| 20/21 | TCP | FTP |
| 22 | TCP | SSH |
| 23 | TCP | Telnet |
| 25 | TCP | SMTP |
| 53 | UDP | DNS |
| 67/68 | UDP | DHCP |
| 80 | TCP | HTTP |
| 110 | TCP | POP3 |
| 139 | TCP | NetBIOS |
| 143 | TCP | IMAP4 |
| 389 | TCP | LDAP |
| 443 | TCP | HTTPS |
| 445 | TCP | SMB |
| 3389 | TCP | RDP |

---

### 2.2 Wireless Network Technologies

#### IEEE 802.11 Standards
- **IEEE** — Institute of Electrical and Electronics Engineers
- **802.11** — the committee responsible for wireless networking standards

| Standard | Wi-Fi Name | Frequency |
|---|---|---|
| 802.11ac | Wi-Fi 5 | 5 GHz |
| 802.11ax | Wi-Fi 6 / Wi-Fi 6E (extended) | 2.4, 5, 6 GHz |
| 802.11be | Wi-Fi 7 | 2.4, 5, 6 GHz |

- Frequencies: **2.4 GHz**, **5 GHz**, **6 GHz**
- Frequencies are grouped into **channels**
  - Example: Channel 6 = 2.4 GHz, Channel 44 = 5 GHz
- **2.4 GHz** — longer range, more interference, slower
- **5 GHz** — shorter range, less interference, faster

#### Bluetooth
- Uses **2.4 GHz** frequency range
- **Unlicensed ISM** (Industrial, Scientific, Medical) band
- Short range **PAN** (Personal Area Network)
- Used for: headsets, speakers, keyboards, mice

#### RFID — Radio Frequency Identification
- Used to track anything (inventory, assets, access cards)
- Based on **radar technology**
- Radio energy is transmitted to a tag → RF powers the tag → tag transmits ID back
- **Bidirectional communication**
- Some tags are **active** (have their own power source)
- Some tags are **passive** (powered by the reader's radio signal)

#### NFC — Near Field Communication
- Builds on top of RFID technology
- Very short range (a few centimeters)
- Used for: **payment systems** (tap to pay), **bootstrapping** other wireless connections
- Example: tap phone to speaker to initiate Bluetooth pairing

---

### 2.3 Network Services

#### Core Network Services
| Service | Description |
|---|---|
| **DNS Server** | Converts domain names to IP addresses and vice versa. Distributed system, usually managed by ISP |
| **DHCP Server** | Automatically assigns IP addresses. Enterprises have DHCP redundancy for reliability |
| **File Server** | Centralized document storage using SMB (Windows), AFP (Apple Filing Protocol) |
| **Print Server** | Built into printer or software. Uses SMB, IPP (Internet Printing Protocol), LPD (Line Printer Daemon) |
| **Mail Server** | Handles sending and receiving email |
| **Web Server** | Serves web pages using HTTP/HTTPS. Built with HTML/HTML5 |
| **NTP Server** | Network Time Protocol — keeps all devices on the same time. Critical for log files, encryption, and logins |
| **Database Server** | Stores data in rows and columns (relational database). Uses SQL (Structured Query Language) to link tables |

#### Security Services
| Service | Description |
|---|---|
| **Authentication Server** | Handles AAA — Authentication, Authorization, Accounting |
| **Syslog Server** | Standard for message logging. Central logging receiver acts as a **SIEM** (Security Information and Event Manager) |
| **Spam Gateway** | Filters unsolicited email before it reaches users |
| **All-in-one Security Appliance** | Combines Next Generation Firewall + **UTM** (Unified Threat Management) |
| **Proxy Server** | Intermediate server — user sends request to proxy → proxy forwards to destination → checks response → sends back to user |

#### Load Balancing
- Distributes traffic across **multiple servers**
- **Invisible to end user**
- Provides **fault tolerance** — if one server fails, others keep working
- Used in large-scale applications (websites, enterprise apps)

#### Specialized Systems
| System | Description |
|---|---|
| **SCADA/ICS** | Supervisory Control and Data Acquisition — controls industrial equipment (power plants, factories) |
| **Legacy Systems** | Very old but still critical systems — hard to update or replace |
| **Embedded Systems** | Computers built into devices (medical equipment, cars) |
| **IoT** | Internet of Things — everyday devices connected to the internet (smart TVs, cameras, thermostats) |

---

## TryHackMe — Intro to LAN

### Network Topologies
> A **topology** refers to the design or layout of a network

| Topology | Description | Pros | Cons |
|---|---|---|---|
| **Star** | All devices connect to a central switch/hub | Easy to add devices, reliable | If central switch fails, whole network fails |
| **Bus** | All devices share one cable | Simple, cheap | One break = whole network down |
| **Ring** | Devices connected in a circle, data travels one direction | Predictable traffic | One failure breaks the ring |

### Key Network Devices

#### Switch
- Dedicated device that connects multiple devices together using Ethernet
- Available with 4, 8, 16, 24, 32, or 64 ports
- Found in businesses, schools, larger networks
- **Smarter than a hub** — sends data only to the intended device, not everyone

#### Router
- Connects **different networks** together and passes data between them
- Uses **routing** to determine the best path for data
- Example: connects your home network to the internet

### 🔑 Additional Important Concepts You Missed

#### Hub vs Switch
- **Hub** — sends data to ALL connected devices (dumb, old technology)
- **Switch** — sends data only to the **intended** device (smart, modern)
- Switches are always preferred over hubs for security and efficiency

#### MAC Address Table
- Switches keep a **MAC address table** to know which device is on which port
- This is how they know exactly where to send data

#### Subnetting Basics
- Divides a large network into smaller networks
- Each subnet has its own **network address** and **broadcast address**
- Example: 192.168.1.0/24 means 256 possible addresses (0-255)

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. SSH (port 22) is encrypted, Telnet (port 23) is identical but completely unencrypted — never use Telnet
2. RFID powers passive tags with radio energy — no battery needed in the tag itself
3. Switches are smarter than hubs — they send data only to the intended device, not everyone