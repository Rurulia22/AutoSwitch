# AutoSwitch

**AutoSwitch** is an automated lamp switch control system using **ESP32**, **PIR sensor**, **LDR**, and a **servo motor**.  
It can operate automatically based on light and motion, and also be controlled manually via **Blynk** or **Bluetooth**.

---

## 📦 Required Components

| No | Component             | Qty | Notes |
|----|----------------------|-----|-------|
| 1  | ESP32 DevKit (38-pin)| 1   | Main microcontroller board |
| 2  | PIR Sensor           | 1   | Motion detection |
| 3  | LDR (Light Sensor)   | 1   | Light detection |
| 4  | Servo SG90 / similar | 1   | Press/move physical switch |
| 5  | Jumper Wires         | as needed | For connections |
| 6  | Breadboard (optional)| 1   | For prototyping |
| 7  | 5V Power Supply      | 1   | Can be from USB |

---

## 🔌 Wiring Diagram

| Component | ESP32 Pin | Description |
|-----------|-----------|-------------|
| PIR OUT   | 27        | Digital input |
| LDR       | 34 (ADC)  | Analog input |
| Servo     | 26        | PWM output |
| PIR VCC   | 5V        | Power |
| LDR VCC   | 3.3V      | Power |
| All GND   | GND       | Common ground |

---

## 🚀 Assembly Steps

1. **Assemble all components** according to the wiring table.
2. **Install required libraries** in Arduino IDE:
   - `ESP32Servo`
   - `Blynk` (Blynk IoT)
   - `WiFi.h` (built-in with ESP32 core)
   - `BluetoothSerial.h` (built-in with ESP32 core)
3. **Create a new project in Blynk** and note the **Auth Token**.
4. **Create DataStreams in Blynk**:
   - `V0` (Integer) → Manual lamp control (0=OFF, 1=ON)
   - `V1` (String)  → Lamp status ("Nyala"/"Mati" or "On"/"Off")
   - `V2` (Integer) → LDR threshold
5. **Insert your Auth Token, WiFi SSID, and password into the code**.
6. **Upload the code to the ESP32**.
7. **Run and test the system**.

---

## 📱 Blynk Control

- **V0** → Manual lamp control.
- **V1** → Lamp status.
- **V2** → Adjust LDR threshold.

---

## 📡 Bluetooth Control

Bluetooth name: `AutoSwitch_V1`  
Available commands:
- `ON` → Turn lamp ON
- `OFF` → Turn lamp OFF
- `STATUS` → Send lamp status and sensor values
- `SETLDR:XXXX` → Set LDR threshold (0–4095)

---

## ✨ Features

- Automatic mode (PIR + LDR)
- Manual control via Blynk
- Bluetooth control
- Auto-off timer after 10 minutes
- Runtime adjustable LDR threshold

---

## 📜 License

This project is released under the **MIT License**.  
You are free to use, modify, and distribute it with attribution.

---

## 🙌 Credits

Created by **[Your Name]**  
Third-party libraries:
- [ESP32Servo](https://github.com/madhephaestus/ESP32Servo) (MIT License)
- [Blynk](https://github.com/blynkkk/blynk-library) (Apache 2.0 License)
