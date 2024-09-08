---
tags:
  - X
tanggal: 2024-09-03
cssclasses:
  - center-images
---
___
# Tujuan
Membuat program untuk mengontrol kecerahan LED dengan efek "fading" menggunakan [[Pulse Width Modulation (PWM)]], sehingga LED dapat bertransisi dari terang ke gelap dan sebaliknya secara bertahap.
## Rangkaian
![[image_20240908144332.jpg|500]]
## Kode Program
```c
int ledPin = 9; 
int brightness = 0; 
int fadeAmount = 5;

void setup() {
  pinMode(ledPin, OUTPUT);
}

void loop() {
  analogWrite(ledPin, brightness);
  brightness = brightness + fadeAmount;
  
  if (brightness <= 0 || brightness >= 255) {
    fadeAmount = -fadeAmount;
  }
  delay(30);
}
```
___
# Penjelasan
### Membuat Variable
```c
int ledPin = 9; 
int brightness = 0; 
int fadeAmount = 5;
```
- **`int ledPin = 9;`**: Variabel `ledPin` menyimpan nomor pin digital (9) yang akan digunakan untuk mengontrol LED.
- **`int brightness = 0;`**: Variabel `brightness` menyimpan tingkat kecerahan LED. Nilai ini akan diatur antara 0 hingga 255, di mana 0 adalah kondisi mati (LED tidak menyala) dan 255 adalah kondisi paling terang.
- **`int fadeAmount = 5;`**: Variabel `fadeAmount` menentukan seberapa besar perubahan kecerahan LED dalam setiap siklus. Nilai 5 berarti kecerahan LED akan berubah sebanyak 5 unit setiap kali loop dijalankan, baik bertambah atau berkurang tergantung pada kondisi.
### Atur mode PIN
```c
void setup() {
  pinMode(ledPin, OUTPUT);
}
```
- **`pinMode(ledPin, OUTPUT);`**: Fungsi `pinMode()` digunakan untuk mengatur mode pin yang akan digunakan. Pada kasus ini, pin 9 (`ledPin`) diatur sebagai _output_, yang berarti bahwa Arduino akan mengirim sinyal keluar melalui pin tersebut untuk mengendalikan LED. Setiap pin dapat diatur sebagai _input_ atau _output_ tergantung kebutuhan, dan di sini kita mengirimkan sinyal untuk mengontrol perangkat (LED).
### Void Loop
```c
void loop() {
	// Kode lainnya
}
```
- `void loop()`: Berfungsi mengulang kode yang ada di dalamnya selama Arduino hidup.
### Mengatur kecerahan LED via `analogWrite()`
```c
analogWrite(ledPin, brightness);
```
- `analogWrite(ledPin, brightness);`: Fungsi `analogWrite()` digunakan untuk mengatur kecerahan LED dengan cara mengirimkan sinyal khusus ke pin yang ditentukan (dalam hal ini, pin 9).
	- **Sinyal PWM**: Meskipun pin Arduino hanya bisa mengirim sinyal digital (HIGH atau LOW), kita bisa meniru efek analog dengan mengubah rasio antara HIGH dan LOW dalam waktu yang sangat cepat. Ini disebut **Pulse Width Modulation (PWM)**.
	- **Bagaimana PWM Bekerja**: Dengan menggunakan PWM, kita mengatur seberapa lama pin berada di kondisi HIGH dan seberapa lama berada di kondisi LOW dalam satu siklus.
	    - Jika sinyal HIGH lebih lama daripada LOW, LED akan terlihat lebih terang.
	    - Jika sinyal LOW lebih lama daripada HIGH, LED akan terlihat lebih redup.
	- **Nilai brightness**: Nilai yang diberikan pada `analogWrite()` (antara 0 hingga 255) mengatur seberapa lama pin berada dalam kondisi HIGH dalam satu siklus. Nilai 0 berarti LED mati (karena pin selalu LOW), sedangkan nilai 255 berarti LED sangat terang (karena pin selalu HIGH).
### Menambah kecerahan LED
```c
brightness = brightness + fadeAmount;
```
- **`brightness = brightness + fadeAmount;`**: Bagian  ini menambahkan nilai `fadeAmount` ke variabel `brightness`. Awalnya, `brightness` dimulai dari 0, dan setiap kali loop berjalan, nilai `brightness` bertambah sebesar 5 (nilai dari `fadeAmount`).
### Kondisi pembalikan kecerahan (Terang/Gelap)
```c
if (brightness <= 0 || brightness >= 255) {
	fadeAmount = -fadeAmount;
}
```
- **`if (brightness <= 0 || brightness >= 255)`**: Kondisi ini digunakan untuk membalik kecerahan. Ketika nilai `brightness` mencapai 0 atau 255, variabel `fadeAmount` akan dibalik. Jika `brightness` mencapai 255, artinya LED telah mencapai kecerahan maksimum, dan untuk mulai meredupkan, nilai `fadeAmount` diubah menjadi negatif (`-fadeAmount`). Hal yang sama terjadi ketika nilai `brightness` mencapai 0.
### Delay
```c
delay(30);
```
- **`delay(30);`**: Fungsi `delay()` membuat program berhenti sejenak selama 30 milidetik sebelum menjalankan loop berikutnya.
___
