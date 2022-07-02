# UTS

## Soal
1. Basis data relasional dapat langsung dibangun menggunakan perintah SQL di sistem basis data seperti MySQL, dsb tanpa ada perancangan terlebih dahulu. 
  
    Jelaskan apa keuntungan melakukan perancangan basis data terlebih dahulu (menggunakan ERD ataupun Class Diagram) !

2. Jelaskan bagaimana cara mentransformasikan proses bisnis sebuah organisasi menjadi struktur data di basis data !

3. Rancang solusi digital dari satu permasalahan yang ada di sekitar Anda. 

    A. Deskripsikan solusi digital tersebut dalam satu paragraf
    
    B. Buat list fitur-fitur yang ada pada solusi digital tersebut
    
    C. Buat ERD notasi Chen dari struktur data yang mewakili fitur2 di solusi digital tersebut
    
    D. Buat ERD notasi Crow Foot dari struktur data logical yang mewakili fitur2 di solusi digital tersebut, lengkap dengan keys, tipe data, dan normalisasi hingga bentuk ke 3

## Jawaban

## 1) Keuntungan merancang basis data menggunakan ERD atau Class Diagram
### Keuntungan menggunakan ERD
- Membantu menganalisis suatu database dengan cara yang lebih cepat dan juga lebih murah.
- Mampu menjalankan relasi antar setiap data yang mempunyai keterkaitan dengan berdasarkan objek yang dihubungkan dengan suatu relasi khusus.
- Membantu menjalankan dokumentasi data yang terdapat dalam suatu database dengan cara melakukan analisis dan identifikasi pada setiap objek ataupun entitas serta relasinya.
- Melakukan suatu pengujian model yang sebelumnya sudah dibuat.

### Keuntungan menggunakan Class Diagram
- Mampu mengilustrasikan model data untuk sistem informasi, terlepas dari apakah model data tersebut rumit atau sederhana.
- Memberikan gambaran umum mengenai skema aplikasi dengan lebih baik.
- Membantumu menyampaikan secara visual kebutuhan spesifik apa pun dari suatu sistem dan menyebarkan informasi tersebut ke bisnis.
- Terdapat bagan terperinci yang menyoroti kode spesifik yang perlu diprogram dan diterapkan ke struktur yang sesuai.
- Menyediakan deskripsi implementasi independen dari tipe yang digunakan dalam sistem untuk kemudian diteruskan di antara komponen-komponennya.

## 2) Cara mentransformasikan proses bisnis menjadi struktur data

1. Analisa Kebutuhan dan Pengumpulan Data
    - Menentukan siapa yang akan memakai dan batas-batas bagaimana aplikasi akan bekerja
    - Melakukan pengumpulan informasi dari dokumentasi yang pernah ada
    - Menganalisa proses di organisasi dan bagaimana data akan di proses
    - Membuat daftar pertanyaan dan melakukan wawancara
    - Mendeskripsikan ide solusi bisis & fitur-fitur dari aplikasi

2. Perancangan basis data secara Konseptual
    - Merancang/mengkonsep bagaimana database akan dibuat
    - Membuat skema alur database, Menentukan entitas & atribut dari aplikasi, perancangan alur transaksi yang nantinya akan dilakukan di database. (Pembuatan Flowchart atau ERD)

3. Perancangan Database secara Logical
    - Pemetaan (Transformasi data)
      Pemetaan ke dalam model data DBMS dengan tidak mempertimbangkan karakteristik atau hal-hal yang khusus yang berlaku pada implementasi DBMS dari model data tsb.
    - Penyesuaian Skema ke DBMS
      Mengatur skema yang dihasilkan dari tahap Pemetaan untuk disesuaikan pada implementasi yang khusus di masa yang akan datang dari suatu model data yang digunakan pada DBMS yang dipilih.
    - Menambahkan Primary key, Composite key & Foreign key dari setiap Entitas / Tabel dan menambahkan tipe data untuk setiap atribut.
    - Menambahkan cardinality dan optionality untuk setiap Entitas / Tabel dan menerapkan aturan normalisasi.   
4. Perancangan Database secara Fisikal
    
    Beberapa hal yang bisa dipertimbangkan dalam pemilihan perancangan basis data secara fisik :
    - Response time, waktu akses basis data untuk data item yang ditunjuk oleh suatu transaksi.
    -Space utility, jumlah ruang penyimpanan yang digunakan oleh file-file basis data dan struktur jalur akses.
    - Transaction throughput, rata-rata jumlah transaksi yang dapat diproses per menit oleh sistem basis data dan merupakan parameter kritis dari sistem transaksi (misal : digunakan pada pemesanan tempat di pesawat, bank, dll).

5. Pemilihan DBMS
    
    Beberapa faktor yang bisa dijadikan pertimbangan saat memilih DBMS :
    - Faktor Teknik
      Keberadaan DBMS dalam menjalankan tugasnya seperti jenis-jenis DBMS (relational, network, hierarchical), struktur penyimpanan, dan jalur akses yang mendukung DBMS, pemakai, dll.
    - Faktor Ekonomi dan Organisasi
      Struktur Data, personal yang telah terbiasa menggunakan sistem (programmer), dan tersedianya layananan purna jual.

6. Implementasi
    Setelah menganalisa permasalahan, mengkonsep proses bisnis, mendesain database, yang terakhir adalah menggabungkan atau mengimplementasikan database yang telah dirancang untuk kemudian mulai dibentuk sebuah aplikasi (dilakukan oleh programmer). Selesainya proses implementasi ini adalah apabila sebuah aplikasi telah selesai dan bisa memproses data sesuai dengan konsep.



## 3 ) Ide Solusi: Sistem Pemesanan Tiket Objek Pariwisata Situ Bagendit 

## ERD Rancangan Database
![plot](./Screenshot%202022-03-11%20095917.png)
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
