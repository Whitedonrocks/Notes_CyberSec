# CCNA 200-301 — Phase 2 Week 1 Day 6 Notes

**Lab Files:** https://drive.google.com/drive/folders/1PwK_jWqfUtOjV7gHt8ODutq9QA5cxCgi

---

## Videos Watched
- ✅ Day 9 — Switch Interfaces
- ✅ Day 9 Lab — Configuring Interfaces

---

## Key Concepts

### Viewing Switch Interfaces

#### Show IP Interface Brief

Command:
    show ip interface brief

Displays:
- Interface names
- IP addresses
- Status
- Protocol state

---

#### Show Interface Status

Command:
    show interfaces status

Output fields:

| Field | Meaning |
|---|---|
| Port | Interface name |
| Name | Interface description |
| Status | Connected/not connected |
| VLAN | Assigned VLAN |
| Duplex | Full/Half |
| Speed | Interface speed |
| Type | Cable/interface type |

---

### Configuring Interface Speed & Duplex

Enter configuration mode:
    configure terminal

Select interface:
    interface fastethernet 0/1

Set speed:
    speed 100

Set duplex:
    duplex full

Add description:
    description ##to R1##

---

### Configuring Multiple Interfaces

#### Interface Range

Example:
    interface range f0/5-12

Multiple ranges:
    interface range f0/5-6 , f0/9-12

---

#### Disable Unused Ports

Add description:
    description not in use

Disable interface:
    shutdown

---

### Full Duplex vs Half Duplex

#### Half Duplex
- Device cannot send and receive simultaneously
- Must wait before transmitting
- Common in older hub-based networks

---

#### Full Duplex
- Device can send and receive at the same time
- No waiting required
- Used in modern switched networks

---

### LAN Hubs & Collision Domains

#### Hub
- Operates at Layer 1
- Sends received frames to ALL ports
- All devices share the same bandwidth

---

#### Collision Domain
- Area where Ethernet collisions can occur

With a hub:
- Entire hub = ONE collision domain

With a switch:
- EACH switch port = separate collision domain

---

### CSMA/CD

#### Carrier Sense Multiple Access with Collision Detection

Used in half-duplex Ethernet networks.

Process:
1. Device listens before sending
2. If line is free → send frame
3. If collision occurs:
   - Send jamming signal
   - Stop transmission
4. Wait random time
5. Try again

---

### Collision Domains: Hub vs Switch

#### Hub
- One collision domain
- More collisions
- Lower efficiency

#### Switch
- Separate collision domain per port
- Fewer/no collisions
- Better performance

---

### Speed & Duplex Auto-Negotiation

- Interfaces support:
  - `speed auto`
  - `duplex auto`

- Devices advertise capabilities
- Negotiate best supported settings automatically

---

#### If Auto-Negotiation is Disabled

##### Speed
- Switch tries to detect speed
- If detection fails:
  - Uses slowest supported speed

---

##### Duplex
- If speed = 10 or 100 Mbps:
  - Uses half duplex

- If speed = 1000 Mbps or greater:
  - Uses full duplex

---

### Interface Errors

Command:
    show interfaces

---

#### Runts
- Frames smaller than 64 bytes

---

#### Giants
- Frames larger than 1518 bytes

---

#### CRC Errors
- Frame failed CRC check in Ethernet trailer
- Usually caused by:
  - Cabling issues
  - Duplex mismatch
  - Electrical interference

---

#### Input Errors
- Errors while receiving traffic

---

#### Output Errors
- Errors while sending traffic

---

## Terminal / CLI Practice

    # View interface summary
    show ip interface brief

    # View switch interface status
    show interfaces status

    # Enter configuration mode
    configure terminal

    # Configure interface
    interface fastethernet 0/1

    # Set speed and duplex
    speed 100
    duplex full

    # Add description
    description ##to R1##

    # Configure multiple interfaces
    interface range f0/5-12

    # Disable unused ports
    shutdown

    # View detailed interface statistics
    show interfaces

---

## 🔑 Exam Focus Summary
**show ip interface brief** = interface summary  
**show interfaces status** = switch port status  
**speed** and **duplex** commands configure interfaces  
**interface range** configures multiple interfaces at once  
**shutdown** disables interface  
**Half duplex** = cannot send & receive simultaneously  
**Full duplex** = send & receive simultaneously  
**Hub = one collision domain**  
**Switch = one collision domain per port**  
**CSMA/CD** handles Ethernet collisions  
**Auto-negotiation** automatically selects speed/duplex  
**Runts < 64 bytes**  
**Giants > 1518 bytes**  
**CRC errors** often caused by cabling or duplex mismatch  

---

## What I Didn't Understand
-

---

## 3 Key Things I Learned
1. How switches separate collision domains and improve network efficiency compared to hubs  
2. The difference between half duplex and full duplex communication  
3. How to configure switch interfaces, interface ranges, and troubleshoot interface errors  