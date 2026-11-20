# Panduan Pemasangan: Arsip Pembelian Obat

Untuk petugas yang akan memakai aplikasi di komputer kantor. Tidak perlu keahlian komputer khusus; ikuti langkahnya berurutan.

Versi terbaru: **0.2.0**. Sudah memasang versi 0.1.0? Tidak perlu memasang ulang: lihat [bagian 7](#7-pembaruan-aplikasi).

---

## 1. Yang dibutuhkan

| | |
|---|---|
| Komputer | Windows 10 atau Windows 11, 64-bit |
| Ruang disk | Sekitar 200 MB untuk aplikasi, data dan cadangan |
| Internet | Hanya untuk mengunduh dan memperbarui aplikasi. Pemakaian sehari-hari tidak butuh internet |
| Hak admin | **Tidak perlu.** Aplikasi dipasang untuk akun Windows yang sedang dipakai |
| Flashdisk | Disarankan, khusus untuk cadangan data |

---

## 2. Mengunduh

1. Buka alamat ini di browser:
   **https://github.com/mnooryusuf/arsip-obat-rilis/releases/latest**
2. Di bagian **Assets**, klik file yang namanya berakhiran **`_x64-setup.exe`**, misalnya:
   `Arsip.Pembelian.Obat_0.2.0_x64-setup.exe` (sekitar 4 MB). Angka versinya bisa lebih baru; pilih yang tercantum di halaman itu.
3. Tunggu sampai unduhan selesai. File biasanya tersimpan di folder **Unduhan (Downloads)**.

> Jangan unduh file `.sig` atau `latest.json`. Itu untuk pembaruan otomatis, bukan untuk dipasang.
> File `.msi` hanya untuk pemasangan oleh admin TI.

---

## 3. Memasang

1. Buka folder **Unduhan**, lalu klik dua kali file `..._x64-setup.exe`.
2. **Jika muncul layar biru "Windows protected your PC":**
   Klik tulisan **More info**, lalu tombol **Run anyway**.
   Peringatan ini muncul karena aplikasi belum memiliki sertifikat penerbit berbayar. Aplikasinya sendiri aman: installer ditandatangani untuk pembaruan dan dibangun langsung dari kode sumbernya.
3. Ikuti layar pemasang (dalam bahasa Inggris): klik **Next**, lalu **Install**, lalu **Finish**.
4. Jika komputer belum memiliki komponen **Microsoft Edge WebView2**, pemasang mengunduhnya otomatis. Pastikan internet tersambung saat langkah ini. Windows 10/11 yang rutin diperbarui biasanya sudah memilikinya.

Setelah selesai, aplikasi **Arsip Pembelian Obat** ada di **Start Menu**. Agar mudah dibuka, klik kanan ikonnya lalu pilih **Pin to taskbar**.

---

## 4. Membuka pertama kali

Saat pertama dibuka, aplikasi membuat folder data di:

```
Dokumen\ArsipObat\
├── arsip-obat.db      ← seluruh data pembukuan
└── cadangan\          ← salinan otomatis harian dan bulanan
```

**Jangan memindahkan, mengganti nama, atau menghapus folder ini.** Semua data ada di file `arsip-obat.db`.

Layar pertama adalah **Beranda**, masih kosong.

---

## 5. Mulai memakai

Urutan yang disarankan:

| Langkah | Menu | Keterangan |
|---|---|---|
| 1 | **Impor Excel** | Bila ada rekap lama seperti `DATA OBAT MASUK.xlsx`. Lihat cara lengkapnya di bawah |
| 2 | **Master data → PBF** | Isi **nama singkat** (mis. `KF` untuk Kimia Farma) dan **tempo pembayaran**. Untuk pembelian lewat medref, centang **Pembelian dispensing** |
| 3 | **Faktur baru** | Salin faktur dari kertas (cara lengkap di bawah) |
| 4 | **Pembayaran** | Saat membayar PBF: centang faktur yang dibayar, lalu **Catat pelunasan** |
| 5 | **Riwayat obat** dan **Laporan** | Membandingkan harga, rekap bulanan, utang, dan daftar pembayaran |

Tombol pintas: **Ctrl+S** menyimpan faktur yang sedang diisi.

### Mengisi faktur

1. Pilih **PBF**, isi **No faktur** dan **Tanggal faktur**. Jatuh tempo terisi sendiri dari tempo PBF.
2. Untuk setiap obat: pilih **Obat** (nama seperti di faktur, mis. LIXIANA 60mg), isi **Jumlah**, **Isi** per box, **Harga per box**, dan **Diskon**.
   - Diskon diisi dalam **persen**, sama seperti di faktur PBF (mis. `20` untuk 20%).
   - Bila faktur menulis diskon dalam rupiah, klik tombol **%** di samping kotak diskon sampai berubah menjadi **Rp**.
   - **Pabrik** boleh dikosongkan. Bila pabrik disimpan di Master data → Obat, kotak ini terisi sendiri.
   - Tekan **Enter** di kotak diskon baris terakhir untuk menambah baris obat.
3. Isi **Jumlah tagihan** yang tertulis di faktur. Pita hitung di kanan mencap **COCOK** bila sama, atau **SELISIH** bila berbeda (periksa lagi diskon dan jumlah).
4. **Kena PPN 11%** tercentang otomatis. Untuk pembelian dispensing, centangnya hilang sendiri; nomor faktur boleh dikosongkan dan dibuat otomatis.
5. Klik **Simpan faktur**. Bila hari ini juga dibayar, klik **Bayar sekarang** pada pemberitahuan yang muncul.

Obat atau PBF yang belum ada bisa ditambahkan langsung dari kotak pilihannya: ketik namanya, lalu pilih **Tambah "…"**.

### Mengimpor rekap Excel lama

Aplikasi bisa membaca langsung rekap yang disusun **satu lembar per PBF** seperti `DATA OBAT MASUK.xlsx`.

1. Buka **Impor Excel**, pilih file. Semua lembar yang berisi data otomatis tercentang; **nama lembar dipakai sebagai nama PBF**.
2. **Petakan kolom**: kolom ditebak otomatis untuk setiap lembar. Lembar bertanda ⚠ perlu dicek. Untuk lembar DISPENSING, pilihan *Tanpa PPN* dan *Kolom harga berisi total* sudah tercentang.
3. **Cocokkan nama**: periksa nama yang bertanda *periksa* (ejaan mirip yang akan digabung).
4. **Periksa**: faktur yang rinciannya tidak cocok dengan tagihan diberi peringatan. Faktur tetap diimpor dan bercap SELISIH; cocokkan dengan faktur kertas lalu perbaiki lewat **Ubah**.
5. **Simpan**: semua faktur masuk sekaligus. Faktur yang sudah lunas di Excel (kolom tanggal lunas dan jumlah transfer) langsung tercatat lunas, satu pembayaran untuk setiap transfer.

Baris rincian obat di bawah baris faktur otomatis ikut faktur itu sampai bertemu baris kosong. Baris sisa salinan yang tidak bertanggal dilewati.

### Pengganti file DATA PEMBAYARAN

File rekap pembayaran terpisah tidak perlu diisi lagi. Buka **Laporan → Pembayaran**: isinya sama (tanggal lunas, PBF, jumlah nota, rincian per nota, total transfer) dan bisa diekspor ke Excel atau dicetak.

---

## 6. Cadangan data (penting)

Aplikasi membuat cadangan otomatis setiap hari di `Dokumen\ArsipObat\cadangan`. Tetapi cadangan itu ada di komputer yang sama: jika komputer rusak, cadangannya ikut hilang.

**Minimal sekali seminggu:**

1. Colokkan flashdisk.
2. Buka menu **Cadangan**, klik **Simpan cadangan ke…**
3. Pilih flashdisk, lalu **Save**.

Titik oranye di samping menu **Cadangan** berarti sudah lebih dari 7 hari belum dicadangkan ke flashdisk.

---

## 7. Pembaruan aplikasi

Jika ada versi baru, tombol **"Versi x tersedia · Perbarui"** muncul di bagian bawah menu kiri saat aplikasi dibuka (internet harus tersambung).

1. Klik tombol itu. Daftar perubahan versi baru ditampilkan.
2. Klik **Perbarui sekarang**.
3. Data dicadangkan otomatis, pemasang berjalan, lalu aplikasi terbuka kembali dengan versi baru.

**Dari 0.1.0 ke 0.2.0:** saat versi 0.2.0 pertama kali dibuka, susunan data diperbarui sendiri (untuk diskon persen, PBF dispensing, dan pabrik pada obat). Salinan data sebelum pembaruan disimpan di `Dokumen\ArsipObat\cadangan\sebelum-migrasi-v1_….db`. Data lama tidak berubah isinya.

Pembaruan bisa ditunda dengan **Nanti**. Untuk memeriksa secara manual: **Pengaturan → Periksa pembaruan**. Versi yang terpasang terlihat di bagian bawah menu kiri.

---

## 8. Pindah ke komputer baru

1. Di komputer lama: **Cadangan → Simpan cadangan ke…** flashdisk.
2. Di komputer baru: pasang aplikasi (langkah 2 dan 3).
3. Buka aplikasi, menu **Cadangan → Pilih file cadangan…**, pilih file dari flashdisk, lalu **Ganti dengan cadangan**.

---

## 9. Menghapus aplikasi

**Settings → Apps → Installed apps → Arsip Pembelian Obat → Uninstall.**

Folder data `Dokumen\ArsipObat` **tidak ikut terhapus**. Jika aplikasi dipasang lagi, data lama langsung terbaca kembali.

---

## 10. Jika ada masalah

| Masalah | Yang dilakukan |
|---|---|
| "Windows protected your PC" saat memasang | Klik **More info → Run anyway** (lihat langkah 3) |
| Antivirus memblokir pemasang | Minta admin TI mengizinkan file `..._x64-setup.exe` dari halaman rilis di atas |
| Pemasang macet di "WebView2" | Pastikan internet tersambung, lalu jalankan pemasang sekali lagi |
| Aplikasi menampilkan **"Data tidak bisa dibuka"** | Jangan menghapus apa pun. Catat pesannya, lalu hubungi pengelola aplikasi. Salinan data aman ada di `Dokumen\ArsipObat\cadangan` |
| Tombol pembaruan tidak muncul | Normal jika tidak ada internet atau sudah versi terbaru. Cek di **Pengaturan → Periksa pembaruan** |
| Pembaruan gagal | Data tidak berubah. Coba lagi nanti, atau unduh pemasang versi terbaru dari halaman rilis dan pasang seperti biasa (data tetap aman) |
| Salah memasukkan faktur | Buka faktur → **Ubah**, atau **Batalkan** dengan alasan. Faktur tidak pernah benar-benar dihapus |
| Salah mencatat pelunasan | Menu **Pembayaran** → riwayat pembayaran → **Batalkan** |

Untuk bantuan lain, hubungi pengelola aplikasi di kantor Anda dan sebutkan **versi aplikasi** (terlihat di bagian bawah menu kiri).
