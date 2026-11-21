# module-mta

Katalog unduhan indikator untuk aplikasi custom **MetaTrader 5**.

Gunakan APK custom `metatrader5.apk` yang mendukung **API modul versi 2** (`PlotFrame` dan `HistoryIndicatorPlugin`). APK custom versi lama perlu diperbarui satu kali; host lama menolak paket API 2 dengan pesan versi tidak didukung. Paket `.mt5ind` merupakan hasil konversi indikator; MT5 Android resmi tidak menjalankan paket ini atau source `.mq5` secara langsung.

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
| HPX Quarter Zones | Grid quarter, zona dan sub-quarter berdasarkan ukuran pip/tick. |
| HPX ZWave Pro | Analisis gelombang dan proyeksi dari riwayat harga. |
| EMA 20 / SMA 50 | Modul contoh moving average. |

Semua modul custom pada rilis ini berjalan tanpa push notification, suara, email atau notifikasi Android. Modul tidak membuka, mengubah atau menutup order.

Riwayat harga yang diperlukan harus sudah tersedia sebelum perhitungan dapat ditampilkan.

Lima port tambahan menggambar melalui Canvas tanpa membuat objek grafis chart. Garis, zona dan teks tetap terikat ke waktu/harga sumber ketika chart digeser atau diperbesar. HPX ZWave tidak memiliki tombol di chart; derajat proyeksi dipilih melalui `InpFibonacciDegree` pada pengaturan indikator.

Isi kotak OB, breaker dan FVG FiboZone memakai opasitas sekitar 15%, dengan warna batas serta jangkar waktu/harga tetap dipertahankan.

## Paket dan katalog

Setiap entri katalog mencantumkan identitas, versi, ukuran dan SHA-256 paket. Aplikasi memeriksa ukuran, hash dan tanda tangan paket sebelum memasukkannya ke library. Nama berkas unduhan tetap pada folder `modules/`; pembaruan isi paket harus disertai pembaruan metadata katalog.

Kunci penandatanganan dan kredensial akun tidak disimpan pada repository publik ini.

## Source HPX ZWave

Source HPX ZWave beserta perubahan port, bridge, generator, pengujian native dan
petunjuk build tersedia di [`sources/hpx-zwave-source.zip`](sources/hpx-zwave-source.zip).
Checksum tersedia pada [berkas SHA-256](sources/hpx-zwave-source.zip.sha256).
Notis asli dipertahankan, dan salinan lisensi MPL-2.0 disertakan pada arsip.
Source SDK API 2 dan skrip build SDK juga disertakan; native payload dan class Java
dapat dibangun tanpa keystore. Kunci privat tidak disertakan dalam arsip ini.
