# PGRI Web — Laravel Statis Multi-Daerah

Website resmi PGRI yang bisa di-deploy untuk setiap daerah hanya dengan mengubah file `.env`.

---

## Fitur

- **Multi-daerah dari `.env`** — nama daerah, provinsi, kontak, statistik semuanya dari environment variable
- **Pengurus pusat terpusat** — data di `config/pengurus.php`, sama untuk semua daerah
- **5 halaman hidup** — Beranda, Profil, Berita, Pengurus, Kontak
- **Mobile responsive** — navbar hamburger, grid responsif
- **Ticker pengumuman** — bar info kontak di bawah navbar
- Modern dengan Tailwind CSS + Google Fonts (Plus Jakarta Sans + Lora)

---

## Setup Cepat

```bash
# 1. Clone & install
git clone ...
cd pgri-web
composer install

# 2. Salin env
cp .env.example .env
php artisan key:generate

# 3. Edit konfigurasi daerah di .env
nano .env

# 4. Jalankan
php artisan serve
```

---

## Konfigurasi Daerah (.env)

| Variable              | Keterangan                        | Contoh                        |
|-----------------------|-----------------------------------|-------------------------------|
| `PGRI_DAERAH`         | Nama daerah                       | `Sumatera Utara`              |
| `PGRI_PROVINSI`       | Nama provinsi                     | `Provinsi Sumatera Utara`     |
| `PGRI_SINGKATAN`      | Singkatan untuk display ringkas   | `PGRI Sumut`                  |
| `PGRI_ALAMAT`         | Alamat kantor                     | `Jl. Pendidikan No. 1, Medan` |
| `PGRI_KOTA`           | Nama kota                         | `Medan`                       |
| `PGRI_KODE_POS`       | Kode pos                          | `20111`                       |
| `PGRI_TELEPON`        | Nomor telepon                     | `(061) 123456`                |
| `PGRI_EMAIL`          | Email resmi                       | `pgri-sumut@pgri.or.id`       |
| `PGRI_JUMLAH_ANGGOTA` | Statistik anggota                 | `85.000+`                     |
| `PGRI_JUMLAH_CABANG`  | Jumlah cabang/kecamatan           | `33`                          |
| `PGRI_TAHUN_BERDIRI`  | Tahun berdiri daerah              | `1945`                        |

---

## Struktur File

```
├── .env.example               ← template konfigurasi daerah
├── config/
│   ├── pgri.php               ← membaca dari .env
│   └── pengurus.php           ← data pengurus pusat (edit langsung)
├── routes/web.php             ← 5 route halaman
├── app/Http/Controllers/
│   └── PageController.php     ← logic semua halaman
└── resources/views/
    ├── layouts/app.blade.php  ← layout utama (navbar, footer)
    └── pages/
        ├── beranda.blade.php
        ├── profil.blade.php
        ├── berita.blade.php
        ├── pengurus.blade.php
        └── kontak.blade.php
```

---

## Update Pengurus Pusat

Edit `config/pengurus.php` — perubahan langsung berlaku di semua daerah tanpa deploy ulang.

---

## Deploy ke Daerah Lain

Cukup salin project dan ubah `.env`:
```
PGRI_DAERAH="DKI Jakarta"
PGRI_PROVINSI="Daerah Khusus Ibukota Jakarta"
PGRI_SINGKATAN="PGRI DKI"
...
```

Tidak perlu menyentuh kode sama sekali.
