# CompTIA A+ 220-1201 — Week 2 Day 1 Notes

---

## Videos Watched
- ✅ 3.5 Motherboards
- ✅ 3.5 Motherboard Expansion Slots
- ✅ 3.5 Motherboard Connections
- ✅ 3.5 Motherboard Compatibility
- ✅ 3.5 The BIOS
- ✅ 3.5 BIOS Settings
- ✅ 3.5 HSM and TPM
- ✅ 3.5 CPU Features

---

## Key Concepts

### 3.5 Motherboards

#### What is a Motherboard?
- The main circuit board of a computer
- Every component connects to it directly or indirectly
- Determines what CPU, RAM, storage, and expansion cards you can use

#### Form Factor
- Defines the **physical size, layout, power connectors, and airflow** of the motherboard
- Over 40 different motherboard form factor types exist
- The form factor determines which case it fits in
- Main types to know: **ATX, Micro ATX, ITX**

#### ATX — Advanced Technology Extended
- Most common desktop form factor
- **305mm x 244mm**
- Full-size, most expansion slots, best airflow
- Power connectors:
  - Original: **20-pin** main power connector
  - Modern: **24-pin** (added 4 extra pins for PCIe support)
  - Additional **4-pin or 8-pin** CPU power connector (12V only, dedicated to CPU)
- Best for: gaming PCs, workstations, builds needing many expansion cards

#### Micro ATX
- Smaller than ATX — **244mm x 244mm**
- Fewer expansion slots than ATX
- **Backward compatible** with ATX cases — fits in full ATX cases
- Good balance of size and expandability
- Best for: budget builds, home PCs, small office systems

#### ITX Form Factor
- **Mini-ITX:** 170mm x 170mm — very small
- Only 1 PCIe expansion slot
- Low power consumption
- Best for: HTPCs (home theatre PCs), small form factor builds, embedded systems
- **Nano-ITX and Pico-ITX** exist for even smaller embedded applications

| Form Factor | Size | PCIe Slots | Best For |
|---|---|---|---|
| ATX | 305x244mm | 4-7 | Gaming, workstations |
| Micro ATX | 244x244mm | 2-4 | Budget, home use |
| Mini-ITX | 170x170mm | 1 | Small builds, HTPCs |

---

### 3.5 Motherboard Expansion Slots

#### Computer Bus
- A **pathway connecting different components** to each other
- Like a highway — data travels between CPU, RAM, GPU, storage etc.
- Bus width determines how much data travels at once
- Bus speed determines how fast it travels

#### PCI — Peripheral Component Interconnect
- Older expansion slot standard
- Two sizes: **32-bit bus** and **64-bit bus**
- Parallel communication — all lanes transmit simultaneously
- Being phased out — replaced by PCIe
- Still found on older motherboards for legacy cards (sound cards, network cards)

#### PCIe — PCI Express
- **Replaces older PCI** — modern standard
- Communicates **serially** — one bit at a time per lane, but at much higher speeds
- The "x" means "by" — number of lanes
  - **x1** = "by 1" = 1 lane
  - **x4** = "by 4" = 4 lanes
  - **x8** = "by 8" = 8 lanes
  - **x16** = "by 16" = 16 lanes (used for GPUs)

#### PCIe Speeds Per Lane

| Version | Speed per Lane | x16 Slot Total | Common Use |
|---|---|---|---|
| PCIe 3.0 | 1 GB/s | 16 GB/s | Most current GPUs, NVMe |
| PCIe 4.0 | 2 GB/s | 32 GB/s | Modern GPUs, fast NVMe |
| PCIe 5.0 | 4 GB/s | 64 GB/s | Latest GPUs, enterprise SSDs |

- **Physical size vs electrical size:** A x1 card fits in a x16 slot (slot is bigger than needed) — works fine but only uses x1 speed
- **Cybersecurity use:** PCIe DMA attacks — malicious PCIe device can directly read system RAM bypassing OS security

---

### 3.5 Motherboard Connections

#### 24-Pin Motherboard Power
- Main power connector from PSU to motherboard
- Provides **3.3V, 5V, and 12V** rails
- **20-pin** was the original ATX standard
- **24-pin** was added to support PCIe power requirements
- The extra 4 pins provide additional 12V power for PCIe devices

#### CPU Power Connector
- Separate from the main 24-pin connector
- Dedicated power just for the CPU
- **4-pin** = older systems, basic CPUs
- **8-pin** = modern CPUs, provides more stable power
- Always located near the CPU socket in the top corner of the motherboard

#### PCIe Power Connectors (GPU Power)
- High-power components like GPUs need extra power beyond what the PCIe slot provides
- **6-pin PCIe** = 75 watts
- **8-pin PCIe** = 150 watts
- Modern high-end GPUs may use two 8-pin connectors (300W) or the new 16-pin (600W)
- **Cybersecurity use:** Power analysis attacks measure power consumption to extract cryptographic keys

#### Storage Drive Interface — SATA
- L-shaped data and power connectors on motherboard
- Each SATA port connects one drive
- Usually 4-8 SATA ports on a modern motherboard

#### eSATA Expansion
- External SATA port on the back panel for external drives
- Same speed as internal SATA (6 Gbps)
- Rarely seen on modern motherboards — replaced by USB 3.0

#### Headers
- **Small pin connectors** on the motherboard for front panel connections
- Power button, reset button, power LED, HDD activity LED, front USB, front audio
- Labelled on the motherboard PCB — must match case wiring
- **Cybersecurity use:** Physical access to reset header = can force reboot to attack boot process

#### M.2 Connector
- Slot directly on motherboard for M.2 SSDs
- Supports SATA or NVMe depending on the slot
- **Key types** determine compatibility (B, M, B+M)
- Much faster than SATA when using NVMe

---

### 3.5 Motherboard Compatibility

#### Intel vs AMD
- **Intel and AMD use different CPU sockets** — not cross-compatible
- Must match CPU brand to motherboard socket
- Example:
  - Intel 13th gen = LGA1700 socket
  - AMD Ryzen 7000 = AM5 socket
- Even within the same brand, generations may use different sockets

#### Common Sockets

| Brand | Socket | Generation |
|---|---|---|
| Intel | LGA1200 | 10th/11th gen |
| Intel | LGA1700 | 12th/13th/14th gen |
| AMD | AM4 | Ryzen 1000-5000 |
| AMD | AM5 | Ryzen 7000+ |

#### Server Motherboards
- Designed for **rack-mounted systems** (1U, 2U, 4U)
- **Multi-socket** — support 2 or more CPUs simultaneously
- More **memory slots** — 16-32 DIMM slots for ECC RAM
- Redundant power supply support
- IPMI (Intelligent Platform Management Interface) for remote management
- **Cybersecurity use:** IPMI vulnerabilities have been widely exploited — remote access to server hardware

---

### 3.5 The BIOS

#### BIOS — Basic Input Output System
- **Firmware** of the system — software stored on a chip on the motherboard
- The very first software that runs when you power on a computer
- Responsibilities:
  1. **Initialise CPU and memory**
  2. **POST** — Power On Self Test — checks that hardware is working
  3. **Find and load the boot loader** from storage
  4. Hand control over to the OS

#### POST — Power On Self Test
- Runs every time you power on
- Checks: CPU, RAM, GPU, keyboard, storage
- If POST fails: beep codes or LED indicators show what failed
- One beep = POST passed, system OK

#### Legacy BIOS
- Original BIOS standard from 1975
- **16-bit** processor mode — very limited
- Maximum bootable drive size: **2.2 TB** (MBR partition table)
- Text-only interface, no mouse support
- Being replaced by UEFI

#### UEFI BIOS — Unified Extensible Firmware Interface
- **Modern replacement for legacy BIOS**
- A **defined standard** — not proprietary to one manufacturer
- **64-bit** processor mode — much more capable
- Supports drives larger than **2.2 TB** (GPT partition table)
- Graphical interface — mouse support
- Secure Boot support
- Faster boot times
- Network capability — can update firmware over internet
- **Cybersecurity use:** UEFI rootkits (bootkits) survive OS reinstall — very hard to remove

---

### 3.5 BIOS Settings

#### Accessing BIOS/UEFI Setup
- Press during POST (before OS loads):
  - **Del, F1, F2** — most common
  - **Ctrl+S, Ctrl+Alt+S** — some older systems
- On Windows 11: **Shift + Restart** → Troubleshoot → Advanced Options → UEFI Firmware Settings

#### Fast Startup (Windows)
- Does **not actually shut down** — saves system state to disk (hybrid sleep)
- Makes next boot faster but can cause issues with dual boot
- **Why we disabled it** when setting up your Ubuntu dual boot — it locks the Windows drive

#### Boot Options
- **Boot order** — which device the BIOS tries to boot from first
  - Example: USB → SSD → Network
- **Disable hardware** — can turn off unused ports and devices in BIOS
- **USB permissions** — can restrict USB boot or usage entirely
  - The US Dept of Defence banned USB flash media for **15 months in 2008** due to the **Agent.BTZ (SillyFDC) worm** — spread through USB drives on classified networks
- **Cybersecurity use:** Controlling boot order prevents booting from a live USB to bypass OS login

#### Fan Control
- Configure fan curves — temperature vs fan speed
- Silent mode, performance mode, manual control
- Important for thermal management — especially on your ASUS laptop

#### Secure Boot
- **UEFI Secure Boot** — only allows signed, trusted bootloaders to run
- Prevents malicious bootloaders and rootkits from loading before the OS
- Uses digital certificates stored in UEFI firmware
- **Cybersecurity use:** Disabling Secure Boot (like we did for Ubuntu) opens the system to bootkit attacks — re-enable if possible after setup

#### Boot Password Management
- **Boot password** — required to start the computer at all
- **Supervisor/Admin password** — required to access BIOS settings
- Stored in CMOS/NVRAM on the motherboard
- **Bypass method:** Remove CMOS battery to reset (physical access required)
- **Cybersecurity use:** Without a boot password, attacker with physical access can boot from USB and bypass the OS

#### CMOS — Complementary Metal Oxide Semiconductor
- Small chip that stores BIOS settings and system time
- Powered by a small **CR2032 coin cell battery** on the motherboard
- **Usually flash memory these days** — not actual CMOS technology anymore
- Removing the battery resets all BIOS settings to default (including passwords)
- **Cybersecurity use:** Physical CMOS reset = bypasses BIOS password

#### Temperature Monitoring
- BIOS monitors CPU, GPU, and motherboard temperatures
- Shows current temps, fan speeds, voltages
- Can set thermal shutdown threshold — prevents hardware damage

#### Virtualisation Support
- Must be **enabled in BIOS** to run virtual machines
- **AMD-V (AMD Virtualisation)** — AMD processors
- **VT-x (Intel Virtualisation Technology)** — Intel processors
- Also called: AMD SVM, Intel VMX
- **Required for:** VirtualBox, VMware, Hyper-V, WSL2
- Check if enabled on your Ubuntu system:
```bash
grep -E "vmx|svm" /proc/cpuinfo | head -5
```
- If output shows `vmx` (Intel) or `svm` (AMD) — virtualisation is enabled

---

### 3.5 HSM and TPM — Explained Simply

#### Why We Need These
- We use encryption for everything — HTTPS, BitLocker, password managers, VPNs
- Encryption requires **secret keys** — but where do you store a secret key safely?
- If you store the key in software, malware can steal it
- Solution: store keys in **dedicated hardware** that software cannot directly access

---

#### TPM — Trusted Platform Module

**Think of TPM like a safe bolted to your motherboard:**
- A **hardware chip** on the motherboard (or built into the CPU)
- Specification for **cryptographic functions** — defined by TCG (Trusted Computing Group)

**What TPM does:**
- **Persistent memory** — stores permanent, unique cryptographic keys burned in at manufacture
  - Endorsement Key (EK) — unique to every TPM chip, never leaves the chip
- **Versatile memory** — stores additional keys and data that can be changed
- **Password protected** — access requires authentication
- Performs cryptographic operations **inside the chip** — keys never exposed to software

**Real world uses of TPM:**
- **BitLocker** (Windows full disk encryption) — stores the encryption key in TPM
  - Without TPM, BitLocker key stored on USB — less secure
  - With TPM, drive only decrypts on the exact machine it was encrypted on
- **Secure Boot** — stores trusted boot certificates
- **Windows Hello** — stores biometric authentication keys
- **VPN certificates** — stores private keys securely

**TPM versions:**
- **TPM 1.2** — older, limited algorithms
- **TPM 2.0** — current standard, required for Windows 11

**Cybersecurity use:**
- TPM sniffing attack — on older systems, the communication between CPU and discrete TPM chip can be intercepted on the bus
- Modern CPUs with built-in TPM (fTPM) are immune to this

---

#### HSM — Hardware Security Module

**Think of HSM like an enterprise-grade bank vault for cryptographic keys:**
- Used in **large environments** — banks, certificate authorities, data centres
- **Dedicated hardware device** — often a PCIe card or external appliance
- Performs high-speed cryptographic operations entirely in hardware
- Never exposes private keys to the host system

**Real world uses of HSM:**
- Certificate Authorities (CAs) — stores the root CA private key (if this key is stolen, all certificates it issued are compromised)
- Banks — stores encryption keys for card transactions
- Government — stores classified encryption keys
- Payment processors — stores card data encryption keys

#### TPM vs HSM Comparison

| Feature | TPM | HSM |
|---|---|---|
| Location | Chip on motherboard / inside CPU | PCIe card or external appliance |
| Scale | Single device | Enterprise / data centre |
| Purpose | Secure boot, disk encryption, device identity | Key management, certificate authority, high-volume crypto |
| Performance | Basic cryptographic operations | High-speed, hardware-accelerated crypto |
| Cost | ~$0 (built-in) to $20 (discrete chip) | $1,000–$100,000+ |
| Key backup | Limited | Full key backup and recovery |
| Use case | Your laptop's BitLocker, Windows Hello | Bank transaction processing, SSL certificate signing |

**Simple analogy:**
- **TPM** = the safe in your bedroom (personal, built-in, protects your stuff)
- **HSM** = the vault in a bank (enterprise, high security, protects millions of transactions)

**Cybersecurity use:**
- Stealing an HSM or compromising its admin credentials = access to all encrypted data it protects
- HSMs are air-gapped in high-security environments

---

### 3.5 CPU Features

#### 32-bit vs 64-bit Processors

**32-bit processor:**
- Can address **2^32** memory locations = **4 GB maximum RAM**
- Runs 32-bit operating systems and applications
- Architecture called **x86**
- Cannot run 64-bit applications

**64-bit processor:**
- Can address **2^64** memory locations = **17 billion GB (17 exabytes) theoretical maximum**
- Runs both 32-bit AND 64-bit operating systems and applications
- Architecture called **x64** (also called AMD64 or x86-64)
- Practical RAM limit today: 128GB–2TB depending on platform

**Compatibility:**
- ✅ 64-bit OS can run 32-bit apps (via compatibility layer — WOW64 on Windows)
- ❌ 32-bit OS cannot run 64-bit apps
- ✅ 64-bit CPU can run 32-bit OS
- ❌ 32-bit CPU cannot run 64-bit OS

**Hardware drivers:**
- **x86** drivers for 32-bit OS
- **x64** drivers for 64-bit OS
- Not interchangeable — must install correct driver version

**Cybersecurity use:**
- 32-bit processes on 64-bit systems have different memory protections
- Many exploits target the 32-bit compatibility layer (WOW64)

---

#### ARM — Advanced RISC Machine

**What is ARM:**
- CPU architecture developed by **ARM Ltd** (now owned by SoftBank)
- **RISC** — Reduced Instruction Set Computer
  - Fewer, simpler instructions than x86 (CISC — Complex Instruction Set)
  - Each instruction does less but executes faster and uses less power
- ARM does NOT manufacture CPUs — they licence the architecture to other companies
  - Apple (M1, M2, M3 chips), Qualcomm (Snapdragon), Samsung (Exynos), NVIDIA (Tegra)

**Why ARM is important:**
- Dominates **mobile devices** — almost every phone and tablet uses ARM
- Apple switched Macs to ARM (Apple Silicon) in 2020
- ARM servers growing in data centres — AWS Graviton, Ampere
- Lower power consumption = longer battery life = less heat

**ARM vs x86:**
| Feature | ARM | x86 |
|---|---|---|
| Power consumption | Very low | Higher |
| Performance per watt | Excellent | Good |
| Instruction set | RISC (simple) | CISC (complex) |
| Primary use | Mobile, tablets, embedded | Desktop, laptop, server |
| Examples | Apple M3, Snapdragon 8 Gen 3 | Intel Core i9, AMD Ryzen 9 |

**Cybersecurity use:**
- ARM TrustZone — hardware security extension that splits processor into secure and non-secure worlds
- Many mobile exploits target ARM-specific features

---

#### Processor Cores

**Single Core:**
- One processing unit — does one thing at a time
- Multitasking = rapidly switching between tasks (not true parallel)

**Dual Core:**
- **2 cores** — two independent processing units on one chip
- True parallel processing — two tasks simultaneously
- Modern minimum for any computer

**Quad Core:**
- **4 cores** — four independent processing units
- Standard for modern laptops and desktops
- Your ASUS laptop likely has 4-8 cores

**Octa Core:**
- **8 cores** — common in modern phones and mid-range laptops
- ARM big.LITTLE architecture — 4 performance cores + 4 efficiency cores

**Multi-core:**
- General term for any processor with more than one core
- Server CPUs: 32, 64, even 128 cores (AMD EPYC)

**How cores help:**
```
Single core running 4 apps:
App1 → App2 → App3 → App4 → App1... (rapid switching, feels simultaneous)

Quad core running 4 apps:
Core1: App1 | Core2: App2 | Core3: App3 | Core4: App4 (truly simultaneous)
```

**Hyper-Threading / SMT:**
- Intel: **Hyper-Threading (HT)**
- AMD: **Simultaneous Multi-Threading (SMT)**
- Each physical core appears as **2 logical cores** to the OS
- A 4-core CPU with HT appears as 8 logical processors
- Not as fast as real cores but improves utilisation of idle execution units

**Cybersecurity use:**
- **Spectre and Meltdown** — CPU vulnerabilities that exploit speculative execution across cores
- Hyper-threading can leak data between processes sharing a physical core

---

#### CPU Die
- The actual **silicon chip** inside the CPU package
- Contains all the transistors, cores, cache, and other circuits
- Modern CPUs: billions of transistors on a die measured in nanometres
  - Intel 13th gen: 10nm process
  - Apple M3: 3nm process (smaller = faster + less power)
- **Multi-die design** — some CPUs contain multiple dies in one package
  - AMD Ryzen with 3D V-Cache stacks multiple dies vertically
- **Chiplet design** — CPU split into multiple smaller dies
  - AMD uses separate chiplets for cores, I/O, and cache

---

## Terminal Practice + Expected Output

### Check Motherboard Info
```bash
sudo dmidecode -t baseboard
```
**Expected output:**
```
Base Board Information
        Manufacturer: ASUSTeK COMPUTER INC.
        Product Name: ASUS TUF Gaming FX505
        Version: 1.0
        Serial Number: ...
        Asset Tag: ...
        Features: Board is a hosting board
```

---

### Check BIOS/UEFI Info
```bash
sudo dmidecode -t bios
```
**Expected output:**
```
BIOS Information
        Vendor: American Megatrends Inc.
        Version: 310
        Release Date: 03/15/2021
        Characteristics:
                UEFI is supported
                Targeted content distribution is supported
```
- `UEFI is supported` confirms you have UEFI BIOS

---

### Check Virtualisation Support
```bash
grep -E "vmx|svm" /proc/cpuinfo | head -3
```
**Expected output (Intel CPU):**
```
flags: ... vmx ... — Intel VT-x enabled
```
**Expected output (AMD CPU):**
```
flags: ... svm ... — AMD-V enabled
```
- If you see `vmx` or `svm` → virtualisation is enabled in BIOS ✅
- If no output → need to enable in BIOS settings

---

### Check CPU Details
```bash
lscpu
```
**Expected output:**
```
Architecture:            x86_64
CPU(s):                  8
Thread(s) per core:      2
Core(s) per socket:      4
Model name:              Intel Core i5-9300H
CPU MHz:                 800.000
CPU max MHz:             4100.0000
Virtualisation:          VT-x
L1d cache:               128 KiB
L2 cache:                1 MiB
L3 cache:                8 MiB
```
- `x86_64` = 64-bit processor
- `Thread(s) per core: 2` = Hyper-Threading enabled
- `Core(s) per socket: 4` = Quad core CPU
- `CPU max MHz: 4100` = max boost clock 4.1 GHz
- `Virtualisation: VT-x` = Intel virtualisation enabled

---

### Check CPU Temperature
```bash
sensors
```
**Expected output:**
```
coretemp-isa-0000
Core 0:        +42.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +41.0°C  (high = +100.0°C, crit = +100.0°C)
Core 2:        +43.0°C  (high = +100.0°C, crit = +100.0°C)
Core 3:        +40.0°C  (high = +100.0°C, crit = +100.0°C)
```
- Under 60°C at idle = healthy
- Under 90°C under load = normal for laptops
- Above 95°C = thermal throttling happening

---

## 🔑 Additional Important Concepts You Missed

### CPU Cache
- Ultra-fast memory built directly into the CPU die
- Faster than RAM — stores frequently used data for instant access
- **L1 cache** — smallest (32-256KB), fastest, one per core
- **L2 cache** — medium (256KB-4MB), fast, one per core
- **L3 cache** — largest (4-64MB), slightly slower, shared between all cores
- **Cybersecurity use:** Cache-timing attacks — measuring cache access times reveals what data the CPU is processing (used in Spectre attack)

### CPU Clock Speed
- Measured in **GHz** — how many cycles per second
- More GHz = faster (generally)
- **Base clock** — guaranteed minimum speed
- **Boost/Turbo clock** — maximum speed for short bursts
- **Cybersecurity use:** Underclocking can be used to slow down brute force attacks on encrypted systems

### PCIe Lanes
- Each device needs PCIe lanes to communicate with the CPU
- CPU has a limited number of total lanes (16-64 typically)
- GPU uses x16, NVMe uses x4, other cards use x1-x4
- **Cybersecurity use:** PCIe lane exhaustion = denial of service for high-performance systems

### BIOS/UEFI Attacks
- **UEFI rootkit** — malware stored in UEFI firmware survives OS reinstall and even drive replacement
- Example: LoJax (2018) — first known UEFI rootkit used in the wild by APT28
- **Protection:** Secure Boot + firmware signing + regular UEFI updates
- **Cybersecurity use:** UEFI attacks are nation-state level — extremely persistent and hard to detect

---

## What I Didn't Understand
- TPM sniffing attack in more detail *(research later)*
- How ARM TrustZone divides secure and non-secure worlds *(research later)*

## 3 Key Things I Learned
1. TPM stores encryption keys in hardware — BitLocker only decrypts on the exact machine it was encrypted on
2. Removing the CMOS battery resets all BIOS settings including passwords — physical security is critical
3. Hyper-Threading makes 4 physical cores appear as 8 logical processors — but Spectre exploits this shared execution