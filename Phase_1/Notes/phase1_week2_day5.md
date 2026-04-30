# CompTIA A+ 220-1201 — Week 2 Day 5 Notes

---

## Videos Watched
- ✅ 5.1 Troubleshooting Hardware
- ✅ 5.2 Troubleshooting Storage Devices
- ✅ 5.3 Troubleshooting Display Issues
- ⏭ 5.4 Troubleshooting Mobile Devices — carry over to Day 6

---

## Key Concepts

### 5.1 Troubleshooting Hardware

#### POST — Power On Self Test
- Runs every time the computer powers on
- Tests **core components** to verify they are performing properly
- Failures are noted with **beep codes** or **on-screen error codes**
- If POST passes → proceeds to boot loader
- If POST fails → beeps or error message indicating which component failed

#### Common Beep Code Meanings (AMI BIOS)
| Beeps | Meaning |
|---|---|
| 1 short | POST passed — all good |
| 2 short | POST error — check screen for code |
| 1 long, 3 short | RAM not detected |
| 1 long, 2 short | GPU failure |
| Continuous | RAM or power issue |

---

#### POST and Boot Issues

**Blank screen on boot:**
- Monitor not receiving signal from GPU
- Could be POST failure or display connection issue

**BIOS time and settings reset:**
- CMOS battery dying — settings revert to defaults on every boot
- Replace the CR2032 coin cell battery on the motherboard

**Attempts to boot to incorrect device:**
- Boot order in BIOS set to wrong device
- Enter BIOS → change boot order → set correct drive first
- Could also be a corrupted boot loader

---

#### Crash Screens

**Blue Screen of Death (BSOD) — Windows Stop Error:**
- Windows encountered an error it cannot recover from
- Contains critical information:
  - **Stop code** — identifies the specific error (e.g. MEMORY_MANAGEMENT, IRQL_NOT_LESS_OR_EQUAL)
  - **Faulting module** — which driver or file caused the crash
  - **Memory dump** — saved to disk for analysis
- Common causes: bad drivers, failing RAM, corrupted system files, hardware failure
- **Cybersecurity use:** BSoDs can be triggered by malware — kernel-level rootkits commonly cause stop errors

**Linux equivalent — Kernel Panic:**
```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```
- Similar to BSOD — kernel encountered unrecoverable error
- Check: `sudo dmesg | grep -i "panic\|error" | tail -20`

---

#### BSODs and Shutdown Issues

**Troubleshooting steps:**
1. **Use Last Known Good Configuration** — boots with last working registry settings
2. **System Restore** — rolls back system to a previous restore point
3. **Rollback driver** — if BSOD started after a driver update
4. **Reseat or remove hardware** — faulty RAM, GPU, or expansion card
5. **Check event viewer** — Windows logs the exact cause before crashing

---

#### Proprietary Crash Screens
- Every OS and application has its own crash notifications
- **macOS** — Spinning beach ball (app hang) or grey/black screen (kernel panic)
- **Linux** — Kernel panic, segmentation fault, OOM killer messages
- **Android** — App crash dialog or bootloop
- **iOS** — Spinning wheel, app crash, or recovery mode
- **What they mean:** The application or OS encountered an error it could not handle — could be software bug, memory issue, or hardware problem
- Always note the error message/code before dismissing — it tells you exactly what failed

---

#### Blank Screen Issues
| Cause | Solution |
|---|---|
| Monitor not connected | Check cable at both ends |
| Wrong input source selected | Press input button on monitor (HDMI 1, HDMI 2, DP) |
| Image is dim | Increase brightness — may be at minimum |
| Faulty monitor | Swap with known-good monitor |
| No video after Windows loads | GPU driver issue — boot in safe mode, reinstall driver |
| Backlight failure | Image visible with flashlight — backlight needs replacement |

---

#### No Power
- Check power cable is fully seated at both PSU and wall
- Test wall outlet with another device
- Check PSU power switch (back of PC) is ON
- Check power button header connection on motherboard
- Try different power cable
- PSU may have failed — test with known-good PSU
- Check for blown fuse in plug (UK/Nepal)
- **Laptop:** Try without battery, power adapter only — adapter may be faulty

---

#### Sluggish Performance
| Cause | Solution |
|---|---|
| Too many processes | Open Task Manager — identify high CPU/RAM processes |
| Pending Windows updates | Install updates — may include performance fixes |
| Low disk space | Less than 10% free = severe slowdown — clear space |
| Power saving mode (laptop) | Change power plan to Balanced or High Performance |
| Malware | Run antivirus and anti-malware scan |
| Startup programs | Disable unnecessary startup apps |
| Fragmented HDD | Run disk defragment (SSDs don't need this) |

**Check on Ubuntu:**
```bash
htop              # identify high CPU/RAM processes
df -h             # check disk space
sudo apt autoremove && sudo apt clean  # free up space
```

---

#### Overheating
- CPUs and GPUs **throttle themselves** when too hot — slows down to reduce heat
- Causes: blocked vents, failed fan, dried thermal paste, dusty heatsink
- **Verify with monitoring software:**
```bash
sensors           # check all temperatures
watch -n 1 sensors # live temperature monitor
nvidia-smi        # GPU temperature
```
- **Solutions:** Clean dust from vents, replace thermal paste, improve airflow, replace failed fan

---

#### Smoke and Burning Smell
- **Always disconnect power immediately** — do not wait
- Electrical burning smell = component has failed catastrophically
- Common causes: PSU failure, short circuit, swollen capacitor, fried VRM
- Locate the bad component — usually visible burn marks or bulging capacitors
- **Never power on again** until bad component is found and replaced
- **Safety:** Capacitors can hold charge even after power is disconnected — be careful

---

#### Random Shutdown
- Computer turns off with no warning — black screen instantly
- **Heat related** — CPU/GPU hits thermal limit → emergency shutdown to prevent damage
- **Failing hardware** — PSU failing under load, failing RAM
- **Check:** temperatures under load, PSU voltage stability, RAM with memtest86
```bash
# Check system logs for shutdown cause
sudo journalctl -p err -n 50
sudo dmesg | grep -i "thermal\|temperature\|shutdown" | tail -20
```

---

#### Application Crashes
- Application stops working unexpectedly
- **Windows:** Check Event Viewer → Windows Logs → Application
- **Windows:** Reliability Monitor — shows crash history timeline
- **Linux:** Check application logs
```bash
journalctl -f              # live system log
journalctl -p err -n 30    # last 30 errors
~/.xsession-errors         # GUI application errors
```
- **Solutions:** Reinstall application, update drivers, check for conflicting software

---

#### Unusual Noises
| Sound | Meaning | Action |
|---|---|---|
| Humming | Normal operation | None needed |
| Grinding | HDD head crash or failing fan bearing | Replace immediately |
| Rattling | Loose component, fan hitting cable | Open case, identify and secure |
| Scraping | Fan blade hitting object | Check fans immediately |
| Clicking | HDD read/write head repeatedly repositioning | Back up immediately — drive failing |
| Clicking (repeated) | "Click of death" — HDD failure imminent | Emergency backup now |
| Pop/bang | Component failure — capacitor blow | Disconnect power immediately |

> **If you hear clicking from storage: back up immediately. The drive is about to fail.**

---

#### Inaccurate System Date/Time
- Clock resets to wrong date every time you reboot
- Cause: **dead CMOS/motherboard battery** (CR2032 coin cell)
- Battery keeps BIOS settings and real-time clock running when PC is off
- Replace the battery (~NPR 100-200) — settings will be restored
- Also check: time server sync settings, timezone configuration

**Fix on Ubuntu:**
```bash
# Sync time with internet time server
sudo timedatectl set-ntp true
timedatectl status
```

---

### 5.2 Troubleshooting Storage Devices

#### Storage Failure Symptoms
| Symptom | Likely Cause |
|---|---|
| Read/write failure | Failing drive, bad sectors, loose cable |
| Slow performance | Drive filling up, failing drive, fragmentation (HDD) |
| Loud clicking noise | HDD head failure — imminent drive death |
| Files randomly disappearing | File system corruption, failing drive |
| OS not found on boot | Boot sector corruption, wrong boot order, dead drive |

---

#### Grinding Noises
- Hard drives are **mechanical devices** with extremely high tolerances
- The read/write head floats nanometres above the spinning platter
- Grinding = **metal on metal contact** — the head is touching the platter
- This is catastrophic — **head crash**
- Very difficult to recover data after grinding starts
- **Action:** Power off immediately, send to professional data recovery service

---

#### Troubleshooting Disk Failure — Step by Step
1. **Get a backup first** — before doing anything else
2. Check for **loose or damaged cables** — reseat SATA data and power cables
3. Check for **overheating** — poor ventilation causes premature drive failure
4. Check **power supply** — unstable power corrupts drives
5. Run **hard drive diagnostics** — manufacturer tools or `smartctl`

```bash
# Install smartmontools
sudo apt install smartmontools -y

# Check NVMe drive health
sudo smartctl -a /dev/nvme0n1

# Run a short self-test
sudo smartctl -t short /dev/nvme0n1

# Check results after test (wait 2 minutes)
sudo smartctl -a /dev/nvme0n1 | grep -A5 "Self-test"
```

---

#### Boot Failure Symptoms
| Error | Meaning | Solution |
|---|---|---|
| "OS not found" | Boot sector corrupt or drive not detected | Check cables, check boot order |
| "Drive not recognised" | Drive dead, cable issue, or wrong port | Reseat cables, try different port |
| "BOOTMGR is missing" | Windows boot manager corrupted | Repair with Windows installation media |
| "Grub rescue>" | GRUB bootloader corrupted | Boot from Ubuntu live USB, repair GRUB |

```bash
# Check if Ubuntu can see the drive
lsblk
sudo fdisk -l

# Check for disk errors
sudo dmesg | grep -i "error\|fail" | grep -i "nvme\|sda\|sdb"
```

---

#### Data Loss and Corruption
- Causes: sudden power loss, improper shutdown, failing drive, filesystem errors
- **Prevention:** Regular backups, UPS, proper shutdown procedure
- **Recovery tools:**
  - `fsck` — Linux filesystem check and repair
  - TestDisk — recovers lost partitions
  - PhotoRec — recovers deleted files
```bash
# Check filesystem for errors (unmounted drive only)
sudo fsck /dev/sda1

# Check disk for bad blocks
sudo badblocks -v /dev/sda
```

---

#### RAID Failure
- Causes: hardware failure, power issue, communication issue (bad cable)
- **Almost always very obvious** — OS reports degraded array, missing disk alerts
- Single disk failure in RAID 1/5/6 = degraded but still running
- Two disk failures in RAID 5 = complete data loss
- RAID controller failure = entire array inaccessible

#### RAID Recovery
- Each RAID level recovers differently:
  - **RAID 1:** Replace failed drive → automatic mirror rebuild
  - **RAID 5:** Replace failed drive → parity used to rebuild missing data
  - **RAID 6:** Can replace up to 2 drives → rebuild from double parity
  - **RAID 0:** One drive fails = total loss — no recovery possible
- During rebuild: system is vulnerable — another failure = complete loss
- Use **hot spare** to reduce rebuild time

---

#### SMART — Self-Monitoring Analysis and Reporting Technology
- Built into all modern drives — **avoids hardware failure** by predicting it
- Monitors: read error rate, reallocated sectors, spin retry count, temperature
- Key SMART attributes to watch:
  - **Reallocated Sector Count** — bad sectors remapped to spare area (increasing = drive dying)
  - **Pending Sector Count** — sectors waiting to be reallocated
  - **Uncorrectable Sector Count** — sectors that could not be read
  - **Temperature** — consistently high temps = shorter life
```bash
sudo smartctl -H /dev/nvme0n1    # overall health
sudo smartctl -A /dev/nvme0n1    # all attributes
```

---

#### Extended Read/Write Times
- Operations that should be fast taking much longer than normal
- Causes: drive approaching failure, filesystem fragmentation (HDD), overheating
- Check SMART data for increasing error counts
- **Test read speed:**
```bash
sudo hdparm -tT /dev/nvme0n1
```

---

#### Missing Drives in OS
| Drive Type | Possible Cause | Solution |
|---|---|---|
| Internal drive | Cable issue, not initialised, wrong filesystem | Check cables, initialise in disk management |
| External drive | USB cable issue, no power, driver issue | Try different USB port/cable |
| Network share | Network down, share permissions, wrong credentials | Check network, re-enter credentials |

---

#### Array Missing
- Entire RAID array not visible to OS
- Cause: **missing or faulty RAID controller**
- Controller card failed, driver issue, or controller configuration lost
- Solution: replace RAID controller with identical model, restore configuration

---

### 5.3 Troubleshooting Display Issues

#### Incorrect Input Source
| Issue | Solution |
|---|---|
| Monitor connected but no image | Check cable at both ends — HDMI, DP, VGA |
| Wrong input selected | Press Input/Source button on monitor bezel |
| Image very dim | Increase brightness setting on monitor |
| Still no image | Swap with known-good monitor to isolate fault |
| No video after Windows loads | GPU driver issue — safe mode → reinstall driver |

---

#### LCD Projector Bulbs
- LCD projectors use **high-pressure mercury bulbs** that generate intense heat
- **Cooling is always an issue** — blocked vents cause overheating
- Bulb lifespan: 2,000-5,000 hours — replace when dim or discoloured
- **Never touch bulb with bare hands** — oils from skin cause hot spots → bulb explosion
- Allow projector to cool completely before moving — fan runs after shutdown
- Replacement bulbs are expensive ($100-500)

---

#### Fuzzy/Blurry Image
- LCD displays have a **fixed native resolution**
- Running at non-native resolution = scaled image = blurry/fuzzy
- **Solution:** Always set display resolution to native resolution
- Example: 1920x1080 monitor → always use 1920x1080 in display settings
```bash
# Check available resolutions
xrandr
# Set native resolution
xrandr --output eDP-1 --mode 1920x1080
```

---

#### Burn-In
- Long-term display of static image causes permanent image retention
- **Occurs across all monitor types** (OLED worst, LCD less so)
- **Prevention:** Use screensaver, set display timeout, enable pixel shift
- **LCD image sticking** — temporary version of burn-in, usually self-corrects
- **OLED burn-in** — permanent, especially for static UI elements (taskbar, HUD)
- Modern displays use **pixel shift** — slightly moves image to prevent burn-in

---

#### Dead Pixels
- Pixel permanently stuck — **always black** (no light output)
- Caused by manufacturing defect or physical damage
- Cannot be fixed — monitor warranty replacement if within dead pixel policy
- Different from **stuck pixels** — stuck pixels are always one colour (red, green, blue)
- Test: display solid white/black/red/green/blue screens to identify

---

#### Flashing/Flickering Screen
- Check **video cable connections** at both ends — loose connection causes flickering
- Check refresh rate — set to monitor's native refresh rate
- GPU driver issue — update or rollback driver
- Failing monitor backlight — flickering gets worse over time
- **High-frequency flicker** — PWM dimming issue — some monitors flicker to control brightness

---

#### Incorrect Colour Display
| Cause | Solution |
|---|---|
| Monitor colour settings | Adjust tint, colour temperature, reset to factory defaults |
| Custom colour preset | Reset monitor to factory/sRGB preset |
| Driver configuration | Check GPU control panel colour settings |
| OS night light settings | Disable night light (Ubuntu: Settings → Display → Night Light) |
| Outdated GPU driver | Update GPU driver |
| Faulty cable | Replace cable — damaged cables cause colour issues |

---

#### Audio Issues with Monitors
- Many monitors include **built-in speakers**
- Monitor may have audio controls (volume buttons on bezel)
- Audio travels over: **HDMI, DisplayPort, or Thunderbolt** — confirm correct input
- If no audio from monitor speakers:
  - Check audio output device in OS settings
  - Confirm cable carries audio (HDMI/DP — yes, VGA/DVI — no)
  - Check monitor volume is not muted

---

#### Dim Image
| Cause | Solution |
|---|---|
| Brightness set too low | Increase brightness via monitor buttons or OS |
| Auto-dimming enabled | Disable ambient light sensor in OS settings |
| Dim on battery (laptop) | Change power plan — increase screen brightness on battery |
| Driver settings | Check GPU driver — may have auto-brightness |
| **Backlight failure** | Image visible with flashlight — LCD needs backlight replacement |

**Backlight failure test:**
- Shine a flashlight at an angle on the screen in a dark room
- If you can faintly see the image — backlight has failed (not the LCD panel)
- LCD panel is fine, just the backlight needs replacement

---

#### Image Quality Problems
| Problem | Cause | Solution |
|---|---|---|
| Flickering colour patterns | Loose or damaged cable pins | Replace cable |
| Distorted image/geometry | Hardware acceleration issue | Disable hardware acceleration in browser/app |
| Incorrect geometry | Wrong resolution or refresh rate | Match to display's native specs |
| Colour fringing | Damaged cable | Replace cable |

---

#### Sizing Issues
- Video output resolution does not match monitor's native resolution
- Monitor may **scale to fit** (stretches image) or show black bars
- Solution: match output resolution to native monitor resolution
- **Overscan/underscan** — image extends beyond or inside screen edge
  - Common on TVs used as monitors
  - Fix in GPU driver settings — adjust display scaling

---

#### Distorted Image
| Symptom | Likely Cause |
|---|---|
| Lines across screen | Failing GPU or cable damage |
| Flashing colours | GPU failure or cable issue |
| Random blocks/artefacts | GPU VRAM failure or overheating |
| Screen tears | V-sync disabled — enable V-sync or FreeSync/G-Sync |
| Wavy lines | Electromagnetic interference (rare with LCD) |

- **Hardware failure** — failing GPU, dying VRAM, damaged screen
- **Software configuration** — wrong driver, hardware acceleration conflicts
- Test: connect monitor to different computer — if problem follows monitor = monitor fault, if problem stays = GPU fault

---

## Terminal Practice + Expected Output

### Check Storage Health
```bash
sudo smartctl -a /dev/nvme0n1
```
**Expected output (key parts):**
```
=== START OF INFORMATION SECTION ===
Model Number:    Samsung SSD 970 EVO
Firmware Version: 2B2QEXM7
Capacity:        500 GB

=== START OF DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

Temperature:                        35 Celsius
Data Units Read:                    15,000,000
Data Units Written:                 8,000,000
```
- `PASSED` = drive is healthy ✅
- Temperature under 50°C = normal

---

### Check for Hardware Errors in System Log
```bash
sudo dmesg | grep -i "error\|fail\|warn" | tail -20
```
**Expected output:**
```
[    2.847] nvme nvme0: 8/0/0 default/read/poll queues
[    3.123] ACPI Warning: ...
```
- A few warnings are normal
- Repeated errors about same device = hardware problem

---

### Check Critical System Errors
```bash
sudo journalctl -p err -n 30
```
**Expected output:**
```
Mar 20 10:00:01 prayagn kernel: ACPI Warning...
Mar 20 10:00:02 prayagn systemd[1]: ...
```

---

## 🔑 Additional Important Concepts You Missed

### The Troubleshooting Process (CompTIA Official Method)
> Always follow this structured approach — examiners test this

1. **Identify the problem** — gather information, question the user
2. **Establish a theory of probable cause** — consider obvious causes first
3. **Test the theory** — confirm or deny your theory
4. **Establish a plan of action** — resolve the issue with minimal impact
5. **Implement the solution** — carry out the fix
6. **Verify full system functionality** — confirm the fix worked
7. **Document findings** — record what happened and what fixed it

### Memtest86 — RAM Testing
- Dedicated tool to test RAM for errors
- Runs before OS loads — tests RAM completely
- Let it run for at least 2 full passes
- Any errors = replace the RAM module
```bash
# Install memtest86 on Ubuntu
sudo apt install memtest86+ -y
# Run from GRUB menu on next boot
```

### Event Viewer (Windows) / Journal (Linux)
- **Windows Event Viewer** — complete log of all system events, errors, warnings
- Critical for diagnosing BSoDs and application crashes
- **Linux equivalent:**
```bash
sudo journalctl -f              # live log
sudo journalctl -p crit         # critical events only
sudo journalctl -p err --since "1 hour ago"  # last hour errors
```

### S.M.A.R.T Failure Prediction
- When SMART predicts failure: **backup immediately**
- SMART is not 100% accurate — drives can fail without warning
- Drives can also continue working long after SMART warnings
- Treat SMART warning as: **change this drive soon**

### Display Port vs HDMI Flickering
- Some cables cause flickering due to poor shielding
- Always use high-quality cables for 4K/144Hz
- Test with a different cable before replacing monitor or GPU

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. Clicking sound from HDD = imminent failure — back up immediately, do not wait
2. Backlight failure test — shine flashlight on dim screen — if image visible, backlight failed not panel
3. CompTIA 7-step troubleshooting process — always identify before fixing, always document after