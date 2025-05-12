# System Notifications (React + Vite Tailwind) Demo

This project demonstrates a system notification feature built using React, Vite, and Tailwind CSS. The code is private and not available for public access.

# HJMB - WhatsApp Dashboard with Customer Management

HJMB adalah sistem dashboard yang terintegrasi dengan WhatsApp Official API, Accurate, dan sistem manajemen pelanggan berbasis wilayah.

## 🔧 Fitur Utama

- 🔐 **Login Multi-user** dengan role dan wilayah (kategori)
- 👥 **Manajemen pelanggan** berdasarkan data dari Accurate
- 💬 **Chat pelanggan via WhatsApp** (Official API)
- 📑 **Template pesan** dinamis dengan variabel
- 📈 **Realtime chat** dengan socket.io
- 📂 **Kategori pelanggan** digunakan sebagai wilayah kerja user

---

## 📁 Struktur Project

```
HJMB/
├── backend/                # Server Express.js
│   ├── config/             # Configurasi tambahan
│   ├── controllers/        # Logika bisnis (auth, chat, message, etc)
│   ├── models/             # Skema Mongoose
│   ├── routes/             # REST API endpoint
│   ├── services/           # Layanan ke Accurate, WhatsApp API
│   ├── middleware/         # Autentikasi dan role check
│   ├── handlers/           # Olah data sebelum proses
│   ├── jobs/               # Penanganan jadwal sinkronisasi dan reminder
│   ├── tests/              # Unit test
│   ├── public/             # Statik folder untuk Frontend
│   ├── app.js              # Entry point backend
│   └── server.js           # Main
├── frontend/               # Aplikasi React
│   |── src/                # Halaman dan komponen
│   │   ├── assets/          # File media
│   │   ├── components/      # Komponen dan sub komponen reusable
│   │   ├── contexts/        # Auth Profider(Login, Regis, Token Refresh Token) dan Data Realtime
│   │   ├── layouts/         # Penanganan layout responsivitas
│   │   ├── pages/           # File halaman
│   │   ├── routes/          # Route ke halaman
│   │   ├── services/        # Berisi fungsi request API ke Backend dan SocketIO Client
│   │   ├── utils/           # Fungsi sederhana tambahan untuk kelola kalimat, format RP dll
│   │   ├── lib/             # Config api request dengan interceptors
│   │   ├── App.jsx         # Penggunaan contex
│   │   ├── main.jsx        # File main aplikasi
│   │   └── index.css       # Tailwind dan costum CSS
|   |── public/             # Statik folder
|   └── index.html          # Main HTML
├── .env                    # Variabel environment
├── README.md               # Dokumentasi ini
```

---

## 🚀 Cara Menjalankan

### 1. Clone dan Install

```bash
git clone https://github.com/xxxxx/hjmb.git
cd hjmb
```

### 2. Setup Frontend

```bash
cd ../frontend
npm install
npm run build
```

### 3. Setup Backend

```bash
cd backend
npm install
cp .env.example .env
# Edit .env: WABA_TOKEN, WABA_PHONE_NUMBER_ID, ACCURATE_TOKEN, MONGO_URI dll.
npm run dev
```

Pastikan backend berjalan di `http://localhost:5000`

---

## ⚙️ Backend - Endpoint Utama

| Endpoint | Method | Deskripsi |
|----------|--------|-----------|
| `/api/auth/login` | POST | Login dan dapatkan token |
| `/api/users/` | CRUD | Manajemen user |
| `/api/customers/` | CRUD | Data pelanggan dari Accurate |
| `/api/chats/` | CRUD | Data chat pelanggan |
| `/api/messages/` | GET/POST | Riwayat dan kirim pesan |
| `/api/templates/` | CRUD | Template pesan WhatsApp |

---

## 💡 Role & Wilayah

- Admin dapat mengelola semua user dan kategori wilayah.
- Setiap user memiliki role dan wilayah (kategori pelanggan).
- Chat dan pelanggan dibatasi hanya wilayah user.

---

## 💬 Sistem Chat WhatsApp

- Menggunakan WhatsApp Business API (official)
- Pesan disimpan di MongoDB (`messages`)
- Gunakan socket.io client untuk realtime update

---

## ✍️ Template Pesan

- Judul unik, hanya boleh alphanumeric dan underscore
- Variabel: bisa didefinisikan dan diberikan contoh
- Template mendukung header, body, footer, dan tombol

---

## 🔌 Socket.io

Socket aktif setelah login. Mendengarkan event:

- `new_message` → Diterima oleh client dan ditambahkan ke riwayat

---

## 👤 Dokumentasi User

### Admin
- Kelola user & role
- Sinkron data Accurate
- Tambah & atur template

### Operator
- Chat dengan pelanggan
- Gunakan template yang tersedia
- Hanya akses wilayah masing-masing

---

## 📚 Pengembangan Lanjutan

- Tambah notifikasi push/browser
- Export laporan
- Statistik pengingat & respon
- Integrasi CRM lain (selain Accurate)
- ...

---

## 📄 Lisensi

Proyek ini dikembangkan dengan ❤️ oleh mbingsdk untuk kebutuhan internal.