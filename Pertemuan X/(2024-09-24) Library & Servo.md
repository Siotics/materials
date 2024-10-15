---
tags:
  - X
tanggal: 2024-09-24
cssclasses:
  - center-images
---
___
# Library
- Kumpulan kode/fitur yang sudah ditulis oleh orang lain yang kita bisa gunakan.
- Fungsinya untuk menghemat waktu, daripada menulis kode yang panjang untuk menggerakkan servo, menggunakan sensor, dan lain-lain. Kita bisa gunakan kode yang sudah ditulis oleh orang lain.
- **Cara Instalasi Library di Arduino IDE**
	- Buka Arduino IDE
	- Pergi ke **Sketch** → **Include Library** → **Manage Libraries**.
	- Cari/Search library yang ingin di-Install, contohnya 'Servo'.
	- Klik **Install**
- **Cara menggunakan Library**
	- Setelah Instalasi selesai. Cukup tambahkan `#include <NamaLibrary.h>` di kode. Contohnya:
		```c
		#include <Servo.h>
		```
___
# Servo
- Sebuah jenis Motor (bukan kendaraan) yang kita bisa program atau kontrol perputarannya.
- Servo motor biasanya bisa memutar dari 0° hingga 180°. Namun, ada Servo motor yang bisa memutar sampai 360°.
- Digunakan dalam projek seperti robotika, untuk mengatur lengan/persendian robot.
- **Mini Servo terdiri dari**:
	- Motor DC (Motor Servo)
	   - Mengubah energi listrik menjadi energi mekanik untuk menghasilkan gerakan.
	   - TLDR: Yang buat muter-muter.
	- Gearbox
	   - Dipasang pada motor.  
	   - Berfungsi mengurangi kecepatan motor dan meningkatkan torsi (gaya putar) supaya gerakannya lebih halus dan akurat.
	- Potentiometer  
	   - Sensor yang digunakan untuk mengukur posisi sudut lengan servo secara real-time.
	   - Mengecek apakah posisi motor sudah sesuai dengan sinyal yang dikirim.
	- Control Circuit  
	   - Mengatur perputaran motor berdasarkan sinyal input (sinyal PWM).  
	   - Mengontrol kecepatan, arah, dan posisi motor.
	- Housing  
	   - Pelindung luar yang melindungi komponen servo dari kerusakan fisik dan debu.  
	- Power Supply Terminal  
	   - Terminal tempat sumber daya listrik terhubung untuk menjalankan motor dan control circuit.
- Cara kerja:
	- Servo menggunakan pin [[Pulse Width Modulation (PWM)]]
	- Posisi atau sudut perputaran servo bergantung pada durasi sinyal aktif (HIGH) dari PWM. Semakin lama sinyal HIGH, semakin besar sudut perputarannya.
- Contoh Kode:
```c
#include <Servo.h>

Servo myServo;  // Membuat objek/variabel servo

void setup() {
  myServo.attach(9);  // Servo dikoneksikan di pin 9
}

void loop() {
  myServo.write(90);  // Putar servo 90 derajat
  delay(1000);        // Tunggu 1 detik
  myServo.write(0);   // Putar kembali servo ke 0 derajat
  delay(1000);        // Tunggu 1 detik
}
```
- Pin dalam servo:
![[Screenshot 2024-09-30 073825.png]]