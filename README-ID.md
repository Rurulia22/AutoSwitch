# AutoSwitch

Proyek **AutoSwitch** adalah sistem otomatis untuk mengontrol saklar lampu menggunakan **ESP32**, **sensor PIR**, **LDR**, dan **servo**.  
Sistem dapat bekerja otomatis berdasarkan cahaya & gerakan, dikontrol manual lewat **Blynk** atau **Bluetooth**.

---

## 📦 Komponen yang Dibutuhkan

| No | Komponen              | Jumlah | Keterangan |
|----|----------------------|--------|------------|
| 1  | ESP32 DevKit (38 pin)| 1      | Board mikrokontroler utama |
| 2  | Sensor PIR           | 1      | Deteksi gerakan |
| 3  | Sensor LDR           | 1      | Deteksi cahaya |
| 4  | Servo SG90 / setara  | 1      | Menekan/menggerakkan saklar |
| 5  | Kabel jumper         | secukupnya | Untuk koneksi |
| 6  | Breadboard (opsional)| 1      | Untuk prototipe |
| 7  | Sumber daya 5V       | 1      | Bisa dari USB |

---

## 🔌 Skema Wiring

| Komponen | Pin ESP32 | Keterangan |
|----------|----------|------------|
| PIR OUT  | 27       | Digital input |
| LDR      | 34 (ADC) | Analog input |
| Servo    | 26       | PWM output |
| PIR VCC  | 5V       | Daya |
| LDR VCC  | 3.3V     | Daya |
| Semua GND| GND      | Ground bersama |


---

## 🚀 Langkah Pembuatan

1. **Rangkai semua komponen** sesuai tabel wiring.
2. **Pasang library yang dibutuhkan** di Arduino IDE:
   - `ESP32Servo`
   - `Blynk` (Blynk IoT)
   - `WiFi.h` (bawaan ESP32 core)
   - `BluetoothSerial.h` (bawaan ESP32 core)
3. **Buat project baru di Blynk** dan catat **Auth Token**.
4. **Buat DataStreams di Blynk**:
   - `V0` (Integer) → Kontrol manual lampu (0=OFF, 1=ON)
   - `V1` (String)  → Status lampu ("Nyala"/"Mati")
   - `V2` (Integer) → Threshold LDR
5. **Masukkan Auth Token, SSID WiFi, dan password ke kode**.
6. **Upload kode ke ESP32**.
7. **Jalankan dan uji sistem**.

---

## 📱 Kontrol Blynk

- **V0** → Kontrol manual lampu.
- **V1** → Menampilkan status lampu.
- **V2** → Mengubah nilai threshold LDR.

---

## 📡 Kontrol Bluetooth

Nama Bluetooth: `AutoSwitch_V1`  
Perintah yang tersedia:
- `ON` → Nyalakan lampu
- `OFF` → Matikan lampu
- `STATUS` → Kirim status lampu dan nilai sensor
- `SETLDR:XXXX` → Atur threshold LDR (0–4095)

---

## ✨ Fitur Utama

- Mode otomatis (PIR + LDR)
- Kontrol manual via Blynk
- Kontrol via Bluetooth
- Timer otomatis mati setelah 10 menit
- Threshold LDR bisa diubah runtime

---

## 📜 Lisensi

Proyek ini dirilis dengan **MIT License**.  
Silakan gunakan, modifikasi, dan sebarkan dengan mencantumkan kredit.

---

## 🙌 Credit

Dibuat oleh **Ruruu & BITVEL22**  
Library pihak ketiga:
- [ESP32Servo](https://github.com/madhephaestus/ESP32Servo) (MIT License)
- [Blynk](https://github.com/blynkkk/blynk-library) (Apache 2.0 License)
