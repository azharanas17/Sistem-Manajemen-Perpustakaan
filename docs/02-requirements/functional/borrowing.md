# Borrowing Management

## 1. Overview

Borrowing Management merupakan modul yang digunakan untuk mengelola proses peminjaman buku oleh anggota perpustakaan, mulai dari pengajuan peminjaman, proses persetujuan oleh Administrator, pengambilan buku, hingga pengembalian buku secara fisik di perpustakaan.

Modul ini digunakan oleh:

- Administrator
- Mahasiswa
- Dosen

Mahasiswa dan Dosen memiliki aturan peminjaman yang sama.

---

# 2. Tujuan

Modul Borrowing Management bertujuan untuk:

- Memudahkan anggota mengajukan peminjaman buku secara online.
- Membantu Administrator memproses pengajuan peminjaman.
- Menampilkan status pengajuan secara jelas kepada anggota.
- Membantu Administrator mencatat pengambilan buku.
- Membantu Administrator mencatat pengembalian buku.
- Menjaga informasi ketersediaan Eksemplar Buku tetap akurat.
- Mencatat keterlambatan dan denda apabila terjadi.

---

# 3. Aktor

## 3.1 Administrator

Administrator merupakan pustakawan yang bertanggung jawab memproses aktivitas peminjaman.

Administrator dapat:

- Melihat pengajuan peminjaman.
- Memeriksa detail pengajuan.
- Menyetujui pengajuan.
- Menolak pengajuan.
- Memberikan alasan penolakan.
- Mencatat pengambilan buku.
- Mencatat pengembalian buku.
- Melihat riwayat peminjaman.
- Mencatat keterlambatan.
- Mencatat denda.

## 3.2 Mahasiswa

Mahasiswa dapat:

- Melihat katalog buku.
- Mengajukan peminjaman.
- Melihat status pengajuan.
- Membatalkan pengajuan yang belum diproses.
- Melihat informasi peminjaman.
- Melihat riwayat peminjaman.

## 3.3 Dosen

Dosen memiliki hak dan aturan peminjaman yang sama dengan Mahasiswa.

Dosen dapat:

- Melihat katalog buku.
- Mengajukan peminjaman.
- Melihat status pengajuan.
- Membatalkan pengajuan yang belum diproses.
- Melihat informasi peminjaman.
- Melihat riwayat peminjaman.

---

# 4. Borrowing Flow

Alur utama peminjaman adalah:

1. Anggota memilih buku dari katalog.
2. Anggota mengajukan peminjaman.
3. Sistem memeriksa kelayakan pengajuan.
4. Pengajuan masuk ke Administrator.
5. Administrator melakukan review.
6. Administrator menyetujui atau menolak setiap buku dalam pengajuan.
7. Jika disetujui, anggota datang ke perpustakaan untuk mengambil buku.
8. Administrator mencatat bahwa buku telah diambil.
9. Anggota mengembalikan buku secara fisik ke perpustakaan.
10. Administrator mencatat pengembalian.
11. Status Eksemplar kembali menjadi `Available`.

---

# 5. Pengajuan Peminjaman

## 5.1 Pemilihan Buku

Anggota memilih Judul Buku yang ingin dipinjam melalui katalog.

Anggota tidak memilih Eksemplar tertentu.

Contoh:

- Judul Buku: Laravel untuk Pemula
- Eksemplar 001: `Borrowed`
- Eksemplar 002: `Available`
- Eksemplar 003: `Available`

Anggota cukup memilih Judul Buku "Laravel untuk Pemula".

Sistem akan menentukan Eksemplar yang digunakan berdasarkan ketersediaan.

## 5.2 Buku Tidak Tersedia

Jika tidak terdapat Eksemplar dengan status `Available`, buku tidak dapat diajukan untuk peminjaman.

Sistem tidak menyediakan waiting list dalam MVP.

## 5.3 Satu Pengajuan

Satu pengajuan peminjaman dapat berisi beberapa Judul Buku.

Contoh:

- Laravel untuk Pemula
- Database Design
- Python Fundamental

Setiap Judul Buku diproses secara terpisah oleh Administrator.

---

# 6. Validasi Pengajuan

Sistem melakukan validasi sebelum pengajuan dapat dibuat.

Validasi meliputi:

- Anggota harus memiliki status keanggotaan `Active`.
- Judul Buku harus berstatus `Published`.
- Judul Buku harus memiliki Eksemplar dengan status `Available`.
- Anggota tidak sedang memiliki keterlambatan yang menghalangi peminjaman baru.
- Anggota belum mencapai batas maksimal 3 pengajuan dengan status `Pending` atau `Approved` pada saat yang sama.

Jika kondisi tidak terpenuhi, pengajuan tidak dapat dibuat.

---

# 7. Batas Peminjaman

Anggota dapat memiliki maksimal 3 pengajuan aktif pada saat yang sama.

Pengajuan aktif adalah pengajuan dengan status:

- `Pending`
- `Approved`

Pengajuan dengan status `Rejected` atau `Cancelled` tidak dihitung sebagai pengajuan aktif.

Jika anggota telah memiliki 3 pengajuan aktif, anggota tidak dapat membuat pengajuan baru sampai salah satu pengajuan tersebut tidak lagi aktif.

## 7.1 Batas Pengajuan Pending

Anggota tidak dapat memiliki lebih dari 3 pengajuan dengan status `Pending` atau kombinasi `Pending` dan `Approved` yang secara keseluruhan mencapai batas 3 pengajuan aktif.

Jika anggota telah memiliki 3 pengajuan aktif, anggota harus menunggu sampai salah satu pengajuan tersebut tidak lagi aktif.

Jika pengajuan `Pending` berubah menjadi:

- `Rejected` → slot pengajuan kembali tersedia.
- `Approved` → pengajuan tetap dihitung sebagai pengajuan aktif.

## 7.2 Pengajuan Approved

Pengajuan dengan status `Approved` tetap dihitung sebagai pengajuan aktif sampai buku dikembalikan.

Setelah buku dikembalikan dan peminjaman selesai, pengajuan tersebut tidak lagi dihitung sebagai pengajuan aktif.

Contoh:

- Buku A → `Approved`
- Buku B → `Approved`
- Buku C → `Pending`

Total pengajuan aktif = 3.

Anggota tidak dapat membuat pengajuan baru sampai salah satu pengajuan tersebut tidak lagi aktif.

---

# 8. Status Pengajuan

Pengajuan peminjaman memiliki status yang menggambarkan prosesnya.

Status utama:

- `Pending`
- `Approved`
- `Rejected`
- `Cancelled`

## 8.1 Pending

Pengajuan telah dibuat tetapi belum diproses oleh Administrator.

## 8.2 Approved

Administrator menyetujui peminjaman.

## 8.3 Rejected

Administrator menolak peminjaman.

Penolakan wajib disertai alasan.

## 8.4 Cancelled

Anggota membatalkan pengajuan sebelum diproses oleh Administrator.

---

# 9. Persetujuan Administrator

Administrator dapat memproses setiap Judul Buku dalam pengajuan secara terpisah.

Contoh:

- Buku A → `Approved`
- Buku B → `Rejected`
- Buku C → `Approved`

Dengan demikian, hasil pemrosesan tidak harus sama untuk seluruh buku dalam satu pengajuan.

---

# 10. Penolakan Peminjaman

Jika Administrator menolak suatu pengajuan, Administrator wajib memberikan alasan penolakan.

Contoh alasan:

- Buku tidak tersedia.
- Data pengajuan tidak sesuai.
- Anggota memiliki masalah peminjaman sebelumnya.
- Alasan lain sesuai kebijakan perpustakaan.

Alasan penolakan dapat dilihat oleh anggota pada detail pengajuan.

---

# 11. Pembatalan Pengajuan

Anggota dapat membatalkan pengajuan selama status masih:

`Pending`

Setelah Administrator memproses pengajuan, anggota tidak dapat membatalkannya melalui sistem.

Tujuan pembatalan:

- Mempercepat pembaruan status.
- Membebaskan buku agar dapat digunakan oleh anggota lain.
- Menghindari pengajuan yang tidak lagi dibutuhkan.

---

# 12. Pengambilan Buku

Setelah pengajuan disetujui, anggota harus datang ke perpustakaan untuk mengambil buku secara fisik.

Administrator melakukan konfirmasi pengambilan melalui sistem.

Setelah buku diambil:

- Peminjaman menjadi aktif.
- Eksemplar memiliki status `Borrowed`.
- Sistem mencatat tanggal pengambilan.
- Sistem menentukan tanggal jatuh tempo berdasarkan masa peminjaman.

---

# 13. Masa Peminjaman

Masa peminjaman buku adalah:

**7 hari.**

Tanggal jatuh tempo dihitung berdasarkan tanggal pengambilan buku.

Contoh:

- Tanggal Pengambilan: 17 Agustus 2026
- Masa Peminjaman: 7 hari
- Tanggal Jatuh Tempo: 24 Agustus 2026

---

# 14. Pengembalian Buku

Pengembalian dilakukan secara fisik di perpustakaan.

Anggota tidak perlu mengajukan pengembalian melalui website.

Proses:

1. Anggota datang ke perpustakaan.
2. Anggota menyerahkan buku.
3. Administrator menerima buku.
4. Administrator mencatat pengembalian.
5. Sistem mencatat tanggal pengembalian.
6. Status peminjaman menjadi selesai.
7. Status Eksemplar menjadi `Available`.

---

# 15. Keterlambatan

Sistem dapat mengidentifikasi peminjaman yang melewati tanggal jatuh tempo.

Jika anggota terlambat mengembalikan buku:

- Peminjaman dicatat sebagai terlambat.
- Informasi keterlambatan disimpan.
- Anggota tidak dapat mengajukan peminjaman baru sampai kewajiban peminjaman sebelumnya diselesaikan.

---

# 16. Denda

Perpustakaan menerapkan denda untuk keterlambatan.

Namun, sistem MVP hanya menangani pencatatan denda.

Sistem tidak melakukan:

- Perhitungan denda otomatis.
- Pembayaran denda.
- Pembayaran online.
- Integrasi payment gateway.
- Pelunasan denda melalui sistem.

Informasi denda dapat dicatat oleh Administrator.

Informasi yang dapat dicatat meliputi:

- Peminjaman terkait.
- Jumlah denda.
- Status denda.
- Catatan.
- Tanggal pencatatan.

---

# 17. Perpanjangan Peminjaman

Fitur perpanjangan peminjaman tidak termasuk dalam MVP.

Jika anggota ingin meminjam buku yang sama setelah buku dikembalikan, anggota harus melakukan pengajuan peminjaman baru melalui flow peminjaman yang normal.

Alur:

1. Peminjaman berlangsung.
2. Buku dikembalikan.
3. Buku menjadi `Available`.
4. Jika ingin meminjam kembali, anggota membuat pengajuan baru.

---

# 18. Riwayat Peminjaman

Anggota dapat melihat riwayat peminjaman mereka.

Informasi yang dapat ditampilkan antara lain:

- Judul Buku.
- Tanggal pengajuan.
- Status pengajuan.
- Tanggal persetujuan.
- Tanggal pengambilan.
- Tanggal jatuh tempo.
- Tanggal pengembalian.
- Informasi keterlambatan apabila ada.
- Informasi denda apabila ada.

Administrator dapat melihat riwayat peminjaman seluruh anggota.

---

# 19. Ketersediaan Eksemplar

Status Eksemplar mengikuti aktivitas peminjaman.

## 19.1 Available

Eksemplar tersedia untuk dipinjam.

## 19.2 Borrowed

Eksemplar sedang berada dalam status peminjaman.

Perubahan status secara umum:

`Available → Borrowed → Available`

Status berubah menjadi `Borrowed` ketika buku telah diambil oleh anggota.

Status kembali menjadi `Available` ketika Administrator mencatat pengembalian buku.

---

# 20. Aturan Bisnis

| No | Aturan |
|----|--------|
| 1 | Hanya anggota aktif yang dapat mengajukan peminjaman. |
| 2 | Mahasiswa dan Dosen memiliki aturan peminjaman yang sama. |
| 3 | Anggota memilih Judul Buku, bukan Eksemplar tertentu. |
| 4 | Sistem menentukan Eksemplar berdasarkan ketersediaan. |
| 5 | Buku harus memiliki Eksemplar `Available` untuk dapat diajukan. |
| 6 | Buku yang tidak tersedia tidak dapat diajukan. |
| 7 | Waiting list tidak termasuk MVP. |
| 8 | Satu pengajuan dapat berisi beberapa Judul Buku. |
| 9 | Setiap buku dalam pengajuan diproses secara terpisah. |
| 10 | Maksimal 3 pengajuan peminjaman yang dapat berada dalam status `Pending` atau `Approved` pada saat yang sama. |
| 11 | Pengajuan yang ditolak tidak dihitung dalam batas 3 buku. |
| 12 | Penolakan wajib disertai alasan. |
| 13 | Anggota dapat membatalkan pengajuan yang masih `Pending`. |
| 14 | Anggota tidak dapat membatalkan pengajuan yang sudah diproses. |
| 15 | Masa peminjaman adalah 7 hari. |
| 16 | Pengambilan buku dilakukan secara fisik di perpustakaan. |
| 17 | Pengembalian dilakukan secara fisik di perpustakaan. |
| 18 | Pengembalian dicatat oleh Administrator. |
| 19 | Anggota yang memiliki keterlambatan tidak dapat mengajukan peminjaman baru. |
| 20 | Denda hanya dicatat dalam sistem pada MVP. |
| 21 | Perpanjangan peminjaman tidak termasuk MVP. |
| 22 | Untuk meminjam kembali buku yang sama, anggota harus mengikuti flow peminjaman baru. |
| 23 | Setelah pengembalian dicatat, status Eksemplar kembali menjadi `Available`. |

---

# 21. Fitur di Luar MVP

Fitur berikut tidak termasuk dalam MVP:

- Waiting list buku.
- Perpanjangan peminjaman.
- Pembayaran denda secara online.
- Perhitungan denda otomatis.
- Payment gateway.
- Pengembalian melalui pengajuan online.
- Pemilihan Eksemplar secara manual oleh anggota.

Fitur tersebut dapat dipertimbangkan pada fase pengembangan berikutnya.

---

# 22. Acceptance Criteria

Modul Borrowing Management dianggap memenuhi requirement apabila:

## Pengajuan

- [ ] Anggota aktif dapat mengajukan peminjaman.
- [ ] Anggota dapat memilih beberapa Judul Buku dalam satu pengajuan.
- [ ] Anggota tidak perlu memilih Eksemplar.
- [ ] Sistem hanya mengizinkan buku dengan Eksemplar `Available`.
- [ ] Buku yang tidak tersedia tidak dapat diajukan.

## Approval

- [ ] Administrator dapat melihat pengajuan.
- [ ] Administrator dapat menyetujui setiap buku secara terpisah.
- [ ] Administrator dapat menolak setiap buku secara terpisah.
- [ ] Alasan wajib diberikan ketika pengajuan ditolak.
- [ ] Anggota dapat melihat hasil keputusan Administrator.

## Pembatalan

- [ ] Anggota dapat membatalkan pengajuan berstatus `Pending`.
- [ ] Anggota tidak dapat membatalkan pengajuan yang telah diproses.

## Pengambilan

- [ ] Administrator dapat mencatat pengambilan buku.
- [ ] Sistem mencatat tanggal pengambilan.
- [ ] Sistem menentukan tanggal jatuh tempo 7 hari setelah pengambilan.
- [ ] Status Eksemplar berubah menjadi `Borrowed`.

## Pengembalian

- [ ] Administrator dapat mencatat pengembalian.
- [ ] Sistem mencatat tanggal pengembalian.
- [ ] Status Eksemplar berubah kembali menjadi `Available`.
- [ ] Anggota tidak perlu membuat pengajuan pengembalian.

## Keterlambatan

- [ ] Sistem dapat mengidentifikasi peminjaman yang melewati tanggal jatuh tempo.
- [ ] Informasi keterlambatan dapat dicatat.
- [ ] Anggota yang terlambat tidak dapat membuat pengajuan peminjaman baru.

## Denda

- [ ] Administrator dapat mencatat denda.
- [ ] Sistem menyimpan informasi denda.
- [ ] Sistem tidak melakukan pembayaran atau perhitungan denda otomatis.

## Batas Peminjaman

- [ ] Sistem membatasi maksimal 3 pengajuan aktif pada saat yang sama.
- [ ] Pengajuan aktif terdiri dari status `Pending` dan `Approved`.
- [ ] Pengajuan `Rejected` tidak dihitung sebagai pengajuan aktif.
- [ ] Pengajuan `Cancelled` tidak dihitung sebagai pengajuan aktif.
- [ ] Anggota tidak dapat membuat pengajuan baru ketika sudah memiliki 3 pengajuan aktif.
- [ ] Ketika pengajuan `Pending` berubah menjadi `Rejected`, slot pengajuan kembali tersedia.
- [ ] Ketika pengajuan `Pending` berubah menjadi `Approved`, pengajuan tetap dihitung sebagai pengajuan aktif.
- [ ] Setelah buku dikembalikan dan peminjaman selesai, slot pengajuan kembali tersedia.

## Riwayat

- [ ] Anggota dapat melihat riwayat peminjaman sendiri.
- [ ] Administrator dapat melihat riwayat peminjaman seluruh anggota.

---

# 23. Status Requirement

| Item | Status |
|------|--------|
| Business Requirement | Resolved |
| Functional Requirement | Resolved |
| Business Rules | Resolved |
| Acceptance Criteria | Defined |
| Client Review | Pending |
| Client Approval | Pending |