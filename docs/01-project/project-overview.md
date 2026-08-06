---
title: Project Overview
version: 0.1.0
status: Draft
---

# Project Overview

## 1. Latar Belakang

Perpustakaan merupakan salah satu unit pendukung utama dalam kegiatan akademik di lingkungan universitas. Seiring meningkatnya kebutuhan akan layanan digital, proses administrasi dan pelayanan perpustakaan perlu dilakukan secara terintegrasi melalui sebuah sistem informasi berbasis web.

Saat ini berbagai aktivitas seperti pendaftaran anggota, pencarian koleksi buku, proses peminjaman, pengelolaan repository karya ilmiah, hingga penyampaian informasi kepada sivitas akademika masih dapat dilakukan secara manual atau menggunakan beberapa sistem yang terpisah. Kondisi tersebut berpotensi menimbulkan ketidakefisienan operasional, kesulitan dalam pengelolaan data, serta pengalaman pengguna yang kurang optimal.

Melalui proyek ini akan dibangun sebuah **Library Management System (LMS)** yang mampu mengintegrasikan seluruh layanan utama perpustakaan ke dalam satu platform berbasis web.

---

## 2. Tujuan Proyek

Pengembangan sistem ini bertujuan untuk:

- Mendigitalisasi layanan perpustakaan universitas.
- Mempermudah proses administrasi perpustakaan.
- Menyediakan katalog buku yang dapat diakses secara daring.
- Mendukung proses peminjaman buku secara elektronik.
- Menyediakan repository karya ilmiah universitas.
- Menyediakan media komunikasi antara pengguna dengan pustakawan.
- Menyediakan dashboard dan laporan operasional sebagai dasar pengambilan keputusan.

---

## 3. Ruang Lingkup

Versi Minimum Viable Product (MVP) mencakup modul-modul berikut.

### 3.1 Manajemen Anggota

Mengelola proses registrasi anggota, persetujuan keanggotaan, autentikasi pengguna, serta administrasi data pengguna.

### 3.2 Manajemen Buku

Mengelola data koleksi buku, eksemplar buku, kategori, penulis, penerbit, serta lokasi penyimpanan buku.

### 3.3 Peminjaman Buku

Mengelola proses pengajuan peminjaman, persetujuan oleh pustakawan, pengambilan buku, pengembalian buku, serta status peminjaman.

### 3.4 Repository Karya Ilmiah

Menyediakan akses terhadap metadata karya ilmiah beserta abstraknya, serta mekanisme pengunduhan dokumen sesuai kebijakan perpustakaan.

### 3.5 Layanan Tanya Pustakawan

Menyediakan media komunikasi antara pengguna dan pustakawan melalui sistem.

### 3.6 Pengumuman

Menyediakan media publikasi informasi resmi dari perpustakaan kepada seluruh pengguna.

### 3.7 Dashboard

Menyediakan ringkasan informasi sesuai peran pengguna.

### 3.8 Pelaporan

Menyediakan laporan operasional perpustakaan yang dapat digunakan oleh administrator.

---

## 4. Ruang Lingkup yang Tidak Termasuk dalam MVP

Fitur berikut tidak termasuk dalam ruang lingkup pengembangan tahap pertama.

- Integrasi Single Sign-On (SSO)
- Perpanjangan masa peminjaman
- Pengembalian buku melalui website
- Integrasi QR Code
- Upload repository secara mandiri oleh mahasiswa atau dosen
- Integrasi dengan sistem akademik universitas

Fitur-fitur tersebut dapat dipertimbangkan pada fase pengembangan berikutnya.

---

## 5. Aktor Sistem

Sistem memiliki tiga aktor utama.

| Aktor | Deskripsi |
|-------|-----------|
| Administrator | Mengelola seluruh data, layanan, dan konfigurasi sistem perpustakaan. |
| Mahasiswa | Menggunakan layanan perpustakaan sesuai hak akses yang dimiliki. |
| Dosen | Menggunakan layanan perpustakaan sesuai hak akses yang dimiliki. |

---

## 6. Target Pengguna

Sistem dirancang untuk melayani sekitar **1.000 pengguna aktif** yang terdiri dari mahasiswa, dosen, dan administrator perpustakaan.

Jumlah tersebut digunakan sebagai dasar awal dalam perancangan arsitektur sistem dan bukan merupakan batas maksimum pengguna.

---

## 7. Teknologi yang Direncanakan

| Komponen | Teknologi |
|----------|-----------|
| Backend | Laravel |
| Admin Panel | Filament |
| Database | MySQL |
| Web Server | Nginx |
| Containerization | Docker |
| Deployment | VPS |

Pemilihan teknologi dapat berubah selama proses pengembangan apabila terdapat kebutuhan teknis yang lebih sesuai.

---

## 8. Pendekatan Pengembangan

Pengembangan proyek menggunakan pendekatan **Documentation-Driven Development (DDD)**.

Seluruh implementasi diawali dengan proses analisis kebutuhan, penyusunan dokumentasi, validasi bersama client, kemudian dilanjutkan ke tahap desain, implementasi, pengujian, dan deployment.

Setiap perubahan kebutuhan sistem harus terlebih dahulu diperbarui pada dokumentasi sebelum diimplementasikan ke dalam source code.

---

## 9. Deliverables

Pada akhir proyek diharapkan dihasilkan artefak sebagai berikut.

- Source code aplikasi.
- Dokumentasi kebutuhan sistem.
- Dokumentasi desain sistem.
- Struktur basis data.
- Dokumentasi API (apabila diperlukan).
- Dokumen deployment.
- Dokumen pengujian.
- Panduan penggunaan sistem.

---

## 10. Status Dokumen

| Informasi | Nilai |
|-----------|-------|
| Versi | 0.1.0 |
| Status | Draft |
| Tahap | Requirement Analysis |
