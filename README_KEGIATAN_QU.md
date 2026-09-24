# KEGIATAN QU

Aplikasi web untuk mencatat, memantau, dan merekap kegiatan kerja dengan **Google Apps Script + Google Sheets**.

> **Catat · Pantau · Selesaikan Bersama**

## Fitur Utama

- 🔐 **Login Username & Password**
  - Login tidak bergantung pada email Google sebagai username.
  - Password disimpan menggunakan hash + salt.
  - Tersedia tombol 👁 untuk menampilkan / menyembunyikan password.

- ⏱️ **Pencatatan Waktu Kerja**
  - Input kegiatan saat mulai pekerjaan.
  - Status kegiatan dapat dimulai sebagai **MASIH PROSES**.
  - Saat pekerjaan selesai, klik **Selesai** untuk mengisi jam selesai dan menghitung durasi otomatis.

- 📝 **Input Kegiatan Terlewat**
  - Digunakan ketika pekerjaan sudah selesai tetapi lupa dicatat saat mulai.
  - Tanggal, jam mulai, jam selesai, dan durasi dapat diinput manual.

- 🏷️ **Kategori Kegiatan**
  - DAILY
  - WEEKLY
  - MONTHLY

- 📊 **Dashboard**
  - Ringkasan total waktu.
  - Total kegiatan.
  - Kegiatan masih proses.
  - Daftar kegiatan hari ini.

- 📋 **Data Saya**
  - Melihat kegiatan milik user.
  - Filter berdasarkan tanggal, kategori, dan status.
  - Edit dan hapus kegiatan sesuai hak akses.
  - Menyelesaikan kegiatan yang masih proses.

- 📅 **Rekap**
  - Harian.
  - Mingguan.
  - Bulanan.
  - Ringkasan durasi dan kategori.

- 👥 **Manajemen User**
  - Tambah user.
  - Edit user.
  - Ubah role.
  - Aktif / nonaktifkan user.
  - Hapus user dengan pengamanan.
  - Histori kegiatan tidak ikut terhapus ketika user dihapus.

- 🧩 **Master Data**
  - Pengaturan data master aplikasi sesuai hak akses admin.

- 🛡️ **Audit Log**
  - Mencatat aktivitas penting seperti tambah, edit, hapus, dan perubahan data.

## Role Pengguna

### ADMIN

ADMIN dapat mengakses fungsi administrasi, antara lain:

- Dashboard
- Semua Data / Data Tim
- Rekap Tim
- Manajemen User
- Master Data
- Audit Log

### USER

USER dapat mengakses:

- Dashboard
- Input Kegiatan
- Input Kegiatan Terlewat
- Data Saya
- Rekap

## Teknologi

- Google Apps Script
- Google Sheets
- HTML5
- CSS3
- JavaScript
- Chart.js
- Google Apps Script HTML Service

## Struktur File

```text
KEGIATAN-QU/
├── Code.gs
├── index.html
└── README.md
```

## Struktur Google Sheets

Aplikasi menggunakan beberapa sheet utama:

```text
USERS
ACTIVITIES
SETTINGS
AUDIT_LOG
```

### USERS

Menyimpan akun pengguna, role, status, serta data autentikasi.

Contoh struktur:

```text
USERNAME
PASSWORD_HASH
PASSWORD_SALT
EMAIL
NAMA
ROLE
STATUS
```

### ACTIVITIES

Menyimpan seluruh pencatatan kegiatan kerja.

Contoh data:

```text
ID
TIMESTAMP
EMAIL
NAMA
TANGGAL
JAM_MULAI
JAM_SELESAI
DURASI_MENIT
KATEGORI
AKTIVITAS
STATUS
CATATAN
USERNAME
```

### SETTINGS

Menyimpan pengaturan aplikasi seperti jam kerja dan parameter waktu.

### AUDIT_LOG

Menyimpan riwayat aktivitas administrasi dan perubahan data.

## Instalasi

### 1. Buat Google Spreadsheet

Buat satu Google Spreadsheet sebagai database aplikasi.

### 2. Buka Apps Script

Dari Google Spreadsheet:

```text
Ekstensi → Apps Script
```

Masukkan file:

```text
Code.gs
index.html
```

### 3. Jalankan Setup

Di Apps Script pilih fungsi:

```text
setup
```

Kemudian klik **Run**.

### 4. Deploy sebagai Web App

Pilih:

```text
Deploy
→ New deployment
→ Web app
```

Setelah deploy, gunakan URL Web App:

```text
https://script.google.com/macros/s/XXXXXXXXXXXX/exec
```

## Login Awal

Gunakan akun ADMIN yang sudah dikonfigurasi pada sheet `USERS`.

Untuk keamanan, **jangan menyimpan password ADMIN di repository GitHub**.

Jika password ADMIN perlu di-reset, gunakan fungsi reset password yang tersedia pada versi `Code.gs` yang digunakan.

## Penggunaan

### Mencatat pekerjaan yang sedang dimulai

1. Login.
2. Buka **Input Kegiatan**.
3. Pilih kategori DAILY, WEEKLY, atau MONTHLY.
4. Isi aktivitas.
5. Simpan kegiatan sebagai **MASIH PROSES**.
6. Setelah pekerjaan selesai, tekan **Selesai**.
7. Sistem mengisi jam selesai dan menghitung durasi.

### Jika lupa mencatat

Gunakan menu **Input Terlewat**.

Masukkan:

- tanggal
- kategori
- jam mulai
- jam selesai
- aktivitas
- status
- catatan

Durasi dihitung berdasarkan jam mulai dan jam selesai.

## Keamanan

- Login menggunakan username + password.
- Password tidak disimpan sebagai teks biasa.
- Hak akses dibedakan berdasarkan role.
- Fungsi administrasi dilindungi oleh pengecekan role.
- Penghapusan user tidak menghapus histori aktivitas.
- Aktivitas penting dicatat dalam `AUDIT_LOG`.
- Akun ADMIN terakhir dilindungi dari penghapusan / penonaktifan.
- Akun yang sedang login dilindungi dari penghapusan.

## Catatan Deployment

Setelah melakukan perubahan kode:

```text
Save
→ Deploy
→ Manage deployments
→ Edit
→ New version
→ Deploy
```

Kemudian buka kembali URL `/exec`.

## Favicon

Logo aplikasi dapat digunakan sebagai favicon dengan menambahkan elemen berikut pada `<head>`:

```html
<link rel="icon" type="image/png" href="URL-LOGO.png">
```

## Status Project

✅ Login Username + Password  
✅ Password visibility toggle  
✅ Dashboard  
✅ Input Kegiatan  
✅ Penyelesaian kegiatan otomatis  
✅ Input kegiatan terlewat  
✅ DAILY / WEEKLY / MONTHLY  
✅ Data Saya  
✅ Rekap harian / mingguan / bulanan  
✅ Manajemen User  
✅ Master Data  
✅ Audit Log  
✅ Role-based access

---

## Lisensi

Project internal untuk kebutuhan pencatatan dan monitoring kegiatan kerja.

Hak penggunaan, perubahan, dan distribusi mengikuti kebijakan pemilik project.
