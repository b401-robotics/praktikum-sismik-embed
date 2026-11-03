# Tutorial Serial Plotter pada VSCode + PlatformIO (Ringkas)

## Persyaratan
| Komponen | Konfigurasi |
|---|---|
| IDE | Visual Studio Code |
| Extension | [Serial Plotter (`badlogicgames.serial-plotter`)](https://marketplace.visualstudio.com/items?itemName=badlogicgames.serial-plotter) |
| Build System | PlatformIO |
| Mikrokontroler | ESP32 |
| Framework | Arduino |
| Interface | USB Serial |
| Baud Rate | 115200 bps |

## 1. Instalasi Extension
1. Buka **Extensions** (`Ctrl+Shift+X`).
2. Cari **Serial Plotter** oleh **badlogic**.
   - Marketplace: https://marketplace.visualstudio.com/items?itemName=badlogicgames.serial-plotter
   - GitHub: https://github.com/badlogic/serial-plotter
3. Klik **Install**, tunggu selesai.
4. Verifikasi: `Ctrl+Shift+P` → ketik **`Serial Plotter: Open pane`** → panel harus terbuka.

## 2. Hubungkan ESP32
1. Sambungkan ESP32 ke komputer via USB (kabel data).
2. Pastikan serial interface dikenali OS dan tidak dipakai aplikasi lain.

## 3. Buka & Konfigurasi Serial Plotter
1. `Ctrl+Shift+P` → **`Serial Plotter: Open pane`**.
2. Cek serial port via terminal PlatformIO:
   ```bash
   pio device list
   ```
3. Pilih serial port ESP32 pada panel (Linux: `/dev/ttyUSB0`/`/dev/ttyACM0`, Windows: `COM3`/`COM4`/dst).
4. Set baud rate sama dengan firmware (`Serial.begin(115200);` → isi **115200**).
5. Klik **Start**.

## 4. Format Data Telemetri
- Satu variabel: `>NamaVariabel:nilai`, contoh: `>RPM:120.5`
- Beberapa variabel: `>Var1:nilai1,Var2:nilai2`, contoh: `>RPM:120.5,Target:150.0`

Contoh firmware:
```cpp
#include <Arduino.h>

void setup()
{
    Serial.begin(115200);
}

void loop()
{
    float rpm = 120.5;
    float target = 150.0;

    Serial.print(">");
    Serial.print("RPM:");
    Serial.print(rpm);
    Serial.print(",Target:");
    Serial.print(target);
    Serial.println();

    delay(100);
}
```

Contoh format lain:
- Sensor tunggal: `>Temperature:28.5`
- Dua sensor: `>Temperature:28.5,Humidity:72.4`
- Encoder: `>Pulse:1250,RPM:120.5`
- Filtering: `>Raw:125.4,Filtered:119.7`
- Sistem kontrol: `>Target:150,RPM:142,Error:8,PWM:187`

## 5. Prosedur Pengambilan Data
1. Hubungkan ESP32 via USB.
2. Upload firmware via PlatformIO.
3. Buka Serial Plotter (`Ctrl+Shift+P` → `Serial Plotter: Open pane`).
4. Pilih serial port ESP32.
5. Set baud rate sesuai firmware (contoh: 115200).
6. Klik **Start**.
7. Jalankan eksperimen (sensor/motor/actuator/sistem yang diuji).
8. Amati grafik setiap data series.
9. Dokumentasikan hasil (screenshot/data).
10. Klik **Stop** sebelum memakai port untuk keperluan lain (mis. upload firmware).

## 6. Fitur Panel
- **Variables**, daftar variabel yang terdeteksi dari data serial.
- **Show/Hide Variables**, tampilkan/sembunyikan variabel tertentu.
- **Auto-Scroll**, grafik otomatis mengikuti sample terbaru (bisa dinonaktifkan untuk analisis sample lama).
- **Zoom**, atur jumlah data yang ditampilkan.

## 7. Best Practice
1. Gunakan nama variabel deskriptif (`RPM_Mentah`, bukan `A`).
2. Satu sample per baris (`>RPM:120,Target:150`).
3. Baud rate firmware dan Serial Plotter harus sama.
4. Jangan campur output debug dengan baris data plotting.
5. Batasi frekuensi pengiriman data sesuai kebutuhan eksperimen.

## 8. Validasi Sistem
1. Kirim `>Test:100` → pastikan komunikasi ESP32 berjalan.
2. Pastikan Serial Plotter menampilkan variabel `Test`.
3. Kirim `>Sensor:100,Filter:90` → pastikan dua series (`Sensor`, `Filter`) muncul.
4. Kirim data berubah (`>Sensor:100,Filter:95` → `>Sensor:105,Filter:98` → ...) → pastikan grafik bergerak.
5. Uji dengan data aktual dari sensor/sistem yang diuji.

## 9. Troubleshooting

| Masalah | Solusi |
|---|---|
| Serial port tidak terdeteksi | Cek `pio device list`, pastikan kabel USB mendukung data. |
| Serial Plotter tidak menampilkan data | Cek serial port, baud rate, status firmware, format data, koneksi plotter. |
| Data diterima tapi grafik tidak muncul | Pastikan format `>Nama:nilai` benar (bukan `=`). |
| Grafik hanya menampilkan sebagian variabel | Pastikan setiap variabel pakai format `Nama:nilai`, dipisah koma. |
| Upload firmware gagal setelah pakai Serial Plotter | Klik **Stop** di Serial Plotter → pastikan port terlepas → upload ulang. |

## 10. Penghentian
1. Klik **Stop**.
2. Pastikan koneksi serial sudah terputus sebelum upload firmware berikutnya (hindari konflik port antara Serial Plotter dan PlatformIO Upload).
