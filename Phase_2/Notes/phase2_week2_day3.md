# CCNA 200-301 — Phase 2 Week 2 Day 3 Notes

**Lab Files:** https://drive.google.com/drive/folders/1PwK_jWqfUtOjV7gHt8ODutq9QA5cxCgi

---

## Videos Watched
- ✅ Day 15 — Subnetting Part 3
- ✅ Day 15 Lab — VLSM Subnetting Lab

---

## Key Concepts

### Subnetting Class A Networks

Original Class A network:
- `/8`

Default subnet mask:
- `255.0.0.0`

---

### Class A Characteristics

| Property | Value |
|---|---|
| First Octet Range | 0–126 |
| Default Prefix | /8 |
| Default Netmask | 255.0.0.0 |

---

### Why Subnet Class A?

- Class A networks are extremely large
- Huge waste of addresses if not subnetted
- Subnetting improves:
  - Efficiency
  - Security
  - Broadcast control

---

## Example Class A Network

Original network:
- `10.0.0.0/8`

Default:
- 8 network bits
- 24 host bits

---

## Example: Subnetting to /16

Borrow:
- 8 bits

New prefix:
- `/16`

New subnet mask:
- `255.255.0.0`

---

### Number of Subnets

Formula:
    2^borrowed_bits

Calculation:
    2^8 = 256 subnets

---

### Hosts Per Subnet

Remaining host bits:
- 16

Formula:
    2^16 - 2

Calculation:
    65536 - 2 = 65534 hosts

---

## Resulting Subnets

| Subnet |
|---|
| 10.0.0.0/16 |
| 10.1.0.0/16 |
| 10.2.0.0/16 |
| 10.3.0.0/16 |
| 10.4.0.0/16 |

---

## Example Subnet Breakdown

### Subnet: 10.2.0.0/16

| Type | Address |
|---|---|
| Network Address | 10.2.0.0 |
| First Host | 10.2.0.1 |
| Last Host | 10.2.255.254 |
| Broadcast Address | 10.2.255.255 |

---

## Example: Subnetting Further to /24

Original:
- `10.0.0.0/8`

New prefix:
- `/24`

Borrowed bits:
- 16

---

### Number of Subnets

Calculation:
    2^16 = 65536 subnets

---

### Hosts Per Subnet

Remaining host bits:
- 8

Calculation:
    2^8 - 2 = 254 hosts

---

## Resulting Subnets

| Subnet |
|---|
| 10.0.0.0/24 |
| 10.0.1.0/24 |
| 10.0.2.0/24 |
| 10.0.3.0/24 |

---

## CIDR Subnet Table — Class A (/8 Base Network)

| Dotted Decimal | CIDR | Total Addresses per Subnet | Number of Subnets |
|---|---|---|---|
| 255.128.0.0 | /9 | 8388608 | 2 |
| 255.192.0.0 | /10 | 4194304 | 4 |
| 255.224.0.0 | /11 | 2097152 | 8 |
| 255.240.0.0 | /12 | 1048576 | 16 |
| 255.248.0.0 | /13 | 524288 | 32 |
| 255.252.0.0 | /14 | 262144 | 64 |
| 255.254.0.0 | /15 | 131072 | 128 |
| 255.255.0.0 | /16 | 65536 | 256 |
| 255.255.128.0 | /17 | 32768 | 512 |
| 255.255.192.0 | /18 | 16384 | 1024 |
| 255.255.224.0 | /19 | 8192 | 2048 |
| 255.255.240.0 | /20 | 4096 | 4096 |
| 255.255.248.0 | /21 | 2048 | 8192 |
| 255.255.252.0 | /22 | 1024 | 16384 |
| 255.255.254.0 | /23 | 512 | 32768 |
| 255.255.255.0 | /24 | 256 | 65536 |
| 255.255.255.128 | /25 | 128 | 131072 |
| 255.255.255.192 | /26 | 64 | 262144 |
| 255.255.255.224 | /27 | 32 | 524288 |
| 255.255.255.240 | /28 | 16 | 1048576 |
| 255.255.255.248 | /29 | 8 | 2097152 |
| 255.255.255.252 | /30 | 4 | 4194304 |
| 255.255.255.254 | /31 | 2 | 8388608 |
| 255.255.255.255 | /32 | 1 | 16777216 |

---

# Variable Length Subnet Mask (VLSM)

## What is VLSM?

- VLSM stands for:
  - Variable Length Subnet Mask

- Allows creation of subnets with DIFFERENT sizes

---

## Before VLSM — FLSM

### FLSM (Fixed Length Subnet Mask)

- All subnets use SAME subnet mask

Example:
- Every subnet uses `/24`

Problem:
- Wastes IP addresses

---

## Why VLSM is Better

- Different departments/networks need different numbers of hosts
- VLSM creates subnet sizes based on actual need

Benefits:
- Efficient IP usage
- Less waste
- Better scalability

---

## VLSM Process

### Step 1
- Identify required host counts

---

### Step 2
- Sort from largest to smallest subnet

---

### Step 3
- Assign largest subnet FIRST

---

### Step 4
- Assign next largest subnet after previous subnet

---

### Step 5
- Continue until all subnets assigned

---

# VLSM Example

## Given Network

Main network:
- `192.168.1.0/24`

Need subnets for:

| Department | Hosts Needed |
|---|---|
| Sales | 100 |
| IT | 50 |
| HR | 25 |
| WAN Link | 2 |

---

# Step 1 — Largest Subnet First

## Sales — 100 Hosts

Hosts needed:
- 100

Required subnet:
- `/25`

Why?
- `/25 = 128 addresses`
- `126 usable hosts`

Assigned subnet:
- `192.168.1.0/25`

Range:
- `192.168.1.0 – 192.168.1.127`

---

# Step 2 — Second Largest

## IT — 50 Hosts

Required subnet:
- `/26`

Why?
- `/26 = 64 addresses`
- `62 usable hosts`

Next available subnet:
- `192.168.1.128/26`

Range:
- `192.168.1.128 – 192.168.1.191`

---

# Step 3 — Third Largest

## HR — 25 Hosts

Required subnet:
- `/27`

Why?
- `/27 = 32 addresses`
- `30 usable hosts`

Next available subnet:
- `192.168.1.192/27`

Range:
- `192.168.1.192 – 192.168.1.223`

---

# Step 4 — Smallest Subnet

## WAN Link — 2 Hosts

Required subnet:
- `/30`

Why?
- `/30 = 4 addresses`
- `2 usable hosts`

Next available subnet:
- `192.168.1.224/30`

Range:
- `192.168.1.224 – 192.168.1.227`

---

## Final VLSM Allocation

| Department | Subnet |
|---|---|
| Sales | 192.168.1.0/25 |
| IT | 192.168.1.128/26 |
| HR | 192.168.1.192/27 |
| WAN | 192.168.1.224/30 |

---

## Important VLSM Rules

- Always assign largest subnet first
- Avoid overlapping ranges
- Use smallest subnet possible for efficiency
- Point-to-point links usually use `/30`

---

## FLSM vs VLSM

| Feature | FLSM | VLSM |
|---|---|---|
| Subnet Size | Same | Different |
| Efficiency | Lower | Higher |
| Complexity | Easier | More complex |
| Address Waste | More | Less |

---

## Terminal / CLI Practice

    # Configure interface IP
    interface g0/0
    ip address 192.168.1.1 255.255.255.128
    no shutdown

    # View interfaces
    show ip interface brief

    # View routing table
    show ip route

    # Test connectivity
    ping 192.168.1.10

---

## 🔑 Exam Focus Summary
**Class A default prefix = /8**  
**Subnetting borrows bits from host portion**  
**Formula for subnets = 2^borrowed_bits**  
**Formula for hosts = 2^host_bits - 2**  
**VLSM = Variable Length Subnet Mask**  
**FLSM = Fixed Length Subnet Mask**  
**VLSM creates different subnet sizes**  
**Always assign largest subnet FIRST in VLSM**  
**/30 commonly used for point-to-point links**  
**VLSM is more efficient than FLSM**  
**Know network address, broadcast address, first/last usable host calculations**  

---

## What I Didn't Understand
-

---

## 3 Key Things I Learned
1. How Class A networks can be divided into thousands of smaller subnets  
2. How VLSM allows different subnet sizes based on host requirements  
3. Why assigning the largest subnet first prevents address overlap and IP wastage  