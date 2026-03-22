# CompTIA A+ 220-1201 — Week 1 Day 5 Notes

---

## Videos Watched
- ✅ 2.6 IPv4 and IPv6
- ✅ 2.6 Assigning IP Addresses
- ✅ 2.7 Internet Connection Types
- ✅ 2.7 Network Types
- ✅ 2.8 Network Tools

---

## Key Concepts

### 2.6 IPv4 and IPv6

#### IPv4
- **Primary** internet protocol — still dominant today
- **32-bit** address = 4 octets
- 1 octet = 1 byte = 8 bits
- Total addresses: **2^32 = ~4.3 billion**
- Written in dotted decimal: `192.168.1.1`
- We are running out of IPv4 addresses — solved temporarily by **NAT**

#### IPv4 Private Address Ranges (RFC 1918)
> Private IPs are NOT internet routable — only used internally

| Range | Subnet | Common Use |
|---|---|---|
| 10.0.0.0 – 10.255.255.255 | /8 | Large enterprises |
| 172.16.0.0 – 172.31.255.255 | /12 | Medium networks |
| 192.168.0.0 – 192.168.255.255 | /16 | Home and small office |

- **RFC** = Request For Comments — official internet standards documents
- **RFC 1918** defines private IP address space
- **NAT** (Network Address Translation) allows many private IPs to share one public IP
- **Cybersecurity use:** Private IPs found during internal recon reveal network structure

#### NAT — Network Address Translation
- Router translates private IP → public IP when traffic leaves the network
- Example:
```
Your laptop:  192.168.1.50  (private)
Your router:  203.45.67.89  (public — what the internet sees)
Website sees: 203.45.67.89, not your real IP
```
- **Cybersecurity use:** NAT hides internal network structure from the internet — but once inside, attacker can see all private IPs

#### IPv6
- **128-bit** address = 16 bytes = 8 groups of 4 hex characters
- Total addresses: **2^128** = virtually unlimited (340 undecillion addresses)
- Written in hexadecimal: `2400:1a00:3b6f:77c1::1`
- 2 octets = 2 bytes = 16 bits per group
- **First 64 bits** = network prefix
- **Last 64 bits** = host address
- DNS is even more critical with IPv6 — addresses too long to memorise
- All major operating systems support IPv6

#### IPv6 Shortening Rules
```
Full:      2001:0db8:0000:0000:0000:0000:0000:0001
Shorten:   2001:db8::1
Rules:
  - Remove leading zeros in each group (0db8 → db8)
  - Replace ONE consecutive group of all zeros with ::
```

#### IPv6 Special Addresses
| Address | Meaning |
|---|---|
| `::1` | Loopback (same as 127.0.0.1 in IPv4) |
| `fe80::/10` | Link-local (auto-assigned, not routable) |
| `2400::/12` | Global unicast (internet routable) |

- **Cybersecurity use:** IPv6 is often forgotten in security configs — attackers can bypass IPv4 firewalls using IPv6

---

### 2.6 Assigning IP Addresses

#### What Every Device Needs
- **IP Address** — unique identifier on the network
- **Subnet Mask** — defines which part is network and which is host
- **Default Gateway** — the router's IP — where to send traffic outside the local network
- **DNS Server** — to resolve domain names

#### Static IP Addressing
- IP address is **manually configured** and does not change
- Used for: servers, printers, routers, access points
- Pros: predictable, easier to manage firewalls and DNS
- Cons: time-consuming, easy to make mistakes
- **Best practice:** Use **DHCP reservation** instead of fully static — same result, easier to manage
- **Cybersecurity use:** Servers with static IPs are permanent targets — always know your exposed static IPs

#### APIPA — Automatic Private IP Addressing
- **Automatic Private IP Addressing** — IPv4 link-local address
- Assigned when a device **cannot reach a DHCP server**
- Range: **169.254.0.0/16** (169.254.x.x)
- Device randomly picks an address then uses **ARP** to confirm it is not already in use
- **Cybersecurity use:** Seeing 169.254.x.x means DHCP failed — device is isolated, possible network issue or attack

#### Turning Dynamic into Static (DHCP Reservation)
- Instead of manually setting static IP on the device, configure the DHCP server to always give the same IP to a specific MAC address
- Much better than fully static — managed centrally, less error-prone
- Example:
```
DHCP Server Rule:
MAC: AA:BB:CC:DD:EE:FF  →  Always assign 192.168.1.25
```

#### Subnet Mask Basics
| Subnet | CIDR | Hosts Available |
|---|---|---|
| 255.255.255.0 | /24 | 254 |
| 255.255.0.0 | /16 | 65,534 |
| 255.0.0.0 | /8 | 16,777,214 |
| 255.255.255.128 | /25 | 126 |
| 255.255.255.192 | /26 | 62 |

- **Cybersecurity use:** Subnetting is essential for reading network diagrams and planning attack paths

---

### 2.7 Internet Connection Types

#### Satellite
- Communication via satellite in orbit
- **High cost** — expensive hardware and service
- **High latency** — signal travels 35,000km to satellite and back (~600ms)
- **Rain fade** — heavy rain degrades signal quality
- Good for: remote areas with no other options (mountains, rural Nepal)
- Examples: Starlink (low earth orbit — lower latency ~40ms), traditional geostationary

#### Fibre Optic
- Uses **frequencies of light** to transmit data
- Fastest available — speeds up to 10+ Gbps
- Very low latency
- Most reliable — not affected by electrical interference
- **Cybersecurity use:** Physically tapping fibre requires special equipment but is possible

#### Cable (Broadband)
- Internet over **coaxial cable** (same cable as TV)
- Uses **DOCSIS** — Data Over Cable Service Interface Specification
- Shared bandwidth with neighbours — speeds vary at peak times
- Speeds: typically 100Mbps–1Gbps download

#### DSL — Digital Subscriber Line
- Internet over **telephone lines**
- **ADSL** — Asymmetric DSL — faster download than upload
- Speed limited by distance from telephone exchange
- Still widely used in Nepal and developing countries
- Speeds: typically 1–100Mbps

#### Cellular Networks
- Divides land into **cells** — each cell has a base station (tower)
- As you move, you hand off between towers seamlessly
- **Tethering** — one-to-one connection sharing cellular data
- **Hotspot** — shares cellular data with multiple devices via Wi-Fi
- Generations: 3G → 4G/LTE → 5G

#### WISP — Wireless Internet Service Provider
- Provides internet via **radio towers** instead of cables
- Common in rural areas where fibre and cable don't reach
- Uses licensed or unlicensed radio frequencies
- **Cybersecurity use:** Wireless links can be intercepted if not properly encrypted

---

### 2.7 Network Types

| Type | Full Name | Description | Range |
|---|---|---|---|
| **LAN** | Local Area Network | Devices in same building/floor | Building |
| **WAN** | Wide Area Network | Connects LANs across large distances | Country/World |
| **PAN** | Personal Area Network | Devices around one person | ~10 metres |
| **MAN** | Metropolitan Area Network | Covers a city | City |
| **SAN** | Storage Area Network | Dedicated network for storage devices | Data centre |
| **WLAN** | Wireless LAN | Wi-Fi based local network | Building |

#### WAN Technologies
- **Point-to-point** — dedicated leased line between two sites, always on
- **MPLS** — Multiprotocol Label Switching — routes traffic using labels instead of IP addresses, very fast
- **Terrestrial** — ground-based connections (fibre, cable, DSL)
- **Non-terrestrial** — satellite-based connections

#### MAN — Metropolitan Area Network
- **Metro Ethernet** — Ethernet technology extended across a city
- Example: connecting multiple university campuses across Kathmandu

#### SAN — Storage Area Network
- Dedicated high-speed network just for **storage devices**
- Looks like a **local storage device** to the server even though it is on the network
- **Block-level access** — server accesses raw storage blocks, not files
- Used in data centres and enterprises
- **Cybersecurity use:** SAN compromise = all stored data is at risk

---

### 2.8 Network Tools

#### Cable Crimper
- **Pinches** a wire connector (RJ45 plug) onto a cable
- Used to make custom-length Ethernet cables
- You need to know the **568A or 568B** wiring standard when crimping

#### Wi-Fi Analyser
- Scans nearby wireless networks and shows:
  - SSID (network name)
  - Signal strength (dBm)
  - Channel being used
  - Frequency (2.4GHz or 5GHz)
  - Security type (WPA2, WPA3 etc.)
- Used to find channel congestion and optimise Wi-Fi placement
- **Cybersecurity use:** Shows all nearby networks including hidden SSIDs and their security — first tool in Wi-Fi hacking recon
- Free tool on Ubuntu: `sudo apt install wavemon -y` then run `wavemon`

#### Tone Generator (Fox and Hound)
- Two-part tool: **tone generator** and **tone probe**
- Tone generator connects to one end of a cable and sends an electrical tone
- Tone probe is held near cables — beeps louder as it gets closer to the right cable
- Used to **trace and identify cables** in walls, ceilings, or large bundles
- Very useful in messy server rooms

#### Punch Down Tool
- Used to push wire into a **punch down block** or patch panel
- The blade cuts the wire to the correct length and seats it firmly
- Two types: 110 block (modern) and 66 block (older telephone)
- Used when terminating Ethernet cables at a wall jack or patch panel

#### Cable Tester
- Verifies that a cable is wired correctly end to end
- Tests: continuity, correct pin mapping, short circuits, crossed wires
- Basic testers just show pass/fail
- Advanced testers show exact pin mapping and identify which wire has a fault

#### Loopback Plug
- A connector that **loops the output back to the input**
- Used to test if a network port or interface is working
- Example: plug into an Ethernet port — if the port can send and receive its own signal, it is working
- Different plugs for: RJ45 (Ethernet), RJ11 (phone), serial, fibre
- **Cybersecurity use:** Used in physical security audits to test network port accessibility

#### Taps and Port Mirrors

**Network Tap:**
- A **physical device** that copies all network traffic passing through a cable
- Installed inline between two devices — completely passive, devices do not know it is there
- Sends a copy of all traffic to a monitoring device
- Used by: network analysts, law enforcement, attackers with physical access
- **Cybersecurity use:** Physical tap = complete traffic capture including passwords if unencrypted

**Port Mirror (SPAN — Switched Port Analyser):**
- A **software feature** on managed switches
- Copies all traffic from one or more ports and sends it to a designated monitoring port
- No physical device needed — configured through the switch management interface
- Used for: network monitoring, IDS/IPS, Wireshark analysis
- **Cybersecurity use:** Attackers who gain switch management access can set up a port mirror to capture all traffic silently

**Tap vs Port Mirror:**
| Feature | Network Tap | Port Mirror |
|---|---|---|
| Type | Physical hardware | Software feature |
| Detectable | No | Yes (on switch logs) |
| Traffic captured | 100% — never drops packets | May drop packets under load |
| Cost | Higher | Free (built into managed switch) |
| Use case | Passive monitoring, forensics | Active monitoring, IDS |

---

## TryHackMe — Packets and Frames + Extending Your Network

### Packets vs Frames

- **Packets and frames** are small pieces of data that together form a larger message
- They are different things at different OSI layers:

| Term | OSI Layer | Contains |
|---|---|---|
| **Frame** | Layer 2 — Data Link | MAC addresses + packet inside |
| **Packet** | Layer 3 — Network | IP addresses + data payload |

- Think of it like posting a letter:
  - The **envelope** = Frame (handles the physical delivery, has the address label)
  - The **letter inside** = Packet (has the actual content and final destination)
- Once the recipient opens the envelope (frame), they read the letter (packet) to know what to do next

### Port Forwarding

#### What is Port Forwarding?
- **Essential for making internal services accessible from the internet**
- Without it, services like web servers are only available inside the local network (intranet)

#### Example Without Port Forwarding:
```
Internal network:
  Web server:  192.168.1.10:80
  Computer A:  192.168.1.20  ✅ can access the web server
  Computer B:  192.168.1.30  ✅ can access the web server
  Internet:                  ❌ cannot reach 192.168.1.10 (private IP)
```

#### Example With Port Forwarding:
```
Router public IP: 203.45.67.89
Port forward rule: 203.45.67.89:80 → 192.168.1.10:80

Internet user visits: http://203.45.67.89
Router forwards to:   http://192.168.1.10:80  ✅
```

#### How to Set Up Port Forwarding:
1. Log into your router admin page (usually 192.168.1.1)
2. Find "Port Forwarding" section
3. Add rule: External port → Internal IP:Internal port
4. Example: Port 80 → 192.168.1.10:80

- **Cybersecurity use:** Open port forwards are a major attack surface — every forwarded port is an exposed service on the internet

### Firewalls and Port Forwarding Together
- Firewall rules control **which traffic is allowed**
- Port forwarding rules control **where allowed traffic goes**
- Both must be configured correctly — port forwarding without a firewall = fully exposed server

### NAT and Port Forwarding Relationship
- Port forwarding is a special type of NAT rule
- Regular NAT: internal → external (outbound)
- Port forwarding: external → internal (inbound)

### 🔑 Additional Important Concepts You Missed

#### Subnetting Practice
- Try calculating subnets for your home network:
```bash
# Check your IP and subnet on Ubuntu
ip a
# Look for lines like: inet 192.168.1.71/24
# /24 means subnet mask 255.255.255.0
# Network: 192.168.1.0
# Broadcast: 192.168.1.255
# Usable hosts: 192.168.1.1 - 192.168.1.254
```

#### ICMP — Internet Control Message Protocol
- Used by **ping** and **traceroute**
- Not a data transport protocol — used for network diagnostics
- **Cybersecurity use:** ICMP can be used for covert communication (ICMP tunnelling) or blocked by firewalls to hide hosts

#### Traceroute
- Shows every router (hop) a packet passes through to reach its destination
```bash
traceroute google.com    # Linux
tracert google.com       # Windows
```
- **Cybersecurity use:** Reveals network topology, ISP infrastructure, and geographic path of traffic

#### MTU — Maximum Transmission Unit
- Maximum size of a packet that can be sent without fragmentation
- Default Ethernet MTU: **1500 bytes**
- If a packet is larger, it gets fragmented into smaller pieces
- **Cybersecurity use:** MTU manipulation can be used to bypass firewalls or cause denial of service

---

## What I Didn't Understand
- How exactly does MPLS work? *(research later)*
- How does a network tap work at the physical level? *(research later)*

## 3 Key Things I Learned
1. APIPA (169.254.x.x) means DHCP failed — device cannot reach the network properly
2. Network tap is passive and undetectable — port mirror is software-based and visible in switch logs
3. Port forwarding makes internal services reachable from the internet — every open port forward is an attack surface