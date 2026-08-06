---
title: Library Management System
version: 0.1.0
status: Draft
author: Anas
last_updated: 2026-08-06
---

# 📚 Library Management System

> Sistem Informasi Perpustakaan berbasis web untuk mendukung digitalisasi layanan perpustakaan di lingkungan universitas.

## Deskripsi

Library Management System (LMS) adalah aplikasi berbasis web yang dirancang untuk membantu perpustakaan universitas dalam mengelola seluruh layanan perpustakaan secara terintegrasi. Sistem ini mendukung proses administrasi anggota, pengelolaan koleksi buku, peminjaman buku, repository karya ilmiah, layanan tanya pustakawan, pengumuman, dashboard, dan pelaporan.

Pengembangan proyek menggunakan pendekatan **Documentation-Driven Development (DDD)**, yaitu seluruh kebutuhan sistem dianalisis, didokumentasikan, dan disepakati sebelum memasuki tahap implementasi.

## Tujuan

- Mendigitalisasi layanan perpustakaan universitas.
- Mempermudah pengelolaan anggota dan koleksi buku.
- Mendukung proses peminjaman buku secara daring.
- Menyediakan repository karya ilmiah universitas.
- Meningkatkan efisiensi operasional perpustakaan.
- Menyediakan fondasi sistem yang mudah dikembangkan pada masa mendatang.

## Ruang Lingkup MVP

- Manajemen Anggota
- Manajemen Buku
- Peminjaman Buku
- Repository Karya Ilmiah
- Layanan Tanya Pustakawan
- Pengumuman
- Dashboard
- Pelaporan

## Status Pengembangan

| Modul | Status |
|--------|--------|
| Manajemen Anggota | ✅ Requirement Selesai |
| Manajemen Buku | ✅ Requirement Selesai |
| Peminjaman Buku | ✅ Requirement Selesai |
| Repository | 🚧 Sedang Dianalisis |
| Tanya Pustakawan | ⏳ Belum Dimulai |
| Pengumuman | ⏳ Belum Dimulai |
| Dashboard | ⏳ Belum Dimulai |
| Pelaporan | ⏳ Belum Dimulai |

## Rencana Teknologi

| Komponen | Teknologi |
|----------|-----------|
| Backend | Laravel |
| Admin Panel | Filament |
| Database | MySQL |
| Frontend | Blade + Livewire *(dapat berubah sesuai kebutuhan)* |
| Penyimpanan Berkas | Laravel Storage |
| Deployment | Docker + VPS |

## Struktur Dokumentasi

```text
docs/
├── 01-project/
├── 02-requirements/
├── 03-analysis/
├── 04-design/
└── 05-planning/
```

## Pendekatan Pengembangan

Proyek ini menggunakan pendekatan **Documentation-Driven Development (DDD)**.

```text
Requirement
    ↓
Documentation
    ↓
Design
    ↓
Development
    ↓
Testing
    ↓
Deployment
```

Seluruh implementasi harus mengacu pada requirement yang telah disepakati.

## Maintainer

Anas
