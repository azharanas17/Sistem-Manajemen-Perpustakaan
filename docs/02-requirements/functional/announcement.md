# Announcement Management

## 1. Overview

Announcement Management merupakan modul yang digunakan untuk mengelola dan menyampaikan informasi resmi perpustakaan kepada seluruh pengguna sistem.

Pengumuman dapat digunakan untuk menyampaikan:

- Informasi layanan perpustakaan.
- Perubahan jadwal layanan.
- Informasi kegiatan.
- Informasi kebijakan.
- Pemberitahuan penting lainnya.

Seluruh pengumuman pada MVP ditujukan kepada semua pengguna sistem.

---

## 2. Tujuan

Modul Announcement Management bertujuan untuk:

- Menyediakan media penyampaian informasi resmi perpustakaan.
- Memudahkan Administrator membuat dan mengelola pengumuman.
- Memastikan pengguna dapat mengetahui informasi terbaru perpustakaan.
- Mengatur periode publikasi pengumuman.
- Menyediakan pengelolaan arsip pengumuman tanpa harus menghapus data.

---

## 3. Aktor

### 3.1 Administrator

Administrator bertanggung jawab untuk mengelola pengumuman.

Administrator dapat:

- Membuat pengumuman.
- Mengubah pengumuman.
- Mengatur kategori pengumuman.
- Menentukan tanggal mulai pengumuman.
- Menentukan tanggal berakhir pengumuman.
- Menambahkan gambar atau lampiran apabila diperlukan.
- Menerbitkan pengumuman.
- Mengarsipkan pengumuman.
- Menghapus pengumuman.
- Melihat daftar pengumuman.
- Melihat detail pengumuman.

### 3.2 Mahasiswa

Mahasiswa dapat:

- Melihat daftar pengumuman.
- Membuka detail pengumuman.
- Membaca pengumuman yang sedang aktif.

### 3.3 Dosen

Dosen memiliki akses pengumuman yang sama dengan Mahasiswa.

Dosen dapat:

- Melihat daftar pengumuman.
- Membuka detail pengumuman.
- Membaca pengumuman yang sedang aktif.

---

## 4. Target Pengumuman

Pada MVP, seluruh pengumuman selalu ditujukan kepada:

**Semua pengguna sistem.**

Tidak terdapat mekanisme untuk menargetkan pengumuman hanya kepada:

- Mahasiswa.
- Dosen.
- Kelompok pengguna tertentu.

Dengan demikian, setiap pengumuman yang dipublikasikan akan tersedia untuk seluruh pengguna yang dapat mengakses sistem.

---

## 5. Announcement Information

Setiap pengumuman memiliki informasi yang digunakan untuk menampilkan konten kepada pengguna.

Informasi pengumuman meliputi:

- Judul.
- Isi pengumuman.
- Kategori.
- Tanggal mulai.
- Tanggal berakhir.
- Gambar atau lampiran apabila tersedia.
- Status pengumuman.

---

## 6. Category

Setiap pengumuman wajib memiliki kategori.

Kategori digunakan untuk membantu pengelompokan dan pengelolaan informasi.

Kategori dikelola oleh Administrator.

Administrator dapat:

- Membuat kategori.
- Mengubah kategori.
- Mengelola kategori yang digunakan oleh pengumuman.

Contoh kategori:

- Informasi.
- Kegiatan.
- Layanan.
- Akademik.
- Pengumuman Umum.

Daftar kategori di atas merupakan contoh dan dapat disesuaikan dengan kebutuhan perpustakaan.

---

## 7. Publication Period

Setiap pengumuman memiliki:

- Tanggal mulai.
- Tanggal berakhir.

Tanggal mulai menentukan kapan pengumuman mulai ditampilkan kepada pengguna.

Tanggal berakhir menentukan kapan periode publikasi pengumuman berakhir.

Pengumuman hanya dianggap aktif selama berada dalam periode publikasinya.

Contoh:

- Tanggal mulai: 17 Agustus 2026
- Tanggal berakhir: 24 Agustus 2026

Pengumuman aktif selama periode tersebut.

---

## 8. Announcement Status

Pengumuman memiliki status yang digunakan untuk mengelola siklus hidupnya.

Status utama:

- `Draft`
- `Published`
- `Archived`

### 8.1 Draft

Pengumuman masih dalam proses penyusunan dan belum ditampilkan kepada pengguna.

### 8.2 Published

Pengumuman telah diterbitkan dan dapat ditampilkan kepada pengguna sesuai periode publikasinya.

### 8.3 Archived

Pengumuman telah diarsipkan dan tidak lagi ditampilkan sebagai pengumuman aktif.

Data pengumuman tetap disimpan di dalam sistem.

---

## 9. Active Announcement

Pengumuman dapat ditampilkan kepada pengguna apabila memenuhi kondisi publikasi.

Pengumuman harus:

- Berstatus `Published`.
- Sudah mencapai tanggal mulai.
- Belum melewati tanggal berakhir.
- Tidak berstatus `Archived`.

Dengan demikian, pengumuman yang berada di luar periode publikasinya tidak ditampilkan sebagai pengumuman aktif.

---

## 10. Announcement Detail

Pengguna dapat membuka halaman detail pengumuman untuk membaca informasi secara lengkap.

Halaman detail menampilkan:

- Judul.
- Kategori.
- Isi pengumuman.
- Tanggal mulai.
- Tanggal berakhir.
- Gambar apabila tersedia.
- Lampiran apabila tersedia.

---

## 11. Image and Attachment

Pengumuman dapat memiliki gambar atau lampiran.

Gambar atau lampiran:

- Bersifat opsional.
- Tidak wajib disertakan ketika membuat pengumuman.
- Dapat digunakan untuk mendukung informasi yang disampaikan.

Pengumuman tetap dapat diterbitkan tanpa gambar atau lampiran.

---

## 12. Archive

Archive digunakan untuk menyembunyikan pengumuman dari daftar pengumuman aktif tanpa menghapus data dari sistem.

Ketika pengumuman diarsipkan:

- Pengumuman tidak lagi ditampilkan sebagai pengumuman aktif.
- Data pengumuman tetap tersimpan.
- Administrator masih dapat melihat data pengumuman yang telah diarsipkan.
- Pengumuman dapat digunakan sebagai riwayat informasi.

Archive berbeda dengan Delete.

---

## 13. Delete

Delete digunakan untuk menghapus pengumuman dari sistem.

Berbeda dengan Archive, Delete menghapus data pengumuman secara permanen.

Setelah pengumuman dihapus:

- Data pengumuman tidak lagi tersedia.
- Pengumuman tidak dapat ditampilkan kepada pengguna.
- Data tidak dianggap sebagai arsip pengumuman.

Administrator harus berhati-hati ketika menggunakan fungsi Delete karena data akan benar-benar dihapus.

---

## 14. Announcement Flow

Alur pengelolaan pengumuman:

1. Administrator membuat pengumuman.
2. Administrator mengisi judul dan isi.
3. Administrator memilih kategori.
4. Administrator menentukan tanggal mulai.
5. Administrator menentukan tanggal berakhir.
6. Administrator dapat menambahkan gambar atau lampiran.
7. Pengumuman disimpan sebagai `Draft`.
8. Administrator menerbitkan pengumuman.
9. Pengumuman menjadi `Published`.
10. Pengumuman ditampilkan kepada pengguna selama periode publikasi.
11. Setelah periode berakhir, pengumuman tidak lagi ditampilkan sebagai pengumuman aktif.
12. Administrator dapat mengarsipkan pengumuman.
13. Administrator dapat menghapus pengumuman apabila memang diperlukan.

---

## 15. Announcement Visibility

Pengguna hanya dapat melihat pengumuman yang tersedia untuk mereka.

Pada MVP, seluruh pengumuman memiliki target:

**Semua pengguna.**

Tidak terdapat segmentasi berdasarkan role.

Contoh:

- Pengumuman: "Perpustakaan Tutup pada 17 Agustus"
- Target: Semua pengguna
- Mahasiswa: Dapat melihat
- Dosen: Dapat melihat
- Administrator: Dapat melihat

---

## 16. Business Rules

| No | Aturan |
|----|--------|
| 1 | Pengumuman ditujukan kepada seluruh pengguna pada MVP. |
| 2 | Pengumuman tidak memiliki target audience khusus berdasarkan role. |
| 3 | Setiap pengumuman wajib memiliki kategori. |
| 4 | Setiap pengumuman wajib memiliki tanggal mulai. |
| 5 | Setiap pengumuman wajib memiliki tanggal berakhir. |
| 6 | Gambar atau lampiran bersifat opsional. |
| 7 | Pengumuman berstatus `Draft` tidak ditampilkan kepada pengguna. |
| 8 | Pengumuman berstatus `Published` ditampilkan sesuai periode publikasinya. |
| 9 | Ketika tanggal berakhir tercapai, status pengumuman otomatis berubah menjadi `Archived`. |
| 10 | Pengumuman berstatus `Archived` tidak ditampilkan sebagai pengumuman aktif. |
| 11 | Pengumuman `Archived` dapat dikembalikan menjadi `Published` oleh Administrator dengan memperbarui tanggal publikasi sesuai kebutuhan. |
| 12 | Archive mempertahankan data pengumuman di dalam sistem. |
| 13 | Delete menghapus data pengumuman secara permanen. |
| 14 | Delete wajib melalui konfirmasi Administrator sebelum data dihapus. |
| 15 | Administrator bertanggung jawab terhadap pengelolaan pengumuman. |
| 16 | Pengguna dapat membaca pengumuman yang sedang aktif. |

---

## 17. Features Outside MVP

Fitur berikut tidak termasuk dalam Announcement Management MVP:

- Target pengumuman berdasarkan Mahasiswa atau Dosen.
- Target pengumuman berdasarkan kelompok pengguna tertentu.
- Notifikasi email otomatis.
- Push notification.
- Notifikasi berdasarkan preferensi pengguna.
- Penjadwalan publikasi yang lebih kompleks.

Fitur tersebut dapat dipertimbangkan pada fase pengembangan berikutnya.

---

## 18. Acceptance Criteria

Modul Announcement Management dianggap memenuhi requirement apabila:

### Announcement

- [ ] Administrator dapat membuat pengumuman.
- [ ] Administrator dapat mengubah pengumuman.
- [ ] Administrator dapat menghapus pengumuman.
- [ ] Administrator dapat mengarsipkan pengumuman.
- [ ] Administrator dapat melihat pengumuman yang telah diarsipkan.

### Category

- [ ] Setiap pengumuman memiliki kategori.
- [ ] Administrator dapat mengelola kategori pengumuman.

### Publication Period

- [ ] Administrator dapat menentukan tanggal mulai.
- [ ] Administrator dapat menentukan tanggal berakhir.
- [ ] Pengumuman hanya ditampilkan selama periode publikasi.
- [ ] Pengumuman yang telah melewati tanggal berakhir tidak ditampilkan sebagai pengumuman aktif.

### Target Audience

- [ ] Setiap pengumuman ditujukan kepada semua pengguna.
- [ ] Sistem tidak membatasi pengumuman berdasarkan role pada MVP.

### Image and Attachment

- [ ] Administrator dapat menambahkan gambar apabila diperlukan.
- [ ] Administrator dapat menambahkan lampiran apabila diperlukan.
- [ ] Pengumuman dapat diterbitkan tanpa gambar atau lampiran.

### Status dan Archive

- [ ] Pengumuman berstatus `Draft` tidak ditampilkan kepada pengguna.
- [ ] Pengumuman berstatus `Published` ditampilkan selama periode publikasi.
- [ ] Sistem otomatis mengubah status menjadi `Archived` ketika tanggal berakhir tercapai.
- [ ] Pengumuman `Archived` tidak ditampilkan sebagai pengumuman aktif.
- [ ] Administrator dapat mengubah pengumuman `Archived` menjadi `Published`.
- [ ] Administrator harus memperbarui tanggal publikasi sebelum menerbitkan kembali pengumuman `Archived`.
- [ ] Data pengumuman tetap tersimpan setelah status berubah menjadi `Archived`.

### Delete

- [ ] Administrator dapat menghapus pengumuman.
- [ ] Sistem meminta konfirmasi sebelum penghapusan permanen.
- [ ] Setelah dikonfirmasi, data pengumuman dihapus secara permanen.

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