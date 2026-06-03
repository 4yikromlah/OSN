<div align="center">

# SMASA-Online CBT

**Sistem Ujian Berbasis Komputer (Computer Based Test)**

Platform ujian daring modern dengan integrasi AI Gemini untuk generasi soal otomatis, import soal dari dokumen Word, dan tampilan Neumorphism + Glassmorphism + Claymorphism.

[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-6-646CFF?logo=vite)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?logo=tailwindcss)](https://tailwindcss.com/)
[![Gemini AI](https://img.shields.io/badge/Gemini_AI-API-4285F4?logo=google)](https://ai.google.dev/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

</div>

---

## Daftar Isi

- [Fitur Utama](#fitur-utama)
- [Tech Stack](#tech-stack)
- [Prasyarat](#prasyarat)
- [Instalasi & Menjalankan](#instalasi--menjalankan)
- [Konfigurasi](#konfigurasi)
- [Struktur Proyek](#struktur-proyek)
- [Akun Default](#akun-default)
- [Deployment](#deployment)
- [Screenshot](#screenshot)
- [Kontribusi](#kontribusi)
- [Lisensi](#lisensi)

---

## Fitur Utama

### Portal Siswa
- Login dengan username dan password yang telah didaftarkan admin
- Memilih paket ujian aktif yang tersedia
- Mengerjakan ujian dengan timer countdown otomatis
- Navigasi antar soal dengan nomor soal interaktif
- Auto-submit saat waktu habis
- Melihat hasil ujian beserta pembahasan tiap soal

### Portal Guru
- Login khusus guru dengan akses berdasarkan mata pelajaran
- Melihat dan mengelola ujian sesuai mata pelajaran yang diampu
- Melihat hasil ujian siswa per mata pelajaran
- Mengelola data siswa

### Panel Admin
- Manajemen paket ujian (buat, edit, hapus, aktifkan/nonaktifkan)
- Manambahkan soal secara manual (5 pilihan A-E, kunci jawaban, pembahasan)
- **Generasi soal otomatis dengan AI Gemini** (tentukan topik, tingkat kesulitan, jumlah soal)
- **Import soal dari file Microsoft Word (.docx)** dengan format terstruktur
- Import soal dari teks yang disalin-tempel (copy-paste)
- Download template soal format .docx
- Manajemen akun siswa (tambah manual, import CSV, edit, hapus)
- Manajemen akun guru (tambah, edit, hapus)
- Rekap hasil ujian dengan fitur ekspor CSV
- Pencarian dan filter data siswa, guru, dan hasil ujian

### Desain UI/UX
- Desain **Neumorphism** (efek timbul dan tenggelam pada elemen)
- Desain **Glassmorphism** (efek kaca transparan pada header dan panel)
- Desain **Claymorphism** (efek 3D clay pada tombol dan card)
- Animasi halus dengan Framer Motion
- Jam real-time di header
- Responsif untuk mobile dan desktop

---

## Tech Stack

| Teknologi | Versi | Kegunaan |
|-----------|-------|----------|
| React | 19 | Library UI |
| TypeScript | 5.8 | Type safety |
| Vite | 6 | Build tool & dev server |
| Express.js | 4 | Backend server |
| Tailwind CSS | 4 | Styling framework |
| Google Gemini AI | 2.4 | Generasi soal otomatis |
| Mammoth.js | 1.12 | Parser file Word (.docx) |
| Docx.js | 9.7 | Generator file Word (.docx) |
| Lucide React | 0.546 | Ikon UI |
| Framer Motion | 12 | Animasi UI |

---

## Prasyarat

- **Node.js** versi 18 atau lebih baru
- **npm** versi 9 atau lebih baru
- **API Key Google Gemini** (untuk fitur AI) - Dapatkan di [Google AI Studio](https://aistudio.google.com/apikey)

---

## Instalasi & Menjalankan

### 1. Clone Repository

```bash
git clone https://github.com/USERNAME/smasa-online-cbt.git
cd smasa-online-cbt
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Konfigurasi Environment

Salin file `.env.example` menjadi `.env` dan isi API key Gemini:

```bash
cp .env.example .env
```

Edit file `.env`:
```
GEMINI_API_KEY="API_KEY_KAMU_DISINI"
```

### 4. Jalankan dalam Mode Development

```bash
npm run dev
```

Buka browser di `http://localhost:3000`

### 5. Build untuk Production

```bash
npm run build
```

### 6. Jalankan Production Server

```bash
npm start
```

---

## Konfigurasi

### Environment Variables

| Variable | Wajib | Default | Deskripsi |
|----------|-------|---------|-----------|
| `GEMINI_API_KEY` | Ya | - | API key Google Gemini untuk fitur generasi soal AI |
| `PORT` | Tidak | 3000 | Port server Express |

### Catatan Penting
- Tanpa `GEMINI_API_KEY`, fitur generasi soal AI tidak akan berfungsi, tetapi fitur lainnya tetap berjalan normal
- Data ujian, siswa, dan guru disimpan di `localStorage` browser (client-side storage)
- Untuk penggunaan multi-device, diperlukan integrasi database di backend

---

## Struktur Proyek

```
smasa-online-cbt/
├── server.ts                    # Express server + API endpoint Gemini
├── vite.config.ts               # Konfigurasi Vite
├── tsconfig.json                # Konfigurasi TypeScript
├── index.html                   # Entry point HTML
├── package.json                 # Dependencies & scripts
├── .env.example                 # Template environment variables
├── .gitignore                   # Git ignore rules
├── LICENSE                      # MIT License
├── README.md                    # Dokumentasi proyek
├── Dockerfile                   # Konfigurasi Docker
├── docker-compose.yml           # Docker Compose config
├── railway.json                 # Railway deployment config
└── src/
    ├── main.tsx                 # Entry point React
    ├── App.tsx                  # Komponen utama aplikasi
    ├── index.css                # Global styles + Neumorphism/Glassmorphism/Claymorphism
    ├── types.ts                 # TypeScript type definitions
    ├── vite-env.d.ts            # Vite type declarations
    ├── assets/
    │   └── images/
    │       └── smasa_logo_*.png # Logo SMASA
    ├── components/
    │   ├── Header.tsx           # Header dengan jam real-time
    │   ├── MetricCard.tsx       # Card statistik dengan tema warna
    │   └── WordImportHelper.tsx # Komponen import soal dari Word/teks
    ├── lib/
    │   └── storage.ts           # CRUD localStorage + data default
    └── utils/
        └── wordParser.ts        # Parser teks soal & file .docx
```

---

## Akun Default

Aplikasi dilengkapi data bawaan untuk pengujian awal:

### Admin
| Username | Password |
|----------|----------|
| - | `admin321` atau `Admin123` |

### Guru
| Username | Nama | Password | Mata Pelajaran |
|----------|------|----------|----------------|
| mulyadi | Drs. Mulyadi | guru | Matematika |
| sari | Sari Wahyuni, S.Pd | guru | Bahasa Indonesia |

### Siswa
| Username | Nama | Password | Mata Pelajaran |
|----------|------|----------|----------------|
| ahmadsudjiwo | Ahmad Sudjiwo | siswa | Matematika |
| rianasafitri | Riana Safitri | siswa | Bahasa Indonesia |

### Paket Ujian Default
1. **PAS - Matematika Dasar** (5 soal, 15 menit) - Aktif
2. **PH - Tata Bahasa Indonesia** (2 soal, 10 menit) - Aktif

> **Penting**: Segera ganti password default setelah deployment di lingkungan produksi!

---

## Deployment

### Vercel (Serverless)

Proyek ini menggunakan Express.js server, sehingga untuk Vercel diperlukan konfigurasi tambahan. Disarankan menggunakan Railway atau Render untuk deployment full-stack.

### Railway

1. Fork/clone repository ini ke GitHub
2. Buka [Railway.app](https://railway.app/) dan login
3. Klik "New Project" > "Deploy from GitHub repo"
4. Pilih repository ini
5. Tambahkan environment variable `GEMINI_API_KEY` di tab Variables
6. Railway akan otomatis mendeteksi dan menjalankan build

File `railway.json` sudah tersedia untuk konfigurasi otomatis.

### Render

1. Buka [Render.com](https://render.com/) dan login
2. Klik "New" > "Web Service"
3. Hubungkan repository GitHub
4. Set Build Command: `npm run build`
5. Set Start Command: `npm start`
6. Tambahkan environment variable `GEMINI_API_KEY`
7. Deploy

### Docker

```bash
# Build image
docker build -t smasa-online-cbt .

# Jalankan container
docker run -p 3000:3000 -e GEMINI_API_KEY=your_api_key smasa-online-cbt
```

Atau menggunakan Docker Compose:

```bash
# Edit GEMINI_API_KEY di docker-compose.yml terlebih dahulu
docker-compose up -d
```

### Manual VPS

```bash
# Clone dan build
git clone https://github.com/USERNAME/smasa-online-cbt.git
cd smasa-online-cbt
npm install
npm run build

# Set environment variables
export GEMINI_API_KEY="your_api_key"
export PORT=3000
export NODE_ENV=production

# Jalankan dengan PM2 (recommended)
npm install -g pm2
pm2 start dist/server.cjs --name smasa-cbt
pm2 save
pm2 startup
```

---

## Screenshot

### Login Page
Halaman login dengan 3 portal: Siswa, Guru, dan Admin. Desain Neumorphism dengan tab selector bertema Claymorphism.

### Dashboard Admin
Dashboard admin dengan metric cards, manajemen ujian, soal, siswa, dan guru. Fitur import soal dari Word dan generasi AI.

### Ujian Aktif
Tampilan ujian dengan timer countdown, navigasi nomor soal, dan pilihan jawaban A-E.

### Hasil Ujian
Review hasil ujian dengan skor, detail jawaban benar/salah, dan pembahasan.

---

## Kontribusi

Kontribusi sangat diterima! Silakan ikuti langkah berikut:

1. Fork repository ini
2. Buat branch fitur baru (`git checkout -b fitur-baru`)
3. Commit perubahan (`git commit -m 'Menambahkan fitur baru'`)
4. Push ke branch (`git push origin fitur-baru`)
5. Buat Pull Request

---

## Lisensi

Proyek ini dilisensikan di bawah [MIT License](LICENSE).

---

<div align="center">

**SMASA-Online CBT** - Dibangun untuk kemajuan pendidikan Indonesia

</div>
