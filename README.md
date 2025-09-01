# Real-Time-Triage-Monitoring-System
Real-Time Monitoring System for a hospital Triage Area

---

## 📌 Project Overview  
This project implements a **portable triage system** that continuously monitors vital signs — ECG, heart rate, oxygen saturation (SpO₂), and body temperature — and automatically classifies patients into triage levels (Green, Yellow, Orange, Red).  

The system uses **sensors + ESP8266 + GSM module** for remote monitoring, with **real-time LED + buzzer alerts** and SMS notifications.  

---

## 🎯 Objectives  
- Real-time monitoring of **vital signs** (ECG, SpO₂, HR, Temp).  
- Automated **triage level calculation** using scoring algorithm.  
- Emergency alerts via **LED, buzzer, and GSM SMS**.  
- Prototype with PCB + 3D printed enclosure.  
- 🔮 Future Scope: Miniaturize the PCB by designing sensor circuits at **microcontroller integration level**, instead of mounting all sensors as separate modules.  

---

## 📌 Note on Contribution  
This project was developed as part of a **group project**.  
- The repository and documentation presented here focus only on **my contribution** to the project.  
- My tasks included:  
  - Designing and simulating the triage monitoring system.  
  - Implementing IoT connectivity with ESP8266.  
  - Developing real-time monitoring.  
  - Preparing the initial design for PCB miniaturization.  

---

## 🛠️ System Design  

### ⚙️ Hardware Setup  
- **Microcontroller**: Arduino/ESP-based controller for data acquisition.  
- **Sensors**: Current and voltage sensors to measure energy usage.  
- **Communication**: ESP8266 WiFi module for IoT connectivity.  
- **Data Processing**: Energy usage calculated in real-time.  
- **Visualization**: Data displayed via web dashboard / mobile interface.  

![System Block Diagram](Results/system_design.png)  
*Figure 01: System Design / Block Diagram*  

### Pin Configurations  
- ECG (AD8232) → A0, D5, D6  
- Pulse Oximeter (MAX30100) → I2C (D1, D2)  
- Temperature Sensor (MLX90614) → I2C (D1, D2)  
- LCD Display → I2C (D1, D2) + DC/RES (D5, D6)  
- GSM Module (SIM800L) → D3 (RX), D4 (TX), external 3.7V–4.4V supply  

### Circuit Diagrams  
![ECG Circuit](./images/ecg_circuit.png)  
![Temperature Sensor Circuit](./images/temp_circuit.png)  
![LCD + GSM Circuit](./images/lcd_gsm_circuit.png)  

---

## 🧮 Triage Algorithm  

The algorithm assigns **points** to vital signs and generates a triage level.  

### Vital Sign Ranges  

| Vital Sign | Level A | Level B | Level C | Level D |
|------------|---------|---------|---------|---------|
| Heart Rate (bpm) | 60–100 | 51–59 / 101–110 | 41–50 / 111–120 | ≤40 / ≥120 |
| SpO₂ (%) | 94–100 | 90–93 | 85–89 | <85 |
| Temp (°C) | 36.1–37.2 | 35–36 / 37.3–38.4 | 34.5–34.9 / 38.5–39.4 | <34.5 / >39.4 |

### Scoring Rules  
- Level A → **1 point**  
- Level B → **5 points**  
- Level C → **16 points**  
- Level D → **50 points**  

### Triage Decision Table  

| Score | Triage Level | Colour | Status |
|-------|-------------|--------|--------|
| 1–5   | 4 | 🟢 Green | Safe |
| 6–15  | 3 | 🟡 Yellow | Need Help |
| 16–49 | 2 | 🟠 Orange | Immediate Help |
| ≥50   | 1 | 🔴 Red | Emergency |  

### Algorithm Code Example  
![Algorithm Code](./images/algorithm_code.png)  

### LED Output Samples  
![LED Outputs](./images/led_outputs.png)  

---

## 📊 Results  

- ✅ Sensor readings validated with reference medical devices  
- ✅ Real-time triage indication using **LEDs + buzzer**  
- ✅ Alerts successfully sent to mobile via **GSM**  
- ✅ PCB design in **EasyEDA** + enclosure modeled in **SolidWorks**  

![PCB Design](./images/pcb_design.png)  
![3D Enclosure](./images/3d_model.png)  
![Final Prototype](./images/final_prototype.png)  

---

## 🚀 Features  
- Continuous monitoring of power usage.  
- ioT integration for remote access.  
- Forecasting model for better energy management.  

---

## 🚀 Future Improvements  

- 📏 **Miniaturization**: Custom PCB integrating sensor front-ends directly into the MCU to reduce size.  
- 🔋 **Low-power optimization** for longer operation on battery.  
- 📡 **Cloud integration** for remote monitoring via IoT dashboard.  
- 📱 **Mobile app interface** for real-time triage visualization.  

---

## 🛠 Tools & Software Used
- xxxxxxxxxxxxxxxxxx

---

## 🎯 Skills
- xxxxxxxxxxxxx

---

## 📄 License
This project is shared for educational purposes. Please give credit if you use it.

---

## 📬 Contact
If you have feedback or suggestions, feel free to [open an issue](https://github.com).

---
