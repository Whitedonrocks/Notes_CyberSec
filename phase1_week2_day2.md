# CompTIA A+ 220-1201 — Week 2 Day 2 Notes

---

## Videos Watched
- ✅ 3.5 Expansion Cards
- ✅ 3.5 Cooling
- ✅ 3.6 Computer Power
- ✅ 3.7 Multifunction Devices

---

## Key Concepts

### 3.5 Expansion Cards

#### What Are Expansion Cards?
- Cards that **extend the functionality** of a computer
- Installed into PCIe or PCI slots on the motherboard
- Relatively simple process — slot in, install driver, done
- Always check motherboard AND adapter card documentation before installing

#### Sound Card
- Provides **high-end audio** beyond what onboard audio offers
- Use cases:
  - Advanced headphone amplifier (drives high-impedance headphones)
  - Multiple audio inputs (microphones, instruments)
  - Professional recording — lower latency, better DAC/ADC
  - Surround sound processing
- Most users don't need one — onboard audio is sufficient for gaming and general use
- **Cybersecurity use:** Some malware has been known to use audio hardware for covert data exfiltration via ultrasonic signals

#### Video Card (GPU)
**Discrete Graphics:**
- The GPU is a **separate chip** from the CPU — has its own dedicated VRAM
- Installed as a PCIe x16 expansion card
- Much more powerful than integrated — required for gaming, 3D rendering, ML/AI
- Examples: NVIDIA GeForce RTX series, AMD Radeon RX series
- Your GTX 1650 is a discrete GPU

**Integrated Graphics:**
- GPU built **into the CPU die** — shares system RAM
- Lower performance than discrete
- Uses system RAM (no dedicated VRAM)
- Sufficient for: office work, video playback, light use
- Examples: Intel UHD Graphics, AMD Radeon Vega (Ryzen APUs)
- **Cybersecurity use:** GPU can be used for password cracking — discrete GPUs crack passwords much faster than CPUs (hashcat uses GPU)

#### Capture Card
- Accepts **video as an input** from an external source
- Captures HDMI/SDI video signal from cameras, consoles, other computers
- Used for: game streaming, video production, recording lectures
- High performance — must process real-time video without dropping frames
- Internal (PCIe) or external (USB) versions available

#### NIC — Network Interface Card
- Provides **Ethernet connectivity** to a computer
- Most modern motherboards have built-in NIC — expansion NIC for:
  - Faster speeds (2.5G, 10G, 25G)
  - Additional network ports
  - Specific protocols (fibre, SFP+)
- **Multiport Ethernet** — single card with 2, 4, or more Ethernet ports
  - Used in servers for redundancy or link aggregation
  - Network engineers use multiport NICs for capturing traffic from multiple segments

#### Driver Installation
- Always install the driver for the expansion card
- Without driver: OS cannot communicate with the card properly
- Driver source: manufacturer website (always use latest stable)
- **Cybersecurity use:** Unsigned or fake drivers are a common malware delivery method — always verify driver signatures

---

### 3.5 Cooling

#### Why Cooling Matters
- CPUs and GPUs generate significant heat during operation
- Without cooling: **thermal throttling** (CPU slows itself down to prevent damage)
- Extreme overheating: permanent hardware damage
- Good cooling = stable performance = longer hardware life

#### Case Fans
- Pull **cool air through** the computer case
- Create airflow: cool air in from front → hot air out from back/top
- **Always check for good airflow** — blocked vents or poor cable management kills cooling
- Positive pressure (more intake than exhaust) — keeps dust out
- Negative pressure (more exhaust than intake) — pulls air through every gap

#### Onboard Fans (Card Fans)
- Fans designed to cool an **entire adapter card** (usually GPU)
- GPU coolers: 1, 2, or 3 fans depending on the card
- Your GTX 1650 has its own onboard fan controlled by the GPU driver

#### Fan Specifications
| Size | Use | Noise |
|---|---|---|
| 80mm | Small cases, GPU exhausts | Louder (spins faster to move same air) |
| 120mm | Most common, CPU coolers, case fans | Balanced |
| 200mm | Full tower cases, large coolers | Quietest (moves same air at lower RPM) |

- Larger fans = lower RPM needed = quieter
- Fan speed measured in **RPM** (revolutions per minute)
- Noise measured in **dBA** — lower is quieter

#### Fanless / Passive Cooling
- No fans at all — completely silent
- Uses large heatsinks and natural convection
- Limited to low-power systems
- Used in: industrial computers, silent home theatre PCs, embedded systems

#### Heatsink
- Metal block (usually aluminium or copper) that **dissipates heat through thermal conduction**
- Heat travels from CPU → heatsink → air
- Copper conducts heat better than aluminium but costs more
- Large surface area (fins) maximises heat transfer to air

#### Thermal Paste (Thermal Grease / Conductive Grease)
- Applied **between the heatsink and the component** (CPU/GPU)
- Fills microscopic gaps between the two surfaces — air is a terrible heat conductor
- Without thermal paste: huge air gaps = poor heat transfer = overheating
- Must be replaced when removing/reseating a heatsink
- Common brands: Arctic MX-4, Thermal Grizzly Kryonaut, Noctua NT-H1
- **Application:** Small pea-sized amount in centre — spreads when heatsink is pressed down
- **Cybersecurity use:** Improperly applied thermal paste = thermal throttling = performance drops that affect encryption/decryption speeds

#### Thermal Pad
- Pre-cut pad of thermally conductive material
- **No mess** — easier to apply than paste
- Almost as effective as thermal paste
- **Not reusable** — must replace when removed
- Used on: GPU VRAM chips, VRMs, M.2 SSDs, RAM

#### Liquid Cooling (AIO — All In One)
- **Coolant circulated** through a closed loop system
- Components: water block (sits on CPU) → pump → radiator → fans
- Much better cooling than air for high-end CPUs
- **Custom loop** — separate components, highest performance, complex setup
- **AIO (All In One)** — sealed pre-built loop, easier to install
- Used for: overclocked CPUs, high-performance workstations, enthusiast builds
- **Cybersecurity use:** Liquid cooling failure = catastrophic — leak can destroy entire system

---

### 3.6 Computer Power

#### Power Supply Unit (PSU)
- Converts **AC (mains power) to DC (computer power)**
- Most power sources provide **AC voltage** — computers need DC
- Converts:
  - **120V AC** (US/Nepal) or **240V AC** (UK/Europe/Australia)
  - → **3.3V, 5V, and 12V DC**

#### Electrical Fundamentals

**Ampere (Amp, A):**
- The **rate of electron flow** past a point in one second
- Think of it as: how much water is flowing through a pipe
- More amps = more current flowing

**Voltage (V):**
- **Electrical pressure** pushing the electrons
- Think of it as: the water pressure in the pipe
- More voltage = more pressure pushing current

**Watt (W) — Real Power:**
- Measurement of actual power consumption
- Formula: **Volts × Amps = Watts**
- Example: 12V × 10A = 120W
- This is what your electricity bill measures

#### AC vs DC Current

**AC — Alternating Current:**
- Current **constantly reverses direction** — oscillates back and forth
- Used for mains power (wall outlets)
- Easier to transmit over long distances
- Nepal mains: 230V AC at 50Hz

**DC — Direct Current:**
- Current moves in **one direction only** with constant voltage
- Used inside computers and electronic devices
- Batteries produce DC
- PSU converts AC → DC

#### Dual Voltage Input Options
- Many PSUs support both **110-120V and 220-240V** input
- **Manual switch** (older PSUs): physical switch on the back — must set correctly or PSU will be damaged
- **Auto-sensing** (modern PSUs): automatically detects input voltage — works worldwide
- In Nepal (230V): ensure PSU supports 220-240V input
- **Cybersecurity use:** Incorrect voltage setting = instant PSU failure = data loss if no UPS

#### Power Supply Output — Components and Their Voltages

| Voltage Rail | Components Powered |
|---|---|
| **3.3V** | RAM, some motherboard circuits, older PCI cards |
| **5V** | USB ports, older drives, some motherboard circuits |
| **12V** | CPU, GPU, case fans, SATA drives, NVMe drives |
| **-12V** | Some legacy serial ports (very small amount) |
| **5VSB (Standby)** | Powers the motherboard even when PC is "off" — for wake-on-LAN |

#### 24-Pin Motherboard Power
- Main motherboard power connector
- Provides 3.3V, 5V, and 12V to the motherboard
- Was **20-pin** in original ATX standard
- Extra 4 pins added for PCIe power support

#### Redundant Power Supplies
- Used in **servers and enterprise equipment**
- Each PSU can handle **100% of the load** independently
- **Hot swappable** — failed PSU can be replaced without shutting down
- If one fails, the other instantly takes over
- Critical for uptime in data centres

#### Power Supply Connectors
**Fixed (Non-modular):**
- All cables permanently attached to PSU
- Cheaper
- Messy — unused cables clutter the case
- Worse airflow

**Modular:**
- Only attach the cables you need
- More expensive
- Clean build, better airflow
- **Semi-modular** — essential cables fixed, others detachable

#### Sizing a Power Supply
- Rated in **watts** — how much total power it can deliver
- Must calculate total power requirement of all components
- Example system:
```
CPU:        125W
GPU:        150W
RAM:        10W
Motherboard: 50W
Storage:    15W
Fans:       10W
Total:      360W
```
- **50% capacity rule** — run PSU at 50% load for best efficiency and longevity
- So for 360W system: buy a **750W PSU** (360W ÷ 0.5 = 720W minimum → round up to 750W)
- Video cards are usually the **largest power draw** — always check GPU TDP

#### Energy Efficiency
- Converting AC to DC is not perfect — some energy lost as heat
- **80 PLUS Certification program** — industry standard for PSU efficiency

| 80 PLUS Rating | Efficiency at 50% load |
|---|---|
| 80 PLUS (White) | 80% |
| 80 PLUS Bronze | 85% |
| 80 PLUS Silver | 88% |
| 80 PLUS Gold | 90% |
| 80 PLUS Platinum | 92% |
| 80 PLUS Titanium | 94% |

- 90% efficient at 500W load = 50W wasted as heat
- Higher efficiency = lower electricity bill + less heat in case
- **Cybersecurity use:** Power analysis attacks measure PSU efficiency fluctuations to extract cryptographic keys

---

### 3.7 Multifunction Devices (MFD)

#### What is an MFD?
- A single device that combines multiple functions:
  - **Printer** — output documents
  - **Scanner** — input documents digitally
  - **Fax** — send/receive documents over phone line
  - **Network connection** — share over wired/wireless network
  - **Phone line connection** — for fax functionality
  - **Print from web** — direct printing from cloud services
- Your **Canon G2010** is an MFD!

#### Setting Up an MFD
- Can be large — check the area before unboxing
- Check power requirements and connection options
- **Printer drivers** must be installed on each computer that will print
- Firmware updates available from manufacturer website

#### PCL vs PostScript
- **PCL — Printer Command Language** — developed by HP
  - Most common for office printing
  - Faster for simple documents
  - Windows-friendly
- **PostScript** — developed by Adobe
  - Better for complex graphics and typography
  - Used in professional printing and publishing
  - More accurate colour rendering

#### Firmware
- The **internal operating system** of the MFD
- Controls all printer functions
- Can be updated to fix bugs or add features
- **Cybersecurity use:** Printer firmware vulnerabilities are real — unpatched printers on networks have been used as attack pivot points (FaxPloit, PrintNightmare)

#### Device Sharing

**Wired Device Sharing:**
- Direct USB connection to one computer (printer is private to that machine)
- Network cable (Ethernet) connection to network switch — shared by all

**Wireless Device Sharing:**
| Method | Description |
|---|---|
| **Bluetooth** | Short range, direct pairing, good for personal use |
| **802.11 (Wi-Fi)** | Connect printer to Wi-Fi network — accessible by all |
| **802.11 Ad-hoc mode** | Direct device-to-device Wi-Fi without a router |
| **Wi-Fi Direct** | Modern ad-hoc — phone/laptop connects directly to printer |
| **NFC** | Tap phone to printer to initiate print job |

#### Sharing the Printer
**Print Share (Windows sharing):**
- One computer connects printer via USB
- Shares it on the network through Windows
- Other computers print via that host computer
- Host computer must be on for others to print

**Print Server:**
- Dedicated device (hardware or software) manages print jobs
- Printer connects to print server, not to a specific computer
- Any network device can send jobs anytime
- More reliable than print share — no dependency on one PC

#### Configuration Settings
| Setting | Description |
|---|---|
| **Duplex** | Print on both sides of paper automatically |
| **Orientation** | Portrait (tall) or Landscape (wide) |
| **Tray settings** | Which paper tray to use, paper size/type |
| **Quality** | Draft (fast, low ink) vs Normal vs Best (slow, high ink) |
| **Colour vs B&W** | Print in colour or black and white only |
| **Copies** | Number of copies per print job |

#### Printer Security
> Printers are often the most neglected device on a network — attackers love them

| Security Feature | Description |
|---|---|
| **User authentication** | Require login before printing |
| **Printing vs Managing** | Separate permissions for printing and admin settings |
| **Badging** | Tap access card at printer to release held print job |
| **Audit logs** | Record every print job — who printed what and when |
| **Secured prints** | Job held in queue until user physically authenticates at printer |
| **Encryption** | Encrypt data in transit from computer to printer |
| **Network isolation** | Put printers on separate VLAN from workstations |

- **Cybersecurity use:** Printers store the last 100+ print jobs in memory — physical access = data breach. Printers with open web admin interfaces (port 9100, 80, 443) are frequently exploited

#### Flatbed Scanner
- Glass surface where document is placed face down
- Scanning head moves beneath the glass
- **Form factors:**
  - **Standard flatbed** — most common, scans documents and photos
  - **Sheet-fed** — document feeds through automatically (like your Canon G2010's ADF)
  - **Portable/handheld** — small, battery-powered, for field use
  - **Drum scanner** — professional, wraps document around a cylinder, highest quality

#### Network Scan Service
- Scanner accessible over the network — not just from directly connected PC
- Scan from any device on the network

#### Scan to Folder
- Scanned document saved directly to a network folder
- Uses **SMB (Server Message Block)** — same protocol as Windows file sharing
- Configuration: enter server IP, share name, username, password on the MFD touchscreen
- Example path: `\\192.168.1.100\scans`
- **Cybersecurity use:** SMB credentials stored in MFD can be extracted — SMB relay attacks can capture authentication hashes

#### Scan to Cloud
- Scanned document sent directly to cloud storage
- Services: Google Drive, OneDrive, Dropbox, email
- No local server needed
- **Cybersecurity use:** Cloud scan services store documents externally — data sovereignty concern for sensitive documents

---

## Terminal Practice + Expected Output

### Check Battery and Power Info
```bash
upower -i /org/freedesktop/UPower/devices/battery_BAT1
```
**Expected output:**
```
  native-path:          BAT1
  vendor:               ASUSTeK
  model:                ASUS Battery
  state:                charging
  energy:               38.54 Wh
  energy-empty:         0.00 Wh
  energy-full:          52.66 Wh
  energy-full-design:   52.66 Wh
  energy-rate:          12.45 W
  voltage:              12.15 V
  charge-cycles:        N/A
  percentage:           60%
  capacity:             100%
```
- `energy-rate` = current power draw in watts
- `percentage: 60%` = your battery charge limit is working!

---

### Check All Hardware Temperatures
```bash
sensors
```
**Expected output:**
```
coretemp-isa-0000
Core 0:        +45.0°C
Core 1:        +44.0°C
Core 2:        +46.0°C
Core 3:        +43.0°C

nvme-pci-0200
Composite:     +35.9°C

BAT1-virtual-0
temp1:         +28.0°C
```

---

### Check Connected USB Devices
```bash
lsusb
```
**Expected output:**
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04a9:183a Canon, Inc. PIXMA G2010
Bus 001 Device 002: ID 8087:0029 Intel Corp. AX200 Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
- Your Canon G2010 shows as `04a9:183a` — 04a9 is Canon's vendor ID

---

### Check Power Consumption
```bash
cat /sys/class/thermal/thermal_zone*/temp
```
**Expected output:**
```
27800
29000
30000
45000
```
- Values are in millidegrees Celsius
- Divide by 1000 for actual temp: 45000 = 45°C

---

## 🔑 Additional Important Concepts You Missed

### UPS — Uninterruptible Power Supply
- Battery backup for your computer
- Provides power during outages — gives time to save work and shut down properly
- Protects against: power outages, voltage spikes, brownouts
- Types: offline (basic), line-interactive (better), online double-conversion (best)
- **Critical for servers** — unexpected shutdown = data corruption
- **Cybersecurity use:** Power outage during disk encryption = corrupted encrypted volume

### Power Factor
- Ratio of real power (watts) to apparent power (volt-amps)
- PSUs with active power factor correction (APFC) are more efficient
- **80 PLUS certified PSUs** must have APFC

### PrintNightmare (CVE-2021-34527)
- Critical Windows vulnerability in the **Print Spooler service**
- Allowed attackers to remotely execute code with SYSTEM privileges
- Affected every Windows version
- Patched in July 2021 but variants kept appearing
- Real world example of printer-related cybersecurity risk

### GPU Acceleration in Security
```bash
# Check if CUDA (NVIDIA GPU compute) is available
nvidia-smi
nvcc --version  # if CUDA toolkit installed
```
- Hashcat (password cracker) uses GPU acceleration
- GPU can test billions of password hashes per second
- Your GTX 1650 can crack MD5 hashes at ~5 billion per second
- CPU alone: ~100 million per second
- **50x faster with GPU** — this is why GPU acceleration matters in cybersecurity

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. PSU 50% capacity rule — buy double what you need for efficiency and longevity
2. Printers store print jobs in memory and have open network ports — most neglected attack surface in offices
3. Scan to folder uses SMB — credentials stored in the MFD can be extracted by attackers