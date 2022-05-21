# Pertemuan 11

## Changelog
View at [Homepage](https://github.com/ricky03knowhere/IF214002#pertemuan-11)
- ✅ CREATE : Mengerjakan Assesment
  
## Assesment
Buat DDL, sampel DML, dan DQL untuk proyek besar teman-teman
  - Contoh DDL : CREATE TABLE santri ( . . . ), dsb.
  - Contoh DML : INSERT INTO santri ( . . . ) VALUES ( . . . ), dsb.
  - Contoh DQL :
      - Santri dengan setoran hafalan terbanyak : SELECT nama FROM santri INNER JOIN . . .
      - Agregat pemasukan kencleng per bulan tahun 2022 : SELECT bulan, pemasukan FROM . . . INNER JOIN . . .

## Jawab

### DDL (Data Definition Language) 

**Membuat Tabel**
```sql
CREATE TABLE detail_pemesanan (
  id_detail_pem int(8) NOT NULL,
  id_pemesanan int(8) NOT NULL,
  id_tiket int(8) NOT NULL,
  id_loket int(8) NOT NULL,
  tanggal_wisata date NOT NULL,
  jumlah_tiket int(3) NOT NULL,
  total_harga int(8) NOT NULL
);

CREATE TABLE jenis_pembayaran (
  id_jenis_pemb int(8) NOT NULL,
  nama_pemb varchar(24) NOT NULL,
  metode_pemb varchar(24) NOT NULL
);

CREATE TABLE jenis_tiket (
  id_jenis_tiket int(8) NOT NULL,
  id_obj_wisata int(8) NOT NULL,
  nama varchar(24) NOT NULL,
  harga int(8) NOT NULL
);

CREATE TABLE kode_pos (
  kode_pos int(8) NOT NULL,
  provinsi varchar(50) NOT NULL,
  kota varchar(50) NOT NULL,
  kecamatan varchar(50) NOT NULL,
  desa varchar(50) NOT NULL
);

CREATE TABLE loket (
  id_loket int(8) NOT NULL,
  nama varchar(50) NOT NULL,
  lokasi varchar(50) NOT NULL
);

CREATE TABLE objek_wisata (
  id_obj_wisata int(8) NOT NULL,
  nama varchar(50) NOT NULL,
  lokasi varchar(50) NOT NULL,
  photo varchar(256) NOT NULL
);

CREATE TABLE pembayaran (
  id_pembayaran int(8) NOT NULL,
  id_jenis_pemb int(8) NOT NULL,
  kode_pembayaran int(8) NOT NULL,
  tanggal_bayar date NOT NULL,
  img_barcode varchar(256) NOT NULL,
  status enum('paid','unpaid','','') NOT NULL
);

CREATE TABLE pemesanan (
  id_pemesanan int(8) NOT NULL,
  id_user int(8) NOT NULL,
  id_pembayaran int(8) NOT NULL,
  tanggal_pesan date NOT NULL,
  status enum('pending','complete','cancelled','') NOT NULL,
  total_harga int(8) NOT NULL
);

CREATE TABLE tiket (
  id_tiket int(8) NOT NULL,
  id_jenis_tiket int(8) NOT NULL,
  stok int(8) NOT NULL
);

CREATE TABLE user (
  id_user int(8) NOT NULL,
  kode_pos int(8) NOT NULL,
  email varchar(50) NOT NULL,
  password varchar(256) NOT NULL,
  is_admin int(2) NOT NULL,
  nama_lengkap varchar(50) NOT NULL,
  no_telp varchar(24) NOT NULL,
  alamat varchar(256) NOT NULL,
  photo varchar(256) NOT NULL
);

```

**Membuat Primary key & Foreign key**
```sql
ALTER TABLE detail_pemesanan
  ADD PRIMARY KEY (id_detail_pem),
  ADD KEY id_pemesanan (id_pemesanan),
  ADD KEY id_tiket (id_tiket),
  ADD KEY id_loket (id_loket);

ALTER TABLE jenis_pembayaran
  ADD PRIMARY KEY (id_jenis_pemb);

ALTER TABLE jenis_tiket
  ADD PRIMARY KEY (id_jenis_tiket),
  ADD KEY id_obj_wisata (id_obj_wisata);

ALTER TABLE kode_pos
  ADD PRIMARY KEY (kode_pos);

ALTER TABLE loket
  ADD PRIMARY KEY (id_loket);

ALTER TABLE objek_wisata
  ADD PRIMARY KEY (id_obj_wisata);

ALTER TABLE pembayaran
  ADD PRIMARY KEY (id_pembayaran),
  ADD UNIQUE KEY kode_pembayaran (kode_pembayaran),
  ADD UNIQUE KEY img_barcode (img_barcode),
  ADD KEY id_jenis_pemb (id_jenis_pemb);

ALTER TABLE pemesanan
  ADD PRIMARY KEY (id_pemesanan),
  ADD KEY id_user (id_user),
  ADD KEY id_pembayaran (id_pembayaran);

ALTER TABLE tiket
  ADD PRIMARY KEY (id_tiket),
  ADD KEY id_jenis_tiket (id_jenis_tiket);

ALTER TABLE user
  ADD PRIMARY KEY (id_user),
  ADD UNIQUE KEY email (email),
  ADD KEY kode_pos (kode_pos);

```

**Membuat Relasi antar Tabel**
```sql
ALTER TABLE detail_pemesanan
  ADD CONSTRAINT detail_pemesanan_ibfk_1 FOREIGN KEY (id_pemesanan) REFERENCES pemesanan (id_pemesanan),
  ADD CONSTRAINT detail_pemesanan_ibfk_2 FOREIGN KEY (id_tiket) REFERENCES tiket (id_tiket),
  ADD CONSTRAINT detail_pemesanan_ibfk_3 FOREIGN KEY (id_loket) REFERENCES loket (id_loket);

ALTER TABLE jenis_tiket
  ADD CONSTRAINT jenis_tiket_ibfk_1 FOREIGN KEY (id_obj_wisata) REFERENCES objek_wisata (id_obj_wisata);

ALTER TABLE pembayaran
  ADD CONSTRAINT pembayaran_ibfk_1 FOREIGN KEY (id_jenis_pemb) REFERENCES jenis_pembayaran (id_jenis_pemb);

ALTER TABLE pemesanan
  ADD CONSTRAINT pemesanan_ibfk_1 FOREIGN KEY (id_user) REFERENCES user (id_user),
  ADD CONSTRAINT pemesanan_ibfk_2 FOREIGN KEY (id_pembayaran) REFERENCES pembayaran (id_pembayaran);

ALTER TABLE tiket
  ADD CONSTRAINT tiket_ibfk_1 FOREIGN KEY (id_jenis_tiket) REFERENCES jenis_tiket (id_jenis_tiket);

ALTER TABLE user
  ADD CONSTRAINT user_ibfk_1 FOREIGN KEY (kode_pos) REFERENCES kode_pos (kode_pos);
COMMIT;

```

### DML (Data Manipulation Language) 
**Insert Data pada setiap Tabel**

```sql
INSERT INTO kode_pos (kode_pos, provinsi, kota, kecamatan, desa) VALUES ('41234', 'Jawa Barat', 'Garut', 'Leuwigoong', 'Margahayu');

INSERT INTO user (id_user, kode_pos, email, password, is_admin, nama_lengkap, no_telp, alamat, photo) VALUES ('421345', '41234', 'Devin.Heidenreich@yahoo.co.id', '$2b$10$rsMC2KHm/XXVctodbUUNhubNL0D105tIOxlP889tr81DdtdUj/2JO', '1', 'Tasnim Budiman', '(+62) 973 1979 237', 'Bartoletti Flats no 8 Apt. 468', 'tasmin.jpg');

INSERT INTO objek_wisata (id_obj_wisata, nama, lokasi, photo) VALUES ('002', 'kantin bagendit', 'East', 'kantin.jpg');

INSERT INTO jenis_tiket (id_jenis_tiket, id_obj_wisata, nama, harga) VALUES ('1', '2', 'Dewasa', '80000');

INSERT INTO tiket (id_tiket, id_jenis_tiket, stok) VALUES ('142983912', '1', '423');

INSERT INTO jenis_pembayaran (id_jenis_pemb, nama_pemb, metode_pemb) VALUES ('1', 'dana', 'e-wallet');

INSERT INTO pembayaran (id_pembayaran, id_jenis_pemb, kode_pembayaran, tanggal_bayar, img_barcode, status) VALUES ('21432', '1', '132', '2022-05-19', '23uediuwe8y8dweyeqad43ew.jpg', 'unpaid');

INSERT INTO loket (id_loket, nama, lokasi) VALUES ('002', 'loket-02', 'Crystal Camp no 5 Apt. 530');

INSERT INTO pemesanan (id_pemesanan, id_user, id_pembayaran, tanggal_pesan, status, total_harga) VALUES ('6897679', '421345', '21432', '2022-05-02', 'pending', '80000');

INSERT INTO detail_pemesanan (id_detail_pem, id_pemesanan, id_tiket, id_loket, tanggal_wisata, jumlah_tiket, total_harga) VALUES ('92349234', '6897679', '142983912', '2', '2022-05-31', '3', '160000');

```

### DQL (Data Query Language)
- Mencari wilayah / kota dengan pengunjung terbanyak
  ```sql
  SELECT tb.kota, MAX(tb.pengunjung) FROM (SELECT kp.kota AS kota, COUNT(*) AS pengunjung FROM user u INNER JOIN kode_pos kp ON u.kode_pos = kp.kode_pos GROUP BY kode_pos) AS tb
  ```

- Agregat pemasukan penjualan tiket perbulan
  ```sql
  SELECT date_format(tanggal_pesan, "%Y - %M") AS bulan, SUM(total_harga) AS total FROM pemesanan GROUP BY month(tanggal_pesan) 
  ```

- Agregat objek wisata terfavorit (pengunjung terbanyak)
  ```sql
  SELECT id_obj_wisata, COUNT(id_obj_wisata) as pengunjung FROM jenis_tiket GROUP by id_obj_wisata ORDER BY pengunjung DESC 
  ```
