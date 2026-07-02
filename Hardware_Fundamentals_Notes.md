# 🖥️ Day 1 — Hardware Fundamentals & System Information

---

## 🎯 Learning Objective

Day 1 ka goal tha computer ke major hardware components ko identify karna aur Windows ke built-in tools use karke system information collect karna.

---

## 🏗️ Basic PC Components

### CPU (Central Processing Unit)

CPU computer ka **brain** hota hai. Ye saare calculations perform karta hai aur instructions execute karta hai.

**Real World Analogy 🧠** — Socho CPU office ka manager hai. Kis employee ko kya kaam karna hai, kaunsi file pehle process hogi, kaunsa task important hai — sab decisions CPU leta hai.

```text
Mere System Mein:
Intel Core i7-13650HX
14 Cores
20 Logical Processors
```

---

### RAM (Random Access Memory)

RAM temporary working memory hoti hai. Jitne applications open honge, utni RAM use hogi.

**Real World Analogy 📚** — Socho tumhari study table. Badi table = Zyada books ek saath khol sakte ho. Chhoti table = Baar-baar books replace karni padengi.

```text
Mere System Mein:
Installed RAM: 16 GB
```

---

### SSD (Solid State Drive)

SSD permanent storage device hai. Isme Windows, software aur files store hoti hain.

**Real World Analogy 🗄️** — Socho ek locker. Jab computer band ho jata hai tab bhi data locker me safe rehta hai.

---

### Motherboard

Motherboard computer ka main circuit board hota hai. Saare hardware isi se connected hote hain — CPU, RAM, SSD, GPU, USB Ports, Network Adapter.

**Real World Analogy 🏙️** — Socho ek city. Motherboard us city ki roads aur infrastructure hai. Saare components isi ke through communicate karte hain.

---

### PSU (Power Supply Unit)

PSU wall electricity ko computer ke usable voltage me convert karta hai.

**Real World Analogy ⚡** — Power Station → Electricity. PSU → Computer ko safe power supply.

---

## 🖥️ PC Hardware Diagram

```text
                ┌──────────────┐
                │     CPU      │
                └──────┬───────┘
                       │
        ┌──────────────┼──────────────┐
        │              │              │
        ▼              ▼              ▼
    ┌───────┐     ┌────────┐     ┌────────┐
    │ RAM   │     │ SSD    │     │ GPU    │
    └───────┘     └────────┘     └────────┘

               All Connected To

           ┌─────────────────┐
           │  Motherboard    │
           └─────────────────┘
                     ▲
                     │
             ┌────────────┐
             │    PSU     │
             └────────────┘
```

---

## 🛠️ System Information Tools

### 1️⃣ msinfo32

**Purpose:** System ki complete hardware aur software information dikhata hai.

```cmd
msinfo32
```

**Information Available:** Windows Version, System Model, BIOS Version, CPU, RAM, Motherboard, Drivers, Security Features.

**Real World Analogy 📖** — Hospital ki patient file jisme patient ki poori history likhi hoti hai. `msinfo32` computer ki waise hi complete history file hai.

**Service Desk Use:**
```
User: "Mera laptop model kya hai?" / "BIOS version kya hai?"
Answer: msinfo32 → sabkuch milega!
```

---

### 2️⃣ CPU Information

```cmd
wmic cpu get name
```

| Command Part | Meaning |
|--------------|---------|
| `wmic` | Windows Management Instrumentation |
| `cpu` | CPU Information |
| `get name` | Processor Name Show Karo |

**Example Output:**
```text
Intel(R) Core(TM) i7-13650HX
```

**Real World Analogy 🚗** — Car ka bonnet khole bina engine model dekhna. Laptop khole bina CPU model bata deta hai.

**Service Desk Use:** Compatibility check — VMware, VirtualBox, Android Studio, Video Editing Software ke liye CPU verify karo.

---

### 3️⃣ RAM Information

```cmd
wmic memorychip get capacity
```

**Example Output:**
```text
8589934592
8589934592
```

**Conversion:**
```text
8589934592 Bytes = 8 GB
8 GB + 8 GB = 16 GB Total
```

**Real World Analogy 📚** — Almirah me kitni shelves hain aur har shelf me kitni books aa sakti hain.

**Service Desk Use — RAM Upgrade Planning:**
```text
Current: 8 GB + 8 GB
Upgrade: 16 GB + 16 GB = 32 GB
```

---

### 4️⃣ Disk Information

```cmd
wmic diskdrive get model,size,mediatype
```

**Information Available:** Disk Model, Disk Size, Media Type.

**Example Output:**
```text
Samsung SSD 512GB
```

**Real World Analogy 🗄️** — Warehouse inventory card. Batata hai kaunsi storage lagi hai, kitni capacity hai, kis type ki hai.

**Service Desk Use:**
```
User: "System slow chal raha hai."
Check: wmic diskdrive get model,size,mediatype
Identify: HDD / SATA SSD / NVMe SSD
```

---

### 5️⃣ Total Physical Memory

```cmd
systeminfo | findstr /C:"Total Physical Memory"
```

**Breakdown:**

| Part | Kya Karta Hai |
|------|---------------|
| `systeminfo` | Complete system report generate karta hai |
| `\|` (Pipe) | Ek command ka output dusri command ko pass karta hai |
| `findstr /C:"..."` | Specific text search karta hai |

**Example Output:**
```text
Total Physical Memory: 15,874 MB
```

**Service Desk Use:** Remote troubleshooting mein quick RAM verification.

---

## 🎯 Interview Questions

**Q1. CPU ka role kya hai?**
Computer ka brain hai jo instructions execute karta hai.

**Q2. RAM aur SSD me difference?**
RAM temporary memory hai. SSD permanent storage hai.

**Q3. `wmic cpu get name` kya karta hai?**
Processor ka exact model show karta hai.

**Q4. `wmic memorychip get capacity` kyun use karte hain?**
Har RAM stick ki individual capacity dekhne ke liye.

**Q5. `wmic diskdrive get model,size,mediatype` kya karta hai?**
Storage device ka model, size aur media type show karta hai.

**Q6. Pipe (`|`) kya karta hai?**
Ek command ka output dusri command ko pass karta hai.

---

## 🧠 Quick Revision — Commands

```cmd
msinfo32
wmic cpu get name
wmic memorychip get capacity
wmic diskdrive get model,size,mediatype
systeminfo | findstr /C:"Total Physical Memory"
```

---

## 🔥 One Line Memory Tricks

```
CPU         = Brain
RAM         = Study Table
SSD         = Locker
Motherboard = City Roads
PSU         = Power Station
msinfo32    = Computer Biography
WMIC        = Hardware Database Query Tool
systeminfo  = Complete Audit Report
findstr     = Search Filter
```
