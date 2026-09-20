# Pembagian Tugas Fullstack (Vertical Feature Ownership)
**Project:** AKARA — AI Career Platform  
**Anggota Tim:**
1. **Rozi** (@rozi) — *Fullstack Developer*
2. **Diki** (@diki) — *Fullstack Developer*  
**Referensi Desain UI (Google Stitch):** [stitch.withgoogle.com/projects/465219332161847245](https://stitch.withgoogle.com/projects/465219332161847245)

---

## 1. Prinsip Pembagian: Fullstack Vertical Slicing

> [!IMPORTANT]
> **Tidak ada pembagian horizontal kaku.**  
> Setiap anggota memegang fitur secara **end-to-end (Fullstack)**:
> - Mendesain database schema / seed terkait;
> - Membangun endpoint Express, service logic, validasi Zod, dan dokumentasi Swagger;
> - Membangun komponen UI di React Vite, styling Tailwind + shadcn/ui, custom hook, dan integrasi TanStack Query;
> - Melakukan testing & review fitur tersebut.

---

## 1.1 Standar Alur Pengerjaan Fitur (Contract-First 6-Step Flow)

Agar proses koding terstruktur, tidak terjadi bongkar-pasang komponen UI, dan data selalu valid, setiap pengerjaan fitur wajib mengikuti urutan langkah berikut:

```text
┌─────────────────────────────────────────────────────────────────────────┐
│              ALUR KERJA FITUR (CONTRACT-FIRST DEVELOPMENT)              │
├─────────────────────────────────────────────────────────────────────────┤
│ 1. DATABASE & SEED   │ Prisma schema, migrasi database, & data awal     │
│ 2. BUSINESS SERVICE  │ Logika murni, kalkulasi, & Unit Test (Vitest)    │
│ 3. API CONTROLLER    │ Route Express, Zod validation, & Swagger test    │
│ 4. FRONTEND CLIENT   │ Interface TypeScript & fungsi pemanggil Axios    │
│ 5. QUERY HOOKS       │ Integrasi TanStack Query (cache & data fetching) │
│ 6. UI SLICING        │ Komponen tampilan Tailwind + shadcn/ui           │
└─────────────────────────────────────────────────────────────────────────┘
```

### Rincian 6 Langkah:
1. **Langkah 1 — Database & Seeding (`server/prisma/`)**:
   - Definisikan model tabel di `schema.prisma`.
   - Jalankan `npx prisma migrate dev` untuk update tabel Neon DB.
   - Buat/perbarui data awal di `prisma/seed.ts` dan jalankan `npx prisma db seed`.
2. **Langkah 2 — Business Service & Unit Test (`server/src/services/`)**:
   - Tulis logika bisnis independen pada file `*.service.ts`.
   - Buat unit test pada file `*.service.test.ts` dan pastikan lulus pengujian Vitest.
3. **Langkah 3 — Controller, Route, & Swagger (`server/src/routes/` & `controllers/`)**:
   - Pasang skema validasi request menggunakan Zod.
   - Buat route endpoint Express dan anotasi Swagger OpenAPI.
   - Uji coba endpoint via browser di `http://localhost:5000/api-docs` atau Supertest.
4. **Langkah 4 — Client Type & API Function (`client/src/features/<fitur>/api/`)**:
   - Definisikan tipe data TypeScript respon API di `types/`.
   - Buat fungsi pemanggil Axios (misal `getCareers()`, `submitAssessment()`).
5. **Langkah 5 — Custom Hook TanStack Query (`client/src/features/<fitur>/hooks/`)**:
   - Bungkus fungsi API dengan hook `useQuery` (untuk GET) atau `useMutation` (untuk POST/PUT).
   - Manfaatkan status `isLoading`, `isError`, dan `data`.
6. **Langkah 6 — UI Component Slicing & Assembly (`client/src/features/<fitur>/components/`)**:
   - Bangun tampilan menggunakan komponen `shadcn/ui` dan Tailwind CSS.
   - Hubungkan tampilan ke custom hook yang sudah dibuat pada Langkah 5.

---

## 2. Fase 0: Setup Awal Proyek

Sebelum pengerjaan fitur paralel dimulai, **Rozi bertanggung jawab menginisialisasi pondasi proyek** agar Diki langsung bisa pull dan mulai ngoding tanpa konflik konfigurasi:

### Checklist Setup Rozi:
- [ ] Inisialisasi Git Repository & remote GitHub.
- [ ] Setup struktur direktori monorepo (`client/` & `server/`).
- [ ] **Backend Setup**:
  - Inisialisasi Express + TypeScript + `tsconfig.json`.
  - Inisialisasi Prisma ORM & koneksi database Neon PostgreSQL.
  - Setup **Vitest** + **Supertest** untuk unit dan integration testing.
  - Setup konfigurasi **ESLint** & **Prettier** untuk standardisasi format kode.
  - Setup konfigurasi Swagger UI (`/api-docs`).
  - Setup standard error handling & response wrapper (`AppError`, `sendSuccess`).
  - Setup handler Vercel Serverless (`api/index.ts` & `vercel.json`).
- [ ] **Frontend Setup**:
  - Inisialisasi React + Vite + TypeScript.
  - Setup **React Router (v6/v7)** & struktur routing dasar di `routes/`.
  - Setup Tailwind CSS & konfigurasi path alias `@/*`.
  - Inisialisasi komponen dasar `shadcn/ui` (Button, Card, Dialog, Toast, Input).
  - Setup **Vitest** + **@testing-library/react** + **jsdom** untuk testing komponen & hooks.
  - Setup konfigurasi **ESLint** & **Prettier** (termasuk plugin `prettier-plugin-tailwindcss`).
  - Setup Axios client instance (`api-client.ts`) & TanStack Query Provider.
- [ ] Push branch `main` & buat branch `develop`.

---

## 3. Matriks Pembagian Fitur (Terstruktur & Saling Melengkapi)

> [!TIP]
> **Prinsip Kolaborasi**: 
> - **Rozi**: Memegang arsitektur monorepo, database & scoring engine, matching Cosine Similarity, pipeline AI Gemini, **Halaman Beranda (Landing Page)**, dan **Komponen AI Roadmap Timeline**.
> - **Diki**: Fokus pada tugas yang modular dan terisolasi: **Seed data karier**, **Visualisasi Radar Chart (Recharts)**, **Kartu & List Rekomendasi Karier**, **Modal Detail Karier**, dan **Komponen FAQ / Panduan RIASEC**.

```text
┌─────────────────────────────────────────────────────────────┐
│                            AKARA                            │
├──────────────────────────────┬──────────────────────────────┤
│   ROZI (Lead / Core & Flows) │   DIKI (Frontend & Guided)   │
├──────────────────────────────┼──────────────────────────────┤
│ • Setup Arsitektur & Monorepo│ • Seed Data Karier (JSON/TS) │
│ • Scoring Engine 16 Tipe     │ • Visualisasi Radar Chart    │
│ • Cosine Similarity Matching │ • Career Card & List UI      │
│ • Pipeline AI Gemini Flash   │ • Career Detail Modal/Drawer │
│ • Halaman Beranda (Landing)  │ • Komponen FAQ & Panduan     │
│ • Halaman Kuis (/test)       │   Tipe RIASEC (Accordion)    │
│ • AI Roadmap Timeline UI     │                              │
└──────────────────────────────┴──────────────────────────────┘
```

---

### 3.1 Detail Tanggung Jawab: ROZI (Core Engine, Math, AI, & Key Pages)

#### Domain: Algoritma, Database, AI Pipeline, Landing Page, & Roadmap Timeline

1. **Setup Pondasi & Endpoint Standard**:
   - Monorepo, Prisma schema, standard error handler, dan Swagger UI.
   - Setup provider, client axios, dan contoh fullstack reference code.

2. **Scoring Engine & Cosine Similarity**:
   - `scoring.service.ts`: Kalkulasi 4 dimensi MBTI dan 6 dimensi RIASEC mentah.
   - `matching.service.ts`: Algoritma perhitungan vektor **Cosine Similarity** antara profil user vs database karier.

3. **Gemini AI Service & Prompt Guardrails**:
   - `ai.service.ts`: Integrasi Gemini API dengan Zod Structured Outputs (Result Insight, Why This Career, & 4-Phase Roadmap).

4. **Halaman Beranda (Landing Page)**:
   - Slicing hero section modern, value proposition, statistik/keunggulan platform, dan Call to Action (CTA) "Mulai Tes Kariermu".

5. **Halaman Kuis Asesmen (`/test`)**:
   - Wizard kuis interaktif, Likert slider/radio, dan submission jawaban ke backend.

6. **Fitur & Komponen Roadmap Timeline (End-to-End)**:
   - Backend endpoint `POST /api/ai/career-roadmap`.
   - Frontend komponen `RoadmapTimeline` interaktif (4 fase perkembangan, checklist aksi 30/60/90 hari).

---

### 3.2 Detail Tanggung Jawab: DIKI (UI/UX Komponen Karier, Visualisasi, & Panduan)

#### Domain: Komponen Tampilan, Visualisasi Recharts, Slicing Desain, & Data Seeding

> *Tugas Diki terisolasi dengan jelas, visual, berfokus pada eksplorasi karier dan edukasi hasil tes tanpa beban kalkulasi matematika berat atau prompt engineering.*

1. **Task 1: Seed Data Karier (`careers.seed.ts`)**:
   - **Tujuan**: Memahami struktur data objek TypeScript / JSON.
   - **Yang Dikerjakan**: Mengisi daftar 20–30 karier target (nama karier, deskripsi, kisaran gaji Indonesia, skill wajib, dan skor acuan RIASEC 1–100) mengikuti skema Prisma yang sudah disiapkan Rozi.

2. **Task 2: Visualisasi RIASEC Radar Chart (Frontend)**:
   - **Tujuan**: Menguasai integrasi library visualisasi data interaktif.
   - **Yang Dikerjakan**: Menggunakan **Recharts** untuk membuat komponen `RiasecRadarChart`.
   - Datanya sudah siap pakai dari backend Rozi, Diki tinggal fokus styling poligon chart, aksen warna elegan, responsive container, dan custom tooltip saat di-hover.

3. **Task 3: Komponen List & Kartu Karier (`CareerCard` & `CareerList`)**:
   - **Tujuan**: Melatih komponen UI React, Tailwind CSS, dan shadcn/ui.
   - **Yang Dikerjakan**:
     - Membuat `CareerCard` yang menampilkan gelar karier, badge persentase kecocokan (*Match Score %*), tag industri, dan skill chips.
     - Input pencarian sederhana & filter kategori karier.

4. **Task 4: Modal / Drawer Detail Karier (`CareerDetailModal`)**:
   - **Tujuan**: Belajar dialog modal dan conditional rendering props data.
   - **Yang Dikerjakan**:
     - Membuat Drawer / Modal popup saat kartu karier diklik.
     - Menampilkan informasi lengkap karier: ringkasan peranan, estimasi rentang gaji, prospek kerja, dan daftar skill utama.

5. **Task 5: Komponen FAQ & Panduan Tipe RIASEC (Edukasi Hasil)**:
   - **Tujuan**: Slicing komponen informatif berbasis Accordion/Card.
   - **Yang Dikerjakan**:
     - Membuat komponen panduan 6 tipe kepribadian RIASEC (Realistic, Investigative, Artistic, Social, Enterprising, Conventional) agar user paham arti skor mereka.
     - Accordion FAQ seputar hasil tes karier.

---

### 3.3 Rencana Prioritas Eksekusi Sprint 1 (Target 2 Minggu)

Untuk menjaga momentum dan mencegah blocker antar developer, berikut adalah urutan pengerjaan harian Sprint 1:

```text
┌─────────────────────────────────────────────────────────────────────────┐
│                     ROADMAP SPRINT 1: MVP CORE LAUNCH                   │
├──────────────┬────────────────────────────┬─────────────────────────────┤
│   TIMELINE   │      ROZI (Lead/Core)      │  DIKI (Frontend/Guided UI)  │
├──────────────┼────────────────────────────┼─────────────────────────────┤
│ Hari 1 – 3   │ Setup Monorepo, DB Prisma, │ Menyusun data JSON/TS:      │
│ (Fondasi)    │ Swagger, Vitest, & Linter  │ careers.seed.ts (30 karier) │
├──────────────┼────────────────────────────┼─────────────────────────────┤
│ Hari 4 – 7   │ Scoring Engine, Cosine     │ RiasecRadarChart (Recharts) │
│ (Core & UI)  │ Similarity, & Mock Data    │ & Komponen CareerCard List  │
├──────────────┼────────────────────────────┼─────────────────────────────┤
│ Hari 8 – 11  │ Halaman Kuis (/test) &     │ Modal Detail Karier &       │
│ (Flow & AI)  │ Gemini AI Insight Pipeline │ Panduan RIASEC + FAQ        │
├──────────────┼────────────────────────────┼─────────────────────────────┤
│ Hari 12 – 14 │ Slicing Landing Page &     │ Integrasi TanStack Query &  │
│ (Final/QA)   │ Roadmap Timeline Component │ Verifikasi Test 100% Pass   │
└──────────────┴────────────────────────────┴─────────────────────────────┘
```

#### Rincian Milestone Harian:
- **Milestone 1 (Hari 1–3) — Setup & Seed Data**:
  - **Rozi**: Selesaikan Checklist Fase 0 (Express, Neon DB, Prisma schema `Question` & `Career`, Vitest, ESLint/Prettier). Push ke `develop`.
  - **Diki**: Clone/pull `develop`. Buat isi file `server/prisma/seed.ts` (mengisi data 25–30 profil profesi Indonesia dengan tag skill & range gaji).
- **Milestone 2 (Hari 4–7) — Core Engine & Komponen Visual**:
  - **Rozi**: Buat `scoring.service.ts` & `matching.service.ts` (Cosine Similarity) + unit test Vitest. Sediakan file `mock-careers.json` untuk Diki.
  - **Diki**: Buat komponen `RiasecRadarChart` (Recharts) dan `CareerCard` + `CareerList` mengacu pada file `mock-careers.json` dan prompt UI Duolingo.
- **Milestone 3 (Hari 8–11) — Alur Asesmen & Detail Karier**:
  - **Rozi**: Buat endpoint `POST /api/test/session/submit`, integrasi Gemini AI `ai.service.ts`, dan slicing Halaman Kuis `/test` (Likert 1–5).
  - **Diki**: Buat `CareerDetailModal` (dialog popup ringkasan peran & prospek) serta komponen panduan 6 tipe RIASEC (Accordion FAQ).
- **Milestone 4 (Hari 12–14) — Landing Page, Polish, & Quality Gate**:
  - **Rozi**: Slicing Halaman Beranda (Landing Page) dan komponen `RoadmapTimeline`.
  - **Diki**: Hubungkan komponen UI ke hook live `useCareers` dan `useTestResult`.
  - **Berdua**: Jalankan `npm run test:run` (wajib 100% lulus), review PR, dan deploy preview ke Vercel!

---

## 4. Alur Kolaborasi & Bantuan Mentor (Rozi -> Diki)

1. **Rozi Menyediakan Mock Data & Template Hook**:
   Sebelum backend selesai 100%, Rozi menyediakan file mock JSON dummy (misal `mock-careers.json`) dan template hook React agar Diki bisa langsung mendesain UI tanpa terhambat backend.
2. **Review Santai & Edukatif**:
   Code review di pull request difokuskan untuk sharing best-practice (misal cara split component yang rapi, penamaan class Tailwind), bukan mencari kesalahan.
3. **No Pressure Milestone**:
   Diki tidak ditargetkan logic backend yang kompleks, melainkan konsistensi tampilan visual yang rapi dan nyaman dipakai user.

---

## 5. Protokol Kerja Sama & Sinkronisasi

1. **Kontrak API Terlebih Dahulu (Contract-First)**:
   Sebelum menulis kode UI, diskusikan schema data API atau gunakan mock data berbasis Swagger agar tidak saling menunggu.
2. **Review Silang (Cross-Review)**:
   - PR dari Rozi direview oleh Diki.
   - PR dari Diki direview oleh Rozi.
3. **Standup Singkat / Sync Mingguan**:
   Lakukan sync 15 menit setiap 2-3 hari untuk membahas blocker atau integrasi AI prompt.
4. **Quality Gate Testing Wajib (Zero Failing Tests)**:
   Sebelum membuka Pull Request (PR), developer **wajib menjalankan `npm run test:run` dan memastikan 100% test lulus hijau**. Dilarang melakukan merge jika ada test yang gagal atau merah.
