# CCNA 200-301 — Phase 2 Week 1 Day 5 Notes

**Lab Files:** https://drive.google.com/drive/folders/1PwK_jWqfUtOjV7gHt8ODutq9QA5cxCgi

---

## Videos Watched
- ✅ Day 5 — IPv4 Addressing Part 1
- ✅ Day 5 — IPv4 Addressing Part 2
- ✅ Day 5 Lab — Configuring IP Addresses

---

## Key Concepts

### Network Layer (Layer 3)

- Provides communication between hosts on different networks
- Responsible for:
  - Logical addressing (IP addresses)
  - Path selection (routing)
  - Packet forwarding

- Routers operate at **Layer 3 (Network Layer)**

---

### Routing

- Process of moving packets from source network to destination network
- Routers determine the best path for packets

---

### IPv4 Header

| Field |
|---|
| Version |
| Header Length |
| Type of Service (TOS) |
| Total Length |
| Identification |
| Flags |
| Fragment Offset |
| TTL |
| Protocol |
| Header Checksum |
| Source Address |
| Destination Address |
| Options |
| Data |

---

### IPv4 Addresses

- IPv4 address size = **32 bits (4 bytes)**

Examples:
- `192.168.1.254`
- `8.8.8.8`

---

#### Binary Representation

Example:
- `192.168.1.254`

Binary:
- `11000000.10101000.00000001.11111110`

---

#### Octets

- IPv4 addresses are divided into **4 groups of 8 bits**
- Each 8-bit group is called an **octet**

---

### Binary & Decimal Conversion

#### Binary → Decimal
- Add values where bits are `1`

#### Decimal → Binary
- Subtract using powers of 2

---

### Prefix Length (/Notation)

Example:
- `/24`

Means:
- First 24 bits = network portion
- Remaining bits = host portion

---

### IPv4 Address Classes

| Class | First Bits | Range | Default Prefix |
|---|---|---|---|
| A | 0xxxxxxx | 0–126 | /8 |
| B | 10xxxxxx | 128–191 | /16 |
| C | 110xxxxx | 192–223 | /24 |
| D | 1110xxxx | 224–239 | Multicast |
| E | 1111xxxx | 240–255 | Experimental |

---

### Loopback Addresses

- Range:
  - `127.0.0.0 – 127.255.255.255`

- Used to test:
  - TCP/IP stack
  - Local network functionality

- `127.0.0.1` = localhost

---

### Network & Broadcast Addresses

#### Network Address
- First address in network
- Host bits all `0`
- Cannot be assigned to a host

---

#### Broadcast Address
- Last address in network
- Host bits all `1`
- Cannot be assigned to a host

---

### Netmasks

| Class | Prefix | Netmask |
|---|---|---|
| A | /8 | 255.0.0.0 |
| B | /16 | 255.255.0.0 |
| C | /24 | 255.255.255.0 |

---

### Maximum Hosts Per Network

Example:
- `192.168.1.0/24`

Host bits:
- 8 bits

Total addresses:
- `2^8 = 256`

Usable hosts:
- `256 - 2 = 254`

Formula:
- `2^n - 2`
- `n = number of host bits`

---

### First & Last Usable Addresses

Example:
- Network: `192.168.1.0/24`

| Type | Address |
|---|---|
| Network Address | 192.168.1.0 |
| First Usable | 192.168.1.1 |
| Last Usable | 192.168.1.254 |
| Broadcast Address | 192.168.1.255 |

---

### Configuring Cisco Router Interfaces

#### Checking Interfaces

Command:
    show ip interface brief

Shows:
- Interface status
- IP addresses
- Protocol state

---

#### Interface States

**Administratively Down**
- Interface disabled using:
    shutdown

- Default state of Cisco router interfaces

---

#### Configuring an Interface

Enter global config:
    configure terminal

Select interface:
    interface gigabitethernet 0/0

Short form:
    int g0/0

Assign IP:
    ip address 192.168.1.1 255.255.255.0

Enable interface:
    no shutdown

Short form:
    no sh

---

### Useful Interface Commands

#### Show Detailed Interface Information
    show interfaces

---

#### Show Interface Descriptions
    show interfaces description

---

#### Configure Interface Description

Inside interface config mode:
    description Connected-to-SW1

---

## Terminal / CLI Practice

    # Enter global configuration mode
    configure terminal

    # Select interface
    interface gigabitethernet 0/0

    # Assign IP address
    ip address 192.168.1.1 255.255.255.0

    # Enable interface
    no shutdown

    # View interfaces
    show ip interface brief

    # Show interface details
    show interfaces

    # Show interface descriptions
    show interfaces description

---

## 🔑 Exam Focus Summary
**IPv4 = 32-bit address (4 octets)**  
**Router operates at Layer 3**  
**/24 = first 24 bits are network bits**  
**Class A = /8 | Class B = /16 | Class C = /24**  
**127.0.0.0/8 = loopback range**  
**Network address = host bits all 0**  
**Broadcast address = host bits all 1**  
**Maximum hosts formula = 2^n - 2**  
**Know first/last usable host calculation**  
**show ip interface brief** is VERY important  
**Router interfaces are administratively down by default**  
**no shutdown enables interfaces**  

---

## What I Didn't Understand
-

---

## 3 Key Things I Learned
1. How IPv4 addresses are divided into network and host portions using prefix lengths  
2. How to calculate usable hosts, network address, and broadcast address  
3. How to configure and enable interfaces on Cisco routers using CLI commands  