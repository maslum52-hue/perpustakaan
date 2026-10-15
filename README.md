# Perpustakaan Digital SMAN 1 Halmahera Timur

Aplikasi lokal berbasis React, Vite, Tailwind CSS, dan Dexie/IndexedDB untuk katalog, anggota, sirkulasi, QR, laporan, serta backup perpustakaan.

## Menjalankan

1. Pasang Node.js versi 20 atau lebih baru.
2. Buka folder proyek, lalu jalankan `npm install`.
3. Jalankan `npm run dev` dan buka alamat localhost yang ditampilkan Vite.
4. Kamera membutuhkan izin browser dan konteks aman (`localhost` atau HTTPS). Untuk penggunaan dari laptop lain melalui jaringan sekolah, pasang HTTPS pada server jaringan; halaman HTTP biasa umumnya tidak dapat mengakses kamera.

## Akun awal

- Admin: `admin` / `smansa123`
- Guru: `guru` / `smansa123`
- Siswa: `siswa` / `smansa123`

Ganti kata sandi melalui **Pengaturan → Akun lokal**. Hash SHA-256 dilakukan di browser. Ini cocok untuk uji coba pada satu profil browser, bukan autentikasi kuat untuk layanan publik.

## Fitur

- Penyimpanan utama pada IndexedDB database `PerpustakaanSMANSAHT`, termasuk akun, buku, eksemplar, anggota, pinjaman, pengaturan, dan aktivitas.
- CRUD buku dan anggota, pencarian, grid/tabel katalog, status anggota, dan data demo awal.
- Peminjaman berbasis pemindaian QR anggota lalu QR eksemplar; validasi dan pembaruan stok dijalankan dalam transaksi Dexie. Pengembalian dapat melalui QR atau kode manual.
- Kebijakan jumlah transaksi dan lama pinjam dapat diubah di Pengaturan.
- Ekspor CSV laporan, koleksi, dan anggota; backup JSON dan pemulihan dengan konfirmasi.
- Cetak QR satu eksemplar per judul melalui katalog.

## QR dan transaksi

Setiap salinan fisik memiliki kode inventaris sendiri. QR buku berisi kode itu saja. Di halaman **Scan QR**, pilih peminjaman, pindai QR anggota, kemudian QR eksemplar. Tinjau daftar dan konfirmasi peminjaman; pemindaian sendiri tidak menyelesaikan transaksi. Untuk pengembalian, pilih tab **Pengembalian**, lalu pindai kode inventaris.

## Backup dan batas penggunaan lokal

Ekspor backup JSON dari **Pengaturan → Backup & pemulihan**. File backup menyertakan seluruh tabel IndexedDB. Pemulihan memvalidasi format dasar dan mengganti data lokal setelah konfirmasi. Data berada di browser/perangkat yang dipakai dan tidak tersinkron dengan laptop lain. Untuk penggunaan banyak perangkat dengan akun dan data bersama, migrasikan layanan transaksi dan autentikasi ke API backend dengan database server serta penyimpanan gambar terpusat.

## Catatan cakupan

Foto sampul/anggota, impor CSV, kartu anggota, perpanjangan pinjaman, denda aktual, laporan anggota/buku terpopuler, sinkronisasi beberapa kamera, penggabungan backup, dan migrasi data demo penuh belum disediakan. Antarmuka menjelaskan data lokal secara eksplisit; hindari memakai akun demo atau data pribadi sungguhan pada perangkat bersama. Data demo dimasukkan sekali saat database belum berisi buku, anggota, atau akun.
