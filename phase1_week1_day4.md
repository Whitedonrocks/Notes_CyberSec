# CompTIA A+ 220-1201 — Week 1 Day 4 Notes

---

## Videos Watched
- ✅ 2.4 DNS Configuration
- ✅ 2.4 DHCP
- ✅ 2.4 VLANs and VPNs
- ✅ 2.5 Network Devices

---

## Key Concepts

### 2.4 DNS — Domain Name System

#### What is DNS?
- Translates human-readable names into computer-readable IP addresses
- Example: `google.com` → `142.250.64.46`
- **Hierarchical** — follows a structured path from root down to the host
- **Distributed database** — no single server holds all records
- **13 root server clusters** (over 100 actual physical servers worldwide)
- Hundreds of generic top-level domains (gTLDs)
- Over 275 country code top-level domains (ccTLDs)

#### DNS Hierarchy Example
```
. (Root)
└── .com (Top-Level Domain / gTLD)
    └── google.com (Second-Level Domain)
        └── mail.google.com (Subdomain / Host)
```
```
. (Root)
└── .np (Country Code TLD — Nepal)
    └── .com.np
        └── worldlink.com.np
```

#### DNS Query Commands
```bash
# Linux — dig command
dig google.com          # basic query
dig google.com MX       # query mail records
dig google.com AAAA     # query IPv6 address
dig @8.8.8.8 google.com # query using specific DNS server (Google DNS)

# Windows — nslookup
nslookup google.com
nslookup -type=MX google.com
nslookup -type=AAAA google.com
```

#### Resource Records (RR)
> Over 30 record types exist. These are the most important ones:

---

#### A Record (IPv4 Address)
- Maps a hostname to an **IPv4** address
- Example:
```
google.com.     A     142.250.64.46
```
- **Cybersecurity use:** DNS A record lookup is the first step in recon on a target

#### AAAA Record (IPv6 Address)
- Maps a hostname to an **IPv6** address (Quad-A record)
- Example:
```
google.com.     AAAA     2607:f8b0:4004:c09::64
```
- **Cybersecurity use:** Many tools miss IPv6 during scanning — attackers can hide services here

#### CNAME Record (Canonical Name)
- Creates an **alias** that points to another hostname
- Example:
```
www.google.com.     CNAME     google.com.
shop.example.com.   CNAME     stores.shopify.com.
```
- **Use:** Redirecting subdomains without changing the real IP
- **Cybersecurity use:** CNAME takeover attacks — if the target domain expires, attacker registers it

#### MX Record (Mail Exchanger)
- Determines the **hostname of the mail server** for a domain
- Example:
```
google.com.     MX     10     smtp.google.com.
google.com.     MX     20     alt1.aspmx.l.google.com.
```
- The number (10, 20) is the **priority** — lower number = higher priority
- **Cybersecurity use:** Finding mail servers for phishing infrastructure recon

#### TXT Record (Text)
- Stores **human-readable text** — used for domain verification
- Example:
```
example.com.    TXT    "v=spf1 include:_spf.google.com ~all"
example.com.    TXT    "google-site-verification=abc123xyz"
```
- **Uses:** Domain ownership verification, SPF, DKIM, DMARC

#### DKIM — DomainKeys Identified Mail
- **Digitally signs** a domain's outgoing mail using a private key
- Receiving mail server checks the public key (stored in DNS) to verify the signature
- Example TXT record:
```
google._domainkey.example.com.    TXT    "v=DKIM1; k=rsa; p=MIGfMA0..."
```
- **Cybersecurity use:** Without DKIM, attackers can spoof emails from your domain

#### SPF — Sender Policy Framework
- Lists **all servers authorised to send email** for a domain
- Example:
```
example.com.    TXT    "v=spf1 ip4:192.168.1.0/24 include:sendgrid.net -all"
```
- `-all` means reject all other senders
- `~all` means soft fail (mark as spam but don't reject)
- **Cybersecurity use:** Prevents email spoofing — if no SPF, anyone can send as you

#### DMARC — Domain-based Message Authentication Reporting and Conformance
- Tells receiving servers **what to do** if SPF or DKIM checks fail
- Prevents unauthorised email use (spoofing)
- Example:
```
_dmarc.example.com.    TXT    "v=DMARC1; p=reject; rua=mailto:dmarc@example.com"
```
- `p=none` — monitor only
- `p=quarantine` — send to spam
- `p=reject` — block the email completely
- **Cybersecurity use:** DMARC misconfiguration = domain open to phishing attacks

> **DKIM + SPF + DMARC together = email authentication trinity. Without all three, your domain can be spoofed for phishing.**

---

### 2.4 DHCP — Dynamic Host Configuration Protocol

#### What is DHCP?
- Provides **automatic IP address configuration** — no manual setup needed
- Before DHCP, every IP had to be configured manually on every device
- Released in **1997**
- Provides: IP address, subnet mask, default gateway, DNS server, lease duration

#### DORA Process (How DHCP Works)
> Every time a device joins a network, it goes through DORA:

| Step | Name | Description |
|---|---|---|
| **D** | Discover | Client broadcasts: "Is there a DHCP server?" (UDP, from 0.0.0.0 to 255.255.255.255) |
| **O** | Offer | Server responds: "I can give you 192.168.1.50 for 24 hours" |
| **R** | Request | Client broadcasts: "Yes, I'll take 192.168.1.50 please" |
| **A** | Acknowledge | Server confirms: "192.168.1.50 is yours for 24 hours" |

**Example DORA in action:**
```
[Client]  →  DISCOVER  →  [Broadcast 255.255.255.255]
[Server]  →  OFFER     →  "Here is 192.168.1.50, lease 24hrs"
[Client]  →  REQUEST   →  "I accept 192.168.1.50"
[Server]  →  ACK       →  "Confirmed, it is yours until tomorrow"
```
- Uses **UDP/67** (server) and **UDP/68** (client)
- **Cybersecurity use:** Rogue DHCP attack — attacker runs fake DHCP server, assigns themselves as the default gateway → man-in-the-middle attack

#### DHCP Scopes
- **Predefined IP address range** the server can hand out
- Includes: subnet mask, lease duration, excluded addresses, gateway, DNS server
- Example scope:
```
Scope Name:     Office Network
Range:          192.168.1.1 - 192.168.1.254
Excluded:       192.168.1.1 - 192.168.1.20  (reserved for servers/printers)
Subnet Mask:    255.255.255.0
Default Gateway: 192.168.1.1
DNS Server:     8.8.8.8
Lease Duration: 8 hours
```

#### DHCP Pools
- **Grouping of IP addresses** available for assignment
- Usually one large contiguous pool with exclusions carved out
- Example pool:
```
Total pool:  192.168.1.0/24  (254 usable addresses)
Excluded:    192.168.1.1-20  (routers, servers, printers)
Available:   192.168.1.21-254  (233 addresses for clients)
```

#### Address Reservation (Static DHCP)
- Administratively configured — always gives the **same IP to the same device**
- Based on **MAC address** of the device
- Also called: DHCP reservation, static mapping, IP/MAC binding
- Example:
```
MAC Address:        AA:BB:CC:DD:EE:FF
Reserved IP:        192.168.1.25
Device Name:        Office-Printer
```
- **Cybersecurity use:** MAC spoofing can bypass reservations — attacker clones a known MAC to get a reserved IP

---

### 2.4 VLANs and VPNs

#### LAN — Local Area Network
- A group of devices in the **same broadcast domain**
- All devices can communicate directly without a router
- Example: all computers in one office floor

#### VLAN — Virtual LAN
- Devices in the **same broadcast domain separated logically** instead of physically
- Configured on managed switches using 802.1Q tagging
- Example without VLANs:
```
All departments on same network → HR can see Finance traffic
```
- Example with VLANs:
```
VLAN 10 → HR Department     (192.168.10.0/24)
VLAN 20 → Finance           (192.168.20.0/24)
VLAN 30 → IT                (192.168.30.0/24)
Traffic between VLANs requires a router or Layer 3 switch
```
- **Cybersecurity use:** VLAN hopping attack — attacker tricks a switch into giving access to another VLAN by sending double-tagged 802.1Q frames

#### VPN — Virtual Private Network
- **Encrypted private data** traversing a public network (the internet)
- Creates a secure tunnel between two endpoints
- Data looks encrypted to anyone intercepting it in the middle

#### VPN Concentrator
- Encryption and decryption access device
- Often integrated into a firewall
- Handles multiple VPN connections simultaneously
- Example: Cisco ASA, Palo Alto, pfSense

#### Client-to-Site VPN (Remote Access VPN)
- **One device connects to a remote network** over the internet
- In simple terms: you are at home, you connect to your company's internal network as if you were sitting in the office
- Example: employee working from home connects to office VPN → can access internal servers, printers, file shares
- **Cybersecurity use:** Weak VPN credentials are a top entry point for attackers

#### Site-to-Site VPN
- **Two entire networks connect** to each other over the internet permanently
- In simple terms: two office buildings in different cities connect their networks together so all devices can communicate as if on the same local network
- Example: Kathmandu office ↔ Pokhara office connected via site-to-site VPN
- Always on — no manual connection needed
- **Cybersecurity use:** If one site is compromised, attacker can pivot to the other site through the VPN tunnel

---

### 2.5 Network Devices

#### Router
- Connects **different networks** together
- Forwards packets based on IP address using a routing table
- Makes the decision: "Which path does this packet take?"
- **Cybersecurity use:** Router exploitation gives attacker full network control

#### Switches
- Uses **ASIC** (Application Specific Integrated Circuit) for fast hardware-based forwarding
- Forwards frames based on **MAC addresses**
- Much faster than routers for local network traffic

#### Unmanaged Switches
- Plug and play — no configuration needed
- No security features — anyone who plugs in gets access
- Used in home networks
- **Cybersecurity use:** Easy target — no port security, no VLAN support

#### Managed Switches
- Fully configurable — VLANs, port security, SNMP monitoring
- Interconnect with other switches via **802.1Q** (VLAN tagging)
- **SNMP** — Simple Network Management Protocol — used to monitor and manage the switch remotely
- **Cybersecurity use:** Misconfigured managed switches are a goldmine for attackers

#### Access Point (AP)
- Extends a wired network wirelessly
- Bridges wireless clients to the wired LAN
- **Cybersecurity use:** Rogue AP attacks — attacker sets up a fake access point with the same SSID

#### Patch Panel
- Centralises cable management in a server room
- Cables from all rooms terminate at the patch panel
- Makes moves, adds, changes easy without re-running cable

#### Firewall
- Filters traffic by **port number** and IP address
- Can act as a **proxy** — inspects traffic on behalf of clients
- Types: packet filtering, stateful inspection, next-gen (NGFW)
- **Cybersecurity use:** Firewall misconfiguration = open ports = attack surface

#### PoE — Power over Ethernet
- Delivers **electrical power through Ethernet cable** — no separate power cord needed
- Used for: IP cameras, VoIP phones, access points

| Type | Power | Use Case |
|---|---|---|
| PoE (802.3af) | 15.4W | IP phones, basic cameras |
| PoE+ (802.3at) | 30W | PTZ cameras, advanced APs |
| PoE++ (802.3bt) | 60-100W | Video conferencing, laptops |

- **PoE Injector (Midspan)** — adds power to existing non-PoE switch port
- **Built-in PoE (Endspan)** — switch has PoE built in

#### Cable Modem
- Broadband internet connection over coaxial cable (TV cable)
- Uses **DOCSIS** — Data Over Cable Service Interface Specification
- **Cybersecurity use:** Default router credentials on home cable modems are a common attack target

#### DSL Modem
- **Digital Subscriber Line** — internet over telephone lines
- Slower than cable but widely available
- ADSL (Asymmetric) — faster download than upload

#### ONT — Optical Network Terminal
- Used for **fibre optic** internet connections
- Converts optical signal to electrical signal for your router
- Located at the **demarc** (demarcation point) — where ISP responsibility ends and yours begins
- **Cybersecurity use:** ONT is owned by ISP — if compromised, ISP-level access achieved

#### NIC — Network Interface Card
- Hardware that connects a device to a network
- Has a **burned-in MAC address** (can be spoofed in software)
- Can be wired (Ethernet) or wireless (Wi-Fi)
- **Cybersecurity use:** MAC spoofing — attacker changes their MAC to impersonate another device

---

## TryHackMe — OSI Model

### What is the OSI Model?
- **Open Systems Interconnection Model**
- Essential framework dictating how all networked devices send, receive and interpret data
- Gives a **common language** for networking — same across all vendors and operating systems
- Has **7 layers** — each has a specific job

### The 7 Layers (Remember: **All People Seem To Need Data Processing**)

| Layer | Name | What It Does | Examples | Cybersecurity Relevance |
|---|---|---|---|---|
| 7 | **Application** | Interface between user and network | HTTP, HTTPS, FTP, DNS, SMTP | SQL injection, XSS, application-level attacks |
| 6 | **Presentation** | Data formatting, encryption, compression | SSL/TLS, JPEG, ASCII, Unicode | SSL stripping, encryption attacks |
| 5 | **Session** | Opens, manages, and closes sessions | NetBIOS, RPC, authentication sessions | Session hijacking, cookie theft |
| 4 | **Transport** | End-to-end delivery, error checking | TCP, UDP, port numbers | Port scanning, SYN flood attacks |
| 3 | **Network** | Logical addressing, routing | IP, ICMP, routers | IP spoofing, routing attacks |
| 2 | **Data Link** | Physical addressing, MAC addresses | Ethernet, 802.11, switches, ARP | ARP spoofing, MAC flooding |
| 1 | **Physical** | Raw bits over physical medium | Cables, hubs, radio waves, fibre | Physical tapping, signal interception |

### Memory Trick for OSI Layers (Top to Bottom)
> **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing
> Application → Presentation → Session → Transport → Network → Data Link → Physical

### How Data Travels Through the OSI Model
```
Sender (top to bottom):
Application → breaks data into chunks
Transport   → adds port numbers (TCP/UDP)
Network     → adds IP addresses
Data Link   → adds MAC addresses
Physical    → converts to bits and sends

Receiver (bottom to top):
Physical    → receives bits
Data Link   → reads MAC address
Network     → reads IP address
Transport   → reads port number
Application → delivers data to the app
```

### PDU — Protocol Data Unit
Each layer has a different name for its data:
| Layer | PDU Name |
|---|---|
| Application/Presentation/Session | Data |
| Transport | Segment |
| Network | Packet |
| Data Link | Frame |
| Physical | Bits |

### 🔑 Important Concepts You Missed

#### DNS Caching
- Your computer and router **cache** DNS responses locally for faster lookup
- This speeds up browsing but can be exploited
- **DNS Cache Poisoning** — attacker injects fake DNS records into cache → redirects users to malicious sites
- To flush DNS cache on Linux: `sudo systemd-resolve --flush-caches`

#### DNS over HTTPS (DoH) and DNS over TLS (DoT)
- Traditional DNS is **unencrypted** — anyone on the network can see what sites you're visiting
- DoH and DoT encrypt DNS queries
- **Cybersecurity use:** Attackers use DoH to hide malicious DNS queries from network monitors

#### DHCP Snooping
- A security feature on managed switches
- Blocks **rogue DHCP servers** by only allowing DHCP responses from trusted ports
- **Critical security control** — prevents DHCP-based man-in-the-middle attacks

#### Split Tunnelling (VPN)
- VPN setting where only **some traffic** goes through the VPN tunnel
- Rest goes directly to the internet
- **Cybersecurity use:** Split tunnelling can leak sensitive traffic outside the encrypted tunnel

#### ARP — Address Resolution Protocol
- Resolves IP addresses to MAC addresses on the local network
- Example: "Who has 192.168.1.1? Tell 192.168.1.50"
- **ARP Spoofing/Poisoning** — attacker sends fake ARP replies to associate their MAC with another device's IP → man-in-the-middle attack
- Operates at **Layer 2** of the OSI model

---

## What I Didn't Understand
- How exactly does VLAN hopping work? *(research Day 5)*
- Difference between stateful and stateless firewalls *(research Day 5)*

## 3 Key Things I Learned
1. DNS has three email security records — SPF, DKIM, DMARC — without all three your domain can be used for phishing
2. DHCP DORA process — Discover, Offer, Request, Acknowledge — rogue DHCP is a classic man-in-the-middle attack
3. VLANs separate networks logically on the same physical switch — VLAN hopping can bypass this separation