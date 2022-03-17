# Ide Solusi: Sistem Pemesanan Tiket Objek Pariwisata Situ Bagendit 

## ERD Rancangan Database
![img](./Screenshot%202022-03-11%20095917.png)

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
- \* email
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
- \* kode_pembayaran
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

## ERD Crow's Foot  Database
![img 404](./)
