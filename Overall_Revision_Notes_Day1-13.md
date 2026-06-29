# 📝 Complete Revision Notes
## Phase 1 + Phase 2 (Day 1-13)

---

## 🖥️ HARDWARE (Day 1)

### CPU
```
CPU = Computer ka dimaag
    - Cores = ek saath kitne kaam
    - GHz   = speed
    - Tera  = i7-13650HX, 13th Gen
    - SD    = Task Manager → CPU % check
```

### RAM
```
RAM = Temporary working memory (Volatile!)
    - Power off = data clear
    - Tera = 16GB (2x8GB dual channel)
    - SD   = Browser crash = RAM full
```

### HDD vs SSD

| Type | Speed | Notes |
|------|-------|-------|
| HDD | ~100 MB/s | Moving parts, cheap |
| SSD | ~500 MB/s | No moving parts |
| NVMe | ~3000 MB/s | Fastest |

```
KEY: Difference = SPEED not space!
SD:  Slow boot = HDD issue
```

### Motherboard
```
Motherboard = Sab connect karta hai
    - BIOS/UEFI = boot software
    - SD: Beep on boot = POST error
```

### PSU
```
PSU = AC to DC convert karta hai
    - SD: Random shutdown = PSU failing
```

---

## 🔌 PORTS & DISPLAY (Day 2)

### Display Ports

| Port | Details |
|------|---------|
| HDMI | Common, digital, audio+video |
| DisplayPort | Gaming, high refresh rate |
| VGA | OLD, analog, blurry, no audio ❌ |
| Thunderbolt | 40Gbps, USB-C shape, Intel+Apple |
| USB-C | Modern, reversible |

### USB Types

| Type | Speed | Color |
|------|-------|-------|
| USB 2.0 | 480 Mbps | Black |
| USB 3.0 | 5 Gbps | Blue |
| USB 3.1 | 10 Gbps | — |
| USB 3.2 | 20 Gbps | — |

```
KEY: Color se assume mat karo — devmgmt.msc se verify!
```

### Other Ports
```
3.5mm   = Audio
RJ-45   = Wired internet
SD slot = Camera storage
```

### Commands
```cmd
devmgmt.msc = Device Manager
wmic path win32_usbhub get name
wmic path win32_pnpentity where "name like '%USB%'" get name
```

---

## 📁 FILE SYSTEM & CMD (Day 3)

### File Systems

| Type | Use | File Size Limit |
|------|-----|----------------|
| NTFS | Windows default | Unlimited |
| FAT32 | Universal USB | 4GB max per file |
| exFAT | Modern USB/SD | Large files ok |

### Windows Folder Structure
```
C:\                      = Root
C:\Windows\System32\     = Critical files — TOUCH MAT!
C:\Program Files\        = 64-bit apps
C:\Program Files (x86)\  = 32-bit apps
C:\Users\username\       = User data
C:\Users\username\AppData\ = Hidden, app settings
C:\Windows\Temp\         = Temp files — safe to clear
```

### CMD Commands
```cmd
cd foldername     = Folder change
cd ..             = Ek peeche
dir               = Contents dekho
dir /a            = Hidden files bhi
mkdir FolderName  = Folder banao
rmdir FolderName  = Folder delete
echo text > file  = File banao
type filename     = Content dekho
copy file path    = Copy karo
move file path    = Move karo
del filename      = Delete karo
cls               = Screen clear
attrib +h file    = Hide karo
attrib -h file    = Unhide karo
attrib +r file    = Read only
attrib -r file    = Read only hatao
fsutil fsinfo volumeinfo C: = File system check
chkdsk C: /scan   = Disk health
```

---

## 👤 USER MANAGEMENT (Day 4)

### Account Types
```
Administrator = Full control, high virus risk
Standard User = Limited, safer, daily use
Guest         = Minimum access, disabled by default
```

### UAC
```
UAC = Security guard
    = Permission popup before system changes
    = Malware se protect karta hai
    = DISABLE MAT KARO!
```

### Commands
```cmd
net user                                   = Sab users
net user username                          = User info
net user Name Pass /add                    = User banao
net user Name /active:no                   = Disable
net user Name /active:yes                  = Enable
net user Name /delete                      = Delete
net localgroup administrators              = Group members
net localgroup administrators Name /add    = Admin banao
net localgroup administrators Name /delete = Admin hatao
net accounts                               = Password policy
whoami                                     = Current user
whoami /groups                             = Groups dekho
runas /user:Administrator cmd              = Admin CMD
compmgmt.msc                               = Computer Management
```

### Principle of Least Privilege
```
= User ko sirf utni permission do jitni zarurat hai
```

---

## 📊 TASK MANAGER & SERVICES (Day 5)

### Task Manager
```
Shortcut = Ctrl + Shift + Esc

Tabs:
    Processes   = Running apps + processes
    Performance = CPU, RAM, Disk graphs
    Startup     = Boot pe kya chalta hai
    Users       = Logged in users
    Services    = Services status

SD use:
    Slow PC  → CPU/RAM % check
    Startup  → High Impact → Disable (not Stop!)
```

### Services States
```
Running  = Chal raha hai ✅
Stopped  = Band hai ⛔
Disabled = Kabhi nahi chalega 🚫
```

### Startup Types
```
Automatic = Windows ke saath start
Manual    = Zarurat pe start
Disabled  = Never
```

### Important Services

| Service | Purpose |
|---------|---------|
| Print Spooler | Printing |
| Windows Update | Updates |
| DHCP Client | Auto IP |
| DNS Client | DNS resolve |
| Remote Desktop | RDP |

```cmd
services.msc = Services window
```

### Event Viewer
```cmd
eventvwr.msc = Event Viewer
```

### Important Event IDs

| Event ID | Matlab |
|----------|--------|
| 41 | Unexpected shutdown/crash |
| 6008 | Unexpected shutdown |
| 4624 | Successful login |
| 4625 | Failed login |
| 4720 | User account created |
| 4726 | User account deleted |
| 7034 | Service crashed |

### Resource Monitor
```cmd
resmon = Resource Monitor (Task Manager ka advanced version)
       = Per process detail
```

---

## 🔑 REGISTRY (Day 6)

```
Registry = Windows ka master database
Command  = regedit
```

### 5 Hives

| Hive | Matlab |
|------|--------|
| HKLM | Local Machine — sab users |
| HKCU | Current User — sirf current user |
| HKCR | Classes Root — file associations |
| HKU | All Users |
| HKCC | Current Config — hardware |

### Value Types
```
REG_SZ     = Text string
REG_DWORD  = Number — 1=Enable, 0=Disable
REG_BINARY = Binary data
```

### Important Paths
```
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run     = Startup programs
HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion      = Windows version
HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run     = User startup
```

### Rules
```
1. BACKUP PEHLE! → File → Export
2. Sirf wahi touch karo jo pata hai
3. C:\Windows keys = danger zone!
```

---

## ⚙️ WINDOWS ENVIRONMENT (Day 7)

### Control Panel Shortcuts
```cmd
control      = Control Panel
appwiz.cpl   = Programs & Features
ncpa.cpl     = Network Connections
sysdm.cpl    = System Properties
desk.cpl     = Display Settings
firewall.cpl = Windows Firewall
gpedit.msc   = Group Policy Editor
```

### Environment Variables

| Variable | Path |
|----------|------|
| %SystemRoot% | C:\Windows |
| %TEMP% | Temp folder |
| %USERNAME% | Current user |
| %USERPROFILE% | User folder |
| %APPDATA% | App data |
| %PROGRAMFILES% | Program Files |

```
PATH = Programs kahan dhundne hain
SD:  "python not recognized" = PATH mein add karo
Location: sysdm.cpl → Advanced → Environment Variables
```

### Group Policy
```
gpedit.msc = Group Policy Editor
= Admin ka remote control
= USB disable, wallpaper lock, etc.
= Pro/Enterprise only!
```

---

## 🍎 macOS BASICS (Day 8)

### Equivalents

| Windows | macOS |
|---------|-------|
| File Explorer | Finder |
| Task Manager | Activity Monitor |
| Control Panel | System Settings |
| CMD | Terminal |
| .exe | .dmg / .pkg |
| C:\Program Files | /Applications |
| C:\Users\user | /Users/username |
| AppData | /Library |

### Shortcuts
```
Cmd + Space          = Spotlight search
Cmd + Option + Esc   = Force Quit
Cmd + Shift + G      = Go to folder
```

### Recovery Mode
```
Intel Mac  = Restart + Cmd + R hold
M1/M2 Mac  = Power button hold → Options
```

### Terminal vs CMD

| CMD | Terminal |
|-----|----------|
| dir | ls |
| type | cat |
| ipconfig | ifconfig |
| del | rm |

---

## 🌐 NETWORKING (Day 9–12)

### IP Address
```
Private  = 192.168.x.x / 10.x.x.x
Public   = Internet pe visible
169.254.x.x = DHCP nahi mila (APIPA)
```

### DNS
```
DNS     = Internet ki phone book
8.8.8.8   = Google DNS
1.1.1.1   = Cloudflare DNS
SD: google.com nahi but 8.8.8.8 ping = DNS problem
```

### DHCP
```
DHCP = Automatic IP deta hai
DORA = Discover, Offer, Request, Acknowledge
SD:  IP conflict = ipconfig /release /renew
```

### Important Ports

| Port | Protocol |
|------|---------|
| 80 | HTTP |
| 443 | HTTPS |
| 22 | SSH |
| 23 | Telnet (insecure!) |
| 25 | SMTP (email send) |
| 53 | DNS |
| 3389 | RDP |
| 67/68 | DHCP |

### Network Commands
```cmd
ipconfig /all          = Full network info
ipconfig /release      = IP release
ipconfig /renew        = Naya IP
ipconfig /flushdns     = DNS cache clear
ipconfig /displaydns   = DNS cache dekho
ping 8.8.8.8           = Internet test
ping 8.8.8.8 -t        = Continuous ping
ping 8.8.8.8 -n 10     = 10 packets
nslookup google.com    = DNS lookup
tracert google.com     = Route trace
netstat -an            = All connections
netstat -b             = Process + port
netstat -r             = Routing table
arp -a                 = IP to MAC table
netsh winsock reset    = Winsock reset
netsh int ip reset     = TCP/IP reset
netsh winhttp show proxy = Proxy check
netsh winhttp set proxy proxy-server="http=proxy:8080"
netsh wlan show profiles   = WiFi list
netsh wlan show interfaces = WiFi info
netsh wlan show networks   = Available WiFi
netsh wlan show profile "Name" key=clear = Password
```

### Troubleshoot Steps
```
Step 1: ipconfig /all  → IP check
Step 2: ping Gateway   → Router ok?
Step 3: ping 8.8.8.8   → Internet ok?
Step 4: ping google.com → DNS ok?
Step 5: nslookup       → DNS verify
Step 6: ipconfig /flushdns
Step 7: netsh winsock reset
```

### VPN
```
= Encrypted tunnel
= Remote Access VPN  = ghar se office
= Site-to-Site VPN   = do offices connect
Protocols: OpenVPN, IKEv2, WireGuard
```

### Proxy
```
= Middleman between user and internet
= Forward Proxy = client side
= Reverse Proxy = server side
= Less secure than VPN
```

### WiFi

| Band | Speed | Range |
|------|-------|-------|
| 2.4GHz | Slow | Far |
| 5GHz | Fast | Short |

| Security | Status |
|----------|--------|
| WEP | Weak ❌ |
| WPA2 | Good ✅ |
| WPA3 | Best ✅ |

```
Power Management fix = Disconnect issue solve!
```
