# 🏥 MediQueue — Sistem Simulasi Antrian Rumah Sakit

Sistem simulasi antrian rumah sakit berbasis web yang dibangun menggunakan struktur data **Queue** dan **Heap**. Dirancang dengan tampilan navy elegan untuk mensimulasikan alur pelayanan pasien dari pendaftaran hingga selesai, termasuk layanan apotek dan pemanggilan ambulan darurat.

> ⚠️ **Disclaimer:** Proyek ini dibuat untuk keperluan edukasi/simulasi (tugas struktur data). Data tersimpan secara lokal di browser pengguna (`localStorage`) dan belum terhubung ke backend/database terpusat, sehingga belum cocok digunakan sebagai sistem produksi rumah sakit sungguhan.

---

## ✨ Fitur Utama

### 1. Dashboard
Menampilkan ringkasan operasional secara real-time:
- Jumlah pasien menunggu
- Jumlah pasien sedang dilayani
- Jumlah pasien prioritas tinggi
- Rata-rata waktu tunggu
- Daftar antrian berikutnya & log aktivitas terbaru

### 2. Pendaftaran Pasien
Form pendaftaran dengan data: nama, umur, keluhan, dan kategori (**Normal**, **Prioritas**, **Darurat**).
- Pasien **Normal** → masuk struktur **Queue** (FIFO)
- Pasien **Prioritas/Darurat** → masuk struktur **Heap** dan didahulukan

### 3. Halaman Antrian
Menampilkan seluruh pasien yang sedang menunggu, dengan urutan pelayanan otomatis:
**Darurat → Prioritas → Normal**

### 4. Apotek (Antrian Pengambilan Obat)
Pasien yang telah selesai diperiksa dapat mengajukan antrian pengambilan obat di apotek.

### 5. Ambulan
Form pemanggilan ambulan darurat lengkap dengan status real-time (Dikirim → Menuju Lokasi).

### 6. Kontak
Daftar nomor layanan penting rumah sakit (IGD, CS, Apotek, Ambulan) serta form kirim pesan.

### 7. Riwayat
Arsip pasien yang telah selesai dilayani, lengkap dengan lama waktu tunggu — dapat **diekspor ke PDF**.

---

## 🧠 Struktur Data yang Digunakan

| Struktur Data | Digunakan Untuk | Kompleksitas |
|---|---|---|
| **Queue (FIFO)** | Antrian pasien kategori Normal | Enqueue/Dequeue O(1) |
| **Binary Max-Heap** | Antrian pasien Prioritas & Darurat | Insert/Extract-Max O(log n) |

Logika prioritas pada heap: pasien **Darurat** memiliki skor tertinggi, disusul **Prioritas**, dengan tie-breaker berdasarkan urutan pendaftaran (FIFO) agar adil antar pasien dalam kategori yang sama.

---

## 🛠️ Teknologi

- **HTML5, CSS3, JavaScript (Vanilla)** — tanpa framework, satu file (`index.html`)
- **jsPDF** & **jspdf-autotable** (via CDN) — untuk fitur export riwayat ke PDF
- **localStorage** — penyimpanan data sisi klien agar data tidak hilang saat refresh
- Font: **Fraunces**, **Space Grotesk**, **JetBrains Mono** (Google Fonts)

---

## 🚀 Cara Menjalankan

### Opsi 1 — Buka langsung
Cukup buka file `index.html` di browser apa pun (Chrome, Edge, Firefox).

### Opsi 2 — Live Demo (GitHub Pages)
🔗 [https://USERNAME.github.io/mediqueue/](https://USERNAME.github.io/mediqueue/)
*(ganti `USERNAME` dengan username GitHub kamu setelah deploy)*

---

## 📂 Struktur Proyek

```
mediqueue/
├── index.html      # seluruh aplikasi (HTML + CSS + JS dalam satu file)
└── README.md        # dokumentasi proyek
```

---

## 📌 Catatan Teknis

- Data pasien, antrian, riwayat, apotek, dan ambulan tersimpan otomatis di `localStorage` browser.
- Tombol **Reset Semua Data** tersedia di footer untuk mengembalikan ke data contoh awal.
- Fitur export PDF membutuhkan koneksi internet karena library dimuat dari CDN.

---

## 📄 Lisensi

Proyek ini dibuat untuk keperluan pembelajaran. Bebas digunakan, dimodifikasi, dan dikembangkan lebih lanjut untuk tujuan edukasi.
