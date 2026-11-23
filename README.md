# module-mta

Katalog unduhan indikator untuk aplikasi custom **MetaTrader 5**.

APK terbaru **6320 / 500.6310-mtc.10** menambahkan sakelar **PLAN di chart** pada halaman Modul. OFF menyembunyikan tombol/garis dan membatalkan ARM; ON menampilkan fitur lagi tanpa mengaktifkan ARM otomatis. Aplikasi menyediakan tombol **PLAN** mengambang yang dapat digeser, dengan flyout **Atur PLAN** khusus pada tab Chart. Flyout juga memuat informasi margin serta pengaturan garis horizontal MC/Margin Call dan LIQUIDATION STOP; stop-out memakai fallback EA 50% yang dapat diubah. Pengaturan mencakup BUY/SELL, DIRECT/RETEST, Knife, layer/grid, LOT/Risk%, SL/TP dan timeframe konfirmasi. Simpan draf untuk menampilkan garis yang dapat digeser, lalu tinjau dan tekan ARM untuk mengaktifkan pengiriman order setelah candle tertutup. Perubahan pengaturan/level, pergantian akun/chart, restart atau meninggalkan aplikasi membatalkan ARM. Pemantauan pending berjalan saat aplikasi terbuka. Tidak ada notifikasi tambahan. Alur pengiriman diuji memakai broker simulasi; eksekusi broker sesungguhnya belum diuji.

Zwave Core 1.0.0 memerlukan **API 6/APK 6317**. Katalog tetap berisi tujuh indikator custom dengan paket yang sama. Host API 6 menerima paket API 1–6. SMC 1.0.2 tetap memerlukan minimal APK 6316/API 5, sedangkan HPX Quarter Zones 2.3.1 memerlukan APK 6313/API 3. PLAN tersedia di APK dan tidak menambahkan paket indikator ke katalog.

Paket `.mt5ind` merupakan hasil konversi indikator. Aplikasi custom memakai package `net.metaquotes.metatrader5` dan label **MetaTrader 5**; MT5 Android resmi tidak menyediakan API modul ini atau menjalankan source MQL5/Pine secara langsung.

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
| Smart Money Concepts [LuxAlgo] | Struktur internal/swing, BOS/CHoCH, OB, EQH/EQL, FVG MTF, level D1/W1/MN1, zona premium/discount dan warna candle; membutuhkan APK 6316/API 5. |
| Zwave Core | ZigZag/Elliott, MACD divergence, Fibonacci dan shadow korelasi dari feed broker; versi 1.0.0 membutuhkan APK 6317/API 6. |

Semua modul custom pada rilis ini berjalan tanpa push notification, suara, email atau notifikasi Android. Modul tidak membuka, mengubah atau menutup order.

Riwayat harga yang diperlukan harus sudah tersedia sebelum perhitungan dapat ditampilkan.

Tujuh port tambahan menggambar melalui Canvas tanpa membuat objek grafis chart. Garis, zona dan teks tetap terikat ke waktu/harga sumber ketika chart digeser atau diperbesar. HPX ZWave tidak memiliki tombol di chart; derajat proyeksi dipilih melalui `InpFibonacciDegree` pada pengaturan indikator.

SMC menyediakan seluruh 52 kontrol input sumber yang dapat diedit, bersama delapan judul bagian pada 60 baris halaman parameter native. Pilihan timeframe FVG mencakup `Current` dan 21 timeframe MT5. Ketika riwayat broker masih dimuat, indikator menunggu dan mencoba lagi tanpa menghapus pemasangannya. SMC tidak mempunyai alert atau notifikasi.

Sejak SMC 1.0.1, isi kotak OB/FVG memakai alpha maksimal 0x26 (sekitar 15% opacity). Warna dan alpha batas serta zona premium/discount dipertahankan. Garis dan teks strong/weak maupun MTF berakhir di candle nyata terakhir, tanpa label 20 bar ke depan atau penempatan mengikuti viewport. APK 6315 memperbaiki cleanup saat surface chart berubah agar callback Layer lama tidak menghapus Layer pengganti.

SMC 1.0.2 menghitung pada worker latar belakang dengan antrean terbatas, menggabungkan permintaan yang menunggu dan memakai kembali hasil ketika data/parameter tidak berubah. Renderer memproyeksikan dan menggambar geometri yang relevan dengan area terlihat, serta memakai cache proyeksi yang mengikuti perubahan sumbu native. Riwayat tidak dipangkas dan aturan sinyal tetap sama. Perbaikan transparansi, jangkar candle asli dan cleanup APK 6315 dipertahankan.

Quarter menandai setiap level utama di skala harga kanan dengan warna levelnya. Jika angka level akan menutup harga berjalan atau terpotong batas chart, hanya tanda garis pada harga tepatnya yang ditampilkan.

Isi kotak OB, breaker dan FVG FiboZone memakai opasitas sekitar 15%, dengan warna batas serta jangkar waktu/harga tetap dipertahankan.

## Paket dan katalog

Setiap entri katalog mencantumkan identitas, versi, ukuran dan SHA-256 paket. Aplikasi memeriksa ukuran, hash dan tanda tangan paket sebelum memasukkannya ke library. Nama berkas unduhan tetap pada folder `modules/`; pembaruan isi paket harus disertai pembaruan metadata katalog.
Perubahan daftar katalog tidak menghapus paket yang sudah tersimpan di library atau pemasangannya pada chart secara otomatis.

Kunci penandatanganan dan kredensial akun tidak disimpan pada repository publik ini.

## Pembaruan APK

Unduh aplikasi custom dari [mtc_versi.apk](https://github.com/handi425/module-mta/releases/latest/download/mtc_versi.apk).
Nama aplikasi tetap **MetaTrader 5**. APK rilis dan [metadata pembaruan](https://github.com/handi425/module-mta/releases/latest/download/mtc_versi.json) tersedia publik; source host dan keystore tetap private.

Versi yang mendukung updater memeriksa GitHub saat aplikasi digunakan, dengan jeda pemeriksaan enam jam. APK baru diunduh dan diverifikasi otomatis; pemasangan tetap memerlukan persetujuan melalui installer Android. Izin memasang dari aplikasi ini diminta melalui pengaturan Android saat pertama kali diperlukan. Pemeriksaan manual tersedia pada **Modul → Update APK**.

Setiap rilis memakai versionCode lebih tinggi, package yang sama, serta sertifikat proyek yang sama. Tidak perlu uninstall. Berkas APK sementara dibersihkan setelah versi baru berjalan.
Pembaruan APK tidak memperbarui paket indikator di library secara otomatis; unduh atau perbarui paket SMC dan Zwave Core terpisah melalui halaman Modul.

## Zwave Core dan sumber datanya

Zwave Core menyediakan seluruh **74 kontrol input** sumber bersama sepuluh judul bagian pada **84 baris parameter native**. Primary menghitung candle tertutup; shadow berlabel `S:` dapat diperbarui pada tick aktif dan hitungan sementara memakai `?`. Panel struktur/shadow opsional, sedangkan status tersedia pada properti indikator. Analisis utama tetap berjalan ketika pembanding masih dimuat atau tidak tersedia.

Candle dan MACD pembanding berasal dari **simbol broker pada akun/server yang sama**, bukan feed TradingView, OANDA atau CME. Preset mencoba nama simbol broker beserta suffix-nya; pilihan Manual tersedia bila pasangan otomatis tidak ditemukan. Jika simbol pembanding belum ada di Market Watch, host dapat menambahkannya untuk berlangganan kuotasi. Riwayat broker dimuat asinkron tanpa membuat chart tersembunyi. Sesi dan OHLC broker dapat berbeda dari source TradingView.

Jangkar otomatis memakai bar bersama termuat pertama dengan ATR sebelumnya yang valid. Jangkar manual memakai bar bersama pertama pada/setelah waktu pilihan. Skala tetap pada jangkar dan tidak dinormalisasi ulang setiap tick. Fibonacci terbaru berakhir pada candle nyata terakhir beserta ekstensi bar yang dipilih. Pemetaan ini mengganti koordinat viewport Pine dengan jangkar waktu/harga tetap sehingga pan/zoom tidak membuat candle atau label mengambang.

Source Pine lengkap, port Java, SDK API 6, fixture dan petunjuk build tersedia pada [`sources/zwave-core-source.zip`](sources/zwave-core-source.zip), dengan [checksum SHA-256](sources/zwave-core-source.zip.sha256). Source Zwave Core oleh **XoRonX | Mr Poleks** dan adaptasinya memakai [Mozilla Public License 2.0](https://mozilla.org/MPL/2.0/); pemberitahuan upstream dipertahankan. Kunci privat dan source host tidak disertakan dalam arsip publik ini.

## Source Smart Money Concepts

Smart Money Concepts [LuxAlgo] berasal dari [publikasi resmi LuxAlgo](https://www.tradingview.com/script/CnB3fSph-Smart-Money-Concepts-SMC-LuxAlgo/), © LuxAlgo. Port Java/Canvas, Pine asli, SDK API 5, pengujian dan petunjuk build tersedia di [`sources/luxalgo-smc-source.zip`](sources/luxalgo-smc-source.zip), dengan checksum pada [berkas SHA-256](sources/luxalgo-smc-source.zip.sha256).

Source dan adaptasi SMC didistribusikan dengan [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) untuk penggunaan nonkomersial. Pertahankan atribusi LuxAlgo, pemberitahuan perubahan dan lisensi yang sama ketika mendistribusikan adaptasi. Port menghapus seluruh alert dan mengganti gambar Pine dengan Canvas; port ini tidak disponsori atau disahkan LuxAlgo. Keystore dan source host privat tidak disertakan dalam ZIP publik.

## Source HPX ZWave

Source HPX ZWave beserta perubahan port, bridge, generator, pengujian native dan
petunjuk build tersedia di [`sources/hpx-zwave-source.zip`](sources/hpx-zwave-source.zip).
Checksum tersedia pada [berkas SHA-256](sources/hpx-zwave-source.zip.sha256).
Notis asli dipertahankan, dan salinan lisensi MPL-2.0 disertakan pada arsip.
Arsip ZWave tetap memuat source SDK API 3 dan skrip build SDK; native payload dan class Java
dapat dibangun tanpa keystore. Kunci privat tidak disertakan dalam arsip ini.
Arsip ini tetap SDK API 3 pada rilis API 6 ini. Paket ZWave API 2 yang
dipublikasikan tetap kompatibel dan payload native tidak berubah.
