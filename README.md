# Boiler Monitoring Web

Sistem monitoring suhu industri berbasis Rust untuk memantau suhu pada food industry secara realtime menggunakan file log sensor (`sensor_log.csv`). Program akan membaca data suhu, menampilkan status kondisi suhu, dan melakukan monitoring secara otomatis melalui terminal.

---

## Deskripsi Project

Project ini dibuat untuk mensimulasikan sistem monitoring suhu pada industri makanan (food industry). Sistem membaca data suhu dari file CSV kemudian menampilkan kondisi suhu secara realtime dengan status:

- NORMAL
- WARNING
- CRITICAL

Program dibuat menggunakan bahasa Rust karena memiliki performa tinggi, aman terhadap memory leak, dan cocok digunakan untuk sistem monitoring industri.

---

## Fitur Program

- Monitoring suhu realtime
- Membaca data dari file CSV
- Tampilan terminal interaktif
- Deteksi status suhu otomatis
- Simulasi sensor suhu industri
- Delay monitoring realtime

---

## Teknologi yang Digunakan

- Rust
- Cargo
- File CSV
- Terminal CLI

---

## Struktur Folder

```bash
boiler-monitoring-web
│
├── src
│   └── main.rs
│
├── sensor_log.csv
├── Cargo.toml
└── README.md
```

---

## Cara Menjalankan Program

### 1. Install Rust

Download Rust melalui website resmi:

[Rust Official Website](https://www.rust-lang.org/tools/install?utm_source=chatgpt.com)

Cek instalasi:

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

## Format File sensor_log.csv

Contoh isi file:

```csv
08:00,2.5
08:01,5.7
08:02,-2.0
08:03,9.1
```

Keterangan:
- Kolom pertama = waktu monitoring
- Kolom kedua = suhu (°C)

---

## Source Code Program

```rust
use std::{
    fs::File,
    io::{BufRead, BufReader},
    thread,
    time::Duration,
};

#[derive(Debug)]
struct SensorData {
    timestamp: String,
    suhu: f32,
}

fn baca_data_sensor(path: &str) -> Vec<SensorData> {
    let file = match File::open(path) {
        Ok(f) => f,
        Err(_) => {
            println!("❌ File sensor_log.csv tidak ditemukan di path: {}", path);
            return Vec::new();
        }
    };

    let reader = BufReader::new(file);
    let mut data = Vec::new();

    for line in reader.lines() {
        if let Ok(line) = line {
            let parts: Vec<&str> = line.split(',').collect();

            if parts.len() == 2 {
                let timestamp = parts[0].trim().to_string();
                let suhu = parts[1].trim().parse::<f32>().unwrap_or(0.0);

                data.push(SensorData { timestamp, suhu });
            }
        }
    }

    data
}

fn cek_status_suhu(suhu: f32) -> &'static str {
    if (0.0..=4.0).contains(&suhu) {
        "NORMAL ❄️"
    } else if (-5.0..0.0).contains(&suhu) || (4.1..=8.0).contains(&suhu) {
        "WARNING ⚠️"
    } else {
        "CRITICAL 🔥"
    }
}

fn main() {
    let path = "sensor_log.csv";
    let data_sensor = baca_data_sensor(path);

    println!("\n==============================");
    println!(" SISTEM MONITORING SUHU FOOD INDUSTRY ");
    println!("==============================\n");

    if data_sensor.is_empty() {
        println!("⚠️ Tidak ada data sensor untuk ditampilkan.");
        return;
    }

    for data in data_sensor {
        let status = cek_status_suhu(data.suhu);

        println!(
            "[{}] Suhu: {:>5.2}°C | Status: {}",
            data.timestamp,
            data.suhu,
            status
        );

        thread::sleep(Duration::from_millis(700));
    }

    println!("\n✅ Monitoring selesai.");
}
```

---

## Cara Kerja Sistem

1. Program membaca file `sensor_log.csv`
2. Data suhu diproses satu per satu
3. Sistem menentukan status suhu:
   - NORMAL ❄️
   - WARNING ⚠️
   - CRITICAL 🔥
4. Data ditampilkan pada terminal secara realtime
5. Program berhenti setelah semua data selesai dibaca

---

## Penjelasan Status Suhu

| Rentang Suhu | Status |
|---|---|
| 0°C – 4°C | NORMAL ❄️ |
| -5°C – 0°C atau 4.1°C – 8°C | WARNING ⚠️ |
| < -5°C atau > 8°C | CRITICAL 🔥 |

---

## Contoh Output Program

```bash
==============================
 SISTEM MONITORING SUHU FOOD INDUSTRY
==============================

[08:00] Suhu:  2.50°C | Status: NORMAL ❄️
[08:01] Suhu:  5.70°C | Status: WARNING ⚠️
[08:02] Suhu: -2.00°C | Status: WARNING ⚠️
[08:03] Suhu:  9.10°C | Status: CRITICAL 🔥

✅ Monitoring selesai.
```

---

## Konsep Pemrograman yang Digunakan

### 1. Struct
Digunakan untuk menyimpan data sensor:
```rust
struct SensorData
```

### 2. File Handling
Membaca data dari file CSV menggunakan:
```rust
File::open()
```

### 3. Looping
Menggunakan perulangan untuk membaca seluruh data sensor.

### 4. Conditional Statement
Menggunakan `if`, `else if`, dan `else` untuk menentukan status suhu.

### 5. Thread dan Delay
Menggunakan:
```rust
thread::sleep()
```
untuk simulasi monitoring realtime.

---

## Tujuan Project

- Mempelajari bahasa Rust
- Memahami sistem monitoring industri
- Mengimplementasikan pembacaan file CSV
- Membuat simulasi monitoring realtime
- Melatih logika pemrograman dan kontrol suhu

---

## Pengembangan Selanjutnya

- Integrasi sensor suhu asli
- Penyimpanan database
- Tampilan GUI/Web
- Grafik monitoring realtime
- Sistem alarm otomatis

---

## Author

Project dibuat untuk tugas Sistem Instrumentasi dan Pemrograman Rust.
