# CompTIA A+ 220-1202 — Week 4 Day 2 Notes
## FINAL DAY OF CORE 2! 🎉

---

## Videos Watched
- ✅ 4.5 Environmental Impacts
- ✅ 4.6 Incident Response
- ✅ 4.6 Privacy, Licensing, and Policies
- ✅ 4.7 Professionalism
- ✅ 4.7 Communication
- ✅ 4.8 Scripting Languages
- ✅ 4.8 Scripting Use Cases
- ✅ 4.9 Remote Access
- ✅ 4.10 Managing AI

---

## Key Concepts

### 4.5 Environmental Impacts

#### SDS / MSDS — Safety Data Sheet
- **SDS** (Safety Data Sheet) — current term
- **MSDS** (Material Safety Data Sheet) — older term, same thing
- Provides information for all **hazardous chemicals** used in the workplace
- Required by law — must be accessible to all employees

#### What an SDS Contains
1. **Product identification** — chemical name, manufacturer, contact info
2. **Hazard identification** — danger warnings, signal words (Danger/Warning)
3. **Composition** — what the chemical is made of
4. **First aid measures** — what to do if exposed
5. **Fire-fighting measures** — how to extinguish, protective equipment needed
6. **Accidental release** — spill cleanup procedures
7. **Handling and storage** — safe use and storage conditions
8. **Exposure controls / PPE** — ventilation, gloves, goggles needed
9. **Physical and chemical properties** — appearance, smell, flash point
10. **Stability and reactivity** — conditions to avoid, incompatible materials
11. **Toxicological information** — health effects of exposure
12. **Ecological information** — environmental impact
13. **Disposal considerations** — how to dispose safely and legally
14. **Transport information** — shipping regulations
15. **Regulatory information** — laws governing the substance
16. **Other information** — revision dates

---

#### Handling Toxic Waste

**Batteries:**
- Lithium, NiMH, NiCd batteries — must NOT go in regular rubbish
- Contain: lead, cadmium, lithium, mercury — toxic and fire hazard
- Recycle at designated battery recycling points
- Swollen lithium batteries — handle carefully, do not puncture, take to hazardous waste

**Toner:**
- Fine particles — potential carcinogen if inhaled
- Never use regular vacuum — use toner-specific vacuum
- Return used cartridges to manufacturer recycling programs
- Toner spills — damp cloth, do not breathe particles

**Other Devices and Assets:**
- **CRT monitors** — contain lead and barium — hazardous waste disposal required
- **Circuit boards** — contain lead solder, heavy metals
- **Fluorescent bulbs** — contain mercury — special disposal
- **Ink cartridges** — recycle through manufacturer
- **Mobile phones** — contain rare earth metals — electronics recycler
- **Hard drives** — must be securely wiped or shredded before disposal

---

#### Room Controls for IT Equipment

**Temperature:**
- Servers and networking equipment generate significant heat
- Ideal temperature: **18-27°C** (64-80°F)
- Overheating causes: throttling, crashes, premature hardware failure
- Hot/cold aisle containment — cold air in front, hot air expelled from back

**Humidity Level:**
- Too low (<40%) → ESD risk increases significantly
- Too high (>60%) → condensation risk, corrosion
- Ideal: **40-60% relative humidity**
- Data centres use precision cooling to maintain both temperature and humidity

**Proper Ventilation:**
- Adequate airflow prevents heat buildup
- Cable management — blocked airflow is as bad as no cooling
- Positive pressure rooms — more air in than out — keeps dust out

---

#### UPS — Uninterruptible Power Supply

**What is a UPS?**
- **Battery backup** that provides power during outages
- Gives time to: save work and shut down gracefully, or keep systems running
- Protects against: power outages, voltage sags, voltage spikes

**UPS Types:**

**Standby UPS (Offline UPS):**
- Normally passes utility power directly to devices
- Switches to battery when power fails — small delay (~20ms)
- Cheapest option — home use
- Basic protection

**Line-Interactive UPS:**
- Has voltage regulator — corrects minor voltage fluctuations without switching to battery
- Faster switchover than standby
- Better protection — good for small business
- Most common type for IT equipment

**Online UPS (Double-Conversion):**
- Always running on battery — continuously converts AC to DC to AC
- **Zero switchover time** — no delay when power fails
- Best protection — constant clean power
- Expensive — used in data centres and critical equipment
- Also conditions power — removes all noise and fluctuations

| Type | Switchover | Protection | Cost | Use |
|---|---|---|---|---|
| Standby | ~20ms | Basic | Low | Home |
| Line-Interactive | ~4ms | Good | Medium | Small business |
| Online | 0ms | Best | High | Data centre |

**UPS Features:**
- **Auto shutdown** — software signals computers to shut down gracefully before battery depletes
- **Battery capacity** — measured in VA (volt-amps) or watts — determines how long it can run
- **Outlets** — some outlets battery-backed, some surge-only
- **LCD display** — shows battery level, load, runtime remaining
- **USB/network port** — for auto shutdown software connection

---

#### Surge Suppressor

**What is a Surge Suppressor?**
- Not all power from the wall is clean — voltage spikes occur
- **Spikes diverted to ground** — protects connected devices
- **Noise filters remove line noise** — electrical interference from motors, appliances

**Surge Suppressor Specs to Know:**
- **Joule rating** — how much energy the suppressor can absorb before failing
  - Higher joules = better protection (look for 600+ joules minimum)
  - Once joule capacity is used up — suppressor no longer protects (replace it!)
- **Surge amp rating** — maximum surge current it can handle
- **UL 1449 Voltage Protection Rating (VPR)** — industry standard rating
  - Lower VPR = better — means lower voltage gets through to devices
  - Look for UL 1449 certification — tested and verified
- **Not the same as UPS** — surge suppressor provides NO battery backup

---

### 4.6 Incident Response

#### Chain of Custody
- **Control of evidence** from collection to courtroom
- Documents **everyone who contacts the evidence** — when, why, what they did
- **Label and catalogue everything** — every piece of evidence tagged and recorded
- Broken chain of custody = evidence may be inadmissible in court
- **Cybersecurity use:** Digital forensics requires chain of custody — without it, evidence cannot be used in legal proceedings

#### Incident Response — First Response Steps
1. **Identify the issue** — what happened? What systems are affected?
2. **Report to proper channels** — security team, management, legal if required
3. **Collect and protect evidence related to event** — do not alter, do not turn off systems without guidance
   - Live forensics — capture RAM and network state before shutdown
   - Preserve logs — event logs, firewall logs, web server logs

#### Incident Response — Copy of Drive
- **Bit-for-bit, byte-for-byte copy** of entire disk — exact forensic image
- Remove the physical drive — work on copy only, never original
- **Software imaging tools:** FTK Imager, dd (Linux), Autopsy
- **Use hashes for data integrity:**
  - Calculate MD5/SHA-256 hash of original drive
  - Calculate hash of copy — must match exactly
  - Any difference = copy is not forensically sound
```bash
# Linux forensic copy command
sudo dd if=/dev/sda of=/mnt/evidence/disk.img bs=4M
# Hash verification
md5sum /dev/sda
md5sum /mnt/evidence/disk.img
# Both hashes must be identical
```

#### Incident Response Documentation
- **Summary information** — what happened at a high level
- **Detailed explanation of data acquisition** — how evidence was collected
- **The findings** — what was discovered during analysis
- **Conclusion** — what caused the incident, recommendations

#### Order of Volatility
> Data that disappears fastest should be collected first

| Order | Data Type | How Long it Lasts |
|---|---|---|
| 1 | **CPU registers and cache** | Milliseconds |
| 2 | **RAM / memory** | Seconds to minutes |
| 3 | **Network state / connections** | Minutes |
| 4 | **Running processes** | Until reboot |
| 5 | **Disk / storage** | Until overwritten |
| 6 | **Remote logging / monitoring data** | Until log rotation |
| 7 | **Physical configuration / network topology** | Long term |
| 8 | **Archival media / backups** | Very long term |

**Exam tip:** Most volatile = collect first. RAM (order 2) is critical — contains: encryption keys, passwords, running malware code, network connections. Always capture RAM before shutting down a compromised system.

---

### 4.6 Privacy, Licensing, and Policies

#### Software Licenses

**Personal License:**
- For individual use only — one user, typically one or two devices
- Cannot install on multiple computers
- Example: Microsoft 365 Personal

**Corporate Use License:**
- For business use — covers multiple users/devices
- Volume licensing — buy in bulk, cheaper per seat
- Example: Microsoft 365 Business

**Open Source License (FOSS):**
- **Free and Open Source Software** — source code is publicly available
- Anyone can view, modify, and distribute
- Examples: Linux, Firefox, LibreOffice, VLC
- Types of open source licenses:
  - **GPL** (GNU General Public License) — must share modifications
  - **MIT** — very permissive, minimal restrictions
  - **Apache 2.0** — permissive, patent protection included

**Closed Source / Commercial:**
- Source code not available — proprietary
- Must purchase licence to use
- Example: Microsoft Windows, Adobe Photoshop

**EULA — End User Licence Agreement:**
- Legal agreement between software vendor and user
- Defines permitted use — what you can and cannot do
- Agreed to during installation (click "I Agree")
- **Cybersecurity use:** Violating EULA can result in legal action — using software beyond licence scope

---

#### NDA — Non-Disclosure Agreement
- **Confidentiality agreement between parties**
- Protects confidential information from being shared with third parties
- Types:
  - **Unilateral** — one party agrees to keep other's information confidential
  - **Bilateral** — both parties agree to keep each other's information confidential
  - **Multilateral** — three or more parties, all agree to confidentiality
- Common in: employment (employee NDA), vendor relationships, mergers
- **Cybersecurity use:** IT staff often sign NDAs — access to sensitive systems requires confidentiality obligation

---

#### PCI DSS — Payment Card Industry Data Security Standard
- **Regulates how credit card data is stored, processed, and transmitted**
- Required for any organisation that accepts card payments
- Six control objectives:

| Objective | Requirements |
|---|---|
| **1. Build and maintain secure network** | Install firewall, don't use vendor default passwords |
| **2. Protect cardholder data** | Protect stored data, encrypt transmission |
| **3. Maintain vulnerability management** | Use antivirus, develop secure systems |
| **4. Implement strong access control** | Restrict access by need, unique IDs, physical access controls |
| **5. Monitor and test networks** | Track all access, regularly test security |
| **6. Maintain information security policy** | Policy that addresses information security |

- Non-compliance = fines, loss of ability to process card payments
- **Cybersecurity use:** PCI DSS compliance is a minimum baseline — breaches still occur in compliant organisations

---

#### Personal Government-Issued Information
- Used for government services and documents: passport, driving licence, national ID, tax ID (PAN in Nepal)
- May be restrictions on collecting or storing government-issued information
- Extra care required — identity theft uses this information
- **Cybersecurity use:** Government ID data is highly sensitive — treat with maximum protection

#### PII — Personally Identifiable Information
- **Any data that can identify an individual**
- Examples: name, address, email, phone, date of birth, national ID, IP address, biometrics
- Not everyone realises the importance of this data
- Must be protected under various privacy laws (GDPR in Europe, various national laws)
- **Cybersecurity use:** PII breach requires notification to affected individuals and regulators — fines can be enormous (GDPR up to 4% of global revenue)

#### PHI — Protected Health Information
- **Health information associated with an individual**
- Includes: medical records, diagnoses, prescriptions, insurance information
- Shared between: doctors, hospitals, insurance companies, pharmacies
- **HIPAA — Health Insurance Portability and Accountability Act (1996):**
  - US law protecting PHI
  - Requires: safeguards for PHI, breach notification, patient rights to their data
  - Violation penalties: up to $1.9 million per violation category per year
- **Cybersecurity use:** Healthcare is the most targeted industry for data breaches — PHI is worth 10x more than credit card data on dark web

---

#### Data Retention Requirements
- Keep files that change frequently for **version control** — access previous versions
- Recover from virus infection — restore clean version of files
- Often **legal requirements for data retention:**
  - Financial records: 7 years (varies by country)
  - Medical records: 7-10 years minimum
  - Email: 3-7 years for regulated industries
  - CCTV: 31 days typical (longer for incidents)
- **Cybersecurity use:** Forensic investigations need logs — if logs deleted too soon, evidence lost

#### AUP — Acceptable Use Policy
- Defines **what is acceptable use of company assets** — computers, network, email, internet
- Covers: personal use limits, prohibited websites, software installation rules, data handling
- Used by organisation to **limit legal liability** — if employee violates policy, company not responsible
- Signed by all employees — usually during onboarding
- **Cybersecurity use:** AUP is the legal foundation for disciplinary action against policy violations

#### Splash Screens
- Message, logo, or graphics shown **during startup or login**
- IT departments use login splash screens to display: AUP reminder, legal warnings, "authorised users only" notices
- **Cybersecurity use:** Login warning banners are legally important — without them, prosecution of unauthorised access is more difficult in some jurisdictions

---

### 4.7 Professionalism

#### Professional Appearance
- **Match the attire of the current environment**
  - Formal environments — business formal
  - Tech company — business casual
  - Field work — practical but neat
- Find the right balance — represent your organisation professionally
- First impressions matter — appearance affects trust

#### Avoid Being Judgemental
- **Cultural sensitivity** — different backgrounds, different ways of working
- **You are the teacher** — users come to you for help, not judgement
- Make people smarter — educate, don't belittle
- You will make mistakes — own them, learn from them
- Never mock users for not knowing technical things

#### Be On Time and Avoid Distractions
- Punctuality shows respect for the user's time
- **Do not allow interruptions** during support calls
- Apologise for delays and unintended distractions
- Put phone away — do not check messages during support sessions
- Create an environment for focused conversation

#### Difficult Situations
- Technical problems are stressful for users — be patient
- **Do not argue or be defensive** — even when user is wrong
- **Diffuse difficult situations** with listening and questions
- Ask clarifying questions — reframe the conversation
- Communicate status clearly — explain what you're doing
- **Never take the situation to social media** — never complain about users online
- Escalate if necessary — some situations need management involvement

#### Maintain Confidentiality
- **Privacy concerns and professional responsibilities**
- Never share customer/user data with unauthorised parties
- Do not discuss support cases outside of work context
- **Personal respect** — treat all information shared with you as confidential

---

### 4.7 Communication

#### Avoid Jargon
- Avoid **abbreviations, TLAs (Three-Letter Acronyms)**, and technical slang
- Communicate in terms **everyone can understand**
- If you must use technical terms — explain them simply
- Example: say "the device that connects your home to the internet" not "the router/gateway"

#### Maintain a Positive Attitude
- **Positive tone of voice** — even when dealing with frustrating situations
- Problems cannot always be fixed immediately — manage expectations kindly
- "I understand this is frustrating — let me help you find the best solution"
- Positivity is contagious — it changes the dynamic of difficult interactions

#### Avoid Interrupting
- Let the user finish speaking — even if you already know the answer
- **Why we interrupt:** excitement about having the answer, time pressure
- **Actively listen** — take notes, make eye contact
- Interrupting makes users feel unheard — they may withhold important information

#### Clarify Customer Statements
- **Ask pertinent questions** — gather complete information
- **Repeat your understanding** of the problem back to the customer — confirm you understood
- Keep an open mind — your first assumption may be wrong
- "Let me make sure I understand — you're saying that X happens when you do Y, is that correct?"

#### Setting Expectations
- Offer different options — repair vs replace vs workaround
- Give realistic timelines — do not overpromise
- **Under-promise and over-deliver** — better to finish early than be late
- If you cannot fix it — explain why and what alternatives exist
- Follow up — confirm the issue is resolved after the fact

---

### 4.8 Scripting Languages

#### Why Scripting?
- **Automate tasks** — save time, reduce human error
- May be specific to a task or operating system
- Small scripts can replace hours of manual work

#### Scripting Languages to Know

| Language | Extension | Use Case | OS |
|---|---|---|---|
| **Batch files** | `.bat` | Automate Windows CMD tasks | Windows |
| **PowerShell** | `.ps1` | Windows system administration | Windows/Linux/Mac |
| **VBScript** | `.vbs` | Legacy Windows automation | Windows |
| **Shell Script** | `.sh` | Linux/macOS automation | Linux/macOS |
| **JavaScript** | `.js` | Web interactivity, Node.js | Any (browser/server) |
| **Python** | `.py` | General purpose, cross-platform | Any |

**Important:** JavaScript is NOT Java — completely different languages despite similar name

#### PowerShell Detail
- **Command line interface for system administrators**
- Object-based — passes objects between commands, not just text
- Runs on Windows, Linux, and macOS (PowerShell Core)
- Used for: Active Directory management, Azure management, automation
- **Cybersecurity use:** Most Windows malware and pentesting tools use PowerShell — AMSI monitors it

---

### 4.8 Scripting Use Cases

#### Basic Automation
- Automate mundane repetitive tasks — same thing every day
- The need for speed — scripts run in seconds, manual takes hours
- Reduces human error — script does it the same way every time

#### Restarting Machines
- Script to restart machines on schedule
- Common uses: applying updates, clearing memory leaks, troubleshooting
- Can target specific computers or all computers in a group
- Example Windows: `shutdown /r /t 0 /m \\computername`

#### Remapping Network Drives
- Shared network drives mapped at startup automatically
- Common task during user login — logon scripts
- Automate software changes — update drive letters across organisation
- Add or move user data locations without user intervention

#### Application Installations
- Install applications automatically — no user interaction needed
- Many applications support silent install: `setup.exe /S /quiet`
- On-demand or automatic — triggered by event or schedule
- Used in: enterprise deployment, new employee setup, mass rollout

#### Automated Backups
- Usually performed **at night or during off-hours** — minimal impact on users
- Time-consuming — automate so it happens without human action
- Script: identifies changed files, copies to backup location, logs result, sends report

#### Information Gathering
- Get specific information from **remote devices** without visiting them
- Performance monitoring — CPU, RAM, disk usage across all machines
- Inventory management — list all software installed on all computers
- Security and vulnerability checks — scan for missing patches, weak passwords

#### Initiating Updates
- Nothing stays the same — OS, drivers, applications all need updates
- Script checks for updates, downloads, installs, reboots if needed
- Can be scheduled — run at 2am when users are not working

#### Scripting Security Considerations
- **Unintentionally introducing malware** — script downloaded from internet may contain malicious code
- **Inadvertently changing system settings** — one wrong line can affect all targeted systems
- **Browser or system crashes** — poorly tested scripts cause instability
- **Best practices:**
  - Test in sandbox before production
  - Code review — have another person check the script
  - Use version control (Git) for scripts
  - Sign scripts with digital signature — PowerShell execution policies
  - **Cybersecurity use:** Malicious PowerShell scripts are the most common malware delivery method on Windows — execution policy and script signing help mitigate

---

### 4.9 Remote Access

#### Remote Desktop Connections
- **Share a desktop from a remote location** — see and control another computer's screen
- Common uses: technical support, remote work, server management

**RDP — Microsoft Remote Desktop Protocol:**
- Microsoft's proprietary remote desktop protocol
- **Port TCP 3389**
- Full graphical desktop of remote Windows machine
- Available in Windows Pro and above (not Home)
- Client: Remote Desktop Connection (`mstsc.exe`)
- **Cybersecurity use:** RDP is the most attacked service on the internet — exposed RDP on port 3389 = constant brute force. Use VPN instead of exposing RDP directly.

**VNC — Virtual Network Computing:**
- Cross-platform remote desktop — Windows, Linux, macOS
- Open standard — many implementations (TightVNC, RealVNC, UltraVNC)
- Commonly used for technical support
- Less secure than RDP by default — encryption varies by implementation
- **Cybersecurity use:** Many VNC installations use weak or no passwords — frequently exploited

#### Remote Desktop Security
- **Microsoft Remote Desktop Services (RDS):**
  - Server-side component that enables RDP connections
  - Manages multiple simultaneous RDP sessions
  - Includes: Session Host (multiple users), Gateway (secure external access), Broker (load balancing)
  - **RD Gateway** — allows RDP over HTTPS (port 443) — no need to expose 3389 publicly
  - **Network Level Authentication (NLA)** — authenticate before desktop loads — reduces attack surface
  - **Always enable NLA** — prevents unauthenticated connection attempts
- **Cybersecurity use:** BlueKeep (CVE-2019-0708) — critical RDP vulnerability allowing remote code execution without authentication — patched but unpatched systems still exist

---

#### VPNs (Remote Access Context)

**VPN Concentrator:**
- Handles VPN connections from many remote users
- Often **integrated into firewall**
- Manages: authentication, encryption, IP assignment, session management

**Many Deployment Options:**
- Hardware VPN appliance (Cisco ASA, Palo Alto)
- Software VPN server (OpenVPN, WireGuard)
- Cloud-based VPN (Azure VPN Gateway, AWS VPN)
- Used with **client software** installed on user's device

**Client-to-Site VPN:**
- **On-demand access from a remote device**
- User connects when needed — not always-on
- Good for: remote workers, travelling employees

#### VPN Security
- VPN data on the network is **very secure** — encrypted tunnel
- **Authentication is critical** — weak VPN auth = easy entry point
- **MFA always included** for enterprise VPN — password alone not sufficient
- **Split tunnelling** — only company traffic through VPN, personal traffic goes direct — risk vs performance trade-off
- **Cybersecurity use:** VPN credentials are prime targets — credential stuffing and phishing attacks against VPN login pages are extremely common

---

#### SSH — Secure Shell

**What is SSH?**
- **Encrypted console communication** — command line access to remote systems
- **Port TCP 22**
- Looks and acts the same as Telnet but with encryption
- Telnet (port 23) = same functionality but **no encryption** — never use Telnet

**SSH Security:**
- Network traffic is **fully encrypted** — cannot be intercepted
- **Authentication is the concern:**
  - Password authentication — brute force risk
  - **Key-based authentication** — more secure, recommended
- **Certain accounts should be disabled in SSH:**
  - Disable root login: `PermitRootLogin no` in `/etc/ssh/sshd_config`
  - Disable password auth: `PasswordAuthentication no` (use keys only)
  - Whitelist specific users: `AllowUsers username`
- **Cybersecurity use:** SSH port 22 is constantly probed by bots. Change to non-standard port, use key auth only, use fail2ban to block repeated failures.

---

#### RMM — Remote Monitoring and Management

**What is RMM?**
- Used by **MSP (Managed Service Providers)** to manage client systems remotely
- Provides centralised management of many client devices

**RMM Features:**
- **Remote monitoring** — CPU, RAM, disk, network alerts in real time
- **Patch management** — deploy Windows/app updates to all managed devices
- **Remote control** — access any device without user involvement
- **Antivirus management** — deploy, monitor, and manage AV across all devices
- **Scripting** — run scripts on any managed device remotely
- **Asset inventory** — automatic hardware and software inventory
- **Alerting** — email/SMS alerts for hardware failure, security events
- **Reporting** — generate reports for clients on system health

**RMM Security:**
- **A popular attack point** — attackers target MSPs to reach all their clients simultaneously
- Access should be **limited** — MFA required, least privilege
- **Auditing is important** — log every action taken through RMM
- **Cybersecurity use:** Kaseya VSA attack (2021) — RMM software compromised → ransomware pushed to 1,500 businesses through single MSP attack

---

#### SPICE — Simple Protocol for Independent Computing Environments
- Helps **manage virtual machines** — remote display protocol for VMs
- Developed by Red Hat — used in KVM virtualisation
- Feels like other remote desktops but optimised for virtual machines
- Supports: audio, video, USB redirection, clipboard sharing
- Used in: enterprise VM management, virtual desktop infrastructure

#### Windows Remote Management (WinRM)
- Microsoft's implementation of **WS-Management protocol**
- Allows remote management of Windows systems via command line
- Enables **PowerShell remoting** — run PowerShell commands on remote computers
- **Port 5985** (HTTP) or **5986** (HTTPS)
- Used by: System Centre Configuration Manager, Azure automation, PowerShell scripts
- Enable with: `winrm quickconfig`
- Remote PowerShell: `Enter-PSSession -ComputerName servername`
- **Cybersecurity use:** WinRM is used by attackers for lateral movement after initial compromise — PowerShell remoting across the network. Restrict with firewall rules — only allow from management servers.

---

### 4.10 Managing AI

#### What is AI?
- **Artificial Intelligence** — technology designed to meet or exceed human intelligence in specific tasks
- Machine Learning (ML) — AI that learns from data without explicit programming
- Deep Learning — ML using neural networks with many layers
- Generative AI — creates new content (text, images, code) — ChatGPT, Claude, DALL-E

#### Application Integration
- AI integrated into everyday applications:
  - **Email** — spam filtering, smart reply suggestions, phishing detection
  - **Security tools** — anomaly detection, threat intelligence, log analysis
  - **Help desk** — AI chatbots handle tier 1 support automatically
  - **Search** — AI improves search relevance and understanding
  - **Code** — GitHub Copilot suggests code, finds bugs
  - **Productivity** — Microsoft Copilot in Word/Excel/Teams
  - **Voice assistants** — Siri, Cortana, Google Assistant
  - **Image recognition** — face recognition, barcode scanning

#### Appropriate AI Use
- **Process large data repositories** — AI analyses millions of logs to find anomalies humans would miss
- **Automation** — repetitive tasks performed by AI faster and more consistently
- **Healthcare** — diagnose conditions from medical images, drug discovery, patient monitoring
- **Communication** — translation, transcription, accessibility features
- **Security** — threat detection, vulnerability scanning, SIEM analysis
- **Customer service** — 24/7 chatbot support for common questions

#### Inappropriate AI Use
- **Fraud** — AI-generated deepfakes for identity fraud, voice cloning for vishing
- **Unethical shortcuts** — using AI to bypass required human review processes
- **Plagiarism** — submitting AI-generated work as your own without disclosure
- **AI bias** — AI trained on biased data produces biased results — discrimination in hiring, lending, criminal justice
- **Surveillance** — mass surveillance, tracking individuals without consent
- **Misinformation** — AI-generated fake news, fake images, propaganda

#### AI Hallucinations
- AI **misinterpretation of data** — generates confident but incorrect answers
- AI presents false information as fact — no uncertainty expressed
- Examples: invented citations, wrong dates, fabricated statistics, incorrect code
- Occurs because: AI predicts likely next words/tokens, not verifiable facts
- **Cybersecurity use:** Attackers use AI hallucinations to generate convincing fake documentation, fake security advisories

#### AI Accuracy
- AI is not always correct — must verify important outputs
- Accuracy depends on: training data quality, model design, task type
- Better for: pattern recognition, summarisation, creative tasks
- Less reliable for: specific facts, recent events, calculations, legal/medical advice
- Always verify AI outputs against authoritative sources for critical decisions

#### Private vs Public AI

**Public AI:**
- Cloud-based — data sent to provider's servers for processing
- Examples: ChatGPT (OpenAI), Claude (Anthropic), Gemini (Google)
- **Data privacy concern** — input data may be used for training
- Do NOT enter: passwords, PII, PHI, trade secrets, confidential business data
- Convenient — no infrastructure needed

**Private AI:**
- Runs on organisation's own infrastructure — data never leaves
- Examples: locally hosted Llama, private Azure OpenAI deployment
- More expensive — requires hardware and maintenance
- Better for: sensitive data, regulated industries, confidential business use
- **Cybersecurity use:** Use private AI for security-sensitive tasks — threat intelligence analysis, log review with sensitive data

---

## 🔑 Exam Focus Summary

**Environmental:**
- SDS/MSDS — 16 sections, required for all hazardous chemicals
- UPS types: Standby (20ms), Line-Interactive (4ms), Online (0ms)
- Joule rating = energy absorption capacity of surge suppressor
- Batteries, CRTs, fluorescent bulbs — special disposal required

**Incident Response:**
- Chain of custody — document everyone who touches evidence
- Order of volatility — CPU cache → RAM → network → disk → backups
- Forensic copy = bit-for-bit with hash verification
- Collect most volatile data first

**Licensing:**
- EULA — agreement accepted during installation
- NDA — unilateral/bilateral/multilateral
- PCI DSS — 6 objectives for card data protection
- PII — any data identifying an individual
- PHI — health information protected by HIPAA

**Scripting:**
- .bat = Batch (Windows CMD)
- .ps1 = PowerShell
- .sh = Shell script (Linux)
- .py = Python
- .js = JavaScript (NOT Java)
- .vbs = VBScript

**Remote Access:**
- RDP = port 3389 — Microsoft remote desktop
- VNC = cross-platform remote desktop
- SSH = port 22 — encrypted, Telnet = port 23 — unencrypted
- WinRM = port 5985/5986 — PowerShell remoting
- NLA = Network Level Authentication — enable for RDP security

**AI:**
- Hallucinations = confident but incorrect AI outputs
- Public AI = data sent to cloud — do not enter sensitive data
- Private AI = runs locally — safe for sensitive data

---

## ⭐ PHASE 1 COMPLETE — What To Do Now

### Immediate Tasks:
1. **Take Core 2 practice exam** — ExamPremium or ExamCompass
2. **Take Core 1 practice exam** — refresh before moving on
3. **Target score: 80%+** on both before Phase 2
4. **Apply for Coursera Financial Aid** — Google IT Support Certificate
5. **Enroll Cisco IT Essentials** — check if local academy available

### Push all notes to GitHub:
```bash
cd ~/Documents/Labs
git add .
git commit -m "Phase 1 complete - Week 4 Day 2 final notes"
git push
```

### Phase 2 Begins Next:
- Jeremy's IT Lab — full free CCNA course on YouTube
- Cisco Packet Tracer — download from NetAcad (free)
- Wireshark — already on Ubuntu or install: `sudo apt install wireshark -y`

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. Order of volatility — CPU cache and RAM are most volatile — must be captured first in forensic investigation — RAM contains encryption keys, passwords, and running malware code that disappears on reboot
2. RMM tools are the highest-value target for attackers targeting MSPs — Kaseya attack reached 1,500 businesses through one MSP compromise — MFA and auditing on RMM is critical
3. Public AI should never receive PII, PHI, passwords, or confidential data — it may be used for training — use private/local AI for sensitive security work