# EcoSort AR

Aplikasi WebAR edukasi pilah sampah. Arahkan kamera HP ke marker kategori sampah (organik / anorganik / B3) untuk melihat overlay AR berisi informasi cara membuang yang benar.

## Struktur File

```
site/
├── index.html      # Aplikasi AR utama (buka ini di HP)
├── markers.html     # Halaman kartu marker untuk dicetak/discan
├── markers/
│   ├── 0.png         # Marker kategori ORGANIK
│   ├── 1.png         # Marker kategori ANORGANIK
│   └── 2.png         # Marker kategori B3
└── README.md
```

## Cara Deploy ke GitHub Pages (gratis, ~5 menit)

1. Buat repository baru di GitHub, misalnya `ecosort-ar`.
2. Upload semua isi folder `site/` ke root repository tersebut (jangan masukkan folder `site` itu sendiri, isinya saja).
3. Buka **Settings → Pages** di repo tersebut.
4. Pada **Branch**, pilih `main` (atau `master`) dan folder `/root`, lalu klik **Save**.
5. Tunggu 1-2 menit. URL aplikasi akan muncul di bagian atas, formatnya:
   `https://<username-github>.github.io/ecosort-ar/`
6. Aplikasi AR bisa diakses di `.../index.html`, dan kartu marker cetak di `.../markers.html`.

## Cara Testing di HP

1. Buka `index.html` versi online (harus HTTPS — GitHub Pages sudah otomatis HTTPS, kamera tidak akan aktif di HTTP biasa).
2. Izinkan akses kamera saat diminta browser.
3. Buka halaman `markers.html` di **layar lain** (laptop/HP kedua) atau cetak halaman itu di kertas.
4. Arahkan kamera HP ke salah satu marker (Organik / Anorganik / B3).
5. Overlay AR berisi nama kategori sampah dan tips pembuangan akan muncul di atas marker.

## Kenapa pakai Barcode Marker (bukan foto kemasan produk asli)?

Untuk versi cepat ini dipakai **barcode marker** bawaan AR.js (pola kotak hitam-putih) karena:
- Tidak perlu proses training marker dari foto produk.
- Deteksinya sangat stabil dan cepat dibanding pattern marker custom.

**Untuk mengembangkan ke arah proposal asli** (marker dari foto kemasan produk sungguhan), langkahnya:
1. Siapkan foto kemasan produk (kontras tinggi, pola unik) — misalnya logo pada kemasan.
2. Buka [AR.js Marker Training Tool](https://ar-js-org.github.io/AR.js/three.js/examples/marker-training/examples/generator.html).
3. Upload foto, generator akan membuat file `.patt`.
4. Ganti `<a-marker type="barcode" value="0">` menjadi `<a-marker type="pattern" patternUrl="markers/nama-produk.patt">` di `index.html`.

## Kategori Sampah yang Tersedia

| Marker | Kategori | Warna |
|---|---|---|
| Barcode 0 | Organik | Hijau |
| Barcode 1 | Anorganik | Biru |
| Barcode 2 | B3 (Berbahaya & Beracun) | Merah |
