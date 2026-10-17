# batteryOps

*Automated battery ETA and charge insights. Powered by iOS Shortcuts.*

batteryOps is a set of Apple Shortcuts designed to intelligently estimate the time remaining to **fully charge** or **completely discharge** your iPhone. It provides real-time duration updates, ETA projections, and smart notifications — all triggered automatically based on your device's charging state or battery level.

---

## Features

- **Time to Charge** – Displays how long it will take to fully charge, with an ETA.
- **Time Left** – Estimates how long you have left before your battery is drained.
- **Smart checker** – Detects whether you're charging or discharging and calls the right shortcut.
- **Friendly time format** – Human-readable output like `About 1 hour and 5 minutes. ETA 10:45`.
- **Fully automatic** – Triggers based on defined system events (e.g., plugging in, battery %).

---

## Setup Guide

batteryOps consists of three main shortcuts:

### 1. **Time to Charge -** [Link here](https://www.icloud.com/shortcuts/3c293e5c6add48c8ac73779cc779900f)
- Calculates how long it will take your phone to fully charge.
- Also shows an ETA (estimated time of completion).

### 2. **Time Left -** [Link here](https://www.icloud.com/shortcuts/4460511668a74c7aa4c9ab32848324da)
- Calculates how long your phone can last before hitting 0%.
- Works in reverse of charging — from full to empty.

### 3. **Checker -** [Link here](https://www.icloud.com/shortcuts/2c0e3524c8474b149e13c94f84ca6ed3)
- Acts as a bridge.
- Automatically checks if your device is charging.
  - ✅ If plugged in (charging), it runs **Time to Charge**.
  - ❌ else (not charging), it runs **Time Left**.

---

## Required Automations (Set in iOS Shortcuts > Automation)

Create **three personal automations**:

<p align="center">

<img width="300" height="auto" alt="IMG_3573" src="https://github.com/user-attachments/assets/8201b2c7-3acc-4dfb-ab4c-e6c3adc66553" />

</p>


### 1. When Charger is Connected
- **Trigger:** When device is connected to power.
- **Action:** Run `Checker` shortcut.
<p align="center">
  <img width="500" height="auto" alt="IMG_3575" src="https://github.com/user-attachments/assets/8c756444-1ccd-47f3-9bb0-a3ca95878150" />
</p>

### 2. When Battery Rises Above [Your Choice, e.g., 80%]
- **Trigger:** Battery level rises above `X%`. 80% is recommended because that's when the second phase of charging begins. This phase is commonly known as the constant voltage (CV) phase.
- **Action:** Run `Checker` shortcut.
<p align="center">
  <img width="500" height="auto" alt="IMG_3577" src="https://github.com/user-attachments/assets/8f7b26d1-0423-4b38-886b-866eca365c21" />
</p>

### 3. When Battery Falls Below [Your Choice, e.g., 30%]
- **Trigger:** Battery level falls below `X%`
- **Action:** Run `Checker` shortcut.
<p align="center">
<img width="500" height="auto" alt="IMG_3578" src="https://github.com/user-attachments/assets/3be874e8-5e58-4095-9fd1-9b341fbb40e1" />
</p>


---

## How It Works (Logic Summary)

1. On trigger, `Checker` runs.
2. It checks if the phone is **charging**.
3. If yes, it runs **Time to Charge**:
   - Gets the rate of charge over time.
   - Calculates time left using battery percentage difference and time elapsed (10 minutes).
   - Adds that duration to current time to generate an ETA.
   - Formats output like:
     > "About 1 hour and 20 minutes. ETA 18:45."
4. If not charging, it runs **Time Left** using similar logic in reverse.

---

## Actual Output Examples

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
**Alex** inspired this. Check him out.  
- [Alex Amygdalios 👨🏻‍💻](https://github.com/amygdalios) on GitHub  
- [AlxR25](https://www.reddit.com/u/AlxR25/s/Kg6Oj3ZvCj) on Reddit

Crafted with attention to logic, user experience, and iOS automation.

---

## License

MIT License. Use freely, modify boldly.
