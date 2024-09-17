---
tags:
  - resource
tanggal: 2024-09-17
cssclasses:
  - center-images
---
___
- **Potentiometer** (sering disebut “pots”) adalah resistor variatif yang bisa digunakan untuk menaikkan atau menurunkan hambatan listrik.
	- Analogi seperti keran air, semakin "diputar" semakin banyak air (dalam hal ini listrik) keluar.
- Memiliki tiga Pin:
	- Pin yang di tengah (wiper) memberikan sinyal yang berbeda-beda.
	- Salah satu Pin luar terhubung ke VCC (biasanya 5V) dan yang lainnya ke GND.
	- Memutar knob akan menyesuaikan hambatan, yang mengubah tegangan output yang dapat dibaca dari pin tengah.
___
Contoh: mengatur intensitas cahaya LED
```c
int potPin = A0;  // Potentiometer connected to analog pin A0
int ledPin = 9;   // LED connected to PWM pin 9
int potValue = 0; // Variable to store pot value

void setup() {
  pinMode(ledPin, OUTPUT);
}

void loop() {
  potValue = analogRead(potPin);  // Read potentiometer value
  int brightness = map(potValue, 0, 1023, 0, 255);  // Map to 0-255
  analogWrite(ledPin, brightness);  // Set LED brightness
  delay(10);
}
```