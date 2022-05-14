# Pertemuan 10

## Changelog
View at [Homepage](https://github.com/ricky03knowhere/IF214002#pertemuan-10)
- ✅ `CREATE` : Mengerjakan Tugas
  
## Tugas
### Soal
- Buat infografik / cheatsheet dari perintah-perintah MySQL di atas (boleh yang mau pake PostgreSQL)
- Buat query untuk mencari penduduk berusia diatas 25 tahun yang berada di kabupaten 3204 dari data ini
- Nilai tambah, untuk yang menambahkan perintah-perintah MySQL lainnya

### Jawab
- PostgreSQL Cheatsheets
![img](./PostgreSql%20Cheatsheet.png)

- Query untuk mencari penduduk berusia diatas 25 tahun yang berada di kabupaten 3204

  ```sql
  SELECT *, TIMESTAMPDIFF(YEAR, tanggal_lahir, now()) as usia from penduduk WHERE (TIMESTAMPDIFF(YEAR, tanggal_lahir, now()) > 25) && (kode_kabupaten = 3204);
  ```

  ![img](./Screenshot%20(188).png)