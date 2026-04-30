# CompTIA A+ 220-1202 — Week 3 Day 7 Notes

---

## Videos Watched
- ✅ 2.6 Removing Malware
- ✅ 2.7 Security Best Practices
- ✅ 2.8 Mobile Device Security
- ✅ 2.9 Data Destruction
- ✅ 2.10 Securing a SOHO Network
- ✅ 2.11 Browser Security
- ✅ 3.1 Troubleshooting Windows
- ✅ 3.2 Troubleshooting Mobile Devices
- ✅ 3.3 Troubleshooting Mobile Device Security
- ✅ 3.4 Troubleshooting Security Issues

---

## Key Concepts

### 2.6 Removing Malware

#### Malware Removal Process — Step by Step

**Step 1 — Identify and Research:**
- Identify symptoms — what is the malware doing?
- Research the specific malware — understand what it modifies
- Check: Task Manager, startup programs, running services, network connections
- Tools: Process Explorer (Sysinternals), Autoruns, TCPView

**Step 2 — Quarantine the Infected System:**
- **Disconnect from network immediately** — prevent spread and C2 communication
- Disable Wi-Fi and unplug Ethernet cable
- Prevents: spreading to other systems, receiving commands, exfiltrating data
- If ransomware — isolation may prevent encryption of network shares

**Step 3 — Disable System Restore (Windows):**
- Malware may hide in restore points
- Clear restore points before scanning — prevents reinfection from restore
- Control Panel → System → System Protection → Configure → Delete restore points

**Step 4 — Boot into Safe Mode:**
- Safe Mode loads minimal drivers and services
- Many malware variants cannot run in Safe Mode
- Safe Mode with Networking — allows downloading tools if needed
- Access: hold Shift + Restart → Troubleshoot → Advanced → Startup Settings → F4/F5

**Step 5 — Run Multiple Scans:**
- Use at least two different scanning tools — no single tool catches everything
- **Windows Defender Offline scan** — scans before Windows loads (detects rootkits)
- **Malwarebytes** — excellent second-opinion scanner
- **Kaspersky Virus Removal Tool** — free standalone scanner
- Update definitions before scanning — detect latest malware

**Step 6 — Remove Malware:**
- Quarantine detected items first — review before deleting
- Some detections may be false positives
- Delete confirmed malware files, registry entries, scheduled tasks

**Step 7 — Check for Persistence Mechanisms:**
After removing main malware always check:
- `HKCU\Software\Microsoft\Windows\CurrentVersion\Run` — user startup
- `HKLM\Software\Microsoft\Windows\CurrentVersion\Run` — system startup
- Task Scheduler — scheduled tasks
- Services — hidden services
- Browser extensions — malicious add-ons
- Hosts file (`C:\Windows\System32\drivers\etc\hosts`) — DNS hijacking

**Step 8 — Patch and Update:**
- Update OS — patch the vulnerability that allowed infection
- Update all applications — browser, plugins, Office
- Update antivirus definitions

**Step 9 — Re-enable System Restore and Create Restore Point:**
- Create a clean restore point after verified clean system

**Step 10 — Change All Passwords:**
- Assume all passwords typed on infected system are compromised
- Change: email, banking, social media, work accounts
- Enable MFA on all important accounts
- Check for unauthorised access during infection period

**When to Reinstall OS:**
- Rootkit or bootkit detected — impossible to fully remove
- System still unstable after removal attempts
- Unknown malware with no removal tool available
- Critical system files modified
- **Nuclear option but guaranteed clean result**

---

### 2.7 Security Best Practices

#### Patch Management
- Apply security updates promptly — most attacks exploit known vulnerabilities
- **Windows Update** — set to automatic for security updates
- **Third-party patching** — browsers, Java, Adobe, Office all need separate updates
- **Patch Tuesday** — Microsoft releases patches second Tuesday of each month
- Test patches in non-production environment before wide deployment (enterprise)
- **Cybersecurity use:** WannaCry exploited a vulnerability patched 2 months earlier — unpatched systems = easy targets

#### Account Management Best Practices
- **Disable default accounts** — rename or disable Administrator account
- **Strong password policy** — length, complexity, history, lockout
- **Principle of least privilege** — minimum access needed
- **Disable unused accounts** — dormant accounts are attack targets
- **Regular access reviews** — audit who has access to what
- **Separate admin accounts** — use regular account for daily tasks, admin account only for admin tasks
- **Cybersecurity use:** Attackers look for default credentials and disabled-but-not-deleted accounts

#### Data Encryption
- **Encrypt sensitive data at rest** — BitLocker, FileVault, VeraCrypt
- **Encrypt data in transit** — HTTPS, VPN, SSH, SFTP
- **Encrypt email** — S/MIME or PGP for sensitive communications
- **Encrypt backups** — backup is useless if stolen without encryption

#### Security Awareness Training
- Users are the weakest link — training is critical
- Topics: phishing recognition, password hygiene, physical security, social engineering
- **Phishing simulations** — send fake phishing emails to test employees
- Regular training — not just once at onboarding
- **Cybersecurity use:** Well-trained users catch phishing attempts that technical controls miss

#### End-of-Life (EOL) Systems
- Software/hardware no longer supported — no security patches
- Running EOL systems = known vulnerabilities with no fix available
- Examples: Windows 7 (EOL 2020), Windows XP (EOL 2014)
- **Solutions:** Upgrade OS, isolate on separate network, virtual machine, replace hardware
- **Cybersecurity use:** Many critical infrastructure attacks target EOL systems — hospitals, utilities, manufacturing

#### Defence in Depth
- Multiple overlapping security layers — no single point of failure
- If one layer fails, others provide protection
- Layers: perimeter firewall, network segmentation, endpoint AV, application controls, user training, monitoring
- **Cybersecurity use:** Attacker who bypasses firewall still faces AV, still faces application controls, still faces monitoring

---

### 2.8 Mobile Device Security

#### Screen Locks
- **PIN** — 4-6 digit number — minimum acceptable
- **Password** — full alphanumeric — stronger
- **Pattern** — connect dots — leave fingerprint smudges, guessable
- **Fingerprint** — convenient and secure
- **Face ID** — convenient — can be bypassed with photos on some implementations
- **Cybersecurity use:** Enable screen lock timeout — auto-lock after 30-60 seconds of inactivity

#### Remote Wipe
- Erase all data remotely if device lost or stolen
- **iOS:** Find My iPhone → Erase iPhone
- **Android:** Find My Device → Erase device
- **MDM (enterprise):** Remote wipe via MDM console
- **Must be set up BEFORE losing device** — requires account login or MDM enrollment
- **Cybersecurity use:** Lost device with corporate data = data breach if no remote wipe capability

#### Mobile Device Encryption
- **iOS** — encrypted by default since iPhone 3GS — cannot disable
- **Android** — encrypted by default on modern devices — verify in settings
- Encryption tied to PIN/password — strong passcode = strong encryption
- **Cybersecurity use:** Encrypted device with strong PIN requires physical cracking tools — useless to casual thieves

#### App Security
- **Only install from official stores** — App Store (iOS), Google Play (Android)
- **Review app permissions** — camera, microphone, location, contacts — only grant what necessary
- **Keep apps updated** — security patches in updates
- **Remove unused apps** — less attack surface
- **Cybersecurity use:** Sideloading (installing from outside official store) bypasses security review — major malware vector on Android

#### MDM — Mobile Device Management (Security Focus)
- Enterprise tool to manage and secure mobile devices
- Capabilities:
  - **Enforce policies** — screen lock, encryption, app restrictions
  - **Remote wipe** — erase device if lost
  - **Application management** — push/remove apps remotely
  - **Container/sandboxing** — separate work data from personal data
  - **Geofencing** — restrict device capabilities based on location
  - **Jailbreak/root detection** — detect and respond to compromised devices

#### BYOD Security Considerations
- Personal device used for work — security vs privacy tension
- MDM on personal device: company can remotely wipe entire device
- **MAM (Mobile Application Management)** — manage only work apps, not entire device
- **Containerisation** — work data in encrypted container, personal data separate
- **Policy requirements:** minimum OS version, screen lock required, no jailbreak

#### Jailbreaking and Rooting
- **Jailbreaking (iOS)** — bypass Apple's restrictions, install unofficial apps
- **Rooting (Android)** — gain root access, bypass manufacturer restrictions
- Both **remove security protections** — OS vulnerabilities exposed
- Voids warranty, prevents OS updates on some devices
- **Cybersecurity use:** MDM detects jailbroken/rooted devices — corporate policy usually prohibits them

---

### 2.9 Data Destruction

#### Why Proper Data Destruction Matters
- Simply deleting files does not erase data — only removes pointer
- Formatted drives still contain recoverable data
- Improperly disposed devices = data breach
- Legal requirements in many industries (HIPAA, GDPR)

#### Data Destruction Methods

**Shredding (Physical):**
- Industrial shredder physically destroys storage media
- Hard drives, SSDs, USB drives, phones reduced to small pieces
- Most thorough method — data impossible to recover
- **Certificate of destruction** provided by vendor
- **Exam focus:** Physical destruction is the only guaranteed method

**Degaussing:**
- Powerful magnetic field scrambles magnetic storage
- Effective on: HDDs, magnetic tape, floppy disks
- **NOT effective on SSDs or flash storage** — no magnetic medium
- Renders drive unusable — cannot be reused after degaussing
- **Cybersecurity use:** Degaussed drives should still be physically destroyed — confirm degausser was effective

**Overwriting / Wiping:**
- Write random data over entire drive multiple times
- **Single pass (zeros)** — sufficient for most purposes
- **DoD 5220.22-M** — 7-pass overwrite standard — extremely thorough
- **Gutmann method** — 35 passes — overkill for modern drives
- Software tools: DBAN (Darik's Boot and Nuke), Eraser, Secure Erase
- **NOT fully effective on SSDs** — wear levelling leaves data in unmapped cells
- **Exam focus:** Overwriting is NOT reliable for SSDs — use encryption + wipe or physical destruction

**Cryptographic Erasure:**
- Encrypt the drive with strong key → destroy the key
- Data remains but is permanently inaccessible without key
- **Best method for SSDs** — works regardless of wear levelling
- iOS uses this — "Erase all content" destroys encryption key, not data

**Factory Reset:**
- Not the same as secure data destruction
- Modern smartphones: factory reset + encryption = acceptable
- Without prior encryption: factory reset recoverable with forensic tools
- **Cybersecurity use:** Always encrypt before factory reset — in that order

#### Data Destruction Standards
| Standard | Passes | Use Case |
|---|---|---|
| Single pass zeros | 1 | General use, home/office |
| DoD 5220.22-M | 7 | Government, sensitive data |
| NIST 800-88 | Varies by media | Current recommended standard |
| Gutmann | 35 | Unnecessary for modern drives |

#### Paper Data Destruction
- Shred all documents containing sensitive information
- **Cross-cut shredder** — cuts horizontally and vertically — much harder to reconstruct
- **Micro-cut shredder** — highest security — tiny particles
- **Strip-cut shredder** — long strips — can be reassembled — insufficient for sensitive data
- **Dumpster diving defence** — properly shredded documents cannot be reconstructed

---

### 2.10 Securing a SOHO Network

#### SOHO — Small Office/Home Office Network

**Change Default Router Credentials:**
- Default admin username/password publicly known for every router model
- First thing to do after setting up any router
- Use strong unique password for admin interface
- **Cybersecurity use:** Thousands of routers compromised daily through default credentials — Mirai botnet exploited this

**Update Router Firmware:**
- Router firmware contains security vulnerabilities
- Manufacturers release updates to fix them
- Check for updates in router admin interface regularly
- Enable automatic updates if available

**Change Default SSID:**
- Default SSID reveals router brand/model — helps attackers
- Use non-identifying name — not your name, address, or ISP
- Do not use "hidden SSID" — security through obscurity — still discoverable

**Use WPA3 or WPA2-AES Encryption:**
- Never use WEP or WPA
- Always select AES — never TKIP
- Strong Wi-Fi password — 12+ characters, mix of types

**Guest Network:**
- Separate Wi-Fi network for visitors and IoT devices
- Cannot access main network — isolation
- Smart TVs, cameras, doorbells on guest network — compromise cannot spread to computers
- **Cybersecurity use:** IoT devices have terrible security — isolate them on guest VLAN

**Disable WPS — Wi-Fi Protected Setup:**
- Allows device connection via PIN or button press
- WPS PIN has known vulnerability — crackable in hours (Reaver attack)
- **Always disable WPS** — no legitimate use case worth the risk

**Firewall:**
- Router has built-in firewall — ensure it is enabled
- Blocks unsolicited inbound connections
- NAT provides some protection — hides internal IPs

**DHCP Settings:**
- Limit IP range to number of devices you have
- Enable DHCP lease logging — know which device got which IP
- **DHCP reservation** for servers and printers — consistent IPs

**Port Forwarding Security:**
- Only forward ports that are absolutely necessary
- Never forward RDP (3389) directly to internet
- Use VPN instead of direct port forwarding for remote access
- **Cybersecurity use:** Exposed RDP port = constant brute force attacks

**MAC Address Filtering:**
- Only allow specific MAC addresses to connect
- Not truly secure — MAC addresses can be spoofed
- Adds friction for attackers but not a reliable defence
- High maintenance — must add every new device

**DNS Security:**
- Change DNS from ISP default to secure provider
- **Cloudflare 1.1.1.1** — privacy-focused, fast
- **OpenDNS 208.67.222.222** — includes malware filtering
- **Quad9 9.9.9.9** — blocks malicious domains automatically

---

### 2.11 Browser Security

#### Browser Security Settings

**HTTPS Everywhere:**
- Only connect to websites over HTTPS — encrypted
- Modern browsers warn about HTTP sites
- **HSTS** — HTTP Strict Transport Security — browser remembers site must be HTTPS
- Enable: always use HTTPS mode in browser settings

**Certificate Validation:**
- Browser verifies website certificate is valid and trusted
- Certificate errors = **do not proceed** — possible attack in progress
- Check: padlock icon → certificate details → verify domain matches

**Private/Incognito Mode:**
- Does NOT make you anonymous — hides from other local users only
- Does NOT hide from: ISP, employer, websites, government
- Useful for: shared computers, multiple account login, no browsing history
- **Cybersecurity use:** Private mode prevents local history but not network surveillance

**Browser Extensions Security:**
- Extensions have broad access to browser data
- Malicious extensions: steal credentials, inject ads, track browsing, redirect searches
- **Best practice:** Install only from official store, review permissions, remove unused
- **Cybersecurity use:** Malicious extensions often acquired by attackers to access millions of browsers

**Pop-up Blockers:**
- Block unwanted pop-up windows
- Malicious pop-ups: fake virus alerts, phishing pages, malware downloads
- Enable in browser settings — allow exceptions for legitimate sites only

**Clearing Browser Data:**
- Cookies — track browsing across sites
- Cache — stored web content (can contain sensitive info)
- History — visited URLs
- Saved passwords — stored credentials
- Regular clearing reduces privacy risk on shared computers
- **Cybersecurity use:** Browser caches and cookies are forensic evidence — and targets for theft

**Password Manager:**
- Store unique strong passwords for every site
- Auto-fill prevents typosquatting (typing wrong URL and entering credentials)
- Built-in: Chrome Password Manager, Firefox Lockwise, Safari Keychain
- Third-party: Bitwarden (open source, free), 1Password, LastPass
- **Cybersecurity use:** Password manager + MFA = best practice for account security

**Browser Isolation:**
- Run browser in isolated environment — malicious content cannot reach OS
- Built into Windows: Microsoft Defender Application Guard
- Separate VM for browsing — even browser compromise doesn't affect main system

#### Malicious Browser Redirects
- Browser hijacker — changes homepage, default search engine, new tab page
- All searches redirect through attacker's server — tracks and monetises searches
- Signs: unexpected homepage, strange search results, extra ads
- Fix: check extensions, check browser settings, scan for malware

#### Drive-By Downloads
- Malware downloaded automatically when visiting compromised website
- No user interaction needed — just visiting page triggers download
- Exploits: browser vulnerabilities, JavaScript vulnerabilities, plugin vulnerabilities
- **Defence:** Keep browser updated, disable Java/Flash (both EOL), use script blockers

---

### 3.1 Troubleshooting Windows

#### Common Windows Problems and Solutions

**Slow Performance:**
- Check Task Manager — identify resource-hungry processes
- Check disk space — low space causes severe slowdown
- Check for malware — run AV scan
- Check startup programs — disable unnecessary items
- Run Disk Cleanup — free up disk space
- Check for Windows updates — may include performance fixes
- Defragment HDD (not SSD) — improves file access speed

**Application Crashes:**
- Check Event Viewer — application error log
- Update the application
- Reinstall the application
- Check for conflicting software
- Check system requirements — application may need more RAM/CPU

**Blue Screen of Death (BSOD):**
- Note the stop code — search online for specific fix
- Check recently installed hardware/drivers — roll back if needed
- Run memory test — faulty RAM causes many BSODs
- Check disk — run chkdsk
- Boot into Safe Mode — if BSOD only in normal mode, driver issue likely
- Check Event Viewer — look at System log just before crash time

**System Won't Boot:**
- Check boot order in BIOS
- Try Startup Repair from Windows installation media
- Command prompt from recovery: `bootrec /fixmbr`, `bootrec /fixboot`, `bootrec /rebuildbcd`
- Check hard drive health — SMART data

**Windows Update Failures:**
- Run Windows Update Troubleshooter
- Clear update cache: stop Windows Update service → delete `C:\Windows\SoftwareDistribution` → restart service
- Check disk space — updates need free space
- Run `sfc /scannow` — repair corrupted system files
- Run `DISM /Online /Cleanup-Image /RestoreHealth` — repair Windows image

**Profile Issues:**
- User profile corrupted — cannot log in properly
- Log in as different admin account
- Copy files from corrupted profile to new profile
- Delete corrupted profile from Registry: `HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList`

---

### 3.2 Troubleshooting Mobile Devices

#### Common Mobile Issues and Solutions

**App Crashes:**
- Force stop the app — Settings → Apps → select app → Force Stop
- Clear app cache — Settings → Apps → select app → Storage → Clear Cache
- Update the app — outdated apps have bugs
- Uninstall and reinstall — fresh installation often fixes issues
- Check available storage — apps need free space to function

**Battery Drain:**
- Check battery usage — Settings → Battery — identify draining apps
- Disable background refresh for unnecessary apps
- Reduce screen brightness and timeout
- Disable unused radios — Bluetooth, GPS, NFC when not needed
- Check for rogue apps using CPU in background

**Device Overheating:**
- Remove case while charging — traps heat
- Avoid direct sunlight
- Close resource-intensive apps
- Check for malware — cryptominer causes overheating
- Battery failure can cause overheating — replace if swollen

**Storage Full:**
- Delete unused apps
- Move photos/videos to cloud (Google Photos, iCloud)
- Clear app caches — Settings → Storage
- Use streaming instead of downloading media

**Wi-Fi Issues:**
- Forget network and reconnect
- Toggle Wi-Fi off/on
- Restart router and device
- Check IP address — 169.254.x.x = DHCP failure
- Reset network settings — last resort, removes all saved Wi-Fi passwords

**Touchscreen Issues:**
- Clean screen — moisture/oils cause ghost touches
- Remove screen protector — may be causing issues
- Restart device
- Check for software update — may fix touch firmware
- Hardware failure — screen replacement needed

---

### 3.3 Troubleshooting Mobile Device Security

#### Security Issues on Mobile Devices

**Unexpected Data Usage:**
- Possible malware sending data to C2 server
- Check data usage by app — Settings → Mobile Data
- Identify unknown apps consuming data
- Run mobile AV scan
- Factory reset if malware confirmed

**Unknown Apps:**
- Check all installed apps — remove anything unrecognised
- Check for apps with device administrator privileges — Settings → Security → Device Administrators
- **Cybersecurity use:** Some malware grants itself device administrator — harder to remove

**Excessive Permissions:**
- Review app permissions regularly
- Flashlight app requesting contacts = suspicious
- Revoke unnecessary permissions
- Android: Settings → Apps → select app → Permissions
- iOS: Settings → Privacy → select permission type

**Leaked Credentials:**
- Check haveibeenpwned.com for email in data breaches
- Change passwords for compromised accounts immediately
- Enable MFA
- Review recent account activity for unauthorised access

**MDM Removal:**
- Users attempting to remove MDM profile to bypass corporate controls
- iOS: Settings → General → VPN & Device Management → attempt to remove
- MDM can detect removal attempts — alerts IT
- Some MDMs prevent removal — supervise mode (iOS)

**Jailbreak/Root Detection:**
- MDM detects compromised devices
- Common signs: Cydia installed (iOS), SuperSU present (Android)
- Policy: disconnect from corporate network, remote wipe corporate data

---

### 3.4 Troubleshooting Security Issues

#### Malware Symptoms and Response

**Ransomware:**
- Symptoms: files with strange extensions, ransom note, cannot open files
- Response:
  1. Disconnect from network immediately — stop spread
  2. Do NOT pay ransom — no guarantee of key, funds criminal
  3. Restore from clean backup
  4. Report to authorities (FBI IC3, local police)
  5. Identify infection vector — patch vulnerability

**Browser Hijacking:**
- Symptoms: homepage changed, search redirects, extra ads
- Response:
  1. Scan with Malwarebytes
  2. Check and remove browser extensions
  3. Reset browser settings to default
  4. Check hosts file for suspicious entries

**OS Update Failures:**
- Symptoms: update loops, update fails with error code
- Response:
  1. Run Windows Update Troubleshooter
  2. Clear SoftwareDistribution folder
  3. Run SFC and DISM
  4. Check disk health

**False Antivirus Alerts:**
- Fake AV software (scareware) claims computer infected — demands payment
- Never pay — legitimate AV never demands credit card to remove malware
- Response: run legitimate AV, use Malwarebytes, System Restore if needed

**Certificate Warnings:**
- Browser shows certificate error — possible attack in progress
- Do NOT proceed — especially on banking or login pages
- Check: correct URL typed, no extra characters, certificate details
- If persistent: check hosts file, check for rogue proxy, check for SSL-intercepting software

**Missing Files:**
- Could be: user error, ransomware, insider threat, disk failure
- Check Recycle Bin first
- Check file history/backup
- Run SMART test on drive
- If ransomware: restore from backup

---

## 🔑 Exam Focus Summary

**Malware Removal Steps:**
1. Identify and research
2. Quarantine (disconnect from network)
3. Disable System Restore
4. Boot Safe Mode
5. Run multiple scans
6. Remove malware
7. Check persistence mechanisms
8. Patch and update
9. Re-enable System Restore
10. Change all passwords

**Data Destruction:**
- Physical destruction = guaranteed, best for SSDs
- Degaussing = HDDs only, not SSDs
- Overwriting = good for HDDs, unreliable for SSDs
- Cryptographic erasure = best for SSDs
- Factory reset alone = NOT secure

**SOHO Security Checklist:**
- Change default credentials
- Update firmware
- Use WPA3/WPA2-AES
- Disable WPS
- Enable guest network for IoT
- Use secure DNS (1.1.1.1 or 9.9.9.9)

**Browser Security:**
- HTTPS always
- Verify certificates
- Extension permissions
- Password manager
- Private mode ≠ anonymous

**Mobile Security:**
- Encrypt device
- Enable remote wipe
- MDM for enterprise
- Official app stores only
- Review app permissions

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. Malware removal requires 10 steps — most important are: disconnect from network first, run offline scan for rootkits, check ALL persistence mechanisms after removing main malware — attackers leave multiple backdoors
2. Data destruction for SSDs requires cryptographic erasure or physical destruction — overwriting is unreliable because wear levelling leaves data in unmapped cells inaccessible to the OS
3. Disable WPS immediately on any router — the PIN brute force vulnerability (Reaver) allows cracking WPS in hours regardless of Wi-Fi password strength