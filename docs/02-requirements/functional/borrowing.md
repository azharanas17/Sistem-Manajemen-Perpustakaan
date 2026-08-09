---
title: Borrowing Management
module: Functional Requirements
code: FR-BOR
version: 0.1.0
status: Draft
---

# Borrowing Management

# 1. Tujuan

Modul Borrowing Management bertanggung jawab untuk mengelola seluruh proses peminjaman buku di perpustakaan, mulai dari pengajuan peminjaman oleh anggota, proses persetujuan oleh Administrator, pengambilan buku, hingga pengembalian buku.

Modul ini memastikan seluruh proses peminjaman tercatat dengan baik sehingga status setiap Eksemplar Buku dapat dipantau secara akurat.

---

# 2. Istilah yang Digunakan

### Pengajuan Peminjaman

Permintaan peminjaman yang dibuat oleh anggota melalui website dan masih menunggu keputusan Administrator.

---

### Transaksi Peminjaman

Data peminjaman yang telah disetujui Administrator dan menjadi dasar proses pengambilan maupun pengembalian buku.

---

### Jatuh Tempo

Tanggal terakhir anggota harus mengembalikan Eksemplar Buku sesuai kebijakan perpustakaan.

---

### Eksemplar Buku

Salinan fisik dari suatu Judul Buku yang dapat dipinjam oleh anggota perpustakaan.

---

# 3. Aktor

| Aktor | Deskripsi |
|--------|-----------|
| Administrator | Menyetujui atau menolak pengajuan peminjaman, menyerahkan buku, menerima pengembalian, serta mengelola transaksi peminjaman. |
| Mahasiswa | Mengajukan peminjaman, membatalkan pengajuan sebelum diproses, melihat status peminjaman, dan melihat riwayat peminjaman. |
| Dosen | Mengajukan peminjaman, membatalkan pengajuan sebelum diproses, melihat status peminjaman, dan melihat riwayat peminjaman. |

---

# 4. Tujuan Bisnis

Implementasi modul ini bertujuan untuk:

- Mendigitalisasi proses peminjaman buku.
- Mempermudah anggota mengajukan peminjaman tanpa harus datang terlebih dahulu ke perpustakaan.
- Membantu Administrator mengelola transaksi peminjaman.
- Menjaga ketersediaan setiap Eksemplar Buku secara akurat.
- Menyediakan riwayat peminjaman sebagai arsip layanan perpustakaan.

---

# 5. Ruang Lingkup

Modul ini mencakup proses berikut.

- Pengajuan peminjaman buku.
- Persetujuan atau penolakan setiap pengajuan.
- Pembatalan pengajuan oleh anggota.
- Pengambilan buku di perpustakaan.
- Pengembalian buku.
- Melihat status peminjaman.
- Melihat riwayat peminjaman.

---

# 6. Functional Requirements

## FR-BOR-001 — Pengajuan Peminjaman Buku

### Tujuan

Anggota dapat mengajukan peminjaman satu atau lebih Eksemplar Buku melalui website.

### Deskripsi

Sistem menyediakan fasilitas pengajuan peminjaman yang dapat dilakukan tanpa harus datang langsung ke perpustakaan.

Setiap Eksemplar Buku dalam pengajuan akan diproses secara independen oleh Administrator.

### Aktor

- Mahasiswa
- Dosen

### Acceptance Criteria

- Hanya anggota aktif yang dapat mengajukan peminjaman.
- Hanya Eksemplar Buku berstatus **Tersedia** yang dapat dipilih.
- Pengajuan berhasil disimpan.
- Status awal pengajuan adalah **Menunggu Persetujuan**.

---

## FR-BOR-002 — Persetujuan Pengajuan

### Tujuan

Administrator dapat menyetujui atau menolak setiap Eksemplar Buku dalam satu pengajuan.

### Deskripsi

Administrator dapat memberikan keputusan berbeda untuk setiap Eksemplar Buku yang diajukan.

### Acceptance Criteria

- Persetujuan dilakukan per Eksemplar Buku.
- Penolakan dilakukan per Eksemplar Buku.
- Status pengajuan diperbarui sesuai keputusan Administrator.

---

## FR-BOR-003 — Pembatalan Pengajuan

### Tujuan

Anggota dapat membatalkan pengajuan selama belum diproses Administrator.

### Acceptance Criteria

- Hanya pengajuan yang masih menunggu persetujuan yang dapat dibatalkan.
- Pengajuan yang telah diproses tidak dapat dibatalkan oleh anggota.

---

## FR-BOR-004 — Pengambilan Buku

### Tujuan

Administrator mencatat bahwa anggota telah mengambil buku di perpustakaan.

### Acceptance Criteria

- Pengambilan hanya dapat dilakukan setelah pengajuan disetujui.
- Status transaksi diperbarui setelah buku diserahkan.

---

## FR-BOR-005 — Pengembalian Buku

### Tujuan

Administrator mencatat pengembalian buku secara langsung ketika anggota menyerahkan buku ke perpustakaan.

### Acceptance Criteria

- Pengembalian hanya dapat dicatat oleh Administrator.
- Status Eksemplar Buku kembali menjadi **Tersedia** setelah pengembalian selesai.

---

## FR-BOR-006 — Riwayat Peminjaman

### Tujuan

Anggota dapat melihat seluruh riwayat peminjaman yang pernah dilakukan.

### Acceptance Criteria

- Riwayat menampilkan status setiap transaksi.
- Riwayat dapat diurutkan berdasarkan tanggal terbaru.

---

# 7. Informasi Transaksi Peminjaman

## Informasi Pengajuan Peminjaman

Setiap pengajuan peminjaman harus memiliki informasi berikut.

| Informasi | Wajib | Keterangan |
|-----------|:-----:|-----------|
| Nomor Pengajuan | ✅ | Nomor unik sebagai identitas pengajuan. |
| Tanggal Pengajuan | ✅ | Tanggal anggota mengajukan peminjaman. |
| Anggota | ✅ | Mahasiswa atau Dosen yang mengajukan. |
| Status Pengajuan | ✅ | Menunjukkan status keseluruhan pengajuan. |
| Catatan Administrator | ❌ | Digunakan apabila Administrator ingin memberikan informasi tambahan kepada anggota. |

---

## Informasi Detail Pengajuan

Karena satu pengajuan dapat terdiri dari beberapa Eksemplar Buku, maka setiap detail pengajuan memiliki informasi berikut.

| Informasi | Wajib | Keterangan |
|-----------|:-----:|-----------|
| Eksemplar Buku | ✅ | Buku yang diajukan untuk dipinjam. |
| Status Persetujuan | ✅ | Status keputusan untuk eksemplar tersebut. |
| Tanggal Persetujuan | ❌ | Diisi setelah Administrator memberikan keputusan. |
| Tanggal Pengambilan | ❌ | Diisi setelah buku diambil oleh anggota. |
| Tanggal Jatuh Tempo | ❌ | Diisi ketika buku diserahkan kepada anggota. |
| Tanggal Pengembalian | ❌ | Diisi ketika Administrator menerima buku kembali. |

---

# 8. Business Rules

## BR-BOR-001 — Pengajuan Peminjaman

Satu Pengajuan Peminjaman dapat terdiri dari satu atau lebih Eksemplar Buku.

---

## BR-BOR-002 — Persetujuan Per Eksemplar

Administrator memberikan keputusan untuk setiap Eksemplar Buku secara terpisah.

Dalam satu pengajuan, sebagian Eksemplar Buku dapat disetujui dan sebagian lainnya dapat ditolak.

---

## BR-BOR-003 — Status Awal

Setiap Pengajuan Peminjaman memiliki status awal **Menunggu Persetujuan**.

---

## BR-BOR-004 — Pembatalan Pengajuan

Anggota hanya dapat membatalkan pengajuan yang masih berstatus **Menunggu Persetujuan**.

---

## BR-BOR-005 — Pengambilan Buku

Eksemplar Buku dianggap mulai dipinjam setelah Administrator mencatat bahwa buku telah diserahkan kepada anggota.

---

## BR-BOR-006 — Pengembalian Buku

Pengembalian hanya dapat dicatat oleh Administrator setelah buku diterima secara fisik.

---

## BR-BOR-007 — Status Eksemplar Buku

Status Eksemplar Buku harus berubah mengikuti proses peminjaman.

Contoh perubahan status:

- Tersedia → Dipinjam
- Dipinjam → Tersedia

---

## BR-BOR-008 — Batas Maksimal Peminjaman

Jumlah maksimum Eksemplar Buku yang dapat dipinjam oleh seorang anggota ditentukan oleh kebijakan perpustakaan.

Nilai batas maksimum tersebut harus dapat diubah oleh Administrator tanpa mengubah aplikasi.

---

## BR-BOR-009 — Riwayat Peminjaman

Setiap transaksi peminjaman dan pengembalian harus tercatat sebagai riwayat dan tidak boleh dihapus.

---

## BR-BOR-010 — Perpanjangan Peminjaman

Fitur perpanjangan masa pinjam tidak termasuk dalam ruang lingkup MVP.

Apabila anggota ingin meminjam kembali buku yang sama setelah dikembalikan, maka proses dilakukan melalui pengajuan peminjaman baru.

---

# 9. Status Peminjaman

Modul peminjaman menggunakan dua tingkat status, yaitu **Status Pengajuan** dan **Status Detail Peminjaman**.

Pemisahan ini diperlukan karena satu Pengajuan Peminjaman dapat berisi beberapa Eksemplar Buku yang dapat memperoleh keputusan berbeda dari Administrator.

## 9.1 Status Pengajuan

| Status | Deskripsi |
|--------|-----------|
| Menunggu Persetujuan | Pengajuan baru dibuat dan belum seluruhnya diproses oleh Administrator. |
| Diproses | Administrator telah memberikan keputusan terhadap sebagian atau seluruh detail pengajuan. |
| Siap Diambil | Terdapat satu atau lebih Eksemplar Buku yang telah disetujui dan dapat diambil oleh anggota. |
| Selesai | Seluruh Eksemplar Buku yang disetujui telah dikembalikan. |
| Dibatalkan | Pengajuan dibatalkan oleh anggota sebelum diproses Administrator. |

### Aturan Status Pengajuan

Status pengajuan merupakan status agregat dari seluruh detail peminjaman di dalamnya.

Contoh:

```text
Pengajuan #PMJ-2026-001

Clean Code
→ Disetujui
→ Sudah Diambil
→ Sudah Dikembalikan

Atomic Habits
→ Ditolak

Status Pengajuan
→ Selesai
```

Apabila terdapat detail yang masih menunggu keputusan Administrator, pengajuan tidak dapat dinyatakan selesai.

---

## 9.2 Status Detail Peminjaman

Setiap Eksemplar Buku dalam sebuah pengajuan memiliki statusnya sendiri.

| Status | Deskripsi |
|--------|-----------|
| Menunggu Persetujuan | Eksemplar Buku sedang menunggu keputusan Administrator. |
| Disetujui | Administrator menyetujui peminjaman, tetapi buku belum diambil. |
| Ditolak | Administrator menolak peminjaman Eksemplar Buku tersebut. |
| Sudah Diambil | Buku telah diserahkan kepada anggota dan sedang dipinjam. |
| Sudah Dikembalikan | Buku telah diterima kembali oleh Administrator. |
| Dibatalkan | Detail peminjaman dibatalkan oleh anggota sebelum diproses. |

---

## 9.3 Contoh Status Bertingkat

Satu pengajuan dapat memiliki kondisi berikut:

```text
Pengajuan #PMJ-2026-001
Status: Diproses

├── Clean Code
│   └── Sudah Diambil
│
├── Atomic Habits
│   └── Ditolak
│
└── Design Patterns
    └── Menunggu Persetujuan
```

Dalam kondisi tersebut, status setiap Eksemplar Buku tetap independen, sedangkan status Pengajuan Peminjaman menggambarkan kondisi keseluruhan pengajuan.

---

# 10. Aturan Batas Peminjaman

Jumlah Eksemplar Buku yang dapat diajukan atau dipinjam oleh seorang anggota dibatasi berdasarkan kebijakan perpustakaan.

Nilai batas tersebut harus dapat dikonfigurasi oleh Administrator.

## BR-BOR-011 — Batas Pengajuan

Sistem harus mencegah anggota mengajukan jumlah Eksemplar Buku melebihi batas yang ditentukan oleh kebijakan perpustakaan.

---

## BR-BOR-012 — Perhitungan Batas Peminjaman

Dalam menentukan apakah anggota masih dapat mengajukan peminjaman, sistem harus mempertimbangkan jumlah Eksemplar Buku yang masih berada dalam proses peminjaman atau masih menjadi tanggungan anggota sesuai kebijakan perpustakaan.

---

## BR-BOR-013 — Pengajuan Ditolak

Eksemplar Buku yang ditolak oleh Administrator tidak dihitung sebagai buku yang sedang dipinjam oleh anggota.

---

## BR-BOR-014 — Pengajuan Dibatalkan

Eksemplar Buku yang dibatalkan oleh anggota tidak dihitung sebagai buku yang sedang dipinjam.

---

# 11. Alur Perubahan Status

## 11.1 Alur Status Detail Peminjaman

Status setiap Eksemplar Buku mengikuti alur berikut:

```text
Menunggu Persetujuan
        │
        ├───────────────┐
        │               │
        ▼               ▼
   Disetujui          Ditolak
        │
        ▼
   Sudah Diambil
        │
        ▼
Sudah Dikembalikan
```

Selain alur utama tersebut, anggota dapat membatalkan detail peminjaman selama Administrator belum memberikan keputusan:

```text
Menunggu Persetujuan
        │
        ▼
    Dibatalkan
```

### Aturan Transisi

| Status Saat Ini | Status Berikutnya | Pemicu | Aktor |
|-----------------|-------------------|--------|-------|
| Menunggu Persetujuan | Disetujui | Administrator menyetujui peminjaman | Administrator |
| Menunggu Persetujuan | Ditolak | Administrator menolak peminjaman | Administrator |
| Menunggu Persetujuan | Dibatalkan | Anggota membatalkan pengajuan | Anggota |
| Disetujui | Sudah Diambil | Buku diserahkan kepada anggota | Administrator |
| Sudah Diambil | Sudah Dikembalikan | Buku diterima kembali oleh Administrator | Administrator |

Transisi status yang tidak tercantum dalam tabel di atas tidak diperbolehkan.

---

## 11.2 Alur Status Pengajuan

Status Pengajuan merupakan status agregat dari seluruh Detail Peminjaman di dalam pengajuan.

Secara umum alurnya adalah:

```text
Menunggu Persetujuan
        │
        ▼
     Diproses
        │
        ▼
   Siap Diambil
        │
        ▼
     Selesai
```

Pengajuan juga dapat berakhir sebagai:

```text
Menunggu Persetujuan
        │
        ▼
    Dibatalkan
```

### Aturan Status Agregat

| Kondisi Detail | Status Pengajuan |
|----------------|------------------|
| Seluruh detail masih menunggu keputusan | Menunggu Persetujuan |
| Administrator telah memberikan keputusan terhadap sebagian atau seluruh detail | Diproses |
| Terdapat detail yang disetujui dan belum diambil | Siap Diambil |
| Seluruh detail yang disetujui telah dikembalikan dan tidak ada detail yang masih menunggu keputusan | Selesai |
| Seluruh detail dibatalkan sebelum diproses | Dibatalkan |

Detail yang berstatus **Ditolak** atau **Dibatalkan** tidak dianggap sebagai buku yang sedang dipinjam.

---

# 12. Aturan Pengambilan Buku

## BR-BOR-015 — Pengambilan Fisik

Pengambilan buku dilakukan secara fisik di perpustakaan.

Website digunakan untuk mencatat bahwa Eksemplar Buku telah diserahkan kepada anggota.

---

## BR-BOR-016 — Pengambilan Setelah Persetujuan

Eksemplar Buku hanya dapat diserahkan kepada anggota setelah Administrator menyetujui peminjaman terhadap Eksemplar Buku tersebut.

---

## BR-BOR-017 — Perubahan Status Setelah Pengambilan

Status Detail Peminjaman berubah menjadi **Sudah Diambil** setelah Administrator mencatat bahwa Eksemplar Buku telah diserahkan kepada anggota.

Pada saat yang sama, status Eksemplar Buku berubah menjadi **Dipinjam**.

---

# 13. Aturan Pengembalian Buku

## BR-BOR-018 — Pengembalian Fisik

Pengembalian buku dilakukan secara langsung di perpustakaan.

Anggota tidak perlu membuat pengajuan pengembalian melalui website.

---

## BR-BOR-019 — Pencatatan Pengembalian

Administrator mencatat pengembalian setelah menerima Eksemplar Buku secara fisik.

---

## BR-BOR-020 — Perubahan Status Setelah Pengembalian

Setelah pengembalian dicatat:

- Status Detail Peminjaman berubah menjadi **Sudah Dikembalikan**.
- Status Eksemplar Buku berubah menjadi **Tersedia**, apabila kondisi buku masih layak dipinjam.

Apabila buku mengalami kerusakan atau dinyatakan hilang, Administrator dapat menetapkan status Eksemplar Buku sesuai kondisi aktualnya.

---

# 14. Batas Pengajuan Peminjaman

## BR-BOR-021 — Batas Harian

Sistem harus membatasi jumlah Eksemplar Buku yang dapat diajukan oleh seorang anggota dalam satu hari berdasarkan kebijakan perpustakaan.

---

## BR-BOR-022 — Perhitungan Batas

Eksemplar Buku yang telah diajukan pada hari yang sama diperhitungkan dalam batas pengajuan sesuai kebijakan perpustakaan.

Detail yang telah ditolak atau dibatalkan tidak dihitung sebagai peminjaman aktif.

---

## BR-BOR-023 — Konfigurasi Batas

Nilai batas jumlah pengajuan harian harus dapat ditentukan dan diubah oleh Administrator tanpa mengubah proses bisnis utama sistem.

---

# 15. Fitur di Luar MVP

## Perpanjangan Peminjaman

Fitur perpanjangan masa peminjaman tidak termasuk dalam ruang lingkup MVP.

Apabila anggota ingin menggunakan kembali Eksemplar Buku yang sama setelah buku dikembalikan, anggota harus melakukan pengajuan peminjaman baru sesuai prosedur yang berlaku.

---

# 16. Open Questions

Bagian ini berisi keputusan bisnis yang masih memerlukan konfirmasi dari pihak perpustakaan sebelum modul Borrowing dapat dinyatakan final.

| ID | Pertanyaan | Status |
|----|------------|:------:|
| OQ-BOR-001 | Berapa jumlah maksimal Eksemplar Buku yang dapat diajukan oleh seorang anggota dalam satu hari? | ⏳ |
| OQ-BOR-002 | Berapa lama masa peminjaman untuk setiap Eksemplar Buku? | ⏳ |
| OQ-BOR-003 | Apakah terdapat denda atau konsekuensi apabila buku terlambat dikembalikan? | ⏳ |
| OQ-BOR-004 | Apakah anggota yang masih memiliki buku terlambat dapat mengajukan peminjaman baru? | ⏳ |
| OQ-BOR-005 | Apakah Administrator wajib memberikan alasan ketika menolak pengajuan peminjaman? | ⏳ |
| OQ-BOR-006 | Apakah terdapat perbedaan kebijakan peminjaman antara Mahasiswa dan Dosen? | ⏳ |

> **Catatan:** Open Question tidak boleh dianggap sebagai requirement final sebelum mendapatkan konfirmasi dari pihak perpustakaan.

---

# 17. Definition of Done

Dokumen Borrowing Management dapat dinyatakan **Approved** apabila:

| No | Kriteria | Status |
|----|----------|:------:|
| 1 | Tujuan modul telah didefinisikan | ☑ |
| 2 | Aktor telah diidentifikasi | ☑ |
| 3 | Ruang lingkup telah ditentukan | ☑ |
| 4 | Functional Requirement telah ditulis | ☑ |
| 5 | Informasi transaksi telah didefinisikan | ☑ |
| 6 | Business Rule telah ditulis | ☑ |
| 7 | Status Pengajuan telah didefinisikan | ☑ |
| 8 | Status Detail Peminjaman telah didefinisikan | ☑ |
| 9 | Status transition telah didefinisikan | ☑ |
| 10 | Proses pengambilan telah didefinisikan | ☑ |
| 11 | Proses pengembalian telah didefinisikan | ☑ |
| 12 | Batas pengajuan harian telah didefinisikan sebagai kebijakan yang dapat dikonfigurasi | ☑ |
| 13 | Fitur perpanjangan telah ditetapkan di luar MVP | ☑ |
| 14 | Seluruh Open Question telah dikonfirmasi oleh client | ☐ |
| 15 | Tidak terdapat asumsi teknis yang tercampur dalam requirement | ☑ |
| 16 | Dokumen siap digunakan sebagai dasar desain dan pengembangan | ☐ |
