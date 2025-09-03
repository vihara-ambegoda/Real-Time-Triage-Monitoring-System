# 🏥 Real-Time-Triage-Monitoring-System

IoT-Based Patient Monitoring System with Triage Level Indication
> This is a final year **group project** developed as part of our academic curriculum.  
> The following documentation highlights **my individual contribution** to the hardware development, sensor integration, triage algorithm implementation, and prototype design.

---

## 📌 Project Overview  

The project monitors a patient’s health parameters using various sensors and sends the data securely to an IoT dashboard. Real-time alerts and triage levels are indicated on a hardware module and also sent via SMS using GSM.

![System Block Diagram](Results/system_design.png)  

---

## 🎯 Objectives  
- Real-time monitoring of **vital signs** (ECG, SpO₂, HR, Temp).  
- Automated **triage level calculation** using scoring algorithm.  
- Emergency alerts via **LED, buzzer, and GSM SMS**.  
- Prototype with PCB + 3D printed enclosure.  

---

## ⚙️ My Individual Contribution

- Hardware setup and circuit design
- Sensor integration and data collection
- Implementation of a custom triage algorithm
- PCB and prototype model design
- GSM-based alert message system
  
---

## System Design  

### 🛠️ Development Timeline

1. Selected and purchased sensor components
2. Configured circuits and programmed microcontroller
3. Read sensor outputs and validated accuracy
4. Developed triage algorithm and integrated it into system
5. Designed PCB using EasyEDA
6. Designed 3D prototype model using SolidWorks
7. Integrated GSM module to send alerts to mobile

---

### ⚙️ Hardware Setup  
- **Microcontroller**: Arduino/ESP-based controller for data acquisition.  
- **Sensors**: Vital signs (e.g., temperature, pulse, SpO₂) and environmental sensors (humidity, temperature).  
- **Communication**: ESP8266 WiFi module for IoT connectivity.  
- **Data Processing**: Patient health status processed in real-time.  
- **Visualization**: Data displayed via a web dashboard / local monitoring station.  

### 🧩 Components Used

| Component | Description |
|----------|-------------|
| NodeMCU ESP8266 | Microcontroller + Wi-Fi |
| AD8232 | ECG Heart Monitoring Sensor |
| MAX30100 | Pulse Oximeter & Heart Rate Sensor |
| MLX90614 | Contactless Temperature Sensor |
| SIM800L | GSM Module |
| LCD Display | OLED for output display |

> Note: NIBP sensor was planned but couldn't be procured due to the pandemic.

### Pin Configurations  
- ECG (AD8232) → A0, D5, D6  
- Pulse Oximeter (MAX30100) → I2C (D1, D2)  
- Temperature Sensor (MLX90614) → I2C (D1, D2)  
- LCD Display → I2C (D1, D2) + DC/RES (D5, D6)  
- GSM Module (SIM800L) → D3 (RX), D4 (TX), external 3.7V–4.4V supply  
> A 9V battery + LM2596 buck converter was used to power the GSM module (3.4V – 4.4V).

### Circuit Diagrams  
![ECG Circuit](./images/ecg_circuit.png)  
![Temperature Sensor Circuit](./images/temp_circuit.png)  
![LCD + GSM Circuit](./images/lcd_gsm_circuit.png)  

---

## 🧮 Triage Algorithm  

The algorithm assigns **points** to vital signs and generates a triage level.  

### 📊 Vital Sign Classification

| Vital Sign | Level A | Level B | Level C | Level D |
|------------|---------|---------|---------|---------|
| Heart Rate (bpm) | 60–100 | 51–59 / 101–110 | 41–50 / 111–120 | ≤40 / ≥120 |
| SpO₂ (%) | 94–100 | 90–93 | 85–89 | <85 |
| Temp (°C) | 36.1–37.2 | 35–36 / 37.3–38.4 | 34.5–34.9 / 38.5–39.4 | <34.5 / >39.4 |

### 🧮 Scoring System

| Level | Points |
|-------|--------|
| A     | 1      |
| B     | 5      |
| C     | 16     |
| D     | 50     |

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

- Continuous monitoring of patient vital parameters in the triage area.  
- Data successfully transmitted to IoT cloud/local dashboard.  
- Visualization of trends in health/environment parameters.  
- Early-warning and forecasting models assist in quick decision-making.  

- ✅ Sensor readings validated with reference medical devices  
- ✅ Real-time triage indication using **LEDs + buzzer**  
- ✅ Alerts successfully sent to mobile via **GSM**  
- ✅ PCB design in **EasyEDA** + enclosure modeled in **SolidWorks**  

![PCB Design](./images/pcb_design.png)  
![3D Enclosure](./images/3d_model.png)  
![Final Prototype](./images/final_prototype.png)  

---

## 🚀 Features  
- Real-time monitoring of patient health status.  
- IoT integration for remote access and central monitoring.  
- Forecasting support for proactive decision-making.  
- Scalable for multiple patients in a triage environment. 

---

## 🚀 Future Improvements  

- 📏 **Miniaturization**: Custom PCB integrating sensor front-ends directly into the MCU to reduce size.  
- 🔋 **Low-power optimization** for longer operation on battery.  
- 📡 **Cloud integration** for remote monitoring via IoT dashboard.  
- 📱 **Mobile app interface** for real-time triage visualization.  

- **Miniaturization of PCB**: Instead of mounting all sensors as external modules, future work will design a **custom PCB** that integrates sensor front-ends and microcontroller peripherals. This will make the system more compact, reliable, and portable for hospital deployment.  
- **Advanced Communication Protocols**: Incorporating MQTT/LoRaWAN for larger hospital networks.  
- **Mobile App Integration**: Native mobile application for quick alerts to medical staff.  
- **AI-based Triage Assistance**: Applying ML models for prioritizing patients automatically based on their health parameters.  

---
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
