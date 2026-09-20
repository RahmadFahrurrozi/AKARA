<div align="center">

# 🧭 AKARA — AI-Powered Career Platform

**Platform Penemuan & Perencanaan Karier Masa Depan Berbasis Psikometrik RIASEC & AI**

[![Tech Stack: React](https://img.shields.io/badge/Frontend-React%20%2B%20Vite-61dafb?logo=react)](https://react.dev/)
[![Backend: Express](https://img.shields.io/badge/Backend-Express.js%20%2B%20TypeScript-black?logo=express)](https://expressjs.com/)
[![Database: Neon Postgres](https://img.shields.io/badge/Database-Neon%20PostgreSQL-00e599?logo=postgresql)](https://neon.tech/)
[![AI: Google Gemini](https://img.shields.io/badge/AI-Google%20Gemini%202.5%20Flash-4285f4?logo=google)](https://aistudio.google.com/)
[![Testing: Vitest](https://img.shields.io/badge/Testing-Vitest-729b1b?logo=vitest)](https://vitest.dev/)

</div>

---

## 📌 Tentang AKARA

**AKARA** adalah platform eksplorasi karier modern yang dirancang khusus untuk mahasiswa dan *fresh graduates* di Indonesia. Menggabungkan pengujian minat kerja ilmiah **Holland RIASEC & 16 Tipe Kepribadian** dengan algoritma deterministik **Cosine Similarity** dan orkestrasi narasi aksi **Google Gemini AI**.

AKARA menyelesaikan masalah *"overthinking karier"* dengan menyajikan rekomendasi profesi yang terukur, visualisasi grafik radar yang interaktif, serta rencana aksi konkret 4 fase (30/60/90 hari).

---

## 🚀 Tech Stack

### Client (`client/`)
- **Framework:** React 19/18 + Vite SPA
- **Language:** TypeScript
- **Styling:** Tailwind CSS + [shadcn/ui](https://ui.shadcn.com/) (Duolingo-inspired Playful Aesthetic)
- **Routing:** React Router v6/v7
- **Data Fetching:** TanStack Query v5 + Axios Client
- **Data Visualization:** Recharts (RIASEC Radar Chart)
- **Testing:** Vitest + React Testing Library + jsdom

### Server (`server/`)
- **Runtime:** Node.js + Express.js
- **Language:** TypeScript
- **Database & ORM:** PostgreSQL ([Neon Serverless](https://neon.tech/)) + Prisma ORM
- **Cache:** Upstash Serverless Redis (Fase 2)
- **AI Integration:** Google Gemini 2.5 Flash API (Zod Structured Outputs)
- **Testing:** Vitest + Supertest
- **API Docs:** Swagger UI (OpenAPI 3.0) di `/api-docs`

---

## 📚 Indeks Dokumentasi Proyek

Seluruh acuan teknis, arsitektur, dan alur kolaborasi telah terdokumentasi secara lengkap:

| Dokumen | Deskripsi |
| :--- | :--- |
| **[PRD & Visi Produk](./AKARA_PRD_v2_AI_Career_Platform.md)** | Spesifikasi kebutuhan produk, user stories, guardrails, & fitur lengkap |
| **[Pembagian Tugas Tim](./TEAM_TASK_DIVISION.md)** | Jobdesk Rozi vs Diki, alur kerja 6 langkah, & roadmap Sprint 1 |
| **[Database Schema & ERD](./DATABASE_SCHEMA.md)** | Diagram visual ERD & skema Prisma siap pakai |
| **[Kontrak API & Mock Data](./API_CONTRACTS.md)** | Spesifikasi request-response JSON baku & data dummy untuk frontend |
| **[Setup Environment](./ENV_SETUP.md)** | Panduan template `.env` & akun cloud gratis (Neon DB & Gemini) |
| **[Design System (Duolingo Style)](./DESIGN.md)** | Style guide warna `#58cc02`, font, token border, dan komponen |
| **[Prompt Google Stitch](./GOOGLE-STICH.md)** | Koleksi prompt AI untuk visualisasi UI di [Google Stitch Canvas](https://stitch.withgoogle.com/projects/465219332161847245) |
| **[Konvensi Client](./FRONTEND_CONVENTION.md)** | Standar kode React, komponen, custom hooks, dan testing |
| **[Konvensi Server](./BACKEND_CONVENTION.md)** | Arsitektur berlapis, error handling AppError, dan standardisasi API |
| **[Workflow Git](./GIT_WORKFLOW.md)** | Strategi branch, conventional commit, dan panduan anti-conflict |

---

## 👥 Tim Pengembang

- **Rozi** ([@rozi](https://github.com/)) — *Fullstack Lead (Core Engine, Math Algorithms & AI Orchestration)*
- **Diki** ([@diki](https://github.com/)) — *Fullstack Developer (UI/UX, Visualizations & Feature Slicing)*

---

<div align="center">
  <sub>Dibangun dengan dedikasi untuk membantu generasi muda menemukan arah karier terbaik.</sub>
</div>
