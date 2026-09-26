# Merangkai Cipta Nusantara

Landing page resmi **Merangkai Cipta Nusantara**, software house untuk web development, UI/UX design, dan jasa push followers.

## Live Website

https://merangkaiciptanusantara-tech.github.io/website-merata.id/

## Fitur

- Landing page responsive untuk desktop, tablet, dan mobile
- Branding Merangkai Cipta Nusantara dengan logo resmi
- Tampilan responsif dengan mode terang dan gelap
- Enam card layanan dengan gambar dan hover animation
- Bagian Our Projects dengan preview website ACC Japan Centre, GMI Japan, dan Rakerda Jateng 2025
- Daftar layanan:
  - Web Development
  - UI/UX Design
  - Mobile Apps Development
  - Graphic Design
  - API Service Development
  - Push Like Follower
- Kontak langsung melalui WhatsApp, Instagram, dan TikTok
- Kontak WhatsApp, Instagram, dan TikTok Merangkai Cipta Nusantara
- Kontak Instagram dan TikTok pemilik
- Deployment otomatis ke GitHub Pages saat ada push ke branch `main`

## Teknologi

- Vue 3
- Vite
- JavaScript
- CSS responsive
- GitHub Pages
- GitHub Actions

## Menjalankan Lokal

Pastikan Node.js versi 20 atau lebih baru sudah terpasang.

```bash
npm install
npm run dev
```

Buka alamat yang tampil di terminal, biasanya:

```text
http://localhost:5173/
```

## Production Build

Membuat build production:

```bash
npm run build
```

Menguji hasil build secara lokal:

```bash
npm run preview
```

Hasil production berada di folder `dist/`.

## Deployment GitHub Pages

Project menggunakan workflow:

```text
.github/workflows/pages.yml
```

Workflow GitHub Pages akan berjalan otomatis setiap push ke branch `main` atau `master`.

```bash
git add .
git commit -m "update website"
git push origin master
```

Pastikan GitHub Pages di repository sudah menggunakan source **GitHub Actions** jika masih ingin memakai alamat GitHub Pages:

1. Buka repository GitHub.
2. Masuk ke **Settings**.
3. Pilih **Pages**.
4. Pada bagian **Build and deployment**, pilih **GitHub Actions**.

## Deployment Otomatis ke Rumahweb

Workflow `.github/workflows/main.yml` akan membangun dan mengunggah folder `dist/` ke Rumahweb setiap push ke branch `main`. Untuk mengaktifkannya:

1. Buat akun FTP khusus di cPanel Rumahweb dan arahkan aksesnya ke document root domain. Rumahweb menjelaskan pembuatan akun FTP di [panduan resmi ini](https://www.rumahweb.com/journal/cara-membuat-akun-ftp-di-cpanel/).
2. Di GitHub repository, buka **Settings → Secrets and variables → Actions**.
3. Tambahkan repository secrets `FTP_SERVER`, `FTP_USERNAME`, dan `FTP_PASSWORD` sesuai detail akun FTP.
4. Jika akun FTP membuka root akun cPanel, tambahkan repository variable `FTP_SERVER_DIR` bernilai `public_html/`. Jika akun FTP dibatasi langsung ke document root domain, gunakan `./`.
5. Workflow menerima secret host bernama `FTP_SERVER` atau `FTP_HOST`. FTP dipakai secara default; jika Rumahweb mengaktifkan FTPS untuk akunmu, tambahkan variable `FTP_PROTOCOL` bernilai `ftps`.

Setelah secrets dan variable disimpan, push berikutnya akan otomatis memperbarui http://merangkaiciptanusantara.my.id/. Password FTP hanya disimpan di GitHub Secrets, bukan di file project. Lihat [panduan resmi GitHub untuk Actions Secrets](https://docs.github.com/en/actions/how-tos/write-workflows/choose-what-workflows-do/use-secrets).

## Struktur Project

```text
.
├── .github/
│   └── workflows/
│       └── deploy-pages.yml
├── public/
│   └── merangkai-cipta-nusantara.png
├── src/
│   ├── App.vue
│   ├── main.js
│   └── style.css
├── index.html
├── package.json
└── vite.config.js
```

## Kontak

- WhatsApp: https://wa.me/6285794909132
- Instagram: https://www.instagram.com/merata.id/
- TikTok: https://www.tiktok.com/@merata.id
- Instagram Owner: https://www.instagram.com/mohfiqih_/
- TikTok Owner: https://www.tiktok.com/@mohfiqih_/
