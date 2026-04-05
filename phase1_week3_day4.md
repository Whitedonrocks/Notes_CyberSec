# CompTIA A+ 220-1202 — Week 3 Day 4 Notes

---

## Videos Watched
- ✅ 1.10 Installing Applications
- ✅ 1.11 Cloud Productivity Tools
- ✅ 2.1 Physical Security
- ✅ 2.1 Physical Access Security
- ✅ 2.1 Logical Security
- ✅ 2.1 Authentication and Access

---

## Key Concepts

### 1.10 Installing Applications

#### System Requirements — Check Before Installing
Before installing any application always verify:
- **CPU speed** — minimum processor speed required
- **RAM** — minimum memory required to run the app
- **Storage space** — how much disk space the app needs
- **32-bit vs 64-bit** — application must match OS architecture
  - 64-bit OS can run both 32-bit and 64-bit apps
  - 32-bit OS can ONLY run 32-bit apps
- **Operating system version** — app may require Windows 10/11 minimum
- **Graphics** — some apps require dedicated GPU or DirectX version
- **Network** — some apps require internet for licensing or features

#### Application Installation Methods

**Local Installation (.exe / .msi):**
- Download installer from manufacturer website
- Double-click → follow setup wizard
- **.exe** = executable installer — runs setup program
- **.msi** = Microsoft Installer — more controlled, supports Group Policy deployment
- Always download from **official manufacturer website** — not third-party sites
- **Cybersecurity use:** Fake installers are the most common malware delivery method — always verify the source

**Silent/Unattended Installation:**
- Install without any user interaction
- Used for enterprise mass deployment
- Example: `setup.exe /S` or `msiexec /i package.msi /quiet`
- **Cybersecurity use:** Malware uses silent installation to install without user noticing

**Windows Store / Microsoft Store:**
- Curated app marketplace built into Windows
- Apps reviewed by Microsoft before publishing
- Automatic updates
- Sandboxed — apps have limited system access
- **Safer than downloading random .exe files**

**Third-Party App Stores:**
- Ninite.com — install multiple apps at once, no bloatware
- Chocolatey — command-line package manager for Windows
- winget — Microsoft's official command-line package manager

**Linux Installation Methods:**
```bash
sudo apt install appname      # Debian/Ubuntu — package manager
sudo dnf install appname      # Red Hat/Fedora
sudo snap install appname     # Universal snap package
flatpak install appname       # Universal flatpak package
./install.sh                  # Manual installation script
```

#### Impact on Device

**Impact on Operations:**
- Applications consume CPU, RAM, disk, network
- Too many apps = sluggish performance
- Background processes from apps run even when app is closed
- Check Task Manager → Startup for apps that auto-start

**Impact on Network:**
- Apps that phone home — telemetry, update checks, licensing
- Bandwidth-heavy apps affect other network users
- Enterprise apps may require firewall rules for network access

**Impact on Device:**
- Driver installation — some apps install device drivers
- System32 DLL files — shared library files added to Windows
- Registry entries — app settings stored in Windows Registry
- Services — apps may install background Windows services
- **Cybersecurity use:** Apps that install drivers have kernel-level access — malicious driver = rootkit

#### Removing Applications

**Windows:**
- Settings → Apps → Apps & Features → select app → Uninstall
- Control Panel → Programs and Features → Uninstall
- Some apps leave behind: registry entries, leftover files, services
- Use a third-party uninstaller (Revo Uninstaller) for complete removal

**Linux:**
```bash
sudo apt remove appname         # remove app (keep config)
sudo apt purge appname          # remove app + all config files
sudo apt autoremove             # remove unused dependencies
```

#### App Compatibility Issues

**Legacy Applications:**
- Old software may not run on modern Windows
- Solutions:
  - **Compatibility mode** — right-click .exe → Properties → Compatibility tab → Run as Windows 7/XP
  - **Virtual machine** — run old OS in VM, install old app there
  - **Application virtualisation** — stream app without full install (App-V)

**32-bit vs 64-bit Conflicts:**
- 32-bit apps install to `C:\Program Files (x86)\`
- 64-bit apps install to `C:\Program Files\`
- Cannot mix 32-bit and 64-bit DLL files

---

### 1.11 Cloud Productivity Tools

#### What Are Cloud Productivity Tools?
- Software delivered over the internet — no local installation required
- Access from any device, anywhere
- Files stored in the cloud — always synced and backed up
- Collaboration in real time — multiple people edit simultaneously

#### Microsoft 365 (formerly Office 365)
- Cloud-based version of Microsoft Office
- Includes: Word, Excel, PowerPoint, Outlook, Teams, OneDrive
- Subscription-based — monthly or annual fee
- Apps available: web browser (free), desktop app (subscription)
- **OneDrive** — integrated cloud storage (1TB with subscription)
- **Teams** — video conferencing, chat, file sharing, collaboration
- **Exchange Online** — cloud email hosting
- **SharePoint Online** — company intranet and document management
- **Cybersecurity use:** Microsoft 365 accounts are prime phishing targets — MFA is essential

#### Google Workspace (formerly G Suite)
- Google's cloud productivity suite
- Includes: Gmail, Google Docs, Sheets, Slides, Drive, Meet, Calendar
- Free personal tier, paid business tier
- Real-time collaboration — multiple users edit same document simultaneously
- **Google Drive** — 15GB free cloud storage
- **Google Meet** — video conferencing
- No desktop app needed — runs entirely in browser
- **Cybersecurity use:** Google account compromise = access to all files, emails, and connected services

#### Comparison

| Feature | Microsoft 365 | Google Workspace |
|---|---|---|
| Word processor | Word | Google Docs |
| Spreadsheet | Excel | Google Sheets |
| Presentation | PowerPoint | Google Slides |
| Email | Outlook | Gmail |
| Storage | OneDrive | Google Drive |
| Video calls | Teams | Google Meet |
| Free storage | 5GB | 15GB |
| Offline access | Yes (desktop app) | Limited |
| Best for | Enterprise, Windows | Education, startups |

#### Other Cloud Tools
- **Dropbox** — cloud file storage and sync
- **Slack** — team messaging and collaboration
- **Zoom** — video conferencing
- **Salesforce** — cloud CRM (Customer Relationship Management)
- **Box** — enterprise cloud storage with advanced security

#### Benefits of Cloud Productivity Tools
- **Accessibility** — work from any device, any location
- **Collaboration** — real-time multi-user editing
- **Automatic updates** — always latest version, no manual updates
- **Automatic backup** — files saved to cloud automatically
- **Scalability** — easily add/remove users
- **Cost** — subscription vs large upfront licence cost

#### Security Concerns
- **Data sovereignty** — where is your data physically stored?
- **Account security** — MFA is critical — one stolen password = all your data
- **Shared responsibility** — provider secures infrastructure, you secure your account
- **Data breaches** — cloud providers are high-value targets
- **Compliance** — some industries (healthcare, finance) have strict rules about cloud data

---

### 2.1 Physical Security

#### Why Physical Security Matters
- The most secure network is useless if someone can physically access the hardware
- Physical access = game over for most security controls
- **Cybersecurity use:** Attacker with physical access can: boot from USB, remove drive, connect hardware keylogger, install malicious hardware

#### Securing Physical Locations

**Barricades and Bollards:**
- **Barricades** — physical barriers preventing vehicle access
- **Bollards** — short posts embedded in ground, prevent vehicle ramming attacks
- Protect entrances to data centres, government buildings
- Prevent vehicle-borne attacks

**Access Control Vestibules (Mantraps):**
- Small room with two doors — only one can open at a time
- Person enters first door → door closes → identity verified → second door opens
- Prevents **tailgating** (unauthorised person following authorised person in)
- Used in: data centres, high-security buildings, banks
- **Cybersecurity use:** Prevents the most common physical security bypass — following someone through a secured door

**Cameras — CCTV:**
- Closed Circuit Television — records all activity
- Motion detection, night vision, remote monitoring
- Deterrent effect — people behave differently when cameras visible
- Evidence for investigations
- **PTZ cameras** — Pan, Tilt, Zoom — remotely controllable
- **Cybersecurity use:** Camera footage is forensic evidence — must be secured and retained

**Guards:**
- Human security personnel — judgement that cameras lack
- Check credentials, respond to incidents, patrol
- Reception/front desk — first line of physical security

**Alarms:**
- Motion sensors, door/window sensors, glass break sensors
- Triggered alerts sent to security team or authorities
- Types: silent (alerts security without alerting intruder), audible (loud siren)

**Lighting:**
- Well-lit areas deter physical attacks and tailgating
- Dark areas are hiding spots for attackers
- Motion-activated lighting — alerts and deters

**Fencing:**
- Perimeter control — defines secure boundary
- Different heights for different security levels
- Topped with barbed wire for higher security

**Signage:**
- "No tailgating" signs — remind people of policy
- "Under surveillance" signs — deterrent effect
- "Authorised personnel only" — legal notice

---

### 2.1 Physical Access Security

#### Door Locks

**Conventional Locks:**
- Traditional key-based locks
- Easy to pick, key can be copied
- No audit trail — don't know who entered or when

**Electronic/Smart Locks:**
- PIN pad — enter code to unlock
- Card/proximity reader — tap badge to unlock
- Biometric — fingerprint, face, iris scan
- Creates **audit trail** — logs who entered and when
- Can be remotely controlled and revoked
- **Cybersecurity use:** Lost or stolen access card can be immediately deactivated — unlike a key

**Badges and Access Cards:**
- RFID or smart card technology
- Each person has unique card with unique ID
- Access levels programmed — different areas for different people
- Must be visibly worn at all times
- **Tailgating/piggybacking** — following someone through a door without scanning own card
- **Cybersecurity use:** Card cloning — RFID cards can be cloned with cheap hardware if not encrypted properly

**Biometric Locks:**
- Fingerprint scanner — most common
- Retina/iris scanner — high security
- Facial recognition — convenient but spoofable with photos
- Hand geometry — shape of hand
- **False Acceptance Rate (FAR)** — how often wrong person is accepted (lower = better)
- **False Rejection Rate (FRR)** — how often right person is rejected (lower = better)
- **Cybersecurity use:** Biometrics cannot be changed if compromised — unlike passwords

#### Hardware Security

**Cable Locks:**
- Kensington lock — steel cable + lock attached to laptop
- Loop cable through desk anchor, lock to laptop's Kensington port
- Prevents opportunistic theft
- Can be cut with bolt cutters — deterrent, not impenetrable

**Server Locks:**
- Lock server case shut — prevents internal hardware tampering
- Rack-mount servers have lockable rack enclosures
- Prevents: RAM theft, drive theft, hardware keylogger installation

**USB Port Locks:**
- Physical plastic locks inserted into USB ports
- Prevent: unauthorised USB drive use, USB-based attacks (BadUSB)
- Used in high-security environments

**Hardware Intrusion Detection:**
- Case intrusion switch — detects if computer case is opened
- Logs event in BIOS, can trigger alert
- **Cybersecurity use:** Alerts if attacker opens computer to install hardware

#### Protecting Mobile Devices Physically

**Laptop:**
- Kensington lock when in public
- Never leave unattended in public
- Use privacy screen filter — prevents shoulder surfing
- Full disk encryption (BitLocker/FileVault) — data safe if stolen

**Phones/Tablets:**
- Screen lock with PIN/biometric
- Remote wipe capability (MDM, Find My, Find My Device)
- Case with GPS tracker
- Do not leave visible in parked car

---

### 2.1 Logical Security

#### What is Logical Security?
- Software-based security controls — as opposed to physical
- Controls access to systems, data, and resources through software
- Works alongside physical security — both needed

#### Principle of Least Privilege
- Users and processes should have the **minimum access necessary** to do their job
- No more, no less
- Example: receptionist needs email and calendar — not access to financial records
- **Cybersecurity use:** Limits damage if account is compromised — attacker can only do what that user could do

#### Access Control Models

**DAC — Discretionary Access Control:**
- Resource owner decides who gets access
- Owner can grant/revoke access to others
- Most flexible — also least secure
- Example: you share your Google Doc with specific people
- Windows NTFS permissions use DAC

**MAC — Mandatory Access Control:**
- Access controlled by security labels/classifications assigned by admin
- Users cannot change their own access level
- Used in: military, government, top-secret environments
- Example: Top Secret document only accessible to users with Top Secret clearance
- Even if you own a file — you cannot share it with someone at lower clearance

**RBAC — Role-Based Access Control:**
- Access granted based on **job role** not individual
- Example: all nurses have same access level, all doctors have different access level
- Easier to manage — change role = change all permissions
- Most common in enterprise environments
- **Cybersecurity use:** When employee leaves, disable their account and remove role = all access revoked instantly

**Rule-Based Access Control:**
- Access granted based on rules/conditions
- Example: only allow access between 9am-5pm, only from company network
- Often combined with RBAC

#### Authentication Factors

**Something you know:**
- Password, PIN, security question
- Weakest factor — can be guessed, stolen, forgotten

**Something you have:**
- Physical token, smart card, phone (for SMS code), authenticator app
- Stronger — requires physical possession

**Something you are:**
- Biometrics — fingerprint, face, iris, voice, typing pattern
- Very strong — cannot be forgotten, hard to fake
- Cannot be changed if compromised

**Somewhere you are:**
- Location-based — only allow login from specific IP/location
- Example: only allow VPN login from Nepal
- Can be bypassed with VPN

**Something you do:**
- Behavioural biometrics — typing speed, mouse movement patterns
- Continuous authentication — monitors behaviour during session

#### MFA — Multi-Factor Authentication
- Requires **two or more different factors**
- Must be from different categories — two passwords = NOT MFA
- Example: password (know) + authenticator app code (have) = MFA
- Massively reduces account compromise risk — stolen password alone not enough
- **Cybersecurity use:** MFA stops ~99.9% of automated credential attacks according to Microsoft

#### Password Policies
- **Minimum length** — 8 characters minimum, 12+ recommended
- **Complexity** — uppercase, lowercase, numbers, special characters
- **Maximum age** — force password change every 90 days (controversial — may reduce security)
- **History** — cannot reuse last 10 passwords
- **Lockout** — lock account after 5 failed attempts
- **Cybersecurity use:** Account lockout policy prevents brute force attacks but can be used as DoS — lock out all accounts to prevent legitimate access

#### Single Sign-On (SSO)
- Log in once → access to multiple systems without logging in again
- Example: log into company AD → automatically authenticated to email, SharePoint, CRM
- User experience: convenient — one password to remember
- Security risk: one compromised account = access to everything
- **Cybersecurity use:** SSO tokens are high-value targets — token theft = access to all connected systems

---

### 2.1 Authentication and Access

#### AAA Framework
- **Authentication** — who are you? (verify identity)
- **Authorisation** — what are you allowed to do? (permissions)
- **Accounting** — what did you do? (logging and audit trail)

All three must work together for complete access control.

#### RADIUS — Remote Authentication Dial-In User Service
- Centralised authentication, authorisation, and accounting for network access
- Client sends credentials to RADIUS server → RADIUS verifies → grants/denies access
- Used for: Wi-Fi enterprise authentication (WPA2-Enterprise), VPN authentication, network device login
- **Cybersecurity use:** RADIUS centralises authentication — one place to manage and audit all network access

#### LDAP — Lightweight Directory Access Protocol
- Protocol for accessing and maintaining directory services
- Stores: user accounts, groups, computers, printers — organisational information
- **Port 389** (unencrypted), **Port 636** (LDAPS — encrypted)
- Microsoft Active Directory uses LDAP underneath
- **Cybersecurity use:** LDAP injection attacks — similar to SQL injection but against directory services. Unencrypted LDAP (port 389) transmits credentials in clear text.

#### Kerberos
- Network authentication protocol used by Active Directory
- Uses **tickets** — encrypted tokens that prove identity
- Never sends password over network — only encrypted tickets
- **KDC — Key Distribution Centre** — the ticket issuing server (Domain Controller)
- Process:
  1. User logs in → KDC issues **TGT (Ticket Granting Ticket)**
  2. User wants to access resource → presents TGT → KDC issues **Service Ticket**
  3. User presents Service Ticket to resource → access granted
- **Time sensitive** — clocks must be within **5 minutes** of each other
- **Cybersecurity use:** Pass-the-Ticket attack — steal Kerberos ticket from memory and use it to authenticate as that user. Golden Ticket attack — forge a TGT with Mimikatz.

#### Tokens and Smart Cards

**Hardware Token:**
- Physical device that generates a time-based one-time password (TOTP)
- Example: RSA SecurID token — displays 6-digit code that changes every 30 seconds
- No battery dependency on phone — more reliable for high-security environments

**Smart Card:**
- Credit card-sized card with embedded chip
- Contains digital certificate and private key
- Requires PIN to use — two-factor (card + PIN)
- Common in government and military (CAC — Common Access Card)
- **Cybersecurity use:** Smart card + PIN = very strong authentication — card stolen without PIN is useless

**Software Token / Authenticator App:**
- App on smartphone generates TOTP codes
- Examples: Google Authenticator, Microsoft Authenticator, Authy
- Same principle as hardware token but on phone
- **Cybersecurity use:** SIM swapping attack — attacker convinces carrier to transfer phone number to their SIM — intercepts SMS codes

#### Certificate-Based Authentication
- Uses **digital certificates** to prove identity
- Certificate contains: public key, owner identity, expiry date, CA signature
- **PKI — Public Key Infrastructure** — system for issuing and managing certificates
- **CA — Certificate Authority** — trusted organisation that signs certificates
- Used in: HTTPS, email signing (S/MIME), VPN, Wi-Fi (WPA2-Enterprise)
- **Cybersecurity use:** Rogue CA certificates installed by malware can intercept all HTTPS traffic — check trusted root CAs regularly

---

## Terminal Practice

```bash
# Check who is logged in
who
w
last | head -10

# Check authentication logs
sudo grep "Failed password" /var/log/auth.log | tail -10
sudo grep "Accepted password" /var/log/auth.log | tail -10

# Check sudo usage
sudo grep "sudo" /var/log/auth.log | tail -10

# Check user accounts
cat /etc/passwd | grep -v "nologin\|false"
groups whitedonrocks

# Check SSH configuration
cat /etc/ssh/sshd_config | grep -E "PasswordAuth|PermitRoot|Port"
```

---

## 🔑 Exam Focus Summary

1. **Least privilege** — minimum access necessary, nothing more
2. **DAC vs MAC vs RBAC** — know the differences and use cases
3. **MFA factors** — something you know/have/are/somewhere you are
4. **AAA** — Authentication, Authorisation, Accounting
5. **Kerberos** — tickets, TGT, 5-minute clock sync requirement
6. **RADIUS** — centralised network authentication
7. **LDAP ports** — 389 (unencrypted), 636 (encrypted)
8. **Mantrap** — prevents tailgating with two-door system
9. **Smart card = two factor** — card (have) + PIN (know)
10. **Biometrics cannot be changed** — if compromised, permanent problem

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. Mantrap (access control vestibule) prevents tailgating — two doors, only one open at a time — most common physical security bypass is following someone through a door
2. Kerberos uses tickets not passwords over the network — Golden Ticket attack forges a TGT giving unlimited domain access — this is why AD compromise is so devastating
3. MFA with different factors stops 99.9% of automated attacks — two passwords is NOT MFA — must be from different categories