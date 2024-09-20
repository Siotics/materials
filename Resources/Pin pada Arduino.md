---
tags:
  - resource
tanggal: 2024-09-17
cssclasses:
  - center-images
---
___
### Pin Digital (0-13)
- on/off control (HIGH/LOW).
- Dapat digunakan sebagai **INPUT** atau **OUTPUT**.
- Contoh: LED, membaca status button.
	```c
	int ledPin = 13;
	
	void setup() {
	  pinMode(ledPin, OUTPUT);
	}
	
	void loop() {
	  digitalWrite(ledPin, HIGH);  // Turn LED on
	  delay(1000);                 // Wait 1 second
	  digitalWrite(ledPin, LOW);   // Turn LED off
	  delay(1000);                 // Wait 1 second
	}	
	```

### Pin Analog (A0-A5)
- Digunakan untuk membaca tegangan yang bervariasi.
- Pin-pin ini menerima rentang nilai (0-1023) karena menggunakan konverter analog-ke-digital (ADC) 10-bit.
- Hanya **INPUT**.
- Contoh: Sensor (cahaya, suhu).
	```c
	int sensorValue = 0;
	
	void setup() {
	  Serial.begin(9600);
	}
	
	void loop() {
	  sensorValue = analogRead(A0);  // Read the value from sensor at A0
	  Serial.println(sensorValue);   // Print the value to Serial Monitor
	  delay(100);
	}
	```

### Pin PWM (~3, 5, 6, 9, 10, 11)
- Secara teknis, pin PWM adalah pin digital, tetapi dapat meniru output analog dengan cara berdenyut hidup dan mati dengan sangat cepat.
- Ditandai dengan tanda tilde (~), seperti 3, 5, 6, 9, 10, dan 11.
- Hanya **OUTPUT**.
- Contoh: Peredupan LED, kontrol electric motor.
	```c
	int ledPin = 9;
	
	void setup() {
	  pinMode(ledPin, OUTPUT);
	}
	
	void loop() {
	  for (int brightness = 0; brightness <= 255; brightness++) {
	    analogWrite(ledPin, brightness);  // Increase brightness
	    delay(10);
	  }
	  
	  for (int brightness = 255; brightness >= 0; brightness--) {
	    analogWrite(ledPin, brightness);  // Decrease brightness
	    delay(10);
	  }
	}
	```