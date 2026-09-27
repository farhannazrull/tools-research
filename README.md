# tools-research — Boilerplate Astro Modular

Boilerplate web statis pakai Astro. Navbar dan Footer ditulis **1x**, dipakai di semua halaman. Tidak perlu copy-paste HTML lagi.

## Struktur Folder

```
src/
  components/
    Navbar.astro   # Logo "MyApp" + menu Home, About, Contact
    Footer.astro   # Copyright + link sosmed
  layouts/
    MainLayout.astro  # Kerangka <html> + <Navbar /> + <slot /> + <Footer />
  pages/
    index.astro    # Route "/"
    about.astro    # Route "/about"
public/            # File statis (gambar, favicon)
```

## Cara Jalanin

```bash
npm install
npm run dev
```

Buka `http://localhost:4321` (home) dan `http://localhost:4321/about`.

Build produksi:

```bash
npm run build
npm run preview
```

Hasilnya keluar di `dist/`, siap upload ke Netlify / Vercel / GitHub Pages.

## Cara Pakai

**1. Ubah Navbar / Footer sekali, berlaku ke semua halaman.**
Edit `src/components/Navbar.astro` atau `Footer.astro`, simpan, semua halaman otomatis ikut berubah karena semuanya dibungkus `MainLayout`.

**2. Tambah halaman baru.**
Bikin file baru di `src/pages/`, contoh `src/pages/contact.astro`:

```astro
---
import MainLayout from '../layouts/MainLayout.astro';
---
<MainLayout>
  <h1>Kontak</h1>
  <p>Hubungi kami di sini.</p>
</MainLayout>
```

File itu otomatis jadi route `/contact`. Tidak perlu nulis `<html>`, navbar, atau footer lagi.

## Kenapa Modular?

Setiap file `.html` dulu (misal `home-1.html`, `home-2.html`) bawa salinan Navbar/Footer sendiri, jadi 1 perubahan = edit semua file. Di sini komponen di-`import` sekali dan dipakai ulang lewat `<slot />`, jadi 1 perubahan = edit 1 file.
