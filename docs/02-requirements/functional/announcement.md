# Announcement Management

# 1. Tujuan

Modul Announcement Management bertanggung jawab untuk mengelola dan menyampaikan informasi resmi perpustakaan kepada pengguna sistem.

Modul ini memungkinkan Administrator membuat dan mempublikasikan pengumuman yang dapat dibaca oleh Mahasiswa dan Dosen melalui website.

---

# 2. Istilah yang Digunakan

## Pengumuman

Pengumuman adalah informasi resmi yang diterbitkan oleh Administrator untuk disampaikan kepada pengguna perpustakaan.

Contoh:

* Informasi perubahan jam layanan.
* Informasi penutupan perpustakaan.
* Informasi kegiatan perpustakaan.
* Informasi layanan baru.
* Pengumuman akademik yang berkaitan dengan layanan perpustakaan.

---

## Status Pengumuman

Status Pengumuman menunjukkan kondisi publikasi suatu pengumuman.

Status yang digunakan:

* Draft
* Published
* Archived

---

# 3. Aktor

| Aktor         | Deskripsi                                                        |
| ------------- | ---------------------------------------------------------------- |
| Administrator | Membuat, mengubah, mempublikasikan, dan mengarsipkan pengumuman. |
| Mahasiswa     | Melihat pengumuman yang telah dipublikasikan.                    |
| Dosen         | Melihat pengumuman yang telah dipublikasikan.                    |

---

# 4. Tujuan Bisnis

Implementasi modul ini bertujuan untuk:

* Menyediakan media informasi resmi perpustakaan.
* Memudahkan Administrator menyampaikan informasi kepada pengguna.
* Mengurangi ketergantungan terhadap penyampaian informasi secara manual.
* Menyediakan arsip informasi yang dapat diakses kembali oleh pengguna.

---

# 5. Ruang Lingkup

Modul Announcement Management mencakup:

* Membuat pengumuman.
* Mengubah pengumuman.
* Menghapus pengumuman.
* Menyimpan pengumuman sebagai Draft.
* Mempublikasikan pengumuman.
* Mengarsipkan pengumuman.
* Melihat daftar pengumuman.
* Melihat detail pengumuman.
* Menampilkan pengumuman terbaru.

---

# 6. Functional Requirements

## FR-ANN-001 — Membuat Pengumuman

### Tujuan

Administrator dapat membuat pengumuman baru.

### Aktor

* Administrator

### Acceptance Criteria

* Administrator dapat membuat pengumuman.
* Pengumuman dapat disimpan sebagai Draft.
* Pengumuman memiliki judul dan isi.
* Sistem mencatat waktu pembuatan pengumuman.

---

## FR-ANN-002 — Mengubah Pengumuman

### Tujuan

Administrator dapat mengubah pengumuman yang telah dibuat.

### Acceptance Criteria

* Administrator dapat mengubah judul.
* Administrator dapat mengubah isi.
* Administrator dapat mengubah informasi pendukung pengumuman.
* Perubahan tersimpan di sistem.

---

## FR-ANN-003 — Mempublikasikan Pengumuman

### Tujuan

Administrator dapat membuat pengumuman tersedia untuk pengguna.

### Acceptance Criteria

* Administrator dapat mengubah status Draft menjadi Published.
* Pengumuman dengan status Published dapat dilihat oleh pengguna.
* Pengumuman yang belum dipublikasikan tidak muncul pada daftar pengumuman publik.

---

## FR-ANN-004 — Mengarsipkan Pengumuman

### Tujuan

Administrator dapat mengarsipkan pengumuman yang sudah tidak relevan sebagai informasi aktif.

### Acceptance Criteria

* Administrator dapat mengubah status Published menjadi Archived.
* Pengumuman Archived tidak ditampilkan sebagai pengumuman aktif.
* Data pengumuman tetap tersimpan di sistem.

---

## FR-ANN-005 — Menghapus Pengumuman

### Tujuan

Administrator dapat menghapus pengumuman apabila diperlukan.

### Acceptance Criteria

* Administrator dapat menghapus pengumuman.
* Penghapusan dilakukan oleh Administrator.
* Pengumuman yang telah dihapus tidak dapat ditampilkan kepada pengguna.

---

## FR-ANN-006 — Melihat Daftar Pengumuman

### Tujuan

Pengguna dapat melihat pengumuman yang telah dipublikasikan.

### Aktor

* Mahasiswa
* Dosen

### Acceptance Criteria

* Pengguna dapat melihat daftar pengumuman Published.
* Pengumuman terbaru ditampilkan terlebih dahulu.
* Pengumuman Archived tidak ditampilkan sebagai pengumuman aktif.

---

## FR-ANN-007 — Melihat Detail Pengumuman

### Tujuan

Pengguna dapat membaca isi lengkap sebuah pengumuman.

### Acceptance Criteria

Halaman detail menampilkan:

* Judul
* Isi pengumuman
* Tanggal publikasi
* Informasi pendukung apabila tersedia

---

# 7. Informasi Pengumuman

Setiap Pengumuman harus mampu menyimpan informasi berikut.

| Informasi          | Wajib | Keterangan                                |
| ------------------ | :---: | ----------------------------------------- |
| Judul              |   ✅   | Judul pengumuman.                         |
| Isi                |   ✅   | Isi lengkap pengumuman.                   |
| Status             |   ✅   | Draft, Published, atau Archived.          |
| Tanggal Publikasi  |   ❌   | Tanggal ketika pengumuman dipublikasikan. |
| Gambar             |   ❌   | Gambar pendukung apabila diperlukan.      |
| Lampiran           |   ❌   | File pendukung apabila diperlukan.        |
| Tanggal Dibuat     |   ✅   | Waktu pengumuman dibuat.                  |
| Tanggal Diperbarui |   ✅   | Waktu terakhir pengumuman diperbarui.     |

---

# 8. Business Rules

## BR-ANN-001 — Pengelolaan Pengumuman

Pengumuman hanya dapat dikelola oleh Administrator.

---

## BR-ANN-002 — Status Draft

Pengumuman dengan status Draft hanya dapat dilihat dan dikelola oleh Administrator.

Pengumuman Draft tidak ditampilkan kepada pengguna umum.

---

## BR-ANN-003 — Status Published

Pengumuman dengan status Published dapat dilihat oleh Mahasiswa dan Dosen.

---

## BR-ANN-004 — Status Archived

Pengumuman dengan status Archived tidak ditampilkan sebagai pengumuman aktif.

Data pengumuman tetap disimpan sebagai arsip.

---

## BR-ANN-005 — Tanggal Publikasi

Tanggal publikasi dicatat ketika pengumuman dipublikasikan.

---

## BR-ANN-006 — Urutan Pengumuman

Daftar pengumuman aktif ditampilkan berdasarkan tanggal publikasi terbaru.

---

## BR-ANN-007 — Isi Pengumuman

Pengumuman harus memiliki judul dan isi sebelum dapat dipublikasikan.

---

# 9. Status Pengumuman

| Status    | Deskripsi                                             | Terlihat Pengguna |
| --------- | ----------------------------------------------------- | :---------------: |
| Draft     | Pengumuman sedang disiapkan dan belum dipublikasikan. |         ❌         |
| Published | Pengumuman telah dipublikasikan dan aktif.            |         ✅         |
| Archived  | Pengumuman telah diarsipkan dan tidak lagi aktif.     |         ❌         |

---

# 10. Alur Pengelolaan Pengumuman

Alur utama pengelolaan pengumuman:

```text
Draft
  │
  ▼
Published
  │
  ▼
Archived
```

Administrator dapat membuat pengumuman baru dalam status Draft.

Setelah informasi dianggap siap, Administrator dapat mempublikasikan pengumuman.

Setelah tidak lagi relevan sebagai informasi aktif, Administrator dapat mengarsipkan pengumuman.

---

# 11. Definition of Done

Dokumen Announcement Management dapat dinyatakan **Approved** apabila:

| No | Kriteria                                                     | Status |
| -- | ------------------------------------------------------------ | :----: |
| 1  | Tujuan modul telah didefinisikan                             |    ☑   |
| 2  | Istilah bisnis telah didefinisikan                           |    ☑   |
| 3  | Aktor telah diidentifikasi                                   |    ☑   |
| 4  | Ruang lingkup telah ditentukan                               |    ☑   |
| 5  | Functional Requirement telah ditulis                         |    ☑   |
| 6  | Informasi Pengumuman telah didefinisikan                     |    ☑   |
| 7  | Business Rule telah ditulis                                  |    ☑   |
| 8  | Status Pengumuman telah didefinisikan                        |    ☑   |
| 9  | Alur pengelolaan telah didefinisikan                         |    ☑   |
| 10 | Tidak terdapat detail implementasi teknis                    |    ☑   |
| 11 | Seluruh Open Question telah dikonfirmasi oleh client         |    ☐   |
| 12 | Dokumen siap digunakan sebagai dasar desain dan pengembangan |    ☐   |

---

# 12. Open Questions

Bagian ini berisi keputusan bisnis yang masih memerlukan konfirmasi dari pihak perpustakaan.

| ID         | Pertanyaan                                                                     | Status |
| ---------- | ------------------------------------------------------------------------------ | :----: |
| OQ-ANN-001 | Apakah pengumuman perlu memiliki kategori?                                     |    ⏳   |
| OQ-ANN-002 | Apakah pengumuman perlu memiliki tanggal mulai dan tanggal berakhir publikasi? |    ⏳   |
| OQ-ANN-003 | Apakah pengumuman dapat ditujukan hanya kepada Mahasiswa atau Dosen tertentu?  |    ⏳   |
| OQ-ANN-004 | Apakah gambar diperlukan sebagai bagian dari pengumuman?                       |    ⏳   |
| OQ-ANN-005 | Apakah lampiran file diperlukan dalam MVP?                                     |    ⏳   |

> Open Question tidak dianggap sebagai requirement final sebelum mendapatkan konfirmasi dari pihak perpustakaan.
