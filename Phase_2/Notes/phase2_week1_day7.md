# CCNA 200-301 — Phase 2 Week 1 Day 7 Notes

**Lab Files:** https://drive.google.com/drive/folders/1PwK_jWqfUtOjV7gHt8ODutq9QA5cxCgi

---

## Videos Watched
- ✅ Day 10 — IPv4 Header
- ✅ Day 11 — Routing Fundamentals (Part 1)
- ✅ Day 11 — Static Routing (Part 2)
- ✅ Day 11 Lab — Configuring Static Routes
- ✅ Day 11 Lab — Troubleshooting Static Routes

---

## Key Concepts

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

### Version Field

- Identifies IP version
- Two versions:
  - IPv4
  - IPv6

- Size:
  - 4 bits

---

### Header Length (HL)

- Indicates total size of IPv4 header
- Measured in 4-byte increments

Minimum:
- 5 = 20 bytes

Maximum:
- 15 = 60 bytes

- Header may vary because Options field is optional

---

### Type of Service (TOS)

#### DSCP (Differentiated Services Code Point)
- 6 bits
- Used for QoS (Quality of Service)
- Prioritizes delay-sensitive traffic

---

#### ECN (Explicit Congestion Notification)
- 2 bits
- Indicates network congestion without dropping packets

---

### Total Length Field

- Size:
  - 16 bits

- Indicates total packet size:
  - IPv4 header + encapsulated data

Minimum:
- 20 bytes

Maximum:
- 65535 bytes

---

### Identification Field

- Size:
  - 16 bits

- Used during fragmentation
- Identifies which fragments belong to same packet

---

### MTU (Maximum Transmission Unit)

- Maximum frame size supported by a link
- Ethernet MTU usually:
  - 1500 bytes

- Packets larger than MTU may be fragmented

---

### Flags Field

- Size:
  - 3 bits

#### Bit 0
- Reserved
- Always 0

---

#### DF (Don't Fragment)
- Prevents fragmentation if set

---

#### MF (More Fragments)
- Set to 1 if more fragments exist
- Last fragment uses 0

---

### Fragment Offset

- Size:
  - 13 bits

- Indicates fragment position in original packet

---

### TTL (Time To Live)

- Size:
  - 8 bits

- Prevents infinite loops
- Router decrements TTL by 1
- Packet dropped when TTL reaches 0

- Practically functions as hop count

---

### Protocol Field

- Size:
  - 8 bits

- Identifies encapsulated Layer 4 protocol

| Value | Protocol |
|---|---|
| 1 | ICMP |
| 6 | TCP |
| 17 | UDP |
| 89 | OSPF |

---

### Header Checksum

- Size:
  - 16 bits

- Error-checking mechanism for IPv4 header

---

### Source & Destination IP

- Each field:
  - 32 bits

- Contains sender and receiver IP addresses

---

### Options Field

- Optional field
- Size:
  - 0–320 bits

- Rarely used
- If Header Length > 5:
  - Options field exists

---

### Wireshark Packet Capture

- Tool used to capture and analyze packets
- Helps inspect:
  - Headers
  - Protocols
  - Encapsulation

---

### Routing Fundamentals

#### What is Routing?

- Process routers use to determine packet path to destination
- Uses routing table to forward packets

---

### Routing Table

- Stores routes to destination networks
- Viewed using:
    show ip route

---

### Dynamic Routing

- Routers automatically share routing information
- Build routing tables dynamically

Examples:
- OSPF
- EIGRP
- RIP

---

### Static Routing

- Administrator manually configures routes

---

### Connected Routes

- Automatically added when:
  - Interface configured with IP
  - Interface enabled with `no shutdown`

Example:
- Interface:
  - `192.168.1.1/24`

Connected route:
- `192.168.1.0/24`

- Router knows:
  - Send packets for this network out that interface

---

### Local Routes

- Route to exact interface IP address

Example:
- `192.168.1.1/32`

- `/32` means exact IP only

- Router knows:
  - Packet destined for this IP is for itself

---

### Route Matching

- A route matches if destination IP belongs to that network

Example:
- Packet:
  - `192.168.1.1`

Matches:
- `192.168.1.0/24`
- `192.168.1.1/32`

Router selects:
- Most specific route

---

### Default Gateway

- End hosts send remote traffic to default gateway
- Used for destinations outside local network

---

### Static Route Configuration

#### Using Next-Hop IP

    ip route network-address netmask next-hop

Example:
    ip route 192.168.4.0 255.255.255.0 10.0.0.2

---

#### Using Exit Interface

    ip route network-address netmask exit-interface

Example:
    ip route 192.168.4.0 255.255.255.0 g0/0

---

#### Using Both

    ip route network-address netmask exit-interface next-hop

Example:
    ip route 192.168.4.0 255.255.255.0 g0/0 10.0.0.2

---

### Default Route

- Route:
    0.0.0.0/0

- Least specific route possible
- Matches all destination networks

---

## Terminal / CLI Practice

    # View routing table
    show ip route

    # Configure static route using next-hop
    ip route 192.168.4.0 255.255.255.0 10.0.0.2

    # Configure static route using exit interface
    ip route 192.168.4.0 255.255.255.0 g0/0

    # Configure default route
    ip route 0.0.0.0 0.0.0.0 10.0.0.1

    # View interface information
    show ip interface brief

---

## 🔑 Exam Focus Summary
**IPv4 header fields and functions are VERY important**  
**Version field = identifies IPv4/IPv6**  
**TTL prevents infinite routing loops**  
**Protocol field values:**  
- 1 = ICMP  
- 6 = TCP  
- 17 = UDP  
- 89 = OSPF  

**MTU usually = 1500 bytes**  
**Fragmentation occurs if packet > MTU**  
**Connected route = route to connected network**  
**Local route = exact interface IP (/32)**  
**Router chooses most specific matching route**  
**show ip route** displays routing table  
**Static routes are manually configured**  
**Default route = 0.0.0.0/0**  

---

## What I Didn't Understand
-

---

## 3 Key Things I Learned
1. How IPv4 header fields control packet forwarding, fragmentation, and protocol identification  
2. The difference between connected routes, local routes, and static routes  
3. How routers select the most specific matching route when forwarding packets  