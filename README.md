# FDS | Fintechno Development Solution

Landing page resmi untuk **Fintechno Development Solution (FDS)**, digital partner untuk kebutuhan website, desain grafis, dan UI/UX.

## Live Website

https://fintechnodevelopmentsolution-sudo.github.io/website-fds/

## Fitur

- Landing page responsive untuk desktop, tablet, dan mobile
- Branding FDS dengan logo resmi
- Loading screen transparan dengan animasi logo
- Card layanan dengan gambar dan hover animation
- Daftar layanan:
  - Landing Page
  - Website Professional
  - Website Company Profile
  - Website Personal Branding
  - Website Custom
  - Website Undangan Online
  - Desain Grafis
  - UI/UX Figma
- Form brief project interaktif
- Kontak WhatsApp, Instagram, dan TikTok FDS
- Kontak Instagram dan TikTok pemilik
- Deployment otomatis ke GitHub Pages melalui GitHub Actions

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
.github/workflows/deploy-pages.yml
```

Workflow akan berjalan otomatis setiap push ke branch `master`.

```bash
git add .
git commit -m "update website"
git push origin master
```

Pastikan GitHub Pages di repository sudah menggunakan source **GitHub Actions**:

1. Buka repository GitHub.
2. Masuk ke **Settings**.
3. Pilih **Pages**.
4. Pada bagian **Build and deployment**, pilih **GitHub Actions**.

## Struktur Project

```text
.
├── .github/
│   └── workflows/
│       └── deploy-pages.yml
├── public/
│   └── logo.jpg
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
- Instagram FDS: https://www.instagram.com/fintechno_/
- TikTok FDS: https://www.tiktok.com/@fintechno_/
- Instagram Owner: https://www.instagram.com/mohfiqih_/
- TikTok Owner: https://www.tiktok.com/@mohfiqih_/
