# Panduan Setup Environment Variables & Layanan Cloud Gratis
**Project:** AKARA — AI Career Platform  
**Target:** 100% Gratis Permanen (*Free Tier* Tanpa Kartu Kredit)

Dokumen ini memandu Rozi dan Diki dalam menyiapkan file `.env` di folder `server/` dan `client/` serta cara mendapatkan koneksi database PostgreSQL (Neon) dan API Key AI (Google Gemini) dalam waktu kurang dari 3 menit.

---

## 1. File Template `.env`

### A. Backend (`server/.env`)
Buat file bernama `.env` di dalam folder `server/`:

```env
# Port server Express lokal
PORT=5000
NODE_ENV=development

# URL Frontend untuk izin CORS
CORS_ORIGIN=http://localhost:5173

# Koneksi Database Neon PostgreSQL (Pooler URL untuk query harian)
DATABASE_URL="postgresql://neondb_owner:PASSWORD@ep-sample-pooler.us-east-2.aws.neon.tech/neondb?sslmode=require&pgbouncer=true"

# Koneksi Direct Neon PostgreSQL (Direct URL khusus untuk migrasi Prisma)
DIRECT_URL="postgresql://neondb_owner:PASSWORD@ep-sample.us-east-2.aws.neon.tech/neondb?sslmode=require"

# API Key Google Gemini (Model: gemini-2.5-flash)
GEMINI_API_KEY="AIzaSyYourGeminiApiKeyHere"

# Secret Key JWT (Opsional untuk Fase 2)
JWT_SECRET="akara_super_secret_jwt_key_2026"
```

---

### B. Frontend (`client/.env`)
Buat file bernama `.env` di dalam folder `client/`:

```env
# Alamat Backend API lokal
VITE_API_BASE_URL=http://localhost:5000/api
```

---

## 2. Panduan 2 Menit Mendapatkan Akun & API Key Gratis

### Langkah 1: Mendapatkan Database Neon PostgreSQL Gratis (Tanpa Kartu Kredit)
1. Buka situs resmi **[https://neon.tech/](https://neon.tech/)**.
2. Klik tombol **"Sign Up"** dan pilih **Continue with GitHub** (login menggunakan akun GitHub kalian).
3. Setelah masuk ke dashboard, klik **"Create Project"**:
   - Project Name: `akara-db`
   - Database Name: `neondb`
   - Region: Pilih yang terdekat, misal `Singapore (ap-southeast-1)` atau `US East`.
4. Begitu selesai dibuat, layar dashboard akan langsung menampilkan kotak **Connection Details**:
   - Pilih dropdown mode: **Prisma**.
   - Salin string koneksi yang memiliki tanda `?sslmode=require&pgbouncer=true` dan paste ke `DATABASE_URL` di `server/.env`.
   - Pilih tab koneksi **Direct connection** (tanpa pgbouncer), lalu salin ke `DIRECT_URL` di `server/.env`.

---

### Langkah 2: Mendapatkan API Key Google Gemini Gratis (Tanpa Kartu Kredit)
1. Buka situs resmi Google AI Studio: **[https://aistudio.google.com/](https://aistudio.google.com/)**.
2. Login menggunakan akun Gmail / Google pribadi kalian.
3. Di panel sebelah kiri atas, klik tombol biru **"Get API key"**.
4. Klik **"Create API key"** -> pilih **"Create API key in new project"**.
5. Tunggu 5 detik, Google akan memunculkan string token (diawali huruf `AIzaSy...`).
6. Klik tombol **Copy**, lalu paste ke variabel `GEMINI_API_KEY` di `server/.env`.

> [!NOTE]
> Kuota gratis Google Gemini untuk model `gemini-2.5-flash` adalah **±500 request per hari (15 RPM)** secara gratis permanen tanpa perlu memasukkan kartu kredit sama sekali. Ini lebih dari cukup untuk tahap development dan demo pengujian.

---

## 3. Verifikasi Koneksi Database

Setelah file `server/.env` terisi dengan URL Neon, buka terminal di folder `server/` dan jalankan perintah verifikasi:

```bash
# 1. Generate Prisma Client
npx prisma generate

# 2. Uji migrasi skema tabel ke Neon DB
npx prisma migrate dev --name init_database

# 3. Buka GUI browser untuk memastikan tabel sudah terbentuk
npx prisma studio
```

Jika browser berhasil membuka **Prisma Studio** pada `http://localhost:5555` dan menampilkan daftar tabel `Question`, `Career`, `TestSession`, dan `Result`, maka **seluruh setup backend dan database dinyatakan 100% SUKSES dan siap digunakan!**
