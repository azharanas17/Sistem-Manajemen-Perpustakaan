# Book Management

## 1. Overview

Book Management merupakan modul yang digunakan untuk mengelola data koleksi buku perpustakaan.

Modul ini membedakan antara:

- **Judul Buku**
- **Eksemplar Buku**

Satu Judul Buku dapat memiliki lebih dari satu Eksemplar.

Judul Buku merepresentasikan informasi bibliografis buku, sedangkan Eksemplar merepresentasikan salinan fisik yang dimiliki perpustakaan.

---

## 2. Tujuan

Modul Book Management bertujuan untuk:

- Mengelola data Judul Buku.
- Mengelola Eksemplar Buku.
- Memisahkan data bibliografis dari inventory fisik.
- Mengetahui jumlah Eksemplar yang dimiliki untuk suatu Judul Buku.
- Mengetahui ketersediaan Eksemplar.
- Mendukung proses katalog dan peminjaman.

---

## 3. Aktor

### 3.1 Administrator

Administrator bertanggung jawab terhadap pengelolaan koleksi buku.

Administrator dapat:

- Membuat Judul Buku.
- Mengubah data Judul Buku.
- Mengubah status publikasi Judul Buku.
- Menambahkan Eksemplar.
- Melihat daftar Eksemplar.
- Melihat status Eksemplar.
- Mengelola informasi lokasi rak.
- Mengelola informasi bibliografis buku.
- Mengelola kategori buku.

### 3.2 Mahasiswa

Mahasiswa dapat:

- Melihat Judul Buku yang berstatus `Published`.
- Melihat informasi buku melalui katalog.
- Mengajukan peminjaman Judul Buku yang tersedia.

Mahasiswa tidak memilih Eksemplar tertentu.

### 3.3 Dosen

Dosen memiliki hak dan aturan yang sama dengan Mahasiswa.

Dosen dapat:

- Melihat Judul Buku yang berstatus `Published`.
- Melihat informasi buku melalui katalog.
- Mengajukan peminjaman Judul Buku yang tersedia.

Dosen tidak memilih Eksemplar tertentu.

---

## 4. Book Title

Judul Buku merupakan entitas utama yang merepresentasikan sebuah judul koleksi.

Satu Judul Buku dapat memiliki banyak Eksemplar.

Contoh:

```text
Judul Buku:
Laravel untuk Pemula

Eksemplar:
- Copy 001
- Copy 002
- Copy 003
```

Informasi Judul Buku dapat meliputi:

- Judul.
- Penulis.
- Penerbit.
- Tahun terbit.
- ISBN apabila tersedia.
- Kategori.
- Lokasi rak.
- Status publikasi.

---

## 5. Book Title Status

Judul Buku memiliki status:

- `Published`
- `Unpublished`

### 5.1 Published

Judul Buku dengan status `Published` dapat ditampilkan pada katalog kepada pengguna yang telah login.

Judul Buku dapat diajukan untuk peminjaman apabila memiliki Eksemplar dengan status `Available`.

### 5.2 Unpublished

Judul Buku dengan status `Unpublished` tidak ditampilkan sebagai koleksi aktif dalam katalog pengguna.

Judul Buku `Unpublished` tidak dapat diajukan untuk peminjaman.

---

## 6. Book Copy / Eksemplar

Eksemplar merupakan salinan fisik dari suatu Judul Buku.

Satu Judul Buku dapat memiliki lebih dari satu Eksemplar.

Setiap Eksemplar memiliki identitas tersendiri sehingga Administrator dapat membedakan setiap salinan fisik.

Contoh:

```text
Judul Buku:
Database Design

Eksemplar:
- Database Design / Copy 001
- Database Design / Copy 002
- Database Design / Copy 003
```

---

## 7. Book Copy Status

Status Eksemplar pada MVP terdiri dari:

- `Available`
- `Borrowed`

### 7.1 Available

Eksemplar dengan status `Available` tersedia untuk digunakan dalam proses peminjaman.

### 7.2 Borrowed

Eksemplar dengan status `Borrowed` sedang berada dalam status peminjaman.

Perubahan status secara umum:

```text
Available → Borrowed → Available
```

Eksemplar menjadi `Borrowed` setelah buku diambil oleh anggota.

Eksemplar kembali menjadi `Available` setelah Administrator mencatat pengembalian.

---

## 8. Book Title and Book Copy Relationship

Hubungan antara Judul Buku dan Eksemplar:

```text
Book Title
    │
    ├── Book Copy 001
    ├── Book Copy 002
    └── Book Copy 003
```

Satu Judul Buku:

- Dapat memiliki satu Eksemplar.
- Dapat memiliki banyak Eksemplar.

Setiap Eksemplar hanya terkait dengan satu Judul Buku.

---

## 9. Book Location

Setiap Judul Buku memiliki satu lokasi rak.

Eksemplar dari Judul Buku yang sama dianggap berada pada lokasi rak yang sama.

Contoh:

```text
Judul Buku:
Laravel untuk Pemula

Lokasi:
Rak A-03

Eksemplar:
- Copy 001
- Copy 002
- Copy 003
```

Pada MVP, satu Judul Buku tidak memiliki beberapa lokasi rak.

---

## 10. Catalog Visibility

Hanya Judul Buku dengan status `Published` yang dapat ditampilkan dalam katalog pengguna.

Judul Buku `Unpublished` tidak ditampilkan sebagai koleksi aktif.

Status Eksemplar tidak menentukan apakah Judul Buku ditampilkan atau tidak.

Contoh:

```text
Judul Buku: Published

Copy 001 → Borrowed
Copy 002 → Borrowed
Copy 003 → Available
```

Judul Buku tetap dapat ditampilkan.

Jika seluruh Eksemplar sedang `Borrowed`, Judul Buku tetap dapat ditampilkan tetapi tidak dapat diajukan untuk peminjaman karena tidak ada Eksemplar `Available`.

---

## 11. Book Availability

Ketersediaan Judul Buku ditentukan berdasarkan Eksemplar.

Sebuah Judul Buku dapat diajukan untuk peminjaman apabila:

- Status Judul Buku adalah `Published`.
- Terdapat minimal satu Eksemplar dengan status `Available`.

Jika semua Eksemplar berstatus `Borrowed`, Judul Buku tidak dapat diajukan.

Sistem tidak menyediakan waiting list pada MVP.

---

## 12. Book Management Flow

Alur pengelolaan buku:

1. Administrator membuat Judul Buku.
2. Administrator mengisi informasi bibliografis.
3. Administrator menentukan kategori.
4. Administrator menentukan lokasi rak.
5. Administrator menentukan status publikasi.
6. Administrator menambahkan Eksemplar.
7. Setiap Eksemplar memiliki status `Available`.
8. Buku dapat ditampilkan pada katalog apabila Judul Buku berstatus `Published`.
9. Ketika Eksemplar dipinjam, status berubah menjadi `Borrowed`.
10. Ketika Eksemplar dikembalikan, status kembali menjadi `Available`.

---

## 13. Book Information

Informasi yang dapat dikelola untuk Judul Buku meliputi:

- Judul.
- Penulis.
- Penerbit.
- Tahun terbit.
- ISBN apabila tersedia.
- Kategori.
- Lokasi rak.
- Status publikasi.

ISBN bersifat opsional.

---

## 14. Category

Kategori digunakan untuk mengelompokkan koleksi buku.

Kategori dikelola oleh Administrator.

Administrator dapat:

- Membuat kategori.
- Mengubah kategori.
- Mengelola kategori yang digunakan oleh Judul Buku.

Kategori digunakan sebagai filter dalam katalog.

---

## 15. Book Copy Identification

Setiap Eksemplar memiliki identitas yang membedakan Eksemplar tersebut dari Eksemplar lainnya.

Format khusus untuk kode Eksemplar belum ditetapkan pada MVP.

Contoh format kode khusus seperti:

```text
{JudulBuku}_{TahunTerbit}_{Penerbit}_{sortNumber}
```

belum menjadi requirement MVP.

Implementasi kode identifikasi dapat ditentukan pada tahap System Design berdasarkan kebutuhan teknis dan operasional.

---

## 16. Business Rules

| No | Aturan |
|----|--------|
| 1 | Satu Judul Buku dapat memiliki lebih dari satu Eksemplar. |
| 2 | Setiap Eksemplar hanya terkait dengan satu Judul Buku. |
| 3 | Judul Buku memiliki status `Published` atau `Unpublished`. |
| 4 | Eksemplar memiliki status `Available` atau `Borrowed`. |
| 5 | Judul Buku `Published` dapat ditampilkan pada katalog. |
| 6 | Judul Buku `Unpublished` tidak ditampilkan sebagai koleksi aktif. |
| 7 | Judul Buku hanya dapat diajukan apabila memiliki Eksemplar `Available`. |
| 8 | User memilih Judul Buku, bukan Eksemplar tertentu. |
| 9 | Sistem menentukan Eksemplar berdasarkan ketersediaan. |
| 10 | Satu Judul Buku hanya memiliki satu lokasi rak pada MVP. |
| 11 | ISBN bersifat opsional. |
| 12 | Waiting list tidak termasuk MVP. |
| 13 | Status Eksemplar berubah dari `Available` menjadi `Borrowed` ketika buku diambil. |
| 14 | Status Eksemplar berubah dari `Borrowed` menjadi `Available` ketika pengembalian dicatat. |
| 15 | Mahasiswa dan Dosen memiliki aturan akses dan peminjaman yang sama. |
| 16 | Kategori buku dikelola oleh Administrator. |

---

## 17. Features Outside MVP

Fitur berikut tidak termasuk dalam MVP:

- Pemilihan Eksemplar secara manual oleh anggota.
- Waiting list buku.
- QR Code untuk Eksemplar.
- Format kode Eksemplar khusus.
- Satu Judul Buku dengan beberapa lokasi rak.
- Status Eksemplar seperti `Damaged`, `Lost`, atau `Inactive`.
- Integrasi RFID.
- Integrasi barcode scanner.
- Pelacakan kondisi fisik buku secara khusus.

Fitur tersebut dapat dipertimbangkan pada fase pengembangan berikutnya.

---

## 18. Acceptance Criteria

Modul Book Management dianggap memenuhi requirement apabila:

### Book Title

- [ ] Administrator dapat membuat Judul Buku.
- [ ] Administrator dapat mengubah data Judul Buku.
- [ ] Administrator dapat mengatur status `Published`.
- [ ] Administrator dapat mengatur status `Unpublished`.
- [ ] Judul Buku memiliki informasi bibliografis.
- [ ] ISBN dapat disimpan apabila tersedia.

### Book Copy

- [ ] Administrator dapat menambahkan Eksemplar.
- [ ] Satu Judul Buku dapat memiliki banyak Eksemplar.
- [ ] Setiap Eksemplar memiliki identitas tersendiri.
- [ ] Eksemplar memiliki status `Available`.
- [ ] Eksemplar memiliki status `Borrowed`.
- [ ] Administrator dapat melihat status Eksemplar.

### Location

- [ ] Administrator dapat menentukan lokasi rak untuk Judul Buku.
- [ ] Satu Judul Buku hanya memiliki satu lokasi rak pada MVP.

### Availability

- [ ] Judul Buku `Published` dapat ditampilkan pada katalog.
- [ ] Judul Buku `Unpublished` tidak ditampilkan sebagai koleksi aktif.
- [ ] Judul Buku dapat diajukan apabila memiliki Eksemplar `Available`.
- [ ] Judul Buku yang seluruh Eksemplarnya `Borrowed` tidak dapat diajukan.
- [ ] Sistem tidak menyediakan waiting list.

### Borrowing Integration

- [ ] User memilih Judul Buku, bukan Eksemplar.
- [ ] Sistem menentukan Eksemplar berdasarkan ketersediaan.
- [ ] Eksemplar berubah menjadi `Borrowed` ketika buku diambil.
- [ ] Eksemplar berubah kembali menjadi `Available` ketika buku dikembalikan.

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