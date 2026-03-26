# CompTIA A+ 220-1201 — Week 2 Day 3 Notes

---

## Videos Watched
- ✅ 3.8 Laser Printer Maintenance
- ✅ 3.8 Inkjet Printers
- ✅ 3.8 Inkjet Printer Maintenance
- ✅ 3.8 Thermal Printers
- ✅ 3.8 Thermal Printer Maintenance
- ✅ 3.8 Impact Printers
- ✅ 3.8 Impact Printer Maintenance

---

## Key Concepts

### 3.8 Laser Printers

#### What Makes Laser Printers Special?
- **Very high quality** output — sharp text and graphics
- **Fast printing speed** — especially for large print jobs
- **Very complex** internally — many components working together
- More expensive upfront but cheaper per page than inkjet
- Toner (powder) instead of liquid ink — doesn't dry out

---

#### How a Laser Printer Works — The 7 Step Process
> Memorise these 7 steps — they appear constantly in A+ exams

**Step 1 — Processing:**
- Printer receives the print job from the computer
- Rasterises the image — converts to a dot pattern the printer can understand
- Stores the full page in printer memory before printing begins

**Step 2 — Charging:**
- The **corona wire** (or charge roller) applies a **uniform negative charge** (-600V) to the entire surface of the **photosensitive drum**
- The drum is coated with a light-sensitive material (organic photoconductor)
- At this point: entire drum is negatively charged — no image yet

**Step 3 — Exposing (Writing):**
- The **laser beam** scans across the drum surface
- Wherever the laser hits, it **neutralises the charge** (makes those spots less negative ~-100V)
- The laser draws the image by selectively discharging areas
- Result: drum has a hidden electrostatic image — charged areas = no print, discharged areas = print

**Step 4 — Developing:**
- **Toner** (fine plastic powder, negatively charged) is applied to the drum
- Toner is attracted to the **less negative (discharged) areas** — the image areas
- Toner sticks to where the laser fired — the image becomes visible on the drum

**Step 5 — Transferring:**
- Paper passes between the drum and the **transfer corona wire/roller**
- Transfer corona applies a **positive charge** to the back of the paper
- The positively charged paper attracts the negatively charged toner off the drum
- Toner transfers from drum to paper — image is now on paper but not fixed yet

**Step 6 — Fusing:**
- Paper passes through the **fuser assembly** — two rollers (heating roller + pressure roller)
- **Heat (~200°C) and pressure** melts the toner plastic particles into the paper fibres
- This permanently bonds the toner to the paper
- Paper comes out warm — this is why freshly printed pages are warm

**Step 7 — Cleaning:**
- Remaining toner on the drum is scraped off by a **cleaning blade**
- **Erase lamp** exposes the entire drum to light — removes all remaining charge
- Drum is ready for the next page

```
Processing → Charging → Exposing → Developing → Transferring → Fusing → Cleaning
(Memory trick: Please Charge Every Day Till Friday, Clean)
```

---

#### Replacing the Toner Cartridge
- Toner cartridge contains: toner powder, drum, developer roller, cleaning blade (all-in-one)
- Shake gently before installing to distribute toner evenly
- Remove protective strip/tape before installing
- **Cybersecurity use:** Used toner cartridges can be forensically analysed to reconstruct printed documents

---

#### Laser Printer Maintenance Kit
- Contains parts that wear out over time and should be replaced together:
  - Fuser assembly
  - Transfer roller
  - Feed rollers
  - Separation pad
- Kits are rated by **page count** — replace at manufacturer-recommended intervals (e.g. every 100,000 pages)
- Symptoms of worn maintenance kit: paper jams, faded prints, smeared toner

---

#### Laser Printer Calibration
- Ensures colours and alignment are accurate
- **Colour calibration** — prints test page, analyses it, adjusts colour output
- **Alignment calibration** — ensures print head is aligned correctly for duplex printing
- Usually done automatically or from printer settings menu

---

#### Laser Printer Cleaning
- **Outside:** Wipe with a **damp cloth** — removes dust and fingerprints
- **Inside:** Use **dry, lint-free cloth** to wipe away toner dust — never use a vacuum (toner particles too fine, go through filters)
- **Glass/lens:** Clean with **isopropyl alcohol (IPA)** — removes toner smears from the laser lens
- **Never use water inside** — electrical components
- **Toner spills:** Use toner-specific vacuum or damp cloth — never breathe toner dust (carcinogenic)

---

### 3.8 Inkjet Printers

#### Overview
- **Relatively inexpensive** upfront cost
- **Quiet** operation — no high voltage components
- **High resolution** — excellent for photos (up to 9600 DPI)
- **Expensive ink** — ink cartridges cost more per page than laser toner
- Ink can **dry out** if not used regularly

#### How Inkjet Printing Works
- Tiny nozzles spray microscopic droplets of liquid ink onto paper
- Two technologies:
  - **Thermal inkjet** — tiny heating element vaporises ink → bubble forms → forces ink droplet out (HP, Canon)
  - **Piezoelectric inkjet** — electric charge deforms a crystal → pushes ink out mechanically (Epson)

#### Ink Cartridges — CMYK
- **CMYK** — the four colour printing model:
  - **C** — Cyan
  - **M** — Magenta
  - **Y** — Yellow
  - **K** — Key (Black)
- Combining CMY in different amounts produces all colours
- Black (K) is separate because mixing CMY produces muddy brown, not true black
- Some printers use 6-8 cartridges for photo printing (adds light cyan, light magenta etc.)
- Your **Canon G2010** uses refillable ink tanks instead of cartridges — much cheaper per page

#### Print Head
- Contains thousands of tiny nozzles that spray ink
- Can be part of the cartridge (HP) or permanent on the printer (Epson, Canon)
- Permanent print heads last longer but are expensive to replace if damaged

#### Feed Rollers
- Pull paper from the tray into the printer
- Worn rollers cause paper jams and misfeeds
- Can be cleaned with IPA to restore grip

#### Duplexing
- Printing on **both sides of the paper** automatically
- Printer prints one side, flips paper internally, prints other side
- Saves paper — important for environment and cost

---

### 3.8 Inkjet Printer Maintenance

#### Cleaning Print Heads
- Nozzles clog when ink dries inside them — causes streaky or missing colours
- **Software cleaning** — printer runs ink through nozzles to clear blockages (wastes some ink)
- **Manual cleaning** — remove cartridge/head, soak nozzle plate in warm water or IPA
- Print a **nozzle check pattern** to see which nozzles are blocked

#### Replacing Inkjet Cartridges
- Check ink levels before running out — low ink causes poor quality
- Replace individual colours as needed (don't need to replace all at once)
- For your Canon G2010 — refill the ink tanks when low (much cheaper than cartridges)

#### Inkjet Printer Calibration
- Aligns print head horizontally and vertically
- Fixes: offset text, blurry images, colour misalignment
- Printer prints a calibration page → user selects best-aligned pattern → saved

#### Clearing Jams
- Turn off printer before clearing jams
- Pull paper gently in the direction of paper travel — never against it
- Check all access panels — paper can jam in multiple locations
- Small torn pieces must be removed completely

---

### 3.8 Thermal Printers

#### What Are Thermal Printers?
- Print using **heat** instead of ink or toner
- You've seen these at: **petrol pumps, ATMs, supermarket checkouts, restaurants** (thyo oil pump ma dine bill — exactly right! 😄)
- **White paper** goes in, image appears through heat
- **Very quiet** — no moving print heads, no impact
- No ink or toner needed — very low maintenance

#### How Thermal Printing Works
- Paper is coated with a **thermochromic chemical** that changes colour when heated
- The **heating element** selectively heats areas of the paper
- Heated areas turn dark — forms the image
- **Full-length heating element** spans the entire width of the paper — no moving print head needed

#### Components
- **Feed assembly** — motors and rollers that advance the paper
- **Heating element** — the bar that applies heat to the paper
- **Thermal paper** — paper covered with thermochromic coating

#### Thermal Paper
- Special paper with a **thermochromic chemical coating**
- Turns dark when heated above a threshold temperature (~60°C)
- **Cannot substitute** regular paper — won't work
- Different sizes for different applications:
  - 57mm wide — receipt printers
  - 80mm wide — kitchen printers, larger POS
  - 112mm wide — label printers
- Sensitive to: heat (sunlight, friction), chemicals (hand sanitiser fades receipts instantly)
- **Cybersecurity use:** Thermal receipts contain cardholder data — improper disposal = data breach

---

### 3.8 Thermal Printer Maintenance

#### Thermal Paper Replacement
- Relatively inexpensive but cannot substitute with regular paper
- Load with coated side facing the heating element (shiny side)
- Different sizes for different printers — check specifications

#### Cleaning the Heating Element
- Heating element accumulates dust, paper residue, and chemical buildup
- Clean with **IPA (isopropyl alcohol)** on a cotton swab or cleaning card
- **Liquid cleaner** specifically designed for thermal printers
- Clean regularly for consistent print quality

#### Removing Debris
- Use compressed air to blow out paper dust
- Check feed rollers for buildup — clean with IPA
- Never use sharp objects inside the printer

---

### 3.8 Impact Printers

#### Dot Matrix / Impact Printer
- Uses a **print head with a small matrix of pins**
- Pins physically strike an **inked ribbon** against the paper
- Creates characters from a grid of tiny dots
- **Loud** — mechanical impact makes significant noise
- **Still used today** for specific applications

#### Why Impact Printers Are Still Used
- **Carbon copies / multipart paper** — impact transfers through multiple layers of paper simultaneously
  - Example: NCR paper (No Carbon Required) — receipt + copy in one pass
  - Used in: banks, hospitals, government offices, warehouses
- **Low cost per page** — ribbon lasts a long time
- Works in **extreme environments** — heat, dust, cold (factories, warehouses)
- Prints on **continuous form paper** using tractor feed

#### Components

**Dot Matrix Print Head:**
- Contains a grid of metal pins (9-pin or 24-pin)
- 9-pin = draft quality
- 24-pin = near letter quality (NLQ) — much sharper
- Pins fire in patterns to form characters

**Printer Ribbon:**
- Fabric ribbon soaked in ink, runs on a loop
- Print head pins strike through ribbon onto paper
- Fades gradually — replace when prints become light

**Tractor Feed:**
- Sprocket mechanism that pulls continuous form paper through the printer
- Paper has holes along the sides that engage the sprockets
- Ensures precise paper positioning — important for multipart forms

**Multipart Paper:**
- Multiple layers of paper — original + copies
- Impact force transfers through all layers
- 2-part, 3-part, 4-part versions available
- **Cybersecurity use:** Carbon copies are a data security risk — all copies contain the same sensitive data and must be disposed of securely

---

### 3.8 Impact Printer Maintenance

#### Printer Ribbon Replacement
- Replace when prints appear faded or light
- Ribbon runs in a continuous loop — replace entire cartridge
- Do not re-ink ribbons — uneven coverage and potential damage

#### Print Head Replacement
- Print heads wear out over millions of impacts
- Symptoms: missing dots in characters, consistently faded columns
- More expensive to replace than ribbons — test ribbon first

#### Replacing the Paper
- Continuous form paper threaded through tractor feed mechanism
- Must align holes precisely with sprockets
- Tear perforations between pages — paper designed to separate cleanly

---

## Printer Type Comparison

| Feature | Laser | Inkjet | Thermal | Impact |
|---|---|---|---|---|
| Technology | Toner + laser | Liquid ink | Heat | Ink ribbon + pins |
| Speed | Fast | Moderate | Fast | Slow |
| Quality | Very high | High (photos) | Basic | Low-medium |
| Noise | Moderate | Quiet | Very quiet | Very loud |
| Cost per page | Low | High | Very low | Very low |
| Ink/supply | Toner cartridge | Ink cartridge | Thermal paper only | Ribbon |
| Carbon copies | No | No | No | Yes ✅ |
| Special paper | No | No | Yes (thermal) | Optional |
| Best use | Office documents | Photos | Receipts, labels | Multipart forms |

---

## Terminal Practice + Expected Output

### Check Printer Status
```bash
lpstat -p
```
**Expected output:**
```
printer Canon_G2010_series is idle.  enabled since Thu 19 Mar 2026 10:00:00
```

### List All Printers
```bash
lpstat -a
```
**Expected output:**
```
Canon_G2010_series accepting requests since Thu 19 Mar 2026 10:00:00
```

### Check CUPS Printing System
```bash
systemctl status cups
```
**Expected output:**
```
● cups.service - CUPS Scheduler
     Loaded: loaded (/lib/systemd/system/cups.service; enabled)
     Active: active (running) since Thu 2026-03-19 10:00:00 NPT
```
- `active (running)` = CUPS is working correctly

### Print a Test Page from Terminal
```bash
# Print a test page to your Canon G2010
lp -d Canon_G2010_series /usr/share/cups/data/default-testpage.pdf
```

### Check Print Queue
```bash
lpstat -o
```
**Expected output (no jobs):**
```
(no output = no jobs in queue)
```

---

## 🔑 Additional Important Concepts You Missed

### Laser Printer Safety
- **Ozone** — laser printers produce ozone gas during operation
- High-voltage components inside — never reach inside a running printer
- **Toner dust** — fine particles, potential carcinogen — never use regular vacuum
- **Fuser assembly** — extremely hot after use — let cool before touching
- **Cybersecurity use:** Ozone detectors can identify nearby laser printer activity

### OPC Drum — Organic Photoconductor
- The photosensitive drum is called the **OPC drum**
- Sensitive to light — keep in darkness when not in printer
- Scratches permanently damage print quality
- Usually included in the toner cartridge (all-in-one design)

### DPI — Dots Per Inch
- Measure of print resolution
- Higher DPI = more detail = sharper output
| Printer Type | Typical DPI |
|---|---|
| Laser (text) | 600-1200 DPI |
| Laser (graphics) | 1200-2400 DPI |
| Inkjet (standard) | 1200-2400 DPI |
| Inkjet (photo) | 4800-9600 DPI |
| Thermal | 203-300 DPI |
| Impact | 60-240 DPI |

### Printer Spooler
- Software that manages the **print queue**
- Jobs sent to spooler → spooler feeds to printer one at a time
- **PrintNightmare (CVE-2021-34527)** — critical Windows Print Spooler vulnerability
- **Cybersecurity use:** Clearing the print spooler clears pending sensitive documents from memory

### Printer Data Security
- Modern printers have **internal storage (HDD or flash)** that caches print jobs
- Must be securely wiped before disposing of or selling a printer
- **Data remanence** — data persists on printer storage even after printing
- Enterprise printers: enable automatic job deletion after printing

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. Laser printing has 7 steps — Processing, Charging, Exposing, Developing, Transferring, Fusing, Cleaning
2. Thermal printers use thermochromic paper — heat turns the coating dark, no ink needed — hand sanitiser destroys thermal receipts
3. Impact printers are still used today specifically for carbon copies — the physical impact transfers through multiple paper layers simultaneously