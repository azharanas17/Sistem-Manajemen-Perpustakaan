# System Requirements

## 1. Pendahuluan

Dokumen ini merupakan konsolidasi kebutuhan fungsional untuk sistem informasi perpustakaan universitas.

Dokumen ini digunakan sebagai acuan bersama antara pihak perpustakaan sebagai client/stakeholder dan developer dalam memahami ruang lingkup, fungsi utama, aktor, serta aturan bisnis sistem.

Dokumen ini menjadi referensi utama sebelum proses System Design dan Development dimulai.

Detail masing-masing modul dijelaskan pada dokumen requirement fungsional terkait.

---

# 2. Tujuan Sistem

Sistem informasi perpustakaan bertujuan untuk menyediakan layanan perpustakaan berbasis web yang memungkinkan pengguna:

* Mendaftarkan diri sebagai anggota perpustakaan.
* Mengelola akun pengguna.
* Mencari dan melihat koleksi buku.
* Melihat lokasi dan ketersediaan buku.
* Mengajukan peminjaman buku secara online.
* Melihat status peminjaman.
* Mengakses informasi repository.
* Mengajukan akses terhadap dokumen repository yang dibatasi.
* Membaca pengumuman dan informasi perpustakaan.

Bagi Administrator/Pustakawan, sistem menyediakan fasilitas untuk:

* Mengelola anggota.
* Mengelola koleksi buku.
* Mengelola eksemplar buku.
* Mengelola kategori.
* Memproses pengajuan peminjaman.
* Mencatat pengambilan dan pengembalian buku.
* Mengelola repository.
* Mengelola pengumuman.
* Mengelola data master yang diperlukan sistem.

---

# 3. Aktor Sistem

Sistem memiliki tiga role utama:

| Role          | Deskripsi                                                                                     |
| ------------- | --------------------------------------------------------------------------------------------- |
| Administrator | Pustakawan yang bertanggung jawab mengelola data dan operasional perpustakaan melalui sistem. |
| Mahasiswa     | Pengguna dari kalangan mahasiswa yang menggunakan layanan perpustakaan.                       |
| Dosen         | Pengguna dari kalangan dosen yang menggunakan layanan perpustakaan.                           |

---

# 4. Gambaran Modul

Sistem terdiri dari modul utama berikut:

| Modul                   | Administrator |          Mahasiswa         |            Dosen           |
| ----------------------- | :-----------: | :------------------------: | :------------------------: |
| Member Management       |       ✅       | Registrasi / Kelola profil | Registrasi / Kelola profil |
| Book Management         |       ✅       |              —             |              —             |
| Online Catalog          |       ✅       |              ✅             |              ✅             |
| Borrowing Management    |       ✅       |              ✅             |              ✅             |
| Repository Management   |       ✅       |              ✅             |              ✅             |
| Announcement Management |       ✅       |              ✅             |              ✅             |

---

# 5. Scope MVP

## 5.1 Member Management

MVP mencakup:

* Registrasi anggota secara manual melalui website.
* Persetujuan anggota oleh Administrator.
* Login pengguna.
* Pengelolaan profil.
* Pengelolaan role pengguna.
* Import data anggota melalui Excel oleh Administrator.

Administrator dapat melakukan pengelolaan data anggota secara manual maupun melalui import Excel.

---

## 5.2 Book Management

MVP mencakup:

* Pengelolaan Judul Buku.
* Pengelolaan Eksemplar Buku.
* Pengelolaan Penulis.
* Pengelolaan Penerbit.
* Pengelolaan Kategori.
* Pengelolaan lokasi rak.
* Pengelolaan Tahun Terbit.
* ISBN sebagai field opsional.
* Kode khusus untuk setiap Eksemplar Buku.
* Dukungan satu Judul Buku dengan lebih dari satu Penulis.
* Dukungan satu Judul Buku dengan lebih dari satu Eksemplar Buku.

Kode khusus Eksemplar Buku akan mengikuti format yang ditentukan oleh perpustakaan.

Contoh format:

```text
{JudulBuku}_{TahunTerbit}_{Penerbit}_{sortNumber}
```

Implementasi QR Code belum termasuk dalam MVP.

---

## 5.3 Online Catalog

MVP mencakup:

* Daftar koleksi buku.
* Pencarian berdasarkan:

  * Judul Buku
  * Penulis
  * Penerbit
  * Tahun Terbit
* Filter berdasarkan Kategori.
* Melihat Detail Judul Buku.
* Melihat jumlah Eksemplar Buku.
* Melihat ketersediaan.
* Melihat lokasi rak.
* Melihat ISBN apabila tersedia.
* Mengarahkan pengguna ke proses peminjaman.

Kategori digunakan sebagai filter, bukan sebagai keyword pencarian utama.

Lokasi rak ditampilkan sebagai informasi untuk membantu pengguna menemukan buku secara fisik.

---

## 5.4 Borrowing Management

MVP mencakup:

* Pengajuan peminjaman dilakukan oleh anggota melalui website.
* Setiap Eksemplar Buku dalam suatu pengajuan diproses secara terpisah.
* Administrator dapat menyetujui atau menolak setiap Eksemplar Buku secara individual.
* Anggota dapat membatalkan pengajuan selama belum diproses Administrator.
* Sistem memiliki batas jumlah pengajuan peminjaman per hari.
* Buku yang telah disetujui dapat diambil secara fisik di perpustakaan.
* Administrator mencatat pengambilan buku melalui sistem.
* Pengembalian dilakukan secara fisik di perpustakaan.
* Administrator mencatat pengembalian melalui sistem.
* Tidak terdapat pengajuan pengembalian melalui website.
* Status peminjaman dapat dilihat oleh anggota.
* Sistem mencatat riwayat peminjaman.

Perpanjangan peminjaman tidak termasuk dalam MVP.

Apabila pengguna ingin meminjam kembali buku yang sama setelah dikembalikan, pengguna melakukan pengajuan peminjaman baru.

---

## 5.5 Repository Management

MVP mencakup:

* Pengelolaan metadata repository.
* Pengelolaan abstrak.
* Halaman detail repository.
* Pencarian repository.
* Pengelolaan file repository oleh Administrator.
* Pembatasan akses terhadap file repository.
* Pengajuan akses file oleh Mahasiswa dan Dosen.
* Persetujuan atau penolakan akses oleh Administrator.
* Akses file setelah permintaan disetujui.

Abstrak disimpan langsung di dalam sistem sehingga dapat ditampilkan tanpa pengguna harus mengunduh file lengkap.

Apabila mahasiswa atau dosen memiliki file yang perlu dimasukkan ke repository, file dapat dikirim kepada Administrator melalui email atau komunikasi eksternal.

Administrator kemudian mengunggah file tersebut ke dalam sistem.

Upload langsung oleh Mahasiswa atau Dosen tidak termasuk dalam MVP.

---

## 5.6 Announcement Management

MVP mencakup:

* Membuat pengumuman.
* Mengubah pengumuman.
* Menyimpan Draft.
* Mempublikasikan pengumuman.
* Mengarsipkan pengumuman.
* Menghapus pengumuman.
* Melihat daftar pengumuman.
* Melihat detail pengumuman.

Status utama:

```text
Draft → Published → Archived
```

---

# 6. Role & Permission Overview

## 6.1 Administrator

Administrator memiliki kewenangan untuk:

### Member

* Melihat anggota.
* Menyetujui anggota.
* Menolak anggota.
* Mengubah data anggota.
* Mengelola role.
* Import anggota melalui Excel.

### Book

* Mengelola Judul Buku.
* Mengelola Eksemplar Buku.
* Mengelola Penulis.
* Mengelola Penerbit.
* Mengelola Kategori.
* Mengelola lokasi rak.

### Borrowing

* Melihat pengajuan.
* Menyetujui pengajuan detail.
* Menolak pengajuan detail.
* Mencatat pengambilan.
* Mencatat pengembalian.
* Melihat riwayat peminjaman.

### Repository

* Mengelola metadata.
* Mengelola abstrak.
* Mengunggah file.
* Mengelola status repository.
* Memproses permintaan akses.

### Announcement

* Membuat pengumuman.
* Mengubah pengumuman.
* Mempublikasikan pengumuman.
* Mengarsipkan pengumuman.
* Menghapus pengumuman.

---

## 6.2 Mahasiswa

Mahasiswa dapat:

* Melakukan registrasi.
* Login.
* Mengelola profil.
* Melihat katalog.
* Mencari buku.
* Memfilter buku berdasarkan kategori.
* Melihat detail buku.
* Melihat lokasi rak.
* Melihat ketersediaan buku.
* Mengajukan peminjaman.
* Membatalkan pengajuan yang belum diproses.
* Melihat status peminjaman.
* Melihat riwayat peminjaman.
* Melihat repository.
* Melihat abstrak repository.
* Mengajukan akses file repository.
* Melihat pengumuman.

---

## 6.3 Dosen

Dosen memiliki fungsi pengguna yang secara umum sama dengan Mahasiswa:

* Melakukan registrasi.
* Login.
* Mengelola profil.
* Melihat katalog.
* Mencari buku.
* Memfilter buku berdasarkan kategori.
* Melihat detail buku.
* Melihat lokasi rak.
* Melihat ketersediaan buku.
* Mengajukan peminjaman.
* Membatalkan pengajuan yang belum diproses.
* Melihat status peminjaman.
* Melihat riwayat peminjaman.
* Melihat repository.
* Melihat abstrak repository.
* Mengajukan akses file repository.
* Melihat pengumuman.

Apabila terdapat kebijakan peminjaman atau akses repository yang berbeda antara Mahasiswa dan Dosen, aturan tersebut akan ditentukan melalui kebijakan perpustakaan.

---

# 7. Hubungan Antar-Modul

Modul-modul sistem saling berhubungan sebagai berikut:

```text
                    ┌─────────────────────┐
                    │  Member Management  │
                    └──────────┬──────────┘
                               │
                               ▼
                         User Account
                               │
                ┌──────────────┼──────────────┐
                │              │              │
                ▼              ▼              ▼
             Catalog       Borrowing      Repository
                │              │              │
                │              │              │
                ▼              ▼              ▼
          Book Management  Book/Member    Repository
                │
                ▼
          Book Collection


                    ┌─────────────────────┐
                    │ Announcement        │
                    │ Management          │
                    └─────────────────────┘
```

---

# 8. Alur Utama Sistem

## 8.1 Registrasi Anggota

```text
Pengguna
   │
   ▼
Registrasi
   │
   ▼
Menunggu Persetujuan
   │
   ▼
Administrator
   │
   ├── Approve
   │     │
   │     ▼
   │   Aktif
   │
   └── Reject
         │
         ▼
      Ditolak
```

---

## 8.2 Pencarian dan Peminjaman Buku

```text
Pengguna
   │
   ▼
Online Catalog
   │
   ▼
Search / Filter
   │
   ▼
Detail Buku
   │
   ▼
Ketersediaan
   │
   ▼
Ajukan Peminjaman
   │
   ▼
Borrowing Management
   │
   ▼
Administrator
   │
   ├── Setujui
   │
   └── Tolak
```

---

## 8.3 Pengambilan dan Pengembalian

```text
Pengajuan Disetujui
        │
        ▼
Pengguna datang ke perpustakaan
        │
        ▼
Administrator mencatat pengambilan
        │
        ▼
Buku Dipinjam
        │
        ▼
Pengguna mengembalikan buku
        │
        ▼
Administrator menerima buku
        │
        ▼
Administrator mencatat pengembalian
        │
        ▼
Buku Tersedia
```

---

## 8.4 Akses Repository

```text
Pengguna
   │
   ▼
Repository
   │
   ▼
Detail Repository
   │
   ├── Metadata
   │
   └── Abstrak
         │
         ▼
    Ajukan Akses
         │
         ▼
   Administrator
         │
     ┌───┴───┐
     ▼       ▼
 Disetujui  Ditolak
     │
     ▼
 Akses File
```

---

# 9. Data Utama Sistem

Secara konseptual, sistem membutuhkan data utama berikut:

| Data                 | Modul             |
| -------------------- | ----------------- |
| User                 | Member Management |
| Member               | Member Management |
| Role                 | Member Management |
| Judul Buku           | Book Management   |
| Eksemplar Buku       | Book Management   |
| Penulis              | Book Management   |
| Penerbit             | Book Management   |
| Kategori             | Book Management   |
| Lokasi Rak           | Book Management   |
| Pengajuan Peminjaman | Borrowing         |
| Detail Peminjaman    | Borrowing         |
| Item Repository      | Repository        |
| File Repository      | Repository        |
| Permintaan Akses     | Repository        |
| Pengumuman           | Announcement      |

Daftar tersebut merupakan identifikasi konseptual dan belum merupakan desain database final.

---

# 10. Batasan MVP

Fitur berikut secara eksplisit berada di luar MVP:

* QR Code untuk Eksemplar Buku.
* Perpanjangan peminjaman.
* Upload repository secara mandiri oleh Mahasiswa/Dosen.
* Integrasi email otomatis untuk pengiriman file repository.
* Notifikasi otomatis apabila belum dikonfirmasi.
* Digital Rights Management.
* Statistik unduhan repository.
* Versioning file repository.
* Full-text search dalam dokumen PDF.
* Integrasi dengan sistem SSO universitas.

Fitur di luar MVP dapat dipertimbangkan pada fase pengembangan berikutnya.

---

# 11. Keputusan Bisnis yang Telah Disepakati

Bagian ini mencatat keputusan yang telah disepakati selama proses analisis requirement.

| No | Keputusan                                                                              |
| -- | -------------------------------------------------------------------------------------- |
| 1  | Sistem menggunakan tiga role utama: Administrator, Mahasiswa, dan Dosen.               |
| 2  | Registrasi anggota dilakukan secara manual melalui website.                            |
| 3  | Administrator dapat melakukan import data anggota melalui Excel.                       |
| 4  | Keanggotaan memerlukan persetujuan Administrator.                                      |
| 5  | Satu Judul Buku dapat memiliki banyak Eksemplar Buku.                                  |
| 6  | Satu Judul Buku dapat memiliki lebih dari satu Penulis.                                |
| 7  | ISBN bersifat opsional.                                                                |
| 8  | Kategori dikelola oleh Administrator/Pustakawan.                                       |
| 9  | Kategori digunakan sebagai filter katalog.                                             |
| 10 | Keyword pencarian utama katalog adalah Judul, Penulis, Penerbit, dan Tahun Terbit.     |
| 11 | Lokasi rak ditampilkan sebagai informasi untuk membantu pengguna menemukan buku.       |
| 12 | Peminjaman dimulai oleh pengguna melalui website.                                      |
| 13 | Setiap Eksemplar Buku dalam pengajuan dapat disetujui atau ditolak secara terpisah.    |
| 14 | Pengguna dapat membatalkan pengajuan yang belum diproses.                              |
| 15 | Pengembalian dilakukan secara fisik di perpustakaan dan dicatat oleh Administrator.    |
| 16 | Tidak ada pengajuan pengembalian melalui website.                                      |
| 17 | Perpanjangan peminjaman tidak termasuk MVP.                                            |
| 18 | Repository memiliki halaman detail dengan metadata dan abstrak.                        |
| 19 | Abstrak disimpan langsung di dalam sistem.                                             |
| 20 | File repository dapat dibatasi dan memerlukan persetujuan Administrator.               |
| 21 | File repository hanya diunggah oleh Administrator dalam MVP.                           |
| 22 | Mahasiswa/Dosen dapat mengirim file kepada Administrator melalui email di luar sistem. |
| 23 | Pengumuman dikelola oleh Administrator.                                                |
| 24 | QR Code belum termasuk dalam MVP.                                                      |

---

# 12. Open Questions

Requirement berikut masih membutuhkan konfirmasi dari pihak perpustakaan.

| ID         | Modul        | Pertanyaan                                                                    | Status |
| ---------- | ------------ | ----------------------------------------------------------------------------- | :----: |
| OQ-SYS-001 | Member       | Apakah terdapat masa berlaku keanggotaan?                                     |    ⏳   |
| OQ-SYS-002 | Member       | Apakah terdapat perbedaan hak akses antara Mahasiswa dan Dosen?               |    ⏳   |
| OQ-SYS-003 | Book         | Format final kode khusus Eksemplar Buku seperti apa yang akan digunakan?      |    ⏳   |
| OQ-SYS-004 | Borrowing    | Berapa jumlah maksimal buku yang dapat diajukan dalam satu hari?              |    ⏳   |
| OQ-SYS-005 | Borrowing    | Berapa lama masa peminjaman buku?                                             |    ⏳   |
| OQ-SYS-006 | Borrowing    | Apakah terdapat denda atau konsekuensi keterlambatan?                         |    ⏳   |
| OQ-SYS-007 | Borrowing    | Apakah pengguna yang memiliki keterlambatan dapat mengajukan peminjaman baru? |    ⏳   |
| OQ-SYS-008 | Borrowing    | Apakah Administrator wajib memberikan alasan ketika menolak peminjaman?       |    ⏳   |
| OQ-SYS-009 | Borrowing    | Apakah terdapat kebijakan peminjaman berbeda antara Mahasiswa dan Dosen?      |    ⏳   |
| OQ-SYS-010 | Repository   | Jenis karya ilmiah apa saja yang masuk MVP?                                   |    ⏳   |
| OQ-SYS-011 | Repository   | Metadata wajib apa saja untuk setiap jenis karya ilmiah?                      |    ⏳   |
| OQ-SYS-012 | Repository   | Apakah seluruh file repository memerlukan persetujuan akses?                  |    ⏳   |
| OQ-SYS-013 | Repository   | Apakah pengguna dapat mengajukan kembali setelah akses ditolak?               |    ⏳   |
| OQ-SYS-014 | Repository   | Format dan ukuran maksimum file repository?                                   |    ⏳   |
| OQ-SYS-015 | Catalog      | Apakah katalog dapat diakses tanpa login?                                     |    ⏳   |
| OQ-SYS-016 | Catalog      | Apakah satu judul dapat memiliki beberapa lokasi rak?                         |    ⏳   |
| OQ-SYS-017 | Catalog      | Apakah hasil pencarian perlu memiliki opsi sorting?                           |    ⏳   |
| OQ-SYS-018 | Announcement | Apakah pengumuman membutuhkan kategori?                                       |    ⏳   |
| OQ-SYS-019 | Announcement | Apakah pengumuman memiliki tanggal mulai dan berakhir?                        |    ⏳   |
| OQ-SYS-020 | Announcement | Apakah pengumuman membutuhkan gambar atau lampiran?                           |    ⏳   |

> Open Question tidak dianggap sebagai requirement final sampai mendapatkan konfirmasi dari pihak yang berwenang di perpustakaan.

---

# 13. Definition of Done

Requirement sistem dapat dinyatakan **Ready for System Design** apabila:

| No | Kriteria                                                      | Status |
| -- | ------------------------------------------------------------- | :----: |
| 1  | Tujuan sistem telah disepakati                                |    ☑   |
| 2  | Aktor sistem telah ditentukan                                 |    ☑   |
| 3  | Role utama telah ditentukan                                   |    ☑   |
| 4  | Modul utama telah ditentukan                                  |    ☑   |
| 5  | Scope MVP telah ditentukan                                    |    ☑   |
| 6  | Fitur di luar MVP telah dicatat                               |    ☑   |
| 7  | Alur utama sistem telah didefinisikan                         |    ☑   |
| 8  | Hubungan antar-modul telah didefinisikan                      |    ☑   |
| 9  | Data utama telah diidentifikasi secara konseptual             |    ☑   |
| 10 | Keputusan bisnis yang telah disepakati telah didokumentasikan |    ☑   |
| 11 | Seluruh Open Question telah dikonfirmasi client               |    ☐   |
| 12 | Seluruh dokumen functional requirement telah direview client  |    ☐   |
| 13 | Client menyetujui scope MVP                                   |    ☐   |
| 14 | Requirement dinyatakan siap menjadi dasar System Design       |    ☐   |

---

# 14. Requirement Status

**Current Status: Draft — Pending Client Confirmation**

Dokumen ini belum dianggap sebagai spesifikasi final sampai:

1. Seluruh Open Question telah mendapatkan keputusan.
2. Dokumen functional requirement masing-masing modul telah direview.
3. Scope MVP telah disetujui oleh client.
4. Tidak terdapat konflik requirement antar-modul.
5. Client dan developer memiliki pemahaman yang sama terhadap proses bisnis utama.

Setelah seluruh proses tersebut selesai, status dokumen dapat diubah menjadi:

**Approved — Ready for System Design**
