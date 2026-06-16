# 📁 DAY 2 & DAY 3 NOTES – Ports, File System & Troubleshooting

---

# 🔌 Physical Port Inspection

## Purpose

Laptop me available physical ports identify karna.

## Common Ports

- USB-A → Mouse, Keyboard, Pendrive
    
- USB-C → Data Transfer, Charging, Display Output
    
- HDMI → External Monitor/Projector
    
- RJ45 Ethernet → Wired Network Connection
    
- Audio Jack → Headphone/Mic
    
- SD Card Reader → Memory Cards
    

## Service Desk Scenario

User:

> External monitor connect nahi ho raha.

Check:

- HDMI Port available hai?
    
- Cable sahi hai?
    
- Monitor input source correct hai?
    

---

# 🔌 WMIC USB Hub Check

## Command

```cmd
wmic path win32_usbhub get name
```

## Purpose

System ke USB Hubs aur USB Root Hubs dikhata hai.

## Analogy

USB Hub = Traffic Junction

- Keyboard
    
- Mouse
    
- Webcam
    
- Pendrive
    

sab isi junction se motherboard tak pahuchte hain.

## Example Output

```text
Generic USB Hub
USB Root Hub (USB 3.0)
```

## Service Desk Use

User:

> USB port kaam nahi kar raha.

Check:

```cmd
wmic path win32_usbhub get name
```

Agar Hub detect nahi ho raha to driver ya hardware issue ho sakta hai.

---

# 🔌 USB Devices Check

## Command

```cmd
wmic path win32_pnpentity where "name like '%USB%'" get name
```

## Purpose

System ke saare USB devices filter karke dikhata hai.

## Analogy

Mall me 1000 log hain.

Boss bolta hai:

> Sirf delivery boys ki list nikalo.

Ye command bhi waise hi sirf USB devices dikhati hai.

## Example Output

```text
USB Keyboard
USB Mouse
USB Mass Storage Device
USB Composite Device
```

## Service Desk Use

User:

> Pendrive detect nahi ho rahi.

Check:

```cmd
wmic path win32_pnpentity where "name like '%USB%'" get name
```

### Agar dikhe

```text
USB Mass Storage Device
```

✅ Device detect ho gayi.

### Agar na dikhe

❌ Device detect nahi hui.

Possible Causes:

- USB Port Issue
    
- Driver Issue
    
- Pendrive Faulty
    
- Loose Connection
    

---

# 🛠 Device Manager

## Command

```cmd
devmgmt.msc
```

## Purpose

Hardware devices aur unke drivers ki health check karna.

## Indicators

|Symbol|Meaning|
|---|---|
|⚠️ Yellow Sign|Driver Problem|
|⬇️ Down Arrow|Device Disabled|
|❓ Unknown Device|Driver Missing|

## Service Desk Use

User:

> Keyboard kaam nahi kar raha.

Open:

```cmd
devmgmt.msc
```

Check:

- Driver installed?
    
- Device disabled?
    
- Hardware detected?
    

---

# 📂 File & Folder Commands

## Navigation

```cmd
cd
```

Directory change karne ke liye.

---

## Files & Folders List

```cmd
dir
```

Current folder ka content dikhata hai.

---

## Folder Create

```cmd
mkdir TestFolder
```

New folder create karta hai.

---

## Folder Delete

```cmd
rmdir TestFolder
```

Folder delete karta hai.

---

## File Delete

```cmd
del file.txt
```

File delete karta hai.

---

## File Copy

```cmd
copy file.txt Backup.txt
```

File copy karta hai.

---

## File Move

```cmd
move file.txt Documents
```

File move karta hai.

---

## File Content Read

```cmd
type file.txt
```

File ke andar ka text dikhata hai.

---

# 📝 File Create Using Echo

## Command

```cmd
echo Hello World > test.txt
```

## Purpose

New text file create karna aur content write karna.

---

# 🔒 File Attributes

## Hidden File

```cmd
attrib +h file.txt
```

File hide karta hai.

---

## Unhide File

```cmd
attrib -h file.txt
```

Hidden attribute remove karta hai.

---

## Read Only

```cmd
attrib +r file.txt
```

File ko edit/delete se protect karta hai.

---

## Remove Read Only

```cmd
attrib -r file.txt
```

Protection hata deta hai.

---

# 👀 Hidden Files Show

## CMD

```cmd
dir /a
```

Hidden files bhi dikhata hai.

## PowerShell

```powershell
Get-ChildItem -Force
```

---

# 💽 File System Check

## Command

```cmd
fsutil fsinfo volumeinfo C:
```

## Purpose

Drive ka File System check karna.

## Example Output

```text
File System Name : NTFS
```

Possible Types:

- NTFS
    
- FAT32
    
- exFAT
    

## Service Desk Scenario

User:

> 6 GB file USB me copy nahi ho rahi.

Check:

```cmd
fsutil fsinfo volumeinfo E:
```

Agar:

```text
FAT32
```

To issue mil gaya.

### Reason

FAT32 ki limit:

```text
4 GB per file
```

Solution:

- exFAT
    
- NTFS
    

---

# 💊 Disk Health Check

## Command

```cmd
chkdsk C: /scan
```

## Purpose

Disk errors scan karna.

## Use Cases

- Slow System
    
- File Corruption
    
- Boot Problems
    
- Storage Errors
    

---

# 📂 File Explorer Hidden Files

## Steps

File Explorer → View → Show → Hidden Items

## Purpose

GUI se hidden files dekhna.

---

# 🎯 Interview Revision

### USB Hub Command

```cmd
wmic path win32_usbhub get name
```

USB Hubs detect karta hai.

---

### USB Devices Command

```cmd
wmic path win32_pnpentity where "name like '%USB%'" get name
```

USB devices detect karta hai.

---

### Device Manager

```cmd
devmgmt.msc
```

Drivers aur hardware status check karta hai.

---

### File System Check

```cmd
fsutil fsinfo volumeinfo C:
```

NTFS/FAT32/exFAT identify karta hai.

---

### Disk Health

```cmd
chkdsk C: /scan
```

Disk errors scan karta hai.

---

## One Line Memory Trick 🧠

- `win32_usbhub` = USB Highway
    
- `win32_pnpentity` = USB Vehicles
    
- `devmgmt.msc` = Traffic Police
    
- `fsutil` = Drive ID Card
    
- `chkdsk` = Drive Doctor
    
- `attrib` = File Lock/Hide Controls