````md
# Sistem Penerimaan Mahasiswa Baru Pascasarjana (PMB)

🔗 **Live Deployment**
- 🌐 Frontend (Netlify): [https://pmb-gsp.netlify.app](https://gsp-pmb.netlify.app/)
- ⚙️ Backend API (Railway): [https://gsp-pmb-be.up.railway.app/api](https://gsp-pmb-be.up.railway.app/api)
- 🤖 Telegram Bot: [https://t.me/pmbgspbot](https://t.me/pmbgspbot)

Aplikasi web untuk mengelola proses Penerimaan Mahasiswa Baru (PMB) Program Pascasarjana (S2 & S3), mulai dari pendaftaran pendaftar, autentikasi, pengelolaan dokumen, hingga manajemen data oleh admin dan staf.

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
````

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

* [x] Registrasi pendaftar
* [x] Autentikasi pendaftar menggunakan **Telegram Bot**
* [x] Login menggunakan nomor pendaftaran dan kode akses
* [x] Update data diri pendaftar
* [x] Upload dokumen dan foto persyaratan (namun masih disimpan di folder public backend)

### Modul Administrator

* [x] Login admin
* [x] CRUD Program Studi (Prodi)
* [x] Melihat daftar pendaftar

### Modul Staff

* [x] Login staff
* [x] Melihat daftar pendaftar
* [x] Verifikasi dokumen pendaftar

---

## Catatan Teknis

### Arsitektur

* Aplikasi menggunakan arsitektur **client-server**
* Backend menyediakan REST API
* Frontend berkomunikasi dengan backend menggunakan HTTP request
* Autentikasi dan otorisasi menggunakan **JWT** dengan Role-Based Access Control (RBAC)

### Autentikasi Pendaftar

* Pendaftar melakukan registrasi melalui website
* Sistem menghasilkan token Telegram unik
* Pendaftar melakukan verifikasi dengan bot Telegram
* Bot Telegram mengirim **nomor pendaftaran** dan **kode akses**
* Login dilakukan menggunakan nomor pendaftaran dan kode akses

> Autentikasi menggunakan Telegram dipilih sebagai alternatif WhatsApp karena WhatsApp API bersifat berbayar.


### Kendala yang Ditemui

* Deploy server backend dan database
* Penyesuaian routing backend saat deployment di Railway
* Karena background saya frontend, jadi di awal saya terlalu fokus di backend. Sehingga waktu mengerjakan frontend nya sedikit dan terlalu terburu-buru

---

```

```
