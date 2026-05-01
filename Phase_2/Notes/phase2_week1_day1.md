# CCNA 200-301 — Phase 2 Week 1 Day 1 Notes

**Lab Files:** https://drive.google.com/drive/folders/1PwK_jWqfUtOjV7gHt8ODutq9QA5cxCgi

---

## Videos Watched
- ✅ Day 1 — Network Devices (30:26)
- ✅ Day 1 Extra — Anki Flashcards (14:56)
- ✅ Day 1 Lab — Packet Tracer Introduction (15:18)

---

## Key Concepts

### What is a Network?
- A network is a collection of computing devices connected together to share resources and communicate
- Can be as small as two computers connected at home or as large as the internet itself
- Networks allow: file sharing, internet access, communication, centralised resources

---

### Types of Network Nodes

#### Clients
- A device that **accesses a service** made available by a server
- Examples: your laptop browsing a website, your phone checking email
- Clients initiate requests — servers respond
- Most end-user devices are clients: PCs, phones, tablets

#### Servers
- A device that **provides services** to clients
- Examples: web server (serves websites), email server (handles email), file server (stores files)
- A single device can be both client AND server simultaneously
- Example: your PC can browse the web (client) while running a local web server (server)

---

### Network Devices

#### Switches
- Have **many interfaces** for end hosts to connect to — usually **24+ ports**
- Provide connectivity to hosts **within the same LAN (Local Area Network)**
- Do **NOT** provide connectivity between LANs or over the internet
- Operate at **Layer 2 (Data Link)** of the OSI model — use MAC addresses
- Forward frames based on MAC address table
- When a frame arrives: switch checks destination MAC → forwards only to correct port

**How a switch differs from a hub:**
- Hub = sends data to ALL ports (broadcasts everything)
- Switch = sends data only to the intended destination port (intelligent)

**Cisco Switch Examples:**
| Model | Ports | Use Case |
|---|---|---|
| Catalyst 2960 | 24/48 | Small-medium business access layer |
| Catalyst 3650 | 24/48 | Layer 3 capable, medium business |
| Catalyst 9200 | 24/48 | Modern enterprise access layer |
| Catalyst 9300 | 24/48 | Enterprise, high performance |
| Nexus 9000 | Varies | Data centre switching |

---

#### Routers
- Have **fewer network interfaces** than switches (typically 2-8 ports)
- Used to provide **connectivity between LANs**
- Used to **send data over the internet** — route packets between different networks
- Operate at **Layer 3 (Network)** of the OSI model — use IP addresses
- Make routing decisions based on destination IP address
- Each interface connects to a different network

**Router vs Switch — Key Difference:**
```
Switch connects devices WITHIN a network (same LAN)
Router connects DIFFERENT networks together

Home network example:
PC → Switch → Router → Internet
     (LAN)      (connects to ISP's network)
```

**Cisco Router Examples:**
| Model | Use Case |
|---|---|
| ISR 1100 | Small branch office |
| ISR 4000 | Medium-large branch |
| ASR 1000 | Enterprise WAN edge |
| ASR 9000 | Service provider core |
| NCS 5500 | Large scale internet backbone |

---

#### Firewalls
- **Monitor and control network traffic** based on configured rules
- Act as gatekeepers — allow or deny traffic based on rules
- Can be placed **inside** or **outside** the network depending on security design
- Rules typically based on: source IP, destination IP, port numbers, protocol

**Next Generation Firewalls (NGFW):**
- Traditional firewalls: filter by IP and port only
- **NGFW** — include more modern and advanced filtering capabilities:
  - **Deep Packet Inspection (DPI)** — inspect actual content of packets
  - **Application awareness** — identify and control apps (block Facebook, allow Zoom)
  - **Intrusion Prevention System (IPS)** — detect and block attacks in real time
  - **URL filtering** — block malicious or inappropriate websites
  - **SSL/TLS inspection** — decrypt and inspect encrypted traffic
  - **User identity awareness** — apply rules per user, not just IP

**Network Firewalls vs Host-Based Firewalls:**

| Type | What it is | Where it runs | Purpose |
|---|---|---|---|
| **Network Firewall** | Hardware device | Between networks | Filters traffic between networks — protects entire network |
| **Host-Based Firewall** | Software application | On individual PC/server | Filters traffic entering/exiting that specific device |

- Both are needed — **defence in depth**
- Network firewall stops threats before they reach your devices
- Host-based firewall protects against threats that bypass the network firewall

**Cisco Firewall Examples:**
| Model | Type | Use Case |
|---|---|---|
| ASA 5500-X | Traditional + some NGFW | Small-medium business |
| Firepower 1000 | NGFW | Small-medium business |
| Firepower 2100 | NGFW | Medium enterprise |
| Firepower 4100 | NGFW | Large enterprise |
| Firepower 9300 | NGFW | Service provider, large enterprise |
| Meraki MX | Cloud-managed NGFW | Branch offices |

---

### Additional Network Devices (Not in Notes — Important for CCNA)

#### IDS — Intrusion Detection System
- **Monitors** network traffic and alerts on suspicious activity
- Passive — detects and alerts but does NOT block traffic
- Think of it as a security camera — watches and records but doesn't stop anything
- **Cybersecurity use:** IDS logs are analysed by SOC analysts

#### IPS — Intrusion Prevention System
- **Monitors AND blocks** suspicious traffic in real time
- Active — can drop malicious packets automatically
- Think of it as a security guard — watches AND stops threats
- Usually built into modern NGFW

#### Access Points (APs)
- Provide **wireless connectivity** to wired networks
- Connect wireless devices (phones, laptops) to the LAN
- Cisco AP examples: Aironet series, Catalyst 9100 series, Meraki MR series

#### WLC — Wireless LAN Controller
- Centrally manages many access points
- Configure all APs from one place
- Used in enterprise environments with many APs

---

### Anki Flashcards for CCNA

#### What is Anki?
- **Spaced repetition flashcard app** — shows cards just before you forget them
- Scientifically proven to improve long-term retention
- Jeremy provides a free pre-made CCNA deck — covers all exam topics

#### How to Use Anki for CCNA
- **Daily habit** — 10-15 minutes every day
- Review cards shown to you — rate your confidence
- New cards added as you progress through the course
- By exam time — all concepts reviewed hundreds of times

#### Installing Latest Anki on Ubuntu
```bash
# Remove old version
sudo apt remove anki -y

# Install dependencies
sudo apt install libxcb-cursor0 -y

# Download and install latest version from ankiweb.net
# Or force Wayland mode if xcb issues:
ANKI_WAYLAND=1 anki
```

---

### Packet Tracer Introduction

#### What is Packet Tracer?
- **Cisco's free network simulation software**
- Simulate routers, switches, firewalls, PCs, servers without real hardware
- Build virtual networks and configure real Cisco IOS commands
- Essential for CCNA study — practice everything before touching real equipment

#### Packet Tracer Interface
- **Logical workspace** — where you build and configure networks
- **Device panel** (bottom left) — drag devices into workspace
  - Routers, switches, hubs, wireless devices, end devices, connections
- **Cable types:**
  - **Straight-through** (solid line) — connect different device types (PC to switch, router to switch)
  - **Crossover** (dashed line) — connect same device types (switch to switch, PC to PC)
  - **Console** (light blue) — connect PC to router/switch for initial configuration
  - **Serial** (red) — WAN connections between routers
- **CLI** — click on device → CLI tab → configure using real Cisco IOS commands
- **Simulation mode** — watch packets travel through the network in real time

#### Saving Packet Tracer Labs
```bash
# Save labs to your organised folder
~/Documents/Labs/Phase2/PacketTracer/
```

#### Basic Packet Tracer Lab — Day 1
- Add devices to workspace
- Connect them with appropriate cables
- Verify connections with green link lights (amber = not yet active, green = active)

---

## Terminal Practice

```bash
# Check your network interfaces — understand what you're working with
ip a

# Check routing table — how your PC routes traffic
ip route

# Ping your gateway — test local network
ping -c 4 192.168.1.1

# Traceroute — see how packets travel
traceroute google.com

# Check ARP table — MAC to IP mappings
ip neigh
```

---

## 🔑 Exam Focus Summary

**Network Devices:**
- **Client** = accesses services | **Server** = provides services
- **Switch** = connects devices within same LAN, Layer 2, MAC addresses, 24+ ports
- **Router** = connects different networks/LANs, Layer 3, IP addresses, fewer ports
- **Firewall** = monitors/controls traffic based on rules, hardware (network) or software (host-based)
- **NGFW** = Next Generation Firewall — adds DPI, application awareness, IPS, URL filtering

**Key Distinctions:**
- Switch = same LAN connectivity
- Router = between LANs / internet connectivity
- Network firewall = between networks (hardware)
- Host-based firewall = on individual device (software)
- IDS = detects only | IPS = detects AND blocks

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. Switches connect devices within the same LAN using MAC addresses — they do NOT connect different networks — that's what routers do
2. Next Generation Firewalls go beyond port/IP filtering — they can identify specific applications, inspect encrypted traffic, and actively block attacks (IPS)
3. A device can be both client and server simultaneously — your PC browsing the web is a client, but it can also run a local server at the same time