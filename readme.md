Berikut **README.md** profesional untuk proyek kamu **CERVANA**, disusun berdasarkan isi proposal dan struktur sistem docker yang kamu buat:

---

# 🧠 CERVANA — AI Agent Learning untuk SMK Akuntansi

*Inovasi Pembelajaran Digital Berbasis Retrieval-Augmented Generation (RAG) dan Gamifikasi*

---

## 📘 Deskripsi Proyek

**CERVANA** adalah platform pembelajaran berbasis web yang dirancang untuk membantu **siswa SMK Akuntansi** mempersiapkan **sertifikasi kompetensi** secara efektif dan interaktif.
Platform ini menggabungkan:

* **AI Agent Learning** untuk memahami dan menjawab pertanyaan siswa secara kontekstual.
* **Retrieval-Augmented Generation (RAG)** untuk menghasilkan materi pembelajaran akurat dari sumber PDF, video, dan modul digital.
* **Gamifikasi dan microlearning** untuk meningkatkan motivasi belajar dan retensi pengetahuan.

Inovasi ini dikembangkan untuk **Lomba Inovasi Digital Mahasiswa (LIDM) 2025** oleh tim **The2D** dari Universitas Airlangga.

---

## 👥 Tim Pengembang

| Nama                    | NIM       | Peran                    |
| ----------------------- | --------- | ------------------------ |
| **Anindya Wita Wisesa** | 187231045 | Ketua & Perancang Sistem |
| **Misbahul Muttaqin**   | 187241037 | Backend & AI Engineer    |
| **Dina Fadiah**         | 171231069 | Peneliti & Evaluator     |
| **Diana Resti**         | 175221066 | Konten & Gamifikasi      |

Dosen Pembimbing:
**Dr. Indra Kharisma Raharjana, S.Kom., M.T.**

---

## 🧩 Arsitektur Sistem

```
nginx
 ├── web (Nuxt 3)
 ├── admin (Next.js)
 ├── api (NestJS)
 ├── ai-api (FastAPI + RAG)
 ├── postgres
 └── redis
```

Semuanya berjalan dalam container menggunakan **Docker Compose** dan berkomunikasi melalui network internal `cervana_network`.

---

## ⚙️ Fitur Utama

* 📚 **Pembelajaran berbasis RAG** — AI dapat mengambil dan menyajikan materi akuntansi dari dokumen PDF.
* 🎮 **Gamifikasi interaktif** — poin, streak, leaderboard, dan badge untuk memotivasi siswa.
* 💬 **AI Chatbot kontekstual** — membantu siswa memahami konsep dan menjawab pertanyaan.
* 📊 **Evaluasi otomatis** — kuis dan asesmen real-time berbasis hasil belajar.
* 🧑‍🏫 **Portal admin & guru** — kelola konten, progres, dan statistik pengguna.

---

## 🏗️ Struktur Direktori

```
lidm/
├── api/           # Backend utama (NestJS)
├── ai-api/        # Backend AI (FastAPI + RAG)
├── admin/         # Admin dashboard (Next.js)
├── web/           # Frontend siswa (Nuxt 3)
├── nginx/         # Reverse proxy
├── docker-compose.yml
└── db_data/       # Data Postgres
```

---

## 🚀 Cara Menjalankan Proyek

### 1️⃣ Prasyarat

Pastikan kamu sudah menginstal:

* Docker & Docker Compose
* Node.js + pnpm (opsional untuk development)
* Python 3.10+ (opsional untuk AI lokal)

---

### 2️⃣ Clone Repositori

```bash
git clone https://github.com/username/lidm-cervana.git
cd lidm
```

---

### 3️⃣ Konfigurasi Environment

Buat file `.env` di setiap service (`api`, `ai-api`, `web`, `admin`) seperti contoh:

#### 📄 `api/.env`

```env
DATABASE_URL=postgresql://postgres:postgres@postgres:5433/cervana
REDIS_HOST=redis
REDIS_PORT=6380
PORT=3002
NODE_ENV=development
JWT_ACCESS_SECRET=your-secret
JWT_REFRESH_SECRET=your-refresh-secret
SUPABASE_URL=your-supabase-url
SUPABASE_ANON_KEY=your-supabase-key
```

---

### 4️⃣ Build dan Jalankan Container

```bash
docker compose up -d --build
```

Jika kamu ingin memastikan tidak ada cache:

```bash
docker compose build --no-cache
docker compose up -d
```

---

### 5️⃣ Akses Aplikasi

| Service    | URL                                            | Deskripsi           |
| ---------- | ---------------------------------------------- | ------------------- |
| Web (User) | [http://localhost:3000](http://localhost:3000) | Portal siswa SMK    |
| Admin      | [http://localhost:3001](http://localhost:3001) | Dashboard admin     |
| API        | [http://localhost:3002](http://localhost:3002) | Backend utama       |
| AI API     | [http://localhost:3003](http://localhost:3003) | Model RAG & chatbot |
| Nginx      | [http://localhost](http://localhost)           | Proxy & routing     |

---

## 🔁 Hot Reload / Development Mode

* Semua service (`web`, `admin`, `api`, `ai-api`) sudah menggunakan **volume bind mount** ke folder lokal.
  Artinya:

  > setiap perubahan kode di folder lokal akan langsung tercermin di container (realtime update tanpa rebuild).

---

## 🧠 Teknologi Utama

| Komponen         | Teknologi                                       |
| ---------------- | ----------------------------------------------- |
| Backend          | NestJS (API), FastAPI (AI)                      |
| Frontend         | Nuxt 3 (User Web), Next.js (Admin)              |
| Database         | PostgreSQL                                      |
| Caching / PubSub | Redis                                           |
| AI & NLP         | Retrieval-Augmented Generation (RAG), Embedding |
| Proxy            | Nginx                                           |
| Deployment       | Docker Compose                                  |

---

## 🧩 Metodologi Pengembangan

Metode pengembangan yang digunakan adalah **Rapid Application Development (RAD)**, dengan tahapan:

1. Analisis kebutuhan pengguna.
2. Desain prototipe dan arsitektur sistem.
3. Pengembangan cepat (iteratif).
4. Uji coba pada siswa SMK Akuntansi.
5. Evaluasi efektivitas pembelajaran.

---

## 🧾 Evaluasi & Dampak

* **Efektivitas pembelajaran**: peningkatan skor pre-test vs post-test siswa.
* **Kinerja sistem AI**: akurasi retrieval konten dan relevansi jawaban chatbot.
* **Kepuasan pengguna**: survei terhadap interaksi dan motivasi belajar siswa.

---

## 📄 Lisensi

Proyek ini dibuat untuk keperluan **Lomba Inovasi Digital Mahasiswa (LIDM) 2025** dan tidak untuk penggunaan komersial tanpa izin tim pengembang.

---

Apakah kamu ingin saya tambahkan bagian **cara kontribusi & struktur branch Git (development/production)** juga biar README-nya cocok buat publikasi GitHub?
