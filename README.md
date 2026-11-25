# Blibli Seller — Inventory Sync & Stock Analytics

Dashboard portofolio berbasis PHP untuk memantau sinkronisasi stok inventaris, menganalisis kesehatan stok, dan mengidentifikasi SKU yang berisiko kehabisan barang.

> **Catatan demo:** Status koneksi dan proses sinkronisasi pada proyek ini adalah simulasi. Data perubahan disimpan dalam `PHP $_SESSION`, bukan dikirim ke API Blibli sungguhan. Data tren grafik tujuh hari juga merupakan data ilustrasi.

## Fitur

- Ringkasan KPI: SKU tersinkronisasi, stok menipis, selisih stok, dan estimasi potensi kehilangan omzet.
- Grafik tren stok tujuh hari dan distribusi kesehatan inventaris menggunakan Chart.js.
- Filter kategori dan status sinkronisasi, serta pencarian nama produk/SKU.
- Sinkronisasi seluruh inventaris atau satu SKU tanpa reload halaman.
- Ekspor laporan inventaris ke CSV.
- Proteksi request sinkronisasi menggunakan token CSRF berbasis session.
- Contoh skema tabel MySQL dan seed data tersedia di `database.sql`.

## Teknologi

- PHP 8+
- HTML, Tailwind CSS CDN, dan JavaScript
- Chart.js CDN
- Lucide Icons CDN
- MySQL (skema contoh; aplikasi demo saat ini memakai PHP session)

## Struktur folder

```text
blibli-inventory-dashboard/
├── index.php
├── database.sql
├── api/
│   ├── sync_handler.php
│   └── export_csv.php
├── assets/
│   └── js/
│       └── dashboard.js
└── data/
    └── mock_inventory.php
```

## Instalasi di XAMPP

1. Pastikan PHP 8+ aktif di XAMPP.
2. Salin atau clone folder proyek ke direktori `htdocs`, misalnya:
   `C:\xampp\htdocs\blibli-inventory-dashboard`
3. Jalankan Apache dari XAMPP Control Panel.
4. Buka alamat berikut di browser:
   `http://localhost/blibli-inventory-dashboard/`
5. Klik **Sync Now** atau **Force Sync** untuk mencoba sinkronisasi simulasi.
6. Gunakan **Export CSV** untuk mengunduh laporan.

### Opsional: impor skema MySQL

1. Buka phpMyAdmin.
2. Jalankan/import file `database.sql`.
3. Contoh tersebut membuat database `blibli_inventory` dan tabel `tb_inventory_sync`.

Aplikasi demo ini belum membaca atau menulis ke database; penggunaan MySQL memerlukan lapisan koneksi dan penggantian penyimpanan session sesuai kebutuhan deployment.

## Keamanan dan batasan demo

- Endpoint sinkronisasi hanya menerima metode `POST` dan memvalidasi token CSRF.
- Nilai tabel dibuat dengan escaping pada frontend.
- CSV diberi proteksi dasar terhadap formula injection.
- CDN Tailwind, Chart.js, dan Lucide membutuhkan koneksi internet.
- Untuk produksi, gunakan HTTPS, validasi autentikasi/otorisasi, logging, konfigurasi secrets di environment, dan integrasi resmi API Blibli.

## Lisensi

Proyek ini tersedia di bawah [MIT License](https://opensource.org/licenses/MIT).