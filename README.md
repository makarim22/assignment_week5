# assignment_week5

Mendesain Database dalam Bentuk Normal Ketiga (3NF) untuk Field yang Disediakan
 1. Identifikasi Entitas dan Relasi:
    Berdasarkan field yang diberikan, kita dapat mengidentifikasi tiga entitas utama:
    Transaksi: Mewakili satu transaksi tunggal dengan detail seperti step, amount, fraud, dll.
    Pelanggan: Mewakili pelanggan yang terlibat dalam transaksi dengan detail seperti usia, jenis kelamin, kode pos asal.
    Penjual: Mewakili penjual yang terlibat dalam transaksi dengan detail seperti kode pos penjual, kategori.
 2. Membuat Tabel dan Mendefinisikan Primary Key:

     **Tabel Transaksi**
     transaction_id (INT) PRIMARY KEY -- Pengenal unik untuk setiap transaksi
    
     step VARCHAR(255) -- Langkah dalam proses transaksi
    
     amount DECIMAL(10,2) - Jumlah/berat barang dalam ekspedisi pengiriman
    
     fraud integer
    
    **Tabel customer**
    customer_id INT PRIMARY KEY -- Pengenal unik untuk setiap pelanggan
    
    age INT -- Usia pelanggan
    
    gender VARCHAR(255) --Jenis kelamin pelanggan
    
    zipcodeOri VARCHAR(255) -- Kode pos asal pelanggan

    **Tabel Penjual**
    merchant_id INT PRIMARY KEY --Pengenal unik untuk setiap penjual
    
    name VARCHAR(255) --Nama penjual
    
    zipMerchant VARCHAR(255) --Kode pos penjual
    
    category TEXT

 4. Membangun Relasi Foreign Key:
    Tabel Transaksi:
     - Tambahkan foreign key customer_id yang mereferensikan customer_id di tabel Pelanggan.
     - Tambahkan foreign key merchant_id yang mereferensikan merchant_id di tabel Penjual.
 5. Struktur Database yang dihasilkan:

     SQL

     CREATE TABLE Transaksi
     (
        transaction_id INT PRIMARY KEY,
    
        step VARCHAR(255),
    
        amount DECIMAL(10,2),
    
        fraud BOOLEAN,
    
        customer_id INT,
    
        merchant_id INT,
    
        FOREIGN KEY (customer_id) REFERENCES Pelanggan(customer_id),
    
        FOREIGN KEY (merchant_id) REFERENCES Penjual(merchant_id)
      );

     CREATE TABLE Pelanggan (
       customer_id INT PRIMARY KEY,
    
       age INT,
    
       gender VARCHAR(255),
    
       zipcodeOri VARCHAR(255)
     );

    CREATE TABLE Penjual (
    
     merchant_id INT PRIMARY KEY,
    
     name VARCHAR(255),
    
     zipMerchant VARCHAR(255),
    
     category VARCHAR(255)
    
     );


  7. Manfaat Desain 3NF:
     Integritas Data: Menghilangkan duplikasi data dan mengurangi risiko ketidakkonsistenan data.
     Manipulasi Data Lebih Mudah: Menyederhanakan penyisipan, pembaruan, dan penghapusan data.
     Ruang Penyimpanan Berkurang: Menghemat penyimpanan dengan menyimpan data berulang hanya sekali.
     Performa Query yang Lebih Baik: Memisahkan data terkait dapat mengoptimalkan query untuk aspek tertentu.
  8. Dampak pada Query:
     Pengambilan Data yang Efisien: Query dapat secara efisien mengambil data tertentu dari tabel yang sesuai tanpa join yang tidak perlu.
     Mengurangi Operasi Join: Lebih sedikit join yang diperlukan, sehingga meningkatkan kinerja query.
     Hasil yang Akurat: Tidak adanya duplikasi data memastikan hasil query akurat dan konsisten.
     Kesimpulan:
     Mendesain database dalam 3NF mengikuti prinsip integritas data dan meningkatkan kinerja query. Struktur yang dinormalisasi menyederhanakan manajemen data, mengurangi 
     kebutuhan penyimpanan, dan memastikan keakuratan hasil saat mengambil data.
