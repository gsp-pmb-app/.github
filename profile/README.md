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
  - no pendaftaran: PMB217033579
  - kode akses: IZI0PA

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
- Cloudinary (penyimpanan file & gambar)
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
   NODE_ENV=
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
   CLOUDINARY_CLOUD_NAME=
   CLOUDINARY_API_KEY=
   CLOUDINARY_API_SECRET=
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
- Upload dokumen dan foto persyaratan ke Cloudinary
- Melihat data yang sudah diupload
- Melihat, mengunduh, dan mencetak kartu ujian
- Melihat hasil kelulusan ujian

### Modul Administrator

- Login admin
- Melihat daftar pendaftar 
- CRUD Program Studi (Prodi)
- CRUD Ruangan
- CRUD Jadwal

### Modul Staff

- Login staff
- Melihat daftar pendaftar
- Melakukan verifikasi dokumen pendaftar
- Input nilai pendaftar (mekanisme kelulusan otomatis dari backend, jika nilai >=75 maka lulus)
- Melihat hasil yudisium berdasarkan status pendaftar (belum ujian, lulus, tidak lulus)

---

## Catatan Teknis

### Arsitektur

- Aplikasi menggunakan arsitektur **client-server**
- Backend menyediakan REST API
- Frontend berkomunikasi dengan backend menggunakan HTTP request
- Autentikasi dan otorisasi menggunakan **JWT**
- File dan gambar disimpan menggunakan Cloudinary

### Asumsi

- Penyimpanan file menggunakan Cloudinary sebagai alternatif S3 Object Storage
- Notifikasi WA belum diimplementasikan dan digantikan dengan Telegram Auth
- Fokus implementasi pada core system (auth, role, data flow)

### Kendala yang Ditemui

- Deploy server backend dan database
- Penyesuaian routing backend saat deployment di Railway
- Fitur manajemen user (CRUD staff/admin) belum sempat diimplementasikan karena keterbatasan waktu. Untuk keperluan demo, akun admin dan staff telah disediakan, dengan kontrol akses tetap berjalan sesuai role.

---
