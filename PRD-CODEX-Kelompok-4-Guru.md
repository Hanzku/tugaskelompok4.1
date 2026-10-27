# PRD-CODEX
# SISTEM INFORMASI SEDERHANA
## KELOMPOK 4: MODUL GURU

## 1. IDENTITAS PROYEK

Nama proyek: Sistem Informasi Sederhana SMK Malaka
Kategori: Kelompok 4, Guru
Repository eksperimen: https://github.com/Hanzku/tugaskelompok4.1
Branch target: main
Metode kerja Git: PowerShell
Tujuan: eksperimen perbandingan AI coding agent menggunakan repository terpisah agar hasilnya dapat dibandingkan dengan repository utama.

Referensi:
- File Excel Kelompok XI TKJ untuk mengidentifikasi kategori kelompok.
- Diagram ERD Sistem Informasi Sederhana.
- Arsip siswa.zip sebagai referensi source code PHP/MySQL yang tersedia.
- Mockup visual desain website yang disertakan terpisah dengan PRD.

## 2. TUJUAN EKSPERIMEN AI CODING AGENT

Repository tugaskelompok4.1 digunakan sebagai lingkungan eksperimen untuk membandingkan hasil implementasi dari AI coding agent.

Agar perbandingan adil:
- Pertahankan kebutuhan, kategori, ERD, dan kriteria penerimaan yang sama antar-agent.
- Jangan memakai hasil agent lain sebagai implementasi awal kecuali memang sudah ada di repository.
- Catat nama agent, tanggal pengerjaan, commit awal, commit akhir, fitur yang selesai, pengujian yang dijalankan, serta masalah yang ditemukan.
- Jangan mengklaim perbandingan objektif hanya dari kualitas tampilan. Evaluasi juga kebenaran ERD, fungsi CRUD, keamanan, maintainability, responsivitas, dan hasil tes.
- Jangan mengubah atau menimpa repository utama Hanzku/tugaskelompok4. Kerjakan hanya repository eksperimen yang ditentukan dalam prompt.
- Setiap agent wajib melaporkan perubahan sendiri secara transparan.

## 3. RUANG LINGKUP KATEGORI

Kelompok 4 berfokus pada entitas Guru.

Atribut Guru menurut ERD:
| Atribut | Fungsi |
|---|---|
| KODE_GURU | Primary key dan identitas unik guru |
| NAMA | Nama guru |
| FOTOGURU | Foto guru |

Aturan:
- Gunakan tiga atribut tersebut untuk entitas Guru.
- Jangan menambahkan alamat, nomor telepon, email, jenis kelamin, atau jabatan tanpa dasar dari ERD atau skema yang memang sudah ada.
- KODE_GURU wajib diisi dan unik.
- NAMA wajib diisi.
- FOTOGURU harus mengikuti cara penyimpanan foto yang kompatibel dengan aplikasi dan database yang tersedia.

## 4. ANALISIS RELASI ERD

Relasi Diampu menghubungkan Guru dan Pelajaran. Atribut relasi Diampu:
- KODE_GURU
- KD_PELAJARAN
- HARI

Atribut entitas Pelajaran:
- KD_PELAJARAN
- NAMA_PELAJARAN
- BOBOT

Entitas Murid memiliki NIS, NAMA, KELAS, dan FOTO. Relasi Mempelajari memiliki NIS, KD_PELAJARAN, dan NILAI.

Jangan memindahkan KD_PELAJARAN atau HARI ke tabel Guru. Jangan mengembangkan kategori Murid, Pelajaran, atau Mempelajari sebagai fokus utama Kelompok 4. Pertahankan halaman dan fungsi lain yang sudah ada. Jangan menghapus atau merusak skema database yang ada.

## 5. FITUR WAJIB

1. Menampilkan daftar guru dari database.
2. Menambahkan guru.
3. Mengedit data guru.
4. Menghapus data guru dengan konfirmasi.
5. Menampilkan foto guru.
6. Mengunggah foto saat menambahkan guru.
7. Mengganti foto saat mengedit guru.
8. Mempertahankan foto lama ketika tidak ada foto pengganti.
9. Mencari guru berdasarkan KODE_GURU atau NAMA.
10. Menampilkan notifikasi berhasil atau gagal.
11. Memvalidasi input di sisi server.
12. Menangani kondisi data kosong dan data tidak ditemukan.
13. Menangani kegagalan koneksi database dengan pesan yang aman.

## 6. SPESIFIKASI DATABASE

Gunakan konfigurasi database yang benar-benar tersedia dalam proyek. Audit file dan skema sebelum mengubah apa pun.

Struktur logis tabel guru:
- kode_guru: VARCHAR, PRIMARY KEY.
- nama: VARCHAR, NOT NULL.
- fotoguru: tipe penyimpanan sesuai skema dan arsitektur yang sudah ada.

Jika tabel Guru sudah ada, gunakan tabel tersebut. Jika belum, buat skrip SQL yang cocok dengan skema proyek. Jangan membuat tabel duplikat, menghapus data, atau mengubah tabel lain tanpa alasan yang terverifikasi. Jangan mengarang kredensial database. Jangan memasukkan rahasia ke repository.

## 7. REFERENSI DESAIN WEBSITE

Gunakan file mockup yang disertakan bersama PRD sebagai referensi visual. Jika gambar tidak ada dalam workspace, cari file desain di folder proyek atau minta agent menggunakan deskripsi visual ini dan catat bahwa gambar tidak ditemukan. Jangan mengklaim telah melihat gambar yang tidak tersedia.

Gaya visual:
- Sidebar navy atau biru gelap.
- Area konten utama putih dan abu-abu muda.
- Tombol utama biru.
- Aksi hapus merah.
- Panel dan kartu dengan sudut membulat secukupnya.
- Tipografi mudah dibaca.
- Ikon konsisten.
- Jarak antar komponen rapi.
- Bayangan tipis jika diperlukan.
- Hindari gradien dan animasi berlebihan.
- Hindari tampilan template generik yang tidak disesuaikan dengan aplikasi sekolah.

### 7.1 Halaman Data Guru
Tampilkan sidebar, judul Data Guru, keterangan singkat, tombol Tambah Guru, kolom pencarian, jumlah data yang benar-benar dihitung dari database, tabel data, foto guru, tombol Edit, dan tombol Hapus. Kolom tabel: Nomor, KODE_GURU, NAMA, FOTOGURU, AKSI. Tampilkan pagination bila diperlukan.

### 7.2 Form Tambah Guru
Sediakan input KODE_GURU, NAMA, area unggah foto, panduan format dan ukuran file, tombol Batal, dan tombol Simpan. Tampilkan validasi dekat kolom yang bermasalah. Form boleh berupa halaman atau modal sesuai arsitektur proyek.

### 7.3 Form Edit Guru
Tampilkan identitas kode guru, input NAMA, pratinjau foto saat ini, kontrol memilih foto baru, tombol Batal, dan Simpan. Jangan izinkan perubahan primary key yang dapat merusak relasi tanpa memeriksa dampaknya. Jika tidak ada foto baru, pertahankan foto lama.

### 7.4 Konfirmasi Hapus
Tampilkan identitas guru dan tombol Batal serta Hapus. Jika foreign key mencegah penghapusan, tampilkan pesan yang mudah dipahami. Jangan menghapus data relasi secara otomatis tanpa aturan yang telah tersedia.

### 7.5 Halaman Detail
Boleh tersedia jika sesuai arsitektur proyek. Tampilkan foto, KODE_GURU, NAMA, Edit, dan Kembali. Tampilkan data relasi Diampu hanya bila tabel dan datanya memang tersedia.

### 7.6 Responsivitas
Dukung desktop dan ponsel Android. Pada layar kecil, sidebar dapat dilipat, form menggunakan lebar layar, tombol nyaman disentuh, gambar tidak meluber, dan tabel berubah menjadi tampilan responsif atau kartu. Hindari horizontal overflow.

### 7.7 Navigasi
Menu Guru harus terlihat aktif. Menu Dashboard, Murid, Pelajaran, Mempelajari, dan Diampu hanya ditampilkan sebagai tautan jika rutenya benar-benar tersedia. Jangan membuat tautan palsu untuk meniru mockup.

## 8. ATURAN MOCKUP

Mockup adalah referensi visual, bukan sumber data. Nama, kode, foto, dan angka di dalamnya hanya ilustrasi. Jangan memasukkan data mockup sebagai data produksi. Jangan menempelkan gambar mockup sebagai background halaman. Implementasikan komponen nyata yang bekerja dengan database. Jika database kosong, gunakan empty state, bukan data palsu.

## 9. VALIDASI DAN KEAMANAN

- Validasi KODE_GURU wajib dan unik.
- Validasi NAMA wajib.
- Validasi foto berdasarkan ekstensi, MIME type, konten file, dan ukuran.
- Batas awal foto maksimal 3 MB kecuali proyek mempunyai ketentuan lain yang terverifikasi.
- Gunakan nama file aman dan hindari tabrakan nama.
- Simpan foto sesuai pola folder aplikasi.
- Gunakan PDO atau MySQLi dengan prepared statements.
- Hindari fungsi mysql_* yang sudah usang.
- Escape output untuk mencegah XSS.
- Validasi dilakukan di server, bukan hanya JavaScript.
- Jangan menampilkan kredensial atau stack trace sensitif.
- Gunakan proteksi CSRF untuk aksi yang mengubah data jika sesuai pola aplikasi.
- Jangan menghapus foto atau data sebelum operasi database berhasil.

## 10. AUDIT SOURCE CODE

Periksa keseluruhan repository, struktur folder, koneksi database, file CRUD, folder foto, CSS/JavaScript, rute, dependensi, versi PHP, serta penggunaan fungsi mysql_* dan tautan yang rusak.

Jangan mengasumsikan project lengkap. Jangan menulis ulang seluruh aplikasi apabila perbaikan terarah cukup. Pertahankan perubahan lokal dan data yang sudah ada.

## 11. KRITERIA PENERIMAAN

1. Halaman Guru terhubung ke database nyata.
2. Daftar Guru sesuai isi database.
3. Tambah data berhasil.
4. Kode duplikat ditolak.
5. Data dapat diedit.
6. Foto dapat diunggah dan ditampilkan.
7. Foto lama dipertahankan jika tidak ada foto baru.
8. Hapus berjalan dengan konfirmasi dan menangani foreign key.
9. Pencarian bekerja.
10. Validasi input dan unggahan aman.
11. Desain mengikuti referensi.
12. Website responsif desktop dan mobile.
13. Tidak ada perubahan yang merusak fitur/data yang sudah ada.
14. Pengujian dilaporkan berdasarkan hasil nyata.
15. Tidak ada kredensial rahasia yang masuk commit.

## 12. PROTOKOL GIT DAN GITHUB WAJIB MENGGUNAKAN POWERSHELL

Target repository: https://github.com/Hanzku/tugaskelompok4.1
Remote origin: https://github.com/Hanzku/tugaskelompok4.1.git
Branch target: main

Semua perintah Git dan pemeriksaan terminal harus dijalankan menggunakan PowerShell di lingkungan kerja Codex. Jangan menggantinya dengan Bash, WSL, atau perintah terminal shell lain.

### 12.1 Pemeriksaan awal
Jalankan perintah PowerShell:
```powershell
$ErrorActionPreference = "Stop"
git --version
git remote -v
git status --short --branch
git branch --show-current
git log -1 --oneline
```

Pastikan repository aktif adalah tugaskelompok4.1. Jika belum berada pada repository yang benar, clone melalui PowerShell:
```powershell
git clone https://github.com/Hanzku/tugaskelompok4.1.git
Set-Location .\tugaskelompok4.1
```

Jika repository sudah di-clone, masuk ke foldernya tanpa meng-clone ulang.

Periksa remote dan default branch. Jangan mengubah repository utama tugaskelompok4. Jangan menghapus perubahan lokal pengguna. Jika working tree berisi perubahan yang tidak dibuat oleh agent, jangan menimpa atau memasukkannya ke commit. Identifikasi dan pisahkan file hasil pekerjaan agent.

### 12.2 Sinkronisasi branch
Setelah memeriksa perubahan lokal:
```powershell
git fetch origin
git switch main
git pull --ff-only origin main
git status --short --branch
```

Jika branch main belum ada secara lokal, buat/switch sesuai branch origin yang benar setelah memeriksa branch remote. Jangan melakukan reset --hard. Jangan menggunakan force push. Jika pull fast-forward gagal karena konflik atau divergensi, hentikan proses push, evaluasi situasi, lalu laporkan langkah yang aman.

### 12.3 Pengujian sebelum commit
Jalankan tes yang relevan dengan stack yang ditemukan, seperti pemeriksaan sintaks PHP dan test suite yang tersedia. Gunakan PowerShell. Jangan menyatakan test lulus jika belum dijalankan. Jangan commit database credentials, file .env, dump database berisi data nyata, cache, atau file rahasia. Periksa dengan:
```powershell
git status --short
git diff --check
git diff --stat
git diff
```

Tinjau file yang akan di-commit. Jangan gunakan git add . secara membabi buta jika ada perubahan pengguna yang tidak terkait. Stage hanya file pekerjaan agent yang memang perlu:
```powershell
git add <daftar-file-yang-relevan>
git diff --cached --check
git diff --cached --stat
git diff --cached
```

### 12.4 Commit dan push langsung
Jika tes dan pemeriksaan aman, lakukan commit langsung ke branch main pada repository eksperimen:
```powershell
git commit -m "feat: implement teacher management module"
git push origin main
```

Jangan membuat Pull Request untuk tugas ini kecuali repository menerapkan aturan yang mengharuskan PR. Jangan menggunakan --force atau --force-with-lease untuk memaksakan push. Jika push ditolak karena branch berubah, fetch dan evaluasi perubahan remote, integrasikan secara aman, jalankan ulang tes, lalu coba push normal. Jangan pernah menghapus commit remote untuk memaksa keberhasilan.

### 12.5 Verifikasi setelah push
Setelah push, jalankan:
```powershell
git status --short --branch
git log -1 --oneline
git rev-parse HEAD
git ls-remote origin refs/heads/main
```

Pastikan commit lokal dan commit remote sesuai. Jika lingkungan tidak memiliki kredensial atau izin push, jangan berpura-pura berhasil. Tetap selesaikan perubahan lokal, jelaskan hambatannya, dan berikan perintah PowerShell yang diperlukan.

## 13. PENCATATAN HASIL EKSPERIMEN

Tambahkan laporan eksperimen yang ringkas dan berbasis fakta ke dokumentasi proyek. Catat:
- Nama AI coding agent yang digunakan, bila diketahui.
- Tanggal pengerjaan.
- Commit awal dan akhir.
- Fitur yang diimplementasikan.
- Tes yang benar-benar dijalankan dan hasilnya.
- Masalah yang ditemukan atau tersisa.
- Catatan kesesuaian ERD dan desain.
- Hash commit hasil.

Jangan mengarang nama agent, hasil tes, atau angka evaluasi. Untuk membandingkan beberapa agent, gunakan kriteria dan skala yang sama untuk semuanya.

## 14. DOKUMENTASI

Jika proyek sudah memiliki sistem delapan file Markdown untuk konteks coding agent, ikuti sistem yang ada tanpa menggandakan file.

Jika belum tersedia, pertimbangkan membuat:
1. AGENTS.md
2. PRD.md
3. ARCHITECTURE.md
4. DATABASE.md
5. UI_UX.md
6. IMPLEMENTATION_PLAN.md
7. TESTING.md
8. CHANGELOG.md

Isi dokumen sesuai kondisi aktual. Jangan mencatat fitur sebagai selesai sebelum implementasi dan pengujian yang relevan dilakukan.

## 15. LAPORAN AKHIR CODEX

Setelah implementasi selesai, laporkan:
1. Ringkasan perubahan.
2. Daftar file yang dibuat atau diubah.
3. Struktur tabel Guru yang benar-benar digunakan.
4. Hasil tes dengan status aktual.
5. Cara menjalankan aplikasi.
6. Hash commit.
7. Status push ke origin/main.
8. Masalah yang belum terselesaikan.

## 16. INSTRUKSI EKSEKUSI

Mulai dengan audit repository eksperimen tugaskelompok4.1. Implementasikan modul Guru, ikuti desain, uji fungsi, lalu commit dan push langsung ke GitHub menggunakan PowerShell sesuai protokol di atas. Jangan menunggu persetujuan di setiap tahap jika informasi yang tersedia sudah cukup. Jangan pernah mengklaim commit atau push berhasil tanpa verifikasi.
