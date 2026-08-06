---
title: Book Management
module: Functional Requirements
code: FR-BOOK
version: 0.1.0
status: Draft
---

# Book Management

# 1. Tujuan

Modul Book Management bertanggung jawab untuk mengelola seluruh data koleksi buku yang dimiliki perpustakaan, termasuk data bibliografi, data eksemplar buku, kategori, penulis, penerbit, serta lokasi penyimpanan buku.

Modul ini memastikan seluruh koleksi perpustakaan terdokumentasi dengan baik sehingga dapat digunakan oleh modul lain, seperti Katalog Online dan Peminjaman Buku.

## Istilah yang Digunakan

Untuk menghindari ambiguitas, dokumen ini menggunakan istilah berikut.

### Judul Buku

Judul Buku adalah informasi bibliografi suatu buku, seperti judul, penulis, penerbit, tahun terbit, ISBN, kategori, dan informasi deskriptif lainnya.

Satu Judul Buku dapat memiliki satu atau lebih Eksemplar Buku.

Contoh:

- Clean Code
- Laskar Pelangi
- Atomic Habits

---

### Eksemplar Buku

Eksemplar Buku adalah salinan fisik dari suatu Judul Buku yang tersedia di perpustakaan.

Setiap Eksemplar Buku memiliki identitas unik sehingga status ketersediaannya dapat dikelola secara individual.

Contoh:

| Judul Buku | Kode Eksemplar |
|------------|----------------|
| Clean Code | CC-001 |
| Clean Code | CC-002 |
| Clean Code | CC-003 |

Pada modul peminjaman, objek yang dipinjam oleh anggota perpustakaan adalah **Eksemplar Buku**, bukan **Judul Buku**.

---

# 2. Aktor

| Aktor | Deskripsi |
|--------|-----------|
| Administrator | Mengelola seluruh data koleksi buku, kategori, penulis, penerbit, dan lokasi rak. |
| Mahasiswa | Melihat informasi koleksi buku melalui katalog online. |
| Dosen | Melihat informasi koleksi buku melalui katalog online. |

---

# 3. Tujuan Bisnis

Implementasi modul ini bertujuan untuk:

- Menyediakan data koleksi buku yang akurat.
- Mempermudah pengelolaan koleksi perpustakaan.
- Memudahkan pengguna menemukan buku yang dibutuhkan.
- Menjadi sumber data utama bagi proses peminjaman buku.

---

# 4. Ruang Lingkup

Modul ini mencakup fitur-fitur berikut:

- Pengelolaan data buku.
- Pengelolaan eksemplar buku.
- Pengelolaan kategori buku.
- Pengelolaan penulis.
- Pengelolaan penerbit.
- Pengelolaan lokasi rak.
- Import data buku menggunakan file Microsoft Excel.
- Pencarian buku.
- Filter koleksi buku.
- Melihat detail buku.

---

# 5. Functional Requirements

## FR-BOOK-001 — Kelola Data Buku

### Tujuan

Administrator dapat menambahkan, mengubah, melihat, dan menghapus data bibliografi buku.

### Deskripsi

Sistem menyediakan fasilitas untuk mengelola informasi utama sebuah judul buku.

### Aktor

- Administrator

### Acceptance Criteria

- Administrator dapat menambah data buku.
- Administrator dapat mengubah data buku.
- Administrator dapat melihat detail buku.
- Administrator dapat menghapus data buku apabila tidak memiliki eksemplar.

---

## FR-BOOK-002 — Kelola Eksemplar Buku

### Tujuan

Administrator dapat mengelola setiap eksemplar fisik dari suatu judul buku.

### Deskripsi

Satu judul buku dapat memiliki satu atau lebih eksemplar.

Setiap eksemplar memiliki identitas unik sehingga status ketersediaannya dapat dilacak secara individual.

### Aktor

- Administrator

### Acceptance Criteria

- Sistem mendukung lebih dari satu eksemplar untuk setiap judul buku.
- Setiap eksemplar memiliki identitas yang unik.
- Status setiap eksemplar dapat dikelola secara terpisah.

---

## FR-BOOK-003 — Kelola Penulis

### Deskripsi

Administrator dapat mengelola data penulis buku.

Satu buku dapat memiliki lebih dari satu penulis.

### Aktor

- Administrator

### Acceptance Criteria

- Sistem mendukung relasi banyak penulis pada satu judul buku.
- Data penulis dapat digunakan kembali pada buku lain.

---

## FR-BOOK-004 — Kelola Penerbit

### Deskripsi

Administrator dapat mengelola data penerbit buku.

### Aktor

- Administrator

### Acceptance Criteria

- Data penerbit dapat digunakan kembali oleh banyak buku.

---

## FR-BOOK-005 — Kelola Kategori Buku

### Deskripsi

Administrator dapat mengelola kategori buku yang digunakan sebagai klasifikasi koleksi.

Kategori digunakan sebagai filter pada katalog online.

### Aktor

- Administrator

### Acceptance Criteria

- Administrator dapat menambah, mengubah, dan menghapus kategori.
- Pengguna dapat melakukan filter berdasarkan kategori.

---

## FR-BOOK-006 — Kelola Lokasi Rak

### Deskripsi

Administrator dapat menentukan lokasi penyimpanan setiap eksemplar buku.

Lokasi rak akan ditampilkan kepada pengguna setelah melakukan pencarian buku.

### Acceptance Criteria

- Setiap eksemplar memiliki lokasi penyimpanan.
- Lokasi rak dapat diperbarui apabila buku dipindahkan.

---

## FR-BOOK-007 — Import Data Buku

### Deskripsi

Administrator dapat menambahkan data buku melalui proses impor menggunakan file Microsoft Excel.

### Acceptance Criteria

- Sistem melakukan validasi format file.
- Sistem menampilkan jumlah data yang berhasil dan gagal diimpor.
- Kesalahan pada satu baris data tidak menghentikan proses impor.

---

## FR-BOOK-008 — Pencarian Buku

### Deskripsi

Pengguna dapat mencari koleksi buku melalui katalog online.

Pencarian dilakukan berdasarkan informasi bibliografi buku.

### Aktor

- Mahasiswa
- Dosen

### Acceptance Criteria

Pengguna dapat melakukan pencarian berdasarkan:

- Judul buku
- Penulis
- Penerbit
- Tahun terbit

---

## FR-BOOK-009 — Filter Buku

### Deskripsi

Pengguna dapat memfilter daftar buku berdasarkan kategori.

### Acceptance Criteria

- Filter kategori dapat digunakan bersamaan dengan pencarian.

---

## FR-BOOK-010 — Detail Buku

### Deskripsi

Pengguna dapat melihat informasi lengkap mengenai sebuah buku.

Informasi yang ditampilkan meliputi:

- Judul
- Penulis
- Penerbit
- Tahun terbit
- ISBN (jika tersedia)
- Kategori
- Deskripsi
- Lokasi rak
- Jumlah eksemplar
- Jumlah eksemplar yang tersedia

### Acceptance Criteria

Informasi buku ditampilkan secara lengkap sebelum pengguna melakukan proses peminjaman.

---

# 6. Informasi Buku

Modul Book Management harus mampu mengelola informasi berikut untuk setiap judul buku.

| Informasi | Wajib | Keterangan |
|-----------|:-----:|-----------|
| Judul Buku | ✅ | Nama utama buku. |
| Subjudul | ❌ | Diisi apabila buku memiliki subjudul. |
| Penulis | ✅ | Satu judul buku dapat memiliki lebih dari satu penulis. |
| Penerbit | ✅ | Penerbit yang menerbitkan buku. |
| Tahun Terbit | ✅ | Tahun pertama atau edisi buku diterbitkan. |
| ISBN | ❌ | Nomor ISBN apabila tersedia pada buku. |
| Kategori | ✅ | Digunakan sebagai klasifikasi koleksi dan filter pencarian. |
| Bahasa | ❌ | Bahasa utama buku. |
| Edisi | ❌ | Informasi edisi buku, misalnya Edisi 2 atau Revisi. |
| Deskripsi / Sinopsis | ❌ | Ringkasan isi buku. |
| Sampul Buku | ❌ | Gambar sampul buku yang ditampilkan pada katalog. |

---

## Informasi Eksemplar Buku

Selain data bibliografi, setiap eksemplar buku memiliki informasi berikut.

| Informasi | Wajib | Keterangan |
|-----------|:-----:|-----------|
| Kode Eksemplar | ✅ | Identitas unik untuk setiap eksemplar buku. |
| Lokasi Rak | ✅ | Lokasi fisik penyimpanan buku di perpustakaan. |
| Status Ketersediaan | ✅ | Menunjukkan apakah buku tersedia untuk dipinjam atau tidak. |

> **Catatan:** Satu judul buku dapat memiliki satu atau lebih eksemplar. Seluruh eksemplar berbagi informasi bibliografi yang sama, namun masing-masing memiliki identitas, lokasi, dan status ketersediaan yang dikelola secara terpisah.
>
> ---

# 7. Business Rules

## BR-BOOK-001 — Struktur Koleksi Buku

Satu Judul Buku dapat memiliki satu atau lebih Eksemplar Buku.

---

## BR-BOOK-002 — Objek Peminjaman

Anggota perpustakaan melakukan peminjaman terhadap Eksemplar Buku, bukan terhadap Judul Buku.

---

## BR-BOOK-003 — Kode Eksemplar

Setiap Eksemplar Buku harus memiliki kode yang unik di dalam sistem.

Format kode eksemplar ditentukan oleh kebijakan perpustakaan dan dapat berubah sewaktu-waktu tanpa memengaruhi data Judul Buku.

---

## BR-BOOK-004 — ISBN

ISBN bersifat opsional.

Judul Buku tetap dapat didaftarkan meskipun tidak memiliki ISBN.

---

## BR-BOOK-005 — Penulis

Satu Judul Buku dapat memiliki lebih dari satu Penulis.

Seorang Penulis dapat menulis lebih dari satu Judul Buku.

---

## BR-BOOK-006 — Penerbit

Satu Judul Buku hanya memiliki satu Penerbit.

Seorang Penerbit dapat menerbitkan banyak Judul Buku.

---

## BR-BOOK-007 — Kategori

Kategori buku dikelola sepenuhnya oleh Administrator.

Pengguna menggunakan kategori sebagai filter saat mencari koleksi buku.

---

## BR-BOOK-008 — Lokasi Rak

Setiap Eksemplar Buku harus memiliki lokasi penyimpanan fisik.

Lokasi rak ditampilkan kepada pengguna untuk membantu menemukan buku di perpustakaan.

---

## BR-BOOK-009 — Import Data Buku

Administrator dapat menambahkan data buku melalui proses impor menggunakan file Microsoft Excel.

Sistem harus memvalidasi data sebelum menyimpannya.

---

## BR-BOOK-010 — Penghapusan Judul Buku

Judul Buku hanya dapat dihapus apabila tidak memiliki Eksemplar Buku.

Apabila masih terdapat satu atau lebih Eksemplar Buku yang terdaftar, sistem harus menolak proses penghapusan.

---

## BR-BOOK-011 — Penghapusan Penulis

Data Penulis tidak dapat dihapus apabila masih digunakan oleh satu atau lebih Judul Buku.

---

## BR-BOOK-012 — Penghapusan Penerbit

Data Penerbit tidak dapat dihapus apabila masih digunakan oleh satu atau lebih Judul Buku.

---

## BR-BOOK-013 — Penghapusan Kategori

Kategori tidak dapat dihapus apabila masih digunakan oleh satu atau lebih Judul Buku.

---

# 8. Status Eksemplar Buku

Setiap Eksemplar Buku harus memiliki salah satu status berikut.

| Status | Deskripsi | Dapat Dipinjam |
|--------|-----------|:--------------:|
| Tersedia | Buku berada di perpustakaan dan siap dipinjam. | ✅ |
| Dipinjam | Buku sedang dipinjam oleh anggota perpustakaan. | ❌ |
| Rusak | Buku mengalami kerusakan dan tidak dapat dipinjam sementara. | ❌ |
| Hilang | Buku dinyatakan hilang dan tidak tersedia untuk dipinjam. | ❌ |
| Perawatan | Buku sedang menjalani proses perbaikan, inventarisasi, atau perawatan. | ❌ |

---

## BR-BOOK-014 — Perubahan Status

Status Eksemplar Buku harus diperbarui secara otomatis atau manual sesuai proses bisnis yang terjadi.

Contoh:

- Tersedia → Dipinjam (setelah peminjaman disetujui dan buku diambil)
- Dipinjam → Tersedia (setelah pengembalian diterima Administrator)
- Tersedia → Rusak (ditetapkan oleh Administrator)
- Tersedia → Hilang (ditetapkan oleh Administrator)
- Rusak → Tersedia (setelah buku selesai diperbaiki)
- Perawatan → Tersedia (setelah proses perawatan selesai)

---

## BR-BOOK-015 — Kelayakan Dipinjam

Hanya Eksemplar Buku dengan status **Tersedia** yang dapat diajukan untuk dipinjam.

---

# 9. Definition of Done

Dokumen ini dinyatakan selesai apabila seluruh kriteria berikut telah terpenuhi.

| No | Kriteria | Status |
|----|----------|:------:|
| 1 | Tujuan modul telah didefinisikan | ☑ |
| 2 | Istilah bisnis telah didefinisikan | ☑ |
| 3 | Aktor telah diidentifikasi | ☑ |
| 4 | Ruang lingkup modul telah ditentukan | ☑ |
| 5 | Functional Requirement telah ditulis | ☑ |
| 6 | Informasi bisnis yang dikelola telah didefinisikan | ☑ |
| 7 | Business Rule telah ditulis | ☑ |
| 8 | Status Eksemplar Buku telah didefinisikan | ☑ |
| 9 | Tidak terdapat asumsi teknis (database, API, framework) | ☑ |
| 10 | Siap dilakukan review bersama client | ☑ |

---

# 10. Catatan

Dokumen ini mendefinisikan kebutuhan bisnis untuk modul Book Management.

Dokumen ini tidak membahas desain basis data, implementasi API, struktur kode program, maupun teknologi yang digunakan. Seluruh aspek teknis akan dijelaskan pada dokumen tahap desain dan pengembangan.
