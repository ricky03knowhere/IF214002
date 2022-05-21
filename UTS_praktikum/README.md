# UTS Praktikum
## Soal
1. Jelaskan contoh-contoh perintah SQL beserta kegunannya !
2. Rancang solusi digital dari satu permasalahan yang ada di sekitar Anda. Berdasarkan ERD yang telah dibuat, buatlah implementasi basis data dari ERD tersebut dalam bentuk tabel basis data lengkap dengan Primary Key, Foreign Key dengan menggunakan perintah CREATE TABLE bahasa SQL. Anda dapat menggunakan vendor basis data yang Anda sukai (MySQL / PostgreSQL / SQL Server / dsb.). Jika belum sempat install basis data di laptop, bisa menggunakan sqliteonline.com untuk mengecek keberhasilan pembuatan tabelnya.

## Jawaban
### 1) Contoh Perintah SQL
- **DDL (Data Definition Language)**
  
  Perintah-perintah untuk membuat atau menghapus data/tabel.
  - `CREATE` : Membuat database, table, index , dll.
  - `SHOW` : Menampilkan semua tabel yang ada dalam database.
  - `ALTER` : Mengubah struktur tabel yang sebelumnya sudah ada.
  - `RENAME` : Mengganti nama database & table.
  - `COMMENT` : Menambahkan komentar.
  - `DROP` : Menghapus database, tabel, index, dll..
  - `TRUNCATE` : Menghapus semua record atau isi dari sebuah tabel.

- **DQL (Data Query Language)**
  
  Perintah untuk mengqueri atau mengambil data dalam database.
  - `SELECT` : Mengambil data dari database.

- **DML (Data Manipulation Language)**
 
  Perintah-perintah untuk memanipulasi data dalam tabel.
  - `INSERT` : Memasukkan / menginputkan data ke dalam tabel.
  - `UPDATE` : Mengupdate / mengubah data dalam tabel dengan data yang baru.
  - `SELECT` : Menampilkan maupun mengambil sebuah data pada tabel.
  - `DELETE` : Menghapus satu record / baris dalam tabel.

- **DCL (Data Control Language)**
  
  Perintah-perintah untuk menentukan siapa yang dapat mengontrol data (hak akses). 
  - `GRANT`: Memberikan hak akses ke user lainnya. 
  - `REVOKE`: Menghapus hak akses seorang pengguna yang awalnya diberikan akses

- **TCL (Transaction Control Language)**
  
  Perintah-perintah untuk menangani transaksi dalam database.
  - `COMMIT` : Menyimpan transaksi secara permanen di database
  - `ROLLBACK` : Mengembalikan database ke bentuk awal / COMMIT terakhir.


### 2) MySQL Sistem Pemesanan Tiket Objek Pariwisata Situ Bagendit

**Membuat Tabel**
```sql
CREATE TABLE `detail_pemesanan` (
  `id_detail_pem` int(8) NOT NULL,
  `id_pemesanan` int(8) NOT NULL,
  `id_tiket` int(8) NOT NULL,
  `id_loket` int(8) NOT NULL,
  `tanggal_wisata` date NOT NULL,
  `jumlah_tiket` int(3) NOT NULL,
  `total_harga` int(8) NOT NULL
);

CREATE TABLE `jenis_pembayaran` (
  `id_jenis_pemb` int(8) NOT NULL,
  `nama_pemb` varchar(24) NOT NULL,
  `metode_pemb` varchar(24) NOT NULL
);

CREATE TABLE `jenis_tiket` (
  `id_jenis_tiket` int(8) NOT NULL,
  `id_obj_wisata` int(8) NOT NULL,
  `nama` varchar(24) NOT NULL,
  `harga` int(8) NOT NULL
);

CREATE TABLE `kode_pos` (
  `kode_pos` int(8) NOT NULL,
  `provinsi` varchar(50) NOT NULL,
  `kota` varchar(50) NOT NULL,
  `kecamatan` varchar(50) NOT NULL,
  `desa` varchar(50) NOT NULL
);

CREATE TABLE `loket` (
  `id_loket` int(8) NOT NULL,
  `nama` varchar(50) NOT NULL,
  `lokasi` varchar(50) NOT NULL
);

CREATE TABLE `objek_wisata` (
  `id_obj_wisata` int(8) NOT NULL,
  `nama` varchar(50) NOT NULL,
  `lokasi` varchar(50) NOT NULL,
  `photo` varchar(256) NOT NULL
);

CREATE TABLE `pembayaran` (
  `id_pembayaran` int(8) NOT NULL,
  `id_jenis_pemb` int(8) NOT NULL,
  `kode_pembayaran` int(8) NOT NULL,
  `tanggal_bayar` date NOT NULL,
  `img_barcode` varchar(256) NOT NULL,
  `status` enum('paid','unpaid','','') NOT NULL
);

CREATE TABLE `pemesanan` (
  `id_pemesanan` int(8) NOT NULL,
  `id_user` int(8) NOT NULL,
  `id_pembayaran` int(8) NOT NULL,
  `tanggal_pesan` date NOT NULL,
  `status` enum('pending','complete','cancelled','') NOT NULL,
  `total_harga` int(8) NOT NULL
);

CREATE TABLE `tiket` (
  `id_tiket` int(8) NOT NULL,
  `id_jenis_tiket` int(8) NOT NULL,
  `stok` int(8) NOT NULL
);

CREATE TABLE `user` (
  `id_user` int(8) NOT NULL,
  `kode_pos` int(8) NOT NULL,
  `email` varchar(50) NOT NULL,
  `password` varchar(256) NOT NULL,
  `is_admin` int(2) NOT NULL,
  `nama_lengkap` varchar(50) NOT NULL,
  `no_telp` varchar(24) NOT NULL,
  `alamat` varchar(256) NOT NULL,
  `photo` varchar(256) NOT NULL
);

```

**Membuat Primary key & Foreign key**
```sql
ALTER TABLE `detail_pemesanan`
  ADD PRIMARY KEY (`id_detail_pem`),
  ADD KEY `id_pemesanan` (`id_pemesanan`),
  ADD KEY `id_tiket` (`id_tiket`),
  ADD KEY `id_loket` (`id_loket`);

ALTER TABLE `jenis_pembayaran`
  ADD PRIMARY KEY (`id_jenis_pemb`);

ALTER TABLE `jenis_tiket`
  ADD PRIMARY KEY (`id_jenis_tiket`),
  ADD KEY `id_obj_wisata` (`id_obj_wisata`);

ALTER TABLE `kode_pos`
  ADD PRIMARY KEY (`kode_pos`);

ALTER TABLE `loket`
  ADD PRIMARY KEY (`id_loket`);

ALTER TABLE `objek_wisata`
  ADD PRIMARY KEY (`id_obj_wisata`);

ALTER TABLE `pembayaran`
  ADD PRIMARY KEY (`id_pembayaran`),
  ADD UNIQUE KEY `kode_pembayaran` (`kode_pembayaran`),
  ADD UNIQUE KEY `img_barcode` (`img_barcode`),
  ADD KEY `id_jenis_pemb` (`id_jenis_pemb`);

ALTER TABLE `pemesanan`
  ADD PRIMARY KEY (`id_pemesanan`),
  ADD KEY `id_user` (`id_user`),
  ADD KEY `id_pembayaran` (`id_pembayaran`);

ALTER TABLE `tiket`
  ADD PRIMARY KEY (`id_tiket`),
  ADD KEY `id_jenis_tiket` (`id_jenis_tiket`);

ALTER TABLE `user`
  ADD PRIMARY KEY (`id_user`),
  ADD UNIQUE KEY `email` (`email`),
  ADD KEY `kode_pos` (`kode_pos`);

```

**Membuat Relasi antar Tabel**
```sql
ALTER TABLE `detail_pemesanan`
  ADD CONSTRAINT `detail_pemesanan_ibfk_1` FOREIGN KEY (`id_pemesanan`) REFERENCES `pemesanan` (`id_pemesanan`),
  ADD CONSTRAINT `detail_pemesanan_ibfk_2` FOREIGN KEY (`id_tiket`) REFERENCES `tiket` (`id_tiket`),
  ADD CONSTRAINT `detail_pemesanan_ibfk_3` FOREIGN KEY (`id_loket`) REFERENCES `loket` (`id_loket`);

ALTER TABLE `jenis_tiket`
  ADD CONSTRAINT `jenis_tiket_ibfk_1` FOREIGN KEY (`id_obj_wisata`) REFERENCES `objek_wisata` (`id_obj_wisata`);

ALTER TABLE `pembayaran`
  ADD CONSTRAINT `pembayaran_ibfk_1` FOREIGN KEY (`id_jenis_pemb`) REFERENCES `jenis_pembayaran` (`id_jenis_pemb`);

ALTER TABLE `pemesanan`
  ADD CONSTRAINT `pemesanan_ibfk_1` FOREIGN KEY (`id_user`) REFERENCES `user` (`id_user`),
  ADD CONSTRAINT `pemesanan_ibfk_2` FOREIGN KEY (`id_pembayaran`) REFERENCES `pembayaran` (`id_pembayaran`);

ALTER TABLE `tiket`
  ADD CONSTRAINT `tiket_ibfk_1` FOREIGN KEY (`id_jenis_tiket`) REFERENCES `jenis_tiket` (`id_jenis_tiket`);

ALTER TABLE `user`
  ADD CONSTRAINT `user_ibfk_1` FOREIGN KEY (`kode_pos`) REFERENCES `kode_pos` (`kode_pos`);
COMMIT;

```