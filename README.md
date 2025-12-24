# 💧 Smart Water Leakage Detection System (Arduino)

An **Arduino-based Smart Water Leakage Detection System** that continuously monitors water leakage in real time, measures leak duration with high precision, and indicates leakage severity using LEDs.

---

## 🚀 Features

- 🔍 Real-time water leakage detection using an analog water sensor  
- ⏱ Measures leak duration with microsecond-level precision  
- 🚨 Leakage severity indication using LEDs  
  - 🔴 **High Severity** – Strong leakage signal  
  - 🟡 **Low Severity** – Moderate leakage signal  
- 🖥 Serial command interface for monitoring and control  
- ♻️ System reset and threshold inspection via serial commands  

---

## 🧰 Components Used

| Component | Description |
|---------|-------------|
| Arduino Uno | Microcontroller board |
| Water Sensor | Analog water leakage sensor |
| Control Pin | Digital Pin 3 (sensor power control) |
| Red LED | Digital Pin 13 (high severity) |
| Yellow LED | Digital Pin 12 (low severity) |
| Resistor | 1kΩ (voltage divider setup) |
| Serial Monitor | Debugging & interaction (9600 baud) |

---

## ⚙️ How It Works

1. The Arduino powers the water sensor using a digital control pin.
2. Sensor readings are continuously taken from **analog pin A0**.
3. If the sensor value falls below a predefined threshold:
   - A water leak is detected
   - The leak start time is recorded
4. While the leak continues:
   - The system calculates total leak duration
   - LEDs indicate the severity of leakage
5. When no leak is detected:
   - Both LEDs remain OFF
   - Timer pauses until the next detection

---

## 🚦 Severity Indication Logic

| Sensor Value | Condition | LED Status |
|-------------|-----------|------------|
| `< 600` | High severity leak | 🔴 Red LED ON |
| `600 – 1000` | Moderate leak | 🟡 Yellow LED ON |
| `> 1000` | No leak | All LEDs OFF |

---

## 📟 Serial Command Interface

Open the **Serial Monitor** at **9600 baud** and use the following commands:

| Command | Description |
|--------|-------------|
| `r` | Reset system state and leak timer |
| `t` | Display the current threshold value |

---

## 🧪 Threshold Calibration

- Default threshold value is set to **1000**
- Adjust this value based on sensor behavior and environment

```cpp
int threshold = 1000; // Modify if calibration is needed
