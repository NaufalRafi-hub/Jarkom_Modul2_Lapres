# Jarkom_Modul2_Lapres

Laporan Resmi Praktikum Modul 2 Jaringan Komputer 2020

Kelompok C07 (0099 &amp; 0157)

# Pembahasan Jawaban

### No 1 Kalian diminta untuk membuat sebuah website utama dengan (1) alamat http://semeruyyy.pw yang
memiliki 
### No 2 alias http://www.semeruyyy.pw 
### No 3 subdomain http://www.penanjakan.semeruyyy.pw yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO
### No 4 reverse domain untuk domain utama. Untuk mengantisipasi server dicuri/rusak, Bibah minta dibuatkan 
### No 5 DNS Server Slave pada MOJOKERTO agar Bibah tidak terganggu menikmati keindahan Semeru pada Website. Selain website utama Bibah juga meminta dibuatkan 
### No 6 subdomain dengan alamat http://gunung.semeruyyy.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO . Bibah juga ingin memberi petunjuk mendaki gunung semeru kepada anggota komunitas sehingga dia meminta dibuatkan 

### No 7 subdomain dengan nama http://naik.gunung.semeruyyy.pw , domain ini diarahkan ke IP Server PROBOLINGGO. Setelah selesai membuat keseluruhan domain, kamu diminta untuk segera mengatur web server. 

### No 8 Domain http://semeruyyy.pw memiliki DocumentRoot pada /var/www/semeruyyy.pw . Awalnya web dapat diakses menggunakan alamat http:// semeruyyy.pw /index.php/home 
### No 9 Karena dirasa alamat urlnya kurang bagus, maka diaktifkan mod rewrite agar urlnya menjadi http:// semeruyyy.pw /home .
### No 10 Web http://penanjakan.semeruyyy.pw akan digunakan untuk menyimpan assets file yangmemiliki DocumentRoot pada /var/www/ penanjakan.semeruyyy.pw dan memiliki struktur folder sebagai berikut:
/var/www/ penanjakan.semeruyyy.pw
/public/javascripts
/public/css
/public/images
/errors

### No 11 Pada folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan. 

### No 12 Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder /errors untuk mengganti error default 404 dari Apache. 
### No 13 Untuk mengakses file assets javascript awalnya harus menggunakan url http:// penanjakan.semeruyyy.pw /public/javascripts .Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi http:// penanjakan.semeruyyy.pw /js .Untuk web http:// gunung.semeruyyy.pw belum dapat dikonfigurasi pada web server karena menunggu pengerjaan website selesai. 

### No 14 sedangkan web http:// naik.gunung.semeruyyy.pw sudah bisa diakses hanya dengan menggunakan port 8888. DocumentRoot web berada pada /var/www/ naik.gunung.semeruyyy.pw . Dikarenakan web http:// naik.gunung.semeruyyy.pw bersifat private 
### No 15 Bibah meminta kamu membuat web http:// naik.gunung.semeruyyy.pw agar diberi autentikasi password dengan username “ semeru ” dan password “ kuynaikgunung ” supaya aman dan tidak sembarang orang bisa mengaksesnya. Saat Bibah mengunjungi IP PROBOLINGGO , yang muncul bukan web utama http:// semeruyyy.pw melainkan laman default Apache yang bertuliskan “It works!”. 

### No 16 Karena dirasa kurang profesional, maka setiap Bibah mengunjungi IP PROBOLINGGO akan dialihkan secara otomatis ke http:// semeruyyy.pw. 
### No 17 Karena pengunjung pada /var/www/ penanjakan.semeruyyy.pw/public/images sangat banyak maka semua request gambar yang memiliki substring “semeru” akan diarahkan menuju semeru.jpg.


