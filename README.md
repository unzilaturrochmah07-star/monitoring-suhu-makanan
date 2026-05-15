# Boiler Monitoring Web

Sistem monitoring suhu industri berbasis Rust yang digunakan untuk memantau kondisi suhu boiler secara realtime melalui terminal. Program ini mensimulasikan pembacaan sensor suhu dan menampilkan status kondisi suhu industri secara otomatis.

---

## Deskripsi Project

Project ini dibuat untuk membantu proses monitoring suhu pada sistem industri secara realtime. Sistem akan membaca nilai suhu yang disimulasikan, kemudian menampilkan status kondisi boiler seperti NORMAL, WARNING, atau OVERHEAT.

Project ini dikembangkan menggunakan bahasa Rust karena memiliki performa tinggi, keamanan memori yang baik, serta cocok digunakan untuk sistem monitoring dan embedded system.

---

## Fitur Program

- Monitoring suhu realtime
- Simulasi pembacaan sensor suhu
- Tampilan dashboard terminal
- Deteksi kondisi suhu tinggi
- Status kondisi suhu otomatis
- Program berjalan secara kontinu (looping)

---

## Teknologi yang Digunakan

- Rust
- Cargo
- Terminal CLI

---

## Struktur Folder

```bash
boiler-monitoring-web
│
├── src
│   └── main.rs
│
├── Cargo.toml
└── README.md
```

---

## Cara Menjalankan Program

### 1. Install Rust

Download Rust melalui website resmi:

[Rust Official Website](https://www.rust-lang.org/tools/install?utm_source=chatgpt.com)

Pastikan instalasi berhasil:

```bash
rustc --version
cargo --version
```

---

### 2. Clone Repository

```bash
git clone https://github.com/username/boiler-monitoring-web.git
```

---

### 3. Masuk ke Folder Project

```bash
cd boiler-monitoring-web
```

---

### 4. Jalankan Program

```bash
cargo run
```

---

## Cara Kerja Sistem

1. Sistem membaca nilai suhu boiler
2. Suhu ditampilkan pada terminal
3. Sistem menentukan status suhu:
   - NORMAL
   - WARNING
   - OVERHEAT
4. Monitoring berjalan secara realtime menggunakan looping

---

## Contoh Output Program

```bash
=============================
   MONITORING SUHU BOILER
=============================

Suhu Boiler : 72°C
Status      : NORMAL

Suhu Boiler : 91°C
Status      : WARNING

Suhu Boiler : 105°C
Status      : OVERHEAT
```

---

## Algoritma Sistem

1. Mulai program
2. Inisialisasi variabel suhu
3. Membaca data suhu
4. Menampilkan suhu pada terminal
5. Mengecek kondisi suhu
6. Menampilkan status suhu
7. Mengulang proses monitoring

---

## Konsep Pemrograman yang Digunakan

### 1. Looping
Digunakan untuk menjalankan monitoring secara terus menerus.

### 2. Conditional Statement
Menggunakan `if`, `else if`, dan `else` untuk menentukan status suhu.

### 3. Function
Digunakan untuk memisahkan proses monitoring agar kode lebih rapi.

### 4. Variable
Digunakan untuk menyimpan data suhu dan status sistem.

---

## Tujuan Project

- Mempelajari dasar bahasa Rust
- Memahami sistem monitoring industri
- Mengimplementasikan logika kontrol suhu sederhana
- Melatih penggunaan realtime monitoring pada terminal

---

## Pengembangan Selanjutnya

- Integrasi sensor suhu asli
- Penyimpanan data monitoring
- Tampilan GUI/Web Dashboard
- Integrasi database
- Notifikasi otomatis

---

## Author

Project dibuat untuk tugas Sistem Instrumentasi dan Pemrograman Rust.
