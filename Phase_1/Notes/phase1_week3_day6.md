# CompTIA A+ 220-1202 — Week 3 Day 6 Notes

---

## Videos Watched
- ✅ 2.4 Malware
- ✅ 2.4 Anti-malware Tools
- ✅ 2.5 Social Engineering
- ✅ 2.5 Denial of Service
- ✅ 2.5 On-Path Attacks
- ✅ 2.5 Zero-Day Attacks
- ✅ 2.5 Password Attacks
- ✅ 2.5 Insider Threats
- ✅ 2.5 SQL Injection Attacks
- ✅ 2.5 Cross-Site Scripting
- ✅ 2.5 Business Email Compromise
- ✅ 2.5 Supply Chain Attacks
- ✅ 2.5 Security Vulnerabilities

---

## Key Concepts

### 2.4 Malware

#### What is Malware?
- **Malicious Software** — any software designed to harm, exploit, or gain unauthorised access
- Delivered via: email attachments, malicious downloads, infected USB drives, compromised websites, network exploits
- Goal: steal data, encrypt files for ransom, spy on user, use resources for attacks, create backdoors

---

#### Types of Malware — Must Know All for Exam

**Virus:**
- Attaches itself to a legitimate file or program
- **Requires human action to spread** — user must run the infected file
- Replicates by infecting other files on the same system
- Types: file virus, boot sector virus, macro virus (in Office documents)
- **Cybersecurity use:** Macro viruses in Word/Excel documents are still extremely common — disable macros by default

**Worm:**
- **Self-replicating** — spreads automatically without human action
- Exploits network vulnerabilities to spread to other computers
- Does not need to attach to a file — standalone program
- Famous examples: WannaCry, Code Red, ILOVEYOU, Slammer
- **Cybersecurity use:** Worms spread exponentially — one infected machine infects thousands in minutes. WannaCry infected 230,000 computers in one day.

**Trojan Horse:**
- Disguises itself as legitimate, useful software
- User installs thinking it's helpful — malware hidden inside
- Does NOT self-replicate — relies on user installing it
- Common disguises: fake antivirus, game cracks, free software, video codecs
- **Cybersecurity use:** RAT (Remote Access Trojan) — gives attacker full remote control of infected system

**Ransomware:**
- Encrypts victim's files — demands payment for decryption key
- Modern ransomware also **exfiltrates data** before encrypting — double extortion
- Payment demanded in cryptocurrency (Bitcoin, Monero)
- Famous examples: WannaCry, REvil, LockBit, Conti, DarkSide (Colonial Pipeline)
- **Cybersecurity use:** No guarantee decryption key provided after payment. Best defence is offline backups. Average ransom payment: $1.5 million (2023).

**Spyware:**
- Secretly monitors user activity and sends data to attacker
- Collects: keystrokes, screenshots, webcam footage, browsing history, credentials
- Often installed bundled with free software
- **Keylogger** — specific type that records every keystroke
- **Cybersecurity use:** Spyware is often invisible to user — runs silently in background

**Adware:**
- Displays unwanted advertisements
- Often bundled with free software (PUP — Potentially Unwanted Program)
- Less malicious than other malware but annoying and privacy-invasive
- Can redirect browser searches, inject ads into websites
- **Cybersecurity use:** Adware often comes with spyware — treat as potentially dangerous

**Rootkit:**
- Hides its presence on the system — modifies OS to conceal malware
- Can hide: files, processes, network connections, registry entries
- Operates at kernel level — very hard to detect
- Survives reboots — often modifies boot process
- **Types:** Kernel rootkit (in OS kernel), bootkit (in MBR/UEFI), firmware rootkit (in device firmware)
- **Cybersecurity use:** Rootkits are the hardest malware to remove — often requires OS reinstall or offline scan. Firmware rootkits survive OS reinstall.

**Backdoor:**
- Hidden access point into a system bypassing normal authentication
- Allows attacker to return later without exploiting vulnerability again
- Often installed by other malware after initial compromise
- Can be in software, firmware, or hardware
- **Cybersecurity use:** After removing visible malware, always look for backdoors — attacker may have multiple persistence mechanisms

**Botnet:**
- Network of infected computers (**bots/zombies**) controlled by attacker
- **Command and Control (C2/C&C) server** — attacker sends commands to all bots
- Uses: DDoS attacks, spam campaigns, cryptocurrency mining, credential stuffing
- Individual bot owner usually unaware their computer is part of botnet
- **Cybersecurity use:** Botnets for hire — rent 100,000 bots for DDoS attack. Mirai botnet (IoT devices) took down major internet infrastructure in 2016.

**Cryptominer / Cryptojacker:**
- Uses victim's CPU/GPU to mine cryptocurrency for attacker
- Slows system significantly — 100% CPU usage
- Often delivered via: malicious browser extensions, infected software, drive-by downloads
- **Cybersecurity use:** Cryptojacking doubled in 2022 — easier to monetise than ransomware, harder to detect

**Logic Bomb:**
- Malicious code that **triggers on a specific condition** — date/time, event, or action
- Dormant until trigger condition met
- Example: "If I am removed from payroll, delete all financial records"
- Planted by insiders with system access
- **Cybersecurity use:** Very hard to detect before trigger — regular code audits needed

**Fileless Malware:**
- Operates entirely in **memory** — never writes to disk
- Traditional AV cannot detect it — no file to scan
- Uses: PowerShell, WMI, legitimate Windows tools to execute malicious code
- Leaves almost no forensic evidence
- **Cybersecurity use:** Most sophisticated modern attacks use fileless techniques. Detected by behavioural analysis, memory scanning, EDR tools.

---

### 2.4 Anti-malware Tools

#### Windows Defender — Built-in Protection
- Real-time protection, signature updates, behavioural detection
- Already covered in Day 5

#### Third-Party Antivirus
- Malwarebytes — excellent for removing existing infections
- Bitdefender, Kaspersky, ESET, Norton — real-time protection
- **Never run two AV products simultaneously** — conflict and performance issues

#### End Point Detection and Response (EDR)
  - a different method of threat protection.
  - detect the threat 
  - investigate the threat 
  - respond the threat

#### Managed detection and response (MDR)
  - third party edr services 
  - manages the entire process
  - respondds to al issues 
  - expertise from trained professionals

#### Extended Detection and response XDR
  - evolition of edr 
  - add network based detection
  
#### Anti-malware Scanning Best Practices
1. **Keep definitions updated** — new malware released constantly
2. **Schedule regular full scans** — weekly minimum
3. **On-demand scan** — run when suspicious behaviour observed
4. **Offline scan** — for rootkit detection (boot before OS loads)
5. **Second-opinion scanner** — use Malwarebytes alongside primary AV

#### Recovery Tools
- **Bootable rescue disk** — boot from USB with AV tool before Windows loads
- **System Restore** — roll back to clean restore point
- **OS reinstall** — nuclear option — guaranteed clean
- **Backup restore** — restore from clean backup

#### Indicators of Malware Infection
- Unexpected CPU/RAM/network usage spikes
- Antivirus disabled or won't start
- New unknown programs or browser extensions
- Unusual network connections to unknown IPs
- Files encrypted or renamed with strange extensions
- Pop-up advertisements everywhere
- Browser redirects to unexpected sites
- System slower than normal
- Friends report receiving strange emails from your account

---

### 2.5 Social Engineering

#### What is Social Engineering?
- **Manipulating people** into revealing confidential information or performing actions
- Exploits human psychology — trust, fear, urgency, authority, helpfulness
- Often more effective than technical attacks — humans are the weakest link
- No technical skill needed — just convincing communication

#### Types of Social Engineering

**Phishing:**
- Fraudulent email appearing to come from trusted source
- Goal: steal credentials, deliver malware, trick into financial transfer
- Characteristics: urgency, fear, too-good-to-be-true offers, suspicious links
- **Cybersecurity use:** Most common attack vector — 91% of cyberattacks start with phishing email

**Spear Phishing:**
- **Targeted phishing** — personalised for specific individual or organisation
- Attacker researches target — uses real names, job titles, recent events
- Much harder to detect than generic phishing
- **Cybersecurity use:** Spear phishing success rate 3x higher than generic phishing — used in APT (Advanced Persistent Threat) attacks

**Whaling:**
- Spear phishing targeting **senior executives** (CEO, CFO, CTO)
- High value target — executive has authority to authorise large transfers
- Often used in Business Email Compromise (BEC)

**Vishing — Voice Phishing:**
- Social engineering over **phone call**
- Attacker impersonates: IT support, bank, government, Microsoft
- Classic: "Your computer has a virus, give me remote access to fix it"
- **Cybersecurity use:** Tech support scam — caller claims to be Microsoft, convinces victim to install remote access software

**Smishing — SMS Phishing:**
- Phishing via **text message**
- "Your package is delayed, click here to reschedule delivery"
- Malicious link in SMS — mobile browsers offer less protection

**Pretexting:**
- Creating a **fabricated scenario** to extract information
- Attacker plays a role: IT technician, auditor, new employee, vendor
- Example: "Hi, I'm from IT, we're doing a system audit and need your password to check your account"
- **Cybersecurity use:** No legitimate IT department will ever ask for your password

**Tailgating / Piggybacking:**
- Following an authorised person through a secured door
- Attacker acts like they belong — confident posture, hands full, pretends to know staff
- **Cybersecurity use:** Most common physical security bypass — train staff to challenge anyone not badging in

**Shoulder Surfing:**
- Looking over someone's shoulder to see their screen or keyboard
- Used to steal: passwords, PINs, sensitive information
- Common in: coffee shops, public transport, open-plan offices
- **Defence:** privacy screen filters, position monitor away from public view

**Dumpster Diving:**
- Searching through discarded materials for useful information
- Physical documents: bank statements, contracts, employee lists, organisational charts
- Electronic: improperly disposed hard drives, USB drives, phones
- **Cybersecurity use:** Shred all documents, properly wipe/destroy storage before disposal

**Impersonation:**
- Pretending to be someone else — vendor, delivery person, employee
- Can be in person, over phone, or via email
- **Cybersecurity use:** Always verify identity through official channels — call back on official number, not one provided by caller

**Baiting:**
- Leaving infected USB drives in parking lots, lobbies
- Victim finds USB, curious, plugs it in
- Malware auto-runs when USB inserted
- **Cybersecurity use:** In 2016 study — 98% of found USB drives were plugged in by finders

---

### 2.5 Denial of Service (DoS)

#### What is DoS?
- **Overwhelm a system** with traffic or requests until it cannot serve legitimate users
- Goal: disrupt service, not steal data
- Impact: financial loss, reputation damage, ransom pressure

#### DoS vs DDoS
**DoS (Denial of Service):**
- Single attacker, single source
- Easier to block — just block one IP address

**DDoS (Distributed Denial of Service):**
- Many attackers (botnet) from thousands of different IP addresses
- Cannot block all sources — legitimate IP ranges involved
- Volumetric attacks: terabits per second of traffic
- **Cybersecurity use:** Largest DDoS ever: 3.47 Tbps (Microsoft Azure, 2021)

#### Types of DoS Attacks

**Volumetric Attack:**
- Flood network with massive amounts of traffic
- Consumes all available bandwidth
- Example: UDP flood, ICMP flood (ping flood)

**Protocol Attack:**
- Exploit weaknesses in network protocols
- **SYN Flood** — send thousands of TCP SYN packets, never complete handshake
  - Server allocates resources for half-open connections until it runs out
- **Cybersecurity use:** SYN cookies are a defence against SYN flood attacks

**Application Layer Attack:**
- Target specific application — HTTP, DNS, HTTPS
- Fewer requests needed — each request is expensive to process
- **HTTP flood** — legitimate-looking HTTP requests overwhelm web server
- **Slowloris** — keep many connections open by sending partial requests very slowly

**Amplification Attack:**
- Use third-party servers to amplify attack traffic
- **DNS amplification** — send small DNS query → large DNS response sent to victim
- Attacker spoofs victim's IP as source → response floods victim
- **NTP amplification** — Network Time Protocol amplifies 500x

---

### 2.5 On-Path Attacks (Man-in-the-Middle)

#### What is an On-Path Attack?
- Attacker **positions themselves between** two communicating parties
- Intercepts and potentially modifies traffic without either party knowing
- Previously called Man-in-the-Middle (MitM)

#### Types of On-Path Attacks

**ARP Spoofing/Poisoning:**
- Attacker sends fake ARP replies on local network
- Associates attacker's MAC address with victim's IP
- All traffic intended for victim goes to attacker first
- Attacker forwards traffic to real destination — neither side notices
- **Cybersecurity use:** Enables: credential capture, session hijacking, SSL stripping

**DNS Spoofing/Poisoning:**
- Replace legitimate DNS records with attacker-controlled IP
- Victims looking up `bank.com` get attacker's IP instead
- Can poison: local DNS cache, DNS server cache
- **Cybersecurity use:** DNSSEC (DNS Security Extensions) prevents DNS poisoning with cryptographic signatures

**SSL Stripping:**
- Downgrade HTTPS connection to HTTP — remove encryption
- Attacker between user and website — forwards HTTPS to server but HTTP to user
- User sees HTTP (no padlock) — traffic unencrypted and readable
- **Cybersecurity use:** HSTS (HTTP Strict Transport Security) — browser remembers site is HTTPS only — prevents SSL stripping

**Evil Twin Attack:**
- Rogue Wi-Fi access point with same SSID as legitimate network
- Stronger signal attracts victims to connect to attacker's AP
- All traffic flows through attacker — full visibility
- **Cybersecurity use:** Always use VPN on public Wi-Fi — even evil twin cannot read encrypted VPN traffic

**Session Hijacking:**
- Steal authenticated session cookie — use it to impersonate logged-in user
- No password needed — session already authenticated
- **Cybersecurity use:** HTTPS prevents session cookie interception. Cookie flags: Secure (HTTPS only), HttpOnly (JavaScript cannot read it).

---

### 2.5 Zero-Day Attacks

#### What is a Zero-Day?
- Vulnerability that is **unknown to the vendor** — zero days to fix it
- No patch available — systems fully exposed
- Extremely valuable — sold on dark web for millions of dollars
- Once discovered by vendor → patch released → vulnerability no longer zero-day

#### Zero-Day Timeline
```
Day 0:    Vulnerability discovered (by attacker or researcher)
Day 0:    If attacker — exploits immediately, may sell to others
Day X:    Vendor discovers vulnerability (from researcher, breach, or reverse engineering)
Day X+n:  Vendor develops patch
Day X+n:  Patch released to public → no longer zero-day
```

#### Why Zero-Days Are Dangerous
- No defence — cannot patch what has no patch
- Antivirus cannot detect — no signatures for new exploit
- Legitimate software becomes attack vector
- **Cybersecurity use:** Zero-days used in: Stuxnet (Siemens PLCs), NSO Group Pegasus (iPhones), nation-state attacks

#### Defence Against Zero-Days
- **Network segmentation** — limit blast radius
- **Behavioural detection** — detect unusual behaviour even without signatures
- **Least privilege** — limit what compromised system can access
- **Defence in depth** — multiple security layers
- **Prompt patching** — apply patches immediately when released
- **Threat intelligence** — monitor for emerging threats

---

### 2.5 Password Attacks

#### Brute Force Attack
- Try **every possible combination** until correct password found
- Guaranteed to work eventually — time depends on password complexity
- 8-character lowercase password: ~2 hours
- 12-character mixed password: ~3,000 years (with modern hardware)
- **Defence:** Account lockout, long complex passwords, MFA

#### Dictionary Attack
- Try words from a **wordlist** — common passwords, dictionary words
- Much faster than brute force — most people use real words
- Common wordlists: rockyou.txt (14 million real passwords from breach)
- **Defence:** Avoid real words, use passphrases with substitutions, password manager

#### Rainbow Table Attack
- Pre-computed table of **password hashes**
- Look up hash in table → find original password instantly
- Extremely fast — no computation needed at attack time
- **Defence:** **Salting** — add random data to password before hashing → same password produces different hash each time → rainbow tables useless

#### Credential Stuffing
- Use **stolen username/password pairs** from data breaches on other sites
- Works because people reuse passwords across multiple sites
- Automated — test millions of credential pairs per hour
- **Defence:** Unique password for every site, MFA, monitor for breach notifications (haveibeenpwned.com)

#### Password Spraying
- Try **one common password** against many accounts
- Avoids account lockout — only one attempt per account
- Common passwords tried: `Password1!`, `Welcome1`, `Company2024!`
- **Defence:** Block common passwords, MFA, monitor for distributed login failures

#### Keylogger
- Records every keystroke — captures passwords as typed
- Software keylogger: malware running on victim's system
- Hardware keylogger: physical device between keyboard and computer
- **Defence:** AV software, physical inspection of keyboard port, on-screen keyboard for sensitive input

---

### 2.5 Insider Threats

#### What is an Insider Threat?
- **Someone with legitimate access** who abuses it — employee, contractor, partner
- Already inside the network — bypasses perimeter security
- Has legitimate credentials — harder to detect than external attacker
- **Cybersecurity use:** Insider threats cause 60% of data breaches — more damaging than external attacks

#### Types of Insider Threats

**Malicious Insider:**
- Intentionally causes harm — steals data, sabotages systems
- Motivations: financial gain, revenge, ideology, coercion
- Example: disgruntled employee deletes critical data on last day

**Negligent Insider:**
- Causes harm through **carelessness** — not malicious intent
- Example: clicks phishing link, loses laptop, sends sensitive data to wrong recipient
- Most common type of insider threat

**Compromised Insider:**
- Legitimate user's account **taken over** by external attacker
- Attacker uses insider's credentials to move laterally
- Victim may not know their account is being abused

#### Defence Against Insider Threats
- **Least privilege** — limit what each user can access
- **Separation of duties** — no single person controls entire process
- **User and Entity Behaviour Analytics (UEBA)** — detect unusual access patterns
- **DLP (Data Loss Prevention)** — monitor and block sensitive data leaving organisation
- **Audit logs** — log everything, review regularly
- **Background checks** — screen employees before hiring
- **Offboarding process** — disable accounts immediately when employee leaves

---

### 2.5 SQL Injection Attacks

#### What is SQL Injection?
- Attacker **inserts malicious SQL code** into an input field
- Application passes input directly to database without sanitisation
- Database executes attacker's SQL — unintended operations performed
- **Most common web application vulnerability**

#### How SQL Injection Works

Normal login query:
```sql
SELECT * FROM users WHERE username='john' AND password='pass123'
```

Attacker enters username: `admin'--`

Resulting query:
```sql
SELECT * FROM users WHERE username='admin'--' AND password='anything'
-- The -- comments out the rest — password check bypassed!
-- Attacker logs in as admin without knowing password
```

#### Types of SQL Injection
- **Classic/In-band** — results returned directly in application response
- **Blind SQLi** — no direct output — infer data from true/false responses
- **Time-based Blind** — infer data from response time delays
- **Out-of-band** — data exfiltrated via different channel (DNS, HTTP request)

#### Impact of SQL Injection
- **Authentication bypass** — log in without credentials
- **Data exfiltration** — dump entire database
- **Data modification** — change prices, delete records
- **Remote code execution** — in some configurations, execute OS commands
- **Cybersecurity use:** PortSwigger Web Security Academy — you will do all SQL injection labs in Phase 5

#### Defence Against SQL Injection
- **Parameterised queries / Prepared statements** — treat user input as data, never as SQL
- **Input validation** — reject unexpected characters
- **Stored procedures** — pre-compiled SQL
- **WAF (Web Application Firewall)** — detect and block injection attempts
- **Least privilege** — database account used by app should have minimal permissions

---

### 2.5 Cross-Site Scripting (XSS)

#### What is XSS?
- Attacker **injects malicious JavaScript** into a web page
- Script executes in other users' browsers
- Victim's browser runs attacker's code — trusts it because it came from legitimate site

#### Types of XSS

**Reflected XSS:**
- Malicious script in the URL/request
- Server reflects it back in response — runs in victim's browser
- Victim must click malicious link
- Example: `https://site.com/search?q=<script>stealCookies()</script>`

**Stored/Persistent XSS:**
- Script **stored in the database** — e.g. in a comment or profile field
- Executes every time anyone views that page
- More dangerous — no need to trick victim into clicking link
- Example: attacker posts comment containing JavaScript — every visitor runs the script

**DOM-based XSS:**
- Vulnerability in client-side JavaScript
- Script never sent to server — manipulates DOM directly
- Harder to detect — no server-side evidence

#### Impact of XSS
- **Session hijacking** — steal authentication cookies
- **Credential harvesting** — fake login form overlay
- **Keylogging** — record keystrokes in browser
- **Malware distribution** — redirect victims to malware download
- **Defacement** — change appearance of website for all visitors

#### Defence Against XSS
- **Output encoding** — escape special characters before displaying user input
- **Content Security Policy (CSP)** — browser only executes scripts from trusted sources
- **Input validation** — reject unexpected input
- **HttpOnly cookies** — cookies inaccessible to JavaScript — prevents theft
- **WAF** — detect and block XSS attempts

---

### 2.5 Business Email Compromise (BEC)

#### What is BEC?
- Sophisticated attack targeting **businesses through email**
- Attacker impersonates trusted person — CEO, CFO, vendor, lawyer
- Goal: fraudulent wire transfer, credential theft, data theft
- **Average BEC loss: $125,000 per incident** — billions lost annually

#### Common BEC Scenarios

**CEO Fraud:**
- Attacker impersonates CEO — emails CFO or finance
- "Transfer $50,000 to this account urgently for confidential acquisition"
- Creates urgency and authority — CFO complies without verification

**Invoice Fraud:**
- Impersonates vendor — sends fake invoice with changed bank details
- Company pays invoice — money goes to attacker

**Attorney Impersonation:**
- Impersonates company lawyer — requests sensitive documents or money

**Account Compromise:**
- Real employee email account compromised
- Attacker uses legitimate account to request transfers — harder to detect

#### Defence Against BEC
- **Verify all financial transfers** via phone call to known number — not email
- **Out-of-band verification** — use different communication channel to confirm
- **MFA on email accounts** — prevents account takeover
- **Email authentication** — SPF, DKIM, DMARC (covered in Day 4 notes)
- **Employee training** — recognise BEC attempts
- **Transaction approval policies** — two signatures for large transfers

---

### 2.5 Supply Chain Attacks

#### What is a Supply Chain Attack?
- Attack **upstream supplier or vendor** to compromise target downstream
- Target organisation trusts the supplier — installs compromised software/hardware
- One supplier compromised → thousands of customers compromised

#### Famous Supply Chain Attacks

**SolarWinds (2020):**
- Attackers compromised SolarWinds build process
- Malicious code inserted into Orion software update
- 18,000 organisations installed the update — including US government agencies
- Remained undetected for 9 months
- **Cybersecurity use:** Even trusted software updates can contain malware — verify signatures

**3CX (2023):**
- VoIP software compromised at build stage
- Malicious DLL inserted into legitimate software
- Customers unwittingly installed malware
- Second-level supply chain — 3CX was itself compromised via malicious npm package

**ASUS Live Update (2019):**
- ASUS's own update server compromised
- 500,000 machines received malicious update from official source

#### Defence Against Supply Chain Attacks
- **Software Bill of Materials (SBOM)** — know all components in your software
- **Code signing** — verify software hasn't been tampered with
- **Vendor security assessment** — audit third-party security practices
- **Network monitoring** — detect unexpected connections from trusted software
- **Zero trust** — even trusted software should not have unlimited access

---

### 2.5 Security Vulnerabilities

#### Types of Vulnerabilities

**CVE — Common Vulnerabilities and Exposures:**
- Standardised identifier for publicly known vulnerabilities
- Format: `CVE-YEAR-NUMBER` (e.g. CVE-2021-44228 = Log4Shell)
- Published in National Vulnerability Database (NVD)
- **CVSS score** — 0-10 severity rating (10 = critical)

**Zero-Day:** Already covered above

**Unpatched Systems:**
- Most breaches exploit **known vulnerabilities** with available patches
- WannaCry used EternalBlue — patch available 2 months before attack
- **Defence:** Patch management — apply security updates promptly

**Misconfiguration:**
- Default passwords left unchanged
- Open cloud storage buckets (S3 buckets)
- Unnecessary services running
- Overly permissive firewall rules
- **Cybersecurity use:** Most common cause of cloud data breaches is misconfiguration — not sophisticated attacks

**Weak Cryptography:**
- Using outdated algorithms: MD5, SHA1, DES, RC4, WEP
- Short key lengths: RSA-1024 (use 2048+), AES-128 (use 256 for sensitive)
- Weak random number generation

**Physical Vulnerabilities:**
- Unlocked server rooms
- Unattended workstations
- Devices left in public places

---

## 🔑 Exam Focus Summary

**Malware Types:**
- Virus = needs host file + human action
- Worm = self-replicating, no human needed
- Trojan = disguised as legitimate software
- Ransomware = encrypts files, demands payment
- Rootkit = hides presence, kernel-level
- Botnet = C2 server controls zombie computers
- Keylogger = records keystrokes
- Fileless = lives in memory, no disk writes

**Social Engineering:**
- Phishing = email, Vishing = voice, Smishing = SMS
- Spear phishing = targeted, Whaling = executives
- Pretexting = fabricated scenario
- Tailgating = physical access by following
- Baiting = infected USB drives

**Attacks:**
- DoS = single source, DDoS = distributed botnet
- SYN flood = half-open TCP connections
- ARP spoofing = on-path attack on LAN
- SQL injection = malicious SQL in input fields
- XSS = malicious JavaScript in web pages
- BEC = impersonate executive for wire transfer
- Supply chain = compromise vendor to reach target
- Rainbow table = defeated by salting passwords
- Credential stuffing = reused passwords from breaches
- Password spraying = one password, many accounts

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. Supply chain attacks compromise trusted software vendors — 18,000 organisations installed SolarWinds malware from official update server — even trusted sources cannot be blindly trusted
2. SQL injection bypasses authentication by injecting SQL — parameterised queries completely prevent this — the most common and preventable web vulnerability
3. Password salting defeats rainbow table attacks — same password produces different hash each time — without salting one cracked hash reveals all matching passwords in the database