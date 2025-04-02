Laporan Latihan SQL Injection pada XVWA
📌 Deskripsi
Latihan ini dilakukan untuk memahami serangan SQL Injection menggunakan manual injection pada aplikasi XVWA (Xtreme Vulnerable Web Application).

🔧 Environment Setup
Target: XVWA (Xtreme Vulnerable Web Application)

Metode: Manual SQL Injection

Payload yang Digunakan:

sql
Copy
Edit
' UNION SELECT 1,group_concat(column_name),3,4,5,6,7 from information_schema.columns where table_schema = database() #
Tools:

XVWA di lingkungan XAMPP/LAMP/WAMP

Browser dengan Developer Tools

Burp Suite (opsional untuk intercept request)

🎯 Tujuan
Mengeksploitasi SQL Injection pada XVWA.

Mengambil daftar kolom dalam database saat ini.

Memahami struktur database target.

🏴 Proses Eksploitasi
Identifikasi Formulir Rentan

Mencari form input yang rentan terhadap SQL Injection.

Contoh: Login Form atau Search Bar di XVWA.

Pengujian dengan Payload Sederhana

Input awal: ' OR '1'='1 untuk mengonfirmasi kerentanan.

Penggunaan UNION SELECT untuk Enumerasi Kolom

Input eksploitasi:

sql
Copy
Edit
' UNION SELECT 1,group_concat(column_name),3,4,5,6,7 from information_schema.columns where table_schema = database() #
Hasil Output: List kolom yang ada dalam database saat ini.

Menggunakan Informasi yang Ditemukan

Setelah mendapatkan daftar kolom, eksploitasi dapat dilanjutkan dengan mengekstrak isi tabel.

🛠 Hasil Uji Coba
Berikut hasil eksekusi payload:

plaintext
Copy
Edit
id, username, password, email, created_at
Kolom yang ditemukan menunjukkan struktur tabel yang berisi informasi akun.

🏆 Kesimpulan
XVWA rentan terhadap Union-Based SQL Injection.

Payload berhasil menampilkan daftar kolom dalam database.

SQL Injection masih menjadi ancaman serius bagi aplikasi yang tidak mengimplementasikan keamanan yang baik.

🔐 Rekomendasi Mitigasi
Gunakan Prepared Statements (Parameterized Queries) untuk mencegah SQL Injection.

Batasi hak akses database hanya untuk operasi yang diperlukan.

Implementasikan mekanisme Web Application Firewall (WAF).

Filter dan validasi input pengguna sebelum diteruskan ke database.
