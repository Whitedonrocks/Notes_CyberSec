# CompTIA A+ 220-1201 — Week 1 Day 2 Notes

---

## Videos Watched
- ✅ 1.3 Mobile Device Networks
- ✅ 1.3 Mobile Device Management
- ✅ 2.1 Introduction to IP

---

## Key Concepts

### 1.3 Mobile Device Networks

#### Cellular Networks
- Mobile devices can enable or disable voice and/or data separately
- **2G** — original digital cellular, voice only
- **3G** — introduced in 1998, added data connectivity, enabled GPS and mobile TV
- **4G / LTE** — Long Term Evolution
  - Based on **GSM** (Global System for Mobile Communication)
  - Also uses **EDGE** (Enhanced Data Rates for GSM Evolution)
  - LTE supports **150 Mbit/s**, LTE-A supports **300 Mbit/s**
- **5G** — introduced in 2020
  - Peak speed: **10 Gbps**
  - Real world speed: **100–900 Mbit/s**
  - Significant role in **IoT** (Internet of Things)

#### Wi-Fi
- **802.11** wireless network standard
- **Hotspot** — shares cellular data as a Wi-Fi connection for multiple devices
- **Tethering** — same as hotspot but for only 1 device

#### SIM Cards
- **SIM** — Subscriber Identity Module, identifies you on a cellular network
- **eSIM** — Embedded SIM, built directly into the device, no physical card needed
  - Can switch carriers without swapping physical SIM

#### Bluetooth
- **Pairing process** — devices discover each other and establish a trusted connection
- Short range **PAN** (Personal Area Network)
- Used for headsets, keyboards, speakers, wearables

#### GPS
- **GPS** — Global Positioning System, created by the US Department of Defence
- Uses **30+ satellites** orbiting Earth
- Determines location based on **timing differences** between satellite signals
- Provides **longitude, latitude, and altitude**
- Requires line of sight to at least 4 satellites for accurate positioning

---

### 1.3 Mobile Device Management (MDM)

#### What is MDM?
- System to manage company-owned AND user-owned mobile devices centrally
- Allows IT to set policies on apps, data, camera, screen lock, encryption etc.
- Manages access control remotely — can wipe a lost device

#### Device Ownership Models

| Model | Full Name | Who Owns Device |
|---|---|---|
| **BYOD** | Bring Your Own Device | Employee owns it — hard to secure |
| **COPE** | Corporate Owned, Personally Enabled | Company owns, employee can use personally |
| **CYOD** | Choose Your Own Device | Employee picks from approved list |

#### Data Synchronization
- Syncing data across devices — contacts, email, calendar, photos
- Cloud sync (Google, iCloud, OneDrive) keeps all devices updated
- MDM can control what data is allowed to sync and where

---

### 2.1 Introduction to IP

#### Network Basics
- **Network topology** — the layout/road map of a network (Ethernet, DSL, cable)
- Main protocols: **IP**, **TCP**, **UDP**
- These operate at **OSI Layer 4 — Transport Layer**
- **Multiplexing** — running many different applications at the same time over one connection

#### TCP — Transmission Control Protocol
- **Connection-oriented** — formal connection setup (handshake) and close
- Sends data and waits for confirmation it arrived (**return receipt**)
- Application does NOT need to worry about lost data — TCP handles it
- **Slower** but **reliable**
- Used by: **HTTPS**, **SSH** (Secure Shell), email

#### UDP — User Datagram Protocol
- **Connectionless** — no formal open or close, just sends data
- No confirmation that data arrived — application decides what to do if data is lost
- **Faster** — no overhead, ideal for real-time communication
- Used by: **DHCP**, **TFTP**, video streaming, VoIP, online gaming

#### TCP vs UDP Quick Comparison

| Feature | TCP | UDP |
|---|---|---|
| Connection | Connection-oriented | Connectionless |
| Reliability | Guaranteed delivery | No guarantee |
| Speed | Slower | Faster |
| Use case | HTTPS, SSH, email | Streaming, gaming, VoIP |

#### Port Numbers
- TCP and UDP use **port numbers** to know where data is going
- **Non-ephemeral ports (permanent)** — ports **0 to 1023**
  - Usually used by servers and services
- **Ephemeral ports (temporary)** — ports **1024 to 65535**
  - Assigned temporarily to client applications
- Port numbers are for **communication routing**, not security
- TCP and UDP port numbers are **separate and unique** to each protocol

#### Common Port Numbers to Memorize
| Port | Protocol | Use |
|---|---|---|
| 22 | TCP | SSH |
| 53 | UDP | DNS |
| 67/68 | UDP | DHCP |
| 80 | TCP | HTTP |
| 443 | TCP | HTTPS |
| 3389 | TCP | RDP (Remote Desktop) |

---

## TryHackMe — What is Networking?

### What is a Network?
- Networks are simply things connected together
- The **Internet** is one giant network made up of many small private networks
- Small networks = **private networks**
- Networks connecting them = **public networks** (the Internet)

### History of the Internet
- **Late 1960s** — ARPANET, first documented network, funded by the US Defence Department
- **1989** — Tim Berners-Lee invented the **World Wide Web (WWW)**

### Device Identification
Every device on a network has two means of identification:
- **IP Address** — logical address, can change
  - Each section of an IP address is called an **octet**
  - Example: 192.168.1.1 has four octets
- **MAC Address** — Media Access Control, physical address burned into hardware, permanent

### Ping
- Uses **ICMP** (Internet Control Message Protocol) packets
- Measures the **performance and response time** of a connection between devices
- Command: `ping google.com`

### Additional Important Concepts

#### IPv4 vs IPv6
- **IPv4** — 32-bit address, ~4.3 billion addresses (running out)
  - Example: 192.168.1.1
- **IPv6** — 128-bit address, virtually unlimited addresses
  - Example: 2400:1a00:3b6f::1

#### Public vs Private IP Addresses
- **Private IP** — used inside your home/office network (192.168.x.x)
- **Public IP** — used on the internet, assigned by your ISP
- Your router translates between them using **NAT** (Network Address Translation)

---

## What I Didn't Understand
- TCP vs UDP — need to understand better (re-read comparison table above)
- How does the TCP handshake actually work? *(research for Day 3)*

## 3 Key Things I Learned
1. 5G operates at up to 10 Gbps peak but real world is 100-900 Mbit/s
2. TCP guarantees delivery, UDP sacrifices reliability for speed
3. Port numbers 0-1023 are permanent server ports, 1024-65535 are temporary client ports