# LineFollower
# 🤖 Line Follower Robot — Model Engineering College

> **🏆 First Prize Winner** — Line Follower Robot Competition, Model Engineering College

---

## 📌 Overview

An autonomous line-following robot built for the MEC robotics competition, capable of navigating a complex track with multiple checkpoints, junctions, and special maneuvers — all handled intelligently using IR sensing and custom control logic.

---

## ⚙️ Hardware

| Component | Details |
|---|---|
| **Motor Driver** | TB6612FNG Dual H-Bridge |
| **IR Sensor Array** | QTR-8RC (8-channel reflectance sensor) |
| **Power Supply** | 2× Lithium-Ion Batteries + Buck Converter |
| **Visual Indicator** | RGB LED |

---

## 🗺️ Track & Task Sequence

The robot navigates a predefined track with 9 distinct checkpoints, each requiring a specific action:

```
┌─────────────────────────────────────────────────────────┐
│  START BOX → CP2 → CP3 → CP4 → JUNCTION → CP6 → CP7 → CP8 → FINAL
└─────────────────────────────────────────────────────────┘
```

| # | Checkpoint | Action |
|---|---|---|
| 1 | **Start Box** | Move straight through |
| 2 | **Checkpoint 2** | Stop for 5 seconds |
| 3 | **Checkpoint 3** | Turn on 🟢 Green LED (begins green zone) |
| 4 | **Checkpoint 4** | Turn off Green LED (ends green zone) |
| 5 | **Junction** *(False Trigger)* | Take left turn — skip the optional loop |
| 6 | **Checkpoint 6** | Perform 360° rotation, then continue |
| 7 | **Checkpoint 7** | Reverse traverse until next checkpoint detected |
| 8 | **Checkpoint 8** | Reverse traverse, ignore next checkpoint, stop at subsequent one |
| 9 | **Final Checkpoint** | Stop and blink 🔴 Red LED 5 times |

---

## 💡 RGB LED Behavior

| Color | Trigger | Meaning |
|---|---|---|
| 🟢 Green (ON) | Checkpoint 3 | Entered green zone |
| 🟢 Green (OFF) | Checkpoint 4 | Exited green zone |
| 🔴 Red Blink ×5 | Final Checkpoint | Task complete! |

---

## 🧠 Key Logic Highlights

- **PID Control** via QTR-8RC for smooth line tracking
- **Checkpoint Detection** using full-sensor blackout (all sensors over dark line)
- **False Trigger Handling** at junction — robot correctly identifies and ignores the decoy path
- **Reverse Traversal** implemented at CP7 and CP8 with intelligent checkpoint counting
- **360° Rotation** executed at CP6 with timed motor control

---

## 📁 Repository Structure

```
📦 line-follower-robot
 ┣ 📂 src/
 ┃ ┣ 📄 main.ino          # Main control loop
 ┃ ┣ 📄 pid.cpp           # PID controller
 ┃ ┣ 📄 sensors.cpp       # QTR-8RC sensor logic
 ┃ ┣ 📄 motors.cpp        # TB6612FNG motor driver
 ┃ ┗ 📄 tasks.cpp         # Checkpoint task handlers
 ┣ 📂 hardware/
 ┃ ┣ 📄 schematic.pdf     # Circuit schematic
 ┃ ┗ 📄 bom.csv           # Bill of materials
 ┣ 📂 docs/
 ┃ ┗ 📄 track_map.png     # Track layout diagram
 ┗ 📄 README.md
```

---

## 🏁 Competition Result

> 🥇 **First Prize** — Line Follower Robot Event  
> 📍 Model Engineering College, Kerala

---

## 👤 Author

**[Your Name]**  
Student, Model Engineering College  
[GitHub](https://github.com/yourusername) · [LinkedIn](https://linkedin.com/in/yourprofile)

---

<p align="center">Made with ⚡ and lots of PID tuning</p>
