# 📅 Day 15 — ITIL & Ticketing Systems (ServiceNow)

---

## 🧠 PART 1: ITIL Framework aur 4 Main Concepts

**ITIL (Information Technology Infrastructure Library)** simple bhasha mein IT industry ki **"Sanskriti aur Rule Book"** hai. Yeh batati hai ki jab kisi company mein hazaron computers, servers, aur users hon, toh bina kisi chaos ke unhe kaise manage karna hai.

ITIL ke according, computer mein aane wali har dikkat ya request ek jaisi nahi hoti. Isne kaam ko **4 main categories** mein baanta hai:

---

### 1. Incident (Achanak Lagi Aag 🔥)

- **Definition:** Ek unplanned interruption jiski wajah se service down ho jaye aur user ka kaam ruk jaye.
- **Goal:** Kaam ko jaldi se jaldi wapas shuru karwana (Workaround nikalna).
- **Examples:** Network down ho gaya, PC crash ho gaya, Windows blue screen (BSOD) de raha hai.

---

### 2. Service Request (Planned Maang 📝)

- **Definition:** Kuch kharab nahi hua. User pehle se planned tarike se kuch maang raha hai. Koi interruption nahi hota.
- **Examples:** "Mera password reset kar do", "Mujhe ek naya laptop issue kar do", "System mein Wireshark install kar do."

---

### 3. Problem (Root Cause 🕵️)

- **Definition:** Jab ek hi tarah ke Incidents baar-baar aane lagein, toh unke piche ka gupt kaaran (Root Cause) **Problem** kehlata hai.
- **Goal:** Issue ko hamesha ke liye khatam karna.
- **Example:** Roz subah 10 baje poore department ka internet slow ho jata hai. Ek baar slow hua = Incident. Roz ho raha hai = **Problem.**

---

### 4. Change (Planned Operation 🛠️)

- **Definition:** System mein koi bada badlav jiske liye pehle CAB (Change Advisory Board) se approval lena padta hai.
- **Example:** Poore office ke routers ka firmware upgrade karna, ya Windows Server par naya security patch deploy karna.

---

### 🍽️ THE DESI ANALOGY: The Smart Hotel Management 🏨

Socho tum Sikkim ke sabse bade 5-Star Hotel ke Manager (Service Desk) ho:

| Situation | ITIL Category |
|-----------|--------------|
| Room 202 ka AC achanak band ho gaya | **Incident** — turant table fan (workaround) bhejo |
| Room 305 se extra pillow ki maang | **Service Request** — kuch kharab nahi, sirf request hai |
| 2nd floor ke saare rooms ka AC roz dupahar ko trip karta hai | **Problem** — main electricity panel (Root Cause) check karo |
| Purane ACs hata kar naye inverter ACs lagana | **Change** — owner se budget + approval (CAB) lena padega |

---

## 📊 PART 2: Priority Matrix, SLA, aur Ticket Lifecycle

### 🔢 Priority Matrix (P1 to P4)

Priority = **Impact** (Kitne log affected) + **Urgency** (Kitna jaldi fix karna zaroori)

| Priority | Level | Example | Response Time | Resolution |
|----------|-------|---------|---------------|------------|
| P1 | Critical | Poora server crash, company ka kaam band | 15 Min | 1 Hour |
| P2 | High | Poora ek department kaam nahi kar pa raha | — | — |
| P3 | Medium | Kisi ek akele user ka printer nahi chal raha | — | — |
| P4 | Low | Screen ka resolution thoda ajeeb (workaround available) | — | — |

---

### ⏳ SLA (Service Level Agreement)

SLA ek **legal promise** hai jo IT team client se karti hai.

```
"Hum P1 ticket ko 1 ghante mein aur P3 ticket ko 8 ghante mein solve karenge."
```

> **SLA Breach:** Agar time limit cross ho gayi → system par laal (Red) alert, manager ko mail, aur company par penalty. Tracking time is everything!

---

### 🔄 Ticket Lifecycle

```
New → Assigned → In Progress → Pending → Resolved → Closed
```

> ⚠️ **Pending Status Ka Khufiya Rule:** Jab user se koi info chahiye (e.g., "Sir apna IP batao" / "Screenshot bhejo"), ticket ko **Pending (Awaiting Customer)** karo. Iska fayda — **SLA ka timer ruk jata hai (Pause)**, taaki user ki deri ki wajah se tumhara SLA breach na ho!

---

## 🏗️ PART 3: Tier Structure & Escalation Logic

### Tier Structure

| Tier | Role | Kaam |
|------|------|------|
| **Tier 1** | Service Desk (Tum!) | 80% basic issues — password reset, software install, basic networking |
| **Tier 2** | Desktop Support / SysAdmin | Advanced issues, physical desk visit, server deep access |
| **Tier 3** | Backend Engineers / Vendors | Code bugs, hardware failure, Microsoft/Cisco experts |

---

### 🚨 Escalation Kab Karte Hain?

Ticket Tier 2 ko kab saunpoge?

1. Tumhare paas **Admin Access** na ho (e.g., Active Directory mein changes).
2. **30 minutes** ho gaye troubleshooting mein par koi progress nahi aur SLA breach hone wali hai.
3. Issue **P1 Critical** scale ka ho (e.g., poora network router phuk gaya).

---

## ✍️ PART 4: Ticket Documentation (Good vs Bad)

> *"If it's not documented, it didn't happen."*

**❌ BAD DOCUMENTATION:**
```
"PC issue fixed."
```
Manager poochega — kya fixed? Kaise fixed? Kuch pata nahi.

**✅ GOOD DOCUMENTATION:**
```
User: Rahul, Finance Dept.
Issue: Web app not loading — DNS_PROBE_FINISHED_NXDOMAIN error.
Troubleshooting:
  - Checked local IP via ipconfig — valid.
  - Pinged gateway — successful.
  - Flushed DNS using ipconfig /flushdns.
  - Changed primary DNS to 8.8.8.8.
Resolution: Web app loaded successfully.
User confirmed resolution over call at 3:45 PM.
```

---

## 🛠️ PART 5: ServiceNow & Crucial Metrics

**ServiceNow (ITSM Tool)** — IT industry ka king. Web-based portal jahan saare tickets, assets (CMDB), aur knowledge base manage hote hain.

### 4 Key Performance Metrics

| Metric | Full Form | Matlab |
|--------|-----------|--------|
| **FCR** | First Call Resolution | Pehli hi call par issue solve — kisi ko transfer nahi karna pada ⭐ |
| **MTTR** | Mean Time To Resolve | Average time ek ticket solve karne mein |
| **CSAT** | Customer Satisfaction Score | Ticket close hone ke baad user ki rating |
| **SLA Compliance** | — | Kitne % tickets bina breach ke time par solve kiye (Target: 95%+) |

---

## 🚀 Practice Scenarios

**Scenario 1:** Naya server hai — port 8080 pe web app chal rahi hai. Users connect nahi kar pa rahe. Firewall rule banana hai.

**Scenario 2:** Security team ne bola — Telnet (port 23) block karo poore network pe. Exact command?

**Scenario 3:** User bolta hai "ping nahi ho raha tumhare PC ko." Kya dikkat hai aur fix command kya hogi?

**Scenario 4:** Troubleshooting ke liye temporarily firewall off karna hai — test ke baad wapas on karna hai. Dono commands?
