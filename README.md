<div align="center">
  <img src="img/header.png" alt="Header Praktikum Mikrokontroler" width="100%" style="border-radius: 10px;">
  <br><br>

  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=28&pause=1000&color=007BFF&center=true&vCenter=true&width=600&lines=Selamat+Datang+di+Praktikum;Mikrokontroler+%26+Embedded+System;ESP32%2C+STM32%2C+Sensor%2C+Aktuator;Explore+FreeRTOS%2C+Filtering%2C+PID" alt="Typing SVG" />
  </a>

  <p>
    <b>Praktikum ini merupakan bagian dari mata kuliah Mikrokontroler & Embedded System yang bertujuan untuk memberikan pemahaman praktis mengenai konsep dasar mikrokontroler, interfacing sensor dan aktuator, komunikasi serial, real-time operating system, hingga sistem kontrol digital.</b>
  </p>

  <p>
    <img src="https://img.shields.io/badge/ESP32-E7352C?style=for-the-badge&logo=espressif&logoColor=white" alt="ESP32">
    <img src="https://img.shields.io/badge/STM32-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white" alt="STM32">
    <img src="https://img.shields.io/badge/PlatformIO-FF7F00?style=for-the-badge&logo=platformio&logoColor=white" alt="PlatformIO">
    <img src="https://img.shields.io/badge/Arduino-00979D?style=for-the-badge&logo=arduino&logoColor=white" alt="Arduino">
    <img src="https://img.shields.io/badge/FreeRTOS-2496ED?style=for-the-badge&logo=freertos&logoColor=white" alt="FreeRTOS">
  </p>
</div>

---

## 📚 Apa yang Akan Dipelajari?

Dalam modul-modul praktikum ini, kamu akan mempelajari dan mengimplementasikan beberapa konsep penting, di antaranya:

### 1. **Pengantar Mikrokontroler & Dasar Pemrograman**

- Pengenalan STM32 Blackpill (framework Arduino) dan ESP32 (framework ESP-IDF & Arduino)
- Resistor pull-up dan pull-down (eksternal maupun internal)
- Debouncing pada input tombol berbasis GPIO
- Pembacaan ADC sebagai mode akses GPIO analog (sensor LDR)

### 2. **Sensor Berdasarkan Basis Pengukuran & Aktuator Motor**

- Sensor resistif (joystick), kapasitif (touch TTP223), dan induktif (Hall Effect)
- Sensor basis akustik (ultrasonik HC-SR04) dan optik (IR obstacle)
- Kontrol kecepatan dan arah putar motor DC via PWM & driver L298N
- Kontrol posisi motor stepper dan sudut motor servo
- Kontrol kecepatan motor brushless (BLDC) menggunakan ESC

### 3. **Komunikasi Serial & Interfacing Modul**

- Komunikasi UART antar board ESP32
- Interfacing multi-device pada bus I2C (OLED SSD1306 + MPU6500)
- Interfacing modul sensor IMU MPU6500 via bus SPI hardware
- Pembacaan data SPI berkecepatan tinggi dengan DMA (Direct Memory Access)
- Komunikasi Ethernet via SPI menggunakan modul W5500

### 4. **Interrupt, Timer, Watchdog, & Multitasking**

- External interrupt untuk manual recovery sistem dan decoding quadrature encoder
- Hardware timer interrupt untuk tugas periodik non-blocking
- Watchdog timer (WDT) untuk keandalan dan auto-recovery sistem
- Multitasking menggunakan FreeRTOS (Task & Queue)

### 5. **Sensor Filtering & Dasar Sistem Kontrol (PID)**

- Perhitungan dan konversi pulsa quadrature encoder menjadi RPM
- Filtering sinyal sensor: Low-Pass Filter Alpha dan Kalman Filter
- Sistem kontrol loop tertutup (closed-loop): On-Off dan Proportional (P)
- Kontrol PID lengkap beserta proses tuning parameter

---

## 🛠 Aplikasi dan Tools yang Dibutuhkan

Apa aja sih aplikasi yang kalian butuhkan?
Nah, untuk melakukan praktikum ini, kamu perlu menginstal aplikasi berikut:

- **Visual Studio Code**  
  Editor kode utama yang digunakan sepanjang praktikum.  
  Link Download : https://code.visualstudio.com/
- **PlatformIO IDE** (Ekstensi VSCode)  
  Lingkungan pengembangan embedded untuk membuat project, build, serta upload firmware ke STM32 maupun ESP32.
- **Driver USB-to-Serial & ST-Link**  
  Driver ST-Link (STSW-LINK009) untuk STM32 Blackpill, serta CP2102/CH340 untuk board ESP32. Panduan dan file installer tersedia pada folder `Driver/` dan `Setup Inisialisasi/`.
- **Serial Plotter** (Ekstensi VSCode oleh badlogic)  
  Alat bantu visualisasi data serial secara real-time dalam bentuk grafik (digunakan pada pengujian filtering dan PID).

