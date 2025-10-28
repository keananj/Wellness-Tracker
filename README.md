# Emergency Call – Wellness Tracker

**Wellness Tracker** adalah sebuah dashboard web sederhana dan menenangkan yang dibuat menggunakan framework **Vue.js**. Tujuan utama dari website ini adalah membantu pengguna melakukan *self check-in*, memantau suasana hati (*mood*), menulis rasa syukur, menjadwalkan sesi konseling, dan mendapatkan motivasi harian—semuanya dalam satu *dashboard* yang lembut dan mendukung kesehatan mental.

---

## Tujuan Proyek

Website ini dirancang untuk mempromosikan **kesehatan mental dan kesadaran diri (mindfulness)** melalui antarmuka yang sederhana dan menenangkan. Fokus utamanya bukan pada banyaknya fitur, melainkan pada **kejelasan, ketenangan, dan fungsionalitas inti**. 

Proyek ini bertujuan menampilkan *Wellness Tracker Dashboard*, format **satu halaman (single-page)** dianggap paling efektif agar pengguna dapat melihat seluruh fitur utama dengan jelas tanpa distraksi.Dengan satu halaman yang rapi dan responsif, proyek ini menggambarkan keseimbangan antara desain, fungsionalitas, dan tujuan emosional dari sebuah *wellness tracker*.

---

## Fitur Utama

### **Dashboard Utama**

* Tampilan bersih dan hangat dengan sapaan berdasarkan waktu (pagi, siang, malam).
* Kutipan motivasi harian yang berubah secara otomatis untuk memberikan semangat positif.
* Tata letak berbasis grid yang rapi, menyatukan semua fitur utama dalam satu halaman.

### **Konseling**

* Menampilkan daftar sesi konseling yang akan datang dan yang telah selesai.
* Fitur untuk **menambah**, **mengubah**, dan **menghapus** jadwal konseling.
* Pemilihan tanggal dan waktu untuk janji konseling berikutnya.
* Ringkasan kecil seperti total sesi dan sesi dalam bulan berjalan.

### **Pelacak Suasana Hati (Mood Tracker)**

* Laporan suasana hati mingguan yang menampilkan pola emosi pengguna.
* Representasi menggunakan emoji, label, atau grafik batang sederhana.
* Disertai pesan refleksi singkat untuk meningkatkan kesadaran diri.

### **Catatan Syukur (Gratitude Log)**

* Kolom teks sederhana bagi pengguna untuk menulis hal-hal yang disyukuri setiap hari.
* Mendorong pengguna berpikir positif dengan pertanyaan *“Apa yang kamu syukuri hari ini?”*

### **Musik Relaksasi**

* Tombol kecil untuk memutar atau menghentikan musik latar yang menenangkan.
* Menambah suasana damai dan fokus selama pengguna menggunakan aplikasi.

### **Motivasi Harian**

* Menampilkan kutipan motivasi acak setiap kali halaman dimuat.
* Memberikan rasa inspirasi dan pembaruan setiap hari.

---

## **Teknologi yang Digunakan**

* **Frontend:** Vue 3 (Composition API + `<script setup>`)
* **Styling:** CSS3 dengan layout grid dan warna tema yang lembut
* **Build Tool:** Vite
* **Font & Icon:** Google Fonts dan emoji kustom

---

## **Struktur Folder**

```
src/
│
├── assets/               # Gambar dan ikon aplikasi
├── components/           # Komponen Vue (Header, Counseling, MoodTracker, dll.)
├── App.vue               # Struktur utama aplikasi
├── main.js               # Titik masuk aplikasi Vue
└── index.html            # File HTML utama
```

---

## **Konsep Desain**

Desain menggunakan warna **lembut dan netral** (beige muda, putih krem, dan aksen merah halus) untuk menciptakan suasana tenang dan aman. Tujuannya agar pengguna merasa nyaman seperti berada di ruang pribadi yang aman secara emosional (*digital safe space*).

---

## **Cara Menjalankan Proyek**

1. Clone repository:

   ```bash
   git clone https://github.com/yourusername/wellness-tracker.git
   ```
2. Masuk ke folder proyek:

   ```bash
   cd wellness-tracker
   ```
3. Instal dependensi:

   ```bash
   npm install
   ```
4. Jalankan server pengembangan:

   ```bash
   npm run dev
   ```
5. Buka di browser:

   ```
   http://localhost:5173
   ```

---
