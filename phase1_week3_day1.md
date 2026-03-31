# CompTIA A+ 220-1202 — Week 3 Day 1 Notes

---

## Videos Watched
- ✅ 1.4 Task Manager
- ✅ 1.4 The Microsoft Management Console
- ✅ 1.4 Additional Windows Tools
- ✅ 1.5 Windows Command Line Tools
- ✅ 1.5 The Windows Network Command Line

---

## Key Concepts

### 1.4 Task Manager

**Open with:** `Ctrl + Shift + Esc` or `Ctrl + Alt + Del` → Task Manager or right-click taskbar

Task Manager is Windows' built-in system monitor — shows everything happening on your system in real time.

#### Tabs Overview

**Processes:**
- View **all running processes** — apps, background processes, Windows processes
- Shows: CPU%, RAM usage, Disk I/O, Network usage per process
- Right-click any process → End Task to kill it
- **Cybersecurity use:** Malware shows up here — look for suspicious process names, high CPU/RAM usage, unknown processes

**Performance:**
- Real-time **statistical views** of system resources
- CPU usage graph, RAM usage, Disk I/O, Network throughput
- Shows: CPU speed, cores, RAM slots used, uptime
- **Cybersecurity use:** Unexplained 100% CPU usage = possible cryptominer malware

**Users:**
- Shows **who is connected** to the system
- Multiple users can be logged in simultaneously (RDP sessions)
- Can disconnect or sign out users
- **Cybersecurity use:** Unknown users connected via RDP = unauthorised access

**Services:**
- View and manage **hundreds of background processes**
- Start, stop, or restart services
- Link to Services console for full management
- **Cybersecurity use:** Malware often installs itself as a Windows service for persistence

**Startup:**
- Manage which **programs start automatically** with Windows login
- Enable or disable startup items
- Shows impact rating: Low, Medium, High, Not measured
- **Cybersecurity use:** Malware adds itself to startup — check here for unknown entries

#### Linux Equivalent
```bash
htop          # interactive process viewer
top           # basic process viewer
systemctl     # manage services
ss -tuln      # network connections
```

---

### 1.4 The Microsoft Management Console (MMC)

#### What is MMC?
- **MMC = Microsoft Management Console**
- A framework that lets you **build your own custom admin console**
- Run: `mmc.exe`
- Add "snap-ins" — individual management tools — into one window
- Think of it as a toolbox where you pick which tools to include
- IT admins create custom MMC consoles with only the tools they need

#### MMC Snap-ins (All the Tools)

---

**Event Viewer — `eventvwr.msc`**
- **Central event consolidation** — logs everything that happens on Windows
- Categories:
  - **Application** — app crashes, errors, warnings
  - **Security** — login attempts, privilege use, policy changes
  - **System** — hardware events, driver failures, OS events
- Event levels: Information, Warning, Error, Critical
- **Cybersecurity use:** Security log shows every login attempt — successful and failed. Look here after a suspected breach. Attackers often clear event logs to cover tracks — a cleared log IS itself a suspicious event.

---

**Disk Management — `diskmgmt.msc`**
- Manage all **disk operations** from one GUI
- Tasks: create/delete partitions, format drives, assign drive letters, extend/shrink volumes, convert MBR↔GPT
- Shows all physical drives and their partitions visually
- **Cybersecurity use:** Used in forensics to examine drive layout before imaging

---

**Task Scheduler — `taskschd.msc`**
- Schedule applications or scripts to run automatically
- Includes **predefined schedules** (daily, weekly, at login, at startup)
- Can trigger on: time, event, system idle, user login
- Used by: Windows Update, antivirus scans, backup jobs
- **Cybersecurity use:** Malware uses Task Scheduler for persistence — scheduled task runs malware every hour or at every login. Always check Task Scheduler on compromised machines.

---

**Device Manager — `devmgmt.msc`**
- The OS **does not know how to talk directly to hardware**
- **Device drivers** translate between OS and hardware
- Device Manager manages all installed device drivers
- Shows: all hardware, driver status, driver version
- Yellow exclamation = driver problem
- Tasks: update drivers, roll back drivers, disable devices, scan for hardware changes
- **Cybersecurity use:** Malicious drivers (rootkits) can hide from Device Manager — kernel-level attack

---

**Certificate Manager — `certmgr.msc`**
- View **user certificates and trusted certificates**
- Manages: personal certificates, trusted root CAs, intermediate CAs
- Used by: HTTPS, email encryption (S/MIME), code signing, VPN
- **Cybersecurity use:** Attackers install rogue root certificates to perform man-in-the-middle attacks on HTTPS traffic. Check trusted root CAs for unknown entries.

---

**Local Users and Groups — `lusrmgr.msc`**
- Manage local user accounts and groups on the computer

**Built-in Users:**
| Account | Description |
|---|---|
| **Administrator** | Full system access — disabled by default in Windows 10/11 |
| **Guest** | Limited access — disabled by default |
| **Regular User** | Standard user — limited privileges |

**Built-in Groups:**
| Group | Members / Purpose |
|---|---|
| **Administrators** | Full control of the computer |
| **Users** | Standard users — limited rights |
| **Backup Operators** | Can backup/restore files regardless of permissions |
| **Remote Desktop Users** | Can connect via RDP |
| **Power Users** | Legacy group — limited admin rights |
| **Guests** | Very limited access |

- **Cybersecurity use:** Attackers create hidden admin accounts for backdoor access. Check for unknown users in Administrators group after suspected breach.

---

**Performance Monitor — `perfmon.msc`**
- Gather **long-term statistics** about system performance
- Unlike Task Manager (real-time), Performance Monitor records over time
- OS metrics: CPU, RAM, Disk, Network — graphed over hours/days
- Create **Data Collector Sets** — scheduled monitoring sessions
- **Cybersecurity use:** Baseline normal performance → detect anomalies that indicate intrusion or malware

---

**Group Policy Editor — `gpedit.msc`**
- **Centrally manage** users and computer settings
- Local Group Policy Editor — applies to single computer
- Available in: Windows Pro and above (NOT Home)

**Group Policy Management Console — `gpmc.msc`**
- Manages Group Policy across entire **Active Directory domain**
- **Integrated with Active Directory**
- Apply policies to thousands of computers simultaneously
- **Cybersecurity use:** Most powerful tool in Windows administration — and most dangerous if compromised

---

### 1.4 Additional Windows Tools

#### System Information — `msinfo32.exe`
- Complete **system overview** in one place
- Shows:
  - **Hardware Resources** — IRQs, memory addresses, DMA channels
  - **Components** — display, storage, network, sound details
  - **Software Environment** — running tasks, startup programs, drivers, environment variables
- Useful for: tech support, hardware inventory, troubleshooting
- Export as text file for documentation
- **Cybersecurity use:** Full hardware and software inventory — useful for asset management and forensic documentation

---

#### Resource Monitor — `resmon.exe`
- **Detailed real-time view** of performance — more detail than Task Manager
- Categories:
  - **Overview** — summary of all resources
  - **CPU** — per-process CPU usage, services
  - **Memory** — physical memory map, per-process RAM
  - **Disk** — read/write activity per file, per process
  - **Network** — per-process network connections, listening ports
- **Cybersecurity use:** Network tab shows exactly which process is making which network connection — find malware phoning home

---

#### System Configuration — `msconfig.exe`
- Manage **boot process, startup, and services**
- Tabs:
  - **General** — normal, diagnostic, or selective startup
  - **Boot** — boot options, safe mode, timeout
  - **Services** — enable/disable Windows services at startup
  - **Startup** — links to Task Manager startup tab (Windows 10+)
  - **Tools** — shortcut launcher for other admin tools
- **Diagnostic startup** — minimal drivers, isolate startup problems
- **Cybersecurity use:** Safe mode configuration — boot with minimal services to bypass malware that loads at startup

---

#### Disk Cleanup — `cleanmgr.exe`
- Find **unused or unneeded files** to free up disk space
- Categories to clean:
  - Temporary Internet files
  - Downloaded program files
  - Recycle Bin
  - Temporary files
  - System error memory dumps
  - Windows Update cleanup (run as admin)
- Select categories → calculates space savings → delete
- **Cybersecurity use:** Temporary files and browser cache contain forensic evidence — attackers run Disk Cleanup to destroy evidence

---

#### Disk Defragmenter — `dfrgui.exe`
- **Disk defragmentation** — moves file fragments so they are contiguous
- HDDs store files in fragments scattered across the disk
- Defrag brings fragments together → faster read times
- **NOT necessary for SSDs** — SSDs don't benefit and excess writes reduce lifespan
- Windows automatically defrags HDDs weekly
- **Cybersecurity use:** Defragmentation destroys forensic evidence by moving file fragments

---

#### Registry Editor — `regedit.exe`
- **Windows Registry** — central database storing ALL configuration settings
- Used by: almost every application, Windows itself, hardware drivers

**Registry Structure:**
| Hive | Contents |
|---|---|
| **HKEY_LOCAL_MACHINE (HKLM)** | Hardware and system-wide settings |
| **HKEY_CURRENT_USER (HKCU)** | Settings for currently logged-in user |
| **HKEY_CLASSES_ROOT (HKCR)** | File associations and COM objects |
| **HKEY_USERS (HKU)** | Settings for all user profiles |
| **HKEY_CURRENT_CONFIG (HKCC)** | Current hardware profile |

**SAM — Security Account Manager:**
- Stored in registry: `HKLM\SAM`
- Contains **hashed passwords** for all local user accounts
- Protected by Windows — cannot be accessed while OS is running
- **Cybersecurity use:** SAM database is the primary target for credential harvesting. Tools like Mimikatz dump password hashes from SAM. Attackers copy SAM file from offline system for offline cracking.

**Common malware registry persistence locations:**
```
HKCU\Software\Microsoft\Windows\CurrentVersion\Run
HKLM\Software\Microsoft\Windows\CurrentVersion\Run
HKLM\Software\Microsoft\Windows\CurrentVersion\RunOnce
```
These keys run programs automatically at login — always check here on compromised systems.

---

### 1.5 Windows Command Line Tools

#### Privileges
- Not all users can run all commands
- Some commands require **Administrator** — right-click Command Prompt → "Run as administrator"
- **UAC** prompts for elevation when needed

#### Opening Command Prompt
- Search "cmd" → Run as administrator
- `Win + R` → type `cmd`
- PowerShell: `Win + X` → Windows Terminal (Admin)

---

#### Essential File and Directory Commands

| Command | Description | Example |
|---|---|---|
| `dir` | List directory contents | `dir C:\Users` |
| `cd` | Change directory | `cd C:\Windows\System32` |
| `cd ..` | Go up one directory | `cd ..` |
| `md` / `mkdir` | Create directory | `mkdir C:\TestFolder` |
| `rd` / `rmdir` | Remove directory | `rmdir C:\TestFolder` |
| `del` | Delete file | `del file.txt` |
| `copy` | Copy file | `copy file.txt D:\` |
| `move` | Move file | `move file.txt D:\` |
| `ren` | Rename file | `ren oldname.txt newname.txt` |
| `type` | Display file contents | `type file.txt` |
| `cls` | Clear screen | `cls` |
| `exit` | Close command prompt | `exit` |

---

#### System Commands

| Command | Description | Linux Equivalent |
|---|---|---|
| `hostname` | Display computer name | `hostname` |
| `whoami` | Display current user | `whoami` |
| `systeminfo` | Full system information | `uname -a` + `lscpu` |
| `tasklist` | List running processes | `ps aux` |
| `taskkill /PID xxxx /F` | Kill process by PID | `kill -9 xxxx` |
| `sc query` | List services | `systemctl list-units` |
| `sc start servicename` | Start a service | `systemctl start service` |
| `sc stop servicename` | Stop a service | `systemctl stop service` |
| `sfc /scannow` | System File Checker — repair corrupt system files | `sudo apt install --reinstall` |
| `chkdsk C: /f /r` | Check disk for errors and fix | `sudo fsck /dev/sda1` |
| `shutdown /s /t 0` | Shutdown immediately | `sudo shutdown now` |
| `shutdown /r /t 0` | Restart immediately | `sudo reboot` |
| `gpupdate /force` | Force Group Policy update | N/A |
| `gpresult /r` | Show applied Group Policy | N/A |

---

#### Disk Commands

| Command | Description | Notes |
|---|---|---|
| `diskpart` | Disk partitioning tool | Powerful — be careful |
| `format C:` | Format a drive | Destructive — use carefully |
| `defrag C:` | Defragment a drive | HDD only |
| `robocopy` | Robust file copy | Better than xcopy for large transfers |
| `xcopy` | Extended copy | Copies directories recursively |

**diskpart example — list drives:**
```cmd
diskpart
list disk
list volume
exit
```

---

#### File Permissions Commands

| Command | Description |
|---|---|
| `icacls file.txt` | View file permissions |
| `icacls file.txt /grant User:F` | Grant full control to User |
| `attrib +h file.txt` | Hide a file |
| `attrib -h file.txt` | Unhide a file |
| `attrib +r file.txt` | Make file read-only |

**Cybersecurity use:** `attrib +h +s` hides files and marks them as system files — used by malware to hide payloads. Check with `dir /a` to show all files including hidden.

---

#### Useful Diagnostic Commands

| Command | Description | Linux Equivalent |
|---|---|---|
| `driverquery` | List all installed drivers | `lsmod` |
| `msinfo32` | System information | `sudo lshw` |
| `winver` | Windows version popup | `lsb_release -a` |
| `eventvwr` | Event Viewer | `sudo journalctl` |
| `mmc` | Management Console | N/A |
| `regedit` | Registry Editor | N/A |
| `msconfig` | System Configuration | N/A |
| `resmon` | Resource Monitor | `htop` |

---

### 1.5 Windows Network Command Line

#### ipconfig — IP Configuration

| Command | Description | Linux Equivalent |
|---|---|---|
| `ipconfig` | Show IP, subnet, gateway for all adapters | `ip a` |
| `ipconfig /all` | Full details — MAC, DNS, DHCP server | `ip a` + `ip r` |
| `ipconfig /release` | Release DHCP lease — give up IP address | `sudo dhclient -r` |
| `ipconfig /renew` | Request new IP from DHCP | `sudo dhclient` |
| `ipconfig /flushdns` | Clear DNS cache | `sudo systemd-resolve --flush-caches` |
| `ipconfig /displaydns` | Show DNS cache contents | `sudo systemd-resolve --statistics` |

**Most useful troubleshooting sequence:**
```cmd
ipconfig /release
ipconfig /flushdns
ipconfig /renew
ipconfig /all
```

---

#### ping — Test Connectivity

| Command | Description | Linux Equivalent |
|---|---|---|
| `ping google.com` | Test connectivity (sends 4 packets) | `ping -c 4 google.com` |
| `ping -t google.com` | Continuous ping until stopped (Ctrl+C) | `ping google.com` |
| `ping -n 10 google.com` | Send 10 packets | `ping -c 10 google.com` |
| `ping -l 1000 google.com` | Send 1000 byte packets | `ping -s 1000 google.com` |
| `ping 127.0.0.1` | Ping loopback — test TCP/IP stack | `ping -c 4 127.0.0.1` |

---

#### tracert — Trace Route

| Command | Description | Linux Equivalent |
|---|---|---|
| `tracert google.com` | Show every router hop to destination | `traceroute google.com` |
| `tracert -d google.com` | Don't resolve hostnames — faster | `traceroute -n google.com` |

**Reading tracert output:**
```
1    1ms   192.168.1.1      ← your router
2   10ms   10.x.x.x         ← ISP first hop
3   15ms   203.x.x.x        ← ISP backbone
...
10  50ms   142.250.64.46    ← google.com destination
```
- `* * *` = router not responding to ICMP — doesn't mean broken
- Sudden latency jump at a hop = bottleneck at that router

---

#### netstat — Network Statistics

| Command | Description | Linux Equivalent |
|---|---|---|
| `netstat` | Show active connections | `ss` |
| `netstat -a` | All connections + listening ports | `ss -a` |
| `netstat -n` | Show numerical addresses (no DNS lookup) | `ss -n` |
| `netstat -o` | Show PID for each connection | `ss -p` |
| `netstat -b` | Show executable for each connection (admin) | `ss -p` |
| `netstat -an` | All connections, numerical | `ss -tuln` |
| `netstat -ano` | All connections, numerical, with PID | `ss -tulnp` |

**Most useful — find what process owns a connection:**
```cmd
netstat -ano | findstr :443
tasklist | findstr 1234    ← use PID from above
```
**Linux equivalent:**
```bash
ss -tulnp | grep :443
```
**Cybersecurity use:** `netstat -ano` reveals malware network connections — look for unexpected outbound connections to unknown IPs on unusual ports.

---

#### nslookup — DNS Lookup

| Command | Description | Linux Equivalent |
|---|---|---|
| `nslookup google.com` | Basic DNS lookup | `dig google.com` |
| `nslookup -type=MX google.com` | Query MX records | `dig google.com MX` |
| `nslookup -type=AAAA google.com` | Query IPv6 address | `dig google.com AAAA` |
| `nslookup google.com 8.8.8.8` | Query using specific DNS server | `dig @8.8.8.8 google.com` |

---

#### net — Network Resource Commands

| Command | Description |
|---|---|
| `net user` | List all local user accounts |
| `net user username password /add` | Create new user |
| `net user username /delete` | Delete user |
| `net localgroup administrators username /add` | Add user to Administrators |
| `net share` | List shared folders |
| `net use Z: \\server\share` | Map network drive |
| `net view` | List computers on network |
| `net start servicename` | Start a service |
| `net stop servicename` | Stop a service |
| `net accounts` | Show password policy |

**Cybersecurity use:** `net user administrator /active:yes` enables the hidden admin account — used by attackers to create persistence. `net localgroup administrators` lists all admin accounts — check for unknown entries.

---

#### arp — Address Resolution Protocol

| Command | Description | Linux Equivalent |
|---|---|---|
| `arp -a` | Display ARP cache — IP to MAC mappings | `arp -a` or `ip neigh` |
| `arp -d *` | Clear ARP cache | `sudo ip neigh flush all` |

**Cybersecurity use:** ARP cache poisoning — check `arp -a` for duplicate MAC addresses (two IPs sharing same MAC = ARP spoofing attack in progress).

---

#### pathping — Combined ping + tracert

| Command | Description |
|---|---|
| `pathping google.com` | Tests each hop like tracert but also measures packet loss at each hop |

- More detailed than tracert alone
- Shows packet loss percentage at each router
- Takes longer to complete (tests each hop multiple times)
- **Linux equivalent:** `mtr google.com`

---

## Windows vs Linux Command Cheatsheet

| Task | Windows | Linux |
|---|---|---|
| Show IP address | `ipconfig` | `ip a` |
| Show all network details | `ipconfig /all` | `ip a` + `ip r` |
| Flush DNS | `ipconfig /flushdns` | `sudo systemd-resolve --flush-caches` |
| Ping | `ping google.com` | `ping -c 4 google.com` |
| Trace route | `tracert google.com` | `traceroute google.com` |
| Show connections | `netstat -ano` | `ss -tulnp` |
| DNS lookup | `nslookup google.com` | `dig google.com` |
| ARP cache | `arp -a` | `ip neigh` |
| Combined ping+trace | `pathping google.com` | `mtr google.com` |
| List users | `net user` | `cat /etc/passwd` |
| List processes | `tasklist` | `ps aux` |
| Kill process | `taskkill /PID x /F` | `kill -9 x` |
| System info | `systeminfo` | `uname -a` |
| Repair system files | `sfc /scannow` | `sudo apt install --reinstall` |
| Check disk | `chkdsk C: /f /r` | `sudo fsck /dev/sda1` |

---

## Terminal Practice + Expected Output

### Check Active Network Connections (Linux equivalent of netstat -ano)
```bash
ss -tulnp
```
**Expected output:**
```
Netid  State   Recv-Q  Send-Q  Local Address:Port  Peer Address:Port
tcp    LISTEN  0       128     0.0.0.0:22          0.0.0.0:*     users:(("sshd",pid=1234))
tcp    LISTEN  0       5       127.0.0.1:631       0.0.0.0:*     users:(("cupsd",pid=567))
```
- Port 631 = CUPS (your printer service) ✅
- Port 22 = SSH if enabled

---

### Check ARP Cache
```bash
ip neigh
```
**Expected output:**
```
192.168.1.1 dev enp4s0 lladdr aa:bb:cc:dd:ee:ff REACHABLE
192.168.1.1 dev wlp3s0 lladdr aa:bb:cc:dd:ee:ff REACHABLE
```
- Shows your router's MAC address
- Two entries because you have both ethernet and Wi-Fi connected

---

### DNS Lookup (nslookup equivalent)
```bash
dig google.com +short
```
**Expected output:**
```
142.250.64.46
```

---

## 🔑 Additional Important Concepts You Missed

### PowerShell vs Command Prompt
- **Command Prompt (cmd.exe)** — old, basic, batch scripting
- **PowerShell** — modern, object-oriented, much more powerful
- PowerShell can do everything cmd can + much more
- Uses **cmdlets** — verb-noun format: `Get-Process`, `Stop-Service`, `Get-NetIPAddress`
- **Cybersecurity use:** Most modern Windows malware and pen testing tools use PowerShell — AMSI (Antimalware Scan Interface) monitors PowerShell commands

### Windows Firewall from Command Line
```cmd
netsh advfirewall show allprofiles     ← show firewall status
netsh advfirewall set allprofiles state off  ← disable firewall (admin)
netsh advfirewall firewall add rule name="Test" protocol=TCP dir=in localport=8080 action=allow
```
**Cybersecurity use:** Attackers disable Windows Firewall as first step after gaining access

### Environment Variables
```cmd
set                          ← list all environment variables
echo %USERPROFILE%           ← show user profile path
echo %SystemRoot%            ← show Windows directory (usually C:\Windows)
echo %PATH%                  ← show executable search path
```
**Linux equivalent:**
```bash
env                          # list all environment variables
echo $HOME
echo $PATH
```

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. SAM database contains hashed local passwords — Mimikatz dumps these. Check regedit Run keys for malware persistence
2. netstat -ano (Windows) / ss -tulnp (Linux) shows every network connection with the owning process — essential for finding malware phoning home
3. Task Scheduler is a common malware persistence mechanism — always check scheduled tasks on a compromised system