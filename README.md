# module-mta

Katalog unduhan indikator untuk aplikasi custom **MetaTrader 5**.

Gunakan APK custom **6313 / 500.6310-mtc.3** atau lebih baru untuk seluruh fitur terbaru. Host **API 3** menambahkan penanda harga pada sumbu chart dan tetap menerima paket API 1/2. **HPX Quarter Zones 2.3.1 memerlukan API 3**; APK6312 atau lebih lama menolak paket ini sampai aplikasi diperbarui. MA Ribbon, RSI Divergence, FiboZone dan HPX ZWave yang sudah tersedia tetap memakai paket API 2 yang sama. Paket `.mt5ind` merupakan hasil konversi indikator; MT5 Android resmi tidak menjalankan paket ini atau source `.mq5` secara langsung.

## Memasang indikator

1. Buka halaman **Modul** pada aplikasi. Katalog dimuat otomatis dari GitHub.
2. Unduh indikator yang diinginkan. Status berubah menjadi **Terpasang**, dan paket masuk ke library indikator.
3. Tambahkan indikator dari library ke chart, lalu atur parameternya pada halaman pengaturan indikator.
4. Hapus indikator dari chart untuk menghentikan tampilannya. Hapus paket dari library jika tidak diperlukan lagi.

Katalog: [`catalog.json`](https://raw.githubusercontent.com/handi425/module-mta/main/catalog.json).

## Indikator

| Indikator | Fungsi |
| --- | --- |
| MA Ribbon | Lima kurva SMA, EMA, SMMA, WMA atau VWMA sesuai pengaturan. |
| RSI Divergence | RSI dengan regular/hidden divergence dan validasi garis. |
| FiboZone Pro | Pivot Fibonacci, order block/breaker dan FVG. |
| HPX Quarter Zones | Grid quarter, zona, sub-quarter dan penanda harga pada sumbu chart; versi2.3.1 membutuhkan APK6313/API3. |
| HPX ZWave Pro | Analisis gelombang dan proyeksi dari riwayat harga. |
| EMA 20 / SMA 50 | Modul contoh moving average. |

Semua modul custom pada rilis ini berjalan tanpa push notification, suara, email atau notifikasi Android. Modul tidak membuka, mengubah atau menutup order.

Riwayat harga yang diperlukan harus sudah tersedia sebelum perhitungan dapat ditampilkan.

Lima port tambahan menggambar melalui Canvas tanpa membuat objek grafis chart. Garis, zona dan teks tetap terikat ke waktu/harga sumber ketika chart digeser atau diperbesar. HPX ZWave tidak memiliki tombol di chart; derajat proyeksi dipilih melalui `InpFibonacciDegree` pada pengaturan indikator.

Quarter menandai setiap level utama di skala harga kanan dengan warna levelnya. Jika angka level akan menutup harga berjalan atau terpotong batas chart, hanya tanda garis pada harga tepatnya yang ditampilkan.

Isi kotak OB, breaker dan FVG FiboZone memakai opasitas sekitar 15%, dengan warna batas serta jangkar waktu/harga tetap dipertahankan.

## Paket dan katalog

Setiap entri katalog mencantumkan identitas, versi, ukuran dan SHA-256 paket. Aplikasi memeriksa ukuran, hash dan tanda tangan paket sebelum memasukkannya ke library. Nama berkas unduhan tetap pada folder `modules/`; pembaruan isi paket harus disertai pembaruan metadata katalog.

Kunci penandatanganan dan kredensial akun tidak disimpan pada repository publik ini.

## Pembaruan APK

Unduh aplikasi custom dari [mtc_versi.apk](https://github.com/handi425/module-mta/releases/latest/download/mtc_versi.apk).
Nama aplikasi tetap **MetaTrader 5**. APK rilis dan [metadata pembaruan](https://github.com/handi425/module-mta/releases/latest/download/mtc_versi.json) tersedia publik; source host dan keystore tetap private.

Versi yang mendukung updater memeriksa GitHub saat aplikasi digunakan, dengan jeda pemeriksaan enam jam. APK baru diunduh dan diverifikasi otomatis; pemasangan tetap memerlukan persetujuan melalui installer Android. Izin memasang dari aplikasi ini diminta melalui pengaturan Android saat pertama kali diperlukan. Pemeriksaan manual tersedia pada **Modul → Update APK**.

Setiap rilis memakai versionCode lebih tinggi, package yang sama, serta sertifikat proyek yang sama. Tidak perlu uninstall. Berkas APK sementara dibersihkan setelah versi baru berjalan.

## Source HPX ZWave

Source HPX ZWave beserta perubahan port, bridge, generator, pengujian native dan
petunjuk build tersedia di [`sources/hpx-zwave-source.zip`](sources/hpx-zwave-source.zip).
Checksum tersedia pada [berkas SHA-256](sources/hpx-zwave-source.zip.sha256).
Notis asli dipertahankan, dan salinan lisensi MPL-2.0 disertakan pada arsip.
Source SDK API 3 dan skrip build SDK juga disertakan; native payload dan class Java
dapat dibangun tanpa keystore. Kunci privat tidak disertakan dalam arsip ini.
SDK baru bersifat tambahan: paket ZWave API2 yang dipublikasikan tetap kompatibel
dan payload native tidak berubah karena penambahan penanda harga SDK.
