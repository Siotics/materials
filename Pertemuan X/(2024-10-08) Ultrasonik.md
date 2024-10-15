---
tags:
  - X
tanggal: 2024-10-08
cssclasses:
  - center-images
---
___

# Cara Kerja
- Sensor untuk mengukur jarak menggunakan gelombang ultrasonik.
- Gelombang Ultrasonik memiliki frekuensi lebih dari 20.000 Hertz (20 Kilo Hertz)
- Sensor ini bekerja layaknya **Sonar**:
	- Sensor memancarkan gelombang ultrasonik.
	- Gelombang memantul pada objek.
	- Pantulan gelombang balik ke Sensor.
	- Sensor mengukur jarak antar benda dengan menghitung berapa lama gelombang kembali setelah dipancarkan.
# HC-SR04 Ultrasonic Sensor
![[Ultrasonik_Gaming.jpg]]
- **HC-SR04** adalah tipe sensor ultrasonik yang sering digunakan.
	- Terdiri dari dua bagian, **Transmitter** (Memancarkan gelombang ultrasonik) dan **Receiver** (Mendeteksi pantulan gelombang).
- Jarak dari sensor ke objek bisa dihitung menggunakan rumus:
$$
\text{Jarak (Centimeter)} = \frac{\text{Waktu} \times \text{Kecepatan Suara}}{2}
$$
- Kecepatan suara = $0.034cm/µs$ (per mikrodetik).
- Pin dalam HC-SR04:
	- Power (5V)
	- Trigger Pin (ke Pin Digital)
		- Ketika ada listrik, sensor memancarkan gelombang ultrasonik.
	- Echo Pin (ke Pin Digital)
		- Untuk menerima pantulan gelombang ultrasonik. Mengukur berapa lama waktu yang diperlukan.
	- Ground (0V atau GND)
# Contoh Kode
```c
const int triggerPin = 9; // Trigger Pin berada di pin 9
const int echoPin = 10; // Echo Pin berada di pin 10

// duration = waktu; distance = jarak (centimeter)
int duration, distance;

void setup() {
    Serial.begin(9600);
    pinMode(triggerPin, OUTPUT);
    pinMode(echoPin, INPUT);
}

void loop() {
    digitalWrite(triggerPin, LOW);
    delayMicroseconds(2);
	
    digitalWrite(triggerPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(triggerPin, LOW);

    duration = pulseIn(echoPin, HIGH);
    distance = (duration * 0.034 / 2); // Kecepatan suara ~ 0.034 cm/µs

    Serial.print("Distance: ");
    Serial.println(distance);
    delay(1000);
}
```
### Penjelasan
- Matikan pemancar gelombang (`triggerPin LOW`) sejenak untuk menstabilkan sensor, anggap seperti memberi sensor waktu sejenak untuk refresh.
```c
digitalWrite(triggerPin, LOW);
delayMicroseconds(2);
```

- Aktifkan pemancar gelombang (`triggerPin HIGH`), aktifkan selama 10 mikrodetik, kemudian matikan kembali (`triggerPin LOW`).
- HC-SR04 membutuhkan HIGH setidaknya 10 mikrodetik untuk menghasilkan gelombang ultrasonik yang valid.
```c
digitalWrite(triggerPin, HIGH);
delayMicroseconds(10);
digitalWrite(triggerPin, LOW);
```

- `pulseIn` digunakan untuk menghitung berapa lama `echoPin` dalam kondisi HIGH (nyala).
- Ketika Transmitter mengeluarkan gelombang ultrasonik, `echoPin` berada dalam kondisi HIGH.
- Kemudian, ketika gelombang ultrasonik telah ditangkap oleh Receiver, `echoPin` dalam kondisi LOW.
- Lama `echoPin` dalam kondisi high akan disimpan dalam variabel `duration` (variabel waktu atau durasi).
```c
duration = pulseIn(echoPin, HIGH);
```