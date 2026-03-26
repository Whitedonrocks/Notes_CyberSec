# CompTIA A+ 220-1201 — Week 2 Day 4 Notes

---

## Videos Watched
- ✅ 4.1 Virtualization Concepts
- ✅ 4.1 Virtualization Services
- ✅ 4.2 Cloud Models
- ✅ 4.2 Cloud Characteristics

---

## Key Concepts

### 4.1 Virtualization Concepts

#### What is Virtualization?
- Run **one computer as many operating systems** simultaneously
- The physical hardware is shared between multiple virtual machines
- Each VM thinks it has its own dedicated hardware — it does not
- Has been around since **1967** — IBM mainframes
- Modern virtualization is the foundation of all cloud computing

#### Types of Virtualization Setup

**Host-based Virtualization:**
- A regular computer (your laptop/desktop) runs a hypervisor as software
- Host OS runs normally, VMs run inside it
- Example: VirtualBox on your Ubuntu laptop
- Good for: development, testing, learning

**Standalone Server (Enterprise):**
- Dedicated server with no regular OS — runs hypervisor directly
- Hosts many VMs for the entire organisation
- Example: VMware ESXi server in a data centre
- Good for: production environments, enterprise deployments

---

#### Sandboxing
- An **isolated testing environment** completely separated from the rest of the system
- What happens in the sandbox stays in the sandbox — cannot affect the host
- If malware runs in a sandbox it cannot escape to damage the real system

**Uses of sandboxing:**
- **Malware analysis** — run suspicious files safely and observe behaviour
- **Software testing** — test new code without risking production systems
- **Browser isolation** — modern browsers sandbox each tab (if one tab crashes, others survive)
- **Mobile apps** — iOS and Android sandbox every app — apps cannot access each other's data
- **AV products** — antivirus tools sandbox suspicious files before scanning

**Real world example:**
```
Security researcher receives suspicious email attachment
→ Opens in sandbox VM
→ Malware executes, tries to spread, steal data
→ All activity monitored and logged
→ Sandbox destroyed after analysis
→ Real system untouched
```
- **Cybersecurity use:** Malware authors write sandbox-detection code — if malware detects it is in a VM it stays dormant. Signs: no mouse movement, no real user files, suspicious hardware specs

---

#### Building Applications with Virtualization

**Development stage:**
- Developer writes code in a VM matching the production environment
- "Works on my machine" problem eliminated — everyone uses identical VM

**Test stage:**
- QA team tests in identical VM — same OS, same dependencies, same config
- Can snapshot before testing, revert if something breaks

**Production stage:**
- Same VM image deployed to production servers
- Guaranteed to work — tested on identical environment

---

#### Legacy Software and Operating Systems
- Old software that only runs on old OS (Windows XP, Windows 7)
- Running old OS natively is a security risk — no more patches
- Solution: run the old OS in a VM, isolated from the network
- VM acts as a containment zone for the vulnerable legacy system
- **Cybersecurity use:** Legacy VMs are high-value targets — old unpatched OS inside a modern network

---

#### Cross-Platform Virtualization
- Run a different OS than your host on the same hardware
- Examples:
  - Run Windows on a Mac (VMware Fusion, Parallels)
  - Run Linux on Windows (VirtualBox — what you're doing!)
  - Run macOS on Linux (technically possible, legally grey)
- Makes it possible to test software on multiple platforms without multiple physical machines

---

### 4.1 Virtualization Services

#### The Hypervisor — Virtual Machine Manager
- Software (or firmware) that **creates and manages virtual machines**
- Allocates physical resources (CPU, RAM, storage, network) to each VM
- Ensures VMs are isolated from each other
- Also called: **VMM — Virtual Machine Manager**

#### How Virtualization Works — Block Diagram
```
Physical Hardware (CPU, RAM, Storage, Network)
         ↓
    [ Hypervisor ]
    ↙     ↓     ↘
[VM 1] [VM 2] [VM 3]
Windows  Linux  Kali
```
- Each VM gets a **virtual** CPU, virtual RAM, virtual disk, virtual network card
- VMs cannot see each other's memory or storage (isolated)
- Hypervisor manages all resource sharing

---

#### Types of Hypervisor

**Type 1 — Bare Metal Hypervisor:**
- Runs **directly on the hardware** — no host OS underneath
- Hardware → Hypervisor → VMs
- Fastest performance — no host OS overhead
- Used in enterprise data centres and cloud providers
- Examples: VMware ESXi, Microsoft Hyper-V (server), Xen, KVM
- AWS, Azure, Google Cloud all run Type 1 hypervisors

```
[Physical Hardware]
      ↓
[Type 1 Hypervisor]  ← runs directly on hardware
   ↙         ↘
[VM 1]      [VM 2]
```

**Type 2 — Hosted Hypervisor:**
- Runs **as an application on top of a host OS**
- Hardware → Host OS → Hypervisor → VMs
- Slightly slower — host OS adds overhead
- Used for: development, testing, learning (like your VirtualBox)
- Examples: VirtualBox, VMware Workstation, VMware Fusion, Parallels

```
[Physical Hardware]
      ↓
[Host OS — Ubuntu]   ← your normal OS
      ↓
[Type 2 Hypervisor]  ← VirtualBox
   ↙         ↘
[VM 1]      [VM 2]
```

| Feature | Type 1 (Bare Metal) | Type 2 (Hosted) |
|---|---|---|
| Runs on | Hardware directly | Host OS |
| Performance | Excellent | Good |
| Use case | Enterprise, cloud | Development, learning |
| Examples | ESXi, Hyper-V, KVM | VirtualBox, VMware Workstation |
| Cost | Usually expensive | VirtualBox is free |

---

#### Resource Requirements for Virtualization

**CPU — Processor Support:**
- Must have hardware virtualisation support enabled in BIOS
- **Intel VT-x** (Intel Virtualisation Technology)
- **AMD-V** (AMD Virtualisation)
- Without this: VMs run very slowly (software emulation only)
- Check on your system:
```bash
grep -E "vmx|svm" /proc/cpuinfo | head -3
# vmx = Intel VT-x enabled
# svm = AMD-V enabled
```

**Memory (RAM):**
- Each VM needs its own RAM allocation
- Host OS also needs RAM
- Rule: never allocate more than 50-70% of total RAM to VMs
- Example: 16GB system → max 8-10GB for all VMs combined
- Your system has 16GB → can comfortably run 1-2 VMs

**Disk Space:**
- Each VM needs disk space for its virtual hard disk
- Dynamic disks grow as needed, fixed disks pre-allocate all space
- Snapshots also consume disk space

**Network Requirements:**
- VMs can use: NAT, bridged, or host-only networking
- **NAT** — VM shares host's IP (most common, easiest)
- **Bridged** — VM gets its own IP on the network (acts like a real machine)
- **Host-only** — VM can only talk to host, no internet

---

#### Hypervisor Security

**VM Escaping:**
- The most serious VM security threat
- Attacker exploits a vulnerability in the **hypervisor** to break out of the VM
- From inside a VM, attacker gains access to the **host system or other VMs**
- Like a prisoner finding a secret tunnel out of a cell
- Real examples: VENOM (2015), BluePill

```
Normal:
[Attacker in VM 1] → cannot access [VM 2] or [Host]

VM Escape attack:
[Attacker in VM 1] → exploits hypervisor bug → [access to Host + all VMs]
```

- **Sweet spot for bad guys** — compromise one VM, potentially access everything on the hypervisor
- **Protection:** Keep hypervisor software updated, minimal attack surface, hardware-enforced isolation

**Guest OS Security:**
- Each VM guest OS must be secured independently
- Patching the host does not patch the VMs
- VMs can be snapshots of old vulnerable OS states
- **Cybersecurity use:** Stale VM snapshots running old unpatched OS = easy target

---

#### VDI — Virtual Desktop Infrastructure
- Also called **DaaS — Desktop as a Service**
- Users access a **full desktop environment running on a remote server** via thin client or browser
- The desktop VM runs in the data centre — user's device just displays it
- Benefits:
  - Centralised management — update one image, everyone gets updates
  - Data stays in the data centre — lost laptop = no data loss
  - Works on any device — thin client, old laptop, tablet
- Examples: VMware Horizon, Citrix Virtual Apps, Amazon WorkSpaces
- **Cybersecurity use:** VDI environments are high-value targets — compromising the VDI server compromises all users' desktops simultaneously

---

#### Application Containerization

**Container:**
- A **lightweight, isolated environment** for running a single application
- Contains the app + its dependencies + libraries — nothing else
- Shares the **host OS kernel** — does not need a full OS like a VM
- Much faster to start than a VM (milliseconds vs minutes)
- Much smaller than a VM (megabytes vs gigabytes)

**Containerization Software:**
- **Docker** — most popular container platform
- **Podman** — Docker alternative, rootless (more secure)
- **Kubernetes** — orchestrates many containers across many servers

---

#### Virtualized vs Containerized

| Feature | Virtual Machine | Container |
|---|---|---|
| Isolation | Complete — own OS kernel | Partial — shares host kernel |
| Size | Gigabytes | Megabytes |
| Startup time | Minutes | Milliseconds |
| Performance overhead | Higher | Very low |
| OS | Full guest OS | No OS — just app + libs |
| Security isolation | Stronger | Weaker (shared kernel) |
| Use case | Run different OS, legacy apps | Microservices, modern apps |
| Example | VirtualBox Ubuntu VM | Docker nginx container |

```
Virtual Machine:              Container:
┌─────────────┐               ┌────────┐ ┌────────┐
│  Guest OS   │               │ App A  │ │ App B  │
│  + App      │               │ + libs │ │ + libs │
├─────────────┤               ├────────┴─┴────────┤
│  Hypervisor │               │    Container       │
│             │               │    Runtime         │
├─────────────┤               ├────────────────────┤
│  Host OS    │               │      Host OS       │
├─────────────┤               ├────────────────────┤
│  Hardware   │               │      Hardware      │
└─────────────┘               └────────────────────┘
```

- **Cybersecurity use:** Container escape attacks — similar to VM escape but easier due to shared kernel. Docker misconfigurations are a common attack vector.

---

### 4.2 Cloud Models

#### What is Cloud Computing?
- **More than just a server hosted elsewhere**
- On-demand access to computing resources over the internet
- Pay for what you use — no upfront hardware investment
- Managed by the provider — you focus on your application

---

#### Cloud Deployment Models

**Public Cloud:**
- Resources available to **everyone over the internet**
- Owned and operated by cloud provider
- Shared infrastructure — your data on same physical hardware as others
- Examples: AWS, Microsoft Azure, Google Cloud, DigitalOcean
- Pros: no upfront cost, infinite scale, global availability
- Cons: less control, data sovereignty concerns, shared hardware
- **Cybersecurity use:** Public cloud misconfigurations (open S3 buckets, exposed APIs) are the most common cloud attack vector

**Private Cloud:**
- **Your own virtualised local data centre**
- All hardware is dedicated to your organisation
- Can be on-premises or hosted by a provider exclusively for you
- More control, better compliance for regulated industries
- Examples: on-premises VMware cluster, dedicated AWS GovCloud
- Pros: full control, better compliance, no noisy neighbours
- Cons: high upfront cost, you manage everything

**Hybrid Cloud:**
- **A mix of public and private cloud**
- Sensitive data stays in private cloud, scalable workloads go to public cloud
- Example: hospital keeps patient records on-premises, uses AWS for analytics
- "Cloud bursting" — use private cloud normally, burst to public cloud during peak demand
- **Cybersecurity use:** The connection between private and public cloud is a high-value attack target

**Community Cloud:**
- **Several organisations share the same resources**
- Organisations with similar requirements share infrastructure
- Example: government agencies sharing a cloud, universities sharing research computing
- Costs shared between organisations
- More control than public, cheaper than fully private

| Model | Who Uses It | Control | Cost |
|---|---|---|---|
| Public | Anyone | Low | Low (pay per use) |
| Private | One organisation | High | High (own hardware) |
| Hybrid | One org, mixed | Medium | Medium |
| Community | Multiple orgs | Medium | Shared |

---

#### IaaS — Infrastructure as a Service
- Also called **HaaS — Hardware as a Service**
- Provider gives you: **virtual servers, storage, networking**
- You manage: OS, applications, data, runtime
- You do NOT manage: physical hardware, data centre, power, cooling
- Example: you rent a virtual server on AWS EC2, install Ubuntu, run your app
- **Web service providers** are classic IaaS examples
- Other examples: AWS EC2, Azure VMs, Google Compute Engine, DigitalOcean Droplets
- **Cybersecurity use:** IaaS misconfigurations — open security groups, exposed management ports, public snapshots

---

#### SaaS — Software as a Service
- **On-demand software** delivered over the internet
- You manage: your data only
- Provider manages: everything else (hardware, OS, app, updates)
- Just open a browser and use it — no installation needed
- Examples: Gmail, Google Docs, Microsoft 365, Salesforce, Zoom, Dropbox
- **Cybersecurity use:** SaaS account takeover — stealing credentials gives attacker access to all data in the service

---

#### PaaS — Platform as a Service
- **No server, no software, no maintenance team, no HVAC** — provider handles all of that
- You handle: **the development and your application code only**
- Provider manages: hardware, OS, runtime, middleware, scaling

**Simple analogy to understand PaaS:**
```
IaaS = renting an empty plot of land → you build the house yourself
PaaS = renting a house with kitchen, plumbing, electricity already done
       → you just bring your furniture and live in it
SaaS = staying in a hotel → everything provided, just use it
```

**Real world example:**
- You write a web application in Python
- You push the code to Heroku (PaaS)
- Heroku automatically: provisions servers, installs Python, sets up database, handles scaling, manages SSL certificates
- You never touch a server
- Other examples: Heroku, Google App Engine, AWS Elastic Beanstalk, Azure App Service

---

#### Responsibility Matrix

| Responsibility | IaaS | PaaS | SaaS |
|---|---|---|---|
| Data | ✅ You | ✅ You | ✅ You |
| Application | ✅ You | ✅ You | ☁️ Provider |
| Runtime | ✅ You | ☁️ Provider | ☁️ Provider |
| Middleware | ✅ You | ☁️ Provider | ☁️ Provider |
| OS | ✅ You | ☁️ Provider | ☁️ Provider |
| Virtualisation | ☁️ Provider | ☁️ Provider | ☁️ Provider |
| Servers | ☁️ Provider | ☁️ Provider | ☁️ Provider |
| Storage | ☁️ Provider | ☁️ Provider | ☁️ Provider |
| Networking | ☁️ Provider | ☁️ Provider | ☁️ Provider |

> **Key insight:** In all cloud models, YOUR DATA is always your responsibility. The provider never takes responsibility for your data — read the SLA carefully.

---

### 4.2 Cloud Characteristics

#### Shared Resources

**Internal / Private Cloud:**
- **Dedicated resources** — hardware is yours only
- No "noisy neighbour" problem
- **No ongoing costs** after initial investment (just maintenance)
- Full control over resource allocation

**External / Public Cloud:**
- **Share resources** with other cloud customers (multitenancy)
- Your VM runs on the same physical server as someone else's VM
- Provider ensures isolation — but hardware is shared

---

#### Metered vs Non-Metered

**Metered Utilization:**
- Pay for **exactly what you use**
- Like a water meter — tracked per unit consumed
- CPU hours, GB of storage, GB of data transferred
- Example: AWS charges per hour for EC2 instances
- Pros: cost efficient if usage is unpredictable
- Cons: unexpected bills if usage spikes

**Non-Metered Utilization:**
- Pay for a **fixed block** regardless of actual usage
- Example: buy 100GB of storage — pay the same whether you use 1GB or 100GB
- Pros: predictable costs, no surprise bills
- Cons: paying for unused capacity

---

#### Cloud Computing Characteristics

**Elasticity:**
- Ability to **automatically scale resources up or down** based on demand
- Scale up during peak (Black Friday traffic spike) → scale down when quiet
- No human intervention needed — happens automatically
- Example: Netflix scales to thousands of servers during prime time, scales back at night
- **Cybersecurity use:** Attackers use cloud elasticity for massive distributed attacks — rent thousands of servers for hours, attack, delete evidence

**Availability:**
- Cloud providers guarantee **high uptime** via SLA (Service Level Agreement)
- Multiple data centres, redundant power, redundant networking
- **99.99% availability** = maximum 52 minutes downtime per year
- **99.999% (Five 9s)** = maximum 5 minutes downtime per year
- Achieved through geographic redundancy — if one data centre fails, another takes over
- **Cybersecurity use:** DDoS attacks target cloud availability — bring down services for legitimate users

**File Synchronization:**
- Files automatically synced across all devices and users in real time
- Change a file on your phone → instantly updated on your laptop
- Examples: Google Drive, OneDrive, Dropbox, iCloud
- **Cybersecurity use:** Ransomware can sync encrypted files to cloud, overwriting good backups — check if cloud sync has versioning/rollback

**Multitenancy:**
- Multiple customers (**tenants**) share the same physical infrastructure
- Each tenant's data is logically isolated from others
- The cloud provider ensures one tenant cannot access another's data
- Cost is shared across all tenants — makes cloud affordable
- **Cybersecurity use:** Side-channel attacks (like Spectre/Meltdown) can potentially leak data between tenants sharing the same physical CPU

---

## Terminal Practice + Expected Output

### Check Virtualisation Support
```bash
grep -E "vmx|svm" /proc/cpuinfo | head -3
```
**Expected output (Intel):**
```
flags: fpu vme de ... vmx ... — VT-x supported ✅
```

### Check VirtualBox Version
```bash
virtualbox --version
```
**Expected output:**
```
7.0.14r161095
```

### Check System Resources Available for VMs
```bash
free -h
```
**Expected output:**
```
               total    used    free    available
Mem:            15Gi    4.2Gi   7.1Gi   10.5Gi
```
- `available: 10.5Gi` → you can safely allocate 4-6GB to a VM

```bash
lscpu | grep -E "CPU\(s\)|Core|Thread|Virtualisation"
```
**Expected output:**
```
CPU(s):                  8
Core(s) per socket:      4
Thread(s) per core:      2
Virtualisation:          VT-x
```
- 8 logical CPUs → can allocate 2-4 vCPUs to a VM comfortably

---

## 🔑 Additional Important Concepts You Missed

### Snapshot
- A **point-in-time copy** of a VM's entire state
- Can revert to snapshot if something goes wrong
- Like an undo button for an entire VM
- **Cybersecurity use:** Snapshots used in malware analysis — take snapshot before running malware, revert after. Also a risk — old snapshots may contain sensitive data

### VM Templates
- A master VM image used to create new VMs quickly
- Deploy 50 identical VMs in minutes from one template
- Used in cloud auto-scaling and VDI deployments

### Live Migration
- Move a running VM from one physical host to another **without downtime**
- VM keeps running while being transferred
- Used for: maintenance, load balancing, hardware failure
- VMware calls it **vMotion**
- **Cybersecurity use:** Live migration traffic over the network can be intercepted if not encrypted

### Serverless Computing
- Beyond PaaS — you only write individual **functions**, not full applications
- Provider runs function only when triggered — charges per execution (milliseconds)
- No servers to manage at all
- Examples: AWS Lambda, Azure Functions, Google Cloud Functions
- **Cybersecurity use:** Serverless function injection — attacker exploits poorly secured serverless functions to run malicious code in the cloud environment

### Cloud Security Shared Responsibility Model
- **Provider is responsible for:** security OF the cloud (hardware, hypervisor, physical)
- **Customer is responsible for:** security IN the cloud (data, access management, configuration)
- Most cloud breaches are customer misconfigurations — not provider failures
- Example: leaving an S3 bucket publicly readable = customer's fault, not AWS's

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. Type 1 hypervisor runs directly on hardware (ESXi, KVM) — Type 2 runs on a host OS (VirtualBox) — you use Type 2 daily
2. PaaS means you only write code — provider handles everything else including servers, OS, scaling, and SSL
3. Multitenancy means you share physical hardware with strangers in public cloud — Spectre/Meltdown showed this can leak data between tenants
