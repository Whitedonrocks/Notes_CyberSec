# CompTIA A+ 220-1201 — Week 1 Day 7 Notes

---

## Videos Watched
- ✅ 3.2 Storage Cables
- ✅ 3.2 Adapters and Converters
- ✅ 3.2 Copper Connectors
- ✅ 3.2 Fiber Connectors
- ✅ 3.3 An Overview of Memory
- ✅ 3.3 Memory Technologies
- ✅ 3.4 Storage Devices
- ✅ 3.4 RAID

---

## Key Concepts

### 3.2 Storage Cables

#### SATA — Serial AT Attachment
- Standard interface for connecting storage drives to motherboards
- **2 cables per drive:** 15-pin power + 7-pin data
- **One-to-one connection** — each drive gets its own cable to the motherboard
- Hot-swappable in most modern systems

| Version | Max Speed | Notes |
|---|---|---|
| SATA 1.0 | 1.5 Gbps | First generation, rarely seen |
| SATA 2.0 | 3 Gbps | Doubled speed, common in older systems |
| SATA 3.0 | 6 Gbps | Current standard, most HDDs and SSDs |
| SATA 3.2 | 16 Gbps | SATA Express, rarely adopted |

- **Maximum cable length:** 1 metre (internal)
- L-shaped connector — can only plug in one way (keyed)
- **Cybersecurity use:** Physical access to SATA drives = easy data extraction

#### eSATA — External SATA
- External version of SATA for connecting drives outside the case
- **Maximum cable length:** 2 metres
- Faster than USB 2.0 when it launched but now replaced by USB 3.0 and Thunderbolt
- **Differences between SATA and eSATA:**

| Feature | SATA | eSATA |
|---|---|---|
| Use | Internal drives | External drives |
| Cable length | 1 metre | 2 metres |
| Power | Separate power cable | No power (drive needs own power) |
| Connector shape | L-shaped | Flat, more robust |
| Speed | Up to 6 Gbps | Up to 6 Gbps |

---

### 3.2 Adapters and Converters

#### What They Do
- **Convert between different connectors** — physical shape change
- **Convert between different formats** — signal type change (e.g. digital to analogue)
- Good as a **temporary fix** — not ideal for permanent setups
- May reduce quality or speed depending on conversion type

#### Common Adapters

**DVI to HDMI:**
- Converts digital DVI signal to HDMI
- **Video only** — no audio (DVI has no audio)
- No signal conversion needed — both are digital
- Speed/quality: no loss
- Compatibility: works with any DVI-D or DVI-I source

**DVI to VGA:**
- Converts digital DVI-I to analogue VGA
- Requires active conversion — signal quality may degrade
- Only works with DVI-I or DVI-A (not DVI-D — digital only)
- Used for: connecting modern computers to old VGA monitors/projectors

**USB to Ethernet:**
- Adds a wired Ethernet port via USB
- Useful for laptops/ultrabooks without built-in Ethernet
- Speeds: USB 2.0 adapter = 100Mbps, USB 3.0 adapter = Gigabit
- **Cybersecurity use:** Easy to plug in a rogue USB-Ethernet adapter for network access

**USB-C to USB-A:**
- Allows USB-C devices to connect to older USB-A ports
- Speed limited to the lower of the two (usually USB 3.0 = 5Gbps)
- Very common adapter as USB-C becomes standard

**USB Hub:**
- Expands one USB port into multiple ports
- Powered hubs have their own power supply — better for high-draw devices
- Unpowered hubs share the host port's power budget
- **Cybersecurity use:** Malicious USB hubs can act as a man-in-the-middle for USB traffic

---

### 3.2 Copper Connectors

#### RJ11 Connector
- **6 position, 2 or 4 conductor** (6P2C or 6P4C)
- Used for: **telephone lines** (landline phones, DSL modems)
- Smaller than RJ45
- **Cybersecurity use:** Physical access to phone lines for social engineering research

#### RJ45 Connector
- **8 position, 8 conductor** (8P8C)
- Used for: **Ethernet networking** (Cat5e, Cat6, Cat6A)
- The most common network connector in the world
- Wired to T568A or T568B standard
- **Cybersecurity use:** Plugging into an open RJ45 port = potential network access

#### F Connector
- **Coaxial cable connector** — threaded, screw-on design
- Used for: cable TV, cable internet (DOCSIS), satellite TV
- Connects coaxial RG-6 cable to modems, TVs, wall plates

#### Punch Down Block
- **Terminal block** for terminating twisted pair cables
- Wire is pushed (punched) into the block using a punch down tool
- **110 block** — modern standard, used in patch panels and wall jacks
- **66 block** — older, used in telephone systems
- **Cybersecurity use:** Physical access to a punch down block = ability to tap into network lines

#### USB Connectors (Recap with additions)

| Connector | Description | Common Use |
|---|---|---|
| USB-A (Standard A) | Flat rectangle, host side | Computer, charger, hub |
| USB-B (Standard B) | Square with notch, device side | Printers, older devices |
| Mini-B | Small, trapezoid | Old cameras, MP3 players |
| Micro-B | Very small, common | Old Android phones, power banks |
| USB 3.0 Standard A | Same shape as 2.0-A, blue inside | USB 3.0 computers |
| USB 3.0 Standard B | Larger than 2.0-B | USB 3.0 external drives |
| USB 3.0 Micro-B | 10-pin wider connector | USB 3.0 external SSDs |
| USB-C | 24-pin, reversible, oval | Modern phones, laptops, everything |

#### Molex Connector
- **4-pin peripheral power connector**
- Large white plastic connector with 4 pins
- Provides power for: fans, older HDDs, optical drives, some GPUs
- Voltages: +12V (yellow), +5V (red), ground (black x2)
- Being replaced by SATA power in modern systems

#### Lightning
- **Apple proprietary** 8-pin digital connector
- Used on: iPhones, iPads, AirPods (older models)
- Being replaced by USB-C (EU law now requires USB-C on phones)
- **Cybersecurity use:** Malicious Lightning cables (O.MG cable) look identical to real ones but contain a hidden Wi-Fi chip to execute remote attacks

#### DB-9
- **D-Subminiature connector**, 9 pins in 2 rows
- Used for: **RS-232 serial communication**, console ports on network equipment
- Standard configuration port for Cisco routers, switches, and servers
- **Cybersecurity use:** Console access via DB-9 = direct unauthenticated access to network equipment if physical security is weak

---

### 3.2 Fiber Connectors

#### ST — Straight Tip
- **Bayonet-style** connector — push and twist to lock (like a BNC connector)
- Round ferrule
- **Use:** Older multimode fibre installations, legacy enterprise networks
- Being replaced by LC and SC

#### SC — Subscriber Connector
- **Push-pull** connector — square shape, clicks in and out
- Larger than LC
- **Use:** ISP equipment, older data centres, single mode and multimode
- Easy to connect and disconnect — popular in telecommunications

#### LC — Lucent Connector
- **Small form factor** — half the size of SC
- Push-pull latch mechanism
- **Most common modern fibre connector**
- **Use:** Data centres, high-density fibre panels, SFP modules in switches
- Fits more connections in the same space than SC

| Connector | Style | Size | Common Use |
|---|---|---|---|
| ST | Bayonet twist | Large | Legacy networks |
| SC | Push-pull square | Large | ISP, older data centres |
| LC | Push-pull latch | Small | Modern data centres, switches |

---

### 3.3 An Overview of Memory

#### RAM — Random Access Memory
- **Temporary, high-speed storage** — loses all data when power is off
- NOT referring to hard drive or SSD storage
- Data and programs can only run when moved from storage into RAM
- More RAM = more programs running simultaneously without slowdown
- **Cybersecurity use:** RAM forensics — attacker's tools and encryption keys live in RAM — memory dumps can reveal active passwords and keys

#### DIMM — Dual Inline Memory Module
- Standard desktop RAM form factor
- **64-bit data width**
- Multiple slots on the motherboard for multiple DIMMs
- Notch position differs between generations (DDR3, DDR4, DDR5) to prevent wrong installation

#### SO-DIMM — Small Outline DIMM
- Smaller version of DIMM for **laptops and mobile devices**
- Same function, smaller physical size
- Your laptop uses SO-DIMMs
- Run this to see yours: `sudo dmidecode --type memory`

#### DRAM — Dynamic Random Access Memory
- **Dynamic** — needs constant refreshing to retain data (thousands of times per second)
- **Random Access** — any memory location can be accessed in any order instantly
- The type of RAM in all modern computers

#### SDRAM — Synchronous DRAM
- Synchronised to the **system clock**
- Transfers data in sync with the CPU clock — more efficient than asynchronous DRAM

#### SDR vs DDR — Understanding the Difference
- **SDR (Single Data Rate)** — transfers data **once per clock cycle** (on the rising edge)
- **DDR (Double Data Rate)** — transfers data **twice per clock cycle** (on both rising AND falling edge)
- This doubles the effective bandwidth without doubling the clock speed
```
Clock cycle:     /‾\_/‾\_/‾\_
SDR transfers:   ^   ^   ^      (once per cycle = 3 transfers)
DDR transfers:   ^ ^ ^ ^ ^ ^    (twice per cycle = 6 transfers)
```
- Think of it like: SDR delivers one package per truck trip, DDR delivers two packages per trip

#### DDR Generations

| Generation | Voltage | Max Speed | Notes |
|---|---|---|---|
| DDR3 | 1.5V | 2133 MT/s | Older systems, still common |
| DDR4 | 1.2V | 3200 MT/s | Current mainstream standard |
| DDR5 | 1.1V | 6400+ MT/s | Latest, newer CPUs only |

- Lower voltage = less power consumption = less heat
- **Not backward compatible** — DDR4 stick will not fit in a DDR3 slot (different notch position)

---

### 3.3 Memory Technologies

#### Parity Memory
- Adds an extra **parity bit** to each byte of data
- Can **detect** single-bit errors but **cannot correct** them
- If an error is detected, the system crashes (better than silently using wrong data)
- Used in older servers and critical systems
- Mostly replaced by ECC

#### ECC — Error Correction Code Memory
- More advanced than parity — can **detect AND correct** single-bit errors automatically
- Can detect (but not correct) 2-bit errors
- More expensive than non-ECC
- Used in: **servers, workstations, data centres** — anywhere data integrity is critical
- **Cybersecurity use:** Rowhammer attack — flipping bits in non-ECC RAM by rapidly accessing adjacent memory rows — ECC RAM is immune to basic Rowhammer attacks

#### CPU to RAM Throughput
- The speed at which the CPU can read/write data to RAM
- Determined by: RAM speed × bus width × number of channels
- Example: DDR4-3200, dual channel, 64-bit
```
3200 MT/s × 8 bytes (64-bit) × 2 channels = 51.2 GB/s throughput
```

#### Multi-Channel Memory
- Uses **two independent memory buses** to double bandwidth
- **Dual Channel** — 2 DIMMs working together (most common)
- **Triple Channel** — 3 DIMMs (older Intel platforms)
- **Quad Channel** — 4 DIMMs (server and HEDT platforms)
- Must install matched pairs in correct slots for multi-channel to work
- Example: 2x 8GB in slots A1+B1 = dual channel 16GB (faster than 1x 16GB single channel)
- **Check if your Ubuntu system has dual channel:**
```bash
sudo dmidecode --type memory | grep -i "bank\|speed\|size"
```

---

### 3.4 Storage Devices

#### HDD — Hard Disk Drive
- **Magnetic storage** — data stored on spinning magnetic platters
- **Moving arm (read/write head)** moves across spinning platters to read/write data
- The arm never touches the platters — floats on a cushion of air (nanometres away)
- If the arm touches the platter = **head crash** = catastrophic data loss
- **How it works:**
```
Platters spin at 5400 or 7200 RPM
Read/write head moves to the correct track
Data is read/written magnetically as platters spin
```
- Transfer speeds: **80–160 MB/s** (mechanical limit of spinning platters)
- Sizes: **3.5 inch** (desktop), **2.5 inch** (laptop)
- Cheap per GB — good for bulk storage
- **Cybersecurity use:** Deleted files on HDD are recoverable with forensic tools (data remains until overwritten)

#### SSD — Solid State Drive
- **Flash memory storage** — no moving parts
- Data stored in NAND flash memory cells (like a giant USB stick)
- Much faster than HDD — no mechanical movement
- More shock resistant — no moving parts to damage
- Transfer speeds: **200–550 MB/s** (SATA SSD), **3,500 MB/s+** (NVMe SSD)
- More expensive per GB than HDD
- **Cybersecurity use:** Deleted files on SSD are harder to recover — TRIM command actively erases deleted data blocks

#### Flash Drive — EEPROM
- **EEPROM** — Electrically Erasable Programmable Read-Only Memory
- Data persists without power (non-volatile)
- **Limited number of write cycles** — eventually wears out
- Used in: USB drives, SSDs, memory cards, BIOS chips
- **Cybersecurity use:** USB drives are a top malware delivery vector — BadUSB attack reprograms the USB controller itself

#### Drive Size Comparison

| Form Factor | Size | Use |
|---|---|---|
| 3.5 inch | Full size | Desktop HDDs |
| 2.5 inch | Laptop size | Laptop HDDs and SSDs |
| 22mm (M.2) | Small card | NVMe and SATA SSDs in laptops |

#### PCIe Storage — NVMe

**AHCI — Advanced Host Controller Interface:**
- Old interface designed for spinning HDDs
- SATA Revision 3 throughput: up to **6 Gbps**
- Only one command queue with 32 commands
- Too slow for modern SSDs

**NVMe — Non-Volatile Memory Express:**
- Designed specifically for flash storage over PCIe bus
- **64 Gbps per lane** (PCIe 4.0)
- 65,535 command queues with 65,535 commands each
- Dramatically lower latency than AHCI/SATA
- M.2 interface transfer speed: up to **20 Gbps** (PCIe 3.0 x4)

#### HDD vs SSD vs SATA vs M.2 Comparison

| Type | Interface | Speed | Form Factor | Use |
|---|---|---|---|---|
| HDD | SATA | 80-160 MB/s | 3.5"/2.5" | Bulk storage, backups |
| SATA SSD | SATA | 200-550 MB/s | 2.5"/M.2 | Budget upgrade from HDD |
| NVMe SSD | PCIe/M.2 | 3,000-7,000 MB/s | M.2 | OS drive, fast storage |

#### SAS — Serial Attached SCSI
- Enterprise-grade storage interface
- Used in **servers and data centres**
- More reliable and faster than SATA
- High-end SAS reaches **22.5 Gbps**
- Supports longer cable runs than SATA
- More expensive than SATA

#### mSATA — Mini SATA
- Smaller version of SATA for compact devices
- Being replaced by M.2

#### M.2 Interface
- Small card-style connector directly on motherboard
- Can use either **SATA** or **PCIe (NVMe)** bus
- Key types determine compatibility:
  - **B key** — SATA and PCIe x2
  - **M key** — PCIe x4 (fastest NVMe)
  - **B+M key** — compatible with both B and M slots (usually SATA)
- **Check before buying** — M.2 slot on motherboard may only support SATA OR NVMe, not both

#### Flash Memory Cards

| Type | Use | Max Size |
|---|---|---|
| CompactFlash (CF) | Professional cameras (older) | 512GB |
| SD (Secure Digital) | Cameras, devices | 2TB |
| miniSD | Older phones | 2GB |
| microSD | Phones, dashcams, Raspberry Pi | 1TB+ |

#### Optical Drives
- Data stored as **small bumps (pits and lands)** on a reflective disc
- Read with a **laser beam** — laser reflects differently off pits vs lands
- **Relatively slow** compared to flash storage
- Types:

| Type | Capacity | Speed |
|---|---|---|
| CD-ROM | 700 MB | 150 KB/s (1x) |
| DVD-ROM | 4.7 GB (single), 8.5 GB (dual) | 1.38 MB/s (1x) |
| Blu-ray | 25 GB (single), 50 GB (dual) | 4.5 MB/s (1x) |

---

### 3.4 RAID — Redundant Array of Independent Disks

#### What is RAID?
- Combines multiple physical drives into one logical unit
- Goals: **data redundancy** (protection against drive failure) and/or **performance**
- RAID does NOT replace backups — it protects against drive failure only

---

#### RAID 0 — Striping
```
Drive 1: [A1][A3][A5]
Drive 2: [A2][A4][A6]
Data split across both drives simultaneously
```
- Data is split (striped) across multiple drives
- **Speed:** Excellent — reads and writes to all drives simultaneously
- **Redundancy:** None — if ONE drive fails, ALL data is lost
- **Minimum drives:** 2
- **Usable capacity:** 100% of total (2x 1TB = 2TB usable)
- **Use case:** Video editing, scratch disks, performance over safety
- **Cybersecurity use:** No redundancy = higher risk in attack scenarios

---

#### RAID 1 — Mirroring
```
Drive 1: [A1][A2][A3]
Drive 2: [A1][A2][A3]  ← exact copy
```
- Exact copy of data written to two drives simultaneously
- **Speed:** Read is faster (can read from either drive), write is same speed
- **Redundancy:** Excellent — one drive can fail completely, no data loss
- **Minimum drives:** 2
- **Usable capacity:** 50% of total (2x 1TB = 1TB usable)
- **Use case:** OS drives, critical data, small servers
- **Cybersecurity use:** Seizing one mirrored drive gives full forensic copy

---

#### RAID 5 — Striping with Parity
```
Drive 1: [A1][B1][C_parity]
Drive 2: [A2][B_parity][C1]
Drive 3: [A_parity][B2][C2]
Parity rotates across drives
```
- Data striped across drives with parity information distributed across all drives
- **Speed:** Good read performance, slightly slower writes (parity calculation)
- **Redundancy:** Can survive ONE drive failure — parity is used to rebuild lost data
- **Minimum drives:** 3
- **Usable capacity:** (n-1) drives (3x 1TB = 2TB usable)
- **Use case:** File servers, NAS devices, balanced performance and redundancy
- **Rebuild time:** Hours to days — system is vulnerable during rebuild

---

#### RAID 6 — Striping with Double Parity
```
Same as RAID 5 but with TWO parity blocks distributed
```
- Like RAID 5 but with **two parity blocks** instead of one
- **Speed:** Good read, slower writes than RAID 5 (two parity calculations)
- **Redundancy:** Can survive **TWO simultaneous drive failures**
- **Minimum drives:** 4
- **Usable capacity:** (n-2) drives (4x 1TB = 2TB usable)
- **Use case:** Large storage arrays where rebuild times are long and double failure risk is real
- Better than RAID 5 for large arrays (more drives = more failure risk)

---

#### RAID 10 — Nested RAID 1+0 (Mirroring + Striping)
```
Mirror pair 1:   Drive 1 [A1][A2] ←→ Drive 2 [A1][A2]
Mirror pair 2:   Drive 3 [B1][B2] ←→ Drive 4 [B1][B2]
Data striped across mirror pairs
```
- Combines RAID 1 (mirroring) and RAID 0 (striping)
- Data is mirrored in pairs, then striped across pairs
- **Speed:** Excellent — best of RAID 0 and RAID 1
- **Redundancy:** Excellent — one drive from each mirror pair can fail
- **Minimum drives:** 4
- **Usable capacity:** 50% of total (4x 1TB = 2TB usable)
- **Use case:** Databases, high-performance servers, enterprise storage
- Most expensive option but best overall performance + redundancy

---

#### RAID Comparison Table

| RAID | Type | Min Drives | Usable Capacity | Fault Tolerance | Speed |
|---|---|---|---|---|---|
| RAID 0 | Striping | 2 | 100% | None ❌ | Fastest |
| RAID 1 | Mirroring | 2 | 50% | 1 drive | Good |
| RAID 5 | Stripe+Parity | 3 | (n-1)/n | 1 drive | Good |
| RAID 6 | Stripe+2 Parity | 4 | (n-2)/n | 2 drives | Moderate |
| RAID 10 | Mirror+Stripe | 4 | 50% | 1 per pair | Excellent |

---

## Terminal Practice + Expected Output

### Check Your Storage Devices
```bash
lsblk
```
**Expected output:**
```
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda           8:0    0 476.9G  0 disk
├─sda1        8:1    0   100M  0 part /boot/efi
├─sda2        8:2    0    16M  0 part
├─sda3        8:3    0 200.1G  0 part        ← Windows partition
├─sda4        8:4    0   650M  0 part
└─sda5        8:5    0 276.1G  0 part /      ← Ubuntu partition
```
- Shows all drives and partitions
- `disk` = physical drive, `part` = partition

---

### Check Disk Space
```bash
df -h
```
**Expected output:**
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       271G   15G  242G   6% /
tmpfs           7.8G  1.2M  7.8G   1% /dev/shm
/dev/sda1       100M   32M   69M  32% /boot/efi
```

---

### Check RAM Details
```bash
free -h
```
**Expected output:**
```
               total        used        free      shared  buff/cache   available
Mem:            15Gi       3.2Gi       8.1Gi       512Mi       4.1Gi      11.5Gi
Swap:          4.0Gi          0B       4.0Gi
```

```bash
sudo dmidecode --type memory | grep -E "Size|Speed|Type:|Manufacturer"
```
**Expected output:**
```
        Size: 8 GB
        Type: DDR4
        Speed: 3200 MT/s
        Manufacturer: Samsung
        Size: 8 GB
        Type: DDR4
        Speed: 3200 MT/s
        Manufacturer: Samsung
```
- Two 8GB sticks = 16GB total
- Both same speed = dual channel active

---

### Check Storage Hardware Info
```bash
sudo lshw -class disk
```
**Expected output:**
```
  *-disk
       description: ATA Disk
       product: Samsung SSD 870
       size: 476GiB
       capabilities: gpt-1.00 partitioned
```

---

## 🔑 Additional Important Concepts You Missed

### NVMe vs SATA SSD Real World Difference
```
SATA SSD:  Windows boots in ~15 seconds
NVMe SSD:  Windows boots in ~8 seconds
File copy (10GB):
  SATA SSD: ~20 seconds
  NVMe SSD: ~3 seconds
```
- For everyday use the difference is noticeable mainly in large file transfers and boot times

### SMART — Self-Monitoring Analysis and Reporting Technology
- Built into all modern HDDs and SSDs
- Monitors drive health and predicts failure
- Check your drive health on Ubuntu:
```bash
sudo apt install smartmontools -y
sudo smartctl -a /dev/sda
```
- **Cybersecurity use:** SMART data can reveal if a drive has been heavily used or tampered with

### RAID is NOT a Backup
- RAID protects against **hardware failure** only
- RAID does NOT protect against:
  - Accidental file deletion (deleted from all mirrors instantly)
  - Ransomware (encrypts all mirrors simultaneously)
  - Fire, flood, theft
- **3-2-1 backup rule:** 3 copies, 2 different media types, 1 offsite

### Hot Spare
- Extra drive sitting idle in a RAID array
- Automatically starts rebuilding if another drive fails
- Reduces rebuild time and double-failure risk in RAID 5

### Wear Levelling (SSD)
- SSDs distribute writes evenly across all memory cells
- Prevents any single cell from wearing out too fast
- **Cybersecurity use:** Wear levelling means deleted data may persist in unmapped cells — specialist tools can sometimes recover it

---

## Week 1 Review — Key Takeaways

- ✅ A+ covers mobile devices, networking, hardware, virtualization and troubleshooting
- ✅ TCP is reliable/connection-oriented, UDP is fast/connectionless
- ✅ DNS translates names to IPs — SPF+DKIM+DMARC protect against email spoofing
- ✅ DHCP DORA process — rogue DHCP = man-in-the-middle attack
- ✅ VLANs separate networks logically — VLAN hopping bypasses this
- ✅ OSI model has 7 layers — each layer has specific cybersecurity attack vectors
- ✅ RAID protects against drive failure — NOT a replacement for backups
- ✅ NVMe is dramatically faster than SATA SSD via PCIe bus

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. DDR doubles data rate by transferring on both rising AND falling edge of clock cycle
2. RAID 5 can survive one drive failure using distributed parity — but is vulnerable during rebuild
3. NVMe uses PCIe bus directly — bypasses SATA bottleneck for dramatically faster storage speeds