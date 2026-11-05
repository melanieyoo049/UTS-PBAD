# UTS-PBAD - Sistem Peminjaman Perpustakaan

Repositori gabungan (Monorepo) untuk tugas UTS Pengembangan Berbasis Komponen / Aplikasi Terdistribusi (PBAD) yang mencakup **Frontend** dan **Backend**.

---

## 📁 Struktur Repositori

```text
UTS-PBAD/
├── backend/                  # REST API & Database SQLite
│   ├── src/
│   │   ├── config/           # Konfigurasi DB (SQLite) & Seeder
│   │   ├── controllers/      # Logika controller (Auth, Books, Borrowings)
│   │   ├── middlewares_helpers/ # Auth middleware JWT & SQLite helpers
│   │   ├── models/           # Data models
│   │   ├── routes/           # Routing API
│   │   └── sql_scripts/      # Skema database awal (init.sql)
│   ├── server.js             # Entry point server Express (Port 3000)
│   ├── package.json
│   └── readme.md
│
├── frontend/                 # Client SPA (Single Page Application)
│   ├── public/
│   ├── src/
│   │   ├── components/       # Komponen reusable (Navbar, Footer, Card, Modal, dll)
│   │   ├── context/          # Auth Context & Global State
│   │   ├── pages/            # Halaman (Home, Books, Borrowings, AdminDashboard, Login, Register)
│   │   ├── services/         # API Service (Fetch client)
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── index.html
│   ├── vite.config.js        # Konfigurasi Vite
│   ├── tailwind.config.js    # Konfigurasi Tailwind CSS
│   └── package.json
│
├── .gitignore
└── README.md
```

---

## 🚀 Teknologi yang Digunakan

### Frontend
- **React 19**
- **Vite**
- **Tailwind CSS**
- **React Router DOM v7**
- **Lucide React** (Icons)

### Backend
- **Node.js** & **Express 5**
- **SQLite3**
- **JSON Web Token (JWT)**
- **Bcrypt.js** (Password hashing)
- **CORS**

---

## ⚙️ Cara Menjalankan Proyek

Pastikan Anda telah menginstal [Node.js](https://nodejs.org/) (versi 18+ direkomendasikan).

### 1. Menjalankan Backend (Server API)

Buka terminal pertama:
```bash
cd backend
npm install
npm run dev
# Atau: npm start
```
> Server akan berjalan di: `http://localhost:3000`  
> Database SQLite (`database.sqlite`) akan dibuat dan diisi data seed secara otomatis saat server pertama kali dijalankan.

### 2. Menjalankan Frontend (Client)

Buka terminal kedua:
```bash
cd frontend
npm install
npm run dev
```
> Frontend akan berjalan di: `http://localhost:5173` (atau port yang ditampilkan Vite)

---

## 🔑 Akun Uji Coba (Seed Data)

Database telah dilengkapi dengan akun bawaan untuk pengujian:

| Role | Username / Email | Password |
|---|---|---|
| **Admin** | `admin` / `admin@perpustakaan.com` | `admin123` |
| **Member / Pengunjung** | `budi` / `budi@gmail.com` | `user123` |
| **Member / Pengunjung** | `siti` / `siti@gmail.com` | `user123` |

---

## 📡 Daftar Endpoint API Utama

- **Auth**
  - `POST /api/auth/register` - Pendaftaran akun baru
  - `POST /api/auth/login` - Login akun (JWT)
  - `GET /api/auth/me` - Cek identitas pengguna saat ini
- **Books**
  - `GET /api/books` - Ambil daftar buku (mendukung filter pencarian & kategori)
  - `GET /api/books/categories` - Ambil daftar kategori buku
  - `GET /api/books/:id` - Detail buku
  - `POST /api/books` - Tambah buku baru (Admin)
  - `PUT /api/books/:id` - Edit buku (Admin)
  - `DELETE /api/books/:id` - Hapus buku (Admin)
- **Borrowings (Peminjaman)**
  - `POST /api/borrowings` - Ajukan peminjaman buku (Member)
  - `GET /api/borrowings/my` - Riwayat peminjaman saya (Member)
  - `GET /api/borrowings` - Semua data peminjaman (Admin)
  - `PUT /api/borrowings/:id/return` - Konfirmasi pengembalian buku (Admin)
