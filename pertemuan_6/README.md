# Ide Solusi: Sistem Pemesanan Tiket Objek Pariwisata Situ Bagendit 

## Changelog
View at [Homepage](https://github.com/ricky03knowhere/IF214002#pertemuan-6)
- ✅ `CREATE` : Mengerjakan Assessment
- 🚀 `UPDATE` : Normalisasi tabel
  - Menambahkan tebel *kode_pos*, supaya alamat user lebih lengkap
  - Menambahkan tebel *jenis_pembayaran*
  - Menambahkan atribut *is_admin* pada tabel *users*
  - Menambahkan atribut *stok* pada tabel *tiket*
  - Memindahkan  atribut *harga* dari tabel *tiket* ke tabel *jenis_tiket*
  - Menambahkan atribut *tanggal_wisata* pada tabel *detail_pesanan*
  - Menambahkan atribut *tanggal_bayar*, *img_barcode* & *status*  pada tabel *pembayaran*
  
- 🚀 `UPDATE` : Menambahkan relasi baru pada ERDish

## Assessment
### 1) Penyuaian dengan Proses Bisnis
  - Setelah dianalisis lebih lanjut, supaya struktur basis data sesuai dengan proses bisnis maka struktur basis data project harus dinormalisasi terlebih dahulu.

### 2) Normalisasi Tabel

  - 🎖️ Normalisasi bentuk ke-1
    - Semua tabel telah memiliki primary key (1 kolom, atau multi kolom(composite)).
    - Semua tabel tidak memiliki sel yang berisi nilai lebih dari satu.

  - 🎖️ Normalisasi bentuk ke-2
    - Semua tabel telah tersertifikasi Normalisasi Bentuk ke 1
    - Semua tabel tidak memiliki kolom non key yang bergantung sebagian dari composite key

  - 🎖️ Normalisasi bentuk ke-3
    - Semua tabel telah tersertifikasi Normalisasi Bentuk ke 2
    - Pembuatan tabel baru :
      - Menambahkan tebel *kode_pos* yang merupakan extend dari tabel user, supaya alamat user lebih lengkap
      - Menambahkan tebel *jenis_pembayaran* yang merupakan extend dari tabel pembayaran, supaya pembayaran dapat dilakukan melalui berbagai jenis pembayaran

</details>

## ERD Crow's Foot  Database
Setelah Normalisasi

![img 404](./Screenshot%202022-04-08%20102450.png)
<details>
  <summary>Sebelum Normalisasi</summary>

![img 404](./Screenshot%202022-03-18%20092224.png)
</details>



## Relationship
|Relationship| ERDish|
|------------|--------|
| user (1 , 1) ----- (0 , N) pemesanan | Each user **may** order **zero or more** pemesanan |
| kode_pos (1 , 1) ----- (0 , N) user | Each kode_pos **may** have **zero or more** user |
| pemesanan (1 , N) ----- (1 , 1) detail_pemesanan | Each pemesanan **must** have **one and only one** detail_pemesanan |
| pemesanan (1 , 1) ----- (0 , 1) pembayaran | Each pemesanan **may be** paid **zero or one** pembayaran |
| detail_pemesanan (0 , 1) ----- (1 , N) tiket | Each detail_pemesanan **must** have  **one or more** tiket |
| detail_pemesanan (0 , N) ----- (1 , N) loket | Each detail_pemesanan **must** have  **one or more** loket |
| tiket (1 , N) ----- (1 , 1) jenis_tiket | Each tiket **must** have **one and only one** jenis_tiket |
| jenis_tiket (1 , N) ----- (1 , N) objek_wisata | Each jenis_tiket **must** have **one or more** objek_wisata |
| jenis_pembayaran (1 , 1) ----- (0 , N) pembayaran | Each jenis_pembayaran **may** have **zero or more** pembayaran |

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

### user (pemesan / admin)
- \* id_user
- \** email
- (fk) kode_pos
- password
- is_admin
- nama_lengkap
- no_telepon
- alamat
- photo

### kode_pos
- \* kode_pos
- provinsi
- kota
- kecamatan
- desa

### pemesanan
- \* id_pemesanan
- (fk) id_user
- (fk) id_pembayaran
- tanggal_pesan
- status
- total_harga

### detail_pemesanan
- \* id_detail_pem
- (fk) id_pemesanan
- (fk) id_tiket
- (fk) id_loket
- tanggal_wisata
- jumlah_tiket
- total_harga

### pembayaran
- \* id_pembayaran
- \** kode_pembayaran
- (fk) id_jenis_pemb
- tanggal_bayar
- img_barcode
- status

### jenis_pembayaran
- \* id_jenis_pemb
- nama_pembayaran
- metode_pembayaran

### tiket
- \* id_tiket
- (fk) id_jenis_tiket
- stok

### jenis_tiket
- \* id_jenis_tiket
- (fk) id_objek_wisata
- nama
- harga

### loket
- \* id_loket
- nama
- lokasi

### objek_wisata
- \* id_objek_wisata
- nama
- lokasi
- photo
