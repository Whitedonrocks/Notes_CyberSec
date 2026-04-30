# CompTIA A+ 220-1201 — Week 2 Day 6 Notes

---

## Videos Watched
- ✅ 5.4 Troubleshooting Mobile Devices
- ✅ 5.5 Troubleshooting Networks
- ✅ 5.6 Troubleshooting Printers

---

## Key Concepts

### 5.4 Troubleshooting Mobile Devices

#### Poor Battery Health
- Battery capacity degrades over time — holds less charge per cycle
- **Symptoms:** Short battery life, unexpected shutdowns at 20-30%
- **Solutions:**
  - Replace aging battery — most phones allow replacement
  - **Bad reception** drains battery fast — phone constantly searches for signal
  - Disable unnecessary features: Bluetooth, GPS, Wi-Fi, background refresh
  - Reduce screen brightness — display is the biggest power draw
- Check battery health: iOS Settings → Battery → Battery Health, Android: Settings → Battery

---

#### Swollen Battery
- **Buildup of gas** inside the battery cell due to chemical breakdown
- Causes battery to physically expand — screen lifts, case bulges
- **Very dangerous — do NOT:**
  - Puncture or open the battery packet/container
  - Continue using the device
  - Charge a swollen battery
- **Faulty battery** from manufacturing defect or overcharging
- Device can be permanently damaged by pressure from swollen battery
- **Action:** Power off immediately, take to a professional for safe disposal
- **Cybersecurity use:** Lithium battery fires have been used to destroy evidence — batteries are not trivial

---

#### Broken Screen
- **First action:** Back up your data immediately — screen may stop working entirely
- Replace the screen — professional repair recommended (glass is sharp)
- Use screen protector in future to prevent cracks
- Temporary fix: mirror screen to TV via HDMI adapter or screen cast
- **Data recovery:** Even with broken screen, USB debugging + ADB (Android Debug Bridge) can recover data

---

#### Improper Charging
- **Check everything in the charging process:**
  - Cable — damaged, frayed, or cheap third-party cables
  - Interface — charging port physically damaged or dirty
  - Power adapter — check wattage matches device requirement
  - Wall outlet — try a different outlet
- **Verify the power adapter** — wrong wattage can charge slowly or not at all
- USB-C PD (Power Delivery) — adapter must support correct voltage/wattage
- **Cybersecurity use:** Juice jacking — public USB charging stations can be compromised to steal data or install malware. Use a USB data blocker or bring your own charger

---

#### Poor or No Connectivity

**Cellular:**
- Check signal bars — move to area with better coverage
- Toggle airplane mode off/on — resets cellular radio
- Check if data is enabled in settings
- Check if roaming is enabled (if travelling)
- SIM card may be loose — reseat it
- Contact carrier — account may be suspended

**Wi-Fi:**
- Forget network and reconnect
- Toggle Wi-Fi off/on
- Check if correct network is selected
- Check if IP address assigned (169.254.x.x = DHCP failed)
- Restart router and phone
- Check if MAC address filtering is blocking device

---

#### Liquid Damage
- Many phones have a **Liquid Contact Indicator (LCI)**
  - Small sticker that turns red/pink when exposed to liquid
  - Located in SIM tray slot or under battery
  - Used to void warranty claims
- **Immediate actions:**
  1. Power down the phone immediately — do not charge
  2. Remove the case
  3. Remove SIM and SD cards
  4. Remove back cover and battery (if removable)
  5. Do NOT use rice — not effective, wastes time
  6. Use silica gel packets or a professional drying service
- **Cybersecurity use:** Liquid damage can destroy forensic evidence on a device — intentional water damage is a data destruction method

---

#### Overheating
- Phone will **automatically shut down** to prevent damage
- Common causes:
  - Charging and heavy use simultaneously (gaming while charging)
  - Charging/discharging the battery rapidly
  - Faulty battery or charging cable
  - Excessive background app activity
- **Solutions:** Remove case while charging, check app usage, avoid direct sunlight
- Check battery temperature: Android — AccuBattery app, iOS — Settings → Battery

---

#### Digitizer Issues
- Touchscreen completely black or not responding to input
- Digitizer is the touch-sensitive layer on top of the display
- **Android:** Restart device — often resolves temporary digitizer glitch
- **Apple iOS:** Force restart (volume up, volume down, hold side button)
- If physical damage — digitizer layer may need replacement (separate from LCD)

---

#### Physically Damaged Ports
- USB-C, Lightning, or Micro-USB port physically bent or broken
- Caused by: dropping phone while plugged in, forcing wrong orientation
- Check for debris/lint in port — clean with non-metallic tool
- If bent pins internally — professional repair needed
- Wireless charging as temporary workaround while port is repaired

---

#### Malware on Mobile
- Always a concern — mobile malware is increasing rapidly
- **Symptoms to look for:**
  - Unexpected data usage spikes
  - Battery draining much faster than normal
  - Unknown apps appearing
  - Phone running hot when idle
  - Pop-up ads appearing outside browsers
  - Calls or texts sent without your knowledge
- **Solutions:** Factory reset, only install from official app stores, keep OS updated
- **Cybersecurity use:** Mobile RATs (Remote Access Trojans) give attackers full control — camera, microphone, location, all messages

---

#### Cursor Drift
- **Random input or cursor moves without touching the device**
- Causes: damaged digitizer, screen protector issue, moisture on screen
- Remove screen protector — may be lifting and causing phantom touches
- Dry the screen — moisture causes false touches
- Factory reset if hardware appears fine

---

#### Unable to Install New Application
| Cause | Solution |
|---|---|
| Insufficient storage space | Delete unused apps and files |
| No network connectivity | Connect to Wi-Fi or mobile data |
| OS incompatibility | Update OS or find older app version |
| App compatibility | Check minimum OS requirement |
| App store cache | Clear app store cache and data |
| Invalid credentials | Sign out and back into app store account |

---

#### Stylus Does Not Work
1. Check **power** — stylus has internal battery (charge it)
2. Check **Bluetooth connectivity** — stylus pairs via Bluetooth
3. Check **stylus hardware** — tip may be worn or damaged
4. **Restart the device** — re-establishes Bluetooth pairing
5. Re-pair stylus in Bluetooth settings

---

#### Degraded Performance
| Cause | Solution |
|---|---|
| Outdated OS | Update to latest OS version |
| Outdated apps | Update all apps |
| Low storage | Free up space — performance drops below 10% free |
| Excessive background apps | Close background apps, disable background refresh |
| Hardware aging | Battery replacement may help — old battery throttles CPU |
| Too many widgets | Reduce home screen widgets |

---

### 5.5 Troubleshooting Networks

#### No Network Connectivity — Step by Step Ping Test
> Follow this exact order — each step narrows down where the problem is

```
Step 1: ping 127.0.0.1        ← ping loopback — tests your own TCP/IP stack
Step 2: ping your own IP       ← tests your NIC (e.g. ping 192.168.1.71)
Step 3: ping default gateway   ← tests connection to router (e.g. ping 192.168.1.1)
Step 4: ping DNS server        ← tests DNS reachability (e.g. ping 8.8.8.8)
Step 5: ping domain name       ← tests DNS resolution (e.g. ping google.com)
```

- If Step 1 fails → TCP/IP stack corrupted → reinstall network stack
- If Step 2 fails → NIC issue or IP configuration wrong
- If Step 3 fails → cable/Wi-Fi issue between you and router
- If Step 4 fails → router issue or ISP problem
- If Step 5 fails but Step 4 works → DNS issue

**Also check:** Link light on NIC/switch — amber/green light = physical connection OK

```bash
# Run these in order on Ubuntu
ping -c 4 127.0.0.1          # loopback
ping -c 4 192.168.1.71       # your IP (change to yours)
ping -c 4 192.168.1.1        # your gateway
ping -c 4 8.8.8.8            # Google DNS
ping -c 4 google.com         # DNS resolution test
```

---

#### Intermittent Wireless Connectivity
| Cause | Solution |
|---|---|
| Interference | Change Wi-Fi channel, move away from interference sources |
| Poor signal strength | Move closer to AP, add Wi-Fi extender |
| Incorrect channel | Use Wi-Fi analyser — find least congested channel |
| Bounce and latency | Radio waves reflecting off surfaces cause inconsistent signal |
| Too many devices | Upgrade router or use 5GHz band |

---

#### Slow Network Speeds
- **Confirm end-to-end connectivity** — is it slow everywhere or just one site?
- **Evaluate each network hop** — where is the bottleneck?
- **May require packet capture** — Wireshark to analyse traffic
```bash
# Test download speed from terminal
curl -o /dev/null https://speed.cloudflare.com/__down?bytes=100000000

# Check network interface speed
ethtool enp4s0 | grep Speed

# Traceroute to find slow hops
traceroute google.com
```

---

#### Limited or No Connectivity (Windows)
- Yellow exclamation mark (⚠) in Windows system tray = limited connectivity
- Usually means: connected to router but no internet
- IP address may be APIPA (169.254.x.x) — DHCP failed
- Try: `ipconfig /release` then `ipconfig /renew`
- **Linux equivalent:**
```bash
# Release and renew DHCP
sudo dhclient -r enp4s0    # release
sudo dhclient enp4s0       # renew
```

---

#### Jitter
- **Time variation between frames** in real-time media
- Normal network: packets arrive at consistent intervals
- Jitter: packets arrive at irregular intervals → choppy audio/video
- Most **real-time media (VoIP, video calls, gaming) is sensitive to jitter**
- Measured in milliseconds — under 30ms is acceptable for VoIP
- Causes: network congestion, inconsistent routing, wireless interference
- Solution: QoS (Quality of Service) — prioritise real-time traffic on router

---

#### Poor VoIP Quality — Explained Simply
- VoIP (Voice over IP) converts your voice to data packets sent over internet
- Requires: **high speed AND low latency** — both matter
- **Why both matter:**
  - High speed = enough bandwidth for voice data
  - Low latency = voice packets arrive quickly enough to sound natural
  - High latency (>150ms) = noticeable delay, talking over each other
  - Jitter = choppy, robotic voice
  - Packet loss > 1% = voice cuts out

**Troubleshooting VoIP:**
1. Check internet connection speed and latency — `ping -c 20 8.8.8.8`
2. Check for jitter — look at ping variation in results
3. Check if other devices are consuming bandwidth (streaming, downloads)
4. Enable QoS on router — prioritise VoIP traffic
5. Use wired connection instead of Wi-Fi for VoIP

---

#### Port Flapping
- **Network interface repeatedly goes up and down** — unstable connection
- Switch port alternates between connected and disconnected state
- Causes: bad cable, faulty NIC, faulty switch port, duplex mismatch
- **Solutions:**
  - Move to different switch interface
  - Replace bad cable
  - Replace faulty NIC or switch port
- **Cybersecurity use:** Port flapping can be triggered intentionally as a DoS attack — disrupts network stability

---

#### High Latency
- **Delay between sending a request and receiving a response**
- Some latency is expected and normal — distance adds latency
- Light travels ~200km through fibre per millisecond — geography matters
- **Troubleshoot:** Examine response times at every step along the path
```bash
# Measure latency to each hop
traceroute google.com
# Or with round-trip times
mtr google.com
```

---

#### Interference Sources

**Predictable (known sources):**
- **Fluorescent lights** — emit electromagnetic interference
- **Microwave ovens** — operate at 2.4GHz — same as Wi-Fi!
- **Cordless telephones** — older models use 2.4GHz
- **High power sources** — motors, generators, transformers

**Unpredictable:**
- **Multi-tenant buildings** — neighbours' Wi-Fi networks competing on same channels
- Other wireless devices with variable usage patterns

---

#### Signal to Noise Ratio (SNR)
- **Signal** — the data you want to receive (Wi-Fi, cellular)
- **Noise** — unwanted electromagnetic interference from other sources
- **SNR = Signal strength / Noise floor**
- You want a **very large ratio** — much more signal than noise
- Measured in dB (decibels)
- Good Wi-Fi SNR: **>25 dB**
- Poor Wi-Fi SNR: **<10 dB** — unreliable connection
```bash
# Check Wi-Fi signal strength on Ubuntu
iwconfig wlp3s0
# Look for "Signal level" value
```

---

#### Authentication Issues
- Cannot access a network resource despite having credentials
- **Common causes:**
  - Wrong username or password
  - Account locked out (too many failed attempts)
  - Session expired — need to re-authenticate
  - Certificate expired (for certificate-based auth)
  - Time synchronisation issue — Kerberos requires clocks within 5 minutes
- **Hard to diagnose** — authentication failures often look like connectivity failures
- Check event logs on the authentication server for denied access entries
- **Cybersecurity use:** Authentication failures are logged — attackers try to stay under lockout thresholds (slow password spray attacks)

---

#### Intermittent Internet Connectivity
**Determine the scope of outage:**
1. **Ongoing pings** — `ping -i 1 8.8.8.8` — watch for dropped packets
2. **Traceroute** to a known location — identify where packets stop
3. **Speed test** — speedtest.net or `curl` based test

**Check your SLA (Service Level Agreement):**
- Contract with ISP that guarantees minimum uptime and speed
- If ISP consistently below SLA — document outages, contact for credit or resolution
- Enterprise customers have enforceable SLAs — home users usually do not

---

### 5.6 Troubleshooting Printers

#### Testing the Printer First
- Always **print or scan a test page** before assuming the computer is the problem
- Use printer's **built-in diagnostic tools** (from printer menu, not computer)
- If test page prints fine → problem is computer/driver/network
- If test page fails → problem is the printer itself

---

#### Bad Output

| Problem | Likely Cause | Solution |
|---|---|---|
| Lines down the page | Dirty drum or toner cartridge (laser) | Clean drum, replace toner |
| Faded prints | Low toner/ink, wrong paper type | Replace toner/ink, check paper settings |
| Blank pages | Empty toner/ink, drum not charging | Replace toner, check drum |
| Double/echo images | Ghost image offset on page | Replace fuser assembly (laser) |
| Smearing/streaking | Fuser not hot enough, wet paper | Replace fuser, use correct paper |
| Speckled output | Dirty corona wire | Clean corona wire |

---

#### Garbled Print
- Output is random characters, symbols, or nonsense
- Causes:
  - **Wrong printer driver** or incorrect model selected
  - **Incorrect PDL** (Page Description Language) — PCL vs PostScript mismatch
  - Bad application sending corrupt print data
- **Solutions:**
  1. Verify you selected the correct printer model in driver
  2. Reinstall printer driver
  3. Try printing from different application
  4. Check printer's PDL setting matches driver

---

#### Paper Jams
- **Be careful when removing** — pull in direction of paper travel
- Never yank paper — torn pieces left inside cause future jams
- **Paper not feeding** — worn feed rollers, wrong paper size/weight
- **Multiple pages feeding** — worn separation pad, static in paper stack
- **Creased paper** — obstruction in paper path, damaged rollers
- Clean feed rollers with IPA to restore grip
- Fan paper before loading — separates sheets, reduces static

---

#### Multiple Prints Pending in Queue
- **Corrupted print jobs** cause print spooler to crash or freeze
- All subsequent jobs stuck behind corrupted job
- **Problems are logged** in Event Viewer (Windows)
- One bad job can block entire queue

**Fix on Windows:**
1. Stop Print Spooler service
2. Delete files in `C:\Windows\System32\spool\PRINTERS`
3. Restart Print Spooler service

**Fix on Ubuntu:**
```bash
# Cancel all print jobs
cancel -a

# Restart CUPS
sudo systemctl restart cups

# Check queue
lpstat -o
```

---

#### Grinding Noise from Printer
- **Never a good sound** from a printer
- Something is physically not operating properly
- Causes: paper jam fragment stuck in mechanism, worn gear, broken roller
- Power off immediately — running with grinding noise causes more damage
- Check all paper paths for obstructions including tiny torn pieces

---

#### Finishing Issues
- Finishing = what happens **after ink/toner is applied**
- Includes: stapling, hole punching, collating, folding
- **Staple jams** — staple cartridge empty or misfed — remove jammed staples carefully
- **Incorrect hole punch location** — wrong paper size setting or paper misaligned in tray
- Check paper size settings match actual paper loaded

---

#### Incorrect Page Orientation
- Printed in portrait when landscape was needed or vice versa
- **Check the print settings** when printing — orientation set in:
  - Application print dialog
  - Printer preferences
  - Page setup in application
- Document orientation and printer orientation must match

---

#### Tray Not Recognised
- Printer does not see the paper tray or rejects it
- The **size of the printed page must match the paper size in the tray**
- Configure correct paper size in:
  - Printer settings on computer
  - Printer's own menu (for network printers)
- Physical tray may be improperly seated — remove and reseat

---

#### Connectivity Issues
- Printer is a **network device** — treat it like any other network device
- **Confirm connection type:** USB, Ethernet, or Wi-Fi
- **Verify IP address** — printer IP may have changed (use DHCP reservation for printers)
- Check printer IP from printer's settings menu
- Ping the printer IP to confirm network reachability:
```bash
ping -c 4 192.168.1.xxx   # replace with printer IP
```
- Access printer web interface: open browser → type printer IP → login
- **Cybersecurity use:** Default printer web interface credentials (admin/admin) are never changed — printers are one of the easiest devices to compromise on a network

---

## Terminal Practice + Expected Output

### Test Network Connectivity Step by Step
```bash
ping -c 4 127.0.0.1
```
**Expected output:**
```
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.045 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.052 ms
--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss
```
- 0% packet loss = TCP/IP stack working ✅

---

### Check DNS Resolution
```bash
dig google.com | grep -A3 "ANSWER SECTION"
```
**Expected output:**
```
;; ANSWER SECTION:
google.com.        284    IN    A    142.250.64.46
```

---

### Check Wi-Fi Signal and SNR
```bash
iwconfig wlp3s0
```
**Expected output:**
```
wlp3s0  IEEE 802.11  ESSID:"YourNetwork"
        Frequency:5.18 GHz
        Bit Rate=433.3 Mb/s
        Link Quality=65/70  Signal level=-45 dBm
        Noise level=-95 dBm
```
- Signal: -45 dBm, Noise: -95 dBm
- SNR = 95 - 45 = **50 dB** — excellent signal ✅

---

### Check Printer Status
```bash
lpstat -p && systemctl status cups --no-pager | head -5
```
**Expected output:**
```
printer Canon_G2010_series is idle. enabled since...
● cups.service - CUPS Scheduler
   Active: active (running)
```

---

## 🔑 Additional Important Concepts You Missed

### MDM and Remote Wipe
- **Mobile Device Management (MDM)** — enterprise tool to manage mobile devices
- If phone is lost or stolen: **remote wipe** erases all data instantly
- Requires: MDM enrollment before loss occurs
- **Find My (iOS) / Find My Device (Android)** — consumer equivalent
- **Cybersecurity use:** Remote wipe is a critical incident response tool — lost phone with corporate data must be wiped immediately

### ADB — Android Debug Bridge
- Command line tool for communicating with Android devices
- Can: backup data, install apps, access shell, recover from broken screen
```bash
# Install ADB on Ubuntu
sudo apt install adb -y

# List connected devices
adb devices

# Backup all app data
adb backup -all -apk -shared -f backup.ab
```

### Juice Jacking
- Public USB charging stations can be modified to steal data or install malware
- Phone asks "Trust this computer?" when connected — never trust unknown computers
- **Protection:** Use USB data blocker (charge-only adapter), use AC charger, use wireless charging

### Network Troubleshooting Tools Summary
| Tool | Use |
|---|---|
| `ping` | Test connectivity to a host |
| `traceroute` | Show path packets take to destination |
| `mtr` | Combines ping and traceroute — live stats |
| `netstat -tuln` | Show open ports and listening services |
| `iwconfig` | Wi-Fi interface info and signal strength |
| `dig` / `nslookup` | DNS lookup and troubleshooting |
| `ethtool` | NIC speed, duplex, link status |
| `ip a` | Show all network interfaces and IPs |
| `ss -tuln` | Modern replacement for netstat |

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. VoIP needs both high speed AND low latency — high latency causes delay, jitter causes choppy audio
2. Troubleshoot network in order: loopback → own IP → gateway → DNS IP → domain name — each step isolates the problem
3. Juice jacking — public USB charging points can steal data — always use your own charger or a USB data blocker