---
title: Library Management System (LMS)
subtitle: Ringkasan Sistem
version: 0.1.0
status: Draft
date: 2026-08-10
---

# 📚 Library Management System (LMS)
## Ringkasan Sistem

## 1. Tujuan Dokumen Ini

Dokumen ini dibuat untuk menyamakan persepsi antara **pihak perpustakaan** dan **tim pengembang** tentang sistem yang akan dibangun. Bacalah dengan santai — tidak ada istilah teknis di sini. Jika ada bagian yang tidak sesuai atau masih membingungkan, mohon ditandai supaya bisa kita bahas bersama.

## 2. Sistem Apa yang Akan Dibangun?

Sistem Informasi Perpustakaan berbasis **website** yang digunakan oleh sivitas akademika untuk mengakses layanan perpustakaan secara daring, yaitu:

- Mencari dan melihat koleksi buku beserta lokasi serta ketersediaannya.
- Mengajukan peminjaman buku tanpa harus datang langsung ke perpustakaan.
- Melihat status dan riwayat peminjaman.
- Membaca informasi dan pengumuman perpustakaan.
- Mengakses repository karya ilmiah (skripsi, tesis, disertasi, dan sejenisnya).

Di sisi lain, sistem memudahkan **pustakawan** dalam mengelola anggota, koleksi buku, proses peminjaman, repository, dan pengumuman — semuanya terpusat di satu tempat.

## 3. Siapa Saja Penggunanya?

| Pengguna | Peran dalam Sistem |
|----------|--------------------|
| **Mahasiswa** | Mendaftar sebagai anggota, mencari buku, meminjam buku, mengakses repository, melihat pengumuman. |
| **Dosen** | Sama seperti mahasiswa: meminjam buku dan mengakses repository sesuai kebijakan perpustakaan. |
| **Pustakawan (Administrator)** | Menyetujui keanggotaan, mengelola data buku, memproses peminjaman, mengelola repository dan pengumuman. |

## 4. Fitur Utama Sistem

| Modul | Fungsinya secara Singkat |
|-------|---------------------------|
| **Keanggotaan** | Pendaftaran anggota baru melalui website, disetujui oleh pustakawan, lalu dapat login dan mengelola profil. |
| **Katalog Buku** | Daftar koleksi buku yang bisa dicari (judul, penulis, penerbit, tahun) dan difilter berdasarkan kategori. |
| **Manajemen Buku** | Pustakawan mengelola data judul buku, eksemplar, penulis, penerbit, kategori, dan lokasi rak. |
| **Peminjaman** | Anggota mengajukan peminjaman daring; pustakawan menyetujui/menolak; pengambilan dan pengembalian dicatat di perpustakaan. |
| **Repository** | Daftar karya ilmiah beserta abstraknya; sebagian dokumen bisa diakses setelah pustakawan menyetujui permintaan. |
| **Pengumuman** | Pustakawan membuat dan mempublikasikan informasi resmi perpustakaan. |
| **Dashboard** | Ringkasan informasi yang disesuaikan dengan peran masing-masing pengguna. |
| **Pelaporan** | Laporan operasional untuk membantu pustakawan memantau kegiatan perpustakaan. |

## 5. Alur Penting yang Perlu Dipahami

**Menjadi anggota:** Mendaftar lewat website → menunggu persetujuan pustakawan → aktif dan bisa login.

**Meminjam buku:** Cari buku di katalog → ajukan peminjaman → pustakawan menyetujui → ambil buku secara fisik di perpustakaan → kembalikan buku secara fisik (pengembalian tidak melalui website).

**Mengakses repository:** Cari karya ilmiah → lihat metadata & abstrak → ajukan akses dokumen → pustakawan menyetujui → dokumen dapat diunduh.

## 6. Ruang Lingkup Tahap Pertama (MVP)

- Registrasi anggota secara daring, persetujuan oleh pustakawan, dan import data anggota lewat Excel.
- Katalog buku dengan pencarian dan filter kategori.
- Peminjaman buku yang diajukan daring, diproses per buku oleh pustakawan.
- Repository karya ilmiah dengan metadata dan abstrak, serta pengajuan akses dokumen.
- Pengumuman perpustakaan.
- Dashboard dan pelaporan dasar.

## 7. Yang TIDAK Termasuk pada Tahap Pertama

Hal-hal berikut sengaja ditunda agar sistem tahap pertama fokus dan selesai tepat waktu:

- Kode QR pada buku.
- Perpanjangan masa peminjaman.
- Pengajuan pengembalian buku melalui website.
- Upload dokumen repository secara mandiri oleh mahasiswa/dosen.
- Integrasi dengan sistem akademik / single sign-on (SSO) universitas.

Fitur-fitur di atas dapat dibahas sebagai **pengembangan tahap berikutnya**.

## 8. Keputusan yang Perlu Disepakati

Agar pengembangan berjalan lancar, kami mohon konfirmasi atas pertanyaan berikut:

**Keanggotaan**
- Apakah keanggotaan memiliki masa berlaku?
- Apakah hak akses mahasiswa dan dosen berbeda?

**Buku & Katalog**
- Format kode eksemplar buku (label fisik) yang diinginkan seperti apa?
- Apakah katalog bisa diakses tanpa login?
- Apakah satu judul buku bisa berada di lebih dari satu lokasi rak?

**Peminjaman**
- Berapa jumlah maksimal buku yang boleh diajukan dalam satu hari?
- Berapa lama masa peminjaman?
- Apakah ada denda/konsekuensi jika telat mengembalikan?
- Apakah pengguna dengan tunggakan boleh meminjam lagi?
- Apakah ada kebijakan pinjam berbeda antara mahasiswa dan dosen?

**Repository**
- Jenis karya ilmiah apa saja yang masuk pada tahap pertama?
- Data (metadata) apa saja yang wajib untuk setiap karya ilmiah?
- Apakah semua dokumen perlu persetujuan akses, atau sebagian terbuka?
- Apakah pengguna boleh mengajukan ulang setelah akses ditolak?
- Format dan ukuran maksimal file yang diizinkan?

**Pengumuman**
- Apakah pengumuman perlu dikelompokkan dalam kategori?
- Apakah pengumuman memiliki tanggal mulai dan berakhir?
- Apakah pengumuman perlu mendukung gambar/lampiran?

> Terima kasih atas waktu dan masukannya. Kami siap mendiskusikan bagian mana pun yang masih belum jelas.
