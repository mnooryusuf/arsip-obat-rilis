# Panduan Pemasangan: Arsip Pembelian Obat

Untuk petugas yang akan memakai aplikasi di komputer kantor. Tidak perlu keahlian komputer khusus; ikuti langkahnya berurutan.

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
   `Arsip.Pembelian.Obat_0.1.0_x64-setup.exe` (sekitar 4 MB).
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
| 1 | **Impor Excel** | Hanya jika ada data pembelian lama dalam Excel. Ikuti 5 langkahnya; tidak ada yang tersimpan sampai langkah terakhir |
| 2 | **Master data → PBF** | Periksa atau isi **tempo pembayaran** setiap PBF (misalnya 30 hari). Dipakai untuk menghitung jatuh tempo otomatis |
| 3 | **Faktur baru** | Salin faktur dari kertas. PBF, pabrik dan obat yang belum ada bisa ditambahkan langsung dari kotak pilihannya. Isi **jumlah tagihan** yang tertulis di faktur: pita hitung di kanan akan mencap **COCOK** atau **SELISIH** |
| 4 | **Pembayaran** | Saat membayar PBF: centang faktur yang dibayar, lalu **Catat pelunasan** |
| 5 | **Riwayat obat** dan **Laporan** | Membandingkan harga antar PBF dan pabrik, rekap bulanan, dan utang. Bisa dicetak atau diekspor ke Excel |

Tombol pintas: **Ctrl+S** menyimpan faktur yang sedang diisi.

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
