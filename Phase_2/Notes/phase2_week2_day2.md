# CCNA 200-301 — Phase 2 Week 2 Day 2 Notes

**Lab Files:** https://drive.google.com/drive/folders/1PwK_jWqfUtOjV7gHt8ODutq9QA5cxCgi

---

## Videos Watched
- ✅ Day 13 — Subnetting Part 1
- ✅ Day 14 — Subnetting Part 2

---

## Key Concepts

### What is Subnetting?

- Subnetting is the process of dividing a large network into smaller networks
- These smaller networks are called:
  - Subnetworks
  - Subnets

Purpose of subnetting:
- Better IP address usage
- Smaller broadcast domains
- Better performance
- Improved security
- Easier network management

---

## IPv4 Address Classes

Originally IPv4 used fixed network classes.

---

### Class A

| Property | Value |
|---|---|
| First Octet Range | 0–126 |
| Default Prefix | /8 |
| Default Netmask | 255.0.0.0 |

- Very large networks
- Supports many hosts

Example:
- `10.0.0.0/8`

---

### Class B

| Property | Value |
|---|---|
| First Octet Range | 128–191 |
| Default Prefix | /16 |
| Default Netmask | 255.255.0.0 |

- Medium-sized networks

Example:
- `172.16.0.0/16`

---

### Class C

| Property | Value |
|---|---|
| First Octet Range | 192–223 |
| Default Prefix | /24 |
| Default Netmask | 255.255.255.0 |

- Small networks

Example:
- `192.168.1.0/24`

---

### Class D

| Property | Value |
|---|---|
| Range | 224–239 |
| Purpose | Multicast |

---

### Class E

| Property | Value |
|---|---|
| Range | 240–255 |
| Purpose | Experimental |

---

## IANA

### Internet Assigned Numbers Authority

- Organization responsible for assigning:
  - IPv4 addresses
  - IPv6 addresses
  - Autonomous System Numbers (ASN)

- Allocates address blocks to:
  - ISPs
  - Companies
  - Organizations

---

## Point-to-Point Networks

- A network connecting exactly TWO devices

Examples:
- Router ↔ Router
- Firewall ↔ Router

Common subnet used:
- `/30`

Reason:
- Provides exactly 2 usable host addresses

Example:
- `192.168.1.0/30`

| Address Type | Address |
|---|---|
| Network Address | 192.168.1.0 |
| Host 1 | 192.168.1.1 |
| Host 2 | 192.168.1.2 |
| Broadcast Address | 192.168.1.3 |

---

## CIDR (Classless Inter-Domain Routing)

Before CIDR:
- Networks had fixed sizes:
  - Class A = /8
  - Class B = /16
  - Class C = /24

Problem:
- Wasted many IP addresses

---

### CIDR Solution

CIDR removed fixed class restrictions.

Benefits:
- More efficient IP allocation
- Allows subnetting
- Flexible network sizes
- Reduces waste

---

## Borrowing Host Bits

Subnetting works by:
- Borrowing bits from host portion
- Converting them into network bits

---

## Formula for Number of Subnets

    2^x

Where:
- `x = borrowed bits`

---

## CIDR Subnet Table

| Dotted Decimal | CIDR | Total Addresses | Number of Subnets |
|---|---|---|---|
| 255.255.255.128 | /25 | 128 | 2 |
| 255.255.255.192 | /26 | 64 | 4 |
| 255.255.255.224 | /27 | 32 | 8 |
| 255.255.255.240 | /28 | 16 | 16 |
| 255.255.255.248 | /29 | 8 | 32 |
| 255.255.255.252 | /30 | 4 | 64 |
| 255.255.255.254 | /31 | 2 | 128 |
| 255.255.255.255 | /32 | 1 | 256 |

---

## Understanding Class C Subnetting

Original network:
- `192.168.1.0/24`

Default:
- 24 network bits
- 8 host bits

---

## CIDR Subnet Table — Class B (/16 Base Network)

| Dotted Decimal | CIDR | Total Addresses per Subnet | Number of Subnets |
|---|---|---|---|
| 255.255.128.0 | /17 | 32768 | 2 |
| 255.255.192.0 | /18 | 16384 | 4 |
| 255.255.224.0 | /19 | 8192 | 8 |
| 255.255.240.0 | /20 | 4096 | 16 |
| 255.255.248.0 | /21 | 2048 | 32 |
| 255.255.252.0 | /22 | 1024 | 64 |
| 255.255.254.0 | /23 | 512 | 128 |
| 255.255.255.0 | /24 | 256 | 256 |
| 255.255.255.128 | /25 | 128 | 512 |
| 255.255.255.192 | /26 | 64 | 1024 |
| 255.255.255.224 | /27 | 32 | 2048 |
| 255.255.255.240 | /28 | 16 | 4096 |
| 255.255.255.248 | /29 | 8 | 8192 |
| 255.255.255.252 | /30 | 4 | 16384 |
| 255.255.255.254 | /31 | 2 | 32768 |
| 255.255.255.255 | /32 | 1 | 65536 |

---

### Example: /26 Subnet

Borrow:
- 2 host bits

Calculation:
- `2^2 = 4 subnets`

New subnet mask:
- `255.255.255.192`

---

### Resulting Subnets

| Subnet | Range |
|---|---|
| 192.168.1.0/26 | 0–63 |
| 192.168.1.64/26 | 64–127 |
| 192.168.1.128/26 | 128–191 |
| 192.168.1.192/26 | 192–255 |

---

### Example Subnet Breakdown

#### Subnet: 192.168.1.0/26

| Type | Address |
|---|---|
| Network Address | 192.168.1.0 |
| First Host | 192.168.1.1 |
| Last Host | 192.168.1.62 |
| Broadcast Address | 192.168.1.63 |

Hosts:
- `64 - 2 = 62 usable hosts`

---

## Subnetting a Class B Network

Original network:
- `172.16.0.0/16`

Default:
- 16 network bits
- 16 host bits

---

### Example: Borrow 4 Bits

New prefix:
- `/20`

Calculation:
- `2^4 = 16 subnets`

New subnet mask:
- `255.255.240.0`

---

### Block Size Calculation

Interesting octet:
- Third octet

Subnet mask:
- `240`

Calculation:
- `256 - 240 = 16`

Block size:
- 16

---

### Resulting Subnets

| Subnet |
|---|
| 172.16.0.0/20 |
| 172.16.16.0/20 |
| 172.16.32.0/20 |
| 172.16.48.0/20 |
| 172.16.64.0/20 |
| 172.16.80.0/20 |

Continues in increments of 16.

---

### Example Subnet Breakdown

#### Subnet: 172.16.32.0/20

| Type | Address |
|---|---|
| Network Address | 172.16.32.0 |
| First Host | 172.16.32.1 |
| Last Host | 172.16.47.254 |
| Broadcast Address | 172.16.47.255 |

---

## Subnetting Concepts

### Borrowed Bits
- Bits taken from host portion

---

### Network Bits
- Identify subnet/network

---

### Host Bits
- Identify hosts inside subnet

---

### Block Size Formula

    256 - subnet-mask-value

Used to determine subnet increments.

---

## Why Subnetting is Important

- Reduces broadcast traffic
- Improves performance
- Better security separation
- Efficient address usage
- Easier troubleshooting

---

## Terminal / CLI Practice

    # View interface IP addresses
    show ip interface brief

    # View routing table
    show ip route

    # Configure interface IP
    interface g0/0
    ip address 192.168.1.1 255.255.255.192
    no shutdown

    # Test connectivity
    ping 192.168.1.10

---

## 🔑 Exam Focus Summary
**Subnetting = dividing networks into smaller subnets**  
**CIDR removed fixed class limitations**  
**Class A = /8**  
**Class B = /16**  
**Class C = /24**  
**Formula for subnets = 2^borrowed_bits**  
**/30 commonly used for point-to-point networks**  
**Block size formula = 256 - subnet mask value**  
**Know network address, broadcast address, first/last usable host**  
**Subnet masks and CIDR notation are VERY important for CCNA**  
**/26 creates 4 subnets from a /24 network**  
**Borrowing bits reduces available host addresses**  

---

## What I Didn't Understand
-

---

## 3 Key Things I Learned
1. How CIDR allows flexible subnetting instead of fixed address classes  
2. How borrowing host bits creates additional subnets  
3. How to calculate subnet ranges, broadcast addresses, and usable hosts in both Class C and Class B networks  