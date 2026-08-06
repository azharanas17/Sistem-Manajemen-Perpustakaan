---
title: Member Management
module: Functional Requirements
code: FR-MEM
version: 0.1.0
status: Draft
---

# Member Management

# 1. Tujuan

Modul **Member Management** bertanggung jawab untuk mengelola seluruh siklus hidup anggota perpustakaan, mulai dari proses registrasi, persetujuan keanggotaan, autentikasi, pengelolaan profil, hingga administrasi akun oleh Administrator.

Modul ini menjadi pintu masuk utama bagi pengguna untuk memperoleh akses terhadap seluruh layanan perpustakaan yang tersedia pada sistem.

---

# 2. Aktor

| Aktor | Deskripsi |
|--------|-----------|
| Administrator | Mengelola data anggota, menyetujui pendaftaran, mengubah status akun, dan melakukan administrasi pengguna. |
| Mahasiswa | Melakukan registrasi, masuk ke sistem, mengelola profil pribadi, serta menggunakan layanan perpustakaan setelah menjadi anggota. |
| Dosen | Melakukan registrasi, masuk ke sistem, mengelola profil pribadi, serta menggunakan layanan perpustakaan setelah menjadi anggota. |

---

# 3. Tujuan Bisnis

Implementasi modul ini bertujuan untuk:

- Mendigitalisasi proses pendaftaran anggota perpustakaan.
- Memastikan hanya anggota yang telah diverifikasi yang dapat menggunakan layanan perpustakaan.
- Mempermudah Administrator dalam mengelola data anggota.
- Menyediakan data anggota yang konsisten sebagai dasar bagi modul lain, seperti peminjaman buku dan repository.

---

# 4. Ruang Lingkup

Modul ini mencakup fitur-fitur berikut:

- Registrasi anggota.
- Persetujuan keanggotaan.
- Login.
- Logout.
- Pengelolaan profil pengguna.
- Pengelolaan akun oleh Administrator.
- Impor data pengguna melalui file Excel.

---

# 5. Functional Requirements

## FR-MEM-001 — Registrasi Anggota

### Deskripsi

Sistem menyediakan fasilitas registrasi mandiri bagi calon anggota perpustakaan melalui website.

### Aktor

- Mahasiswa
- Dosen

### Prasyarat

- Pengguna belum memiliki akun.
- Pengguna mengakses halaman registrasi.

### Alur Utama

1. Pengguna membuka halaman registrasi.
2. Pengguna mengisi formulir pendaftaran.
3. Pengguna mengirim formulir.
4. Sistem melakukan validasi data.
5. Sistem menyimpan data pengguna.
6. Status akun diubah menjadi **Pending Approval**.
7. Sistem menampilkan informasi bahwa pendaftaran berhasil dan sedang menunggu persetujuan Administrator.

### Kondisi Akhir

- Data pengguna tersimpan.
- Status akun adalah **Pending Approval**.
- Pengguna belum dapat menggunakan layanan perpustakaan.

### Acceptance Criteria

- Seluruh field wajib harus diisi.
- Email tidak boleh digunakan oleh akun lain.
- Nomor induk tidak boleh digunakan oleh akun lain.
- Password memenuhi kebijakan keamanan sistem.
- Status awal akun adalah **Pending Approval**.

---

## FR-MEM-002 — Persetujuan Keanggotaan

### Deskripsi

Administrator dapat menyetujui atau menolak pendaftaran anggota baru.

### Aktor

- Administrator

### Prasyarat

- Administrator telah login.
- Terdapat pendaftaran dengan status **Pending Approval**.

### Alur Utama

1. Administrator membuka daftar pendaftaran anggota.
2. Administrator memilih salah satu pendaftaran.
3. Administrator melakukan verifikasi data.
4. Administrator memilih aksi:
   - Setujui
   - Tolak
5. Sistem memperbarui status pendaftaran.

### Kondisi Akhir

Apabila disetujui:

- Status akun berubah menjadi **Active**.
- Pengguna dapat login ke sistem.

Apabila ditolak:

- Status akun berubah menjadi **Rejected**.
- Pengguna tidak dapat login.

### Acceptance Criteria

- Hanya Administrator yang dapat melakukan persetujuan.
- Setiap perubahan status harus tersimpan pada sistem.
- Pengguna dengan status **Rejected** tidak dapat login.

---

## FR-MEM-003 — Login

### Deskripsi

Pengguna yang telah memiliki akun aktif dapat masuk ke dalam sistem.

### Aktor

- Mahasiswa
- Dosen
- Administrator

### Prasyarat

- Akun telah berstatus **Active**.

### Alur Utama

1. Pengguna membuka halaman login.
2. Pengguna memasukkan email dan password.
3. Sistem melakukan autentikasi.
4. Sistem membuat sesi login.
5. Pengguna diarahkan ke dashboard sesuai perannya.

### Kondisi Akhir

Pengguna berhasil masuk ke sistem.

### Acceptance Criteria

- Hanya akun berstatus **Active** yang dapat login.
- Password harus sesuai.
- Sistem menampilkan pesan yang sesuai apabila autentikasi gagal.

---

## FR-MEM-004 — Logout

### Deskripsi

Pengguna dapat mengakhiri sesi penggunaan sistem.

### Aktor

- Semua pengguna

### Alur Utama

1. Pengguna memilih menu Logout.
2. Sistem menghapus sesi autentikasi.
3. Sistem mengarahkan pengguna ke halaman login.

### Acceptance Criteria

- Seluruh sesi login dihapus.
- Pengguna tidak dapat mengakses halaman yang memerlukan autentikasi setelah logout.

---

## FR-MEM-005 — Manajemen Pengguna

### Deskripsi

Administrator dapat mengelola seluruh data pengguna.

### Fitur

- Menambah pengguna.
- Mengubah data pengguna.
- Menonaktifkan akun.
- Mengaktifkan kembali akun.
- Menghapus akun.

### Acceptance Criteria

- Seluruh perubahan tersimpan pada sistem.
- Hanya Administrator yang memiliki hak akses.

---

## FR-MEM-006 — Import Data Pengguna

### Deskripsi

Administrator dapat mengimpor data pengguna menggunakan file Microsoft Excel.

### Acceptance Criteria

- Sistem memvalidasi format file.
- Sistem menampilkan jumlah data berhasil dan gagal diimpor.
- Data yang gagal tidak menghentikan proses impor data lainnya.

---

## FR-MEM-007 — Pengelolaan Profil

### Deskripsi

Pengguna dapat memperbarui informasi profil pribadinya.

### Acceptance Criteria

- Pengguna hanya dapat mengubah profil miliknya sendiri.
- Perubahan data langsung tersimpan.
- Email tetap harus bersifat unik.

---

# 6. Business Rules

## BR-MEM-001 — Persetujuan Keanggotaan

Setiap pendaftaran anggota baru harus melalui proses persetujuan oleh Administrator sebelum akun dapat menggunakan layanan perpustakaan.

---

## BR-MEM-002 — Status Awal Akun

Setiap akun hasil registrasi mandiri memiliki status awal **Pending Approval**.

---

## BR-MEM-003 — Hak Akses Berdasarkan Status

Hanya akun dengan status **Active** yang dapat mengakses layanan perpustakaan setelah berhasil login.

---

## BR-MEM-004 — Hak Persetujuan

Proses persetujuan maupun penolakan pendaftaran hanya dapat dilakukan oleh Administrator.

---

## BR-MEM-005 — Keunikan Data

Email dan Nomor Induk (NIM atau NIDN) harus bersifat unik dan tidak boleh digunakan oleh lebih dari satu akun.

---

## BR-MEM-006 — Import Data

Administrator dapat menambahkan data anggota melalui proses impor menggunakan file Microsoft Excel.

---

## BR-MEM-007 — Registrasi Mandiri

Mahasiswa dan Dosen melakukan registrasi secara mandiri melalui website.

---

## BR-MEM-008 — Perubahan Profil

Pengguna hanya diperbolehkan mengubah data profil miliknya sendiri.

Administrator dapat mengubah data seluruh pengguna.

---

## BR-MEM-009 — Penghapusan Akun

Penghapusan akun hanya dapat dilakukan oleh Administrator.

Apabila akun masih memiliki transaksi peminjaman yang belum selesai, sistem harus menolak proses penghapusan.

---

## BR-MEM-010 — Penonaktifan Akun

Administrator dapat menonaktifkan akun tanpa menghapus data pengguna.

Akun yang berstatus nonaktif tidak dapat melakukan login.

---

# 7. Data Dictionary

## Data Anggota

| Field | Tipe | Wajib | Keterangan |
|--------|------|:----:|------------|
| id | UUID / BigInt | ✅ | Primary Key |
| full_name | String | ✅ | Nama lengkap pengguna |
| email | String | ✅ | Digunakan untuk login |
| password | String (Hash) | ✅ | Password terenkripsi |
| role | Enum | ✅ | Administrator, Mahasiswa, Dosen |
| identity_number | String | ✅ | NIM atau NIDN |
| faculty | String | ✅ | Fakultas |
| study_program | String | ✅ | Program Studi |
| phone_number | String | ❌ | Nomor telepon |
| address | Text | ❌ | Alamat |
| profile_photo | String | ❌ | Lokasi file foto profil |
| account_status | Enum | ✅ | Pending Approval, Active, Rejected, Inactive |
| created_at | Timestamp | ✅ | Waktu pembuatan data |
| updated_at | Timestamp | ✅ | Waktu perubahan terakhir |

---

## Role

| Role | Deskripsi |
|------|-----------|
| Administrator | Mengelola seluruh sistem |
| Mahasiswa | Menggunakan layanan perpustakaan |
| Dosen | Menggunakan layanan perpustakaan |

---

## Status Akun

| Status | Deskripsi |
|--------|-----------|
| Pending Approval | Menunggu persetujuan Administrator |
| Active | Akun dapat menggunakan seluruh layanan sesuai hak akses |
| Rejected | Pendaftaran ditolak |
| Inactive | Akun dinonaktifkan oleh Administrator |

---

# 8. Definition of Done

Dokumen ini dinyatakan selesai apabila seluruh kriteria berikut telah terpenuhi.

| No | Kriteria | Status |
|----|----------|:------:|
| 1 | Tujuan modul telah didefinisikan | ☑ |
| 2 | Aktor telah diidentifikasi | ☑ |
| 3 | Ruang lingkup modul telah ditentukan | ☑ |
| 4 | Functional Requirement telah ditulis | ☑ |
| 5 | Business Rule telah ditulis | ☑ |
| 6 | Tidak terdapat asumsi teknis (database, API, framework) | ☑ |
| 7 | Tidak terdapat Open Question | ☑ |
| 8 | Siap dilakukan review bersama client | ☑ |

---

# 9. Riwayat Keputusan

| ID | Keputusan |
|----|-----------|
| D-MEM-001 | Sistem menyediakan registrasi anggota secara mandiri. |
| D-MEM-002 | Setiap pendaftaran harus melalui persetujuan Administrator. |
| D-MEM-003 | Sistem menyediakan tiga peran pengguna, yaitu Administrator, Mahasiswa, dan Dosen. |
| D-MEM-004 | Integrasi Single Sign-On (SSO) tidak termasuk ruang lingkup MVP. |
| D-MEM-005 | Administrator dapat melakukan impor data pengguna melalui file Microsoft Excel. |

---

# 10. Catatan

Dokumen ini mendefinisikan kebutuhan bisnis untuk modul Manajemen Anggota.

Dokumen ini tidak membahas desain antarmuka, struktur basis data, implementasi API, maupun detail teknis lainnya. Seluruh aspek teknis akan dijelaskan pada dokumen tahap desain dan pengembangan.
