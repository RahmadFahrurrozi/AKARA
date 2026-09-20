# Panduan & Prompt Google Stitch — UI Design AKARA

**Official Google Stitch Project Canvas:** [https://stitch.withgoogle.com/projects/465219332161847245](https://stitch.withgoogle.com/projects/465219332161847245)

---

## 1. Master Style Guidelines untuk Prompt

- **Canvas / Background**: Pure Paper White (`#ffffff`), bukan dark mode, bukan gradien redup.
- **Warna Utama**: 
  - *Eager Green* (`#58cc02`) untuk tombol aksi utama, progress bar, dan badge sukses.
  - *Spark Blue* (`#1cb0f6`) untuk tombol sekunder dan link interaktif.
  - *Storybook Green* (`#d7ffb8`) untuk tint latar belakang lembut dan tag.
  - *Charcoal* (`#4b4b4b`) untuk teks judul dan *Pencil Gray* (`#777777`) untuk teks paragraf.
- **Bentuk Komponen**: Sudut membulat tebal (`rounded-xl` / `12px` - `16px`), border tegas `2px solid #afafaf` atau warna aksen, tombol 3D berbobot seperti stiker timbul (*tactile pressed button*).
- **Tipografi**: Display font membulat gemuk (*Nunito Black* / *Feather-like*), dan teks isi yang rapi dan mudah dibaca (*Inter* / *Nunito Sans*).
- **Tone**: Bersahabat, edukatif, *gamified*, menyemangati, dan tidak kaku/korporat.

---

## 2. Koleksi Prompt Layar Utama

---

### PROMPT 1: Landing Page / Beranda (Desktop 1440px)

```text
Design a playful, gamified, and modern landing page for "AKARA — AI-Powered Career Platform for Students & Fresh Graduates", heavily inspired by Duolingo's clean storybook aesthetic.

Visual Style & Rules:
- Background: Pure Paper White (#ffffff) throughout the page. Clean and clutter-free, no dark gradients or muddy shadows.
- Primary Accent: Duolingo Eager Green (#58cc02) for high-impact CTAs and progress indicators.
- Secondary Accent: Spark Blue (#1cb0f6) for interactive links and secondary outline buttons.
- Typography: Rounded chunky display headings in charcoal (#4b4b4b) similar to Nunito Black or Feather Bold, paired with clean sans-serif body copy in pencil gray (#777777).
- Component Shape: Chunky tactile buttons and cards with 12px border radius, 2px solid border in #afafaf, with a subtle 3D pressed-sticker feel.

Page Layout (Single column editorial flow):
1. Minimal Navbar: Left side has a friendly rounded "AKARA" logo with a playful mascot emblem (a small smart owl or compass character). Right side has a language pill button with 2px border and a Spark Blue "Masuk" login button.
2. Hero Section:
   - Left column: Catchy chunky headline "Temukan Karier Masa Depanmu, Bebas Overthinking!" in 48px charcoal text. Subtitle "Tes kepribadian & minat karier berbasis RIASEC dengan bimbingan roadmap aksi AI yang konkret."
   - Primary CTA: Large chunky green pill button (#58cc02 fill, white bold text, 3D bottom press effect) with text "MULAI TES GRATIS (5 MENIT)".
   - Below CTA: Outline secondary button in Spark Blue border: "JELAJAHI KATALOG KARIER".
   - Right column: Charming flat 2D vector illustration of an enthusiastic student with a backpack holding a map with a glowing green compass/star.
3. Social Proof / Benefit Bar:
   - 3 rounded sticker cards with 2px borders on white surface:
     a. "100% Deterministik" — Skor ilmiah 16 Tipe & RIASEC, bukan tebakan.
     b. "Rekomendasi Nyata" — Dicocokkan dengan 30+ profesi relevan di Indonesia.
     c. "AI Action Roadmap" — Rencana langkah konkret 30/60/90 hari.
4. "Cara Kerja" (How it Works) 3-Step Section:
   - Step 1: "Isi Kuis Interaktif" (gambar kartu kuis ramah).
   - Step 2: "Lihat Grafis Radar RIASEC" (ilustrasi radar chart polygon).
   - Step 3: "Dapatkan Rencana Aksi Karier" (ilustrasi checklist langkah karier).
5. Footer:
   - Full-bleed rich green (#58cc02) band with white text, clear navigation links, and cute copyright tagline.
```

---

### PROMPT 2: Halaman Kuis Asesmen Interaktif (`/test`)

```text
Design an interactive, gamified assessment test wizard screen for "AKARA Career Quiz", inspired by Duolingo's lesson quiz interface.

Visual Style & Atmosphere:
- Canvas: Clean Paper White (#ffffff) focused on one question at a time to eliminate cognitive overload.
- Color Palette: Eager Green (#58cc02), Spark Blue (#1cb0f6), Storybook Green (#d7ffb8), Faded Gray (#afafaf), Charcoal (#4b4b4b).
- Component Anatomy: 12px chunky rounded corners, 2px solid borders, tactile physical button feedback.

Layout Components:
1. Top Header Bar:
   - Left: Close/Back icon (X).
   - Center: Chunky animated progress bar in bright Eager Green (#58cc02) with 12px rounded pill ends, showing "45% Selesai".
   - Right: Playful question counter badge: "Soal 9 dari 20" with a cute star icon.
2. Question Card (Centered in viewport, max-width 720px):
   - Dimension Tag: Soft Storybook Green pill badge (#d7ffb8 background, dark green bold text) with label "MINAT INVESTIGATIF (I)".
   - Question Statement: Bold, friendly 24px charcoal text: "Saya lebih menikmati memecahkan teka-teki logika yang rumit daripada memimpin diskusi rapat kelompok."
   - 5-Point Likert Scale Selector (Horizontal stack on desktop, vertical on mobile):
     - 5 distinct sticker-like cards with 2px solid borders (#afafaf).
     - Scale 1: "Sangat Tidak Setuju" (soft gray border).
     - Scale 2: "Tidak Setuju".
     - Scale 3: "Netral / Ragu-ragu".
     - Scale 4: "Setuju".
     - Scale 5: "Sangat Setuju" (Active state: filled with #d7ffb8 soft green, 2px solid #58cc02 border, checkmark icon).
3. Bottom Floating Action Footer:
   - Full-width white bar with 1px top border.
   - Right-aligned: Large chunky Eager Green CTA button (#58cc02, bold white uppercase text) labeled "LANJUTKAN →", disabled state in light gray when no option is selected.
```

---

### PROMPT 3: Halaman Dashboard Hasil Tes (`/result/[id]`)

```text
Design a triumphant, celebratory result dashboard screen for "AKARA Career Assessment Result", with Duolingo-style gamification and delightful visual polish.

Visual Style:
- Background: Paper White (#ffffff) with subtle colorful confetti accents at the top.
- Cards: Tactile white cards with 2px solid border (#afafaf) and 16px rounded corners.
- Colors: Eager Green (#58cc02), Spark Blue (#1cb0f6), Storybook Green (#d7ffb8), Charcoal text (#4b4b4b).

Screen Sections:
1. Celebration Hero Banner:
   - Cute mascot illustration celebrating with confetti.
   - Headline in 36px chunky rounded font: "Hore! Profil Kariermu Berhasil Dibuat!"
   - Subhead: "Berdasarkan 20 jawabanmu, berikut adalah analisis minat dan profesi paling cocok."
2. Top Result Grid (2 Columns):
   - Left Card: "Tipe Kepribadian Dominan":
     - Big bold badge: "INTJ — Sang Arsitek Strategis".
     - 4-bar personality trait distribution (Introvert 78%, Intuitive 65%, Thinking 82%, Judging 70%) with chunky rounded progress bars.
     - Short encouraging description of key strengths.
   - Right Card: "Visualisasi Minat RIASEC":
     - Title: "Radar Minat Kerja Holland".
     - An interactive, beautiful 6-axis Radar Chart in center.
     - Axes: Realistic, Investigative, Artistic, Social, Enterprising, Conventional.
     - Chart filled with semi-transparent Eager Green (#58cc02 at 30% opacity) and crisp 2px green stroke.
     - Top 2 dominant dimensions highlighted with Spark Blue badges: "Investigative (92)" & "Enterprising (84)".
3. AI Result Insight Box:
   - Container: Light background with 2px dashed green border and mascot avatar bubble.
   - Title: "Insight Analisis AI Gemini".
   - Structured points: "Kelebihan Utama", "Area Perhatian", and "Langkah Awal yang Disarankan".
4. Bottom Action Bar:
   - Chunky green CTA: "LIHAT TOP 5 REKOMENDASI KARIER ↓".
   - Share button with Spark Blue outline: "Bagikan Hasil Tes".
```

---

### PROMPT 4: Katalog Rekomendasi Karier & Card List (`/careers`)

```text
Design a clean, gamified career recommendation list interface for "AKARA Career Matcher", featuring Duolingo-style sticker cards.

Visual Style:
- Canvas: Pure Paper White (#ffffff).
- Cards: Floating sticker cards with 2px solid borders (#afafaf), 12px rounded corners, and subtle tactile hover state.

Components to Include:
1. Header & Quick Filter:
   - Title: "Rekomendasi Karier Paling Cocok Untukmu" in 28px charcoal bold.
   - Search bar with rounded pill shape and 2px border.
   - Filter chips: "Semua", "Investigatif", "Teknologi", "Bisnis", "Kreatif" (active chip has #58cc02 green fill with white text).
2. Career Recommendation Card (Repeat 3-4 cards in vertical stack):
   - Card Header:
     - Left: Career title "Data Analyst / AI Specialist" in bold 20px charcoal text, with company/industry category "Teknologi & Analitika".
     - Right: Prominent Match Badge in Eager Green (#58cc02 pill with white text): "96% MATCH".
   - Card Body:
     - Short 2-sentence description of what this role does.
     - Estimated Salary pill: "Gaji: Rp 8.000.000 - Rp 16.000.000 / bulan".
     - Key Skill Tags (horizontal pill list with 2px borders): "Python", "SQL", "Data Visualization", "Critical Thinking".
   - Card Action:
     - Spark Blue (#1cb0f6) outlined button with 2px border: "Kenapa Karier Ini Cocok? & Roadmap →".
```

---

### PROMPT 5: Modal Detail Karier & AI Career Roadmap (`CareerDetailModal`)

```text
Design an interactive modal popup and 4-phase action plan roadmap drawer for "AKARA Career Action Plan", styled in Duolingo's milestone progression aesthetic.

Visual Style:
- Modal Dialog: Centered white modal (width 800px) with 16px rounded corners, 2px solid border in charcoal/gray, and clean backdrop blur.
- Palette: Eager Green (#58cc02), Spark Blue (#1cb0f6), Storybook Green (#d7ffb8), Charcoal (#4b4b4b).

Modal Layout:
1. Modal Header:
   - Title: "Detail Karier: Product Manager" with a 92% Match Badge.
   - Close button (X) top right.
2. Tab Switcher (Pill style):
   - Tab 1: "Ringkasan & Prospek" (Active: #58cc02 fill, white text).
   - Tab 2: "AI 4-Phase Roadmap" (Outline button).
3. Roadmap Timeline View (Gamified path similar to Duolingo skill tree):
   - Vertical dotted milestone line connecting 4 chunky milestone cards:
     - Phase 1 (Bulan 1): "Fondasi & Pemahaman Core" — Checklist: Pelajari Agile, kuasai user research basic.
     - Phase 2 (Bulan 2): "Skill Teknis & Tools" — Checklist: Wireframing di Figma, analisis metric data.
     - Phase 3 (Bulan 3): "Portofolio Mini Project" — Checklist: Bikin 1 studi kasus PRD produk nyata.
     - Phase 4 (Bulan 4): "Persiapan Kerja & Interview" — Checklist: Mock interview & update profil LinkedIn.
   - Interactive Checklist: Rounded checkboxes that turn green with a checkmark when clicked.
4. Modal Footer:
   - Left: "Simpan Karier Ini ke Favorit" (Bookmark icon).
   - Right: Chunky green CTA "TUTUP & SIMPAN ACTION PLAN".
```

---

### PROMPT 6: Panduan Tipe RIASEC & FAQ Accordion Component

```text
Design a friendly educational card grid and accordion component explaining "6 Holland RIASEC Personality Codes" for AKARA, with playful storybook illustrations.

Visual Style:
- Background: Paper White (#ffffff).
- 6 RIASEC Dimension Cards (3x2 Grid):
  1. Realistic (R) — "Si Praktis & Lapangan" (Icon: Wrench/Tool, color accent: Orange).
  2. Investigative (I) — "Si Analitis & Peneliti" (Icon: Microscope, color accent: Spark Blue #1cb0f6).
  3. Artistic (A) — "Si Kreatif & Ekspresif" (Icon: Palette, color accent: Purple).
  4. Social (S) — "Si Penolong & Edukator" (Icon: Heart/Hands, color accent: Eager Green #58cc02).
  5. Enterprising (E) — "Si Pemimpin & Negosiator" (Icon: Briefcase/Rocket, color accent: Red/Coral).
  6. Conventional (C) — "Si Teratur & Data Driven" (Icon: Checklist/Spreadsheet, color accent: Teal).
- Card Structure:
  - Each card has 12px rounded corners, 2px solid border, dimension letter badge, short description, and "Contoh Karier Populer".
- Bottom Section:
  - Accordion FAQ: 4 expandable clean white boxes with 2px border (#afafaf), chevron arrow on right, containing common questions like "Apakah hasil tes bisa berubah?" and "Bagaimana cara membaca match score?".
```