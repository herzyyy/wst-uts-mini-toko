# Laporan UTS Web Software Tools

**Nama: Helmi Rizki Pauzi**
**Nomor Induk Mahasiswa: 12523010**
**Kelas: A**
**Tanggal: 11 November 2026**

## A. Bukti pemeriksaan masalah
| Masalah | Alat yang digunakan | Bukti pemeriksaan | Perkiraan penyebab | Perbaikan | Hasil setelah perbaikan |
|---|---|---|---|---|---|
| Daftar produk | Network, Console, Elements | `GET /api/barang` menghasilkan 404; Console mencatat status 404 dan halaman menampilkan “Gagal memuat produk”. | URL API di aplikasi berbeda dari endpoint server. | Ganti URL menjadi `/api/products`. | 4 produk tampil dan status menunjukkan “4 produk tersedia”. |
| Tombol keranjang | Elements, Sources, uji klik browser | Tombol memakai kelas `.add-button`, tetapi kode memasang event pada `.add-to-cart`; klik tidak mengubah keranjang. | Selector event tidak cocok dengan kelas tombol. | Gunakan selector `.add-button`. | Klik tombol menambahkan produk dan memperbarui jumlah keranjang. |
| Total belanja | Tes otomatis, Sources, uji browser | Sebelum perbaikan, 2 unit seharga Rp75.000 menghasilkan Rp75.000, bukan Rp150.000. | Fungsi total hanya menjumlahkan harga satuan. | Hitung `harga × jumlah` untuk setiap produk. | 2 unit menghasilkan Rp150.000; semua tes keranjang lulus. |

## B. Hasil pengujian
- Jumlah pengujian sebelum perbaikan: 7, dengan 5 lulus dan 2 gagal.
- Jumlah pengujian berhasil setelah perbaikan: 7 dari 7.
- Catatan perubahan pada fungsi yang diperiksa: daftar produk memakai endpoint yang benar, tombol memiliki event klik, dan total memperhitungkan kuantitas.

## C. Kualitas kode
- Temuan sebelum perbaikan: lint memberi peringatan variabel `discount` yang tidak digunakan; format check dan quality check gagal.
- Perbaikan yang dilakukan: hapus variabel tidak terpakai dan format berkas dengan Biome.
- Hasil pemeriksaan ulang: `npm run lint`, `npm run format:check`, dan `npm run quality:check` lulus.

## D. Git
- Branch: `fix/daftar-produk`, `fix/tombol-keranjang`, `fix/total-belanja`, `fix/lint-check`, `fix/format-check`, dan `fix/quality-check` (aktif).
- Ringkasan commit: `7fd2818` produk; `155eb35` tombol; `4d68b9c` total; `d0148f9` lint; `d0e7dec` format.
- Hasil pemeriksaan `git status`: bersih; branch aktif tersinkron dengan `origin/fix/quality-check`.

## E. Pemakaian kecerdasan buatan (jika digunakan)
- Nama alat: GitHub Copilot.
- Pertanyaan/instruksi yang diberikan: identifikasi tiga masalah aplikasi serta temuan lint dan format yang ada.
- Bagian jawaban yang diterapkan: perbaikan endpoint produk, selector tombol, perhitungan total, variabel tak terpakai, dan format kode.
- Cara memeriksa apakah saran tersebut benar: tes otomatis, pemeriksaan Biome, dan uji tampilan serta klik di browser secara langsung.

## F. Refleksi singkat
- Satu pelajaran paling penting dari ujian ini: gunakan tes dan pemeriksaan browser untuk membuktikan perilaku; formatter saja tidak memperbaiki kesalahan logika.
