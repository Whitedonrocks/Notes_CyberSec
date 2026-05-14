# CCNA 200-301 — Phase 2 Week 2 Day 4 Notes

**Lab Files:** https://drive.google.com/drive/folders/1PwK_jWqfUtOjV7gHt8ODutq9QA5cxCgi

---

## Videos Watched
- ✅ Day 16 — VLANs Part 1
- ✅ Day 16 Lab — VLAN Configuration Lab

---

## Key Concepts

# VLANs (Virtual Local Area Networks)

---

## What is a LAN?

### LAN (Local Area Network)
- A LAN is a network contained within a relatively small geographical area
- Example:
  - Home network
  - Office floor
  - School lab

---

## Broadcast Domain

### What is a Broadcast Domain?
- A broadcast domain is:
  - The group of devices that receive a broadcast frame

---

### Broadcast MAC Address

Ethernet broadcast MAC:
    FFFF.FFFF.FFFF

- When a device sends a broadcast frame:
  - ALL devices in the same broadcast domain receive it

---

## Example Without VLANs

Imagine:
- 1 switch
- 20 PCs connected

Result:
- All 20 PCs belong to SAME broadcast domain

Meaning:
- Any broadcast frame sent by one PC reaches ALL devices

---

## Problems with Large Broadcast Domains

### Too Many Broadcasts
- Broadcast traffic wastes bandwidth
- Every device must process broadcasts

---

### Security Issues
- Devices can communicate freely
- Easier for attackers to:
  - Scan devices
  - Capture traffic
  - Spread malware

---

### Poor Network Organization
- No separation between departments
- HR, IT, Finance all mixed together

---

# What is a VLAN?

## VLAN (Virtual Local Area Network)

- VLANs logically separate devices at Layer 2
- VLANs divide one physical switch into multiple logical networks

---

## Important VLAN Concept

WITHOUT VLANs:
- One switch = one broadcast domain

WITH VLANs:
- One switch can contain MULTIPLE broadcast domains

---

## Example

| VLAN | Department |
|---|---|
| VLAN 10 | HR |
| VLAN 20 | IT |
| VLAN 30 | Finance |

Even if connected to same switch:
- Devices in VLAN 10 do NOT receive broadcasts from VLAN 20
- Devices in VLAN 20 do NOT receive broadcasts from VLAN 30

---

## VLAN Behavior

### Switches DO NOT Forward:
- Broadcast traffic between VLANs
- Unknown unicast traffic between VLANs
- Normal unicast traffic between VLANs

Meaning:
- VLANs isolate traffic

---

## Communication Between VLANs

Devices in different VLANs CANNOT communicate directly through a switch alone

To communicate between VLANs:
- A router or Layer 3 switch is required

This process is called:
- Inter-VLAN Routing

---

# VLAN Configuration

## Viewing VLANs

Command:
```bash
show vlan brief
```

Displays:
- VLAN IDs
- VLAN names
- Assigned ports

---

# Access Ports

## What is an Access Port?

- A switch port assigned to ONE VLAN only
- Usually connects to:
  - PCs
  - Printers
  - Servers

---

## Example

PC connected to:
- Interface G1/0

Assigned VLAN:
- VLAN 10

Traffic entering interface:
- Belongs to VLAN 10

---

# Trunk Ports

## What is a Trunk Port?

- A port that carries MULTIPLE VLANs
- Usually used between:
  - Switch ↔ Switch
  - Switch ↔ Router
  - Switch ↔ Layer 3 Switch

---

## Access vs Trunk Ports

| Feature | Access Port | Trunk Port |
|---|---|---|
| VLANs Carried | One | Multiple |
| Usually Connects To | End devices | Network devices |
| VLAN Tagging | No | Yes |

---

# VLAN Configuration Commands

## Create VLAN

```bash
vlan 10
```

---

## Name VLAN

```bash
name HR
```

---

## Configure Access Interface

```bash
interface g1/0
switchport mode access
switchport access vlan 10
```

Meaning:
- Interface becomes access port
- Assigned to VLAN 10

---

## Configure Multiple Interfaces

```bash
interface range g1/0-3
switchport mode access
switchport access vlan 10
```

---

# Example VLAN Setup

| Interface | VLAN |
|---|---|
| G1/0 | VLAN 10 |
| G1/1 | VLAN 10 |
| G1/2 | VLAN 20 |
| G1/3 | VLAN 30 |

---

# VLAN Benefits

## Security
- Separates departments/users
- Reduces unauthorized access

---

## Better Performance
- Smaller broadcast domains
- Less unnecessary traffic

---

## Easier Management
- Organize users logically
- Devices can move without changing physical topology

---

## Flexibility
- Same VLAN can exist across different switches

---

# Native VLAN (Important)

- Trunk ports use VLAN tagging
- Native VLAN traffic is sent UNTAGGED

Default native VLAN:
- VLAN 1

---

# VLAN 1

- Default VLAN on Cisco switches
- All ports belong to VLAN 1 by default

Security Best Practice:
- Avoid using VLAN 1 for user traffic

---

# VLAN Tagging (802.1Q)

- Trunk ports use:
  - IEEE 802.1Q tagging

Purpose:
- Identifies which VLAN traffic belongs to

---

# VLAN Traffic Example

Scenario:
- PC1 in VLAN 10
- PC2 in VLAN 20

Result:
- Switch will NOT forward traffic directly between them

Reason:
- Different broadcast domains

---

# VLANs and Cybersecurity

## Benefits

- Limits broadcast traffic
- Reduces attack surface
- Isolates departments
- Helps prevent lateral movement by attackers

---

## VLAN Hopping Attack

Attackers may try:
- Jumping between VLANs

Mitigation:
- Disable unused ports
- Avoid default VLAN 1
- Proper trunk configuration

---

## Best Practices

- Shut down unused interfaces
- Use separate VLANs for departments
- Restrict trunk ports
- Change native VLAN from VLAN 1

---

## Terminal / CLI Practice

```bash
# View VLANs
show vlan brief

# Create VLAN
vlan 10

# Name VLAN
name HR

# Configure access interface
interface g1/0
switchport mode access
switchport access vlan 10

# Configure interface range
interface range g1/0-3
switchport mode access
switchport access vlan 20

# View running config
show running-config
```

---

## 🔑 Exam Focus Summary

**LAN = single broadcast domain**  
**Broadcast MAC = FFFF.FFFF.FFFF**  
**VLAN = logical Layer 2 separation**  
**One VLAN = one broadcast domain**  
**Switches do NOT forward traffic between VLANs**  
**Access port = single VLAN**  
**Trunk port = multiple VLANs**  
**802.1Q = VLAN tagging protocol**  
**Default VLAN = VLAN 1**  
**Use `show vlan brief` to verify VLANs**  
**Inter-VLAN communication requires router or Layer 3 switch**  
**VLANs improve security and reduce broadcasts**  

---

## What I Didn't Understand
-

---

## 3 Key Things I Learned
1. VLANs divide one physical switch into multiple logical broadcast domains  
2. Access ports carry one VLAN while trunk ports carry multiple VLANs  
3. Devices in different VLANs cannot communicate directly without inter-VLAN routing  