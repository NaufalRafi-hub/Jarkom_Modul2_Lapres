# Jarkom_Modul2_Lapres

Laporan Resmi Praktikum Modul 2 Jaringan Komputer 2020

Kelompok C07 (0099 &amp; 0157)

# Pembahasan Jawaban
Sebelum memasuki ke nomor soal, yaitu menambahkan server probolinggo dalam topologi.sh, sehingga menjadi 3 server yaitu Malang, Mojokerto, dan Probolinggo.
### No 1 Kalian diminta untuk membuat sebuah website utama dengan (1) alamat http://semeruyyy.pw 
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2_1.jpg)
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2_1.2.jpg)

membuat domain semeruc07.pw
+ mengubah konfigurasi dari `etc/bind/named.conf.local`, dan diisi zone sesuai domain yang diinginkan
+ membuat folder dengan nama jarkom 
+ copy file db.local ke dalam folder yang sudah dibuat
+ mengubah isi gile dalam `/etc/bind/jarkom2020.com` seperti gambar 2

### No 2 alias http://www.semeruyyy.pw 
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2_1.2.jpg)

menambahkan `cname` dengan menuliskan `www`

### No 3 subdomain http://www.penanjakan.semeruyyy.pw yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2_1.2.jpg)

menambahkan subdomain dengan menuliskan `IN` penanjakan.semeruc07.pw yang mengarah ke IP server PROBOLINGGO yaitu, `10.151.77.68`

### No 4 reverse domain untuk domain utama. Untuk mengantisipasi server dicuri/rusak, Bibah minta dibuatkan 
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2_1.jpg)
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.4.jpg)

menambahkan zone reverse dns dibawah zone domain
+ edit file `etc/bind/named.conf.local`
+ menambahkan 
  ` zone "77.151.10.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/77.151.10.in-addr.arpa";
    }; `
+ copy file dari db.local ke zone yang telah dibuat
+ mengedit file 77.151.10.in-addr.arpa dan menambahkan byte terakhir di IP MALANG

### No 5 DNS Server Slave pada MOJOKERTO agar Bibah tidak terganggu menikmati keindahan Semeru pada Website. Selain website utama Bibah juga meminta dibuatkan 
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2_1.jpg)
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.5.jpg)

membuat malang menjadi master dan mojokerto menjadi slave
+ edit file `etc/bind/named.conf.local` 
+ isi dengan 
    `zone "semeruc07.pw" { type master notify yes; also-notify { 10.151.77.68; }; allow-transfer { 10.151.77.68; }; file "/etc/bind/jarkom/semeruc07.pw"; };`
+ restart bind di malang
+ apt get update di mojokerto & install bind
+ edit file `etc/bind/named.conf.local` di mojokerto
+ mengubah dengan `zone "semeruc07.pw" { type slave;  masters { 10.151.77.68; }; "/var/lib/bind/semeruc07.pw"; };`

### No 6 subdomain dengan alamat http://gunung.semeruyyy.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO . Bibah juga ingin memberi petunjuk mendaki gunung semeru kepada anggota komunitas sehingga dia meminta dibuatkan 
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2_1.2.jpg)

menambahkan delegasi subdomain gunung di dalam semeruc07.pw
+ edit file `nano /etc/bind/jarkom/semeruc07.pw` di malang
+ tulis ns1 yang mengarah ke ip PROBOLINGGO
+ menulis delegasi subdomain yaitu gunung
+ membuat folder delegasi dan copy dblocal `mkdir /etc/bind/delegasi` dan `cp /etc/bind/db.local /etc/bind/delegasi/gunung.semeruc07.pw`
+ lalu edit file `etc/bind/named.conf.local` 
+ menambahkan zone gunung.semeruc07.pw 
+ isi dengan `zone "gunung.semeruc07.pw" { type master; file "/etc/bind/delegasi/gunung.semeruc07.pw"; allow-transfer {any; };  };`
+ dan di ping 

### No 7 subdomain dengan nama http://naik.gunung.semeruyyy.pw , domain ini diarahkan ke IP Server PROBOLINGGO. Setelah selesai membuat keseluruhan domain, kamu diminta untuk segera mengatur web server. 



### No 8 Domain http://semeruyyy.pw memiliki DocumentRoot pada /var/www/semeruyyy.pw . Awalnya web dapat diakses menggunakan alamat http:// semeruyyy.pw /index.php/home 
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.8.jpg)
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.8.2.jpg)
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.8.1.jpg)

langkah kerja
+ mengedit semeruc07.pw.conf
+ menggantikan document root menjadi `var/www/semeruc07.pw`
+ lalu melakukan restart apache `service apache2 restart`
+ cd kedalam `var/www/semeruc07.pw`
+ ls untuk mengecek file yang ada
+ dan masuk ke browser dan input alamat website


### No 9 Karena dirasa alamat urlnya kurang bagus, maka diaktifkan mod rewrite agar urlnya menjadi http:// semeruyyy.pw /home .
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.9.jpg)

langkah 
+ nano file .htaccess
+ rewriteRule `http://semeruc07.pw/index.php/home`
+ rewriteCond `^ /home`


### No 10 Web http://penanjakan.semeruyyy.pw akan digunakan untuk menyimpan assets file yangmemiliki DocumentRoot pada /var/www/ penanjakan.semeruyyy.pw dan memiliki struktur folder sebagai berikut:
/var/www/ penanjakan.semeruyyy.pw
/public/javascripts
/public/css
/public/images
/errors

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.10.jpg)
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.10.1.jpg)
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.10.2.jpg)
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.10.3.jpg)

langkah
+ membuat directory/ folder sesuai dengan yang dimau soal
+ edit file penanjakan.semeruc07.pw.conf
+ menambahkan directory yang sesuai dibawah documentroot
+ ` <Directory /var/www/penanjakan.semeruc07.pw/public> Options +Indexes </Directory>` dan
+ ` <Directory /var/www/penanjakan.semeruc07.pw/public/*> Options +Indexes </Directory>`
+ lalu ls untuk memastikan sesuai dengan kemauan soal

### No 11 Pada folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan. 
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.11.jpg)

langkah :
+ edit file penanjakan.semeruc07.pw.conf
+ menambahkan seperti digambar mulai dari alias


### No 12 Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder /errors untuk mengganti error default 404 dari Apache. 
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.12.jpg)
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.1.jpg)

langkah :
+ menambahkan `ErrorLog ${APACHE_LOG_DIR}/error.log`
+ menambahkan `ErrorDocument 404 /errors/404.html`
+ menambahkan `CustomLog ${APACHE_LOG_DIR}/access.log combined`
+ akses alamat di browser untuk mengecek apakah jika error masuk kedalam file 404

### No 13 Untuk mengakses file assets javascript awalnya harus menggunakan url http:// penanjakan.semeruyyy.pw /public/javascripts .Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi http:// penanjakan.semeruyyy.pw /js .Untuk web http:// gunung.semeruyyy.pw belum dapat dikonfigurasi pada web server karena menunggu pengerjaan website selesai. 
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.13.jpg)
 langkah :
 + mengedit file dalam penanjakan.semeruc70.pw.conf
 + menambahkan `alias "/js" "/var/www/penanjakan.semeruc07.pw/public/javascripts"


### No 14 sedangkan web http:// naik.gunung.semeruyyy.pw sudah bisa diakses hanya dengan menggunakan port 8888. DocumentRoot web berada pada /var/www/ naik.gunung.semeruyyy.pw . Dikarenakan web http:// naik.gunung.semeruyyy.pw bersifat private 


### No 15 Bibah meminta kamu membuat web http:// naik.gunung.semeruyyy.pw agar diberi autentikasi password dengan username “ semeru ” dan password “ kuynaikgunung ” supaya aman dan tidak sembarang orang bisa mengaksesnya. Saat Bibah mengunjungi IP PROBOLINGGO , yang muncul bukan web utama http:// semeruyyy.pw melainkan laman default Apache yang bertuliskan “It works!”. 


### No 16 Karena dirasa kurang profesional, maka setiap Bibah mengunjungi IP PROBOLINGGO akan dialihkan secara otomatis ke http:// semeruyyy.pw. 
![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul2_Lapres/blob/main/image/modul2.16.jpg)

langkah : 
+ mengedit file 000-default.conf
+ menambahkan `redirect /http://semeruc02.pw/`

### No 17 Karena pengunjung pada /var/www/ penanjakan.semeruyyy.pw/public/images sangat banyak maka semua request gambar yang memiliki substring “semeru” akan diarahkan menuju semeru.jpg.


