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
- The **best way to manage support requests** — tracks every issue from start to finish
- Every support interaction becomes a **ticket** — documented, assigned, resolved, reported
- Usually the responsibility of the **help desk**
- Examples: ServiceNow, Jira Service Management, Zendesk, Freshdesk, osTicket (free)
- **Cybersecurity use:** Ticketing systems create an audit trail — every security incident, change, and resolution is documented

#### Managing a Support Ticket

**Information Gathering:**
- Collect all relevant details before attempting resolution
- Ask the right questions — reproduce the issue if possible
- Do not assume — gather facts first

**Applying Context:**
- What changed recently? New software? Windows update? New hardware?
- Is this affecting one user or many? Scope of issue?
- Has this happened before? Previous ticket history?

**Clear and Concise Communication:**
- Use plain language — no jargon with end users
- Set expectations — estimated resolution time
- Keep user informed of progress

#### Ticket Fields — What Every Ticket Contains

**User Information:**
- Name, contact details, department
- User ID / employee number
- Location — building, floor, desk number

**Device Information:**
- Device name / hostname
- Make and model
- Serial number / asset tag
- Operating system version

**Problem Description:**
- Clear description of the issue
- Steps to reproduce
- Error messages — exact text
- When it started

**Categorisation:**
- Type: hardware, software, network, security, account
- Priority: critical, high, medium, low
- Severity: how many users affected

**Escalation:**
- Tier 1 (help desk) → Tier 2 (specialist) → Tier 3 (vendor/developer)
- Escalate when: issue beyond current skill level, SLA at risk, security incident

**Progress Notes:**
- Document every action taken and result
- Time-stamped — who did what and when
- Critical for handover between technicians

**Problem Resolution:**
- Root cause identified
- Solution applied
- User confirmation that issue is resolved
- Lessons learned for knowledge base

---

### 4.1 Asset Management

#### What is Asset Management?
- A **record of every asset** in the organisation
- Know what you have, where it is, who has it, and its status
- Associates support tickets with specific devices
- Used for: **financial records, audits, depreciation, compliance**

#### Asset Tags
- Unique identifier attached to every physical asset
- Barcode, QR code, or RFID tag
- Scanned to instantly identify device and pull up its record
- **Cybersecurity use:** Asset tags help identify unauthorised devices on the network

#### CMDB — Configuration Management Database
- **Central asset tracking system** — the single source of truth for all IT assets
- Stores for each asset:
  - Device details (make, model, serial number, specs)
  - **Assigned user** — who is responsible for it
  - **Location** — which office, building, room
  - **Warranty** information — expiry date, support contract
  - **Licensing** — software licences assigned to device
  - Purchase date and cost
  - Maintenance history
  - Configuration details
- **Cybersecurity use:** CMDB enables rapid incident response — instantly know what systems are affected, who to contact, what software is running

#### Procurement Life Cycle
The full journey of an asset from need to disposal:

1. **Request** — user or department requests new hardware/software
2. **Approval** — manager or IT approves request and budget
3. **Negotiate with suppliers** — get quotes, compare vendors, negotiate price
4. **Purchase** — raise purchase order
5. **Invoice and payment** — receive invoice, process payment
6. **Receive and configure** — unbox, set up, add to CMDB
7. **Deploy** — assign to user, record in asset management system
8. **Maintain** — updates, repairs, support tickets linked to asset
9. **Depreciation** — track asset value reduction over time (for accounting)
10. **Disposal** — secure data destruction, remove from CMDB, comply with environmental regulations

---

### 4.1 Document Types

#### Incident Reports
- Formal documentation of a **security or operational incident**
- Required by security policy — all incidents must be documented
- Contains: what happened, when, who was affected, how resolved, lessons learned
- Used for: compliance, insurance claims, legal proceedings, preventing recurrence
- **Cybersecurity use:** Incident reports are legally required in many industries — HIPAA, GDPR require breach notification and documentation

#### SOP — Standard Operating Procedures
- Step-by-step instructions for performing **routine tasks**
- Organisations have different business objectives — SOPs ensure consistency
- Cover: software installation and upgrades, security configurations, onboarding, troubleshooting steps
- **Documentation is the key** — if it's not written down, it doesn't exist
- Benefits: consistency, training new staff, compliance, quality control
- **Cybersecurity use:** Security SOPs define how to respond to incidents — without them, response is chaotic

#### Onboarding Documentation
- Process of **bringing a new person into the organisation**
- IT tasks for onboarding:
  - **IT agreements signed** — acceptable use policy, NDA, security policy
  - **Create accounts** — Active Directory, email, applications
  - **Provide required IT hardware** — laptop, phone, access card
  - **Configure device** — install required software, apply security policies
  - **Provide access** — network shares, applications, VPN
  - Train on security policies and acceptable use
- **Cybersecurity use:** New accounts should follow least privilege — only access needed for role

#### Offboarding Documentation
- Process of **removing a departing employee** from all systems
- **Must be predefined** — clear process executed immediately on departure
- IT tasks:
  - **Disable accounts** (not delete — preserve audit trail)
  - Revoke VPN and remote access
  - Recover all company hardware — laptop, phone, access cards
  - **Determine what happens to data** — archive emails, transfer files to manager
  - Remove from all systems and groups
  - Change shared passwords the employee knew
- **Cybersecurity use:** Insider threat — disgruntled employees cause 60% of data breaches. Account must be disabled the moment they leave — before they leave if possible.

#### SLA — Service Level Agreement
- **Minimum terms for services provided** — contractual commitment
- Contract between service provider and customer
- Defines: uptime guarantees, response times, resolution times, penalties for failure
- Example: ISP SLA — 99.9% uptime, 4-hour response to outages
- **Cybersecurity use:** Security SLAs define incident response times — how quickly must a breach be contained?

#### Knowledge Base and Articles
- **Repository of solutions** to common problems
- Sources:
  - **External** — vendor documentation, community forums, online resources
  - **Internal** — organisation-specific solutions, workarounds, procedures
- Purpose: find solutions quickly without reinventing the wheel
- Build from resolved tickets — every solution becomes a knowledge base article
- **Cybersecurity use:** Security knowledge base includes: IOCs (Indicators of Compromise), known attack patterns, response procedures

---

### 4.2 Change Management

#### What is Change Management?
- Formal process for managing **any change to IT systems**
- One of the **most common sources of risk** in enterprise — changes break things
- Often overlooked or ignored — but critical for stability
- **Nothing changes without going through the process**

#### Why Change Management Matters
- Uncontrolled changes cause: outages, security vulnerabilities, compliance failures
- Documented changes enable: rollback, troubleshooting, audit trails
- **Cybersecurity use:** Unauthorised changes are a major security risk — attacker making changes to firewall rules would show up in change management

---

#### Change Management Process

**1. Change Request:**
- Formal paperwork — nothing gets missed
- Usually transparent — visible to all stakeholders
- Submitted by person requesting change

**2. Purpose of the Change:**
- Why are we doing this? Must have a good reason
- Common reasons:
  - Application upgrades
  - Security fixes / patch management
  - Performance improvements
  - Hardware replacement
  - Regulatory compliance

**3. Scope of the Change:**
- What exactly will be changed?
- What systems will be affected?
- How long will it take?
- A single change can have far-reaching effects — map all dependencies

**4. Change Types:**

| Type | Risk Level | Urgency | Approval |
|---|---|---|---|
| **Standard** | Low | Routine | Pre-approved — no board needed |
| **Normal** | Medium | Not urgent | Full CAB review |
| **Emergency** | High | Urgent | Expedited approval |

**5. Date and Time of Change:**
- **Maintenance window** — scheduled time when changes are allowed
- **On-demand change windows** — ad-hoc approved windows
- **Regularly scheduled downtime** — weekly/monthly maintenance periods
- **Change freeze** — period when NO changes allowed (e.g. before major holidays, during critical business periods)

**6. Affected Systems and Impact:**
- List every system that will be affected
- Estimate downtime — communicate to users in advance
- Test in sandbox first — always

**7. Risk Analysis:**
- What could go wrong?
- Probability × Impact = Risk level
- What is the impact if it fails?

**8. Rollback Plan:**
- **Always have a way to revert** — before making any change
- Always have backups taken immediately before change
- Test the rollback plan — don't assume it works

**9. Backup Plan (Plan B, C, D):**
- What if the change fails partway through?
- What if the rollback also fails?
- Example: installing firewall update — what if new firmware is corrupt?
- Multiple contingency plans prepared before starting

**10. Sandbox Testing:**
- Test change in **isolated environment** that mirrors production
- Confirm the change works as expected
- Confirm the rollback plan works
- Never test a critical change in production first

**11. Responsible Staff Members:**
- A team effort — not one person's decision
- IT team — technical implementation
- Business customer — accepts the risk and downtime
- Organisation sponsor — authorises the change

**12. Change Advisory Board (CAB) and Approvals:**
- **Go / No-Go decision**
- All important parts of the organisation represented
- Some changes have priority — fast-tracked through board
- Board reviews: purpose, scope, risk, rollback plan

**13. Implementation and Peer Review:**
- Implement during approved window
- Another technician reviews the change — fresh eyes catch mistakes
- Document every step taken

**14. End-User Acceptance:**
- Confirm with users that the change achieved its purpose
- Sign-off from business customer
- Close the change request

---

### 4.3 Managing Backups

#### Why Backups Are Critical
- Hardware fails, ransomware encrypts, humans delete things accidentally
- Without backups: data is permanently lost
- **A backup you haven't tested is not a backup** — test regularly

#### Backup Types

**Full Backup:**
- Backs up **everything** — all selected data
- **Longest backup time** — may be impractical every day
- **Fastest restore** — everything in one backup set
- Usually done weekly or monthly

**Differential Backup:**
- Full backup taken first as baseline
- Each subsequent backup contains **all data changed since the last FULL backup**
- Gets larger over time — each differential is bigger than the last
- **Faster backup than full** — only changed data
- **Restore requires: Full backup + latest differential only**
- Medium restore complexity — two items needed

**Incremental Backup:**
- Full backup taken first as baseline
- Each subsequent backup contains **only data changed since the last backup of ANY type** (full or incremental)
- **Fastest backup** — smallest amount of data each time
- **Slowest restore** — need full backup + EVERY incremental in sequence
- **Restore requires: Full backup + all incrementals in order**

**Synthetic Full Backup:**
- Created from existing full + incrementals — no backup window needed
- Server synthesises a new full backup from existing backups
- Combines benefits: fast backup (incremental) + fast restore (full)
- No impact on production systems during creation

#### Backup Types Summary Table

| Type | What is Backed Up | Backup Speed | Restore Speed | Restore Needs |
|---|---|---|---|---|
| **Full** | Everything | Slowest | Fastest | Full backup only |
| **Differential** | Changes since last FULL | Medium | Medium | Full + latest differential |
| **Incremental** | Changes since last backup | Fastest | Slowest | Full + ALL incrementals |
| **Synthetic Full** | Server-created full | No window needed | Fastest | Synthetic full only |

**Exam tip:** Differential vs Incremental is heavily tested — know the difference in what they back up and what's needed for restore.

---

#### Backup Testing
- **Not enough to perform the backup** — must verify it works
- **Disaster recovery testing** — simulate actual failure scenario
- **Confirm the restoration** — actually restore from backup and verify data integrity
- **Periodic audits** — review backup logs, check for failures
- Test restoration at least quarterly — annually at minimum
- **Cybersecurity use:** Ransomware gangs now target backup systems first — verify backups are offline or air-gapped

#### Recovery Options
- **In-place / Overwrite** — restore to same location — overwrites existing data
- **Alternative location** — restore to different server/path — safer, preserves original

#### On-Site vs Off-Site Backups

| | On-Site | Off-Site |
|---|---|---|
| **Speed** | Fast restore | Slower restore |
| **Cost** | Lower | Higher |
| **Risk** | Fire/flood destroys both data and backup | Protected from local disasters |
| **Examples** | External HDD, NAS, tape library | Cloud backup, remote data centre, tape vault |

**Best practice:** Both on-site AND off-site — different risks covered

#### Grandfather-Father-Son (GFS) Rotation
- Three separate backup rotations — different frequencies:
  - **Son** — daily backups — kept for one week
  - **Father** — weekly backups — kept for one month
  - **Grandfather** — monthly backups — kept for one year
- Provides multiple recovery points going back up to a year
- Minimises media usage — older backups cover longer periods

#### 3-2-1 Backup Rule — Must Memorise
- **3** copies of data should always be available
- **2** different types of media should be used (e.g. HDD + cloud)
- **1** copy should be offsite (cloud, remote location, tape vault)
- **Cybersecurity use:** Ransomware cannot encrypt offline/offsite backups — 3-2-1 ensures recovery even from ransomware

---

### 4.4 Managing Electrostatic Discharge (ESD)

#### What is ESD?
- **Electrostatic Discharge** — sudden flow of static electricity between objects
- The shock you feel touching a doorknob after walking on carpet
- **Can be very damaging to computer components** — even discharges you cannot feel (below 3,000V human threshold) can destroy sensitive electronics
- CMOS chips, CPUs, RAM, and other ICs can be permanently damaged by ESD

#### Controlling ESD

**Humidity:**
- Humidity **over 60%** helps control ESD — moisture dissipates static charge
- Dry air (winter, air conditioning) increases ESD risk
- Data centres maintain controlled humidity

**Self-Grounding:**
- Touch a metal part of the case before handling components
- Equalises static charge between you and the equipment

**Anti-Static Wrist Strap:**
- Most effective personal ESD protection
- Connects your wrist to ground via resistor — continuously drains static charge
- Must be worn against skin — not over clothing
- Test strap regularly — broken strap provides no protection

**Anti-Static Mat:**
- Work surface that dissipates static charge
- Components placed on mat are protected
- Connect mat to ground

**Anti-Static Pad:**
- Similar to mat — portable version
- Place under components while working

**Anti-Static Bag:**
- For storing and transporting components
- **Never place components ON TOP of an anti-static bag** — outside is not protected, only inside
- Pink/silver metallic bags — for storage and shipping

#### Component Handling and Storage
- **Try not to touch components directly** — hold by edges, avoid touching chips and connectors
- **Store in HVAC-regulated environment** — temperature and humidity controlled
- **Avoid high humidity** — can cause corrosion and condensation
- **Store in original packaging** — anti-static bags, foam padding
- Handle circuit boards by edges — avoid touching gold connectors

---

### 4.4 Safety Procedures

#### Electrical Safety
- **Never work on powered equipment** — power off and unplug before opening
- **Capacitors hold charge** after power removed — can deliver lethal shock even unplugged
  - CRT monitors, UPS systems, power supplies — dangerous after power removed
  - Allow capacitors to discharge before working — can take minutes
- **One hand rule** — keep one hand behind your back or in pocket when probing live circuits — prevents current flowing across chest through heart
- **High voltage warning labels** — never open equipment with these labels without training
- Laser printers — **fuser assembly** runs at ~200°C — allow to cool before servicing

#### Lifting Safety
- **Lift with legs not back** — bend knees, keep back straight
- **Team lift** for heavy items — servers, UPS units, large printers
- Get help for anything over 20kg (approximately)
- Use **equipment trolleys** for moving heavy server equipment
- Clear path before moving equipment

#### Fire Safety
- **Never use water on electrical fire** — electrical fires require Class C extinguisher
- **Fire extinguisher types:**
  - **Class A** — ordinary combustibles (wood, paper)
  - **Class B** — flammable liquids
  - **Class C** — electrical equipment ← most relevant for IT
  - **Class D** — metal fires
  - **ABC extinguisher** — covers most situations
- Know fire exit locations
- Never block fire exits with equipment

#### Chemical Safety
- **SDS — Safety Data Sheet** (formerly MSDS — Material Safety Data Sheet)
  - Document describing hazards, handling, storage, and disposal of chemicals
  - Required for all hazardous materials in workplace
  - Toner, cleaning solvents, batteries all have SDS
- **Toner** — fine particles, potential carcinogen — never breathe, use toner vacuum
- **Batteries** — lithium batteries can cause fire if punctured or swollen
- **Cleaning solvents** — isopropyl alcohol is flammable — keep away from heat

#### Environmental Safety
- **Proper disposal** of hazardous materials:
  - **Batteries** — lithium, NiMH — must be recycled, not landfill
  - **CRT monitors** — contain lead — hazardous waste disposal required
  - **Toner cartridges** — recycle through manufacturer programs
  - **Fluorescent bulbs** — contain mercury — special disposal
- **WEEE compliance** (EU) — Waste Electrical and Electronic Equipment directive
- E-waste recycling programs — many manufacturers offer take-back programs

#### Personal Protective Equipment (PPE)
- **Safety glasses** — when working with components that may break or spray
- **Anti-static strap** — ESD protection
- **Gloves** — when handling hot components or chemicals
- **Dust mask** — when working in dusty environments or cleaning printers

#### Workspace Safety
- **Keep workspace clean** — clutter causes accidents
- **Cable management** — loose cables are trip hazards
- **Tools in proper storage** — prevent falls and injuries
- **Proper lighting** — prevent eye strain and mistakes
- **No food or drinks near equipment** — spills cause damage and safety hazards

---

## 🔑 Exam Focus Summary

**Ticketing Systems:**
- Document, assign, resolve, report — every ticket
- Escalation tiers: Tier 1 → 2 → 3
- Progress notes critical for handover

**Asset Management:**
- CMDB = central asset tracking database
- Asset tags for physical identification
- Procurement lifecycle — request to disposal

**Change Management:**
- Change types: Standard (low), Normal (medium), Emergency (high)
- Always have rollback plan AND backup plan
- Sandbox test before production
- CAB = Change Advisory Board — go/no-go
- Change freeze = no changes during critical periods

**Backup Types — Most Tested:**
- Full = everything, slowest backup, fastest restore
- Differential = since last FULL, medium speed, needs full + differential
- Incremental = since last backup, fastest backup, slowest restore, needs all incrementals
- 3-2-1 rule = 3 copies, 2 media types, 1 offsite

**ESD:**
- Anti-static wrist strap = most effective protection
- Never place components ON TOP of anti-static bag
- Humidity over 60% helps control ESD

**Safety:**
- Class C extinguisher for electrical fires — NEVER water
- Lift with legs not back
- SDS = Safety Data Sheet for hazardous materials
- Capacitors hold charge after power removed — dangerous

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. Differential backup stores everything since last FULL — incremental stores only since last backup of any type — differential is faster to restore (2 items) but slower to backup than incremental
2. 3-2-1 backup rule — 3 copies, 2 media types, 1 offsite — ransomware cannot encrypt offline backups — this is why 3-2-1 is the gold standard
3. Change management always requires a rollback plan AND a backup plan — never make a production change without both — one of the most common causes of enterprise outages is uncontrolled changes