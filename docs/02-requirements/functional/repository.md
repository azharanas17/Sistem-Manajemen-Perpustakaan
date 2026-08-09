# Repository Management

# 1. Tujuan

Modul Repository Management bertanggung jawab untuk mengelola koleksi karya ilmiah dan dokumen akademik yang disimpan secara digital oleh perpustakaan.

Modul ini memungkinkan pengguna menemukan dan melihat informasi mengenai karya ilmiah melalui katalog repository, membaca abstrak, serta mengajukan akses terhadap dokumen lengkap apabila akses terhadap file dibatasi.

Modul ini juga menyediakan fasilitas bagi Administrator untuk mengelola metadata dan file repository.

---

# 2. Istilah yang Digunakan

## Repository

Repository adalah kumpulan karya ilmiah atau dokumen akademik yang dikelola dan disediakan oleh perpustakaan dalam bentuk digital.

---

## Item Repository

Item Repository adalah satu karya ilmiah atau dokumen akademik yang terdaftar di dalam repository.

Contoh:

* Skripsi
* Tesis
* Disertasi
* Artikel ilmiah
* Karya ilmiah lainnya

---

## Metadata

Metadata adalah informasi yang menjelaskan suatu Item Repository.

Metadata dapat mencakup:

* Judul
* Penulis
* Tahun
* Program Studi
* Fakultas
* Jenis karya ilmiah
* Abstrak
* dan informasi bibliografi lainnya.

---

## File Repository

File Repository adalah dokumen digital lengkap yang berkaitan dengan suatu Item Repository.

File dapat berupa PDF atau format dokumen lain sesuai kebijakan perpustakaan.

---

## Permintaan Akses

Permintaan Akses adalah pengajuan yang dilakukan oleh pengguna untuk memperoleh akses terhadap File Repository yang tidak tersedia untuk publik.

---

# 3. Aktor

| Aktor         | Deskripsi                                                                                       |
| ------------- | ----------------------------------------------------------------------------------------------- |
| Administrator | Mengelola metadata, abstrak, file, dan permintaan akses repository.                             |
| Mahasiswa     | Mencari repository, melihat metadata dan abstrak, serta mengajukan akses terhadap file lengkap. |
| Dosen         | Mencari repository, melihat metadata dan abstrak, serta mengajukan akses terhadap file lengkap. |

---

# 4. Tujuan Bisnis

Implementasi modul ini bertujuan untuk:

* Menyediakan katalog karya ilmiah yang mudah diakses.
* Memudahkan pengguna menemukan karya ilmiah berdasarkan informasi bibliografi.
* Menampilkan informasi karya ilmiah sebelum pengguna meminta akses terhadap dokumen lengkap.
* Menjaga kontrol perpustakaan terhadap distribusi file karya ilmiah.
* Menyediakan arsip digital karya ilmiah yang dikelola secara terpusat.

---

# 5. Ruang Lingkup

Modul Repository Management mencakup:

* Pengelolaan metadata repository.
* Pengelolaan abstrak.
* Pengelolaan file repository.
* Pencarian repository.
* Filter repository.
* Halaman detail repository.
* Pengajuan akses file repository.
* Persetujuan atau penolakan permintaan akses oleh Administrator.
* Pengunduhan file setelah akses disetujui.
* Pengelolaan status publikasi repository.

---

# 6. Functional Requirements

## FR-REP-001 — Kelola Item Repository

### Tujuan

Administrator dapat menambahkan, melihat, mengubah, dan mengelola Item Repository.

### Aktor

* Administrator

### Acceptance Criteria

* Administrator dapat menambahkan Item Repository.
* Administrator dapat mengubah metadata Item Repository.
* Administrator dapat melihat detail Item Repository.
* Administrator dapat mengelola status publikasi Item Repository.

---

## FR-REP-002 — Kelola Metadata Repository

### Deskripsi

Administrator dapat memasukkan dan mengubah metadata yang berkaitan dengan Item Repository.

### Acceptance Criteria

* Metadata dapat disimpan dan diperbarui.
* Metadata ditampilkan pada halaman detail repository.
* Metadata dapat digunakan sebagai informasi pencarian.

---

## FR-REP-003 — Kelola Abstrak

### Deskripsi

Abstrak harus disimpan langsung di dalam sistem agar dapat ditampilkan pada halaman detail repository.

### Acceptance Criteria

* Administrator dapat memasukkan abstrak secara langsung.
* Administrator dapat mengubah abstrak.
* Abstrak dapat dilihat oleh pengguna yang memiliki akses terhadap halaman repository.
* Pengguna tidak perlu mengunduh file untuk membaca abstrak.

---

## FR-REP-004 — Kelola File Repository

### Deskripsi

Administrator dapat mengunggah file lengkap yang berkaitan dengan Item Repository.

### Acceptance Criteria

* Administrator dapat mengunggah file.
* Administrator dapat mengganti file apabila diperlukan.
* File terkait dengan Item Repository tertentu.
* File tidak otomatis dapat diakses oleh seluruh pengguna apabila repository memiliki pembatasan akses.

---

## FR-REP-005 — Pencarian Repository

### Deskripsi

Pengguna dapat mencari Item Repository melalui katalog repository.

Pencarian dilakukan berdasarkan informasi metadata yang relevan.

### Aktor

* Mahasiswa
* Dosen

### Acceptance Criteria

Pengguna dapat mencari repository berdasarkan informasi seperti:

* Judul
* Penulis
* Tahun
* Program Studi
* Fakultas
* Jenis karya ilmiah

---

## FR-REP-006 — Filter Repository

### Deskripsi

Pengguna dapat melakukan filter terhadap daftar repository.

### Acceptance Criteria

Filter dapat digunakan untuk mempersempit hasil pencarian berdasarkan metadata yang tersedia.

---

## FR-REP-007 — Halaman Detail Repository

### Deskripsi

Setiap Item Repository memiliki halaman detail yang menampilkan informasi lengkap sebelum pengguna mengakses file.

### Acceptance Criteria

Halaman detail menampilkan:

* Judul
* Penulis
* Tahun
* Program Studi
* Fakultas
* Jenis karya ilmiah
* Abstrak
* Informasi metadata lainnya
* Status akses terhadap file

---

## FR-REP-008 — Pengajuan Akses File

### Tujuan

Pengguna dapat meminta akses terhadap File Repository yang dibatasi.

### Aktor

* Mahasiswa
* Dosen

### Acceptance Criteria

* Pengguna harus login sebelum mengajukan akses.
* Pengguna dapat mengajukan permintaan akses dari halaman detail repository.
* Sistem mencatat permintaan akses.
* Permintaan memiliki status yang dapat dipantau.

---

## FR-REP-009 — Persetujuan Akses

### Tujuan

Administrator dapat menyetujui atau menolak permintaan akses terhadap File Repository.

### Acceptance Criteria

* Administrator dapat melihat daftar permintaan akses.
* Administrator dapat menyetujui permintaan.
* Administrator dapat menolak permintaan.
* Status permintaan diperbarui setelah keputusan dibuat.

---

## FR-REP-010 — Akses File Setelah Persetujuan

### Deskripsi

File Repository dapat diakses atau diunduh oleh pengguna setelah permintaan aksesnya disetujui.

### Acceptance Criteria

* Pengguna yang disetujui dapat mengakses file.
* Pengguna yang belum disetujui tidak dapat mengakses file terbatas.
* Pengguna yang ditolak tidak dapat mengakses file tersebut.

---

## FR-REP-011 — Riwayat Permintaan Akses

### Deskripsi

Sistem menyimpan riwayat permintaan akses repository.

### Acceptance Criteria

* Setiap permintaan memiliki identitas dan waktu pengajuan.
* Keputusan Administrator tercatat.
* Riwayat tidak dihapus hanya karena permintaan telah selesai diproses.

---

# 7. Informasi Repository

Setiap Item Repository harus mampu menyimpan informasi berikut.

| Informasi       | Wajib | Keterangan                                                                      |
| --------------- | :---: | ------------------------------------------------------------------------------- |
| Judul           |   ✅   | Judul karya ilmiah atau dokumen.                                                |
| Penulis         |   ✅   | Penulis karya ilmiah.                                                           |
| Tahun           |   ✅   | Tahun publikasi atau penyelesaian karya.                                        |
| Jenis Karya     |   ✅   | Jenis dokumen, misalnya Skripsi, Tesis, atau Disertasi.                         |
| Program Studi   |   ❌   | Program studi yang terkait dengan karya ilmiah.                                 |
| Fakultas        |   ❌   | Fakultas yang terkait dengan karya ilmiah.                                      |
| Abstrak         |   ✅   | Ringkasan isi karya ilmiah yang ditampilkan pada halaman detail.                |
| Kata Kunci      |   ❌   | Kata kunci yang berkaitan dengan karya ilmiah.                                  |
| File Repository |   ❌   | File digital lengkap apabila tersedia.                                          |
| Status Akses    |   ✅   | Menentukan apakah file dapat diakses secara publik atau memerlukan persetujuan. |

> Status dan field di atas dapat disesuaikan berdasarkan kebijakan dan kebutuhan perpustakaan setelah dilakukan review terhadap data repository yang sebenarnya.

---

# 8. Business Rules

## BR-REP-001 — Metadata dan File

Metadata repository merupakan bagian yang terpisah dari File Repository.

Sebuah Item Repository tetap dapat ditampilkan meskipun File Repository belum tersedia.

---

## BR-REP-002 — Abstrak

Abstrak harus disimpan langsung di dalam sistem dan dapat ditampilkan pada halaman detail repository.

---

## BR-REP-003 — Akses Terbatas

File Repository tidak harus dapat diakses oleh seluruh pengguna.

Administrator dapat menetapkan bahwa sebuah file memerlukan persetujuan sebelum dapat diakses.

---

## BR-REP-004 — Pengguna Harus Login

Pengguna harus memiliki akun dan telah mendapatkan akses sebagai anggota perpustakaan untuk mengajukan permintaan terhadap File Repository yang dibatasi.

---

## BR-REP-005 — Persetujuan Administrator

Permintaan akses terhadap File Repository yang dibatasi harus diproses oleh Administrator.

---

## BR-REP-006 — Akses Setelah Persetujuan

Pengguna hanya dapat mengakses File Repository setelah permintaan aksesnya disetujui oleh Administrator.

---

## BR-REP-007 — Penolakan Akses

Permintaan yang ditolak tidak memberikan hak akses terhadap File Repository.

---

## BR-REP-008 — Pengelolaan File

File Repository hanya dapat diunggah atau dikelola oleh Administrator melalui sistem.

---

## BR-REP-009 — Pengiriman File di Luar Sistem

Apabila mahasiswa atau dosen memiliki file karya ilmiah yang perlu dimasukkan ke dalam repository, file dapat dikirimkan kepada Administrator melalui email atau media komunikasi lain di luar sistem.

Administrator kemudian bertanggung jawab mengunggah file tersebut ke dalam sistem.

Proses pengiriman file oleh pengguna melalui email tidak termasuk dalam integrasi sistem MVP.

---

## BR-REP-010 — Satu Item Repository

Satu Item Repository merepresentasikan satu karya ilmiah atau dokumen akademik.

---

## BR-REP-011 — Riwayat Permintaan Akses

Riwayat permintaan akses tidak boleh dihapus hanya karena permintaan telah disetujui atau ditolak.

---

# 9. Status Item Repository

Item Repository memiliki status publikasi yang menentukan apakah item dapat ditampilkan kepada pengguna.

| Status    | Deskripsi                                                                               |
| --------- | --------------------------------------------------------------------------------------- |
| Draft     | Repository sedang disiapkan dan belum ditampilkan kepada pengguna.                      |
| Published | Repository telah dipublikasikan dan dapat ditemukan melalui katalog.                    |
| Archived  | Repository tidak lagi ditampilkan sebagai koleksi aktif, tetapi datanya tetap disimpan. |

---

# 10. Status Permintaan Akses

Setiap Permintaan Akses memiliki salah satu status berikut.

| Status               | Deskripsi                                                |
| -------------------- | -------------------------------------------------------- |
| Menunggu Persetujuan | Permintaan baru dibuat dan belum diproses Administrator. |
| Disetujui            | Administrator menyetujui akses terhadap file.            |
| Ditolak              | Administrator menolak permintaan akses.                  |
| Dibatalkan           | Permintaan dibatalkan sebelum diproses.                  |

---

# 11. Alur Akses Repository

## 11.1 Repository Tanpa Pembatasan

Apabila sebuah repository ditetapkan dapat diakses secara publik:

```text
Pengguna
   │
   ▼
Katalog Repository
   │
   ▼
Halaman Detail
   │
   ▼
Metadata + Abstrak
   │
   ▼
Akses File
```

---

## 11.2 Repository Dengan Pembatasan Akses

Untuk repository yang membutuhkan persetujuan:

```text
Pengguna
   │
   ▼
Katalog Repository
   │
   ▼
Halaman Detail
   │
   ├── Metadata
   │
   └── Abstrak
          │
          ▼
   Ajukan Akses File
          │
          ▼
 Menunggu Persetujuan
          │
      ┌───┴───┐
      ▼       ▼
 Disetujui   Ditolak
      │
      ▼
 Akses File
```

---

# 12. Alur Pengelolaan File

Proses pengelolaan file pada MVP dilakukan oleh Administrator.

```text
Karya Ilmiah
     │
     ▼
Mahasiswa / Dosen
     │
     │  Email / komunikasi eksternal
     ▼
Administrator
     │
     ▼
Upload File
     │
     ▼
Item Repository
     │
     ▼
File Repository
```

Sistem tidak perlu menyediakan fitur upload file repository oleh Mahasiswa atau Dosen pada MVP.

---

# 13. Aturan Pengelolaan File

## BR-REP-012 — Upload File

Hanya Administrator yang dapat mengunggah File Repository melalui sistem.

---

## BR-REP-013 — File Tidak Tersedia

Item Repository tetap dapat dipublikasikan apabila metadata dan abstrak telah tersedia meskipun file lengkap belum diunggah.

---

## BR-REP-014 — Penggantian File

Administrator dapat mengganti File Repository apabila diperlukan.

Penggantian file tidak mengubah identitas Item Repository.

---

# 14. Fitur di Luar MVP

Fitur berikut tidak termasuk dalam ruang lingkup MVP dan dapat dipertimbangkan untuk pengembangan berikutnya:

* Upload repository secara mandiri oleh Mahasiswa atau Dosen.
* Integrasi pengiriman file melalui email secara otomatis.
* Notifikasi otomatis melalui email.
* Digital Rights Management.
* Statistik unduhan repository.
* Versioning file repository.
* Integrasi dengan repository eksternal.
* Full-text search di dalam dokumen PDF.

---

# 15. Open Questions

Bagian ini berisi keputusan yang masih memerlukan konfirmasi dari pihak perpustakaan.

| ID         | Pertanyaan                                                                                                             | Status |
| ---------- | ---------------------------------------------------------------------------------------------------------------------- | :----: |
| OQ-REP-001 | Jenis karya ilmiah apa saja yang akan dikelola pada MVP?                                                               |    ⏳   |
| OQ-REP-002 | Metadata wajib apa saja yang harus tersedia untuk setiap jenis karya ilmiah?                                           |    ⏳   |
| OQ-REP-003 | Apakah seluruh repository harus memerlukan persetujuan untuk mengakses file, atau sebagian dapat dibuka secara publik? |    ⏳   |
| OQ-REP-004 | Apakah Administrator perlu memberikan alasan ketika menolak permintaan akses?                                          |    ⏳   |
| OQ-REP-005 | Apakah pengguna dapat mengajukan kembali akses setelah permintaannya ditolak?                                          |    ⏳   |
| OQ-REP-006 | Apakah terdapat pembatasan khusus terhadap jenis pengguna tertentu dalam mengakses file repository?                    |    ⏳   |
| OQ-REP-007 | Format file apa saja yang diperbolehkan untuk File Repository?                                                         |    ⏳   |
| OQ-REP-008 | Apakah file repository harus memiliki batas ukuran maksimum?                                                           |    ⏳   |

> Open Question tidak boleh dianggap sebagai requirement final sebelum mendapatkan konfirmasi dari pihak perpustakaan.

---

# 16. Definition of Done

Dokumen Repository Management dapat dinyatakan **Approved** apabila:

| No | Kriteria                                                                   | Status |
| -- | -------------------------------------------------------------------------- | :----: |
| 1  | Tujuan modul telah didefinisikan                                           |    ☑   |
| 2  | Aktor telah diidentifikasi                                                 |    ☑   |
| 3  | Ruang lingkup telah ditentukan                                             |    ☑   |
| 4  | Functional Requirement telah ditulis                                       |    ☑   |
| 5  | Informasi Repository telah didefinisikan                                   |    ☑   |
| 6  | Business Rule telah ditulis                                                |    ☑   |
| 7  | Status Item Repository telah didefinisikan                                 |    ☑   |
| 8  | Status Permintaan Akses telah didefinisikan                                |    ☑   |
| 9  | Alur akses repository telah didefinisikan                                  |    ☑   |
| 10 | Mekanisme pengelolaan file telah didefinisikan                             |    ☑   |
| 11 | Fitur di luar MVP telah dicatat                                            |    ☑   |
| 12 | Seluruh Open Question telah dikonfirmasi oleh client                       |    ☐   |
| 13 | Tidak terdapat detail implementasi teknis yang tercampur dalam requirement |    ☑   |
| 14 | Dokumen siap digunakan sebagai dasar desain dan pengembangan               |    ☐   |

```

### Status saat ini

Saya akan memberi status **`Draft — Pending Client Confirmation`**, bukan `Approved`.

Dan ada satu hal yang menurut saya bagus dari struktur ini: **kita tidak mencampurkan proses "user mengirim file ke admin melalui email" dengan sistem.** Itu adalah proses operasional di luar aplikasi, sedangkan aplikasi hanya menangani bagian setelah Admin menerima file.

Dengan demikian boundary MVP-nya menjadi jelas:

**Mahasiswa/Dosen → email → Admin → upload ke sistem → Repository**

bukan:

**Mahasiswa/Dosen → upload langsung → Repository**.

Itu akan sangat membantu nanti ketika kita menentukan scope development dan estimasi pengerjaan.
```
