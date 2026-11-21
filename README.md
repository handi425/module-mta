# module-mta

Katalog unduhan indikator untuk aplikasi custom **MetaTrader 5**.

Gunakan APK custom **6314 / 500.6310-mtc.4** atau lebih baru untuk seluruh fitur terbaru. Host **API 4** mendukung Smart Money Concepts [LuxAlgo] dan tetap menerima paket API 1/2/3. **SMC memerlukan APK 6314/API 4**; **HPX Quarter Zones 2.3.1 tetap memerlukan minimal APK 6313/API 3**. Katalog berisi delapan paket: enam port dan dua contoh MA. Ketujuh paket terdahulu dipertahankan tanpa perubahan. Paket `.mt5ind` merupakan hasil konversi indikator; MT5 Android resmi tidak menjalankan paket ini atau source MQL5/Pine secara langsung.

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
| HPX Quarter Zones | Grid quarter, zona, sub-quarter dan penanda harga pada sumbu chart; versi 2.3.1 membutuhkan minimal APK 6313/API 3. |
| HPX ZWave Pro | Analisis gelombang dan proyeksi dari riwayat harga. |
| Smart Money Concepts [LuxAlgo] | Struktur internal/swing, BOS/CHoCH, OB, EQH/EQL, FVG MTF, level D1/W1/MN1, zona premium/discount dan warna candle; membutuhkan APK 6314/API 4. |
| EMA 20 / SMA 50 | Modul contoh moving average. |

Semua modul custom pada rilis ini berjalan tanpa push notification, suara, email atau notifikasi Android. Modul tidak membuka, mengubah atau menutup order.

Riwayat harga yang diperlukan harus sudah tersedia sebelum perhitungan dapat ditampilkan.

Enam port tambahan menggambar melalui Canvas tanpa membuat objek grafis chart. Garis, zona dan teks tetap terikat ke waktu/harga sumber ketika chart digeser atau diperbesar. HPX ZWave tidak memiliki tombol di chart; derajat proyeksi dipilih melalui `InpFibonacciDegree` pada pengaturan indikator.

SMC menyediakan seluruh 52 kontrol input sumber yang dapat diedit, bersama delapan judul bagian pada 60 baris halaman parameter native. Pilihan timeframe FVG mencakup `Current` dan 21 timeframe MT5. Ketika riwayat broker masih dimuat, indikator menunggu dan mencoba lagi tanpa menghapus pemasangannya. SMC tidak mempunyai alert atau notifikasi.

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
Pembaruan APK tidak memperbarui paket indikator di library secara otomatis; unduh atau perbarui paket SMC terpisah melalui halaman Modul.

## Source Smart Money Concepts

Smart Money Concepts [LuxAlgo] berasal dari [publikasi resmi LuxAlgo](https://www.tradingview.com/script/CnB3fSph-Smart-Money-Concepts-SMC-LuxAlgo/), © LuxAlgo. Port Java/Canvas, Pine asli, SDK API 4, pengujian dan petunjuk build tersedia di [`sources/luxalgo-smc-source.zip`](sources/luxalgo-smc-source.zip), dengan checksum pada [berkas SHA-256](sources/luxalgo-smc-source.zip.sha256).

Source dan adaptasi SMC didistribusikan dengan [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) untuk penggunaan nonkomersial. Pertahankan atribusi LuxAlgo, pemberitahuan perubahan dan lisensi yang sama ketika mendistribusikan adaptasi. Port menghapus seluruh alert dan mengganti gambar Pine dengan Canvas; port ini tidak disponsori atau disahkan LuxAlgo. Keystore dan source host privat tidak disertakan dalam ZIP publik.

## Source HPX ZWave

Source HPX ZWave beserta perubahan port, bridge, generator, pengujian native dan
petunjuk build tersedia di [`sources/hpx-zwave-source.zip`](sources/hpx-zwave-source.zip).
Checksum tersedia pada [berkas SHA-256](sources/hpx-zwave-source.zip.sha256).
Notis asli dipertahankan, dan salinan lisensi MPL-2.0 disertakan pada arsip.
Arsip ZWave tetap memuat source SDK API 3 dan skrip build SDK; native payload dan class Java
dapat dibangun tanpa keystore. Kunci privat tidak disertakan dalam arsip ini.
Arsip ini tidak diperbarui ke API 4 pada rilis SMC. Paket ZWave API 2 yang
dipublikasikan tetap kompatibel dan payload native tidak berubah.
