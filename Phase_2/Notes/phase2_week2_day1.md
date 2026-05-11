# CCNA 200-301 — Phase 2 Week 2 Day 1 Notes

**Lab Files:** https://drive.google.com/drive/folders/1PwK_jWqfUtOjV7gHt8ODutq9QA5cxCgi

---

## Videos Watched
- ✅ Day 12 — The Life of a Packet
- ✅ Day 12 Lab — The Life of a Packet

---

## Key Concepts

### What is “The Life of a Packet”?

- Describes how data travels from a source device to a destination device across networks
- Explains:
  - ARP process
  - Encapsulation
  - MAC address changes
  - IP address preservation
  - Router forwarding process

---

### Communication Inside the Same Network

If devices are in the same LAN:
- Source device sends frame directly to destination
- Uses destination device MAC address

---

### Communication Between Different Networks

If destination is on another network:
- Source device sends packet to default gateway (router)

Important:
- IP addresses stay the same end-to-end
- MAC addresses change at every hop

---

## Step-by-Step Packet Flow

### Example Network

| Device | IP Address |
|---|---|
| PC1 | 192.168.1.10 |
| R1 G0/0 | 192.168.1.1 |
| R2 G0/0 | 192.168.2.1 |
| PC2 | 192.168.2.10 |

---

### Step 1 — PC1 Checks Destination

- PC1 wants to send data to:
    192.168.2.10

- PC1 compares destination network with its own subnet

Result:
- Destination is on different network

Therefore:
- Packet must be sent to default gateway:
    192.168.1.1

---

### Step 2 — ARP Request

PC1 does NOT know router MAC address.

So PC1 sends:
- ARP Request

ARP Request characteristics:
- Broadcast frame
- Destination MAC:
    FF:FF:FF:FF:FF:FF

Question asked:
- “Who has 192.168.1.1?”

---

### Step 3 — ARP Reply

Router R1 replies with:
- ARP Reply

ARP Reply characteristics:
- Unicast frame
- Sent only to PC1

Contains:
- Router MAC address

---

### Step 4 — PC1 Sends Packet

Now PC1 builds packet.

#### Layer 3 (IP Header)

| Field | Value |
|---|---|
| Source IP | 192.168.1.10 |
| Destination IP | 192.168.2.10 |

Important:
- IP addresses remain unchanged end-to-end

---

#### Layer 2 (Ethernet Header)

| Field | Value |
|---|---|
| Source MAC | PC1 MAC |
| Destination MAC | R1 MAC |

---

### Step 5 — Router Receives Frame

Router R1:
1. Removes Ethernet header/trailer
2. Checks destination IP
3. Looks in routing table
4. Determines next hop

This process is called:
- Decapsulation
- Routing decision
- Re-encapsulation

---

### Step 6 — Router Uses ARP Again

Router now needs MAC address of next device.

If MAC unknown:
- Router sends ARP Request

Receives:
- ARP Reply

Stores result in ARP table

---

### Step 7 — Router Rebuilds Ethernet Frame

Router creates NEW Ethernet frame.

Important:
- Source & destination MAC addresses change
- Source & destination IP addresses stay the same

---

### Step 8 — Process Repeats

At every router:
1. Remove old Ethernet frame
2. Read IP packet
3. Determine next hop
4. Build new Ethernet frame
5. Forward packet

Repeat until destination reached

---

### Final Step — Packet Arrives at Destination

Destination device:
- Receives frame
- Removes headers
- Passes data to upper layers

This is:
- Decapsulation

---

## ARP Behavior During Reply Traffic

When destination sends reply:
- Usually NO ARP needed

Reason:
- Devices already learned MAC addresses during initial communication
- Entries stored in ARP table/cache

---

## Important Concept

### IP vs MAC Addresses

#### IP Addresses
- Stay SAME from source to destination
- Used for routing between networks

---

#### MAC Addresses
- Change at EVERY hop
- Used only for local delivery

---

### Encapsulation & Decapsulation

#### Encapsulation
- Adding headers/trailers before transmission

---

#### Decapsulation
- Removing headers/trailers after reception

---

### ARP (Address Resolution Protocol)

Used to map:
- IP address → MAC address

---

#### ARP Request
- Broadcast

---

#### ARP Reply
- Unicast

---

## Life of a Packet Summary

1. Source determines if destination is local or remote
2. If remote → send to default gateway
3. ARP used to discover MAC addresses
4. Packet encapsulated into Ethernet frame
5. Routers remove/rebuild Layer 2 headers
6. MAC addresses change at every hop
7. IP addresses remain unchanged
8. Process repeats until destination reached

---

## Terminal / CLI Practice

    # View ARP table
    show arp

    # View MAC address table (switch)
    show mac address-table

    # View routing table
    show ip route

    # Test connectivity
    ping 192.168.2.10

    # View interface information
    show ip interface brief

---

## 🔑 Exam Focus Summary
**ARP Request = Broadcast**  
**ARP Reply = Unicast**  
**IP addresses stay the SAME end-to-end**  
**MAC addresses change at every hop**  
**Routers remove and rebuild Ethernet frames**  
**ARP maps IP addresses to MAC addresses**  
**Default gateway used for remote networks**  
**Encapsulation = adding headers**  
**Decapsulation = removing headers**  
**Switches forward using MAC addresses**  
**Routers forward using IP addresses**  

---

## What I Didn't Understand
-

---

## 3 Key Things I Learned
1. MAC addresses change at every router hop while IP addresses stay unchanged from source to destination  
2. ARP is required before communication so devices can discover MAC addresses  
3. Routers decapsulate and re-encapsulate frames every time they forward packets between networks  