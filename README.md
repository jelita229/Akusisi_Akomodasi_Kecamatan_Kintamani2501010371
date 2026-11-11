# Akuisisi Data Akomodasi di Kecamatan Kintamani

1. Identitas Praktikum

  Keterangan 
  Nama | Angelina Florensiana Jelita |
  NIM | 2501010371 |
  Program Studi | Informatika |
  Mata Kuliah | BIFP-243 – Akuisisi dan Manajemen Data |
  Fakultas | Teknologi dan Informatika |
  Institusi | INSTIKI |
  Wilayah Penelitian | Kecamatan Kintamani, Kabupaten Bangli, Bali |
  Tanggal Akuisisi | 11 November 2026 |

2. Deskripsi Proyek

Proyek ini merupakan tugas praktikum Akuisisi dan Manajemen Data yang bertujuan untuk memperoleh data akomodasi di Kecamatan Kintamani, Kabupaten Bangli, Bali.

Proses pengambilan data dilakukan menggunakan Python dengan memanfaatkan OpenStreetMap (OSM) melalui Overpass API.

Data yang diperoleh kemudian disimpan dalam format JSON sebagai data mentah dan diolah menjadi dataset berbentuk CSV. Selanjutnya dilakukan pemeriksaan kualitas data, pemeriksaan koordinat berdasarkan batas wilayah administratif, pemetaan sebaran akomodasi, serta perbandingan jumlah data dengan publikasi Badan Pusat Statistik (BPS).

3. Tujuan Praktikum

  1. Mempraktikkan proses akuisisi data menggunakan Python dan API.
  2. Mengambil data akomodasi berdasarkan batas wilayah Kecamatan Kintamani.
  3. Menyimpan respons mentah sebagai dokumentasi sumber data.
  4. Mengubah data JSON menjadi dataset CSV.
  5. Melakukan pemeriksaan kualitas dan kelengkapan data.
  6. Membandingkan hasil akuisisi dengan data BPS.
  7. Mendokumentasikan sumber data, provenance, dan etika penggunaan data.

4. Sumber Data

Sumber data utama yang digunakan adalah:
OpenStreetMap (OSM)
https://www.openstreetmap.org/
Overpass API 
https://overpass-api.de/api/interpreter

Overpass API digunakan untuk mengambil objek akomodasi berdasarkan tag `tourism` pada wilayah administratif Kecamatan Kintamani.

Jenis akomodasi yang menjadi target pengambilan data:

- Hotel
- Guest House
- Hostel
- Motel
- Apartment
- Chalet

Sumber pembanding:
  Badan Pusat Statistik (BPS) Kabupaten Bangli
  Kecamatan Kintamani Dalam Angka 2024.
  https://banglikab.bps.go.id/id/publication/2024/09/26/3313f5ac27a3df4ff0ecbd03/kecamatan-kintamani-dalam-angka-2024.html
5. Metode Akuisisi Data
  Pengambilan data dilakukan menggunakan Python dengan tahapan berikut:

  1. Menentukan wilayah administratif Kecamatan Kintamani.
  2. Mengidentifikasi batas wilayah menggunakan `admin_level=6`.
  3. Menyusun query Overpass untuk mengambil objek dengan tag akomodasi.
  4. Mengirim permintaan data melalui Overpass API menggunakan library `requests`.
  5. Menerapkan mekanisme retry untuk menangani kegagalan permintaan.
  6. Menyimpan respons API dalam format JSON.
  7. Mengubah data JSON menjadi tabel CSV.
  8. Memeriksa kelengkapan, duplikasi, dan koordinat data.
  9. Membuat visualisasi peta persebaran akomodasi.
  10. Membandingkan hasil akuisisi dengan data BPS.

6. Hasil Akuisisi Data
  Berdasarkan hasil eksekusi notebook, diperoleh sebanyak 32 objek akomodasi dari OpenStreetMap.
  Rincian hasil berdasarkan jenis akomodasi:
  Jenis Akomodasi dan Jumlah:
  Hotel 16 
  Guest House 9 
  Hostel 4 
  Chalet 2 
  Motel 1 
  Total=32
Dataset hasil pengolahan memiliki 32 baris dan 11 kolom, yaitu:
  - `osm_type`
  - `osm_id`
  - `nama`
  - `jenis`
  - `lat`
  - `lon`
  - `desa`
  - `bintang`
  - `jumlah_kamar`
  - `website`
  - `url_osm`
7. Pemeriksaan Kualitas Data
  Pemeriksaan kualitas dilakukan untuk mengetahui kelengkapan dan konsistensi dataset.
  Hasil pemeriksaan berdasarkan notebook:
   Pemeriksaan dan Hasil:
   Total data  32 
   Data duplikat  0 
   Nama kosong  1 
   Koordinat kosong  0 
   Titik di luar batas wilayah  0 
   Atribut desa kosong  32 
   Atribut bintang kosong  31 
   Jumlah kamar kosong  30 
   Website kosong  30 
  Data yang memiliki atribut kosong tetap dipertahankan agar informasi asli dari sumber tidak hilang dan tidak dilakukan pengisian berdasarkan perkiraan.
8. Perbandingan dengan Data BPS
  Perbandingan dilakukan menggunakan angka BPS tahun 2023 yang tercantum dalam notebook:
  - Hotel: 19.
  - Penginapan: 99.
  - Total pembanding: 118.
  - Hasil akuisisi OpenStreetMap: 32 objek.

      Perbandingan aritmetis:

        32 / 118 × 100% = 27,12%.
      Angka tersebut merupakan perbandingan kasar, bukan ukuran kelengkapan data yang setara secara langsung, karena perbedaan kategori dan tahun pengumpulan data.
9. Verifikasi Manual 10 Sampel
  Verifikasi manual dilakukan dengan mengambil 10 sampel akomodasi secara acak dan mencocokkannya dengan sumber informasi yang tersedia.
  Pemeriksaan meliputi:
    - Kesesuaian nama akomodasi.
    - Kesesuaian jenis akomodasi.
    - Kesesuaian lokasi.
    - Pencatatan bukti dan sumber verifikasi.
  Status pengerjaan: Verifikasi masih memerlukan pemeriksaan lanjutan. Berdasarkan catatan notebook, 4 dari 10 sampel memenuhi pemeriksaan kelengkapan catatan sumber. Beberapa sampel masih belum dapat dipastikan lokasi atau identitasnya.
10. Etika dan Lisensi Data
    Pengambilan data memperhatikan prinsip penggunaan data secara bertanggung jawab.
    Beberapa ketentuan yang diterapkan:

  1. Menggunakan sumber data OpenStreetMap melalui Overpass API.
  2. Tidak mengambil informasi kontak pribadi seperti nomor telepon dan email.
  3. Menyimpan respons mentah sebagai dokumentasi.
  4. Mencatat sumber, waktu pengambilan, dan provenance.
  5. Memperhatikan lisensi Open Database License (ODbL).
  6. Tidak menggunakan scraping dari situs OTA atau halaman Google Maps dalam proses akuisisi.
Atribusi sumber data:

© OpenStreetMap contributors
https://www.openstreetmap.org/copyright

11. Struktur Repository
Struktur repository:

```text
Akomodasi_Kintamani_2501010371/
│
├── data/
│   ├── raw/
│   │   └── osm_akomodasi_kintamani.json
│   │
│   └── interim/
│       └── akomodasi_kintamani.csv
│
├── notebooks/
│   └── Akomodasi_Kintamani (2).ipynb
│
├── docs/
│   ├── query_overpass.txt
│   ├── provenance.json
│   ├── data_dictionary.csv
│   ├── data_ethics_checklist.csv
│   └── perbandingan_bps.csv
│
├── reports/
│   └── laporan_akomodasi_kintamani.pdf
│
└── README.md
```

 12. Cara Menjalankan Ulang Notebook
    Untuk menjalankan kembali proses akuisisi data:

    1. Clone atau download repository GitHub.
    2. Pastikan Python dan Jupyter Notebook atau Google Colab tersedia.
    3. Buka folder `notebooks`.
    4. Buka file `Akomodasi_Kintamani (2).ipynb`.
    5. Periksa library yang digunakan pada bagian import notebook dan instal jika belum tersedia.
    6. Jalankan seluruh sel notebook secara berurutan dari awal sampai akhir.
    7. Pastikan koneksi internet tersedia untuk mengakses Overpass API.
    8. Periksa hasil penyimpanan JSON, CSV, dan dokumentasi yang dihasilkan.

  13. Kesimpulan
    Praktikum ini berhasil menerapkan proses akuisisi data akomodasi menggunakan Python dan Overpass API. Sebanyak 32 objek akomodasi berhasil diperoleh dari OpenStreetMap dan diolah menjadi dataset CSV.

    Pemeriksaan kualitas data menunjukkan tidak ditemukan duplikasi dan seluruh koordinat berada di dalam batas wilayah Kintamani. Namun, masih terdapat atribut yang kosong dan proses verifikasi manual yang membutuhkan pemeriksaan lanjutan.

    Hasil praktikum ini diharapkan dapat menjadi dasar untuk memahami proses pengambilan, pengolahan, pemeriksaan, dan dokumentasi data secara sistematis.


© OpenStreetMap contributors – Data tersedia di bawah lisensi Open Database License (ODbL).**
