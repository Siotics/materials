---
tags:
  - resource
tanggal: 2024-09-17
cssclasses:
  - center-images
---
___
### Pull-down resistor
- Ketika tombol tidak ditekan, pin terhubung ke ground (LOW). Ketika ditekan, pin ini terhubung ke VCC (HIGH).
- Kamu memerlukan resistor eksternal antara pin dan ground untuk memastikan pin terbaca LOW saat diam (idle).
- TLDR: Button ditekan = HIGH, idle = LOW.
```c
int buttonPin = 2;  // Button connected to digital pin 2
int ledPin = 13;    // LED connected to digital pin 13

void setup() {
  pinMode(buttonPin, INPUT);  // No internal pull-up here
  pinMode(ledPin, OUTPUT);
}

void loop() {
  int buttonState = digitalRead(buttonPin);
  
  if (buttonState == HIGH) {  // Button pressed
    digitalWrite(ledPin, HIGH);  // Turn LED on
  } else {  // Button not pressed
    digitalWrite(ledPin, LOW);   // Turn LED off
  }
}
```
___
### Pull-up resistor
- Kebalikan dari Pull-down.
- Pin ini biasanya terhubung ke VCC (HIGH) saat tidak ditekan. Saat ditekan, pin ini terhubung ke ground (LOW).
- NOTE: Arduino memiliki Pull-up bawaan, jadi tidak perlu kabel tambahan - cukup aktifkan dalam kode.
- TLDR: Button ditekan = LOW, idle = HIGH.
```c
int buttonPin = 2;  // Button connected to digital pin 2
int ledPin = 13;    // LED connected to digital pin 13

void setup() {
  pinMode(buttonPin, INPUT_PULLUP);  // Use internal pull-up resistor
  pinMode(ledPin, OUTPUT);
}

void loop() {
  int buttonState = digitalRead(buttonPin);
  
  if (buttonState == LOW) {  // Button pressed
    digitalWrite(ledPin, HIGH);  // Turn LED on
  } else {  // Button not pressed
    digitalWrite(ledPin, LOW);   // Turn LED off
  }
}
```