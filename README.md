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

### ➕ 1. When Charger is Connected
- **Trigger:** When device is connected to power.
- **Action:** Run `Checker` shortcut.

### 📈 2. When Battery Rises Above [Your Choice, e.g., 80%]
- **Trigger:** Battery level rises above `X%`
- **Action:** Run `Checker` shortcut.

### 📉 3. When Battery Falls Below [Your Choice, e.g., 30%]
- **Trigger:** Battery level falls below `X%`
- **Action:** Run `Checker` shortcut.

> ⚠️ Don't forget to **disable "Ask Before Running"** on each automation.

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
  `About 45 minutes. ETA 21:42.`
- **Discharging:**  
  `At 20%, you have about 2 hours and 10 minutes left.`
- **No charge/discharge data yet:**  
  `Warning, your device may not be charging.`

---

## 🧪 Optional Improvements

- Add notification or vibration when estimated time is under 5 minutes.
- Store historical charge/discharge data for trends.
- Sync across devices with iCloud.

---

## ❤️ Credits

Crafted with attention to logic, user experience, and iOS automation — inspired by real-world charging habits.

---

## 📂 License

MIT License. Use freely, modify boldly.
