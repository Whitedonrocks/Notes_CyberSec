# CompTIA A+ 220-1202 — Week 2 Day 7 Notes
## Core 2 Begins!

---

## Videos Watched
- ✅ 1.1 Operating Systems Overview
- ✅ 1.1 File Systems
- ✅ 1.2 Installing Operating Systems
- ✅ 1.2 Upgrading Windows
- ✅ 1.3 An Overview of Windows
- ✅ 1.3 Windows Features

---

## Key Concepts

### 1.1 Operating Systems Overview

#### Why Do We Need an OS?
- **Controls interaction** between hardware components
- Provides a **common platform** for applications to run on
- Provides a way for **humans to interact** with the machine (GUI or CLI)

#### Standard OS Features
- **File management** — create, read, update, delete files and folders
- **Application support** — run and manage programs
- **Input and output support** — keyboard, mouse, display, network, storage

---

#### Major Operating Systems

**Microsoft Windows:**
- Largest market share in desktop OS (~75%)
- Dominant in enterprise and business environments
- Proprietary — closed source, paid license
- Versions: Windows 10, Windows 11 (for A+ exam focus)

**Linux:**
- **Free, Unix-compatible** software system
- Open source — anyone can view, modify, distribute
- Many different **distributions (distros):**
  - **Ubuntu** — most beginner friendly (what you use!)
  - **Debian** — stable, Ubuntu is based on it
  - **Red Hat** — enterprise focused, paid support
  - **Fedora** — cutting edge, Red Hat sponsored
  - **Kali** — security/pentesting focused
  - **CentOS/Rocky Linux** — free Red Hat alternative for servers
- **Cybersecurity use:** Most servers, cloud infrastructure, and security tools run on Linux

**Apple macOS:**
- Desktop OS running **exclusively on Apple hardware**
- Unix-based — shares DNA with Linux
- Closed source — Apple controls hardware and software
- Known for stability and creative professional use

**Chrome OS:**
- Google's operating system
- **Based on Linux kernel**
- Designed primarily for web-based tasks
- Runs on Chromebooks — cheap, fast boot, cloud-focused
- Can run Android apps and Linux apps

**Apple iPadOS:**
- Operating system for **Apple iPad tablets**
- Derived from iOS but with tablet-specific features
- Supports multitasking, Apple Pencil, keyboard support

**Apple iOS:**
- **Closed source** — Apple controls everything
- **Exclusive to Apple products** (iPhone, iPod Touch)
- Apps developed using **Apple SDK on macOS**
- Highly secure but limited customisation

**Google Android:**
- Developed by the **Open Handset Alliance** (led by Google)
- **Open source OS based on Linux kernel**
- Most popular mobile OS worldwide (~72% market share)
- Apps developed on **Windows, macOS, or Linux using Android SDK (ADK)**
- More customisable than iOS

#### OS Comparison

| OS | Source | Platform | Use Case |
|---|---|---|---|
| Windows | Closed | x86/x64 | Desktop, enterprise |
| Linux | Open | Any | Servers, security, development |
| macOS | Closed | Apple hardware | Creative, professional |
| Chrome OS | Open (Linux) | Chromebook | Web-based, education |
| iOS | Closed | iPhone | Mobile |
| Android | Open (Linux) | Any phone | Mobile |
| iPadOS | Closed | iPad | Tablet |

---

#### Vendor Specific Limitations

**End of Life (EOL):**
- Every OS has an end date when vendor stops providing updates
- After EOL: no security patches = vulnerabilities never fixed
- Example: Windows 7 EOL = January 2020 — still widely used but dangerous
- Windows 10 EOL = October 2025
- **Cybersecurity use:** EOL systems are prime targets — known vulnerabilities with no patches

**Updating:**
- Must keep OS updated — patches fix security vulnerabilities
- Update process differs per OS
- Enterprise: managed updates via WSUS (Windows), Ansible (Linux)

**Compatibility:**
- Applications written for one OS generally cannot run on another
- **Almost no direct application compatibility** between Windows and macOS/Linux
- Solutions: Wine (run Windows apps on Linux), virtual machines, web apps

---

### 1.1 File Systems

#### What is a File System?
- Before data can be written to a partition it **must be formatted**
- The OS expects data to be written in a **particular format**
- File system defines: how files are named, stored, organised, and retrieved

---

#### NTFS — NT File System
- **Default Windows file system** since Windows NT
- Major improvements over FAT32:
  - Supports files larger than 4GB
  - Maximum volume size: **16 exabytes** (theoretical)
  - **File permissions** — control who can access files
  - **Encryption** — EFS (Encrypting File System) built in
  - **Compression** — compress files to save space
  - **Journaling** — logs changes before writing — recovers from crashes
  - **Disk quotas** — limit how much space each user can use
- **Cybersecurity use:** NTFS alternate data streams (ADS) — hidden data can be stored alongside files — used by malware to hide payloads

---

#### ReFS — Resilient File System
- **The future of Windows file system** — an update/replacement for NTFS
- Designed for **huge storage requirements** (data centres, servers)
- Features:
  - **Constant data availability** — RAID-like redundancy built in
  - **Data integrity** — automatically detects and corrects corruption
  - Handles very large files and volumes
- **Measured integration** — not replacing NTFS entirely yet
- Available in: Windows 10 Pro for Workstations, Windows Server

---

#### FAT — File Allocation Table
- Oldest Windows file system — originally from DOS era

**FAT32:**
- Updated version of FAT
- Maximum **volume size: 2 terabytes**
- Maximum **file size: 4 gigabytes** (biggest limitation)
- Widely compatible — works on Windows, macOS, Linux, cameras, TVs
- Used for: USB drives, SD cards, older devices

**exFAT — Extended File Allocation Table:**
- Designed to replace FAT32 for flash storage
- **Files can be larger than 4GB** — removes FAT32's biggest limitation
- Good compatibility across Windows, macOS, Linux
- Used for: large USB drives, SD cards for cameras/drones

| File System | Max File Size | Max Volume | Use Case |
|---|---|---|---|
| FAT32 | 4 GB | 2 TB | USB drives, SD cards |
| exFAT | 16 EB | 128 PB | Large USB drives, cameras |
| NTFS | 16 EB | 16 EB | Windows system drive |
| ReFS | 16 EB | 1 YB | Windows servers, large storage |

---

#### ext4 — Fourth Extended File System
- **Default Linux file system** (including your Ubuntu!)
- Fourth generation of the extended file system family
- Features: journaling, large file support, backwards compatible with ext2/3
- Maximum file size: **16 terabytes**
- Maximum volume size: **1 exabyte**
- **Cybersecurity use:** ext4 journaling preserves forensic evidence of file operations

**Check your filesystem:**
```bash
df -T
# Look for "ext4" on your Ubuntu partition
```

---

#### XFS
- **High performance file system for Linux**
- Designed for **scalability** — handles very large files and filesystems
- **Built-in journaling** — fast recovery after crash
- Used by: Red Hat Enterprise Linux (default), large database servers
- Excellent for: video editing, large media files, high-throughput workloads

---

#### APFS — Apple File System
- Apple's modern file system — replaced HFS+
- **Optimised for SSD** — takes advantage of flash storage characteristics
- Features: snapshots, cloning, strong encryption, space sharing
- Used on: all modern Macs, iPhones, iPads
- **Cybersecurity use:** APFS snapshots are used by Time Machine — forensic investigators can access previous file versions

---

### 1.2 Installing Operating Systems

#### Boot Methods

| Method | Description | Use Case |
|---|---|---|
| **USB storage** | Bootable USB drive | Most common for OS install |
| **Network boot (PXE)** | Pre-boot Execution Environment — boots from network server | Enterprise mass deployment |
| **SSD/HDD** | Boot from installed drive | Normal operation |
| **Internet-based** | Download OS during install | Linux, macOS recovery, Windows updates |
| **External/hot-swappable** | External USB drive, can mount ISO | Testing, recovery |
| **Internal hard drive** | Separate drive for second OS | Dual boot |
| **Multiboot** | Choose from two or more OS at startup | Development, testing (your setup!) |

**PXE — Pre-boot Execution Environment:**
- Boot from network server without any local storage
- Server sends OS image to computer over network
- Used in: enterprise deployments, thin clients, diskless workstations
- **Cybersecurity use:** Rogue PXE server attack — attacker sets up fake PXE server → computers boot malicious OS

---

#### Types of Installation

**Clean Install:**
- Wipe the slate clean and install fresh
- All previous data, applications, and settings removed
- Best for: new computers, recovering from malware, major OS upgrades
- Always back up first!

**In-Place Upgrade:**
- Maintain existing applications and data
- OS upgraded while keeping files and installed programs
- Faster than clean install but carries over any existing problems
- Example: upgrading Windows 10 → Windows 11 keeping all files

**Image Deployment:**
- Deploy a **clone** of a pre-configured OS to many computers
- Relatively quick — one image pushed to many machines
- Can be **completely automated** — no user interaction needed
- Used in enterprises — deploy 500 identical workstations in hours
- Tools: Windows Deployment Services (WDS), SCCM, Clonezilla

**Remote Network Installation:**
- Install OS over the network from a remote server
- Uses PXE boot
- No physical media needed at each workstation

**Recovery Partition:**
- Hidden partition on the drive with a recovery image
- Restore the OS to factory state without installation media
- Usually accessible by pressing F11 or specific key at boot

**Repair Installation:**
- Fix problems with the Windows OS
- **Does NOT modify user files** — keeps personal data intact
- Replaces corrupted system files
- Run from Windows installation media

**Zero Touch Deployment:**
- **Automatic install** with no human interaction required
- Streamlined implementation — computer configures itself
- Used in large enterprises — unbox, plug in, walks away
- Tools: Microsoft Autopilot, MDT (Microsoft Deployment Toolkit)

---

#### Disk Partitioning

**What is a Partition?**
- Separates a physical drive into **logical pieces**
- Useful for: maintaining separate OS, separating data from OS, dual boot
- Your drive has: Windows partition + Ubuntu partition + EFI partition

---

**GPT — GUID Partition Table:**
- **GUID** = Globally Unique Identifier
- Modern partition style — required for UEFI boot
- Can have up to **128 partitions**
- Maximum partition size: **over 9 billion TB** (Windows caps at 256 TB)
- Required for drives larger than 2 TB
- Your Ubuntu drive uses GPT (we set this up in Rufus!)

**MBR — Master Boot Record:**
- Older partition style — used with legacy BIOS
- Maximum partition size: **2 TB** — biggest limitation
- Maximum **4 primary partitions** per drive
- Two types of partitions:
  - **Primary** — bootable partitions, maximum 4, one marked as active
  - **Extended** — used for extending beyond the 4 partition limit (contains logical partitions)

| Feature | MBR | GPT |
|---|---|---|
| Max partition size | 2 TB | 256 TB (Windows) |
| Max partitions | 4 primary | 128 |
| Boot firmware | Legacy BIOS | UEFI |
| Redundancy | None | Backup at end of disk |
| Compatibility | Older systems | Modern systems |

---

#### Quick Format vs Full Format

**Quick Format:**
- Creates a **new file table** only
- Looks like data is erased — but it is NOT
- Old data still physically on disk — recoverable with forensic tools
- Fast — takes seconds
- **Cybersecurity use:** Quick-formatted drives handed to attackers/investigators still contain all original data

**Full Format:**
- **Writes zeros to the entire disk**
- Data is unrecoverable through normal means
- Slow — takes hours for large drives
- Use before selling or disposing of a drive containing sensitive data
- **Cybersecurity use:** Even full format may not be enough for top-secret data — use DoD 7-pass wipe or physical destruction

---

### 1.2 Upgrading Windows

#### Upgrade vs Clean Install

| | Upgrade | Clean Install |
|---|---|---|
| User files | Kept ✅ | Deleted ❌ |
| Applications | Kept ✅ | Deleted ❌ |
| Settings | Kept ✅ | Reset ❌ |
| Speed | Faster | Slower |
| Risk | Carries old problems | Fresh start |
| Best for | Convenience | Performance/malware recovery |

#### In-Place Upgrade
- Upgrade the existing OS while keeping everything
- Maintains consistency — users keep their environment
- Windows Update or installation media

#### Before Installation Checklist
- ✅ Check **minimum OS requirements** (RAM, storage, CPU)
- ✅ Run **hardware compatibility check** — Windows 11 requires TPM 2.0
- ✅ Check **application and driver compatibility** — old apps may not work
- ✅ **Back up all data** — always before any OS change

#### Windows Product Lifecycle
- **Quality updates** — monthly security patches (Patch Tuesday)
- **Feature updates** — new features, twice yearly for Windows 10
- **Support provided after release** for defined period
- Also called the **Modern Lifecycle Policy**

#### TPM Requirement for Windows 11
- Windows 11 **requires TPM 2.0** — hard requirement
- Why: Secure Boot, BitLocker, Windows Hello all depend on TPM
- If no TPM 2.0 — cannot upgrade to Windows 11 officially
- Check TPM: `tpm.msc` in Windows Run dialog

---

### 1.3 An Overview of Windows

#### Windows Versions for A+ Exam
- Focus on **Windows 10 and Windows 11** for Core 2 exam

---

#### Windows 10 Editions

| Edition | Target | Key Features |
|---|---|---|
| **Home** | Home users | Microsoft account integration, Windows Defender, Cortana, basic features |
| **Pro** | Business users | + Remote Desktop Host, BitLocker full disk encryption, join Windows Domain, Hyper-V |
| **Pro for Workstations** | Power users | + ReFS support, NVMe/persistent memory support, faster file sharing |
| **Enterprise** | Large organisations | + AppLocker, BranchCache, Granular UX control, DirectAccess |

**Key features explained:**
- **BitLocker** — full disk encryption using TPM, available in Pro and above
- **Remote Desktop Host** — allows other computers to connect to this PC remotely (Pro+)
- **AppLocker** — control which applications users can run (Enterprise only)
- **BranchCache** — caches content from central servers at branch offices — reduces WAN traffic
- **Granular UX control** — IT can lock down and customise the user interface

#### Windows 10 Support
- Mainstream support ends: **October 14, 2025**
- After that: no new features, security patches only for extended support customers

---

#### Windows 11 Editions

| Edition | Target | Key Features |
|---|---|---|
| **Home** | Home users | New UI, Snap layouts, Microsoft Teams integration, Android apps |
| **Pro** | Business | + BitLocker, Remote Desktop, Hyper-V, Windows Sandbox |
| **Pro for Workstations** | Power users | + ReFS, persistent memory, faster file sharing |
| **Enterprise** | Large orgs | + AppLocker, advanced security, DirectAccess, UE-V |

**Windows 11 requirements:**
- TPM 2.0 (mandatory)
- Secure Boot capable
- 64-bit CPU (no 32-bit support at all)
- 4GB RAM minimum
- 64GB storage minimum
- DirectX 12 compatible GPU

#### Windows N Editions
- **N editions** are Windows versions **for Europe**
- **N = Not with Media Player** — European antitrust regulations required Microsoft to sell Windows without Windows Media Player bundled
- Windows 10 N, Windows 11 N — same as regular but without media features
- Media Feature Pack available separately for free

---

### 1.3 Windows Features

#### Windows at Work
- Large scale enterprise support
- Security concerns — centrally managed
- Working on documents, spreadsheets, presentations

---

#### Domain Services — Explained Simply

**Active Directory Domain Services (AD DS):**
- Think of it as the **master directory/database** for an entire organisation
- Everything documented in one place — all users, computers, printers, policies
- **Distributed architecture** — can span multiple servers across multiple locations
- Many different uses:
  - Centralise user accounts — one login works on any computer in the organisation
  - Apply policies to all computers at once (Group Policy)
  - Control access to resources (files, printers, applications)

**Simple analogy:**
```
Without Active Directory:
  Each computer has its own usernames and passwords
  IT must configure each computer separately
  User needs different login for each computer

With Active Directory:
  One username/password works on ALL computers
  IT configures everything from one central server
  User logs in anywhere and gets their files and settings
```

**Cybersecurity use:** Active Directory is the most attacked component in enterprise networks — compromising AD = controlling the entire organisation. Tools like BloodHound map AD relationships to find attack paths.

---

#### Organising Network Devices

**Windows Workgroup:**
- Simple peer-to-peer network
- No central server — each computer manages its own users
- Each computer must have the same username/password for sharing
- Maximum ~20 computers before it becomes unmanageable
- Used in: small home or office networks
- **Default** for home Windows computers

**Windows Domain:**
- Centralised network managed by a server (Domain Controller)
- One login works on all computers
- IT controls everything centrally via Active Directory
- Scales to thousands of computers
- Used in: businesses, schools, enterprises
- Requires: Windows Server running Active Directory

---

#### Desktop Styles

**Work (Domain-joined):**
- Managed by IT department
- Group Policy restrictions apply
- Centralised software deployment
- Remote monitoring and management

**Home (Workgroup):**
- Personal, unmanaged
- User has full control
- No central management

---

#### Remote Desktop Protocol (RDP)
- **RDP** — allows connecting to and controlling another Windows computer remotely
- Full graphical desktop — like sitting in front of the remote computer
- **Port: TCP 3389**
- Components:
  - **RDP Client** — software on your computer to connect (mstsc.exe on Windows)
  - **Remote Desktop Service** — must be enabled on the target computer
- Available in: Windows 10/11 Pro and above (NOT Home)
- **Cybersecurity use:** RDP is one of the most attacked services on the internet — brute force, credential stuffing, BlueKeep vulnerability (CVE-2019-0708). Never expose RDP directly to the internet.

---

#### RAM Support Limitations

| Edition | Maximum RAM |
|---|---|
| Windows 10/11 Home | 128 GB |
| Windows 10/11 Pro | 2 TB |
| Windows 10/11 Pro Workstations | 6 TB |
| Windows 10/11 Enterprise | 2 TB |

---

#### BitLocker and EFS — Data Confidentiality

**EFS — Encrypting File System:**
- **Built into the NTFS file system**
- Protects **individual files or folders**
- Encryption tied to user account — only that user can decrypt
- Transparent to the user — files open normally when logged in
- If OS is reinstalled or user account deleted — files become inaccessible
- **Cybersecurity use:** EFS can complicate forensic investigations — encrypted files require user's certificate to decrypt

**BitLocker:**
- **Full disk encryption** — everything on the drive is encrypted
- Uses **TPM** to store the encryption key
- Even if drive is removed and put in another computer — data unreadable
- Requires: Windows Pro or above, TPM 2.0 recommended
- **BitLocker To Go** — encrypts USB drives and external storage
- **Cybersecurity use:** BitLocker is excellent protection against physical theft — stolen laptop's data is completely unreadable without the recovery key

| Feature | EFS | BitLocker |
|---|---|---|
| Scope | Individual files/folders | Entire drive |
| Key storage | User certificate | TPM chip |
| Available in | All NTFS editions | Pro and above |
| Protection against | Other users on same PC | Physical theft of drive |
| Transparent to user | Yes | Yes |

---

#### Group Policy Editor

**Local Group Policy:**
- Configure security and behaviour settings for a single computer
- Open with: `gpedit.msc` (Windows Run dialog)
- Available in: Windows Pro and above (NOT Home)
- Settings: password policies, software restrictions, desktop lockdown

**Group Policy Management Console (GPMC):**
- Manage Group Policy across an **entire Active Directory domain**
- Apply policies to hundreds of computers simultaneously
- Examples of what Group Policy can do:
  - Force screensaver after 5 minutes
  - Prevent users from installing software
  - Deploy software to all computers
  - Configure Windows Firewall settings
  - Disable USB storage on all computers
  - Set minimum password length and complexity
- **Cybersecurity use:** Group Policy is a powerful security tool — and a powerful attack tool. Attackers who compromise AD can modify Group Policy to push malware to all domain computers simultaneously.

---

## Terminal Practice + Expected Output

### Check OS and Kernel Version
```bash
uname -a
```
**Expected output:**
```
Linux prayagn 6.8.0-51-generic #52-Ubuntu SMP PREEMPT_DYNAMIC x86_64 GNU/Linux
```
- `Linux` = OS kernel
- `6.8.0-51-generic` = kernel version
- `x86_64` = 64-bit architecture

---

### Check Ubuntu Version Details
```bash
lsb_release -a
```
**Expected output:**
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 24.04.1 LTS
Release:        24.04
Codename:       noble
```

---

### Check Filesystem Types
```bash
df -T
```
**Expected output:**
```
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/nvme0n1p5 ext4       59G   26G   30G  47% /
tmpfs          tmpfs      7.8G  1.4M  7.8G   1% /dev/shm
/dev/nvme0n1p1 vfat        96M   38M   59M  39% /boot/efi
```
- `/dev/nvme0n1p5` uses **ext4** — your Ubuntu root partition ✅
- `/boot/efi` uses **vfat** — EFI system partition (FAT32 based) ✅

---

### Check Partition Layout
```bash
lsblk -f
```
**Expected output:**
```
NAME        FSTYPE  LABEL    UUID                                 MOUNTPOINT
nvme0n1
├─nvme0n1p1 vfat             xxxx-xxxx                            /boot/efi
├─nvme0n1p2                                                       (Windows reserved)
├─nvme0n1p3 ntfs    Windows  xxxxxxxx                             (Windows C: drive)
└─nvme0n1p5 ext4             xxxxxxxx-xxxx                        /
```
- Shows your full dual boot partition layout
- `ntfs` = Windows partition, `ext4` = Ubuntu partition

---

## 🔑 Additional Important Concepts You Missed

### Windows Registry
- **Central database** storing all Windows configuration settings
- Every hardware setting, user preference, and application config stored here
- Organised in hives: HKEY_LOCAL_MACHINE, HKEY_CURRENT_USER etc.
- Open with: `regedit` in Run dialog
- **Cybersecurity use:** Malware commonly modifies registry for persistence — adds itself to startup keys. Registry forensics reveals malware activity.

### Windows Safe Mode
- Starts Windows with **minimal drivers and services**
- Used for: troubleshooting, removing malware, fixing driver issues
- Access: hold Shift while clicking Restart → Troubleshoot → Advanced → Startup Settings
- **Cybersecurity use:** Some malware disables Safe Mode to prevent removal — check if Safe Mode boots correctly on suspicious systems

### UAC — User Account Control
- Prompts for confirmation or admin password when making system changes
- Prevents malware from silently making system changes
- The "Are you sure?" popup in Windows
- **Cybersecurity use:** UAC bypass is a common malware technique — runs malicious code with elevated privileges without triggering the prompt

### File System Journaling
- Logs what changes are about to be made BEFORE making them
- If system crashes mid-write — journal used to recover
- NTFS, ext4, XFS all use journaling
- **Cybersecurity use:** Journal entries can be forensically analysed to reconstruct file system activity even after deletion

---

## What I Didn't Understand
- Active Directory attack paths with BloodHound *(research in Phase 5)*
- Group Policy abuse by attackers *(research in Phase 5)*

## 3 Key Things I Learned
1. Quick format does NOT erase data — forensic tools can recover everything. Only full format (zeros) or physical destruction truly wipes a drive
2. Active Directory is the single most attacked component in enterprise networks — one compromised AD = entire organisation compromised
3. BitLocker full disk encryption + TPM means even removing the drive and putting it in another computer gives you nothing — completely unreadable