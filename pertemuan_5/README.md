# Ide Solusi: Sistem Pemesanan Tiket Objek Pariwisata Situ Bagendit 

## Changelog
View at [Homepage](https://github.com/ricky03knowhere/IF214002#pertemuan-5)
- ✨ `UPDATE` : Merapikan folder dari pertemuan  sebelumnya
  - Merapikan README.md untuk setiap pertemuan
  - Menambahkan changelog untuk setiap pertemuan
- 🚀 `UPDATE` : Menambahkan deskripsi & fitur-fitur aplikasi
- 🚀 `UPDATE` : Menambahkan keteragan pada entitas
- 🆕 `CREATE` : Membuat pointer dari pertemuan 5

## Pointer
- Entity menjadi nama dari tabel
- Atribute menjadi nama kolom dari tabel
- Candidate key = satu atau lebih kolom unik yang akan dijadikan primary key
- Primary key = satu atau lebih kolom unik yang menjadi id atau penanda dari satu record / row data
- Foreign key = kolom yang digunakan atau diambil dari tabel lain
- Composite key = kolom yang merupakan dua atau lebih primary key
- Query = sebuah cara atau bahasa untuk membuat, mendapatkan dan memanipulasi data
- DDL – Data Definition Language = membuat atau menghapus data/tabel
- DQl – Data Query Language = mengambil data
- DML – Data Manipulation Language = memanipulasi data
- DCL – Data Control Language = menentukan siapa yang dapat mengontrol data

## ERD Crow's Foot  Database
![img 404](./Screenshot%202022-03-18%20092224.png)

## Relationship
|Relationship| ERDish|
|------------|--------|
| user (1 , 1) ----- (0 , N) pemesanan | Each user **may** order **zero or more** pemesanan |
| pemesanan (1 , N) ----- (1 , 1) detail_pemesanan | Each pemesanan **must** have **one and only one** detail_pemesanan |
| pemesanan (1 , 1) ----- (0 , 1) pembayaran | Each pemesanan **may be** paid **zero or one** pembayaran |
| detail_pemesanan (0 , 1) ----- (1 , N) tiket | Each detail_pemesanan **must** have  **one or more** tiket |
| detail_pemesanan (0 , N) ----- (1 , N) loket | Each detail_pemesanan **must** have  **one or more** loket |
| tiket (1 , N) ----- (1 , 1) jenis_tiket | Each tiket **must** have **one and only one** jenis_tiket |
| jenis_tiket (1 , N) ----- (1 , N) objek_wisata | Each jenis_tiket **must** have **one or more** objek_wisata |

## Deskripsi
Aplikasi Pemesanan Tiket Objek Pariwisata Situ Bagendit adalah sebuah aplikasi yang dirancang untuk memenuhi pengunjung objek pariwisata Situ Bagendit yang akan memesanan tiket masuk agar lebih cepat, efektif, dan efisien. Saat pemesanan tiket sedang tinggi, pembelian dan pemesanan tiket dengan cara konvensional menjadi tidak efisien dan efektif karena dapat menimbulkan antrian yang panjang. Dengan demikian, penyelesaian permasalahan ini adalah bagaimana sistem yang baru dapat mengganti sistem yang lama agar tercipta efisiensi waktu dan biaya.

## Fitur-fitur
- Melakukan pemesanan tiket
- Menampilkan harga tiket dan jumlah tiket yang tersedia
- Mencatat dan menampilkan rincian riwayat pemesanan tiket yang dibeli seperti waktu masuk, jumlah tiket, dan lokasi objek wisata yang boleh dikunjungi.
- Melakukan pembayaran tiket dan mencatat riwayat transaksi pembayaran tiket.
- Menampilkan jumlah tiket yang terjual dan hasil penjualan tiket kemudian direkap setiap akhir bulan.


## Entitas dan Atribut

_Note:_  
_\* primary key_  
_\** composite key_

### user (pemesan)
- \* id_user
- \** email
- password
- nama_lengkap
- no_telepon
- kota_asal
- alamat
- photo

### pemesanan
- \* id_pemesanan
- (fk) id_user
- (fk) id_pembayaran
- tanggal
- status
- total_harga

### detail_pemesanan
- \* id_detail_pemesanan
- (fk) id_tiket
- (fk) id_pemesanan
- (fk) id_loket
- jumlah
- total_harga

### pembayaran
- \* id_pembayaran
- \** kode_pembayaran
- nama_pembayaran
- jenis_pembayaran

### tiket
- \* id_tiket
- (fk) id_jenis_tiket
- harga

### jenis_tiket
- \* id_jenis_tiket
- (fk) id_objek_wisata
- nama

### loket
- \* id_loket
- nama
- lokasi

### objek_wisata
- \* id_objek_wisata
- nama
- lokasi
- photo
