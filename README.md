# batteryOps

*Automated battery ETA and charge insights. Powered by iOS Shortcuts.*

batteryOps is a set of Apple Shortcuts designed to intelligently estimate the time remaining to **fully charge** or **completely discharge** your iPhone. It provides real-time duration updates, ETA projections, and smart notifications — all triggered automatically based on your device's charging state or battery level.

---

## 🚀 Features

- 📲 **Time to Charge** – Displays how long it will take to fully charge, with an ETA.
- 🔋 **Time Left** – Estimates how long you have left before your battery is drained.
- 🧠 **Smart checker** – Detects whether you're charging or discharging and calls the right shortcut.
- ⏱️ **Friendly time format** – Human-readable output like `About 1 hour and 5 minutes. ETA 10:45`.
- ⚡ Fully automatic – Triggers based on defined system events (e.g., plugging in, battery %).

---

## 🔧 Setup Guide

batteryOps consists of three main shortcuts:

### 1. **Time to Charge**
- Calculates how long it will take your phone to fully charge.
- Also shows an ETA (estimated time of completion).

### 2. **Time Left**
- Calculates how long your phone can last before hitting 0%.
- Works in reverse of charging — from full to empty.

### 3. **Checker**
- Acts as a bridge.
- Automatically checks if your device is charging.
  - ✅ If plugged in (charging), it runs **Time to Charge**.
  - ❌ else (not charging), it runs **Time Left**.

---

## 🧩 Required Automations (Set in iOS Shortcuts > Automation)

Create **three personal automations**:

<p align="center">
  <img src="https://github.com/user-attachments/assets/266ebeb6-53b7-4379-913f-4034e13f2199" width="300" height="auto"/>
  <img src="https://github.com/user-attachments/assets/7d901d7d-4a1c-4924-981e-c51610692bf6" width="300" height="auto"/>
  <img src="https://github.com/user-attachments/assets/f9bad6f3-793a-4337-95a7-9adb8bbc22a8" width="300" height="auto"/>
</p>


### ➕ 1. When Charger is Connected

<p align="center">
  <img src="https://github.com/user-attachments/assets/a8f2072b-5d0b-40f1-b256-0235bd43b169" width="500" height="auto"/>
</p>

- **Trigger:** When device is connected to power.
<p align="center">
  <img src="https://github.com/user-attachments/assets/bda341a3-e5fe-4c33-b985-532a6d1cd4cf" width="500" height="auto"/>
</p>

- **Action:** Run `Checker` shortcut.
<p align="center">
  <img src="https://github.com/user-attachments/assets/8ed32b97-b0c2-4223-b390-88b8e1f21fa2" width="500" height="auto"/>
</p>

### 📈 2. When Battery Rises Above [Your Choice, e.g., 80%]

<p align="center">
  <img src="https://github.com/user-attachments/assets/b3f1f762-83ea-49d0-af4f-3109f8794a45" width="500" height="auto"/>
</p>

- **Trigger:** Battery level rises above `X%`
<p align="center">
  <img src="https://github.com/user-attachments/assets/5c4de285-e50e-4ec0-8a4b-b7480fd80952" width="500" height="auto"/>
</p>

- **Action:** Run `Checker` shortcut.
  <p align="center">
  <img src="https://github.com/user-attachments/assets/287a1d8c-18d6-4195-ad2b-c88bc1b68c56" width="500" height="auto"/>
</p>

### 📉 3. When Battery Falls Below [Your Choice, e.g., 30%]

<p align="center">
  <img src="https://github.com/user-attachments/assets/b3f1f762-83ea-49d0-af4f-3109f8794a45" width="500" height="auto"/>
</p>

- **Trigger:** Battery level falls below `X%`

<p align="center">
  <img src="https://github.com/user-attachments/assets/869f773b-aeeb-4cb9-ba2b-30ab6b920992" width="500" height="auto"/>
</p>

- **Action:** Run `Checker` shortcut.

<p align="center">
  <img src="https://github.com/user-attachments/assets/8cfc20fa-445d-446d-bfed-7487334d7f6a" width="500" height="auto"/>
</p>

> ⚠️ Don't forget to **disable "Run after confirmation"** on each automation.
<p align="center">
  <img src="https://github.com/user-attachments/assets/557770bc-f74b-4c09-b45c-10d83e7a382e" width="500" height="auto"/>
</p>

---

## 🧠 How It Works (Logic Summary)

1. On trigger, `Checker` runs.
2. It checks if the phone is **charging**.
3. If yes, it runs **Time to Charge**:
   - Gets the rate of charge over time.
   - Calculates time left using battery percentage difference and time elapsed.
   - Adds that duration to current time to generate an ETA.
   - Formats output like:
     > "About 1 hour and 20 minutes. ETA 6:45 PM."
4. If not charging, it runs **Time Left** using similar logic in reverse.

---

## 📌 Output Examples

- **Charging:**
<p align="center">
  <img src="https://github.com/user-attachments/assets/9d62996c-187d-4926-b79c-fac015374828" width="500" height="auto"/>
</p>

- **Discharging:**
<p align="center">
  <img src="https://github.com/user-attachments/assets/3267ca15-443f-4bd8-a50f-9d4cd6029c9f" width="500" height="auto"/>
</p>

- **No increase in charge, despite charger plugged in:**  
<p align="center">
  <img src="https://github.com/user-attachments/assets/ad7093a5-0684-4e46-86d8-abf248729ab9" width="500" height="auto"/>
</p>

---

## ❤️ Credits
**Alex Amygdalios**  
- [Alex Amygdalios 👨🏻‍💻](https://github.com/amygdalios) on GitHub  
- [AlxR25](https://www.reddit.com/u/AlxR25/s/Kg6Oj3ZvCj) on Reddit

Crafted with attention to logic, user experience, and iOS automation — inspired by real-world charging habits.

---

## 📂 License

MIT License. Use freely, modify boldly.
