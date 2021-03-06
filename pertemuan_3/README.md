# Ide Solusi: Sistem Pemesanan Tiket Objek Pariwisata Situ Bagendit 

## Changelog
View at [Homepage](https://github.com/ricky03knowhere/IF214002#pertemuan-3)
- 🚀 `UPDATE` : Menambahkan Primary key, Composite key & Foreign key dari setiap Entitas / Tabel
- 🚀 `UPDATE` : Mengubah ERD Conceptual menjadi ERD Logical
- 🆕 `CREATE` : Membuat ERD Crow's Foot Database

## ERD Crow's Foot  Database
![img 404](./Screenshot%202022-03-18%20092224.png)

## Deskripsi
Aplikasi ini dibuat untuk mempermudah pemesanan tiket di objek pariwisata Situ Bagendit. Apliasi ini memiliki fitur-fitur: 
- Melakukan pemesanan tiket
- Melihat jumlah tiket yang tersedia
- Mencatat riwayat pemesanan tiket
- Melakukan pembayaran tiket
- Mencatat riwayat transaksi pembayaran tiket

## Entitas dan Atribut

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