# CCNA 200-301 — Phase 2 Week 1 Day 4 Notes

**Lab Files:** https://drive.google.com/drive/folders/1PwK_jWqfUtOjV7gHt8ODutq9QA5cxCgi

---

## Videos Watched
- ✅ Day 5 — Ethernet LAN Switching Part 1
- ✅ Day 6 — Ethernet LAN Switching Part 2
- ✅ Day 6 Lab — Analyzing Ethernet Switching

---

## Key Concepts

### OSI Model (Quick Revision)

- **7 Layers:**
  - Application  
  - Presentation  
  - Session  
  - Transport  
  - Network  
  - Data Link  
  - Physical  

- Each layer has its own **PDU (Protocol Data Unit):**

| Layer | PDU |
|---|---|
| Application | Data |
| Transport | Segment / Datagram |
| Network | Packet |
| Data Link | Frame |
| Physical | Bits |

---

### Local Area Network (LAN)

- A network contained within a **small geographic area**
- Example:
  - Home network  
  - Office network  

---

### Ethernet Frame Structure

- Ethernet frame consists of:
  - Header + Payload (Packet) + Trailer  

- Fields:

| Field | Description |
|---|---|
| Preamble | Synchronization |
| SFD | Start Frame Delimiter |
| Destination | Receiver MAC |
| Source | Sender MAC |
| Type/Length | Protocol or size |
| Payload | Encapsulated packet |
| FCS | Error detection |

---

#### Preamble & SFD

**Preamble**
- 7 bytes (56 bits)  
- Pattern: `10101010` repeated  
- Used for synchronization  

**SFD (Start Frame Delimiter)**
- 1 byte (8 bits)  
- Pattern: `10101011`  
- Marks start of frame  

---

#### Destination & Source MAC

- Identify sender and receiver  
- MAC = **Media Access Control address**
- Size: **6 bytes (48 bits)**  

---

#### Type / Length Field

- 2 bytes (16 bits)

- If value ≤ 1500 → indicates payload size  
- If value ≥ 1536 → indicates protocol type (IPv4, IPv6)

---

#### FCS (Frame Check Sequence)

- 4 bytes (32 bits)
- Uses **CRC (Cyclic Redundancy Check)**
- Detects corrupted data  

---

### Ethernet Frame Size

- Header + Trailer = **18 bytes**
- Minimum frame size = **64 bytes**
- Minimum payload = **46 bytes**

- If payload < 46 bytes:
  - **Padding is added**

---

### MAC Address

- 6 bytes (48-bit physical address)
- Also called **BIA (Burned-In Address)**
- Globally unique  

---

#### MAC Address Structure

- First 3 bytes → **OUI (Vendor ID)**
- Last 3 bytes → **Device-specific**

- Written in **hexadecimal**

---

#### Number Systems

**Decimal**
- 0–9  

**Hexadecimal**
- 0–9, A–F  

---

### Switch Forwarding Logic

#### Unicast Frame
- Sent to a **single destination device**

---

#### Unknown Unicast Frame
- Destination MAC not in MAC table  
- Switch **floods frame** to all ports except incoming port  

---

#### Known Unicast Frame
- MAC found in table  
- Switch forwards to correct port only  

---

#### MAC Address Learning

- Switch learns **source MAC address**
- Adds it to MAC table with port

---

#### MAC Address Aging

- Dynamic MAC entries removed after **5 minutes of inactivity**

---

### ARP (Address Resolution Protocol)

- Used to find **MAC address from known IP address**

---

#### ARP Process

**ARP Request**
- Broadcast (sent to all devices)
- Destination MAC = `FF:FF:FF:FF:FF:FF`

**ARP Reply**
- Unicast (sent back to requester)

---

#### Example

**ARP Request**
- Src IP: 192.168.1.10  
- Dst IP: 192.168.1.1  
- Src MAC: AA:AA:AA:AA:AA:AA  
- Dst MAC: FF:FF:FF:FF:FF:FF  

**ARP Reply**
- Src IP: 192.168.1.1  
- Dst IP: 192.168.1.10  
- Src MAC: BB:BB:BB:BB:BB:BB  
- Dst MAC: AA:AA:AA:AA:AA:AA  

---

### Ping (ICMP)

- Used to test **reachability**
- Measures **round-trip time**

---

#### Messages Used

- ICMP Echo Request  
- ICMP Echo Reply  

---

### MAC Address Table

- Stored in switch  
- Format:

| VLAN | MAC Address | Type | Port |
|---|---|---|---|

---

### VLAN (Virtual LAN)

- Logical separation of networks
- Devices in different VLANs act as separate networks  

---

### Managing MAC Table

- Remove all dynamic entries:
    clear mac address-table dynamic

- Remove specific MAC:
    clear mac address-table dynamic address XXXX.XXXX.XXXX

- Remove by interface:
    clear mac address-table dynamic interface Gi0/0

---

## Terminal / CLI Practice

    # View MAC address table
    show mac address-table

    # View ARP table
    show arp

    # Test connectivity
    ping 192.168.1.1

    # Clear MAC table
    clear mac address-table dynamic

---

## 🔑 Exam Focus Summary
**Ethernet Frame fields** (Preamble, SFD, MACs, Type, FCS)  
**MAC address = 48-bit (6 bytes), globally unique**  
**OUI = first 3 bytes (vendor)**  
**Minimum Ethernet frame size = 64 bytes**  
**Minimum payload = 46 bytes (padding if smaller)**  
**Unknown unicast = flooding**  
**Known unicast = direct forwarding**  
**Switch learns MAC from source address**  
**MAC aging = 5 minutes**  
**ARP = IP → MAC resolution**  
**ARP request = broadcast | ARP reply = unicast**  
**Ping uses ICMP (Echo Request/Reply)**  
**MAC table format (VLAN, MAC, Type, Port)**  

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. How switches learn MAC addresses and use them to forward frames efficiently  
2. The structure of an Ethernet frame and how data is encapsulated at Layer 2  
3. How ARP resolves IP addresses to MAC addresses and enables communication in a LAN  