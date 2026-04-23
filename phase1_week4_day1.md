# CompTIA A+ 220-1202 — Week 4 Day 1 Notes

---

## Videos Watched
- ✅ 4.1 Ticketing Systems
- ✅ 4.1 Asset Management
- ✅ 4.1 Document Types
- ✅ 4.2 Change Management
- ✅ 4.3 Managing Backups
- ✅ 4.4 Managing Electrostatic Discharge
- ✅ 4.4 Safety Procedures

---

## Key Concepts

### 4.1 Ticketing Systems

#### What is a Ticketing System?
- The **best way to manage support requests** — every issue gets a unique ticket number
- Tracks the entire lifecycle of a support request: document → assign → resolve → report
- Usually the **responsibility of the help desk**
- Examples: ServiceNow, Jira Service Management, Zendesk, Freshdesk, Remedy

#### Managing a Support Ticket

**Information Gathering:**
- Collect all relevant details before attempting to fix anything
- Ask open-ended questions — "What were you doing when this happened?"
- Reproduce the issue if possible
- Gather: error messages, screenshots, recent changes made

**Applying Context:**
- Connect the issue to broader context — is this affecting multiple users?
- Check if related to recent changes — new software, updates, hardware changes
- Check knowledge base — has this been solved before?

**Clear and Concise Communication:**
- Keep user informed throughout the process
- Use plain language — avoid technical jargon with end users
- Set realistic expectations — "I will update you by 3pm"
- Document every action taken in the ticket notes

#### Ticket Fields to Know

**User Information:**
- Name, contact details, department, manager
- How to reach them — phone, email, Teams

**Device Information:**
- Make, model, serial number, asset tag
- Operating system and version
- Location of device

**Problem Description:**
- Detailed description of the issue
- Steps to reproduce
- When it started, frequency of occurrence
- Any error messages or codes

**Categorisation:**
- Type of issue: hardware, software, network, security, account
- Priority: Critical, High, Medium, Low
- Helps route to the right team

**Escalation:**
- Tier 1 (help desk) → Tier 2 (specialist) → Tier 3 (vendor/developer)
- Escalate when: issue beyond current skill level, requires higher access, SLA breach risk

**Progress Notes:**
- Document every step taken — what was tried, what worked, what did not
- Other technicians can pick up where you left off
- Legal protection — proof of what was done

**Problem Resolution:**
- Document the final solution clearly
- Root cause identified
- Steps that resolved the issue
- Prevention recommendations

---

### 4.1 Asset Management

#### What is Asset Management?
- A **record of every asset** in the organisation
- Know what you have, where it is, who has it, what condition it is in
- Associates support tickets with specific devices by make and model
- Used for: **financial records, audits, depreciation calculations**

#### Asset Tags
- **Physical label** attached to every device — barcode or QR code
- Unique identifier — scanned to pull up full asset record
- Links physical device to database entry
- Deters theft — device is clearly marked as company property

#### CMDB — Configuration Management Database
- **Central asset tracking system** — single source of truth for all assets
- Stores: device details, location, assigned user, warranty status, licensing, purchase date, cost
- Tracks relationships between assets — which server runs which applications
- Tracks **changes** — who changed what and when
- **Cybersecurity use:** CMDB reveals unauthorised devices — anything not in CMDB is rogue hardware

**Key CMDB Fields:**
| Field | Description |
|---|---|
| Asset ID / Tag | Unique identifier |
| Make / Model | Manufacturer and model number |
| Serial Number | Manufacturer's unique ID |
| Assigned User | Who currently has it |
| Location | Building, floor, room |
| Purchase Date | When acquired |
| Warranty Expiry | When warranty ends |
| Licensing | Software licence details |
| Status | Active, spare, retired, stolen |

#### Procurement Life Cycle
The process of acquiring new assets:

1. **Request** — user or department requests new equipment
2. **Approval** — manager and budget holder approve
3. **Negotiation** — IT negotiates price and terms with suppliers
4. **Purchase** — purchase order raised, invoice received
5. **Receiving** — asset received, inspected, tagged
6. **Deployment** — asset configured and assigned to user
7. **Management** — tracked throughout useful life
8. **Disposal** — securely decommissioned at end of life

---

### 4.1 Document Types

#### Incident Reports
- Documents a **security or operational incident** in detail
- What happened, when, who was affected, how it was resolved
- Required for: security policy compliance, legal purposes, insurance claims
- Used to improve future response — lessons learned
- **Cybersecurity use:** Incident reports are legally significant — accurate documentation critical

#### SOP — Standard Operating Procedures
- **Step-by-step instructions** for performing routine tasks consistently
- Organisations have different business objectives — SOPs reflect their specific needs
- Covers: software installation, upgrade procedures, new user setup, backup procedures
- **Documentation is the key** — without SOPs knowledge lives in people's heads — risk when staff leave
- Example: SOP for onboarding a new employee — same process every time, nothing missed

#### Onboarding
- **Bringing a new person into the organisation** — IT's role:
  - IT agreements signed — acceptable use policy, confidentiality agreement
  - Create accounts — AD account, email, VPN, application access
  - Provide required IT hardware — laptop, phone, accessories
  - Install required software
  - Provide access to required systems
  - Security training — policies, phishing awareness

#### Offboarding
- **Removing a departing employee** — must be predefined and followed every time
- **What happens to hardware:** collect laptop, phone, access cards, tokens
- **What happens to data:** transfer ownership of files, archive email, revoke cloud access
- **Disable accounts immediately** — on last day or when they leave
- Never delete accounts immediately — preserve audit trail
- **Cybersecurity use:** Offboarding failures are a major security risk — ex-employees with active accounts is a top insider threat vector

#### SLA — Service Level Agreement
- **Contract defining minimum service standards**
- Specifies: uptime guarantee, response times, resolution times, penalties for breach
- Example: ISP SLA guarantees 99.9% uptime — if breached, customer gets credit
- Internal IT SLA: helpdesk responds to critical issues within 1 hour
- **Cybersecurity use:** SLA defines recovery time objectives — important for business continuity planning

#### Knowledge Base and Articles
- **External sources** — vendor documentation, community forums, manufacturer guides
- **Internal documentation** — how-to guides, known issue resolutions, troubleshooting steps
- **Find solutions quickly** — technicians search before spending time investigating
- Reduces repeat work — solved once, documented, anyone can use it
- Grows over time — each resolved ticket adds to the knowledge base

---

### 4.2 Change Management

#### What is Change Management?
- **Formal process for managing changes** to IT systems
- One of the most common sources of risk in enterprise IT
- Often overlooked or ignored — causes outages and security incidents
- **Nothing changes without going through the process**
- Goal: minimise risk while allowing necessary changes

#### Why Change Management Matters
- Uncontrolled changes cause outages — most downtime is self-inflicted
- Changes can have unexpected ripple effects on other systems
- Without documentation — cannot roll back effectively
- Regulatory compliance often requires change documentation

---

#### Change Management Process

**Step 1 — Change Request:**
- Formal request submitted — usually a change request form
- Nothing gets missed — structured template
- Usually a transparent process — visible to all stakeholders

**Step 2 — Purpose of the Change:**
- Why is this change needed?
- Valid reasons: application upgrade, security fix, performance improvement, compliance
- There needs to be a **good documented reason** — not just "because"

**Step 3 — Scope of the Change:**
- What systems are affected?
- A single change can have far-reaching effects — map all dependencies
- How long will the change take?
- Who needs to be notified?

**Step 4 — Risk Analysis:**
- What could go wrong?
- What is the probability of failure?
- What is the impact if it fails?
- Risk level determines approval requirements

**Step 5 — Rollback Plan:**
- **Always have a way to revert the change**
- What is the exact procedure to undo the change if it fails?
- Always have backups before making any change
- Test the rollback procedure — not just the change itself

**Step 6 — Backup Plan (Plan B, C, D):**
- What if something goes wrong?
- Example: installing a firewall update — what if it breaks connectivity?
  - Plan B: rollback to previous version
  - Plan C: bypass firewall temporarily
  - Plan D: activate backup firewall
- Always complete the mission — have alternatives ready

**Step 7 — Sandbox Testing:**
- Test the change in an **isolated environment** before production
- Confirm the change works as expected
- Confirm the rollback plan works
- Identify problems without affecting real users

**Step 8 — Responsible Staff Members:**
- Change management is a **team effort**
- IT team — implements the change
- Business customer — confirms requirements and acceptance
- Organisation sponsor — authorises and funds the change

**Step 9 — Date and Time:**
- **Maintenance window** — scheduled time when changes are allowed
- **On-demand change windows** — for urgent but non-emergency changes
- **Regularly scheduled downtime** — predictable windows users expect
- **Change freeze** — period when NO changes allowed (holidays, end of financial year, major events)

**Step 10 — Change Board Approval (CAB):**
- **CAB — Change Advisory Board** — reviews and approves changes
- **Go/No-Go decision** — all stakeholders represented
- Critical, high-risk changes require CAB approval
- Emergency changes may have expedited approval process
- Some changes have **priority** — security patches may be fast-tracked

**Step 11 — Implementation and Peer Review:**
- Implement the change following documented procedure
- Peer review — another technician verifies the work
- Document everything done during implementation

**Step 12 — End User Acceptance:**
- User confirms the change achieved its goal
- System functioning as expected
- Close the change ticket

---

#### Change Types

| Type | Risk Level | Process |
|---|---|---|
| **Standard** | Low | Pre-approved — no CAB needed — routine, well-understood changes |
| **Normal** | Medium | Full CAB process — not urgent, scheduled |
| **Emergency** | High | Expedited approval — critical security issue or major outage |

---

### 4.3 Managing Backups

#### Why Backups Matter
- Protect against: hardware failure, ransomware, accidental deletion, corruption, disaster
- **A backup you cannot restore from is worthless** — test regularly
- Many organisations discover their backups don't work during an actual disaster

---

#### Backup Types

**Full Backup:**
- **Backs up everything** — entire selected dataset
- Longest backup time — most storage space required
- **Fastest restore** — everything in one backup set
- May be impractical to run every day for large datasets
- Typically run weekly

**Differential Backup:**
- Full backup taken first (on Sunday)
- Each subsequent backup contains **all data changed since the last FULL backup**
- Monday backup = changes since Sunday
- Wednesday backup = changes since Sunday (includes Monday's changes too)
- Backups get **larger each day** until next full backup
- **Restore = full backup + latest differential** (2 sets)
- Faster restore than incremental — only 2 sets needed

**Incremental Backup:**
- Full backup taken first (on Sunday)
- Each subsequent backup contains **only data changed since the last backup of ANY type**
- Monday backup = changes since Sunday
- Wednesday backup = changes since Monday only
- Backups stay **small** — only daily changes
- **Restore = full backup + ALL incrementals in order** (many sets)
- Slower restore — must apply each incremental in sequence

**Synthetic Full Backup:**
- **Creates a full backup** without running a full backup against live data
- Takes existing full backup + incrementals → combines them into new synthetic full
- Reduces backup window — no need to re-read all data from source
- Server does the work — not the live system

---

#### Backup Comparison Summary

| Type | What it backs up | Backup Speed | Storage Used | Restore Speed | Restore Uses |
|---|---|---|---|---|---|
| **Full** | Everything | Slowest | Most | Fastest | Full only |
| **Differential** | Changes since last FULL | Medium | Medium (grows daily) | Fast | Full + latest differential |
| **Incremental** | Changes since last backup | Fastest | Least | Slowest | Full + all incrementals |
| **Synthetic Full** | Everything (computed) | Fast | Most | Fastest | Synthetic full only |

**Exam tip:** Differential vs Incremental is heavily tested — know the difference clearly.

---

#### Backup Testing
- **It is not enough to perform the backup** — must verify it works
- **Disaster recovery testing** — simulate a real recovery scenario
- **Confirm the restoration** — actually restore files and verify they are intact and usable
- **Periodic audits** — regular scheduled backup verification
- Test different scenarios: single file recovery, full system recovery, bare metal restore

#### Recovery Options
- **In-place / Overwrite** — restore over existing system — overwrites current data
- **Alternative location** — restore to different system or folder — preserves current state
- Always test restore to alternative location first — non-destructive

#### On-Site vs Off-Site Backups

**On-site:**
- Fast access — restore quickly
- Risk: same disaster that affects production also affects backup (fire, flood, theft)

**Off-site:**
- Protected from local disaster
- Slower access — must retrieve or download
- Cloud backup = off-site by definition
- **Cybersecurity use:** Ransomware targets connected backup systems — off-site/offline backups are ransomware-proof

#### GFS — Grandfather-Father-Son Backup Rotation
- Three separate backup rotations running simultaneously:
  - **Son** — daily backups (kept for 1 week)
  - **Father** — weekly backups (kept for 1 month)
  - **Grandfather** — monthly backups (kept for 1 year)
- Provides multiple recovery points going back in time
- Balance between storage cost and recovery options

#### 3-2-1 Backup Rule
- **3** — three copies of data should always be available
- **2** — two different types of media (e.g. internal drive + external drive + cloud)
- **1** — one copy should be off-site (cloud counts)
- **Cybersecurity use:** Ransomware cannot encrypt what it cannot reach — offline/off-site backup is immune

---

### 4.4 Managing Electrostatic Discharge (ESD)

#### What is ESD?
- **Electrostatic Discharge** — sudden flow of static electricity between objects
- The static shock you feel touching a doorknob after walking on carpet
- **Very damaging to computer components** — can destroy chips instantly
- Even undetectable ESD (below human feeling threshold ~3,000V) can damage components
- Components most at risk: RAM, CPU, GPU, motherboard, SSD

#### Controlling ESD

**Humidity:**
- **Humidity above 60%** helps control ESD — moist air dissipates static
- Dry environments (below 30%) dramatically increase ESD risk
- Server rooms maintain controlled humidity

**Self-Grounding:**
- Touch a **metal part of the computer case** (unpainted) before touching components
- Discharges any static you are carrying before touching sensitive parts
- Do this every time before reaching inside a computer

**Anti-Static Wrist Strap:**
- **Most effective ESD protection** — worn on wrist, connected to ground point
- Continuously drains static as it builds up
- Clip to unpainted metal chassis of computer
- Must be worn throughout entire work session

**Anti-Static Mat:**
- Place on workbench — components placed on mat are grounded
- Combined with wrist strap = full ESD protection
- Mat connects to same ground point as wrist strap

**Anti-Static Pad:**
- Portable version of anti-static mat
- Use when working at a location without a dedicated workbench

**Anti-Static Bags:**
- **Pink or metallic silver bags** for storing and transporting components
- Never store components on regular plastic bags — generate static
- Always keep components in anti-static bags when not installed

#### Component Handling and Storage
- **Try not to touch components directly** — hold by edges, avoid PCB traces and chips
- **Never touch RAM contacts** or CPU pins directly
- Store in **HVAC-regulated environment** — controlled temperature and humidity
- **Avoid high humidity** — causes corrosion on contacts
- **Store in original packaging** — designed for ESD protection and physical protection

---

### 4.4 Safety Procedures

#### Electrical Safety

**Power Off Before Working:**
- Always power off and **unplug** before working inside a computer
- Laptops: remove battery AND unplug power adapter
- Servers: shut down properly, unplug all power cables

**Capacitors:**
- Hold electrical charge even after power removed
- CRT monitors and power supplies — dangerous capacitors
- **Never open a PSU or CRT** — capacitors can discharge fatally
- Wait several minutes after unplugging before touching internal components

**High Voltage Warning:**
- Laser printer fuser assembly — extremely hot AND high voltage
- UPS (Uninterruptible Power Supply) — contains large batteries, high current
- Always treat electrical equipment as live until confirmed otherwise

#### Physical Safety

**Lifting Techniques:**
- Heavy equipment: bend knees, keep back straight, lift with legs
- Get help for items over 20kg — server equipment is very heavy
- Use proper lifting equipment for rack-mounted servers

**Rack Safety:**
- Never extend more than one rack-mounted server at a time — rack can tip
- Use rack stabilisers and bolt racks to floor
- Fill empty rack spaces with blank panels — maintains airflow

**Cable Management:**
- Keep cables organised and secured — trip hazard
- Use cable ties, cable trays, cable management arms
- Label cables clearly — prevents accidental disconnection

#### Fire Safety

**Fire Extinguisher Types:**
| Class | Fire Type | Extinguisher |
|---|---|---|
| A | Wood, paper, cloth | Water, foam |
| B | Flammable liquids | CO2, foam, dry powder |
| C | Electrical fires | **CO2 or dry powder only** — NEVER water |
| D | Metal fires | Dry powder |

- **Class C — Electrical fires:** always use CO2 or dry chemical
- Water on electrical fire = electrocution risk
- Know location of nearest fire extinguisher before starting work

#### Chemical Safety

**Material Safety Data Sheet (MSDS) / Safety Data Sheet (SDS):**
- Document describing safe handling of chemicals
- Required for all chemical products
- Includes: hazards, first aid, storage, disposal procedures
- Know where MSDS/SDS are kept for all chemicals you use

**Printer Toner:**
- Fine particles — avoid breathing toner dust
- Do not use regular vacuum — toner passes through filters
- Use toner-specific vacuum or damp cloth
- Wash hands after handling toner cartridges

**Battery Disposal:**
- Lithium batteries — do not dispose in regular rubbish
- Take to designated recycling point
- Swollen batteries — do not puncture, handle carefully

#### Environmental Controls

**Temperature and Humidity:**
- Recommended server room: **18-27°C (64-80°F)**
- Recommended humidity: **40-60%**
- Hot aisle/cold aisle rack arrangement — maximises cooling efficiency
- HVAC failure = potential thermal shutdown of all equipment

**Ventilation:**
- Proper airflow around equipment
- Never block vents on computers or servers
- Remove blanking panels from racks only when equipment is installed

---

## 🔑 Exam Focus Summary

**Ticketing Systems:**
- Document → Assign → Resolve → Report
- User info, device info, categorisation, escalation, progress notes, resolution

**Asset Management:**
- CMDB = central asset tracking
- Asset tag = unique physical identifier
- Procurement lifecycle = request → approve → purchase → deploy → manage → dispose

**Document Types:**
- SOP = step-by-step operational procedures
- SLA = minimum service contract terms
- Onboarding = create accounts + provide hardware + sign agreements
- Offboarding = disable accounts immediately + collect hardware

**Change Management:**
- Nothing changes without the formal process
- Always have rollback plan + backups before changing
- Sandbox test before production
- CAB = Change Advisory Board approves changes
- Standard (low) → Normal (medium) → Emergency (high)
- Change freeze = no changes during critical periods

**Backup Types:**
- Full = everything, slowest backup, fastest restore
- Differential = since last FULL, medium storage, 2 sets to restore
- Incremental = since last backup, smallest, slowest restore (many sets)
- 3-2-1 rule = 3 copies, 2 media types, 1 offsite

**ESD:**
- Anti-static wrist strap = most effective protection
- Anti-static bag = pink or silver metallic
- Humidity >60% reduces ESD risk
- Touch metal chassis before touching components

**Safety:**
- Class C fire (electrical) = CO2 or dry chemical — NEVER water
- Never open PSU or CRT — dangerous capacitors
- Lift with legs not back
- MSDS/SDS = chemical safety documents

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. Differential vs Incremental backup — differential grows daily (all changes since full), incremental stays small (only today's changes) — differential restores faster, incremental uses less storage
2. Change management always requires a rollback plan AND sandbox testing before production — most IT outages are self-inflicted through uncontrolled changes
3. Class C electrical fires require CO2 or dry chemical extinguisher — water causes electrocution — know fire extinguisher classes for the exam