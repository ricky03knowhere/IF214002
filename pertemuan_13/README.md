# Pertemuan 13
## Changelog
View at [Homepage](https://github.com/ricky03knowhere/IF214002#pertemuan-13)
- 🚀 `UPDATE` : Memaparkan transaction dalam database
- 🚀 `UPDATE` : Memaparkan software requirement final project

## Transaction
### Outline
- Definisi
- Alur kerja
  - Begin
  - Commit
  - Rollback
  - Savepoint
  - End
- Properti ACID
  - Atomicity
  - Consistency
  - Isolation
  - Durability

### Definisi
- rangkaian lebih dari satu perintah database
- yang dihitung sebagai satu unit proses kerja
- memenuhi sifat ACID
  - atomic : seluruh perintah berhasil, atau tidak sama sekali
  - consistency : transaksi tidak mengganggu integritas data di database
  - isolation : pemisahan urutan eksekusi antar transaksi yang berjalan hampir bersamaan
  - durability : jika seluruh operasi transaksi telah berhasil, data tersimpan permanen di disk

## Final Project
### Tools
- Basis Data & DDL DML nya
  - MySQL
  - PostgreSQL
- DB Explorer
  - DBeaver
- Backend / Web Service Bahasa Pemrograman
  - Java
  - NodeJS [installer](https://nodejs.org/dist/v16.15.1/node-v16.15.1-x64.msi)
  - Dart
  - Python [installer](https://www.python.org/ftp/python/3.9.13/python-3.9.13-amd64.exe)
  - PHP
    - [Contoh file web service php](https://github.com/insanalamin/IF214002/blob/main/final-project/contoh-webservice.php)
    - php -S localhost:8123 contoh-webservice.php
  - Go
  - Rust
  - Ruby
  - dll
- Frontend / Desktop / Mobile / Web
  - Mobile: Flutter - Dart
  - Mobile: Ionic - Javascript
  - Web: React JS / TS - Javascript / Typescript
  - Web: HTML Javascript
    - [HTML5 boilerplate](https://www.sitepoint.com/a-basic-html5-template/)
    - [Contoh visualisasi data ChartJS](https://github.com/insanalamin/IF214002/blob/main/final-project/contoh-visualisasi-chartjs.html)
  - Web: Vue JS
- Visualisasi data
  - Ngikut frontend
  - Apache Superset
  - Metabase
- Terminal
  - Windows
    cd : pindah direktori
    mkdir : buat direktori
    dir : melihat isi direktori