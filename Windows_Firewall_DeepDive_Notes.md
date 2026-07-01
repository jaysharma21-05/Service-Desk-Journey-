# 🛡️ Windows Firewall Deep Dive

> **Firewall kya hai?**
> Firewall computer ka security guard hai jo computer ke andar aane wale aur bahar jaane wale traffic par nazar rakhta hai.

---

## 🛑 PART 1: Profiles Samjho (Windows Ki 3 Aankhein)

Windows Firewall ekdum smart hai. Wo har network ko ek hi nazar se nahi dekhta. Usne duniya ko 3 alag-alag situations (Profiles) mein baanta hua hai taaki security sahi se bani rahe.

---

### 1. Domain Profile (Office Wali Life)

- **Kab activate hoti hai:** Jab tu kisi aisi company ke network se connected ho jahan saare computers ek central system (Active Directory / Domain Controller) se jude hote hain.
- **Rule:** Yahan IT Admin jo bolta hai, wahi hota hai. Settings company ke hisab se tait hoti hain.

---

### 2. Private Profile (Ghar Ka Sukoon)

- **Kab activate hoti hai:** Jab tu apne ghar ke Wi-Fi se connected hota hai aur Windows tujhse poochta hai *"Do you want your PC to be discoverable?"* aur tu **Yes** bolta hai.
- **Rule:** Windows ko pata hai ki ye tera ghar hai. Isliye yahan settings thodi **Relaxed (dheeli)** hoti hain taaki tu printer aur doosre local PCs se easily connect ho sake.

---

### 3. Public Profile (Khatra Area! 🚨)

- **Kab activate hoti hai:** Jab tu kisi Airport, Railway Station, ya Cafe ke Free Wi-Fi se connect hota hai.
- **Rule:** Windows ekdum alert ho jata hai! Usko pata hai ki is public Wi-Fi par koi bhi hacker baitha ho sakta hai jo packet sniffing ya exploit maar raha ho. Isliye yahan **Strictest Settings** lagti hain. Bahar se aane wale lagbhag saare connections block hote hain.

---

## 💻 Command Check: Status Kaise Dekhein?

```cmd
netsh advfirewall show allprofiles
```

| Part | Matlab |
|------|--------|
| `netsh` | Network command utility |
| `advfirewall` | Advanced Firewall |
| `show allprofiles` | Teeno profiles ka status dikhao |

**Output:** Tujhe dikhayega ki teeno profiles `ON` hain ya `OFF`.

---

## 🍽️ THE DESI ANALOGY: The Bodyguard's 3 Modes 🕶️

Maan lo tu ek bohot bada VIP hai aur tera ek personal **Bodyguard (Firewall)** hai:

- **Ghar Par (Private Profile):** Tu apne ghar par dost aur parivaar ke sath baitha hai. Bodyguard ekdum relaxed hai. Koi bhi room mein aata-jaata hai, wo zyada pooch-taach nahi karta, kyunki sab log trusted hain.

- **Office Mein (Domain Profile):** Tu office mein meeting mein hai. Bodyguard company ke rules follow karta hai. Jo badde sahab (IT admin) bolenge, sirf unhi ko andar aane dega.

- **Mela / Public Market mein (Public Profile):** Tu Sikkim ke kisi crowded mele mein ghoom raha hai. Ab Bodyguard apni kaali chashma pehan kar ekdum tait khada hai. Koi bhi anjaan insaan agar tere paas 2 step bhi badhega, bodyguard use wahin rokk dega jab tak poori tasalli na ho jaye.

---

## 📊 Quick Reference Table

| Profile | Situation | Security Level |
|---------|-----------|----------------|
| Domain | Company/Office network | IT Admin controls |
| Private | Ghar ka Wi-Fi | Relaxed ✅ |
| Public | Airport/Cafe Wi-Fi | Strictest 🚨 |
