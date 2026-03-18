<div align="center">

<br/>

# 📚 MyLibrary

### *Generate QR Codes and convert text to PDF — simple, fast, and offline.*

<br/>

[![Java](https://img.shields.io/badge/Java-Android-ED8B00?style=flat-square&logo=openjdk&logoColor=white)](https://www.java.com/)
[![Android](https://img.shields.io/badge/Android-API_15+-3DDC84?style=flat-square&logo=android&logoColor=white)](https://developer.android.com/)
[![ZXing](https://img.shields.io/badge/ZXing-3.2.1-4285F4?style=flat-square)](https://github.com/zxing/zxing)
[![iTextPDF](https://img.shields.io/badge/iTextPDF-5.5.10-E74C3C?style=flat-square)](https://itextpdf.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)

<br/>

> Aplikasi Android sederhana yang menggabungkan dua utilitas penting:
> **Generator QR Code** dari teks dan **Generator PDF** dari tulisan —
> bekerja sepenuhnya secara offline tanpa koneksi internet.

<br/>

> A simple Android utility app combining two essential tools:
> **QR Code Generator** from text input and **Text-to-PDF Generator** —
> works fully offline without any internet connection.

<br/>

---

</div>

## 📋 Daftar Isi / Table of Contents

- [Tentang Aplikasi / About](#-tentang-aplikasi--about)
- [Fitur / Features](#-fitur--features)
- [Tech Stack & Libraries](#-tech-stack--libraries)
- [Cara Kerja / How It Works](#-cara-kerja--how-it-works)
- [Memulai / Getting Started](#-memulai--getting-started)
- [Struktur Proyek / Project Structure](#-struktur-proyek--project-structure)
- [Permissions](#-permissions)
- [Keterbatasan & Ide Pengembangan](#-keterbatasan--ide-pengembangan--limitations--future-development)
- [Kontribusi / Contributing](#-kontribusi--contributing)
- [Kontak / Contact](#-kontak--contact)
- [Lisensi / License](#-lisensi--license)

<br/>

---

## 🌟 Tentang Aplikasi / About

**🇮🇩 Bahasa Indonesia**

**MyLibrary** adalah aplikasi Android ringan yang dibangun menggunakan **Java** dengan dua fitur utama: generator QR Code dari teks secara instan, dan generator file PDF dari tulisan yang langsung tersimpan ke penyimpanan perangkat. Aplikasi ini bekerja **100% offline** tanpa memerlukan koneksi internet.

**🇬🇧 English**

**MyLibrary** is a lightweight Android application built with **Java** featuring two core utilities: an instant QR Code generator from text input, and a text-to-PDF file generator that saves directly to device storage. The app works **100% offline** with no internet connection required.

<br/>

---

## ✨ Fitur / Features

### 🔲 QR Code Generator
- Input teks bebas melalui kolom teks / Free text input via text field
- Generate QR Code instan dengan satu klik / Instant QR Code generation with one tap
- Tampilan QR Code langsung di layar / QR Code displayed directly on screen
- Output Bitmap resolusi tinggi 500×500 pixel / High-resolution 500×500px Bitmap output
- Didukung library **ZXing** (Zebra Crossing)

### 📄 Text to PDF Generator
- Input teks multi-baris / Multi-line text input
- Generate file PDF dan simpan otomatis ke `/Documents/PDFgenerate.pdf`
- Preview PDF langsung setelah generate via PDF viewer bawaan perangkat / Auto-preview after generation via device PDF viewer
- Validasi input — mencegah generate PDF kosong / Input validation — prevents empty PDF generation
- Manajemen permission storage runtime / Runtime storage permission management

<br/>

---

## 🛠 Tech Stack & Libraries

| Kategori | Library / Tool | Versi |
|---|---|---|
| **Language** | Java | - |
| **Min SDK** | API 15 (Android 4.0.3 Ice Cream Sandwich) | - |
| **Target SDK** | API 29 (Android 10) | - |
| **UI** | XML Layouts, AppCompat, ConstraintLayout | 1.1.0 / 1.1.3 |
| **QR Code** | [ZXing (Zebra Crossing)](https://github.com/zxing/zxing) | 3.2.1 |
| **PDF Generator** | [iText for Android (itextg)](https://itextpdf.com/) | 5.5.10 |
| **Testing** | JUnit, Espresso | 4.12 / 3.2.0 |

<br/>

---

## ⚙️ Cara Kerja / How It Works

### 🔲 QR Code Generator

```
Pengguna input teks
        ↓
Tombol "GENERATE KODE" ditekan
        ↓
ZXing MultiFormatWriter.encode()
mengkonversi teks → BitMatrix (500x500)
        ↓
BitMatrix dikonversi ke Bitmap ARGB_4444
(pixel hitam = QR data, putih = background)
        ↓
Bitmap ditampilkan di ImageView
```

### 📄 Text to PDF Generator

```
Pengguna input teks multi-baris
        ↓
Tombol "GENERATE TO PDF" ditekan
        ↓
Cek & minta permission WRITE_EXTERNAL_STORAGE
        ↓
Buat folder /Documents jika belum ada
        ↓
iText Document dibuka → Paragraph ditambahkan
        ↓
Document di-close → File PDF tersimpan
        ↓
Intent ACTION_VIEW membuka PDF viewer
```

<br/>

---

## 🚀 Memulai / Getting Started

### Prasyarat / Prerequisites

- [Android Studio](https://developer.android.com/studio) versi terbaru / latest version
- JDK 8+
- Android device atau emulator **API 15+** (Android 4.0.3+)

### Instalasi / Installation

```bash
# 1. Clone repository
git clone https://github.com/Fajarlaksana/MyLibrary.git

# 2. Buka di Android Studio
# File → Open → pilih folder MyLibrary

# 3. Sync Gradle
# Android Studio akan otomatis menawarkan Gradle sync

# 4. Run aplikasi
# Klik tombol ▶ Run atau tekan Shift+F10
```

### Penggunaan / Usage

**🔲 QR Code Generator:**
1. Dari `PdfActivity` (layar utama), navigasi ke `MainActivity`
2. Ketik teks yang ingin di-encode di kolom input
3. Tekan tombol **"GENERATE KODE"**
4. QR Code langsung muncul di layar

**📄 Text to PDF:**
1. Buka aplikasi — `PdfActivity` adalah launcher activity
2. Ketik teks di kolom multi-baris
3. Tekan tombol **"GENERATE TO PDF"**
4. Izinkan akses storage jika diminta
5. PDF tersimpan di `/Documents/PDFgenerate.pdf` dan langsung terbuka

<br/>

---

## 📁 Struktur Proyek / Project Structure

```
MyLibrary/
│
├── 📄 build.gradle                        # Project-level Gradle config
├── 📄 settings.gradle                     # Project settings
├── 📄 gradle.properties                   # Gradle properties
├── 📄 gradlew / gradlew.bat               # Gradle wrapper scripts
│
├── 📂 gradle/wrapper/                     # Gradle wrapper files
│
└── 📂 app/
    ├── build.gradle                       # Dependencies, SDK versions & build config
    ├── proguard-rules.pro                 # ProGuard rules
    │
    └── 📂 src/main/
        ├── AndroidManifest.xml            # Manifest: permissions & activity declarations
        │
        ├── 📂 java/com/example/mylibrary/
        │   │
        │   ├── MainActivity.java          # 🔲 QR Code Generator
        │   │                              #    ZXing MultiFormatWriter → BitMatrix → Bitmap
        │   │                              #    Ditampilkan via ImageView
        │   │
        │   └── PdfActivity.java           # 📄 Text to PDF Generator (Launcher)
        │                                  #    iText Document & PdfWriter
        │                                  #    Runtime permission handler
        │                                  #    Intent ACTION_VIEW untuk preview PDF
        │
        └── 📂 res/
            ├── 📂 layout/
            │   ├── activity_main.xml         # Layout QR: EditText + Button + ImageView
            │   └── activity_text_to_pdf.xml  # Layout PDF: MultiLine EditText + Button
            │
            ├── 📂 drawable/                  # App launcher background icon
            ├── 📂 drawable-v24/              # Adaptive launcher foreground icon (API 24+)
            └── 📂 values/
                ├── colors.xml                # Warna: colorPrimary, CodeBlackColor, CodeWhiteColor
                ├── strings.xml               # String resources (app_name: "MyLibrary")
                └── styles.xml                # AppTheme & style definitions
```

<br/>

---

## 🔐 Permissions

| Permission | Digunakan oleh / Used by | Kegunaan / Purpose |
|---|---|---|
| `WRITE_EXTERNAL_STORAGE` | `PdfActivity` | Menyimpan file PDF ke folder `/Documents` / Save PDF to `/Documents` |
| `READ_EXTERNAL_STORAGE` | `PdfActivity` | Membaca file PDF untuk preview / Read PDF for preview |

> ℹ️ Permission `WRITE_EXTERNAL_STORAGE` dikelola secara **runtime** pada Android 6.0+ dengan dialog konfirmasi sebelum generate PDF pertama kali.

<br/>

---

## 🚧 Keterbatasan & Ide Pengembangan / Limitations & Future Development

**🇮🇩 Keterbatasan saat ini:**
- Nama file PDF selalu `PDFgenerate.pdf` — file sebelumnya akan tertimpa
- QR Code tidak bisa langsung disimpan ke galeri atau di-share
- Belum ada navigasi in-app yang eksplisit antara halaman QR dan PDF
- UI menggunakan layout dasar tanpa Material Design modern

**🇬🇧 Current limitations:**
- PDF filename is always `PDFgenerate.pdf` — previous file will be overwritten
- QR Code cannot be saved to gallery or shared directly from the app
- No explicit in-app navigation between QR Code and PDF screens
- UI uses basic layouts without modern Material Design

### 💡 Ide Pengembangan / Development Ideas

| Prioritas | Ide / Idea |
|---|---|
| 🔴 **High** | Simpan & share QR Code ke galeri / Save & share QR Code to gallery |
| 🔴 **High** | Nama file PDF custom oleh pengguna / User-defined PDF filename |
| 🟡 **Medium** | Bottom Navigation antara QR & PDF / Bottom Navigation between QR & PDF |
| 🟡 **Medium** | Migrasi UI ke Material Design 3 |
| 🟡 **Medium** | Migrasi bahasa ke Kotlin / Migrate codebase to Kotlin |
| 🟢 **Low** | Format PDF kustom: font, ukuran, warna / Custom PDF formatting |
| 🟢 **Low** | Riwayat QR Code yang pernah dibuat / QR Code generation history |

<br/>

---

## 🤝 Kontribusi / Contributing

**🇮🇩** Kontribusi sangat disambut! Silakan buat issue atau pull request.

**🇬🇧** Contributions are welcome! Feel free to open an issue or submit a pull request.

```bash
# 1. Fork repository ini / Fork this repository

# 2. Buat branch baru / Create a new branch
git checkout -b feature/nama-fitur

# 3. Commit perubahan / Commit your changes
git commit -m "feat: tambah fitur X"

# 4. Push ke branch / Push to branch
git push origin feature/nama-fitur

# 5. Buka Pull Request / Open a Pull Request
```

<br/>

---

## 📬 Kontak / Contact

**🇮🇩** Jika ada pertanyaan atau ingin berkolaborasi, silakan hubungi:

**🇬🇧** For questions or collaboration, feel free to reach out:

<div align="center">

**Fajar Laksana**

📧 [fajarlaksana13@gmail.com](mailto:fajarlaksana13@gmail.com)

🔗 [github.com/Fajarlaksana](https://github.com/Fajarlaksana)

</div>

<br/>

---

## 📄 Lisensi / License

**🇮🇩** Didistribusikan di bawah lisensi MIT. Lihat [`LICENSE`](LICENSE) untuk informasi lebih lanjut.

**🇬🇧** Distributed under the MIT License. See [`LICENSE`](LICENSE) for more information.

<br/>

---

<div align="center">

Dibangun dengan ☕ menggunakan **Java** & **Android SDK**

*MyLibrary — Generate. Save. Share.*

</div>
