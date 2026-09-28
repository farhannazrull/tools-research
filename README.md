# tools-research: Boilerplate Astro Modular

Repositori ini berisi boilerplate situs web statis yang dibangun dengan Astro. Komponen Navbar dan Footer ditulis satu kali dan digunakan kembali pada seluruh halaman, sehingga duplikasi kode HTML tidak diperlukan.

## Struktur Direktori

```
src/
  components/
    Navbar.astro      : Logo teks "MyApp" beserta menu navigasi Home, About, dan Contact
    Footer.astro      : Informasi hak cipta beserta tautan media sosial
  layouts/
    MainLayout.astro  : Kerangka dokumen HTML yang memuat Navbar, slot konten, dan Footer
  pages/
    index.astro       : Halaman utama pada rute "/"
    about.astro       : Halaman profil pada rute "/about"
public/               : Direktori untuk berkas statis seperti gambar dan favicon
```

## Instalasi dan Menjalankan Proyek

Instal seluruh dependensi:

```bash
npm install
```

Menjalankan server pengembangan:

```bash
npm run dev
```

Akses aplikasi pada alamat `http://localhost:4321` untuk halaman utama dan `http://localhost:4321/about` untuk halaman profil.

Membuat hasil build produksi:

```bash
npm run build
npm run preview
```

Hasil build akan dihasilkan pada direktori `dist/` dan dapat diterbitkan melalui layanan seperti Netlify, Vercel, atau GitHub Pages.

## Panduan Penggunaan

**1. Memperbarui Navbar atau Footer.**
Perubahan pada berkas `src/components/Navbar.astro` atau `src/components/Footer.astro` akan diterapkan secara otomatis pada seluruh halaman, karena setiap halaman menggunakan `MainLayout` sebagai pembungkus.

**2. Menambahkan halaman baru.**
Buat berkas baru pada direktori `src/pages/`. Sebagai contoh, `src/pages/contact.astro`:

```astro
---
import MainLayout from '../layouts/MainLayout.astro';
---
<MainLayout>
  <h1>Kontak</h1>
  <p>Hubungi kami melalui halaman ini.</p>
</MainLayout>
```

Berkas tersebut akan tersedia secara otomatis pada rute `/contact` tanpa perlu menulis ulang kerangka dokumen, Navbar, atau Footer.

## Latar Belakang Arsitektur Modular

Pada pendekatan sebelumnya, setiap berkas HTML seperti `home-1.html` dan `home-2.html` memuat salinan Navbar dan Footer masing-masing, sehingga satu perubahan mengharuskan penyuntingan pada seluruh berkas. Pada pendekatan ini, komponen didefinisikan satu kali, diimpor sesuai kebutuhan, dan konten spesifik halaman disalurkan melalui elemen `slot`. Dengan demikian, satu perubahan hanya memerlukan penyuntingan pada satu berkas.
