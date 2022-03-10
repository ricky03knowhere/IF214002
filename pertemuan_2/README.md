# Ide Solusi: Sistem Pemesanan Tiket Objek Pariwisata Situ Bagendit 

## Deskripsi
Aplikasi ini dibuat untuk mempermudah pemesanan tiket di objek pariwisata Situ Bagendit. Apliasi ini memiliki fitur-fitur: 
- Melakukan pemesanan tiket
- Melihat jumlah tiket yang tersedia
- Mencatat riwayat pemesanan tiket
- Melakukan pembayaran tiket
- Mencatat riwayat transaksi pembayaran tiket

## Entitas dan Atribut

### user (pemesan)
- id_user
- email
- password
- nama_lengkap
- no_telepon
- kota_asal
- alamat
- photo

### pemesanan
- id_pemesanan
- id_user
- id_pembayaran
- tanggal
- status
- total_harga

### detail_pemesanan
- id_detail_pemesanan
- id_tiket
- id_pemesanan
- id_loket
- jumlah
- total_harga

### pembayaran
- id_pembayaran
- kode_pembayaran
- nama_pembayaran
- jenis_pembayaran

### tiket
- id_tiket
- id_jenis_tiket
- harga

### jenis_tiket
- id_jenis_tiket
- nama

### loket
- id_loket
- nama
- lokasi
