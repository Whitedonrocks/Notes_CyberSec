# CCNA 200-301 — Phase 2 Week 1 Day 2 Notes

**Lab Files:** https://drive.google.com/drive/folders/1PwK_jWqfUtOjV7gHt8ODutq9QA5cxCgi

---

## Videos Watched
- ✅ Day 2 — Interfaces, Cables, TCP/IP Model, OSI Model

---

## Key Concepts

### Network Interfaces & Ethernet Basics

#### Interfaces (RJ-45)
- **RJ-45 (Registered Jack-45)** is a standard connector used for Ethernet networking
- Commonly used to connect:
  - PCs
  - Switches
  - Routers

---

#### Ethernet
- **Ethernet** is a collection of network protocols used for LAN communication
- Defined under **IEEE 802.3 standard**
- Supports different speeds:
  
| Standard | Speed |
|----------|------|
| 10BASE-T | 10 Mbps |
| 100BASE-T | 100 Mbps |
| 1000BASE-T | 1 Gbps |
| 10GBASE-T | 10 Gbps |

---

#### Bits & Bytes
- **Bit** = smallest unit (0 or 1)
- **Byte** = 8 bits

| Unit | Value |
|------|------|
| 1 Kilobit (Kb) | 1,000 bits |
| 1 Megabit (Mb) | 1,000,000 bits |
| 1 Gigabit (Gb) | 1,000,000,000 bits |
| 1 Terabit (Tb) | 1,000,000,000,000 bits |

- **Network speed** → measured in **bits per second (bps)**
- **Storage (hard drives)** → measured in **bytes**

🔐 **Cybersecurity Note:**
- Misunderstanding bits vs bytes can lead to incorrect bandwidth estimation → affects network security tools (IDS/IPS throughput planning)

---

### UTP (Unshielded Twisted Pair) Cables

#### What is UTP?
- Copper cable with **twisted pairs of wires**
- Twisting helps reduce **EMI (Electromagnetic Interference)**

---

#### Ethernet over UTP (10BASE-T / 100BASE-T)
- Uses specific pins for transmission:

| Function | Pins |
|----------|------|
| Transmit (TX) | 1, 2 |
| Receive (RX) | 3, 6 |

---

#### Straight-Through Cable
Used between:
- PC ↔ Switch  
- Router ↔ Switch  

Pin configuration:
- TX → TX  
- RX → RX  

---

#### Crossover Cable
Used between:
- Router ↔ Router  
- PC ↔ PC  

Pin configuration:
- TX ↔ RX (crossed)

---

#### Full Duplex Communication
- Devices can **send and receive simultaneously**

---

#### Gigabit Ethernet (1000BASE-T)
- Uses **all 4 pairs (8 wires)**
- Each pair is **bidirectional**

---

#### Auto MDI-X
- Automatically adjusts TX/RX pins
- Removes need to worry about straight vs crossover cables

🔐 **Cybersecurity Note:**
- Physical access via Ethernet port = major risk  
- Attackers can plug into open ports → gain LAN access  
- Mitigation: **Port Security on switches**

---

### Fiber Optic Connections

#### SFP (Small Form-factor Pluggable)
- Modular transceiver used in switches/routers for fiber connections

---

#### Fiber Cable Structure
1. Core (fiberglass)
2. Cladding (reflects light)
3. Protective buffer
4. Outer jacket

---

#### Types of Fiber

| Feature | Multimode Fiber | Single-mode Fiber |
|--------|----------------|------------------|
| Core Size | Wider | Narrow |
| Light Source | LED | Laser |
| Distance | Medium | Very Long |
| Cost | Cheaper | Expensive |

---

#### UTP vs Fiber Optic

| Feature | UTP | Fiber |
|--------|-----|------|
| Medium | Copper | Glass |
| Speed | Lower | Very High |
| Distance | Short | Long |
| EMI | Affected | Not affected |
| Cost | Cheap | Expensive |

🔐 **Cybersecurity Note:**
- Fiber is harder to tap than copper → more secure  
- UTP cables are easier to intercept physically

---

### TCP/IP Model

#### What is a Protocol?
- A **set of rules** defining how devices communicate

#### What is a Standard?
- Agreed specification of how technology should work

---

#### History
- 1960s → **ARPANET**
- Early protocol → **NCP (Network Control Protocol)**
- Developed by:
  - Vint Cerf
  - Bob Kahn
- Introduced:
  - TCP (Transmission Control Protocol)
  - IP (Internet Protocol)

---

#### Organizations Defining Standards

- **IEEE**
  - Ethernet → 802.3
  - WiFi → 802.11

- **IETF**
  - Defines protocols like:
    - TCP, IP, UDP, HTTP, DNS
  - Publishes standards as:
    - **RFCs (Request for Comments)**

---

### TCP/IP Layers

| Layer | Function | Examples |
|------|---------|---------|
| Application | User-level data | HTTP, HTTPS, FTP, SMTP |
| Transport | End-to-end communication (ports) | TCP, UDP |
| Internet | Logical addressing & routing | IP, ICMP |
| Network Access | Local delivery (MAC) | Ethernet, WiFi |
| Physical | Bit transmission | Signals (electrical/optical) |

---

### Encapsulation & Decapsulation

#### Encapsulation (Sending Data)

| Layer | Data Unit |
|------|----------|
| Application | Data |
| Transport | Segment (TCP) / Datagram (UDP) |
| Internet | Packet |
| Data Link | Frame |
| Physical | Bits |

---

#### Decapsulation
- Reverse process at receiver

---

#### PDU (Protocol Data Unit)
- Each layer adds its own **header**
- Actual data = **Payload**

🔐 **Cybersecurity Note:**
- Attackers can manipulate headers (e.g., IP spoofing)
- Deep packet inspection tools analyze encapsulated data

---

### OSI Model (7 Layers)

Defined by **ISO (International Organization for Standardization)**

| Layer | Name |
|------|------|
| 7 | Application |
| 6 | Presentation |
| 5 | Session |
| 4 | Transport |
| 3 | Network |
| 2 | Data Link |
| 1 | Physical |

---

#### Important Notes
- Real networks use **TCP/IP model**
- OSI is mainly a **reference model**
- Many resources use a **5-layer hybrid model**:
  - Application
  - Transport
  - Network
  - Data Link
  - Physical

---

## Terminal / CLI Practice

bash
# Check network interfaces (Linux)
ip a

# Test connectivity
ping 8.8.8.8

# View routing table
ip route

# Show interface status
show ip interface brief

# Show MAC address table (switch)
show mac address-table

# Show running configuration
show running-config


## 🔑 Exam Focus Summary
**RJ-45** = Ethernet connector
**Ethernet** = IEEE 802.3 standard
**Know UTP pin usage** (1,2 TX / 3,6 RX)
**Straight vs Crossover cables**
**Auto MDI-X eliminates manual cable selection**
**Fiber types**: Single-mode vs Multimode
**TCP/IP layers + functions** (VERY IMPORTANT)
**Encapsulation order** (Application → Physical)
**OSI 7 layers** (memorization + mapping to TCP/IP)
**PDU names** (Segment, Packet, Frame)


## What I Didn't Understand
-

## 3 Key Things I Learned
1. Difference between straight-through and crossover cables and how Auto MDI-X simplifies connections
2. How data moves through layers using encapsulation and decapsulation
3. Key differences between TCP/IP and OSI models and their practical usage