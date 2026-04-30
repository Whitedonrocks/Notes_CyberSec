# CompTIA A+ 220-1201 — Week 1 Day 6 Notes

---

## Videos Watched
- ✅ 3.1 Display Types
- ✅ 3.1 Display Attributes
- ✅ 3.2 Network Cables
- ✅ 3.2 568A and 568B Colors
- ✅ 3.2 Optical Fiber
- ✅ 3.2 Peripheral Cables
- ✅ 3.2 Video Cables

---

## Key Concepts

### 3.1 Display Types

#### LCD — Liquid Crystal Display
- Uses liquid crystals that block or allow light to pass through
- Requires a **backlight** to illuminate the screen
- Three main LCD technologies:

**TN — Twisted Nematic LCD**
- Oldest and cheapest LCD technology
- Very fast response time (1ms) — good for gaming
- Poor viewing angles — colours shift when viewed from the side
- Poor colour accuracy
- Best for: budget monitors, competitive gaming

**IPS — In-Plane Switching LCD**
- Much better colour accuracy than TN
- Wide viewing angles — colours stay consistent from the side
- Slightly slower response time than TN (4-8ms)
- Best for: photo/video editing, general use, design work
- Most common in modern laptops and phones

**VA — Vertical Alignment LCD**
- Best contrast ratio of the three — deepest blacks
- Better colour than TN, slightly worse than IPS
- Slower response time — ghosting in fast motion
- Best for: movie watching, mixed use

| Feature | TN | IPS | VA |
|---|---|---|---|
| Response Time | 1ms ⭐ | 4-8ms | 4-8ms |
| Colour Accuracy | Poor | Excellent ⭐ | Good |
| Viewing Angles | Poor | Excellent ⭐ | Good |
| Contrast Ratio | Low | Medium | High ⭐ |
| Price | Cheapest ⭐ | Mid-high | Mid |

---

#### OLED — Organic Light Emitting Diode
- Each pixel **produces its own light** — no backlight needed
- When a pixel is black it is completely off → **true black**
- Infinite contrast ratio compared to LCD
- Thinner and lighter than LCD
- Cons: burn-in risk over time, more expensive
- Used in: high-end phones (Samsung AMOLED), premium laptops, TVs

---

#### Mini LED
- Uses thousands of tiny LEDs as a backlight for LCD panels
- Better local dimming than traditional LCD — deeper blacks
- Bridge between LCD and OLED — better than regular LCD, cheaper than OLED
- Used in: Apple Pro Display XDR, high-end gaming monitors

---

#### Touch Screen
- Allows direct interaction with the display using fingers or stylus
- Common types:
  - **Capacitive** — uses electrical charge from skin (modern phones/tablets)
  - **Resistive** — detects physical pressure (older, works with any object)
- Capacitive is more accurate and supports multi-touch

#### Digitizer
- A separate layer on top of the display that detects touch/pen input
- Converts physical touch into digital coordinates
- In phones and tablets the digitizer is bonded to the glass
- Can be replaced independently of the display in some devices

#### Backlight and Inverter
- **Backlight** — light source behind LCD panel (LED or older CCFL)
- **Inverter** — older component that converted DC power to AC for CCFL backlights
- Modern LED-backlit displays do not need an inverter
- Failing backlight = very dim or black screen (still works but barely visible)

---

### 3.1 Display Attributes

#### Pixel Density (PPI — Pixels Per Inch)
- How many pixels fit in one inch of screen
- Higher PPI = sharper image
- Formula: `PPI = √(width² + height²) / screen size`
- Example:
```
iPhone 15:     460 PPI  → very sharp, text looks printed
1080p 27" monitor:  82 PPI  → acceptable for desk distance
4K 27" monitor:    163 PPI  → very sharp at desk distance
```
- **Why it matters:** A 1080p phone looks blurry, a 1080p TV at 10 feet looks sharp — distance matters

#### Pixel Density Comparison
| Device | Resolution | Screen Size | PPI |
|---|---|---|---|
| iPhone 15 Pro | 2556x1179 | 6.1" | 460 |
| MacBook Pro 14" | 3024x1964 | 14.2" | 254 |
| 4K 27" Monitor | 3840x2160 | 27" | 163 |
| 1080p 27" Monitor | 1920x1080 | 27" | 82 |
| 1080p 55" TV | 1920x1080 | 55" | 40 |

---

#### Refresh Rate
- How many times per second the display updates the image — measured in **Hz**
- Higher Hz = smoother motion
- **FPS (Frames Per Second)** from GPU must match or exceed refresh rate to benefit

| Refresh Rate | Best For |
|---|---|
| 60Hz | Office work, browsing, movies |
| 144Hz | Competitive gaming, smooth scrolling |
| 240Hz | Professional esports gaming |
| 360Hz | Top-tier competitive gaming |

**Cable bandwidth limits refresh rate:**
- **HDMI 2.1** — supports 4K at 144Hz
- **DisplayPort 2.1** — supports dual 4K at 144Hz
- Older HDMI 1.4 can only do 4K at 30Hz — major limitation

---

#### Screen Resolution
| Name | Resolution | Common Use |
|---|---|---|
| HD | 1280x720 | Older/budget devices |
| Full HD (1080p) | 1920x1080 | Standard monitors, laptops |
| QHD / 2K | 2560x1440 | Gaming monitors, quality laptops |
| 4K / UHD | 3840x2160 | High-end monitors, TVs |
| 8K | 7680x4320 | Professional video, future TVs |

---

#### Color Gamut
- The **range of colours** a display can show
- Defined by international standards from the **ITU** (International Telecommunication Union)

| Standard | Coverage | Use Case |
|---|---|---|
| sRGB | Standard | Web, office, general use |
| Adobe RGB | Wider | Professional photography |
| DCI-P3 | Wide | Cinema, video production |
| Rec. 2020 | Widest | HDR video, broadcast |

#### Color Coverage
- How much of a colour gamut a display actually reproduces
- Example: "100% sRGB" means it covers the entire sRGB range
- "90% DCI-P3" means it covers 90% of the cinema colour space
- Higher coverage = more accurate colours = more expensive display

---

### 3.2 Network Cables

#### Why Cables Matter
- The physical foundation of every network
- Wrong cable = slow speeds, interference, signal loss
- Cable choice affects: maximum speed, maximum distance, interference resistance

#### Twisted Pair Copper Cabling
- Most common network cable type
- Pairs of wires twisted together — twisting **cancels out electromagnetic interference (EMI)**
- More twists per inch = better interference resistance = higher category

#### Cable Categories
- Standard: **IEEE 802.3**

| Category | Max Speed | Max Distance | Use |
|---|---|---|---|
| Cat5 | 100 Mbps | 100m | Outdated |
| Cat5e | 1 Gbps | 100m | Home networks |
| Cat6 | 1 Gbps (10Gbps up to 55m) | 100m | Office networks |
| Cat6A | 10 Gbps | 100m | Data centres, modern offices |
| Cat7 | 10 Gbps | 100m | Data centres (shielded) |
| Cat8 | 25-40 Gbps | 30m | Data centres only |

---

#### Coaxial Cable
- Two or more conductors share a **common axis**
- Centre conductor surrounded by insulation, then braided shield, then outer jacket
- **RG-6** — most common, used for television and cable internet (DOCSIS)
- More resistant to interference than twisted pair

---

#### Unshielded and Shielded Cable

**Abbreviation system: (overall)/(pairs)TP**

| Abbreviation | Meaning |
|---|---|
| U | Unshielded |
| S | Braided shielding |
| F | Foil shielding |
| TP | Twisted Pair |

**Examples:**
```
U/UTP  = Unshielded overall / Unshielded pairs  → standard Cat5e/Cat6
F/UTP  = Foil overall / Unshielded pairs         → light shielding
S/FTP  = Braided overall / Foil per pair          → heavy shielding, data centres
```
- **Cybersecurity use:** Unshielded cables in sensitive areas can leak data via electromagnetic emissions (Van Eck phreaking)

---

#### Direct Burial STP
- **Direct Burial** — cable designed to be buried underground without conduit
- Uses **STP** (Shielded Twisted Pair) for extra protection
- Has gel filling to resist moisture
- Used for: outdoor campus networks, underground runs

---

#### Plenum vs Non-Plenum Cable

**Plenum space** — the space above dropped ceilings or below raised floors used for air circulation in HVAC systems

| Type | Jacket Material | Fire Behaviour | Cost |
|---|---|---|---|
| Non-Plenum (PVC) | Standard PVC | Burns, releases toxic smoke | Cheaper |
| Plenum rated | FEP or Low-smoke PVC | Self-extinguishing, low toxic smoke | More expensive |

- **FEP** — Fluorinated Ethylene Polymer — premium plenum jacket
- **Required by fire code** to use plenum-rated cable in plenum spaces
- **Cybersecurity use:** Running non-plenum cable in plenum spaces violates fire code — used in physical security audits

---

### 3.2 568A and 568B Wiring Standards

- **International standard:** ISO/IEC 11801
- **US standard:** TIA (Telecommunications Industry Association)
- Defines which colour wire goes on which pin of an RJ45 connector

#### T568A Pin Order (left to right, clip facing down):
```
Pin 1: White/Green
Pin 2: Green
Pin 3: White/Orange
Pin 4: Blue
Pin 5: White/Blue
Pin 6: Orange
Pin 7: White/Brown
Pin 8: Brown
```

#### T568B Pin Order (left to right, clip facing down):
```
Pin 1: White/Orange
Pin 2: Orange
Pin 3: White/Green
Pin 4: Blue
Pin 5: White/Blue
Pin 6: Green
Pin 7: White/Brown
Pin 8: Brown
```

#### Which to Use?
- **T568B** is more common in the US and commercial installations
- **T568A** is used in government and some residential
- **Most important rule:** Use the SAME standard on BOTH ends of a cable (straight-through)
- **Crossover cable** = T568A on one end, T568B on the other (used to connect two computers directly)

---

### 3.2 Optical Fiber

#### How It Works
- Transmits data as **pulses of light** through a glass or plastic core
- **Ferrule** — the tip of a fibre connector that holds and aligns the fibre core
- Completely immune to electromagnetic interference
- Cannot be tapped without physical access and special equipment

#### Multimode Fiber (MMF)
- **Short range** — up to 2km
- Uses **LED** light source
- Larger core diameter (50 or 62.5 microns)
- Multiple light paths travel through the core
- Cheaper than single mode
- Used for: building-to-building, campus networks, data centres

#### Single Mode Fiber (SMF)
- **Long range** — up to 100km without regeneration
- Uses **laser** light source
- Smaller core diameter (9 microns)
- Only one light path — no signal degradation over distance
- More expensive than multimode
- Used for: ISP backbone, long-distance WAN links, undersea cables

| Feature | Multimode | Single Mode |
|---|---|---|
| Range | Up to 2km | Up to 100km |
| Light Source | LED | Laser |
| Core Size | 50/62.5 microns | 9 microns |
| Cost | Lower | Higher |
| Use | Buildings, campus | Long distance, WAN |
| Colour (jacket) | Orange or Aqua | Yellow |

- **Cybersecurity use:** Fibre is very hard to tap — requires physical access and special splicing equipment — makes it more secure than copper

---

### 3.2 Peripheral Cables

#### USB — Universal Serial Bus
- Designed to **simplify connections** — one standard for many devices
- Hot-swappable — plug and unplug without restarting

#### USB Versions

| Version | Max Speed | Notes |
|---|---|---|
| USB 1.1 | 12 Mbps | Very old, rare now |
| USB 2.0 | 480 Mbps | Still common for keyboards, mice |
| USB 3.0 | 5 Gbps | Blue colour coding inside port |
| USB 3.1 | 10 Gbps | Also called USB 3.1 Gen 2 |
| USB 3.2 | 20 Gbps | Requires USB-C connector |

#### USB Connectors

| Connector | Use |
|---|---|
| Standard A | Computer/hub side — flat rectangle |
| Standard B | Device side — square with notch (printers) |
| Mini-B | Older cameras, MP3 players |
| Micro-B | Old Android phones, power banks |
| USB 3.0 Standard B | Larger version of B plug for USB 3.0 |
| USB 3.0 Standard A | Same shape as 2.0 A but blue inside |
| USB 3.0 Micro-B | 10-pin connector for USB 3.0 speeds |

#### USB-C
- **One connector to rule them all**
- 24-pin, reversible (no wrong way to plug in)
- Can carry: data (USB), video (DisplayPort, HDMI), power (up to 240W), Thunderbolt
- Becoming the universal standard across all devices

---

#### Serial Cables — D-Subminiature (D-Sub)
- Trapezoidal connector with rows of pins
- **DB-9** — 9 pins — most common, used for RS-232 serial communication
- **DB-25** — 25 pins — older, used for parallel ports and modems
- Commonly used for **RS-232** serial communication
- Now mainly used as a **configuration port** for routers, switches, and industrial equipment
- Example: connecting a console cable to a Cisco router for initial setup

---

#### Thunderbolt

| Version | Max Speed | Notes |
|---|---|---|
| Thunderbolt 1 | 10 Gbps | Mini DisplayPort connector |
| Thunderbolt 2 | 20 Gbps | Mini DisplayPort connector |
| Thunderbolt 3 | 40 Gbps | USB-C connector |
| Thunderbolt 4 | 40 Gbps | USB-C, improved specs over TB3 |
| Thunderbolt 5 | 120 Gbps | USB-C, latest standard |

- **High-speed serial connector** — data AND power on the same cable
- Can daisy-chain up to 6 devices
- Backwards compatible with USB-C (but not full Thunderbolt speeds)
- Used for: external GPUs, high-speed storage, docking stations
- **Cybersecurity use:** Thunderbolt DMA (Direct Memory Access) attacks — plugging in a malicious Thunderbolt device can read/write system RAM directly, bypassing OS security

---

### 3.2 Video Cables

#### HDMI — High-Definition Multimedia Interface
- Carries **video AND audio** on a single cable
- Maximum cable length: **20 metres** (passive)
- **19-pin Type A connector** — most common
- Versions: HDMI 1.4 (4K@30Hz), HDMI 2.0 (4K@60Hz), HDMI 2.1 (4K@144Hz, 8K@60Hz)
- Used everywhere: TVs, monitors, projectors, game consoles

#### DisplayPort (DP)
- Digital information sent in **packetized form** (like network packets)
- Compatible with HDMI and DVI via adapters
- **Full size** and **Mini DisplayPort** connectors
- Versions: DP 1.4 (8K@60Hz), DP 2.1 (dual 4K@144Hz)
- Preferred for PC gaming monitors — higher bandwidth than HDMI
- **Cybersecurity use:** DisplayPort Alt Mode over USB-C can be used to capture screen output

#### DVI — Digital Visual Interface

| Type | Signals | Max Resolution |
|---|---|---|
| DVI-D (Single Link) | Digital only | 1920x1200 |
| DVI-D (Dual Link) | Digital only | 2560x1600 |
| DVI-A | Analogue only | Lower |
| DVI-I | Digital + Analogue | Up to 2560x1600 |

- Speed: up to 7.92 Gbps (dual link)
- Older standard — being replaced by HDMI and DisplayPort
- **No audio** — video only

#### VGA — Video Graphics Array
- **DB-15 connector** (more accurately called **DE-15**) — blue colour, 15 pins in 3 rows
- **Analogue signal** — video only, no audio
- Maximum practical resolution: 1920x1080 (degrades at higher res)
- Very old standard (1987) but still found on projectors and older equipment
- **No audio** support whatsoever
- Signal quality degrades over long cable runs

#### USB-C Video
- A single USB-C port can carry video via:
  - **DisplayPort Alt Mode** — native DP signal over USB-C
  - **HDMI Alt Mode** — native HDMI signal over USB-C
  - **Thunderbolt** — highest bandwidth video option
- Common uses: laptop to monitor, phone to TV, docking stations
- **Many uses of USB-C:**
  - Power delivery (charging up to 240W)
  - Data transfer (USB 3.2, Thunderbolt)
  - Video output (DisplayPort, HDMI)
  - Audio output
  - Ethernet (with adapter)

#### Video Cable Comparison

| Cable | Signal | Audio | Max Resolution | Age |
|---|---|---|---|---|
| VGA | Analogue | No | 1080p practical | 1987 |
| DVI | Digital/Analogue | No | 2560x1600 | 1999 |
| HDMI | Digital | Yes | 10K (2.1) | 2002 |
| DisplayPort | Digital | Yes | 16K (2.1) | 2008 |
| USB-C | Digital | Yes | Depends on version | 2014 |

---

## Terminal Practice + Expected Output

### Check Your Display Info
```bash
xrandr
```
**Expected output:**
```
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080     60.05*+  60.01    59.97    59.96    59.93
   1680x1050     59.95    59.88
   1400x1050     59.98
```
- `eDP-1` = your laptop's built-in display
- `1920x1080` = your current resolution
- `60.05*` = current refresh rate (the * means active)

---

### Check Network Card Details
```bash
lspci | grep -i network
```
**Expected output:**
```
03:00.0 Network controller: Intel Corporation Wi-Fi 6 AX200 (rev 1a)
```

```bash
lspci | grep -i ethernet
```
**Expected output:**
```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 (rev 15)
```

---

### Check Ethernet Connection Speed
```bash
ethtool enp4s0
```
**Expected output:**
```
Settings for enp4s0:
        Speed: 1000Mb/s
        Duplex: Full
        Auto-negotiation: on
        Link detected: yes
```
- `Speed: 1000Mb/s` = Gigabit Ethernet (Cat5e or better cable)
- `Duplex: Full` = can send and receive simultaneously
- `Link detected: yes` = cable is plugged in and working

---

### Full Hardware Summary
```bash
sudo lshw -short
```
**Expected output (partial):**
```
H/W path        Device     Class          Description
=====================================================
                           system         ASUS TUF Gaming
/0                         bus            Motherboard
/0/0                       memory         16GiB System Memory
/0/1                       processor      Intel Core i5
/0/100/2                   display        Intel UHD Graphics
/0/100/1c/0    enp4s0      network        Realtek RTL8111
/0/100/1c/1    wlp3s0      network        Intel Wi-Fi 6
```

---

### Check USB Devices
```bash
lsusb
```
**Expected output:**
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04a9:183a Canon, Inc. PIXMA G2010
Bus 001 Device 002: ID 8087:0029 Intel Corp. AX200 Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
- You can see your Canon printer listed here!
- Each device shows vendor ID and product ID

---

## 🔑 Additional Important Concepts You Missed

### Aspect Ratio
- Ratio of width to height of a display
- **16:9** — standard widescreen (most monitors and TVs)
- **16:10** — slightly taller, preferred by developers and designers
- **21:9** — ultrawide, great for multitasking
- **4:3** — old square monitors, legacy equipment

### HDR — High Dynamic Range
- Displays much brighter highlights and darker shadows simultaneously
- Requires both HDR-capable display AND HDR content
- Standards: HDR10, Dolby Vision, HDR10+
- **Minimum 1000 nits brightness** for true HDR

### Fibre Connector Types
| Connector | Use |
|---|---|
| LC (Lucent Connector) | Most common, small form factor, data centres |
| SC (Subscriber Connector) | Older, square shape, ISP equipment |
| ST (Straight Tip) | Older, bayonet style, legacy equipment |
| MTP/MPO | Multi-fibre, high density data centres |

### USB Power Delivery (USB PD)
- USB-C can deliver up to **240W** of power (USB PD 3.1)
- Allows charging laptops, monitors, and even some desktops via USB-C
- **Cybersecurity use:** Malicious USB-C chargers (O.MG cables) can deliver power while also stealing data or executing attacks

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. IPS is the best all-round LCD technology — wide viewing angles and accurate colours
2. Plenum-rated cable is legally required above dropped ceilings — FEP jacket prevents toxic smoke
3. Single mode fibre uses laser and reaches 100km — multimode uses LED and only reaches 2km