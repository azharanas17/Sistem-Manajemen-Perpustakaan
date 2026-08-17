# Repository Management

## 1. Overview

Repository Management merupakan modul yang digunakan untuk mengelola koleksi karya ilmiah perpustakaan serta menyediakan akses kepada pengguna terhadap informasi dan file karya ilmiah tersebut.

Pada MVP, repository mencakup:

- Skripsi
- Tesis
- Disertasi

Repository dapat diakses oleh Mahasiswa dan Dosen yang telah login.

Administrator memiliki tanggung jawab untuk mengelola metadata, melakukan review, mengunggah file, serta mengelola permintaan akses terhadap file repository.

---

# 2. Tujuan

Modul Repository Management bertujuan untuk:

- Menyediakan katalog karya ilmiah secara digital.
- Memudahkan pengguna menemukan karya ilmiah yang tersedia.
- Menampilkan metadata dan abstrak karya ilmiah.
- Membatasi akses terhadap file lengkap berdasarkan persetujuan Administrator.
- Membantu Administrator mengelola koleksi repository.
- Menjaga agar metadata repository telah diperiksa sebelum dipublikasikan.

---

# 3. Aktor

## 3.1 Administrator

Administrator bertanggung jawab terhadap pengelolaan repository.

Administrator dapat:

- Membuat data repository.
- Mengubah metadata repository.
- Memasukkan abstrak.
- Mengunggah file repository.
- Melakukan review metadata.
- Menyetujui repository untuk dipublikasikan.
- Mengelola status publikasi repository.
- Melihat permintaan akses repository.
- Menyetujui permintaan akses.
- Menolak permintaan akses.
- Memberikan alasan penolakan.
- Melihat riwayat akses repository.

## 3.2 Mahasiswa

Mahasiswa dapat:

- Melihat daftar repository.
- Mencari repository.
- Melihat detail repository.
- Membaca metadata.
- Membaca abstrak.
- Mengajukan permintaan akses terhadap file lengkap.
- Mengakses file setelah permintaan disetujui dan selama masa akses masih berlaku.

## 3.3 Dosen

Dosen memiliki akses repository yang sama dengan Mahasiswa.

Dosen dapat:

- Melihat daftar repository.
- Mencari repository.
- Melihat detail repository.
- Membaca metadata.
- Membaca abstrak.
- Mengajukan permintaan akses terhadap file lengkap.
- Mengakses file setelah permintaan disetujui dan selama masa akses masih berlaku.

---

# 4. Scope Repository MVP

Jenis karya ilmiah yang termasuk dalam Repository MVP adalah:

1. Skripsi
2. Tesis
3. Disertasi

Jenis karya ilmiah lainnya tidak termasuk dalam scope MVP.

Jenis karya ilmiah tambahan dapat dipertimbangkan pada fase pengembangan berikutnya.

---

# 5. Repository Information

Setiap repository memiliki halaman detail yang menampilkan informasi karya ilmiah kepada pengguna.

Halaman detail harus menampilkan informasi yang tersedia sebelum pengguna dapat mengakses file lengkap.

Informasi repository mencakup:

- Judul.
- Penulis.
- Jenis karya ilmiah.
- Tahun.
- Program studi atau informasi akademik terkait apabila digunakan.
- Pembimbing apabila tersedia.
- Abstrak.
- Metadata lainnya yang ditentukan oleh Administrator.

Metadata yang digunakan harus dapat dikelola oleh Administrator.

---

# 6. Abstract

Abstrak merupakan bagian dari informasi repository yang dapat dibaca langsung oleh pengguna.

Abstrak:

- Disimpan langsung di dalam sistem.
- Dapat ditampilkan pada halaman detail repository.
- Tidak memerlukan pengguna mengunduh file lengkap untuk membacanya.
- Dikelola oleh Administrator.

Dengan demikian, pengguna tetap dapat memahami isi umum karya ilmiah sebelum mengajukan akses terhadap file lengkap.

---

# 7. Repository File

File lengkap karya ilmiah disimpan dalam repository dan tidak langsung tersedia untuk diunduh oleh seluruh pengguna.

File repository hanya dapat diakses setelah permintaan akses disetujui oleh Administrator.

Pada MVP, hanya Administrator yang dapat mengunggah file repository ke dalam sistem.

---

# 8. Upload Repository

Mahasiswa dan Dosen tidak dapat mengunggah file repository secara langsung melalui sistem.

Jika Mahasiswa atau Dosen memiliki karya ilmiah yang perlu dimasukkan ke repository, file dapat dikirimkan kepada Administrator melalui email atau media komunikasi di luar sistem.

Administrator kemudian:

1. Menerima file.
2. Memeriksa file dan informasi terkait.
3. Memasukkan metadata ke dalam sistem.
4. Memasukkan abstrak.
5. Mengunggah file repository.
6. Melakukan review metadata.
7. Mempublikasikan repository apabila telah memenuhi persyaratan.

---

# 9. Metadata Review

Administrator wajib memeriksa metadata sebelum repository dipublikasikan.

Repository tidak boleh dipublikasikan sebelum metadata selesai diperiksa dan disetujui oleh Administrator.

Proses umum:

1. Data repository dibuat.
2. Metadata dimasukkan.
3. Abstrak dimasukkan.
4. File diunggah.
5. Administrator melakukan review.
6. Administrator menyetujui metadata.
7. Repository dapat dipublikasikan.

---

# 10. Repository Publication

Repository memiliki status publikasi yang digunakan untuk menentukan apakah repository dapat ditampilkan kepada pengguna.

Status yang digunakan:

- `Draft`
- `Published`
- `Archived`

## 10.1 Draft

Repository masih dalam proses pengelolaan dan belum dipublikasikan kepada pengguna.

## 10.2 Published

Repository telah melalui proses review Administrator dan dapat ditampilkan kepada pengguna.

## 10.3 Archived

Repository tidak lagi ditampilkan sebagai repository aktif, tetapi data tetap tersimpan di sistem.

---

# 11. Repository Detail Page

Pengguna dapat membuka halaman detail repository yang telah dipublikasikan.

Halaman detail menampilkan:

- Informasi bibliografis.
- Metadata.
- Abstrak.
- Informasi jenis karya ilmiah.
- Informasi penulis.
- Informasi tahun.
- Status ketersediaan file.

File lengkap tidak langsung dapat diunduh hanya karena repository dapat dilihat.

Pengguna harus mengajukan akses terlebih dahulu.

---

# 12. Repository Access Request

Pengguna dapat mengajukan permintaan akses terhadap file lengkap repository.

Alur:

1. Pengguna membuka detail repository.
2. Pengguna membaca metadata dan abstrak.
3. Pengguna mengajukan permintaan akses.
4. Permintaan masuk ke Administrator.
5. Administrator melakukan review.
6. Administrator menyetujui atau menolak permintaan.
7. Jika disetujui, pengguna mendapatkan akses terhadap file selama masa akses berlaku.
8. Jika ditolak, pengguna dapat mengajukan kembali.

---

# 13. Access Request Status

Permintaan akses repository memiliki status:

- `Pending`
- `Approved`
- `Rejected`

## 13.1 Pending

Permintaan telah dibuat oleh pengguna tetapi belum diproses Administrator.

## 13.2 Approved

Administrator menyetujui permintaan akses.

Pengguna mendapatkan akses terhadap file repository selama periode akses yang ditentukan.

## 13.3 Rejected

Administrator menolak permintaan akses.

Pengguna dapat mengajukan permintaan akses kembali.

---

# 14. Access Approval

Semua file repository membutuhkan persetujuan Administrator sebelum dapat diunduh.

Administrator dapat menyetujui permintaan akses setelah melakukan review.

Ketika permintaan disetujui:

- Status permintaan menjadi `Approved`.
- Sistem mencatat waktu persetujuan.
- Sistem menentukan periode akses.
- Pengguna dapat mengakses file selama periode tersebut.

---

# 15. Access Period

Akses terhadap file repository berlaku selama:

**7 hari**

Masa akses dihitung sejak permintaan akses disetujui.

Contoh:

- Permintaan disetujui: 17 Agustus 2026
- Masa akses: 7 hari
- Akses berakhir: 24 Agustus 2026

Setelah masa akses berakhir, pengguna tidak lagi dapat mengakses file melalui persetujuan tersebut.

---

# 16. Rejected Access Request

Jika Administrator menolak permintaan akses:

- Status menjadi `Rejected`.
- Pengguna tidak dapat mengakses file melalui permintaan tersebut.
- Pengguna dapat mengajukan permintaan akses kembali.

Penolakan dapat disertai alasan dari Administrator.

Alasan penolakan digunakan untuk memberikan informasi kepada pengguna mengenai keputusan Administrator.

---

# 17. File Size Limit

Ukuran maksimum file repository adalah:

**100 MB per file.**

File yang melebihi batas tersebut tidak dapat diunggah ke dalam sistem.

---

# 18. Repository Access Security

File repository tidak boleh tersedia sebagai file publik yang dapat diakses tanpa proses otorisasi.

Akses file harus memperhatikan:

- Status repository.
- Status permintaan akses.
- Masa berlaku akses.
- Identitas pengguna yang mendapatkan persetujuan.

Pengguna yang belum mendapatkan persetujuan Administrator tidak dapat mengakses file lengkap repository.

---

# 19. Repository Flow

Alur pengelolaan repository:

1. Administrator menerima karya ilmiah.
2. Administrator memasukkan metadata.
3. Administrator memasukkan abstrak.
4. Administrator mengunggah file.
5. Administrator melakukan review metadata.
6. Repository dipublikasikan.
7. Pengguna membuka repository.
8. Pengguna membaca metadata dan abstrak.
9. Pengguna mengajukan akses file.
10. Administrator melakukan review permintaan.
11. Administrator menyetujui atau menolak.
12. Jika disetujui, pengguna mendapatkan akses selama 7 hari.
13. Setelah 7 hari, akses berakhir.

---

# 20. Business Rules

| No | Aturan |
|----|--------|
| 1 | Repository MVP terdiri dari Skripsi, Tesis, dan Disertasi. |
| 2 | Repository hanya dapat diakses oleh pengguna yang telah login. |
| 3 | Halaman detail repository menampilkan metadata dan abstrak. |
| 4 | Abstrak disimpan langsung di dalam sistem. |
| 5 | File lengkap tidak langsung dapat diunduh oleh pengguna. |
| 6 | Semua file repository membutuhkan persetujuan Administrator sebelum dapat diakses. |
| 7 | Hanya Administrator yang dapat mengunggah file repository pada MVP. |
| 8 | Mahasiswa dan Dosen tidak dapat mengunggah file repository secara langsung melalui sistem. |
| 9 | File dapat dikirim kepada Administrator melalui email atau media komunikasi di luar sistem. |
| 10 | Administrator wajib memeriksa metadata sebelum repository dipublikasikan. |
| 11 | Repository harus melalui proses review sebelum berstatus `Published`. |
| 12 | Pengguna harus mengajukan permintaan akses untuk mengakses file lengkap. |
| 13 | Permintaan akses dapat berstatus `Pending`, `Approved`, atau `Rejected`. |
| 14 | Permintaan akses yang disetujui memberikan akses selama 7 hari. |
| 15 | Setelah masa akses berakhir, akses terhadap file melalui persetujuan tersebut berakhir. |
| 16 | Jika permintaan akses ditolak, pengguna dapat mengajukan kembali. |
| 17 | Ukuran maksimum file repository adalah 100 MB. |
| 18 | Pengguna yang tidak memiliki persetujuan aktif tidak dapat mengakses file lengkap. |

---

# 21. Features Outside MVP

Fitur berikut tidak termasuk dalam Repository MVP:

- Upload repository mandiri oleh Mahasiswa.
- Upload repository mandiri oleh Dosen.
- Integrasi submission repository melalui sistem.
- Persetujuan otomatis.
- Download tanpa approval Administrator.
- Batas download berdasarkan jumlah download.
- Sistem pembayaran untuk akses repository.

Fitur tersebut dapat dipertimbangkan pada fase pengembangan berikutnya.

---

# 22. Acceptance Criteria

Modul Repository Management dianggap memenuhi requirement apabila:

## Repository

- [ ] Administrator dapat membuat data repository.
- [ ] Administrator dapat mengubah metadata repository.
- [ ] Administrator dapat memasukkan abstrak.
- [ ] Repository mendukung jenis Skripsi, Tesis, dan Disertasi.
- [ ] Administrator dapat mengunggah file repository.
- [ ] Ukuran file maksimum adalah 100 MB.

## Metadata

- [ ] Metadata dapat ditampilkan pada halaman detail repository.
- [ ] Abstrak dapat ditampilkan pada halaman detail repository.
- [ ] Metadata harus diperiksa Administrator sebelum repository dipublikasikan.
- [ ] Repository yang belum disetujui tidak dapat dipublikasikan sebagai repository aktif.

## Publication

- [ ] Administrator dapat mempublikasikan repository setelah metadata disetujui.
- [ ] Repository yang dipublikasikan dapat ditemukan oleh pengguna.
- [ ] Repository dapat diarsipkan tanpa menghapus data.

## Access Request

- [ ] Pengguna dapat mengajukan permintaan akses terhadap file.
- [ ] Administrator dapat melihat permintaan akses.
- [ ] Administrator dapat menyetujui permintaan akses.
- [ ] Administrator dapat menolak permintaan akses.
- [ ] Permintaan yang ditolak dapat diajukan kembali oleh pengguna.
- [ ] Alasan penolakan dapat dicatat.

## File Access

- [ ] File tidak dapat diakses sebelum permintaan disetujui.
- [ ] File dapat diakses setelah permintaan disetujui.
- [ ] Akses berlaku selama 7 hari.
- [ ] Akses berakhir setelah masa akses selesai.
- [ ] Pengguna tanpa akses aktif tidak dapat mengakses file lengkap.

## Upload

- [ ] Mahasiswa tidak dapat mengunggah file repository secara langsung.
- [ ] Dosen tidak dapat mengunggah file repository secara langsung.
- [ ] Administrator dapat mengunggah file repository.
- [ ] File yang melebihi 100 MB ditolak oleh sistem.

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