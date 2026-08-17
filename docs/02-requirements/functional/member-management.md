# Member Management

## 1. Overview

Member Management merupakan modul yang digunakan untuk mengelola data keanggotaan pengguna perpustakaan.

Modul ini menangani proses pendaftaran anggota, verifikasi dan persetujuan keanggotaan, pengelolaan data anggota, serta status keanggotaan.

User dan Member merupakan dua konsep yang berbeda.

- **User** merupakan akun yang digunakan untuk mengakses sistem.
- **Member** merupakan status dan data keanggotaan seseorang pada perpustakaan.

Dengan demikian, seseorang dapat memiliki akun pada sistem tetapi belum menjadi anggota aktif perpustakaan.

---

## 2. Tujuan

Modul Member Management bertujuan untuk:

- Mengelola data anggota perpustakaan.
- Menyediakan proses pendaftaran anggota secara online.
- Memungkinkan Administrator melakukan verifikasi pendaftaran.
- Menentukan status keanggotaan.
- Menyimpan informasi anggota secara terstruktur.
- Menjadi dasar validasi akses terhadap layanan perpustakaan seperti peminjaman.

---

## 3. Aktor

### 3.1 Administrator

Administrator merupakan pustakawan yang bertanggung jawab mengelola data keanggotaan.

Administrator dapat:

- Melihat daftar pendaftaran anggota.
- Melihat detail data anggota.
- Memeriksa data pendaftaran.
- Menyetujui pendaftaran anggota.
- Menolak pendaftaran anggota.
- Melihat daftar anggota aktif.
- Melihat riwayat status keanggotaan.
- Mengubah data anggota apabila diperlukan.
- Mengelola data anggota sesuai kewenangan Administrator.

### 3.2 Mahasiswa

Mahasiswa dapat:

- Melakukan pendaftaran keanggotaan.
- Melihat status pendaftaran.
- Melihat informasi keanggotaan setelah disetujui.
- Menggunakan layanan perpustakaan sesuai hak akses sebagai anggota aktif.

### 3.3 Dosen

Dosen dapat:

- Melakukan pendaftaran keanggotaan.
- Melihat status pendaftaran.
- Melihat informasi keanggotaan setelah disetujui.
- Menggunakan layanan perpustakaan sesuai hak akses sebagai anggota aktif.

---

## 4. User dan Member

User dan Member merupakan konsep yang berbeda.

### User

User merupakan akun yang digunakan untuk:

- Login ke sistem.
- Mengakses fitur sesuai role.
- Memiliki identitas akun pada sistem.

### Member

Member merupakan data keanggotaan perpustakaan yang memiliki status keanggotaan.

Hubungan konseptual:

```text
User
  │
  └── Member
       └── Membership Status
```

Tidak semua User harus langsung menjadi anggota aktif.

Contohnya:

- User baru mendaftar → Member `Pending`
- Pendaftaran disetujui → Member `Active`
- Pendaftaran ditolak → Member `Rejected`

---

## 5. Member Type

Pada MVP terdapat dua jenis anggota yang dapat menggunakan layanan peminjaman:

- Mahasiswa
- Dosen

Mahasiswa dan Dosen memiliki aturan peminjaman yang sama.

Tidak terdapat perbedaan batas peminjaman antara Mahasiswa dan Dosen pada MVP.

---

## 6. Registration

Pendaftaran anggota dilakukan secara online melalui sistem.

Alur pendaftaran:

1. User mengisi formulir pendaftaran.
2. Sistem menyimpan data pendaftaran.
3. Status keanggotaan menjadi `Pending`.
4. Administrator memeriksa data pendaftaran.
5. Administrator dapat menyetujui atau menolak pendaftaran.
6. Jika disetujui, status menjadi `Active`.
7. Jika ditolak, status menjadi `Rejected`.

---

## 7. Membership Status

Status keanggotaan pada MVP terdiri dari:

- `Pending`
- `Active`
- `Rejected`

### 7.1 Pending

Status `Pending` menunjukkan bahwa pendaftaran anggota telah dikirim tetapi belum diproses oleh Administrator.

Anggota dengan status `Pending` belum dapat menggunakan layanan yang mensyaratkan keanggotaan aktif, termasuk peminjaman buku.

### 7.2 Active

Status `Active` menunjukkan bahwa pendaftaran anggota telah disetujui oleh Administrator.

Anggota dengan status `Active` dapat menggunakan layanan perpustakaan sesuai hak aksesnya.

Anggota `Active` dapat mengajukan peminjaman buku.

### 7.3 Rejected

Status `Rejected` menunjukkan bahwa pendaftaran anggota ditolak oleh Administrator.

Anggota dengan status `Rejected` tidak dapat menggunakan layanan yang mensyaratkan keanggotaan aktif.

---

## 8. Membership Approval

Administrator bertanggung jawab melakukan verifikasi pendaftaran anggota.

Administrator dapat:

- Menyetujui pendaftaran.
- Menolak pendaftaran.

Alur status:

```text
Pending
   │
   ├── Active
   │
   └── Rejected
```

Tidak terdapat status `Suspended` dalam MVP.

---

## 9. Active Member

Hanya anggota dengan status `Active` yang dapat menggunakan layanan peminjaman buku.

Sebelum membuat pengajuan peminjaman, sistem harus memastikan:

- User memiliki data Member.
- Status Member adalah `Active`.

Jika status Member bukan `Active`, pengajuan peminjaman tidak dapat dibuat.

---

## 10. Member Data

Data anggota dapat meliputi:

- Nama lengkap.
- Email.
- Nomor identitas.
- Jenis anggota.
- Nomor telepon.
- Informasi akademik yang diperlukan.
- Status keanggotaan.
- Tanggal pendaftaran.
- Tanggal persetujuan.

Data final yang diwajibkan mengikuti kebutuhan formulir dan kebijakan perpustakaan.

---

## 11. Member Data Management

Administrator dapat mengelola data anggota.

Pengelolaan meliputi:

- Melihat data anggota.
- Melihat detail anggota.
- Memperbarui data anggota.
- Memeriksa status anggota.

Perubahan data harus dilakukan dengan tetap mempertahankan integritas data keanggotaan.

---

## 12. Registration Flow

Alur pendaftaran anggota:

```text
User
  ↓
Mengisi Form Pendaftaran
  ↓
Submit
  ↓
Pending
  ↓
Administrator Review
  ├── Approve → Active
  └── Reject  → Rejected
```

---

## 13. Relationship with Borrowing

Member Management berhubungan langsung dengan Borrowing Management.

Hanya anggota `Active` yang dapat membuat pengajuan peminjaman.

Selain status keanggotaan, pengajuan peminjaman juga harus memenuhi aturan lain yang ditentukan oleh modul Borrowing Management.

Contoh:

- Anggota tidak memiliki keterlambatan yang menghalangi peminjaman.
- Tidak melebihi batas pengajuan yang ditentukan.
- Buku tersedia.

---

## 14. Business Rules

| No | Aturan |
|----|--------|
| 1 | User dan Member merupakan konsep yang berbeda. |
| 2 | Jenis anggota pada MVP terdiri dari Mahasiswa dan Dosen. |
| 3 | Mahasiswa dan Dosen memiliki aturan peminjaman yang sama. |
| 4 | Pendaftaran baru memiliki status `Pending`. |
| 5 | Administrator dapat menyetujui pendaftaran menjadi `Active`. |
| 6 | Administrator dapat menolak pendaftaran menjadi `Rejected`. |
| 7 | Tidak terdapat status `Suspended` dalam MVP. |
| 8 | Hanya Member dengan status `Active` yang dapat mengajukan peminjaman. |
| 9 | Member dengan status `Pending` tidak dapat mengajukan peminjaman. |
| 10 | Member dengan status `Rejected` tidak dapat mengajukan peminjaman. |
| 11 | Administrator bertanggung jawab melakukan approval keanggotaan. |
| 12 | Perbedaan aturan peminjaman antara Mahasiswa dan Dosen tidak diterapkan pada MVP. |

---

## 15. Features Outside MVP

Fitur berikut tidak termasuk dalam MVP:

- Status `Suspended`.
- Perbedaan kebijakan peminjaman antara Mahasiswa dan Dosen.
- Membership tier atau level keanggotaan.
- Membership renewal otomatis.
- Integrasi SSO.
- Sinkronisasi otomatis dengan sistem akademik.
- Integrasi kartu anggota fisik atau digital khusus.

Fitur tersebut dapat dipertimbangkan pada fase pengembangan berikutnya.

---

## 16. Acceptance Criteria

Modul Member Management dianggap memenuhi requirement apabila:

### Registration

- [ ] User dapat melakukan pendaftaran keanggotaan.
- [ ] Pendaftaran baru memiliki status `Pending`.
- [ ] Administrator dapat melihat pendaftaran anggota.
- [ ] Administrator dapat memeriksa data pendaftaran.
- [ ] Administrator dapat menyetujui pendaftaran.
- [ ] Administrator dapat menolak pendaftaran.

### Membership Status

- [ ] Sistem memiliki status `Pending`.
- [ ] Sistem memiliki status `Active`.
- [ ] Sistem memiliki status `Rejected`.
- [ ] Sistem tidak menggunakan status `Suspended` pada MVP.

### Active Member

- [ ] Hanya anggota `Active` yang dapat mengajukan peminjaman.
- [ ] Anggota `Pending` tidak dapat mengajukan peminjaman.
- [ ] Anggota `Rejected` tidak dapat mengajukan peminjaman.

### Member Type

- [ ] Sistem mendukung Mahasiswa.
- [ ] Sistem mendukung Dosen.
- [ ] Mahasiswa dan Dosen memiliki aturan peminjaman yang sama.

### Member Management

- [ ] Administrator dapat melihat data anggota.
- [ ] Administrator dapat melihat detail anggota.
- [ ] Administrator dapat memperbarui data anggota.

---

## 17. Status Requirement

| Item | Status |
|------|--------|
| Business Requirement | Resolved |
| Functional Requirement | Resolved |
| Business Rules | Resolved |
| Acceptance Criteria | Defined |
| Client Review | Pending |
| Client Approval | Pending |