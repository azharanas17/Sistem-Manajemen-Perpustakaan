# Librarian Contact

## 1. Overview

Librarian Contact merupakan fitur yang menyediakan informasi kontak pustakawan agar pengguna dapat menghubungi layanan perpustakaan secara langsung melalui media komunikasi di luar sistem.

Pada MVP, sistem tidak menyediakan fitur chat internal antara pengguna dan pustakawan.

Komunikasi dilakukan melalui media yang disediakan oleh perpustakaan, seperti WhatsApp, email, atau media komunikasi lainnya.

---

## 2. Tujuan

Fitur Librarian Contact bertujuan untuk:

- Memudahkan pengguna menemukan informasi kontak pustakawan.
- Menyediakan jalur komunikasi antara pengguna dan pustakawan.
- Menghindari kompleksitas pembangunan sistem chat internal pada MVP.
- Memungkinkan pengguna menghubungi pustakawan melalui media komunikasi yang sudah digunakan oleh perpustakaan.

---

## 3. Aktor

### 3.1 Administrator

Administrator bertanggung jawab untuk mengelola informasi kontak pustakawan.

Administrator dapat:

- Menambahkan informasi kontak.
- Mengubah informasi kontak.
- Menghapus informasi kontak yang tidak lagi digunakan.
- Mengatur informasi kontak yang ditampilkan kepada pengguna.

### 3.2 Mahasiswa

Mahasiswa dapat:

- Melihat informasi kontak pustakawan.
- Memilih media komunikasi yang tersedia.
- Menghubungi pustakawan melalui media komunikasi tersebut.

### 3.3 Dosen

Dosen dapat:

- Melihat informasi kontak pustakawan.
- Memilih media komunikasi yang tersedia.
- Menghubungi pustakawan melalui media komunikasi tersebut.

### 3.4 Guest

Guest dapat melihat informasi kontak pustakawan tanpa harus memiliki akun atau login ke dalam sistem.

Guest dapat menggunakan informasi kontak tersebut untuk menghubungi pustakawan melalui media komunikasi yang tersedia.

---

## 4. Contact Information

MVP hanya menyediakan satu kontak utama pustakawan/perpustakaan.

Informasi kontak utama dapat meliputi:

- Nama atau label layanan.
- Nomor WhatsApp.
- Link WhatsApp.
- Alamat email.
- Jam layanan apabila diperlukan.

Tidak semua jenis informasi kontak wajib tersedia.

Informasi yang ditampilkan mengikuti media komunikasi yang disediakan oleh perpustakaan.

---

## 5. WhatsApp Contact

WhatsApp merupakan salah satu media komunikasi yang dapat digunakan untuk menghubungi pustakawan.

Apabila nomor WhatsApp tersedia, sistem dapat menyediakan tombol atau link yang memungkinkan pengguna membuka WhatsApp secara langsung.

Contoh:

> Hubungi Pustakawan melalui WhatsApp

Ketika pengguna memilih kontak tersebut, sistem mengarahkan pengguna ke WhatsApp atau aplikasi/web WhatsApp yang tersedia pada perangkat pengguna.

Percakapan selanjutnya berlangsung di luar sistem perpustakaan.

---

## 6. Email Contact

Apabila perpustakaan menyediakan alamat email pustakawan, sistem dapat menampilkannya sebagai informasi kontak.

Pengguna dapat menggunakan alamat email tersebut untuk menghubungi pustakawan melalui layanan email.

Percakapan email berlangsung di luar sistem perpustakaan.

---

## 7. Contact Management

Informasi kontak dikelola oleh Administrator.

Administrator dapat:

1. Menambahkan informasi kontak.
2. Mengubah informasi kontak.
3. Menghapus informasi kontak yang sudah tidak digunakan.
4. Menentukan informasi kontak yang ditampilkan kepada pengguna.

Perubahan informasi kontak dapat dilakukan tanpa mengubah kode aplikasi.

---

## 8. Contact Visibility

Informasi kontak pustakawan dapat diakses oleh:

- Guest.
- Mahasiswa.
- Dosen.
- Administrator.

Guest tidak perlu login untuk melihat informasi kontak.

Informasi kontak yang ditampilkan kepada Guest dan pengguna yang telah login dapat sama.

---

## 9. Communication Outside the System

Sistem hanya menyediakan informasi dan akses menuju media komunikasi pustakawan.

Sistem tidak menyimpan percakapan antara pengguna dan pustakawan.

Komunikasi berlangsung sepenuhnya pada platform yang digunakan, seperti:

- WhatsApp.
- Email.
- Media komunikasi lainnya yang disediakan perpustakaan.

MVP tidak menyediakan:

- Chat internal.
- Riwayat percakapan.
- Status pesan.
- Notifikasi chat.
- Attachment dalam chat.
- Online/offline status pustakawan.

---

## 10. Librarian Contact Flow

Alur penggunaan fitur:

1. Guest atau pengguna membuka halaman kontak pustakawan.
2. Sistem menampilkan informasi kontak yang tersedia.
3. Pengguna memilih media komunikasi.
4. Sistem mengarahkan pengguna ke media komunikasi tersebut apabila berupa link atau action.
5. Pengguna menghubungi pustakawan melalui media tersebut.
6. Komunikasi berlangsung di luar sistem perpustakaan.

---

## 11. Business Rules

| No | Aturan |
|----|--------|
| 1 | MVP hanya menyediakan satu kontak utama pustakawan/perpustakaan. |
| 2 | Sistem tidak menyediakan pengelolaan beberapa kontak pustakawan pada MVP. |
| 3 | Sistem tidak menyediakan fitur chat internal antara pengguna dan pustakawan. |
| 4 | Informasi kontak dapat dilihat oleh Guest. |
| 5 | Informasi kontak dapat dilihat oleh Mahasiswa dan Dosen. |
| 6 | Administrator bertanggung jawab mengelola kontak utama. |
| 7 | Nomor WhatsApp dapat ditampilkan apabila disediakan oleh perpustakaan. |
| 8 | Alamat email dapat ditampilkan apabila disediakan oleh perpustakaan. |
| 9 | Komunikasi antara pengguna dan pustakawan berlangsung di luar sistem. |
| 10 | Sistem tidak menyimpan riwayat percakapan pengguna dengan pustakawan. |
| 11 | Informasi kontak dapat diperbarui oleh Administrator tanpa perubahan kode aplikasi. |

---

## 12. Features Outside MVP

Fitur berikut tidak termasuk dalam MVP:

- Internal chat antara pengguna dan pustakawan.
- Chat history.
- Real-time messaging.
- Chat notification.
- File attachment dalam chat.
- Online/offline status pustakawan.
- Typing indicator.
- Chat assignment kepada pustakawan tertentu.
- Conversation management.

Fitur tersebut dapat dipertimbangkan pada fase pengembangan berikutnya.

---

## 13. Acceptance Criteria

Modul Librarian Contact dianggap memenuhi requirement apabila:

### Contact Information

- [ ] Sistem dapat menampilkan informasi kontak pustakawan.
- [ ] Administrator dapat menambahkan informasi kontak.
- [ ] Administrator dapat mengubah informasi kontak.
- [ ] Administrator dapat menghapus informasi kontak yang tidak digunakan.
- [ ] Informasi kontak dapat diperbarui tanpa perubahan kode aplikasi.

### User Access

- [ ] Guest dapat melihat informasi kontak pustakawan.
- [ ] Mahasiswa dapat melihat informasi kontak pustakawan.
- [ ] Dosen dapat melihat informasi kontak pustakawan.
- [ ] Administrator dapat melihat informasi kontak pustakawan.

### WhatsApp

- [ ] Nomor WhatsApp dapat ditampilkan apabila tersedia.
- [ ] Pengguna dapat memilih link atau tombol WhatsApp apabila tersedia.
- [ ] Pengguna diarahkan ke WhatsApp untuk melakukan komunikasi.

### Email

- [ ] Alamat email dapat ditampilkan apabila tersedia.
- [ ] Pengguna dapat menggunakan alamat email tersebut untuk menghubungi pustakawan.

### Communication

- [ ] Sistem tidak menyediakan chat internal pada MVP.
- [ ] Sistem tidak menyimpan riwayat percakapan.
- [ ] Komunikasi berlangsung melalui media eksternal yang disediakan perpustakaan.

---

## 14. Status Requirement

| Item | Status |
|------|--------|
| Business Requirement | Resolved |
| Functional Requirement | Resolved |
| Business Rules | Defined |
| Acceptance Criteria | Defined |
| Client Review | Pending |
| Client Approval | Pending |