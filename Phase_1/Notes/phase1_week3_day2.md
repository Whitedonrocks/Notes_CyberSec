# CompTIA A+ 220-1202 — Week 3 Day 2 Notes

---

## Videos Watched
- ✅ 1.6 The Windows Control Panel
- ✅ 1.6 Windows Settings
- ✅ 1.7 Windows Network Technologies
- ✅ 1.7 Configuring Windows Firewall
- ✅ 1.7 Windows IP Address Configuration
- ✅ 1.7 Windows Network Connections

---

## Key Concepts

### 1.6 The Windows Control Panel

#### What is Control Panel?
- The **original Windows configuration hub** — been around since Windows 1.0
- Being gradually replaced by Windows Settings (modern interface)
- Still contains many settings that Settings app does not have yet
- Open: `Win + R` → type `control` → Enter

---

#### Internet Options — `inetcpl.cpl`
The most important Control Panel section for A+ exam. Controls Internet Explorer and system-wide internet settings.

**General tab:**
- Set home page — what opens when browser starts
- Browsing history — delete cookies, cache, saved passwords
- Tabs settings — how new tabs behave
- Appearance — fonts, colours, accessibility

**Security tab:**
- Defines security zones — different trust levels for different websites
- Zones:
  - **Internet** — all websites by default (Medium-High security)
  - **Local intranet** — internal company sites (Medium security)
  - **Trusted sites** — sites you explicitly trust (Low security)
  - **Restricted sites** — sites you explicitly distrust (High security)
- Adjust security level per zone using slider
- **Cybersecurity use:** Attackers social-engineer users into adding malicious sites to Trusted Sites zone — reduces browser security

**Privacy tab:**
- Cookie settings — block/allow cookies per site
- Pop-up blocker — enable/disable, add exceptions
- InPrivate browsing settings
- Location services — allow/block sites from knowing your location

**Content tab:**
- **Certificates** — manage SSL certificates, trusted CAs
- AutoComplete — save form data and passwords
- Feeds — RSS feed settings
- Family Safety settings

**Connections tab:**
- Dial-up and VPN connections
- **LAN settings** — proxy server configuration
  - Set proxy server address and port
  - Bypass proxy for local addresses
- **Cybersecurity use:** Malware sets a rogue proxy here to intercept all browser traffic

**Programs tab:**
- Default browser settings
- Manage add-ons — browser extensions and plugins
- HTML editor settings
- **Cybersecurity use:** Malicious browser add-ons (adware, keyloggers) show up here

**Advanced tab:**
- Hundreds of granular settings
- Important security settings:
  - Enable/disable SSL 2.0, SSL 3.0, TLS 1.0, TLS 1.2, TLS 1.3
  - Warn about certificate errors
  - Check for server certificate revocation
- Reset Internet Explorer settings — returns everything to default

---

#### Other Important Control Panel Sections

**System — `sysdm.cpl`:**
- Computer name, domain, workgroup settings
- Hardware tab — Device Manager, hardware profiles
- Advanced — performance settings, environment variables, startup/recovery
- Remote — Remote Desktop settings, Remote Assistance

**User Accounts:**
- Create, modify, delete user accounts
- Change account type (Standard vs Administrator)
- Manage credentials (saved passwords)
- Set up PIN or picture password

**Network and Sharing Center:**
- View network status and active connections
- Set up new network connection
- Change adapter settings — view and configure each NIC
- Change advanced sharing settings
- **Cybersecurity use:** Shows all network adapters — including VPN and suspicious virtual adapters installed by malware

**Windows Defender Firewall:**
- Enable/disable firewall per network profile
- Allow apps through firewall
- Advanced settings — create custom rules
- Restore defaults

**Power Options:**
- Power plans: Balanced, Power Saver, High Performance
- Sleep, hibernate, shutdown settings
- Battery settings for laptops

**Programs and Features:**
- View and uninstall installed programs
- Turn Windows features on/off (IIS, Hyper-V, Telnet client etc.)
- **Cybersecurity use:** Check for unknown programs — malware often installs itself as a legitimate-looking program

**Credential Manager:**
- Stores saved usernames and passwords for websites and network resources
- Windows Credentials — domain credentials, certificate-based
- Web Credentials — browser saved passwords (older IE/Edge)
- **Cybersecurity use:** Credential Manager is a goldmine for attackers — contains saved network passwords in retrievable form

**BitLocker Drive Encryption:**
- Enable/manage BitLocker full disk encryption
- Back up recovery keys
- Suspend BitLocker for maintenance

**Device Manager:**
- All hardware and drivers in one view
- Already covered in MMC section

**Administrative Tools:**
- Shortcut to all MSC tools (Event Viewer, Services, Disk Management etc.)
- Same as what we covered in MMC

---

### 1.6 Windows Settings

#### What is Windows Settings?
- **Modern replacement for Control Panel** — cleaner, touch-friendly interface
- Open: `Win + I`
- Microsoft is gradually moving everything from Control Panel here
- Some settings still only in Control Panel — both coexist for now

#### Settings Sections — What Falls Under Each

**System:**
- Display — resolution, brightness, night light, multiple monitors
- Sound — output/input devices, volume mixer
- Notifications — app notifications, focus assist (Do Not Disturb)
- Power & sleep — screen timeout, sleep timer
- Storage — disk usage, Storage Sense (auto cleanup)
- Tablet mode — touch interface settings
- Multitasking — snap settings, virtual desktops
- About — PC name, Windows version, device specs, rename PC

**Devices (Windows 10) / Bluetooth & devices (Windows 11):**
- Bluetooth — pair/unpair devices
- Printers & scanners — add/remove, manage printers
- Mouse — pointer speed, scroll direction
- Keyboard — key repeat rate, input languages
- Pen & Windows Ink — stylus settings
- AutoPlay — what happens when USB/disc inserted
- USB — USB connection notifications

**Phone (Windows 10) / Mobile devices (Windows 11):**
- Link your Android or iPhone to Windows
- Sync notifications, messages, photos

**Network & Internet:**
- Wi-Fi — connect to networks, manage known networks, hotspot
- Ethernet — IP configuration, DNS settings
- VPN — add and connect to VPN
- Dial-up — modem connections
- Proxy — manual proxy configuration
- Status — network overview, data usage

**Personalisation:**
- Background — wallpaper, slideshow, solid colour
- Colours — accent colour, dark/light mode
- Lock screen — background, app notifications on lock screen
- Themes — save and apply visual themes
- Fonts — install and manage fonts
- Start — what appears in Start menu
- Taskbar — taskbar behaviour and icons

**Apps:**
- Apps & features — view/uninstall installed apps (modern Control Panel Programs)
- Default apps — set default browser, email, music player etc.
- Offline maps — download maps for offline use
- Apps for websites — which apps open web links
- Video playback — streaming quality settings
- Startup — manage startup apps (same as Task Manager Startup tab)

**Accounts:**
- Your info — account name, picture, Microsoft account
- Email & accounts — add work, school, or personal accounts
- Sign-in options — PIN, password, fingerprint, face, security key
- Access work or school — join domain or Azure AD
- Family & other users — add family members, child accounts, other users
- Sync your settings — sync theme, passwords across devices

**Time & Language:**
- Date & time — set timezone, sync with time server (NTP)
- Region — country format for dates, currency, numbers
- Language — add/remove display languages
- Speech — voice recognition, text-to-speech

**Gaming:**
- Xbox Game Bar — overlay shortcut (Win+G)
- Captures — screenshot and recording settings
- Game Mode — prioritise CPU/GPU for games

**Ease of Access (Windows 10) / Accessibility (Windows 11):**
- Vision — display size, high contrast, narrator, magnifier
- Hearing — closed captions, visual audio alerts
- Interaction — keyboard, mouse, eye control

**Privacy (Windows 10) / Privacy & Security (Windows 11):**
- General — advertising ID, tracking settings
- Location — allow/deny apps access to location
- Camera — allow/deny apps camera access
- Microphone — allow/deny apps microphone access
- Diagnostics — what data sent to Microsoft
- Background apps — which apps run in background
- **Cybersecurity use:** Review app permissions here — check which apps have access to camera, microphone, location

**Update & Security (Windows 10) / Windows Update (Windows 11):**
- Windows Update — check for/install updates
- Delivery Optimisation — peer-to-peer update sharing
- Windows Security — Defender antivirus settings
- Backup — File History settings
- Recovery — reset PC, go back to previous version, advanced startup
- Activation — Windows licence status

---

### 1.7 Windows Network Technologies

#### Shared Resources
- Make a **folder or printer available** on the network so other computers can access it
- **Assign a drive letter to a share** — map a network folder as if it were a local drive
  - Example: `\\server\documents` mapped as `Z:` drive
  - Users open Z: drive normally — no difference from local storage
- Sharing uses **SMB (Server Message Block)** protocol
- **Cybersecurity use:** Open network shares are a massive attack vector — ransomware spreads through accessible network shares

#### Setting Up File Sharing
1. Right-click folder → Properties → Sharing tab
2. Click Share → select users to share with → set permission (Read or Read/Write)
3. Or Advanced Sharing → more granular control
4. Share name appears as `\\ComputerName\ShareName`

#### Mapping a Network Drive
- File Explorer → This PC → Map network drive
- Assign drive letter (Z:, Y: etc.)
- Enter path: `\\server\sharename`
- Check "Reconnect at sign-in" for permanent mapping
- **Command line:** `net use Z: \\server\share`

---

#### Windows Workgroups vs Windows Domain

**Workgroups:**
- Small departments or home networks
- **Each computer maintains its own** user accounts and security database
- No central server required
- To access another computer's share: need a username/password on THAT computer
- Maximum practical size: ~20 computers
- Default for home Windows computers
- Simple setup — no expertise required

**Windows Domain:**
- **Central database** — Active Directory Domain Services (AD DS)
- One set of credentials works on ALL computers in the domain
- Centralised management — IT controls everything from one place
- Requires: Windows Server running Active Directory
- Scales to thousands of computers
- Used in: businesses, schools, enterprises

**Key Differences:**

| Feature | Workgroup | Domain |
|---|---|---|
| User accounts | Local to each PC | Central AD database |
| Login | Must exist on that PC | Works on any domain PC |
| Management | Each PC managed separately | Centralised via Group Policy |
| Scale | ~20 computers max | Thousands of computers |
| Server required | No | Yes (Windows Server) |
| Cost | Free | Windows Server licence |
| Security | Each PC controls its own | Centralised security policies |
| Setup difficulty | Easy | Complex |

**Cybersecurity use:** In a domain, compromising one Domain Controller = compromising every computer in the organisation. In a workgroup, you compromise one PC at a time.

---

#### Sharing Printers
- Share a printer so all network users can print to it
- Right-click printer → Printer properties → Sharing tab → Share this printer
- Give it a share name (e.g. "OfficeHP")
- Other computers: Add printer → network printer → browse for `\\ComputerName\OfficeHP`
- Or use a **print server** — dedicated device manages printing
- **Cybersecurity use:** Network printers are often overlooked in security audits — unpatched printer firmware = network access point

---

### 1.7 Configuring Windows Firewall

#### Windows Defender Firewall
- Built into Windows — **your firewall should always be enabled**
- Filters incoming and outgoing traffic by port, protocol, and application
- Three network profiles:
  - **Domain** — when connected to a Windows domain network
  - **Private** — home or trusted network
  - **Public** — coffee shop, airport, untrusted network (most restrictive)

#### How to Create a New Firewall Rule
1. Open **Windows Defender Firewall with Advanced Security** (`wf.msc`)
2. Click **Inbound Rules** (traffic coming in) or **Outbound Rules** (traffic going out)
3. Click **New Rule** in the right panel
4. Choose rule type:
   - **Program** — block/allow specific application
   - **Port** — block/allow specific port number
   - **Predefined** — use built-in Windows rule templates
   - **Custom** — full control over all settings
5. Set the port number or program path
6. Choose action: **Allow**, **Allow if secure**, or **Block**
7. Choose which profiles: Domain, Private, Public
8. Name the rule → Finish

**Example — allow a web server on port 8080:**
```
Rule type: Port
Protocol: TCP
Port: 8080
Action: Allow the connection
Profile: Private
Name: Allow Web Server 8080
```

**Linux equivalent (UFW):**
```bash
sudo ufw allow 8080/tcp
sudo ufw status verbose
```

**Cybersecurity use:** Attackers disable Windows Firewall after gaining access. Always check firewall status on compromised systems. Outbound rules are often ignored — malware exploits this to phone home.

---

### 1.7 Windows IP Address Configuration

#### DHCP — Dynamic Host Configuration Protocol
- **Automatically assigns** IP address, subnet mask, gateway, DNS server
- Device sends DHCP Discover → server assigns address via DORA process
- Default for most Windows computers
- Configure: Network adapter → Properties → IPv4 → "Obtain an IP address automatically"

#### Static IP Configuration
- Manually set IP address, subnet mask, default gateway, DNS server
- Used for: servers, printers, routers — devices that need consistent address
- Configure: Network adapter → Properties → IPv4 → "Use the following IP address"
- Example static config:
```
IP Address:      192.168.1.100
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.1
DNS Server:      8.8.8.8
Alt DNS:         8.8.4.4
```

#### APIPA — Automatic Private IP Addressing
- Assigned when **DHCP server cannot be reached**
- Range: **169.254.0.0/16** (169.254.x.x)
- Device randomly picks address, uses ARP to verify it's unique
- Can communicate with other APIPA devices on same network segment
- Cannot reach internet — no gateway assigned
- **Diagnosis:** Seeing 169.254.x.x = DHCP problem
  - Check: DHCP server running? Network cable connected? Switch working?

#### IPv4 vs IPv6 Configuration
- Both can be configured simultaneously — **dual stack**
- IPv6 auto-configuration: **SLAAC** (Stateless Address Autoconfiguration)
  - Device generates its own IPv6 address from network prefix + MAC address
  - No DHCP server needed for basic IPv6

#### DNS Configuration
- **Primary DNS** — first server queried
- **Alternate DNS** — used if primary fails
- Common public DNS servers:
  - Google: `8.8.8.8` and `8.8.4.4`
  - Cloudflare: `1.1.1.1` and `1.0.0.1`
  - OpenDNS: `208.67.222.222`
- **Cybersecurity use:** Changing DNS to a malicious server = DNS hijacking — all domain lookups redirected through attacker's server

---

### 1.7 Windows Network Connections

#### Network Setup
- **Network and Sharing Center** → Set up a new connection or network
- Types of connections:
  - Connect to internet (Wi-Fi, broadband)
  - Set up a new network (configure router)
  - Connect to a workplace (VPN)
  - Set up dial-up connection

#### Managing Network Adapters
- Control Panel → Network and Sharing Center → Change adapter settings
- Or: Settings → Network & Internet → Advanced network settings
- Shows all network adapters: Ethernet, Wi-Fi, VPN, virtual adapters
- Right-click adapter → Properties → configure IP, DNS etc.
- Right-click → Disable — disable an adapter entirely

#### SSID — Service Set Identifier
- The **name of a Wi-Fi network** — what you see when scanning for Wi-Fi
- Each wireless network has a unique SSID
- Can be hidden (not broadcast) but still discoverable with wireless tools
- Connect to Wi-Fi: click SSID → enter password → connect
- **Cybersecurity use:** Evil twin attack — attacker creates a Wi-Fi network with the same SSID as a legitimate network → users connect to attacker's network instead

#### Wi-Fi Settings
- **Forget network** — remove saved Wi-Fi credentials
- **Properties** — set as metered connection, auto-connect settings
- **Network profile:** Public or Private — affects firewall rules
- Always set **public Wi-Fi as Public profile** — applies stricter firewall rules

---

#### VPN — Virtual Private Network (Explained Simply)

**The Problem VPN Solves:**
Imagine you are working from home and need to access your company's internal file server. The file server is on the company's private network — not accessible from the internet.

**Without VPN:**
```
Your Home → Internet → ??? → Company File Server
                       ↑
               Can't reach it — private network
```

**With VPN:**
```
Your Home → Internet → [Encrypted Tunnel] → VPN Server at Company → File Server ✅
```

**How it works step by step:**
1. You install VPN client software on your laptop
2. You connect to the company's VPN server (authenticate with username/password)
3. VPN creates an **encrypted tunnel** through the internet
4. Your laptop gets a **virtual IP address** on the company's network
5. Now you can access the file server as if you were physically in the office
6. All traffic between you and the company is **encrypted** — even your ISP cannot see it

**VPN in Windows:**
- Settings → Network & Internet → VPN → Add a VPN connection
- Enter: VPN provider, server address, VPN type, login credentials
- Connect/disconnect from system tray

**VPN Types:**
| Type | Use Case |
|---|---|
| **Client-to-Site** | Individual user connecting to company network remotely |
| **Site-to-Site** | Two entire office networks connected permanently |
| **Split Tunnel** | Only company traffic goes through VPN, personal traffic goes direct |
| **Full Tunnel** | ALL traffic goes through VPN — more secure |

**VPN Protocols:**
| Protocol | Description |
|---|---|
| **OpenVPN** | Open source, very secure, cross-platform (what TryHackMe uses!) |
| **WireGuard** | Modern, fast, simple, increasingly popular |
| **L2TP/IPSec** | Common, built into Windows |
| **PPTP** | Old, fast but weak encryption — avoid |
| **IKEv2** | Fast reconnection, good for mobile |

**Cybersecurity use:**
- VPN credentials are a top attack target — brute forced or phished
- Split tunnelling can leak traffic outside the encrypted tunnel
- Rogue VPN apps can steal all your traffic — only use trusted VPN software
- TryHackMe uses OpenVPN to connect you to their lab network — exactly what you've been doing!

---

## Terminal Practice + Expected Output

### Check Network Configuration
```bash
ip a
```
**Expected output:**
```
2: enp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP>
    inet 192.168.31.157/24 brd 192.168.31.255 scope global
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP>
    inet 192.168.1.71/24 brd 192.168.1.255 scope global
```

### Check Default Gateway
```bash
ip r
```
**Expected output:**
```
default via 192.168.1.1 dev wlp3s0 proto dhcp
default via 192.168.31.1 dev enp4s0 proto dhcp
192.168.1.0/24 dev wlp3s0 proto kernel scope link
```

### Check DNS Settings
```bash
resolvectl status | head -20
```
**Expected output:**
```
Global
       Protocols: +LLMNR +mDNS -DNSOverTLS DNSSEC=no/unsupported
resolv.conf mode: stub

Link 2 (enp4s0)
    Current Scopes: DNS
         Protocols: +DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no
Current DNS Server: 192.168.31.1
       DNS Servers: 192.168.31.1
```

### Check Ubuntu Firewall Status
```bash
sudo ufw status verbose
```
**Expected output:**
```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip
```
- `deny (incoming)` = blocks all incoming connections by default ✅
- `allow (outgoing)` = allows all outgoing connections ✅

### Check Network Connections
```bash
nmcli connection show
```
**Expected output:**
```
NAME                UUID   TYPE      DEVICE
YourWiFiNetwork     xxxx   wifi      wlp3s0
Wired connection 1  xxxx   ethernet  enp4s0
```

---

## 🔑 Additional Important Concepts You Missed

### Network Discovery
- Windows setting that controls whether your PC is visible to other network computers
- **On** = other computers can see your PC and shared resources
- **Off** = your PC is invisible on the network
- Set per profile: Private (on), Public (off)
- Configure: Network and Sharing Center → Advanced sharing settings

### Metered Connection
- Mark a network connection as metered — tells Windows it has a data limit
- Windows will: pause Windows Update downloads, reduce background sync
- Important for mobile hotspot connections — prevents unexpected data usage
- Set: Settings → Network & Internet → Wi-Fi → your network → Properties → Metered

### HomeGroup (Removed in Windows 10 1803)
- Was a simple home file sharing feature
- Removed — replaced by regular network sharing
- If you see HomeGroup in old notes/exams — it no longer exists

### Proxy Server in Windows
- Settings → Network & Internet → Proxy
- Manual proxy: enter server address and port
- Automatic proxy: enter PAC (Proxy Auto-Config) file URL
- **Cybersecurity use:** Check proxy settings on suspicious machines — malware often sets a proxy to intercept traffic

### Network Reset
- Settings → Network & Internet → Advanced → Network Reset
- Reinstalls all network adapters and resets all networking components to defaults
- Last resort for unfixable network issues
- **Warning:** Removes all saved Wi-Fi passwords and VPN configurations

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. VPN creates an encrypted tunnel through the internet — your laptop gets a virtual IP on the remote network as if physically there — this is exactly what TryHackMe OpenVPN does
2. APIPA (169.254.x.x) always means DHCP failed — seeing this address = network/DHCP problem to investigate
3. Workgroup vs Domain — workgroup is each PC for itself, domain is centralised control via Active Directory — domain compromise = all PCs compromised