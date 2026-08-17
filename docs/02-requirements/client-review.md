# Client Requirement Review

# 1. Tujuan Dokumen

Dokumen ini digunakan untuk melakukan review dan konfirmasi kebutuhan sistem informasi perpustakaan antara pihak perpustakaan sebagai client/stakeholder dan developer.

Tujuan utama dokumen ini adalah memastikan bahwa fitur, alur kerja, serta aturan bisnis yang akan diterapkan pada sistem telah sesuai dengan proses dan kebijakan perpustakaan.

Dokumen ini menjadi dasar persetujuan kebutuhan sistem sebelum proses perancangan dan pengembangan dimulai.

---

# 2. Gambaran Umum Sistem

Sistem informasi perpustakaan merupakan aplikasi berbasis web yang menyediakan layanan perpustakaan kepada Mahasiswa dan Dosen serta membantu Administrator/Pustakawan dalam mengelola operasional perpustakaan.

Sistem mencakup beberapa layanan utama:

- Manajemen anggota.
- Katalog buku.
- Peminjaman buku.
- Pengelolaan repository.
- Pengumuman dan informasi perpustakaan.

---

# 3. Pengguna Sistem

Sistem memiliki tiga role utama:

| Role | Deskripsi |
|------|-----------|
| Administrator | Pustakawan yang bertanggung jawab mengelola data dan operasional perpustakaan melalui sistem. |
| Mahasiswa | Anggota perpustakaan dari kalangan mahasiswa. |
| Dosen | Anggota perpustakaan dari kalangan dosen. |

Mahasiswa dan Dosen memiliki aturan peminjaman dan akses layanan yang sama.

---

# 4. Modul Sistem

Sistem terdiri dari modul berikut:

1. Member Management
2. Book Management
3. Online Catalog
4. Borrowing Management
5. Repository Management
6. Announcement Management

---

# 5. Member Management

## 5.1 Registrasi

Mahasiswa dan Dosen dapat melakukan registrasi sebagai anggota melalui website.

Setelah melakukan registrasi, akun berada dalam status menunggu persetujuan Administrator.

Alur registrasi:

1. Pengguna melakukan registrasi.
2. Status keanggotaan menjadi `Pending`.
3. Administrator melakukan review.
4. Administrator dapat:
   - Menyetujui → `Active`
   - Menolak → `Rejected`

## 5.2 Pengelolaan Anggota

Administrator dapat:

- Melihat data anggota.
- Memeriksa data anggota.
- Menyetujui pendaftaran anggota.
- Menolak pendaftaran anggota.
- Mengubah data anggota.
- Mengelola data anggota.

Administrator juga dapat melakukan import data anggota menggunakan file Excel.

## 5.3 User dan Member

Akun pengguna dan keanggotaan perpustakaan diperlakukan sebagai dua konsep yang berbeda.

Akun digunakan untuk mengakses sistem, sedangkan keanggotaan menentukan status pengguna sebagai anggota perpustakaan.

---

# 6. Book Management

Administrator dapat mengelola koleksi buku yang dimiliki perpustakaan.

## 6.1 Judul Buku

Satu Judul Buku dapat memiliki:

- Satu atau lebih Penulis.
- Satu atau lebih Eksemplar.
- Satu Penerbit.
- Satu Tahun Terbit.
- Satu Kategori.
- Satu lokasi rak.

ISBN bersifat opsional.

## 6.2 Eksemplar Buku

Satu Judul Buku dapat memiliki beberapa Eksemplar Buku.

Setiap Eksemplar memiliki identitas sendiri.

Status Eksemplar:

- `Available`
- `Borrowed`

Status publikasi koleksi berada pada level Judul Buku:

- `Published`
- `Unpublished`

Dengan demikian, status publikasi tidak digunakan sebagai status kondisi fisik Eksemplar.

## 6.3 Lokasi Rak

Satu Judul Buku dikelompokkan pada satu lokasi rak.

Sistem tidak mendukung satu Judul Buku memiliki beberapa lokasi rak dalam MVP.

---

# 7. Online Catalog

Katalog digunakan untuk membantu pengguna menemukan koleksi buku yang tersedia di perpustakaan.

Katalog hanya dapat diakses oleh pengguna yang telah login.

## 7.1 Pencarian

Pengguna dapat melakukan pencarian berdasarkan:

- Judul Buku
- Penulis
- Penerbit
- Tahun Terbit

## 7.2 Filter

Pengguna dapat melakukan filter berdasarkan Kategori.

## 7.3 Informasi Buku

Halaman detail buku dapat menampilkan:

- Judul Buku
- Penulis
- Penerbit
- Tahun Terbit
- Kategori
- ISBN apabila tersedia
- Lokasi rak
- Informasi ketersediaan

---

# 8. Borrowing Management

Peminjaman buku dimulai oleh Mahasiswa atau Dosen melalui website.

## 8.1 Pengajuan Peminjaman

Pengguna memilih Judul Buku yang ingin dipinjam.

Pengguna tidak memilih Eksemplar tertentu.

Sistem akan menentukan Eksemplar yang digunakan berdasarkan ketersediaan.

Jika tidak terdapat Eksemplar yang tersedia, buku tidak dapat diajukan untuk peminjaman.

## 8.2 Batas Peminjaman

Seorang anggota dapat memiliki maksimal:

**3 pengajuan peminjaman yang disetujui dalam satu hari.**

Pengajuan yang ditolak tidak dihitung dalam batas tersebut.

## 8.3 Persetujuan Peminjaman

Administrator memproses setiap buku secara terpisah.

Contoh:

- Buku A → `Approved`
- Buku B → `Rejected`
- Buku C → `Approved`

Dengan demikian, satu pengajuan dapat menghasilkan keputusan yang berbeda untuk setiap buku.

Jika suatu buku ditolak, Administrator wajib memberikan alasan penolakan.

## 8.4 Pembatalan Pengajuan

Pengguna dapat membatalkan pengajuan peminjaman selama pengajuan tersebut belum diproses oleh Administrator.

Pembatalan digunakan agar status peminjaman dapat segera diperbarui dan ketersediaan buku dapat digunakan oleh pengguna lain.

## 8.5 Pengambilan Buku

Setelah pengajuan disetujui, pengguna datang ke perpustakaan untuk mengambil buku secara fisik.

Administrator mencatat bahwa buku telah diambil melalui sistem.

## 8.6 Masa Peminjaman

Masa peminjaman buku adalah:

**7 hari.**

## 8.7 Pengembalian

Pengembalian dilakukan secara fisik di perpustakaan.

Pengguna tidak perlu mengajukan proses pengembalian melalui website.

Ketika buku dikembalikan:

1. Pengguna menyerahkan buku secara fisik.
2. Administrator menerima buku.
3. Administrator mencatat pengembalian melalui sistem.
4. Status Eksemplar kembali menjadi `Available`.

## 8.8 Keterlambatan

Jika pengguna terlambat mengembalikan buku:

- Pengguna tidak dapat mengajukan peminjaman baru.
- Informasi keterlambatan dicatat dalam sistem.

## 8.9 Denda

Perpustakaan menerapkan denda keterlambatan.

Namun, sistem dalam MVP hanya menangani **pencatatan denda**.

Sistem tidak mencakup:

- Perhitungan denda otomatis.
- Pembayaran denda secara online.
- Payment gateway.
- Pelunasan denda melalui sistem.

---

# 9. Repository Management

Repository digunakan untuk menyimpan dan menyediakan akses terhadap karya ilmiah perpustakaan.

## 9.1 Scope Repository MVP

Jenis karya ilmiah yang termasuk dalam MVP:

- Skripsi
- Tesis
- Disertasi

## 9.2 Halaman Detail Repository

Setiap repository memiliki halaman detail yang menampilkan informasi lengkap sebelum pengguna meminta akses atau mengunduh file.

Informasi yang dapat ditampilkan meliputi metadata dan abstrak.

Abstrak disimpan langsung di dalam sistem agar dapat dibaca tanpa harus mengunduh file lengkap.

## 9.3 Akses File

Semua file repository membutuhkan persetujuan Administrator sebelum dapat diunduh.

Alur akses:

1. User membuka Repository.
2. User melihat Metadata dan Abstrak.
3. User mengajukan akses.
4. Administrator melakukan review.
5. Administrator dapat:
   - Menyetujui → akses file diberikan selama 7 hari.
   - Menolak → User dapat mengajukan akses kembali.

## 9.4 Upload File

Pada MVP, hanya Administrator yang dapat mengunggah file repository ke dalam sistem.

Jika Mahasiswa atau Dosen memiliki dokumen yang ingin dimasukkan ke repository, dokumen dapat dikirim kepada Administrator melalui email atau media komunikasi di luar sistem.

Administrator kemudian melakukan proses upload ke sistem.

## 9.5 Validasi Repository

Administrator wajib melakukan pemeriksaan dan persetujuan metadata sebelum repository dipublikasikan.

## 9.6 Batas Ukuran File

Ukuran maksimum file repository:

**100 MB.**

---

# 10. Announcement Management

Administrator dapat mengelola pengumuman dan informasi perpustakaan.

## 10.1 Status Pengumuman

Pengumuman memiliki status:

- `Draft`
- `Published`
- `Archived`

Alur umum:

`Draft → Published → Archived`

## 10.2 Target Pengumuman

Seluruh pengumuman ditujukan kepada semua pengguna sistem.

Tidak terdapat segmentasi pengumuman berdasarkan Mahasiswa atau Dosen dalam MVP.

## 10.3 Kategori

Pengumuman memiliki kategori.

Kategori digunakan untuk membantu pengelompokan dan pengelolaan informasi.

## 10.4 Periode Publikasi

Pengumuman memiliki:

- Tanggal mulai.
- Tanggal berakhir.

## 10.5 Gambar dan Lampiran

Gambar atau lampiran tidak wajib digunakan pada pengumuman.

## 10.6 Archive dan Delete

Archive dan Delete memiliki fungsi yang berbeda.

**Archive:**

- Pengumuman tidak lagi ditampilkan sebagai pengumuman aktif.
- Data tetap tersimpan di sistem.

**Delete:**

- Data pengumuman dihapus dari sistem.

---

# 11. Ringkasan Business Rules

Berikut adalah aturan bisnis utama yang telah disepakati:

| No | Business Rule |
|----|---------------|
| 1 | Mahasiswa dan Dosen dapat menjadi anggota perpustakaan. |
| 2 | Keanggotaan memerlukan persetujuan Administrator. |
| 3 | Mahasiswa dan Dosen memiliki aturan peminjaman yang sama. |
| 4 | Satu Judul Buku dapat memiliki banyak Eksemplar. |
| 5 | Satu Judul Buku dapat memiliki banyak Penulis. |
| 6 | Satu Judul Buku memiliki satu lokasi rak. |
| 7 | ISBN bersifat opsional. |
| 8 | Status publikasi Judul Buku adalah `Published` atau `Unpublished`. |
| 9 | Status Eksemplar adalah `Available` atau `Borrowed`. |
| 10 | Katalog hanya dapat diakses setelah pengguna login. |
| 11 | Peminjaman dimulai melalui website. |
| 12 | Pengguna tidak memilih Eksemplar secara langsung. |
| 13 | Sistem menentukan Eksemplar berdasarkan ketersediaan. |
| 14 | Maksimal 3 pengajuan peminjaman yang disetujui per hari. |
| 15 | Setiap buku dalam pengajuan diproses secara terpisah. |
| 16 | Penolakan peminjaman wajib disertai alasan. |
| 17 | Pengguna dapat membatalkan pengajuan yang belum diproses. |
| 18 | Masa peminjaman adalah 7 hari. |
| 19 | Pengembalian dilakukan secara fisik di perpustakaan. |
| 20 | Pengembalian dicatat oleh Administrator. |
| 21 | Pengguna yang terlambat tidak dapat mengajukan peminjaman baru. |
| 22 | Denda hanya dicatat dalam sistem pada MVP. |
| 23 | Perpanjangan peminjaman tidak termasuk MVP. |
| 24 | Repository MVP terdiri dari Skripsi, Tesis, dan Disertasi. |
| 25 | Semua file repository memerlukan persetujuan Administrator. |
| 26 | Akses file repository berlaku selama 7 hari setelah disetujui. |
| 27 | User dapat mengajukan kembali akses repository setelah ditolak. |
| 28 | Ukuran maksimum file repository adalah 100 MB. |
| 29 | Metadata repository harus diperiksa Administrator sebelum publikasi. |
| 30 | Semua pengumuman ditujukan kepada seluruh pengguna. |

---

# 12. Fitur yang Tidak Termasuk MVP

Fitur berikut tidak termasuk dalam versi MVP:

- QR Code untuk Eksemplar Buku.
- Perpanjangan peminjaman.
- Upload repository secara mandiri oleh Mahasiswa/Dosen.
- Sistem pembayaran denda.
- Perhitungan denda otomatis.
- Payment gateway.
- Segmentasi target pengumuman berdasarkan role.
- Waiting list buku yang sedang tidak tersedia.
- Download repository tanpa approval Administrator.

Fitur-fitur tersebut dapat dipertimbangkan pada fase pengembangan berikutnya.

---

# 13. Persetujuan Requirement

Dengan menyetujui dokumen ini, pihak client/stakeholder menyatakan bahwa:

1. Ruang lingkup sistem telah dipahami.
2. Modul utama telah sesuai dengan kebutuhan perpustakaan.
3. Alur utama sistem telah sesuai dengan proses bisnis yang diinginkan.
4. Business rules yang tercantum telah sesuai dengan kebijakan perpustakaan.
5. Fitur yang tidak termasuk MVP telah dipahami.
6. Dokumen ini dapat digunakan sebagai dasar untuk tahap perancangan sistem.

## Status Persetujuan

| Item | Status |
|------|--------|
| Requirement Review | ☐ Belum Review |
| Client Review | ☐ Belum Disetujui |
| Client Approval | ☐ Approved |
| Ready for System Design | ☐ Belum |

## Catatan Client

....................................................................................

....................................................................................

....................................................................................

## Persetujuan

**Pihak Client / Perwakilan Perpustakaan**

Nama: ..............................................................

Jabatan: ...........................................................

Tanggal: ............................................................

Tanda Tangan: ....................................................

---

**Developer**

Nama: ..............................................................

Tanggal: ............................................................

Tanda Tangan: ....................................................
