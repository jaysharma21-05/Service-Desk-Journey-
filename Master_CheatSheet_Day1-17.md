# ⚡ Master Cheat Sheet — Day 1 to Day 17

---

## 🖥️ HARDWARE

```
CPU    = Dimaag | Cores + GHz
RAM    = Volatile, temporary | 16GB tera
SSD    = Fast | NVMe = fastest | HDD = slow
PSU    = AC→DC | Random shutdown = PSU fail
MB     = Sab connect karta hai | Beep = POST error
```

---

## 🔌 PORTS

| Port | Details |
|------|---------|
| HDMI | Common, digital, audio+video |
| Thunderbolt | 40Gbps, Intel+Apple |
| VGA | Analog, blurry, no audio ❌ |
| USB 2.0 | Black, 480Mbps |
| USB 3.0 | Blue, 5Gbps |
| USB-C | Reversible, modern |

> ⚠️ Color se assume mat karo — `devmgmt.msc` se verify!

---

## 📁 FILE SYSTEM

| Type | Details |
|------|---------|
| NTFS | Unlimited size, secure, Windows |
| FAT32 | 4GB max, universal |
| exFAT | Modern USB/SD |

```
C:\Windows\System32  = Touch mat!
C:\Users\username    = User data
%TEMP%               = Temp files
```

```cmd
attrib +h/-h  = Hide/Unhide
attrib +r/-r  = ReadOnly on/off
dir /a        = Hidden files dekho
```

---

## 👤 USER MANAGEMENT

```
Admin    = Full control, risky
Standard = Safe, daily use
UAC      = Security guard, disable mat karo!
```

```cmd
net user                            = Users list
net user Name Pass /add             = User banana
net user Name /active:no            = Disable
net user Name /delete               = Delete
net localgroup admins Name /add     = Admin banana
whoami /groups                      = Groups check
runas /user:Administrator cmd       = Admin CMD
```

---

## 📊 TASK MANAGER

```
Shortcut = Ctrl+Shift+Esc
Startup  = Disable karo (not Stop!)
Services = services.msc
resmon   = Advanced Task Manager
```

### Important Event IDs

| Event ID | Matlab |
|----------|--------|
| 41 | Crash / unexpected shutdown |
| 4624 | Login success |
| 4625 | Login fail |
| 4720 | User created |
| 7034 | Service crashed |

---

## 🔑 REGISTRY

```
regedit = Open karo
HKLM    = All users settings
HKCU    = Current user
HKCR    = File associations
REG_DWORD = 1=ON, 0=OFF
```

> ⚠️ Backup pehle! File → Export

```
Startup path:
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
```

---

## ⚙️ WINDOWS ENVIRONMENT

```cmd
control      = Control Panel
appwiz.cpl   = Programs list
ncpa.cpl     = Network connections
sysdm.cpl    = System properties
gpedit.msc   = Group Policy (Pro only)
firewall.cpl = Firewall
```

```
%TEMP%     = Temp folder
%USERNAME% = Current user
%APPDATA%  = App data
PATH       = Programs kahan dhundne hain
```

---

## 🍎 macOS

| Windows | macOS |
|---------|-------|
| File Explorer | Finder |
| Task Manager | Activity Monitor |
| CMD | Terminal |
| Program Files | /Applications |

```
Cmd+Option+Esc  = Force Quit
Intel Recovery  = Restart + Cmd+R hold
dir → ls
type → cat
ipconfig → ifconfig
```

---

## 🌐 NETWORKING

```
Private IP  = 192.168.x.x / 10.x.x.x
169.254.x.x = DHCP fail! (APIPA)
DNS         = Internet phone book
DHCP        = Auto IP (DORA process)
```

### Important Ports

| Port | Protocol |
|------|---------|
| 80 | HTTP |
| 443 | HTTPS |
| 22 | SSH |
| 23 | Telnet (insecure!) |
| 25 | SMTP |
| 53 | DNS |
| 3389 | RDP |
| 67/68 | DHCP |

### Network Commands

```cmd
ipconfig /all          = Full info
ipconfig /release      = IP release
ipconfig /renew        = Naya IP
ipconfig /flushdns     = DNS cache clear
ping 8.8.8.8           = Internet test
ping google.com        = DNS test
nslookup google.com    = DNS lookup
tracert google.com     = Route trace
netstat -an            = All connections
netstat -b             = Process + port
arp -a                 = IP→MAC table
netsh winsock reset    = Network reset
```

---

## 🔒 VPN + PROXY

```
VPN          = Encrypted tunnel, full traffic
Proxy        = Middleman, no encryption
Split Tunnel = Kuch VPN, kuch direct
```

```cmd
netsh winhttp show proxy                                    = Proxy check
netsh winhttp set proxy proxy-server="http=proxy:8080"     = Proxy set
```

---

## 📶 WiFi

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
Channels = 1, 6, 11 use karo

Disconnecting fix:
devmgmt.msc → WiFi → Properties →
Power Management → Uncheck "Allow computer to turn off this device"
```

```cmd
netsh wlan show profiles
netsh wlan show profile "Name" key=clear
netsh wlan show interfaces
```

---

## 💻 RDP + SSH

```
RDP  = Port 3389, GUI, Windows
SSH  = Port 22, CLI, Linux/Servers
NLA  = Connect SE PEHLE verify
Home = Client only, not host!

TeamViewer/AnyDesk = Third party = No firewall/port issues!
```

```cmd
mstsc                                              = RDP client open
net localgroup "Remote Desktop Users" Name /add    = RDP access dena
```

---

## 🔥 FIREWALL

```
wf.msc   = Firewall GUI
Inbound  = Bahar → Andar
Outbound = Andar → Bahar
Profiles = Domain / Private / Public
```

```cmd
netsh advfirewall show allprofiles

netsh advfirewall firewall add rule ^
  name="X" protocol=TCP dir=in ^
  localport=3389 action=allow

netsh advfirewall firewall delete rule name="X"

netsh advfirewall set allprofiles state off
netsh advfirewall set allprofiles state on

netsh advfirewall firewall add rule ^
  name="Allow Ping" protocol=icmpv4 dir=in action=allow
```

---

## 🎫 ITIL + TICKETING

| Type | Matlab |
|------|--------|
| Incident | Unplanned interruption |
| Problem | Root cause (recurring incidents) |
| Change | Planned modification (CAB approval) |
| Service Request | Planned request (kuch kharab nahi) |

### Priority Matrix

| Priority | Level | Response | Scope |
|----------|-------|----------|-------|
| P1 | Critical | 15 min | All affected |
| P2 | High | 1 hr | Dept affected |
| P3 | Medium | 4 hr | Single user |
| P4 | Low | 24 hr | Minor issue |

```
SLA  = Time promise
FCR  = First Call Resolution
MTTR = Mean Time To Resolve

Escalate when:
→ SLA breach hone wali ho
→ Technical knowledge nahi
→ P1 issue hai
```

---

## 🖥️ SERVICENOW

```
Incident Management = Tickets
CMDB               = IT Assets register
KBA                = Solutions library
Work Notes         = Internal only (user nahi dekh sakta)
Comments           = User bhi dekhe

developer.servicenow.com = Free practice!
```

---

## 🤝 CUSTOMER SERVICE

### HEAT Model

| Letter | Matlab |
|--------|--------|
| H | Hear — Suno |
| E | Empathize — Samjho |
| A | Apologize — Sorry bolo |
| T | Take Action — Karo! |

### Rules

```
✅ Never say NO directly
✅ Underpromise, Overdeliver
✅ Follow up 24hr baad
✅ Naam leke baat karo
❌ "Pata nahi" mat bolo
❌ Hold = max 2 min
```

### Call Opening Script

```
"Thank you for calling IT Support,
this is Jay. How can I help you?"
```
