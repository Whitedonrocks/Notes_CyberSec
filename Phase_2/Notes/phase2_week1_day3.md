# CCNA 200-301 — Phase 2 Week 1 Day 3 Notes

**Lab Files:** https://drive.google.com/drive/folders/1PwK_jWqfUtOjV7gHt8ODutq9QA5cxCgi

---

## Videos Watched
- ✅ Day 3 — Cisco IOS CLI & Basic Configuration
- ✅ Day 3-Lab — Basic Device Security

---

## Key Concepts

### Cisco IOS CLI

#### What is CLI?
- **CLI (Command Line Interface)** is a text-based interface used to interact with network devices
- Used to configure, monitor, and troubleshoot devices

---

#### GUI (Graphical User Interface)
- Uses visual elements (buttons, menus)
- Easier but less powerful than CLI
- CLI is preferred in networking

---

### Connecting to a Cisco Device

#### Console Connection
- Used for initial device setup
- Connect PC → device using console (rollover) cable

---

#### Rollover Cable
- RJ-45 to serial/USB cable
- Pin mapping is reversed:

| Pin | Connects To |
|---|---|
| 1 | 8 |
| 2 | 7 |
| 3 | 6 |
| 4 | 5 |
| 5 | 4 |
| 6 | 3 |
| 7 | 2 |
| 8 | 1 |

---

#### Terminal Emulator
- Used to access CLI
- Example: PuTTY

---

### Cisco IOS Modes

#### User EXEC Mode
- Prompt: `hostname>`
- Limited access
- Basic monitoring only

---

#### Privileged EXEC Mode
- Enter using: enable
- Prompt: `hostname#`
- Full access

---

#### Global Configuration Mode
- Enter using: configure terminal
- Prompt: `hostname(config)#`
- Used for configuration

---

### Password Configuration

#### Enable Password
- Command: enable password <password>
- Case-sensitive
- Stored in plain text (less secure)

---

#### Enable Secret
- Command: enable secret <password>
- Encrypted (more secure)
- Overrides enable password

---

#### Service Password Encryption
- Command: service password-encryption
- Encrypts all plain-text passwords

---

### Configuration Files

#### Running Configuration
- Active configuration currently in use
- Changes apply immediately

---

#### Startup Configuration
- Saved configuration used on reboot
- Stored in NVRAM

---

### Canceling Commands

- Use `no` to remove a command:
  no <command>

Example:
  no enable password

---

## Terminal / CLI Practice

    # Enter privileged mode
    enable

    # Enter global configuration mode
    configure terminal

    # Set passwords
    enable password cisco
    enable secret strongpassword

    # Encrypt passwords
    service password-encryption

    # View configuration
    show running-config

    # Save configuration
    copy running-config startup-config

---

## 🔑 Exam Focus Summary
**CLI** = command-line interface for Cisco devices  
**User EXEC Mode** = limited access (`>`)  
**Privileged EXEC Mode** = full access (`#`)  
**Global Config Mode** = `(config)#`  
**enable** → move to privileged mode  
**configure terminal** → enter config mode  
**enable password vs enable secret** (secret is encrypted and preferred)  
**running-config** = active config  
**startup-config** = saved config  
**service password-encryption** encrypts passwords  
**no command** removes configuration  

---

## What I Didn't Understand
-

---

## 3 Key Things I Learned
1. The difference between CLI and GUI and why CLI is preferred  
2. The hierarchy of Cisco IOS modes and how to navigate them  
3. The importance of securing access using enable secret and encryption  