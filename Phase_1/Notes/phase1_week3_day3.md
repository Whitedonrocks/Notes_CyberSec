# CompTIA A+ 220-1202 — Week 3 Day 3 Notes

---

## Videos Watched
- ✅ 1.8 macOS Overview
- ✅ 1.8 macOS System Preferences
- ✅ 1.8 macOS Features
- ✅ 1.9 Linux
- ✅ 1.9 Linux Commands Part 1
- ✅ 1.9 Linux Commands Part 2

---

## Key Concepts

### 1.8 macOS Overview

#### What is macOS?
- Apple's **desktop operating system** — runs exclusively on Apple hardware
- Based on **Unix** — shares DNA with Linux
- Current versions: macOS Ventura, Sonoma, Sequoia
- Known for: stability, security, creative professional use
- Tight hardware+software integration — Apple controls both

#### macOS Desktop Components

**Finder:**
- macOS equivalent of Windows File Explorer
- Manage files, folders, network drives, external drives
- Sidebar: Favourites, iCloud Drive, Locations, Tags
- Always running — cannot be closed

**Dock:**
- Bar at bottom of screen (like Windows taskbar)
- Pinned apps + running apps (shown with dot underneath)
- Can move to left, right, or bottom
- Trash is always at the right end of the Dock

**Menu Bar:**
- Always at the top of the screen — changes based on active app
- Left side: Apple menu, app name, app menus
- Right side: system status icons (Wi-Fi, battery, time, Spotlight)

**Apple Menu (top left):**
- About This Mac — system info (RAM, CPU, macOS version)
- System Preferences/Settings — configure everything
- App Store — install apps
- Sleep, Restart, Shut Down, Log Out

**Mission Control:**
- Overview of all open windows and virtual desktops (Spaces)
- Open: swipe up with 3 fingers or press F3
- Create Spaces — multiple virtual desktops for organisation

**Spotlight Search:**
- System-wide search — files, apps, settings, web, calculator
- Open: `Cmd + Space`
- Type anything — finds it instantly
- **Cybersecurity use:** Spotlight indexes all files — can reveal sensitive files

---

#### macOS Key Differences from Windows

| Feature | macOS | Windows |
|---|---|---|
| File system | APFS | NTFS |
| Package manager | Homebrew (third party) | Windows Store / winget |
| Terminal | Terminal.app (zsh) | CMD / PowerShell |
| Task Manager | Activity Monitor | Task Manager |
| Control Panel | System Preferences/Settings | Control Panel / Settings |
| Registry | Plist files | Registry |
| Drive format | HFS+/APFS | NTFS |
| App installation | .dmg / .pkg / App Store | .exe / .msi / Store |

---

### 1.8 macOS System Preferences / Settings

> Called **System Preferences** on older macOS, renamed **System Settings** on macOS Ventura+

#### Key Settings Sections to Know for Exam

**General:**
- Appearance — light/dark mode
- Default web browser
- Handoff — continuity between Apple devices

**Desktop & Screen Saver:**
- Wallpaper and screen saver settings
- Hot corners — assign actions to screen corners

**Dock & Menu Bar:**
- Dock size, position, auto-hide
- Menu bar icon management

**Mission Control:**
- Spaces settings, hot corners

**Siri:**
- Enable/disable, shortcut key

**Security & Privacy:**
- General — require password after sleep, allow apps from App Store only vs anywhere
- FileVault — full disk encryption (macOS equivalent of BitLocker)
- Firewall — macOS built-in firewall
- Privacy — app permissions (camera, microphone, location, contacts)
- **Exam focus:** FileVault = BitLocker equivalent on macOS
- **Cybersecurity use:** FileVault encrypts entire drive with AES-XTS 128-bit encryption

**Network:**
- Configure Wi-Fi, Ethernet, VPN
- Network diagnostics

**Bluetooth:**
- Pair/unpair devices

**Sound:**
- Input/output device selection, volume

**Printers & Scanners:**
- Add/manage printers (uses CUPS — same as Linux!)

**Energy Saver / Battery:**
- Sleep settings, battery health management

**Date & Time:**
- Timezone, NTP sync

**Sharing:**
- Enable file sharing, screen sharing, remote login (SSH), AirPlay receiver
- **Cybersecurity use:** Remote Login enables SSH — if enabled, Mac accessible over network

**Users & Groups:**
- Create/delete user accounts
- Login items — apps that start at login (like Windows Startup)
- **Cybersecurity use:** Check login items for unknown entries — malware persistence

**Time Machine:**
- Automated backup to external drive
- Keeps hourly, daily, weekly backups
- Can browse and restore previous file versions

---

### 1.8 macOS Features

#### Key macOS Features to Know

**FileVault:**
- **Full disk encryption** for macOS — BitLocker equivalent
- Encrypts entire startup drive using AES-XTS 128-bit
- Uses your login password as the encryption key
- Recovery key generated during setup — store safely
- Enable: System Preferences → Security & Privacy → FileVault
- **Exam focus:** FileVault = macOS full disk encryption

**Keychain:**
- macOS **password manager** built into the OS
- Stores: website passwords, Wi-Fi passwords, certificates, encryption keys
- Syncs across Apple devices via iCloud Keychain
- Access: Keychain Access app
- **Cybersecurity use:** Keychain stores all saved passwords — attacker with physical access + login password can extract all credentials

**Terminal:**
- Command line interface for macOS
- Default shell: **zsh** (changed from bash in macOS Catalina)
- Same Unix commands as Linux — `ls`, `cd`, `grep`, `chmod` etc.
- Located: Applications → Utilities → Terminal
- **Exam focus:** macOS uses Unix commands — same as Linux

**iCloud:**
- Apple's cloud storage and sync service
- Syncs: Desktop, Documents, Photos, Contacts, Calendar, Mail
- iCloud Drive = Apple's Dropbox/Google Drive
- 5GB free, paid tiers available

**AirDrop:**
- Wireless file sharing between nearby Apple devices
- Uses Bluetooth + Wi-Fi — no internet needed
- Works between Mac, iPhone, iPad
- Three settings: Off, Contacts Only, Everyone
- **Cybersecurity use:** "Everyone" setting allows any nearby Apple device to send files — potential attack vector

**Handoff:**
- Continue tasks seamlessly between Apple devices
- Start email on iPhone → continue on Mac
- Works with: Mail, Safari, Maps, Messages, Notes

**Spotlight:**
- System-wide search — `Cmd + Space`
- Searches files, apps, emails, calendar, web, definitions, calculator

**Time Machine:**
- Automated backup system
- Connects external drive → Time Machine backs up automatically
- Hourly backups for last 24 hours, daily for last month, weekly for older
- Browse backup history like a timeline

**Boot Camp (Intel Macs only):**
- Run Windows natively on Intel Mac hardware
- Dual boot — choose macOS or Windows at startup
- **No longer available on Apple Silicon (M1/M2/M3) Macs**

**Activity Monitor:**
- Task Manager equivalent for macOS
- Shows: CPU, Memory, Energy, Disk, Network usage per process
- Force quit unresponsive apps
- **Cybersecurity use:** Check for suspicious processes consuming CPU/network

**Force Quit:**
- `Cmd + Option + Esc` — opens Force Quit window
- Kill unresponsive applications
- Equivalent of Windows Task Manager End Task

**Disk Utility:**
- Format, partition, repair drives
- First Aid — check and repair disk errors (like chkdsk)
- Create disk images (.dmg files)

---

### 1.9 Linux

#### What is Linux?
- **Free, open source** operating system kernel created by Linus Torvalds in 1991
- Based on Unix principles
- Foundation of: Android, Chrome OS, most web servers, cloud infrastructure, security tools
- Many distributions (distros) — same kernel, different software packages

#### Linux Distributions to Know

| Distro | Base | Use Case |
|---|---|---|
| Ubuntu | Debian | General use, beginners (what you use!) |
| Debian | - | Stable, basis for many others |
| Red Hat Enterprise Linux (RHEL) | - | Enterprise, paid support |
| Fedora | RHEL | Cutting edge, developer focused |
| CentOS / Rocky Linux | RHEL | Free RHEL alternative for servers |
| Kali Linux | Debian | Penetration testing (your Phase 3!) |
| Arch Linux | - | Advanced users, highly customisable |
| openSUSE | - | Enterprise, developer friendly |

#### Linux File System Hierarchy

```
/                   Root directory — top of everything
├── /bin            Essential binaries (ls, cp, mv, cat)
├── /sbin           System binaries (mount, ifconfig) — admin only
├── /etc            Configuration files for all programs
├── /home           User home directories (/home/whitedonrocks)
├── /root           Root user's home directory
├── /var            Variable data (logs, mail, databases)
│   └── /var/log    System log files
├── /tmp            Temporary files — cleared on reboot
├── /usr            User programs and data
│   ├── /usr/bin    User commands
│   └── /usr/local  Locally installed software
├── /opt            Optional/third-party software
├── /dev            Device files (disks, terminals)
├── /proc           Virtual filesystem — running process info
├── /sys            Virtual filesystem — kernel/hardware info
├── /mnt            Mount point for temporary mounts
└── /media          Auto-mount point for removable media
```

**Exam focus:** Know the key directories — especially /etc, /home, /var/log, /tmp

---

### 1.9 Linux Commands Part 1 — Complete Reference

#### Getting Help
```bash
man ls              # manual page for ls command
man -k keyword      # search manual pages for keyword
ls --help           # quick help for a command
info ls             # detailed info page
whatis ls           # one-line description of command
```

---

#### Navigation Commands
```bash
pwd                 # print working directory — where am I?
ls                  # list files in current directory
ls -l               # long format — permissions, size, date
ls -a               # show hidden files (starting with .)
ls -la              # long format + hidden files
ls -lh              # long format with human-readable sizes
ls -lt              # sort by modification time (newest first)
ls -R               # recursive — list all subdirectories
cd /home/user       # change to absolute path
cd Documents        # change to relative path
cd ..               # go up one directory
cd ~                # go to home directory
cd -                # go back to previous directory
```

**Exam tip:** `ls -la` is one of the most tested commands — know all flags

---

#### File and Directory Operations
```bash
# Creating
touch filename.txt          # create empty file / update timestamp
mkdir foldername            # create directory
mkdir -p path/to/folder     # create nested directories

# Copying
cp file.txt destination/    # copy file
cp -r folder/ destination/  # copy directory recursively
cp -p file.txt dest/        # copy preserving permissions and timestamps

# Moving and Renaming
mv file.txt destination/    # move file
mv oldname.txt newname.txt  # rename file
mv folder/ /new/location/   # move directory

# Deleting
rm file.txt                 # delete file (no recycle bin!)
rm -r folder/               # delete directory recursively
rm -rf folder/              # force delete — no confirmation (DANGEROUS)
rm -i file.txt              # interactive — ask before deleting

# Linking
ln file.txt hardlink        # create hard link
ln -s file.txt symlink      # create symbolic link (shortcut)
```

**Exam tip:** `rm -rf` is dangerous — no undo. Know the difference between hard link and symbolic link.

---

#### Viewing File Contents
```bash
cat file.txt                # print entire file to screen
cat -n file.txt             # print with line numbers
less file.txt               # view file page by page (q to quit)
more file.txt               # older pager — view page by page
head file.txt               # show first 10 lines
head -n 20 file.txt         # show first 20 lines
tail file.txt               # show last 10 lines
tail -n 20 file.txt         # show last 20 lines
tail -f /var/log/syslog     # follow file — live updates (great for logs)
```

**Exam tip:** `tail -f` is essential for monitoring log files in real time

---

#### Searching and Filtering
```bash
grep "word" file.txt            # search for word in file
grep -i "word" file.txt         # case-insensitive search
grep -r "word" /directory/      # recursive search in directory
grep -n "word" file.txt         # show line numbers
grep -v "word" file.txt         # show lines NOT containing word
grep -l "word" /dir/*.txt       # list files containing word
grep -c "word" file.txt         # count matching lines

find / -name "file.txt"         # find file by name from root
find /home -name "*.txt"        # find all .txt files in /home
find / -type f -name "passwd"   # find files (not directories)
find / -type d -name "config"   # find directories
find / -mtime -7                # files modified in last 7 days
find / -size +100M              # files larger than 100MB
find / -perm 777                # files with 777 permissions

locate filename                 # fast search using database
updatedb                        # update locate database (run as root)

which ls                        # show full path of command
whereis ls                      # show binary, source, manual locations
```

**Exam tip:** Know `grep` flags especially `-i`, `-r`, `-v`, `-n`. Know `find` vs `locate`.

---

#### File Permissions — Critical for Exam

```bash
ls -l file.txt
# Output: -rwxr-xr-- 1 user group 1234 Apr 1 10:00 file.txt
```

**Permission string breakdown:**
```
- rwx r-x r--
│ │   │   │
│ │   │   └── Other (everyone else): r-- = read only
│ │   └────── Group: r-x = read and execute
│ └────────── Owner: rwx = read, write, execute
└──────────── File type: - = file, d = directory, l = symlink
```

**Permission values:**
| Permission | Symbol | Value |
|---|---|---|
| Read | r | 4 |
| Write | w | 2 |
| Execute | x | 1 |
| None | - | 0 |

**chmod — change permissions:**
```bash
# Symbolic method
chmod u+x file.txt          # add execute for owner (user)
chmod g-w file.txt          # remove write for group
chmod o+r file.txt          # add read for others
chmod a+x file.txt          # add execute for all (a = all)
chmod u=rwx,g=rx,o=r file   # set exact permissions

# Numeric (octal) method — EXAM FAVOURITE
chmod 755 file.txt          # rwxr-xr-x
chmod 644 file.txt          # rw-r--r--
chmod 777 file.txt          # rwxrwxrwx (dangerous — everyone has full access)
chmod 600 file.txt          # rw------- (owner only)
chmod 400 file.txt          # r-------- (read only for owner)

# Common permission combos to memorise:
# 755 = rwxr-xr-x = standard for executables/directories
# 644 = rw-r--r-- = standard for files
# 600 = rw------- = private files (SSH keys)
# 777 = rwxrwxrwx = everyone full access (avoid!)
```

**chown — change ownership:**
```bash
chown user file.txt             # change owner
chown user:group file.txt       # change owner and group
chown -R user:group directory/  # recursive ownership change
```

**Cybersecurity use:** `chmod 777` on sensitive files = major vulnerability. SSH private keys must be `600` or SSH refuses to use them.

---

#### Process Management
```bash
ps                          # show processes for current terminal
ps aux                      # show ALL processes (a=all, u=user, x=no terminal)
ps aux | grep firefox       # find specific process
top                         # live process monitor (q to quit)
htop                        # better live process monitor (F10 to quit)
pgrep firefox               # get PID of process by name
pidof firefox               # get PID of process

kill 1234                   # send SIGTERM to PID 1234 (graceful stop)
kill -9 1234                # send SIGKILL to PID 1234 (force kill)
kill -15 1234               # send SIGTERM (same as just kill)
killall firefox             # kill all processes named firefox
pkill firefox               # kill process by name pattern

jobs                        # list background jobs
bg                          # resume job in background
fg                          # bring background job to foreground
command &                   # run command in background
nohup command &             # run command immune to hangup signals
```

**Exam tip:** Know `kill -9` (force kill) vs `kill` (graceful). Know `ps aux` output.

---

#### Package Management
```bash
# Debian/Ubuntu (apt)
sudo apt update                     # refresh package lists
sudo apt upgrade                    # upgrade all installed packages
sudo apt install packagename -y     # install package
sudo apt remove packagename         # remove package (keep config)
sudo apt purge packagename          # remove package + config files
sudo apt autoremove                 # remove unused dependencies
sudo apt search keyword             # search for package
sudo apt show packagename           # show package details
sudo apt list --installed           # list installed packages

# Red Hat/CentOS (yum/dnf)
sudo yum install packagename        # install (older systems)
sudo dnf install packagename        # install (newer systems)
sudo dnf update                     # update all packages
sudo dnf remove packagename         # remove package
sudo dnf search keyword             # search packages

# Install from .deb file
sudo dpkg -i package.deb            # install .deb file
sudo dpkg -r packagename            # remove package
dpkg -l                             # list installed packages

# Install from .rpm file
sudo rpm -i package.rpm             # install .rpm file
sudo rpm -e packagename             # remove package
```

**Exam tip:** Know apt commands for Debian/Ubuntu. Know the difference between `remove` and `purge`.

---

### 1.9 Linux Commands Part 2 — Complete Reference

#### User Management
```bash
whoami                          # show current username
id                              # show user ID, group ID, groups
id username                     # show info for specific user
who                             # show logged-in users
w                               # show logged-in users + what they're doing
last                            # show login history
lastlog                         # show last login for all users

# User accounts
sudo adduser username           # create new user (interactive, Ubuntu)
sudo useradd username           # create user (manual, less interactive)
sudo useradd -m -s /bin/bash username   # create user with home dir and bash shell
sudo passwd username            # set/change user password
sudo usermod -aG sudo username  # add user to sudo group
sudo usermod -aG groupname username     # add user to group
sudo deluser username           # delete user (Ubuntu)
sudo userdel username           # delete user
sudo userdel -r username        # delete user + home directory

# Groups
groups                          # show current user's groups
groups username                 # show groups for specific user
sudo groupadd groupname         # create new group
sudo groupdel groupname         # delete group
cat /etc/group                  # view all groups
cat /etc/passwd                 # view all user accounts
cat /etc/shadow                 # view password hashes (root only)
```

**Cybersecurity use:** `/etc/shadow` stores hashed passwords — readable only by root. Attackers who get this file can crack passwords offline. `/etc/passwd` is world-readable — shows all accounts but not password hashes.

---

#### sudo — Superuser Do
```bash
sudo command                    # run command as root
sudo -i                         # open root shell (interactive)
sudo su                         # switch to root user
sudo su - username              # switch to another user
su username                     # switch user (need their password)
sudo !!                         # re-run last command as sudo
sudo visudo                     # safely edit sudoers file
cat /etc/sudoers                # view sudo configuration
```

**Exam tip:** Know the difference between `sudo` (run as root temporarily) and `su` (switch user permanently).

---

#### Networking Commands
```bash
ip a                            # show all interfaces and IP addresses
ip addr show eth0               # show specific interface
ip r                            # show routing table
ip route add default via 192.168.1.1    # add default gateway
ip link set eth0 up             # bring interface up
ip link set eth0 down           # bring interface down

ping google.com                 # test connectivity
ping -c 4 google.com            # send 4 packets then stop
ping -i 0.2 google.com          # ping every 0.2 seconds

traceroute google.com           # trace route to host
mtr google.com                  # combined ping + traceroute live

netstat -tuln                   # show listening ports (older)
ss -tuln                        # show listening ports (modern)
ss -tulnp                       # show listening ports with process names
ss -an                          # show all connections

nslookup google.com             # DNS lookup (older tool)
dig google.com                  # DNS lookup (detailed)
dig google.com MX               # query mail records
dig @8.8.8.8 google.com         # query specific DNS server
host google.com                 # simple DNS lookup

curl https://google.com         # fetch URL content
curl -o file.html https://url   # download to file
wget https://url/file           # download file
wget -r https://website.com     # download entire website recursively

ifconfig                        # older network config tool (deprecated)
iwconfig                        # wireless interface info
```

---

#### System Information
```bash
uname -a                        # full system info (kernel, arch, hostname)
uname -r                        # kernel version only
uname -m                        # machine architecture (x86_64)
hostname                        # show hostname
hostname -I                     # show IP addresses

lscpu                           # CPU information
lsmem                           # memory information
free -h                         # RAM usage (human readable)
df -h                           # disk space usage
df -T                           # disk space with filesystem type
du -sh /home/user               # directory size
du -sh *                        # size of all items in current directory

lsblk                           # list block devices (disks/partitions)
lsblk -f                        # list with filesystem types
lspci                           # list PCI devices (GPU, NIC etc.)
lsusb                           # list USB devices
lshw                            # detailed hardware info
sudo lshw -short                # summarised hardware info
sudo dmidecode -t bios          # BIOS information
sudo dmidecode -t memory        # RAM information

uptime                          # how long system has been running
cat /proc/cpuinfo               # detailed CPU info
cat /proc/meminfo               # detailed memory info
```

---

#### Disk and Storage Commands
```bash
lsblk                           # list all disks and partitions
sudo fdisk -l                   # list all disks with details
sudo fdisk /dev/sda             # partition management tool (interactive)
sudo parted /dev/sda print      # show partition table

sudo mkfs.ext4 /dev/sdb1        # format partition as ext4
sudo mkfs.fat -F 32 /dev/sdb1   # format as FAT32
sudo mkfs.ntfs /dev/sdb1        # format as NTFS

sudo mount /dev/sdb1 /mnt       # mount partition to /mnt
sudo umount /mnt                # unmount partition
sudo mount -a                   # mount all in /etc/fstab

cat /etc/fstab                  # view auto-mount configuration
sudo blkid                      # show UUID of all partitions

sudo dd if=/dev/sda of=/dev/sdb bs=4M  # clone entire disk
sudo dd if=/dev/zero of=/dev/sdb bs=4M # wipe disk with zeros
```

**Cybersecurity use:** `dd` is a forensic tool — used to create exact bit-for-bit copies of drives for forensic analysis. `dd if=/dev/zero` securely wipes a drive.

---

#### Compression and Archives
```bash
# tar — tape archive (most common)
tar -cvf archive.tar files/     # create archive
tar -xvf archive.tar            # extract archive
tar -czvf archive.tar.gz files/ # create compressed archive (gzip)
tar -xzvf archive.tar.gz        # extract gzip compressed archive
tar -cjvf archive.tar.bz2 files/# create bzip2 compressed archive
tar -xjvf archive.tar.bz2       # extract bzip2 archive
tar -tf archive.tar             # list contents without extracting

# Flags to remember:
# c = create, x = extract, v = verbose, f = file, z = gzip, j = bzip2, t = list

# Other compression
gzip file.txt                   # compress file (creates file.txt.gz)
gunzip file.txt.gz              # decompress
zip archive.zip files/          # create zip
unzip archive.zip               # extract zip
```

**Exam tip:** tar flags are frequently tested — memorise `cvf` (create) and `xvf` (extract).

---

#### Text Processing
```bash
sort file.txt                   # sort lines alphabetically
sort -r file.txt                # sort reverse
sort -n file.txt                # sort numerically
sort -u file.txt                # sort and remove duplicates

uniq file.txt                   # remove consecutive duplicate lines
uniq -c file.txt                # count occurrences

wc file.txt                     # word count (lines, words, bytes)
wc -l file.txt                  # count lines only
wc -w file.txt                  # count words only

cut -d: -f1 /etc/passwd         # cut field 1 using : delimiter
cut -c1-10 file.txt             # cut first 10 characters

awk '{print $1}' file.txt       # print first column
awk -F: '{print $1}' /etc/passwd # print usernames from passwd file
sed 's/old/new/g' file.txt      # replace all occurrences of old with new
sed -i 's/old/new/g' file.txt   # replace in-place (modify file)

echo "Hello World"              # print text
echo $PATH                      # print variable value
printf "Name: %s\n" "Bob"       # formatted output
```

---

#### Redirection and Pipes — Very Important
```bash
# Output redirection
command > file.txt          # redirect output to file (overwrites)
command >> file.txt         # append output to file
command 2> error.txt        # redirect errors to file
command 2>&1                # redirect errors to same place as output
command > file.txt 2>&1     # redirect both output and errors to file
command > /dev/null 2>&1    # discard all output (silence command)

# Input redirection
command < file.txt          # use file as input to command

# Pipes — send output of one command to another
ps aux | grep firefox               # filter process list
cat /etc/passwd | grep root         # find root in passwd
ls -la | sort -k5 -n                # sort ls output by size
cat access.log | grep "404" | wc -l # count 404 errors in log
ip a | grep "inet "                 # show only IP address lines
history | grep "sudo"               # search command history

# Multiple pipes
cat /var/log/auth.log | grep "Failed" | grep "ssh" | tail -20
# Show last 20 failed SSH attempts
```

**Exam tip:** Pipes (`|`) are fundamental to Linux — know how to chain commands together.

---

#### Environment Variables and Shell
```bash
env                             # list all environment variables
echo $HOME                      # home directory
echo $PATH                      # executable search path
echo $USER                      # current username
echo $SHELL                     # current shell
echo $PWD                       # current directory (same as pwd)
export MYVAR="value"            # set environment variable
unset MYVAR                     # remove variable

history                         # show command history
history | tail -20              # show last 20 commands
!50                             # re-run command number 50
!!                              # re-run last command
Ctrl + R                        # reverse search command history

alias ll='ls -la'               # create command alias
alias                           # list all aliases
unalias ll                      # remove alias
echo "alias ll='ls -la'" >> ~/.bashrc   # make alias permanent

source ~/.bashrc                # reload bash configuration
. ~/.bashrc                     # same as source
```

---

#### Log Files — Critical for Security
```bash
# Key log files to know
/var/log/syslog             # general system messages (Ubuntu)
/var/log/messages           # general system messages (Red Hat)
/var/log/auth.log           # authentication events — logins, sudo (Ubuntu)
/var/log/secure             # authentication events (Red Hat)
/var/log/kern.log           # kernel messages
/var/log/dmesg              # boot and hardware messages
/var/log/apache2/access.log # Apache web server access log
/var/log/nginx/access.log   # Nginx web server access log
/var/log/cron               # scheduled task log
/var/log/faillog            # failed login attempts

# Reading logs
sudo tail -f /var/log/auth.log          # live authentication log
sudo grep "Failed" /var/log/auth.log    # find failed logins
sudo journalctl -f                      # live systemd journal
sudo journalctl -p err                  # show only errors
sudo journalctl -u ssh                  # show SSH service logs
sudo journalctl --since "1 hour ago"    # last hour of logs
dmesg | tail -20                        # last 20 kernel messages
```

**Cybersecurity use:** `/var/log/auth.log` shows every login attempt — critical for detecting brute force attacks. Failed SSH attempts appear here. Attackers clear logs to cover tracks — a blank auth.log is suspicious.

---

#### Scheduled Tasks — cron
```bash
crontab -e                      # edit current user's cron jobs
crontab -l                      # list current user's cron jobs
sudo crontab -e                 # edit root's cron jobs
sudo crontab -l                 # list root's cron jobs
cat /etc/crontab                # system-wide cron jobs
ls /etc/cron.d/                 # additional cron job files

# Cron syntax: minute hour day month weekday command
# Example entries:
* * * * * /script.sh            # every minute
0 2 * * * /backup.sh            # every day at 2:00 AM
*/5 * * * * /check.sh           # every 5 minutes
0 0 * * 0 /weekly.sh            # every Sunday at midnight
```

**Cybersecurity use:** Attackers use cron for persistence — scheduled task runs malware every minute. Always check `crontab -l` and `sudo crontab -l` on compromised systems.

---

#### SSH — Secure Shell
```bash
ssh user@192.168.1.100          # connect to remote host
ssh -p 2222 user@host           # connect on custom port
ssh -i ~/.ssh/key.pem user@host # connect using private key file
ssh -X user@host                # connect with X11 forwarding (GUI apps)

# SSH key generation
ssh-keygen -t ed25519 -C "email@example.com"   # generate ED25519 key (recommended)
ssh-keygen -t rsa -b 4096                       # generate RSA 4096-bit key

# Copy public key to remote server
ssh-copy-id user@host           # copy public key to server's authorized_keys

# SSH config file
cat ~/.ssh/config               # view SSH configuration
cat ~/.ssh/authorized_keys      # view keys allowed to login

# SCP — secure copy over SSH
scp file.txt user@host:/path/   # copy file to remote
scp user@host:/path/file.txt .  # copy file from remote
scp -r folder/ user@host:/path/ # copy directory recursively
```

**Cybersecurity use:** SSH private keys must be `chmod 600` — readable only by owner. `~/.ssh/authorized_keys` lists who can login without a password — check for unknown keys. SSH on default port 22 is constantly probed by bots.

---

#### Firewall — UFW and iptables
```bash
# UFW (Uncomplicated Firewall) — Ubuntu default
sudo ufw status                 # check firewall status
sudo ufw status verbose         # detailed status
sudo ufw enable                 # enable firewall
sudo ufw disable                # disable firewall
sudo ufw allow 22               # allow SSH
sudo ufw allow 80/tcp           # allow HTTP
sudo ufw allow 443/tcp          # allow HTTPS
sudo ufw deny 23                # block Telnet
sudo ufw delete allow 80        # remove rule
sudo ufw reset                  # reset all rules

# iptables (lower level — used on all Linux)
sudo iptables -L                # list all rules
sudo iptables -L -n -v          # detailed rule list with packet counts
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT     # allow SSH in
sudo iptables -A INPUT -j DROP                          # drop all other input
sudo iptables -F                # flush (clear) all rules
```

---

## Quick Reference Cheatsheet — Most Tested Commands

| Command | What it does |
|---|---|
| `ls -la` | List all files with permissions |
| `chmod 755 file` | Set permissions rwxr-xr-x |
| `chown user:group file` | Change ownership |
| `grep -r "text" /dir` | Search recursively |
| `find / -name "file"` | Find file by name |
| `ps aux` | Show all processes |
| `kill -9 PID` | Force kill process |
| `tail -f /var/log/syslog` | Live log monitoring |
| `tar -czvf archive.tar.gz dir/` | Create compressed archive |
| `tar -xzvf archive.tar.gz` | Extract compressed archive |
| `sudo apt install pkg` | Install package |
| `ssh user@host` | Connect via SSH |
| `scp file user@host:/path` | Secure copy over SSH |
| `dd if=/dev/sda of=/dev/sdb` | Clone disk |
| `crontab -l` | List scheduled tasks |
| `cat /var/log/auth.log` | View authentication log |
| `sudo ufw status` | Check firewall |
| `ip a` | Show IP addresses |
| `ss -tulnp` | Show open ports with processes |
| `history \| grep sudo` | Search command history |

---

## Terminal Practice

```bash
# Run these to practice everything covered today

# File permissions
touch testfile.txt
ls -la testfile.txt
chmod 755 testfile.txt
ls -la testfile.txt
chmod 644 testfile.txt
ls -la testfile.txt

# Find commands
find /home -name "*.md" 2>/dev/null
find /var/log -name "*.log" -mtime -1

# Process management
ps aux | grep bash
ps aux | head -10

# Log files
sudo tail -20 /var/log/auth.log
sudo grep "sudo" /var/log/auth.log | tail -10

# Network
ss -tulnp
ip a | grep "inet "

# System info
uname -a
free -h
df -h
lscpu | grep "Model name"

# Pipes practice
cat /etc/passwd | grep whitedonrocks
ls -la /etc | grep "^d" | wc -l    # count directories in /etc
history | tail -20
```

---

## 🔑 Exam Focus Summary

**Most tested topics from Linux Commands:**
1. File permissions — chmod numeric (755, 644, 600, 777) and symbolic
2. `grep` flags — `-i`, `-r`, `-n`, `-v`, `-l`
3. `find` command — by name, type, size, time
4. `ps aux` — know the output columns
5. `kill` vs `kill -9` — graceful vs force
6. `tar` flags — cvf (create), xvf (extract), z (gzip), j (bzip2)
7. Pipe operator `|` — chaining commands
8. Log file locations — especially `/var/log/auth.log`
9. `chmod` and `chown` — ownership and permissions
10. SSH key permissions — must be 600

---

## What I Didn't Understand
-

## 3 Key Things I Learned
1. Linux file permissions use octal notation — 755 = rwxr-xr-x, 644 = rw-r--r--, 600 = rw------- — SSH keys MUST be 600 or SSH refuses to use them
2. Pipes chain commands together — output of one becomes input of next — fundamental to Linux administration and security work
3. /var/log/auth.log records every login attempt — failed SSH brute force visible here — attackers clear this log to hide their tracks