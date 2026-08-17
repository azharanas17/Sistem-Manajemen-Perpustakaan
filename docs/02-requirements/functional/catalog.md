# Catalog

## 1. Overview

Catalog merupakan modul yang digunakan untuk menyediakan informasi koleksi buku perpustakaan kepada pengguna.

Katalog menampilkan informasi berdasarkan **Judul Buku**, bukan berdasarkan Eksemplar secara terpisah.

Satu Judul Buku dapat memiliki beberapa Eksemplar, tetapi pengguna tetap berinteraksi dengan Judul Buku.

---

## 2. Tujuan

Modul Catalog bertujuan untuk:

- Memudahkan pengguna menemukan koleksi buku.
- Menampilkan informasi bibliografis buku.
- Menampilkan status publikasi koleksi.
- Menampilkan informasi ketersediaan buku.
- Menyediakan pencarian dan filter koleksi.
- Menghubungkan katalog dengan proses peminjaman.

---

## 3. Aktor

### 3.1 Administrator

Administrator dapat:

- Melihat katalog.
- Mengelola data Judul Buku.
- Mengelola kategori.
- Mengelola lokasi rak.
- Mengelola Eksemplar.
- Melihat informasi ketersediaan.

### 3.2 Mahasiswa

Mahasiswa dapat:

- Mengakses katalog setelah login.
- Mencari Judul Buku.
- Memfilter koleksi.
- Melihat detail Judul Buku.
- Melihat informasi ketersediaan.
- Mengajukan peminjaman melalui Judul Buku.

### 3.3 Dosen

Dosen memiliki hak akses katalog yang sama dengan Mahasiswa.

Dosen dapat:

- Mengakses katalog setelah login.
- Mencari Judul Buku.
- Memfilter koleksi.
- Melihat detail Judul Buku.
- Melihat informasi ketersediaan.
- Mengajukan peminjaman melalui Judul Buku.

---

## 4. Akses Katalog

Katalog hanya dapat diakses oleh pengguna yang telah login.

Guest tidak dapat mengakses katalog.

Dengan demikian:

```text
Guest
  ↓
Tidak dapat mengakses Catalog

Mahasiswa / Dosen
  ↓
Login
  ↓
Dapat mengakses Catalog
```

Administrator juga dapat mengakses katalog setelah login.

---

## 5. Catalog Item

Setiap item katalog merepresentasikan satu Judul Buku.

Contoh:

```text
Judul Buku:
Laravel untuk Pemula

Penulis:
John Doe

Penerbit:
ABC Publisher

Tahun:
2025

Lokasi:
Rak A-03

Eksemplar:
3

Available:
2
```

Eksemplar tidak ditampilkan sebagai item katalog yang terpisah.

---

## 6. Book Title Visibility

Hanya Judul Buku dengan status:

`Published`

yang ditampilkan sebagai koleksi aktif dalam katalog.

Judul Buku dengan status:

`Unpublished`

tidak ditampilkan sebagai koleksi aktif.

---

## 7. Book Availability

Ketersediaan buku ditentukan berdasarkan status Eksemplar.

Status Eksemplar:

- `Available`
- `Borrowed`

Contoh:

```text
Judul Buku:
Laravel untuk Pemula

Status:
Published

Eksemplar:
- Copy 001 → Borrowed
- Copy 002 → Available
- Copy 003 → Available

Total:
3

Available:
2
```

Maka Judul Buku dapat diajukan untuk peminjaman karena masih memiliki Eksemplar `Available`.

---

## 8. Book Unavailable

Jika seluruh Eksemplar suatu Judul Buku berstatus `Borrowed`, Judul Buku tetap dapat ditampilkan pada katalog selama status Judul Buku adalah `Published`.

Namun, pengguna tidak dapat membuat pengajuan peminjaman terhadap Judul Buku tersebut.

Contoh:

```text
Judul Buku:
Database Design

Status:
Published

Eksemplar:
- Copy 001 → Borrowed
- Copy 002 → Borrowed
- Copy 003 → Borrowed

Available:
0
```

Hasil:

```text
Tampil di katalog: Ya
Dapat diajukan: Tidak
```

Sistem tidak menyediakan waiting list pada MVP.

---

## 9. Book Selection

Ketika pengguna ingin meminjam buku, pengguna memilih:

**Judul Buku**

Pengguna tidak memilih Eksemplar tertentu.

Contoh:

```text
User memilih:

Laravel untuk Pemula
```

Bukan:

```text
Laravel untuk Pemula
├── Copy 001
├── Copy 002
└── Copy 003
```

Sistem menentukan Eksemplar yang digunakan berdasarkan ketersediaan pada proses peminjaman.

---

## 10. Search

Katalog menyediakan pencarian berdasarkan informasi utama buku.

Keyword pencarian dapat mencakup:

- Judul.
- Penulis.
- Penerbit.
- Tahun terbit.

Pencarian dilakukan terhadap Judul Buku.

---

## 11. Filter

Katalog menyediakan filter untuk membantu pengguna menemukan koleksi.

Filter utama meliputi:

- Kategori.
- Tahun terbit.
- Ketersediaan apabila diperlukan.

Kategori dikelola oleh Administrator.

---

## 12. Book Detail

Pengguna dapat membuka halaman detail Judul Buku.

Informasi yang dapat ditampilkan meliputi:

- Judul.
- Penulis.
- Penerbit.
- Tahun terbit.
- ISBN apabila tersedia.
- Kategori.
- Lokasi rak.
- Jumlah Eksemplar.
- Jumlah Eksemplar yang tersedia.
- Status ketersediaan.

Detail Eksemplar individual tidak menjadi fokus interaksi pengguna.

---

## 13. Book Location

Setiap Judul Buku memiliki satu lokasi rak.

Lokasi rak digunakan untuk membantu pengguna menemukan buku secara fisik di perpustakaan.

Contoh:

```text
Lokasi:
Rak A-03
```

Satu Judul Buku tidak memiliki beberapa lokasi rak pada MVP.

---

## 14. Catalog and Borrowing

Catalog terintegrasi dengan Borrowing Management.

Alur:

1. User login.
2. User membuka katalog.
3. User mencari Judul Buku.
4. User membuka detail buku.
5. Sistem menampilkan ketersediaan.
6. Jika tersedia, user dapat mengajukan peminjaman.
7. User memilih Judul Buku.
8. Sistem menentukan Eksemplar berdasarkan ketersediaan.

---

## 15. Access Control

Akses katalog:

| Aktor | Akses |
|-------|-------|
| Guest | Tidak dapat mengakses |
| Mahasiswa | Dapat mengakses setelah login |
| Dosen | Dapat mengakses setelah login |
| Administrator | Dapat mengakses setelah login |

Akses peminjaman tetap mengikuti aturan Borrowing Management.

---

## 16. Business Rules

| No | Aturan |
|----|--------|
| 1 | Katalog hanya dapat diakses oleh user yang telah login. |
| 2 | Guest tidak dapat mengakses katalog. |
| 3 | Katalog menampilkan Judul Buku, bukan Eksemplar sebagai item terpisah. |
| 4 | Hanya Judul Buku berstatus `Published` yang ditampilkan sebagai koleksi aktif. |
| 5 | Judul Buku `Unpublished` tidak ditampilkan sebagai koleksi aktif. |
| 6 | Satu Judul Buku dapat memiliki banyak Eksemplar. |
| 7 | Eksemplar memiliki status `Available` atau `Borrowed`. |
| 8 | Judul Buku tetap dapat ditampilkan walaupun seluruh Eksemplarnya sedang `Borrowed`. |
| 9 | Judul Buku tidak dapat diajukan apabila tidak memiliki Eksemplar `Available`. |
| 10 | User memilih Judul Buku, bukan Eksemplar tertentu. |
| 11 | Sistem menentukan Eksemplar berdasarkan ketersediaan. |
| 12 | Waiting list tidak termasuk MVP. |
| 13 | Satu Judul Buku hanya memiliki satu lokasi rak pada MVP. |
| 14 | Pencarian dapat menggunakan Judul, Penulis, Penerbit, dan Tahun. |
| 15 | Kategori dapat digunakan sebagai filter. |
| 16 | Kategori dikelola oleh Administrator. |
| 17 | Mahasiswa dan Dosen memiliki hak akses katalog yang sama. |

---

## 17. Features Outside MVP

Fitur berikut tidak termasuk dalam MVP:

- Akses katalog tanpa login.
- Pemilihan Eksemplar secara manual.
- Waiting list.
- QR Code untuk buku.
- Barcode scanning untuk pengguna.
- Rekomendasi buku berbasis AI.
- Personalisasi rekomendasi.
- Rating dan review buku.
- Integrasi RFID.

Fitur tersebut dapat dipertimbangkan pada fase pengembangan berikutnya.

---

## 18. Acceptance Criteria

Modul Catalog dianggap memenuhi requirement apabila:

### Access

- [ ] Guest tidak dapat mengakses katalog.
- [ ] Mahasiswa dapat mengakses katalog setelah login.
- [ ] Dosen dapat mengakses katalog setelah login.
- [ ] Administrator dapat mengakses katalog setelah login.

### Catalog

- [ ] Sistem menampilkan Judul Buku sebagai item katalog.
- [ ] Eksemplar tidak ditampilkan sebagai item katalog terpisah.
- [ ] Hanya Judul Buku `Published` yang ditampilkan sebagai koleksi aktif.
- [ ] Judul Buku `Unpublished` tidak ditampilkan sebagai koleksi aktif.

### Search

- [ ] User dapat mencari berdasarkan Judul.
- [ ] User dapat mencari berdasarkan Penulis.
- [ ] User dapat mencari berdasarkan Penerbit.
- [ ] User dapat mencari berdasarkan Tahun.

### Filter

- [ ] User dapat menggunakan filter Kategori.
- [ ] Kategori dikelola oleh Administrator.

### Availability

- [ ] Sistem dapat menampilkan informasi ketersediaan Eksemplar.
- [ ] Judul Buku tetap dapat ditampilkan ketika semua Eksemplarnya `Borrowed`.
- [ ] Judul Buku yang tidak memiliki Eksemplar `Available` tidak dapat diajukan.
- [ ] Sistem tidak menyediakan waiting list.

### Book Detail

- [ ] User dapat melihat detail Judul Buku.
- [ ] Detail menampilkan informasi bibliografis.
- [ ] Detail menampilkan lokasi rak.
- [ ] Detail dapat menampilkan jumlah Eksemplar.
- [ ] Detail dapat menampilkan jumlah Eksemplar yang tersedia.

### Borrowing Integration

- [ ] User memilih Judul Buku ketika melakukan peminjaman.
- [ ] User tidak memilih Eksemplar tertentu.
- [ ] Sistem menentukan Eksemplar berdasarkan ketersediaan.

---

## 19. Status Requirement

| Item | Status |
|------|--------|
| Business Requirement | Resolved |
| Functional Requirement | Resolved |
| Business Rules | Resolved |
| Acceptance Criteria | Defined |
| Client Review | Pending |
| Client Approval | Pending |