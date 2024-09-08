---
tags:
  - resource
tanggal: 2024-09-08
cssclasses:
  - center-images
---
___
# Apa itu PWM?
- **PWM** adalah singkatan dari **Pulse Width Modulation**.PWM adalah suatu teknik yang digunakan untuk mengontrol daya yang diberikan ke perangkat listrik.
- Alih-alih mengirimkan tegangan yang konstan, PWM mengirimkan sinyal yang hidup dan mati dengan cepat.

# Bagaimana Cara Kerja PWM?
- Bayangkan kamu memiliki sakelar lampu yang bisa kamu nyalakan dan matikan dengan sangat cepat.
- Lamanya waktu sakelar menyala dibandingkan dengan lamanya sakelar mati disebut **duty cycle**.
- Jika sakelar menyala untuk waktu yang lebih lama daripada mati, cahayanya akan tampak lebih terang. Jika sakelar mati lebih lama daripada menyala, cahayanya lebih redup.

# Arduino dan PWM
- Pada papan Arduino, beberapa pin digital dapat digunakan untuk PWM.
- Pin ini biasanya ditandai dengan tanda tilde (~), seperti `~3` atau `~9.

# Fungsi PWM di Arduino
- Gunakan function `analogWrite()` untuk mengirim sinyal analog.
___
> [!attention] **Hal yang perlu diketahui**
> - Pin PWM **hanya** bisa digunakan untuk mengirim sinyal analog.
> - Untuk membaca sinyal analog, gunakan pin analog seperti `A0`, `A1`, dll.