# Kontrak API & Mock Data JSON
**Project:** AKARA — AI Career Platform  
**Base URL:** `http://localhost:5000/api` (Development) / `/api` (Production)  
**Standard Response Format:** JSON (`application/json`)

Dokumen ini menjadi acuan tunggal kesepakatan format data antara **Rozi (Backend)** dan **Diki (Frontend)** agar proses koding berjalan independen tanpa saling menunggu.

---

## 1. Format Baku Respon API (Best Practice: JSend Extended)

Di arsitektur RESTful modern, selain mengirimkan HTTP Status Code pada protokol header (`res.status(200)`), **sangat disarankan menyertakan `statusCode: number` eksplisit di dalam JSON body**. Ini memudahkan frontend membaca status secara langsung dari data respon dan mempermudah debugging log.

### Respon Berhasil (HTTP 200 / 201)
```json
{
  "success": true,
  "statusCode": 200,
  "message": "Operasi berhasil dijalankan",
  "data": { ... }
}
```

### Respon Gagal / Validasi Error (HTTP 400 / 404 / 500)
```json
{
  "success": false,
  "statusCode": 404,
  "message": "Pesan error ramah pengguna",
  "errors": null
}
```

---

## 2. Rincian Endpoint MVP (Fase 1)

### 2.1 `GET /api/test/questions`
> **Fungsi:** Mengambil 20 daftar pertanyaan kuis asesmen yang aktif untuk ditampilkan di halaman `/test`.

- **Method:** `GET`
- **Response (200 OK):**
```json
{
  "success": true,
  "statusCode": 200,
  "message": "Daftar pertanyaan berhasil diambil",
  "data": [
    {
      "id": "q1",
      "text": "Saya lebih menikmati memecahkan teka-teki logika yang rumit daripada memimpin diskusi kelompok.",
      "dimension": "I",
      "category": "RIASEC",
      "orderIndex": 1
    },
    {
      "id": "q2",
      "text": "Saya merasa berenergi saat berada di tengah keramaian dan berbicara dengan banyak orang baru.",
      "dimension": "E",
      "category": "PERSONALITY",
      "orderIndex": 2
    }
  ]
}
```

---

### 2.2 `POST /api/test/session`
> **Fungsi:** Menginisialisasi sesi tes baru saat user menekan tombol "Mulai Tes".

- **Method:** `POST`
- **Request Body:** `{}` (Opsional: `{ "userId": "..." }`)
- **Response (201 Created):**
```json
{
  "success": true,
  "statusCode": 201,
  "message": "Sesi tes baru berhasil dibuat",
  "data": {
    "sessionId": "ses_cm1234567890",
    "status": "IN_PROGRESS",
    "currentStep": 1,
    "startedAt": "2026-09-20T10:00:00.000Z"
  }
}
```

---

### 2.3 `POST /api/test/session/:id/submit`
> **Fungsi:** Mengirim seluruh jawaban user, memicu kalkulasi skor deterministik (MBTI & RIASEC Cosine Similarity), memanggil Gemini AI untuk insight, dan mengembalikan hasil akhir.

- **Method:** `POST`
- **URL Params:** `id` (Session ID)
- **Request Body (Zod Validated):**
```json
{
  "answers": [
    { "questionId": "q1", "score": 5 },
    { "questionId": "q2", "score": 2 },
    { "questionId": "q3", "score": 4 }
  ]
}
```
- **Response (200 OK):** *(Struktur sama persis dengan `GET /api/test/session/:id/result` di bawah).*

---

### 2.4 `GET /api/test/session/:id/result`
> **Fungsi:** Mengambil data hasil asesmen lengkap untuk ditampilkan pada halaman `/result/:sessionId`.

- **Method:** `GET`
- **Response (200 OK):**
```json
{
  "success": true,
  "statusCode": 200,
  "message": "Hasil asesmen berhasil dimuat",
  "data": {
    "sessionId": "ses_cm1234567890",
    "personality": {
      "code": "INTJ",
      "title": "Sang Arsitek Strategis",
      "summary": "Kamu memiliki pola pikir analitis, visioner, dan independen. Kamu lebih nyaman merancang sistem jangka panjang dan memecahkan tantangan logis yang terstruktur.",
      "traits": {
        "introvert": 78,
        "intuitive": 65,
        "thinking": 82,
        "judging": 70
      }
    },
    "riasec": {
      "scores": {
        "realistic": 42,
        "investigative": 94,
        "artistic": 60,
        "social": 48,
        "enterprising": 82,
        "conventional": 75
      },
      "topDimensions": ["Investigative", "Enterprising"]
    },
    "aiInsight": {
      "summary": "Kombinasi nilai Investigatif (94) dan Enterprising (82) menjadikanmu seorang 'Analytical Problem Solver with Leadership Edge'. Kamu unggul dalam membedah data teknis sekaligus mampu mengartikulasikan solusinya secara bisnis.",
      "strengths": [
        "Kemampuan deduksi logis dan analisis data tingkat tinggi",
        "Kemandirian tinggi dalam mengeksplorasi solusi baru",
        "Berorientasi pada efisiensi dan perbaikan sistem"
      ],
      "considerations": [
        "Beri ruang toleransi bagi proses kerja tim yang membutuhkan ritme berbeda",
        "Hindari overthinking saat data belum lengkap 100%"
      ],
      "nextSteps": [
        "Fokus membangun portofolio berbasis studi kasus nyata",
        "Perdalam skill visualisasi data dan komunikasi analitis"
      ]
    },
    "careerMatches": [
      {
        "id": "car_1",
        "title": "Data Analyst / AI Specialist",
        "category": "Teknologi & Analitika",
        "matchPercentage": 96.5,
        "rank": 1,
        "salaryMin": 8000000,
        "salaryMax": 16000000,
        "keySkills": ["Python", "SQL", "Tableau", "Critical Thinking"],
        "whyThisCareer": "Profil Investigatifmu yang dominan (94) sangat selaras dengan kebutuhan riset data, penemuan pola anomali, dan pembuatan visual dashboard analitik."
      },
      {
        "id": "car_2",
        "title": "Product Analyst / Tech Strategist",
        "category": "Manajemen Produk",
        "matchPercentage": 91.2,
        "rank": 2,
        "salaryMin": 9000000,
        "salaryMax": 18000000,
        "keySkills": ["A/B Testing", "SQL", "Product Metrics", "User Research"],
        "whyThisCareer": "Memadukan ketajaman investigatif dengan dimensi Enterprising untuk menyusun hipotesis dan metrik keberhasilan produk digital."
      }
    ]
  }
}
```

---

### 2.5 `GET /api/careers`
> **Fungsi:** Mengambil katalog seluruh daftar profesi karier (mendukung pencarian dan filter kategori).

- **Query Params (Opsional):**
  - `search` (contoh: `?search=data`)
  - `category` (contoh: `?category=Teknologi`)
- **Response (200 OK):**
```json
{
  "success": true,
  "statusCode": 200,
  "message": "Daftar karier berhasil dimuat",
  "data": [
    {
      "id": "car_1",
      "title": "Data Analyst",
      "category": "Teknologi & Analitika",
      "description": "Menganalisis kumpulan data besar untuk menemukan tren, membuat dashboard visual, dan mendukung keputusan bisnis strategis.",
      "salaryMin": 8000000,
      "salaryMax": 16000000,
      "keySkills": ["Python", "SQL", "Tableau", "Power BI"],
      "outlook": "Sangat Tinggi"
    }
  ]
}
```

---

## 3. Mock Data JSON Siap Pakai (Frontend Development)

Developer dapat langsung membuat file lokal `client/src/mocks/mock-careers.json` dan menyalin data di bawah ini agar bisa langsung mendesain tampilan UI tanpa menunggu koneksi database live:

```json
[
  {
    "id": "car_1",
    "title": "Data Analyst",
    "category": "Teknologi & Analitika",
    "description": "Mengolah data mentah menjadi wawasan bisnis yang actionable melalui visualisasi dashboard dan query SQL.",
    "salaryMin": 7500000,
    "salaryMax": 15000000,
    "keySkills": ["SQL", "Python", "Tableau", "Excel Lanjut"],
    "outlook": "Sangat Tinggi",
    "matchPercentage": 96
  },
  {
    "id": "car_2",
    "title": "UI/UX Designer",
    "category": "Desain & Kreatif",
    "description": "Merancang pengalaman pengguna dan antarmuka aplikasi digital yang intuitif, estetik, dan mudah digunakan.",
    "salaryMin": 7000000,
    "salaryMax": 14000000,
    "keySkills": ["Figma", "User Research", "Wireframing", "Design System"],
    "outlook": "Tinggi",
    "matchPercentage": 92
  },
  {
    "id": "car_3",
    "title": "Software Engineer (Fullstack)",
    "category": "Teknologi Informasi",
    "description": "Membangun dan mengembangkan sistem aplikasi web atau mobile secara menyeluruh dari database hingga antarmuka user.",
    "salaryMin": 9000000,
    "salaryMax": 20000000,
    "keySkills": ["TypeScript", "React", "Node.js", "PostgreSQL"],
    "outlook": "Sangat Tinggi",
    "matchPercentage": 89
  },
  {
    "id": "car_4",
    "title": "Product Manager",
    "category": "Manajemen Bisnis",
    "description": "Menjembatani kebutuhan pengguna, target bisnis, dan teknologi untuk mengembangkan produk digital yang bernilai tinggi.",
    "salaryMin": 12000000,
    "salaryMax": 25000000,
    "keySkills": ["Product Strategy", "Agile/Scrum", "Data Literacy", "Roadmapping"],
    "outlook": "Tinggi",
    "matchPercentage": 85
  },
  {
    "id": "car_5",
    "title": "Digital Marketing Specialist",
    "category": "Pemasaran & Komunikasi",
    "description": "Mengembangkan strategi kampanye pemasaran online melalui media sosial, SEO, dan paid ads untuk meningkatkan jangkauan brand.",
    "salaryMin": 6500000,
    "salaryMax": 13000000,
    "keySkills": ["Google Ads", "Meta Ads", "SEO", "Copywriting"],
    "outlook": "Tinggi",
    "matchPercentage": 81
  }
]
```
