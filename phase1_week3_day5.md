# CompTIA A+ 220-1202 — Week 3 Day 5 Notes

---

## Videos Watched
- ✅ 2.2 Defender Antivirus
- ✅ 2.2 Windows Firewall
- ✅ 2.2 Windows Security Settings
- ✅ 2.2 Active Directory
- ✅ 2.3 Wireless Encryption
- ✅ 2.3 Authentication Methods

---

## Key Concepts

### 2.2 Defender Antivirus

#### What is Windows Defender Antivirus?
- Microsoft's **built-in antivirus** — included free with Windows 10/11
- Previously called Microsoft Security Essentials (Windows 7)
- Part of **Windows Security** (the security dashboard)
- Provides real-time protection against malware, viruses, spyware, ransomware
- **No need for third-party AV on Windows 10/11** — Defender is genuinely good
- Automatically disables itself if third-party AV is installed

#### How Defender Works

**Signature-Based Detection:**
- Compares files against a database of known malware **signatures** (patterns)
- Must be kept updated — new malware = new signatures needed
- Cannot detect malware with no known signature (zero-day)
- **Definition updates** — Microsoft releases updates multiple times per day
- **Cybersecurity use:** Attackers modify malware slightly to bypass signature detection — called **polymorphic malware**

**Heuristic/Behavioural Detection:**
- Watches what programs **do** rather than what they look like
- Suspicious behaviour: encrypting many files rapidly, injecting into other processes, making registry changes
- Can detect **new malware** even without signatures
- May cause false positives — legitimate software flagged as suspicious

**Cloud-Based Protection:**
- Suspicious files sent to Microsoft cloud for analysis
- Near-instant response to new threats
- Must be enabled for best protection

**Tamper Protection:**
- Prevents malware from disabling Defender
- Locks Defender settings so only authorised users can change them
- **Cybersecurity use:** Malware first step is usually disabling AV — Tamper Protection prevents this

#### Windows Security Dashboard
Open: `Start → Windows Security` or `windowsdefender://`

Sections:
- **Virus & Threat Protection** — scan history, scan now, protection updates
- **Account Protection** — sign-in options, Windows Hello
- **Firewall & Network Protection** — firewall status per profile
- **App & Browser Control** — SmartScreen settings, exploit protection
- **Device Security** — TPM, Secure Boot, core isolation
- **Device Performance & Health** — health report
- **Family Options** — parental controls

#### Running Scans
- **Quick scan** — checks common malware locations only (fast)
- **Full scan** — scans entire system (slow — hours)
- **Custom scan** — scan specific folder or drive
- **Microsoft Defender Offline scan** — boots into special environment before Windows loads — finds rootkits that hide during normal operation
- **Cybersecurity use:** Offline scan is the only way to detect rootkits that hide from running OS

#### Windows Defender SmartScreen
- Checks websites and downloaded files against Microsoft's reputation database
- Warns before opening potentially dangerous files or websites
- **Cybersecurity use:** First line of defence against phishing and drive-by downloads

---

### 2.2 Windows Firewall

#### Windows Defender Firewall
- Built-in stateful packet inspection firewall
- **Should always be enabled** — even with third-party security software
- Three network profiles:

| Profile | When Used | Default Setting |
|---|---|---|
| **Domain** | Connected to Windows domain network | Allow most traffic |
| **Private** | Home or trusted network | Moderate restrictions |
| **Public** | Coffee shop, airport, hotel | Most restrictive |

- Each profile has independent settings — same computer can have different rules for each
- **Cybersecurity use:** Setting network as Public adds extra protection on untrusted networks

#### Firewall Rule Types

**Inbound Rules:**
- Control traffic **coming INTO** your computer
- Default: block all inbound except established connections
- Allow exceptions for: Remote Desktop, file sharing, specific apps

**Outbound Rules:**
- Control traffic **leaving** your computer
- Default: allow all outbound (most restrictive is to block all and whitelist)
- **Cybersecurity use:** Outbound rules are often ignored — malware exploits this to send data out. Configure outbound rules to block unknown processes.

**Connection Security Rules:**
- IPSec rules — encrypt and authenticate connections between computers
- Used for: VPN tunnels, server-to-server encryption

#### Windows Firewall Advanced Settings — `wf.msc`
- Full management interface for firewall rules
- Create rules based on: program, port, protocol, IP address, service
- Import/export rules
- Monitor active connections and matching rules

#### Firewall Rule Properties
- **Program** — which application the rule applies to
- **Protocol** — TCP, UDP, ICMP
- **Local port** — port on your computer
- **Remote port** — port on the remote computer
- **Local IP** — your IP address
- **Remote IP** — IP address of remote computer
- **Action** — Allow, Allow if secure, Block
- **Profile** — Domain, Private, Public (can apply to multiple)

---

### 2.2 Windows Security Settings

#### Windows Security Center
- Central hub for all security settings in Windows 10/11
- Open: `Start → Windows Security`

#### Core Isolation and Memory Integrity
- **Core Isolation** — uses virtualisation to protect core OS processes
- **Memory Integrity (HVCI)** — prevents malicious code from being injected into high-security processes
- Requires: CPU with virtualisation support (VT-x or AMD-V)
- **Cybersecurity use:** Prevents kernel-level attacks — makes rootkit installation much harder

#### Secure Boot
- UEFI feature that only allows signed, trusted boot software
- Prevents malicious bootloaders from loading before Windows
- Required for Windows 11
- **Cybersecurity use:** Prevents boot-level malware (bootkits) — cannot run unsigned code at boot

#### TPM — Trusted Platform Module (Recap in Security Context)
- Hardware chip that stores cryptographic keys
- Required for: BitLocker, Windows Hello, Windows 11
- **Device Encryption** — available on Home edition when TPM present
- **Cybersecurity use:** Without TPM, encryption keys stored in software — vulnerable. With TPM, keys locked to hardware.

#### Exploit Protection
- Windows 10/11 built-in exploit mitigation
- Replaces EMET (Enhanced Mitigation Experience Toolkit) from Windows 7/8
- Protections include:
  - **DEP** — Data Execution Prevention — prevents code running from data memory
  - **ASLR** — Address Space Layout Randomisation — randomises memory addresses
  - **Control Flow Guard** — prevents exploits jumping to arbitrary code
  - **SEHOP** — Structured Exception Handler Overwrite Protection
- Configure: Windows Security → App & Browser Control → Exploit Protection
- **Cybersecurity use:** These make exploiting vulnerabilities much harder — attacker must bypass multiple protections

#### Windows Sandbox
- Available on Windows 10/11 Pro and above
- Isolated temporary desktop environment
- Run untrusted software safely — sandbox completely reset when closed
- No persistent changes — fresh every time
- Enable: Turn Windows Features on/off → Windows Sandbox
- **Cybersecurity use:** Open suspicious files in Sandbox — malware cannot escape to main system

#### Windows Hello
- Biometric authentication system
- Options: facial recognition, fingerprint, PIN
- PIN is more secure than password — local to device, not transmitted over network
- Requires: TPM for full security
- **Cybersecurity use:** Windows Hello PIN is cryptographically tied to the device — cannot be used on another computer even if discovered

---

### 2.2 Active Directory

#### What is Active Directory (AD)?
- Microsoft's **directory service** — the backbone of enterprise Windows networks
- Stores and manages information about: users, computers, printers, groups, policies
- Runs on **Windows Server** — called a **Domain Controller (DC)**
- The single most important system in a Windows enterprise network

#### Key Active Directory Components

**Domain Controller (DC):**
- Server running Active Directory Domain Services
- Authenticates users, enforces policies, stores directory database
- Every domain needs at least one DC — most have two for redundancy
- **Cybersecurity use:** Domain Controller is the highest-value target in any Windows network — compromise = total network control

**AD Database — NTDS.DIT:**
- The actual Active Directory database file
- Located: `C:\Windows\NTDS\NTDS.DIT`
- Contains: all user accounts, password hashes, group memberships, computer accounts
- **Cybersecurity use:** Attackers who obtain NTDS.DIT can crack all domain passwords offline — Mimikatz can extract hashes from running DC

**Forest:**
- The top-level container in Active Directory
- A collection of one or more domains that share a schema
- Multiple forests can have trust relationships

**Domain:**
- Core administrative unit — collection of objects (users, computers, groups)
- Has a DNS name: `company.local` or `company.com`
- All objects in a domain share security policies

**Organisational Unit (OU):**
- Container within a domain to organise objects
- Structure mirrors business: `IT Department OU`, `HR OU`, `London OU`
- Group Policy Objects (GPOs) applied to OUs — affects all objects inside
- Example hierarchy:
```
company.local (Domain)
├── IT Department (OU)
│   ├── Helpdesk (OU)
│   └── Sysadmins (OU)
├── HR (OU)
└── Finance (OU)
```

**Objects:**
- Everything in AD is an object: users, computers, groups, printers, OUs
- Each object has **attributes** — properties like name, email, phone, department

#### Active Directory Users and Computers (ADUC)
- Main GUI tool for managing AD objects
- Open: `dsa.msc` on Domain Controller
- Tasks: create/delete users, reset passwords, add to groups, disable accounts

#### User Accounts in AD

**Creating a User:**
- ADUC → right-click OU → New → User
- Set: first name, last name, username (UPN), password, must change at next login

**User Account Properties:**
- **General** — name, description, phone, email
- **Account** — username, logon hours, computer restrictions, account expiry
- **Profile** — home folder, profile path, logon script
- **Member Of** — group memberships
- **Dial-in** — VPN access permissions

**Account Options:**
- **Disabled** — account cannot log in (use for terminated employees instead of deleting)
- **Password never expires** — service accounts often need this
- **Account is locked out** — unlock after too many failed attempts
- **Must change password at next logon** — force password change

**Cybersecurity use:** 
- Disable (not delete) accounts when employees leave — preserves audit trail
- Check for accounts with "Password never expires" — often abused by attackers
- Check for accounts with no logon restrictions — should only log in during business hours

#### Groups in Active Directory

**Security Groups** — used to assign permissions to resources
**Distribution Groups** — used for email distribution lists only

**Group Scope:**
| Scope | Members From | Used For |
|---|---|---|
| **Domain Local** | Any domain | Assigning permissions to local resources |
| **Global** | Same domain only | Organising users in same domain |
| **Universal** | Any domain in forest | Cross-domain access |

**Built-in Groups:**
- **Domain Admins** — full control of entire domain — most powerful group
- **Enterprise Admins** — full control of entire forest
- **Domain Users** — all user accounts automatically added here
- **Domain Computers** — all computer accounts
- **Administrators** — local admin on Domain Controllers
- **Account Operators** — can create/manage user accounts
- **Backup Operators** — can backup/restore domain controllers

**Cybersecurity use:** Domain Admins group is the primary target of attackers. BloodHound tool maps paths from regular user to Domain Admin. "Pass the hash" and "Kerberoasting" attacks target AD credentials.

#### Group Policy Objects (GPOs)

**What is Group Policy?**
- Rules and settings applied to users and computers in AD
- Automatically enforced — users cannot override
- Applied at domain, OU, or site level

**Common GPO Settings:**
- Password policy — complexity, length, expiry
- Software deployment — push MSI packages to computers automatically
- Desktop restrictions — prevent access to Control Panel, CMD, Registry
- Software restriction — whitelist/blacklist applications (AppLocker)
- Startup/shutdown scripts — run scripts when computer starts/stops
- Security settings — firewall rules, audit policy, user rights

**GPO Processing Order (LSDOU):**
1. **L**ocal — local computer policy
2. **S**ite — AD site policy
3. **D**omain — domain-level policy
4. **O**U — OU policy (most specific wins)

**Cybersecurity use:** Attackers with Domain Admin rights modify GPOs to push malware to all computers in the domain simultaneously — mass compromise with one change.

#### Active Directory Security Best Practices
- Enable **Tiered Administration** — separate accounts for admin vs daily use
- Use **Protected Users security group** — prevents credential caching
- Enable **AD Recycle Bin** — recover accidentally deleted objects
- Monitor **privileged group membership** — alert on changes to Domain Admins
- Use **LAPS (Local Administrator Password Solution)** — randomise local admin passwords
- Regular **AD backups** — can restore after ransomware attack
- **Cybersecurity use:** BloodHound + SharpHound — attackers map AD to find shortest path to Domain Admin. Defence: use PingCastle to audit AD security posture.

---

### 2.3 Wireless Encryption

#### Why Wireless Encryption Matters
- Wi-Fi signals broadcast in all directions — anyone nearby can receive them
- Without encryption — all network traffic visible to anyone with a wireless adapter
- Encryption makes traffic unreadable without the key

#### WEP — Wired Equivalent Privacy
- **First Wi-Fi encryption standard** — introduced 1999
- **Completely broken — never use**
- Uses RC4 cipher with static 40-bit or 104-bit key
- IV (Initialisation Vector) reuse flaw — key recoverable in minutes
- **Cybersecurity use:** WEP can be cracked in under 5 minutes with aircrack-ng — any network using WEP is completely insecure

#### WPA — Wi-Fi Protected Access
- Introduced 2003 as emergency replacement for WEP
- Uses **TKIP** (Temporal Key Integrity Protocol) — key changes per packet
- Better than WEP but still has vulnerabilities
- **Also deprecated — do not use**
- **Cybersecurity use:** TKIP has known attacks — WPA networks are crackable

#### WPA2 — Wi-Fi Protected Access 2
- **Current standard** — introduced 2004, mandatory since 2006
- Uses **AES-CCMP** encryption — much stronger than TKIP
- Two modes:

**WPA2-Personal (PSK — Pre-Shared Key):**
- Single password shared by all users
- Home networks, small offices
- Password entered once — same for everyone
- **Cybersecurity use:** WPA2-Personal handshake can be captured and password cracked offline with dictionary/brute force. 4-way handshake attack.

**WPA2-Enterprise:**
- Each user has individual credentials (username/password or certificate)
- Uses **802.1X** and **RADIUS** server for authentication
- No shared password — revoke individual user access
- Used in: businesses, universities, enterprise Wi-Fi
- **Cybersecurity use:** Much harder to attack — no single password to crack. Evil twin attack requires valid credentials to fool users.

#### WPA3 — Wi-Fi Protected Access 3
- **Latest standard** — introduced 2018, becoming common
- Significant improvements over WPA2:

**WPA3-Personal:**
- Uses **SAE (Simultaneous Authentication of Equals)** — replaces PSK
- **Forward secrecy** — each session uses different encryption keys
  - Even if password is discovered, past sessions cannot be decrypted
- **Protection against offline dictionary attacks** — password cracking much harder
- 192-bit encryption (up from 128-bit)

**WPA3-Enterprise:**
- 192-bit minimum encryption strength
- Improved key management
- Protection against passive eavesdropping

**Cybersecurity use:** WPA3 SAE prevents the 4-way handshake capture attack that works against WPA2. Much more resistant to offline cracking.

#### Encryption Standards Comparison

| Standard | Encryption | Status | Vulnerability |
|---|---|---|---|
| WEP | RC4 40/104-bit | **Broken — never use** | Cracked in minutes |
| WPA | TKIP | **Deprecated** | TKIP attacks |
| WPA2-Personal | AES-CCMP 128-bit | **Current standard** | Offline handshake crack |
| WPA2-Enterprise | AES-CCMP 128-bit | **Recommended for business** | Requires RADIUS server |
| WPA3-Personal | AES-CCMP 128-bit + SAE | **Latest — best** | Few known attacks |
| WPA3-Enterprise | AES-CCMP 192-bit | **Latest enterprise** | Most secure |

#### TKIP vs AES/CCMP
- **TKIP** — older, weaker, uses RC4 base — **avoid**
- **AES-CCMP** — modern, strong, used in WPA2/WPA3 — **use this**
- When configuring router: select **WPA2-AES** or **WPA3** — never "WPA/WPA2 mixed" with TKIP

---

### 2.3 Authentication Methods

#### What Authentication Methods Exist?

#### Local Authentication
- Username and password stored **locally** on the device
- Windows: SAM database (`C:\Windows\System32\config\SAM`)
- Linux: `/etc/shadow`
- No network required — works offline
- **Cybersecurity use:** Local accounts bypass domain security policies — attackers create local admin accounts for persistence

#### Domain Authentication (Active Directory)
- Credentials verified by **Domain Controller**
- Uses **Kerberos** protocol (covered in Day 4)
- Centralised — manage all accounts from one place
- **Cybersecurity use:** DC unavailable = users cannot log in (DoS via DC attack)

#### LDAP Authentication
- Authenticate against an LDAP directory server
- Common in: Linux environments, web applications, custom apps
- **Port 389** (plain) or **636** (LDAPS — encrypted)
- **Cybersecurity use:** LDAP on port 389 sends credentials in cleartext — always use LDAPS

#### RADIUS Authentication
- Centralised authentication for network access
- Client → RADIUS server → grant/deny access
- Used for: enterprise Wi-Fi (WPA2-Enterprise), VPN, network switch/router login
- **Cybersecurity use:** Single RADIUS server compromise = all network access compromised

#### Certificate-Based Authentication
- Uses **digital certificate** + **private key** to prove identity
- No password required — more secure
- Used in: smart cards, WPA2/3-Enterprise, VPN, HTTPS client authentication
- Certificate stored on: smart card, TPM, software keystore
- **Cybersecurity use:** Certificate theft = impersonation. Private key must be protected.

#### Multifactor Authentication (MFA) Methods

**SMS One-Time Password:**
- Code sent via text message
- Convenient but weakest MFA method
- Vulnerable to: SIM swapping, SS7 attacks, phishing
- **Cybersecurity use:** SS7 protocol vulnerabilities allow attackers to intercept SMS messages — sophisticated attackers bypass SMS MFA

**TOTP — Time-Based One-Time Password:**
- Authenticator app generates 6-digit code every 30 seconds
- Uses shared secret between app and server + current time
- Examples: Google Authenticator, Microsoft Authenticator, Authy
- Much better than SMS — no interception risk
- **Cybersecurity use:** TOTP codes can be phished in real-time — attacker phishes code and uses it immediately before it expires (real-time phishing proxy)

**HOTP — HMAC-Based One-Time Password:**
- Counter-based instead of time-based
- Code changes with each use (not every 30 seconds)
- Used in: hardware tokens (RSA SecurID)

**Push Notification:**
- Authentication app receives push notification — approve or deny
- Example: Microsoft Authenticator, Duo Security
- Better UX than typing codes
- **Cybersecurity use:** MFA fatigue/push bombing — attacker spams push notifications until user accidentally approves

**Hardware Security Key (FIDO2/WebAuthn):**
- Physical USB or NFC key (YubiKey, Google Titan)
- Cryptographic authentication — cannot be phished
- Phishing-resistant — key verifies the real website domain
- **Gold standard for MFA** — cannot be intercepted or replicated
- **Cybersecurity use:** Only MFA method completely resistant to phishing — cannot approve login on fake website

#### Passwordless Authentication
- Eliminate passwords entirely — replace with:
  - Biometrics (Windows Hello)
  - Hardware key (FIDO2)
  - Authenticator app (Microsoft Authenticator passwordless)
- **Cybersecurity use:** No password = nothing to steal, phish, or crack

#### SSO — Single Sign-On
- Authenticate once → access multiple systems
- Protocols: **SAML**, **OAuth 2.0**, **OpenID Connect**

**SAML — Security Assertion Markup Language:**
- XML-based standard for SSO
- Enterprise SSO between company systems
- **Identity Provider (IdP)** — verifies identity (e.g. Active Directory)
- **Service Provider (SP)** — the app you want to access
- **Cybersecurity use:** SAML token theft = access to all connected services

**OAuth 2.0:**
- Authorisation framework — not authentication
- Allows apps to access resources on behalf of user without sharing password
- Example: "Sign in with Google" → Google grants app limited access to your profile
- **Cybersecurity use:** OAuth token theft → attacker accesses third-party apps connected to your account

**OpenID Connect:**
- Authentication layer built on top of OAuth 2.0
- Adds user identity verification to OAuth
- Most modern SSO systems use OpenID Connect

---

## Terminal Practice

```bash
# Check wireless security on your network
iwconfig wlp3s0

# Scan for nearby Wi-Fi networks and their security
sudo iwlist wlp3s0 scan | grep -E "ESSID|Encryption|IE"

# Check your current Wi-Fi security type
nmcli -f SSID,SECURITY dev wifi list

# Check authentication logs
sudo grep "authentication failure" /var/log/auth.log | tail -10
sudo grep "session opened" /var/log/auth.log | tail -10

# Check firewall status
sudo ufw status verbose

# Check Windows Defender equivalent on Linux (ClamAV)
which clamscan
sudo apt install clamav -y
sudo freshclam           # update virus definitions
sudo clamscan -r /home   # scan home directory
```

---

## 🔑 Exam Focus Summary

**Defender Antivirus:**
1. Signature-based vs behavioural detection
2. Offline scan detects rootkits
3. Tamper Protection prevents malware disabling AV
4. SmartScreen checks downloads and websites

**Windows Firewall:**
1. Three profiles — Domain, Private, Public
2. Default: block inbound, allow outbound
3. Inbound vs Outbound rules
4. `wf.msc` — advanced firewall management

**Active Directory:**
1. Domain Controller — authenticates and manages
2. NTDS.DIT — AD database containing all password hashes
3. OU — organise objects, apply Group Policy
4. GPO processing order — LSDOU
5. Domain Admins — highest privilege group
6. Kerberos — tickets, not passwords over network

**Wireless Encryption:**
1. WEP — broken, never use
2. WPA — deprecated, avoid
3. WPA2-Personal — current standard, offline crack possible
4. WPA2-Enterprise — individual credentials + RADIUS
5. WPA3 — SAE, forward secrecy, phishing resistant
6. AES-CCMP = good, TKIP = avoid

**Authentication Methods:**
1. MFA = two or more DIFFERENT factors
2. SMS MFA = weakest — SIM swapping attack
3. TOTP = better — Google Authenticator
4. FIDO2/Hardware key = best — phishing resistant
5. Push bombing/MFA fatigue — spam approvals
6. SAE (WPA3) prevents offline dictionary attacks
7. Forward secrecy — past sessions cannot be decrypted

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. WPA3 SAE prevents the 4-way handshake attack that breaks WPA2 — forward secrecy means even if password is discovered later, captured traffic cannot be decrypted
2. NTDS.DIT contains all Active Directory password hashes — attackers who obtain this file can crack every domain account password offline — the entire forest is compromised
3. FIDO2 hardware keys are the only phishing-resistant MFA — all other methods can be bypassed by real-time phishing proxies — hardware key verifies the actual website domain