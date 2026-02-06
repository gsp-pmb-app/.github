# Sistem Penerimaan Mahasiswa Baru Pascasarjana (PMB)

🔗 **Live Deployment**

- 🌐 Frontend (Netlify): https://pmb-gsp.netlify.app  
  **Akun Demo:**

  **Admin**
  - username: admin
  - password: admin

  **Staff**
  - username: staff
  - password: staff

  **User / Pendaftar**
  - no pendaftaran: PMB076620283
  - kode akses: 2VHICE

- ⚙️ Backend API (Railway): https://gsp-pmb-be.up.railway.app/api
- 🤖 Telegram Bot: https://t.me/pmbgspbot

---

## Tech Stack

### Backend

- Node.js
- Express.js
- MySQL
- Sequelize ORM
- JSON Web Token (JWT)
- Telegram Bot API (untuk autentikasi pendaftar)
- Railway (deployment)
- Ngrok (keperluan testing lewat local)

### Frontend

- React.js
- Tailwind CSS
- Redux Toolkit
- Netlify (deployment)

### Database

- MySQL
- Railway (deployment)

---

## Cara Menjalankan Aplikasi

### Backend

1. Clone repository [backend](https://github.com/gsp-pmb-app/pmb-be)
2. Install dependencies:

   ```bash
   npm install
   ```

3. Konfigurasi environment variable:

   ```env
   NOE_ENV=
   PORT=
   DB_HOST=
   DB_USER=
   DB_PORT=
   DB_PASS=
   DB_NAME=
   ACCESS_TOKEN_SECRET=
   TELEGRAM_BOT_TOKEN=
   FE_URL=
   DATABASE_URL=
   ```

4. Jalankan server:

   ```bash
   npm run dev
   ```

   NOTE: Saat menjalankan server backend secara lokal, diperlukan **NGROK** untuk menghubungkan server lokal dengan Telegram agar webhook dapat berfungsi dengan baik.

### Frontend

1. Clone repository [frontend](https://github.com/gsp-pmb-app/pmb-fe)
2. Install dependencies:

   ```bash
   npm install
   ```

3. Jalankan aplikasi:

   ```bash
   npm run dev
   ```

---

## Fitur yang Diimplementasikan

### Modul Pendaftar/User

- Registrasi pendaftar
- Autentikasi pendaftar menggunakan **Telegram Bot**
- Login menggunakan nomor pendaftaran dan kode akses
- Update data diri pendaftar
- Upload dokumen dan foto persyaratan (namun masih disimpan di folder public backend)

### Modul Administrator

- Login admin
- CRUD Program Studi (Prodi)
- Melihat daftar pendaftar

### Modul Staff

- Login staff
- Melihat daftar pendaftar
- Verifikasi dokumen pendaftar

---

## Catatan Teknis

### Arsitektur

- Aplikasi menggunakan arsitektur **client-server**
- Backend menyediakan REST API
- Frontend berkomunikasi dengan backend menggunakan HTTP request
- Autentikasi dan otorisasi menggunakan **JWT** dengan Role-Based Access Control (RBAC)

### Autentikasi Pendaftar

- Pendaftar melakukan registrasi melalui website
- Sistem menghasilkan token Telegram unik
- Pendaftar melakukan verifikasi dengan bot Telegram
- Bot Telegram mengirim **nomor pendaftaran** dan **kode akses**
- Login dilakukan menggunakan nomor pendaftaran dan kode akses

### Asumsi

- Autentikasi pendaftar dibuat menggunakan Telegram Bot sebagai pengganti WhatsApp karena WhatsApp API berbayar dan kurang praktis untuk kebutuhan testing.
- Untuk sementara, file dokumen dan foto disimpan di folder public backend, bukan menggunakan S3 Object Storage, agar implementasi lebih sederhana sesuai waktu pengerjaan.
- Alur pendaftaran dibuat fleksibel, di mana pendaftar bisa login terlebih dahulu lalu melengkapi data diri dan upload dokumen secara bertahap.
- Pembatasan kuota jadwal ujian dilakukan di backend untuk mencegah peserta memilih jadwal yang sudah penuh.
- Beberapa fitur disederhanakan untuk fokus pada alur utama sistem PMB sesuai waktu pengerjaan yang tersedia.

### Kendala yang Ditemui

- Deploy server backend dan database
- Penyesuaian routing backend saat deployment di Railway
- Karena background saya frontend, jadi di awal saya terlalu fokus di backend. Sehingga waktu mengerjakan frontend nya sedikit dan terlalu terburu-buru

---
