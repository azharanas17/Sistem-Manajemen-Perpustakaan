# Online Catalog

# 1. Tujuan

Modul Online Catalog menyediakan katalog koleksi buku perpustakaan yang dapat digunakan oleh pengguna untuk mencari, menemukan, dan melihat informasi buku yang tersedia.

Modul ini menjadi antarmuka utama bagi Mahasiswa dan Dosen untuk menemukan koleksi sebelum melakukan proses peminjaman.

---

# 2. Istilah yang Digunakan

## Katalog Online

Katalog Online adalah layanan yang memungkinkan pengguna mencari dan melihat informasi koleksi buku perpustakaan melalui website.

---

## Hasil Pencarian

Hasil Pencarian adalah daftar Judul Buku yang sesuai dengan kata kunci atau filter yang digunakan pengguna.

---

## Detail Judul Buku

Detail Judul Buku adalah halaman yang menampilkan informasi bibliografi lengkap mengenai suatu Judul Buku serta informasi Eksemplar Buku yang tersedia.

---

## Ketersediaan

Ketersediaan menunjukkan kondisi Eksemplar Buku yang berkaitan dengan suatu Judul Buku, khususnya apakah terdapat eksemplar yang dapat dipinjam.

---

# 3. Aktor

| Aktor         | Deskripsi                                                         |
| ------------- | ----------------------------------------------------------------- |
| Mahasiswa     | Mencari, melihat, dan mengajukan peminjaman buku melalui katalog. |
| Dosen         | Mencari, melihat, dan mengajukan peminjaman buku melalui katalog. |
| Administrator | Mengelola data koleksi yang menjadi sumber informasi katalog.     |

---

# 4. Tujuan Bisnis

Implementasi modul ini bertujuan untuk:

* Memudahkan pengguna menemukan koleksi perpustakaan.
* Mengurangi kebutuhan pengguna untuk mencari buku secara manual.
* Menampilkan lokasi fisik buku di perpustakaan.
* Menampilkan status ketersediaan buku.
* Menjadi titik awal proses peminjaman buku.
* Menyediakan informasi koleksi yang konsisten dengan data perpustakaan.

---

# 5. Ruang Lingkup

Modul Online Catalog mencakup:

* Menampilkan katalog buku.
* Pencarian buku.
* Filter berdasarkan kategori.
* Melihat hasil pencarian.
* Melihat detail Judul Buku.
* Melihat informasi Penulis.
* Melihat informasi Penerbit.
* Melihat tahun terbit.
* Melihat ISBN apabila tersedia.
* Melihat lokasi rak.
* Melihat jumlah dan status Eksemplar Buku.
* Mengarahkan pengguna ke proses peminjaman.

---

# 6. Functional Requirements

## FR-CAT-001 — Menampilkan Katalog Buku

### Tujuan

Pengguna dapat melihat koleksi buku yang tersedia melalui katalog online.

### Aktor

* Mahasiswa
* Dosen

### Acceptance Criteria

* Sistem menampilkan daftar Judul Buku.
* Informasi dasar buku ditampilkan pada daftar katalog.
* Pengguna dapat membuka halaman Detail Judul Buku.

---

## FR-CAT-002 — Pencarian Berdasarkan Judul

### Tujuan

Pengguna dapat menemukan buku berdasarkan Judul Buku.

### Acceptance Criteria

* Pengguna dapat memasukkan kata kunci judul.
* Sistem menampilkan Judul Buku yang sesuai dengan kata kunci.
* Pencarian tidak harus menggunakan judul secara lengkap.

---

## FR-CAT-003 — Pencarian Berdasarkan Penulis

### Tujuan

Pengguna dapat menemukan buku berdasarkan Penulis.

### Acceptance Criteria

* Pengguna dapat memasukkan nama Penulis sebagai kata kunci.
* Sistem menampilkan Judul Buku yang memiliki Penulis tersebut.
* Sistem mendukung buku dengan lebih dari satu Penulis.

---

## FR-CAT-004 — Pencarian Berdasarkan Penerbit

### Tujuan

Pengguna dapat menemukan buku berdasarkan Penerbit.

### Acceptance Criteria

* Pengguna dapat memasukkan nama Penerbit.
* Sistem menampilkan Judul Buku yang diterbitkan oleh Penerbit tersebut.

---

## FR-CAT-005 — Pencarian Berdasarkan Tahun Terbit

### Tujuan

Pengguna dapat menemukan buku berdasarkan Tahun Terbit.

### Acceptance Criteria

* Pengguna dapat menggunakan Tahun Terbit sebagai kata kunci atau parameter pencarian.
* Sistem menampilkan Judul Buku yang sesuai dengan tahun yang dicari.

---

## FR-CAT-006 — Filter Berdasarkan Kategori

### Tujuan

Pengguna dapat mempersempit hasil katalog berdasarkan kategori buku.

### Acceptance Criteria

* Sistem menyediakan filter Kategori.
* Pengguna dapat memilih satu kategori.
* Filter dapat digunakan bersama pencarian.

Kategori dikelola oleh Administrator melalui Book Management.

---

## FR-CAT-007 — Melihat Detail Judul Buku

### Tujuan

Pengguna dapat melihat informasi lengkap sebuah Judul Buku.

### Acceptance Criteria

Halaman detail menampilkan informasi seperti:

* Judul Buku
* Penulis
* Penerbit
* Tahun Terbit
* ISBN apabila tersedia
* Kategori
* Bahasa apabila tersedia
* Edisi apabila tersedia
* Deskripsi atau sinopsis apabila tersedia
* Sampul buku apabila tersedia

---

## FR-CAT-008 — Melihat Eksemplar Buku

### Tujuan

Pengguna dapat mengetahui keberadaan Eksemplar Buku dari suatu Judul Buku.

### Acceptance Criteria

Halaman Detail Judul Buku menampilkan informasi:

* Jumlah Eksemplar Buku.
* Jumlah Eksemplar Buku yang tersedia.
* Lokasi rak.
* Status ketersediaan.

---

## FR-CAT-009 — Melihat Lokasi Rak

### Tujuan

Pengguna dapat mengetahui lokasi fisik buku di perpustakaan.

### Acceptance Criteria

* Lokasi rak ditampilkan pada Detail Judul Buku.
* Informasi lokasi dapat digunakan pengguna untuk menemukan buku secara fisik.

---

## FR-CAT-010 — Menampilkan Status Ketersediaan

### Tujuan

Pengguna dapat mengetahui apakah suatu Judul Buku memiliki Eksemplar Buku yang dapat dipinjam.

### Acceptance Criteria

Sistem menampilkan informasi ketersediaan yang mudah dipahami pengguna.

Contoh:

* Tersedia
* Tidak tersedia

Status tersebut ditentukan berdasarkan status Eksemplar Buku.

---

## FR-CAT-011 — Mengajukan Peminjaman

### Tujuan

Pengguna dapat memulai proses peminjaman dari katalog.

### Acceptance Criteria

* Pengguna yang memenuhi syarat dapat mengajukan peminjaman.
* Pengguna diarahkan ke proses Borrowing Management.
* Hanya Eksemplar Buku yang memenuhi syarat peminjaman yang dapat dipilih.

Detail mengenai proses pengajuan, persetujuan, pengambilan, dan pengembalian didefinisikan dalam `borrowing.md`.

---

# 7. Informasi yang Ditampilkan

Informasi yang ditampilkan dalam katalog berasal dari data Judul Buku dan Eksemplar Buku.

## Informasi Judul Buku

| Informasi            | Ditampilkan | Keterangan                    |
| -------------------- | :---------: | ----------------------------- |
| Judul                |      ✅      | Judul utama buku.             |
| Penulis              |      ✅      | Satu atau lebih penulis.      |
| Penerbit             |      ✅      | Penerbit buku.                |
| Tahun Terbit         |      ✅      | Tahun penerbitan.             |
| ISBN                 |      ❌      | Ditampilkan apabila tersedia. |
| Kategori             |      ✅      | Kategori buku.                |
| Bahasa               |      ❌      | Ditampilkan apabila tersedia. |
| Edisi                |      ❌      | Ditampilkan apabila tersedia. |
| Deskripsi / Sinopsis |      ❌      | Ditampilkan apabila tersedia. |
| Sampul               |      ❌      | Ditampilkan apabila tersedia. |

---

## Informasi Eksemplar

| Informasi        | Ditampilkan | Keterangan                                 |
| ---------------- | :---------: | ------------------------------------------ |
| Jumlah Eksemplar |      ✅      | Jumlah seluruh eksemplar dari suatu judul. |
| Jumlah Tersedia  |      ✅      | Jumlah eksemplar yang dapat dipinjam.      |
| Lokasi Rak       |      ✅      | Lokasi fisik penyimpanan.                  |
| Status           |      ✅      | Ketersediaan eksemplar.                    |

---

# 8. Business Rules

## BR-CAT-001 — Sumber Data Katalog

Data katalog berasal dari data koleksi yang dikelola melalui Book Management.

Administrator tidak perlu memasukkan data buku secara terpisah untuk kebutuhan katalog.

---

## BR-CAT-002 — Hanya Koleksi Aktif

Hanya Judul Buku yang masih menjadi koleksi aktif yang ditampilkan dalam katalog.

---

## BR-CAT-003 — Satu Judul, Banyak Eksemplar

Satu Judul Buku dapat ditampilkan sebagai satu hasil katalog meskipun memiliki beberapa Eksemplar Buku.

Informasi jumlah dan ketersediaan eksemplar ditampilkan pada Detail Judul Buku.

---

## BR-CAT-004 — Penulis Ganda

Katalog harus dapat menampilkan lebih dari satu Penulis untuk satu Judul Buku.

---

## BR-CAT-005 — ISBN Opsional

Ketiadaan ISBN tidak menyebabkan Judul Buku tidak dapat ditampilkan di katalog.

---

## BR-CAT-006 — Kategori sebagai Filter

Kategori digunakan sebagai filter katalog dan bukan merupakan keyword pencarian utama.

---

## BR-CAT-007 — Lokasi Rak

Lokasi rak digunakan untuk membantu pengguna menemukan Eksemplar Buku secara fisik.

Lokasi rak bukan merupakan keyword pencarian utama.

---

## BR-CAT-008 — Ketersediaan

Status ketersediaan pada tingkat Judul Buku ditentukan berdasarkan kondisi Eksemplar Buku yang terkait.

Apabila setidaknya terdapat satu Eksemplar Buku yang berstatus Tersedia, Judul Buku dapat ditampilkan sebagai memiliki ketersediaan.

---

## BR-CAT-009 — Buku Tidak Tersedia

Judul Buku tetap dapat ditampilkan meskipun seluruh Eksemplarnya sedang tidak tersedia.

Pengguna harus dapat mengetahui bahwa buku tersebut saat ini tidak tersedia.

---

## BR-CAT-010 — Akses Peminjaman

Pengguna hanya dapat memulai proses peminjaman apabila memenuhi aturan peminjaman yang ditentukan dalam Borrowing Management.

---

# 9. Alur Penggunaan Katalog

Alur utama katalog:

```text
Katalog Online
      │
      ▼
 Masukkan Keyword
      │
      ▼
Hasil Pencarian
      │
      ├──── Filter Kategori
      │
      ▼
 Detail Judul Buku
      │
      ├── Informasi Bibliografi
      │
      ├── Penulis
      │
      ├── Penerbit
      │
      ├── Ketersediaan
      │
      └── Lokasi Rak
              │
              ▼
       Ajukan Peminjaman
              │
              ▼
      Borrowing Management
```

---

# 10. Pencarian dan Filter

Katalog menyediakan pencarian berdasarkan empat informasi utama:

1. Judul Buku
2. Penulis
3. Penerbit
4. Tahun Terbit

Kategori digunakan sebagai filter.

Contoh penggunaan:

```text
Keyword:
"Laravel"

Filter:
Kategori = Pemrograman
```

Sistem kemudian menampilkan Judul Buku yang sesuai dengan keyword dan filter tersebut.

---

# 11. Definition of Done

Dokumen Online Catalog dapat dinyatakan **Approved** apabila:

| No | Kriteria                                                     | Status |
| -- | ------------------------------------------------------------ | :----: |
| 1  | Tujuan modul telah didefinisikan                             |    ☑   |
| 2  | Istilah bisnis telah didefinisikan                           |    ☑   |
| 3  | Aktor telah diidentifikasi                                   |    ☑   |
| 4  | Ruang lingkup telah ditentukan                               |    ☑   |
| 5  | Functional Requirement telah ditulis                         |    ☑   |
| 6  | Informasi yang ditampilkan telah didefinisikan               |    ☑   |
| 7  | Business Rule telah ditulis                                  |    ☑   |
| 8  | Pencarian telah didefinisikan                                |    ☑   |
| 9  | Filter telah didefinisikan                                   |    ☑   |
| 10 | Detail Judul Buku telah didefinisikan                        |    ☑   |
| 11 | Informasi Eksemplar telah didefinisikan                      |    ☑   |
| 12 | Integrasi dengan Borrowing telah didefinisikan               |    ☑   |
| 13 | Tidak terdapat detail implementasi teknis                    |    ☑   |
| 14 | Seluruh Open Question telah dikonfirmasi oleh client         |    ☐   |
| 15 | Dokumen siap digunakan sebagai dasar desain dan pengembangan |    ☐   |

---

# 12. Open Questions

Bagian ini berisi keputusan yang masih memerlukan konfirmasi dari pihak perpustakaan.

| ID         | Pertanyaan                                                                                        | Status |
| ---------- | ------------------------------------------------------------------------------------------------- | :----: |
| OQ-CAT-001 | Apakah katalog dapat diakses tanpa login?                                                         |    ⏳   |
| OQ-CAT-002 | Apakah pengguna dapat melihat buku yang sedang dipinjam oleh pengguna lain?                       |    ⏳   |
| OQ-CAT-003 | Apakah satu Judul Buku dapat memiliki beberapa lokasi rak?                                        |    ⏳   |
| OQ-CAT-004 | Apakah katalog perlu menyediakan pagination atau infinite scrolling?                              |    ⏳   |
| OQ-CAT-005 | Apakah pengguna perlu dapat mengurutkan hasil pencarian berdasarkan judul, tahun, atau relevansi? |    ⏳   |
| OQ-CAT-006 | Apakah perlu tersedia fitur pencarian berdasarkan ISBN meskipun ISBN bukan keyword utama?         |    ⏳   |

> Open Question tidak dianggap sebagai requirement final sebelum mendapatkan konfirmasi dari pihak perpustakaan.
