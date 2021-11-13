# Jarkom-Modul-3-B08-2021

Nama | NRP |
--- | --- | 
Adam Hadi Prasetyo | 05111940000224 |
Vyra Fania Adelina | 05111940000109 |
Tsania Az Zahra | 05111940000032 |

1.	Luffy bersama Zoro berencana membuat peta tersebut dengan kriteria EniesLobby sebagai DNS Server, Jipangu sebagai DHCP Server, Water7 sebagai Proxy Server
2.	dan Foosha sebagai DHCP Relay
3.	Semua client yang ada HARUS menggunakan konfigurasi IP dari DHCP Server. Client yang melalui Switch1 mendapatkan range IP dari [prefix IP].1.20 - [prefix IP].1.99 dan [prefix IP].1.150 - [prefix IP].1.169 
4.	Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.30 - [prefix IP].3.50
5.	Client mendapatkan DNS dari EniesLobby dan client dapat terhubung dengan internet melalui DNS tersebut.
6.	Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch1 selama 6 menit sedangkan pada client yang melalui Switch3 selama 12 menit. Dengan waktu maksimal yang dialokasikan untuk peminjaman alamat IP selama 120 menit.
7.	Luffy dan Zoro berencana menjadikan Skypie sebagai server untuk jual beli kapal yang dimilikinya dengan alamat IP yang tetap dengan IP [prefix IP].3.69
8.	Loguetown digunakan sebagai client Proxy agar transaksi jual beli dapat terjamin keamanannya, juga untuk mencegah kebocoran data transaksi. Pada Loguetown, proxy harus bisa diakses dengan nama jualbelikapal.yyy.com dengan port yang digunakan adalah 5000
9.	Agar transaksi jual beli lebih aman dan pengguna website ada dua orang, proxy dipasang autentikasi user proxy dengan enkripsi MD5 dengan dua username, yaitu luffybelikapalyyy dengan password luffy_yyy dan zorobelikapalyyy dengan password zoro_yyy
10.	Transaksi jual beli tidak dilakukan setiap hari, oleh karena itu akses internet dibatasi hanya dapat diakses setiap hari Senin-Kamis pukul 07.00-11.00 dan setiap hari Selasa-Jum’at pukul 17.00-03.00 keesokan harinya (sampai Sabtu pukul 03.00)
11.	Agar transaksi bisa lebih fokus berjalan, maka dilakukan redirect website agar mudah mengingat website transaksi jual beli kapal. Setiap mengakses google.com, akan diredirect menuju super.franky.yyy.com dengan website yang sama pada soal shift modul 2. Web server super.franky.yyy.com berada pada node Skypie
12.	Saatnya berlayar! Luffy dan Zoro akhirnya memutuskan untuk berlayar untuk mencari harta karun di super.franky.yyy.com. Tugas pencarian dibagi menjadi dua misi, Luffy bertugas untuk mendapatkan gambar (.png, .jpg), sedangkan Zoro mendapatkan sisanya. Karena Luffy orangnya sangat teliti untuk mencari harta karun, ketika ia berhasil mendapatkan gambar, ia mendapatkan gambar dan melihatnya dengan kecepatan 10 kbps
13.	Sedangkan, Zoro yang sangat bersemangat untuk mencari harta karun, sehingga kecepatan kapal Zoro tidak dibatasi ketika sudah mendapatkan harta yang diinginkannya


## Jawaban
### 1. Luffy bersama Zoro berencana membuat peta tersebut dengan kriteria EniesLobby sebagai DNS Server, Jipangu sebagai DHCP Server, Water7 sebagai Proxy Server
Step :

Pertama jadikan EniesLobby menjadi DNS Server

![](img/modul3_no1_eniesLobby_DNS.PNG)

Lalu jadikan Jipangu sebagai DHCP Server

![](img/modul3_no1_Jipangu_isc-dhcp-server.PNG)

Kemudian jadikan Water7 sebagai Proxy Server

![](img/modul3_no1_Jipangu_isc-dhcp-server.PNG)

### 2.	dan Foosha sebagai DHCP Relay

![](img/modul3_no1_Water7_ProxyServer.PNG)
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no2_Foosha_dhcp-relay-conf.PNG)

### 3.	Semua client yang ada HARUS menggunakan konfigurasi IP dari DHCP Server. Client yang melalui Switch1 mendapatkan range IP dari [prefix IP].1.20 - [prefix IP].1.99 dan [prefix IP].1.150 - [prefix IP].1.169 

![](img/modul3_no3_Jipangu_switch1-conf.PNG)

### 4.	Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.30 - [prefix IP].3.50

![](img/modul3_no4_Jipangu_switch3-conf.PNG)

### 8. Loguetown digunakan sebagai client Proxy agar transaksi jual beli dapat terjamin keamanannya, juga untuk mencegah kebocoran data transaksi. Pada Loguetown, proxy harus bisa diakses dengan nama jualbelikapal.yyy.com dengan port yang digunakan adalah 5000
jualbelikapal.b08.com harus terdaftar pada DNS agar dapat diakses oleh klien :
####  Konfigurasi Domain Pada EniesLobby
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no8_eniesLobby_jualbelikapalb08-domain-conf2.PNG)
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no8_eniesLobby_jualbelikapalb08-domain-conf.PNG)
Port proxy server dikonfigurasikan agar dapat terhubung dengan klien :
####  Konfigurasi Port untuk Proxy Server
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no8_Water7_proxy-port-conf.PNG)
####  Test melalui CLI
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no8_loguetown_CLI-proxy-conf.PNG)
####  Hasil Test
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no8_loguetown_RESULT_proxy-auth-activated.PNG)

### 9. Agar transaksi jual beli lebih aman dan pengguna website ada dua orang, proxy dipasang autentikasi user proxy dengan enkripsi MD5 dengan dua username, yaitu luffybelikapalyyy dengan password luffy_yyy dan zorobelikapalyyy dengan password zoro_yyy
username dan password harus terdefinisikan pada proxy-server :
#### Konfigurasi proxy
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no9_water7_create-acc-MD5encryption.PNG)
melakukan test untuk cek jika konfigurasi berhasil :
#### Test Loguetown/Client
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no9_loguetown_lynx-username-input.PNG)
#### Hasil
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no9_loguetown_lynx-enter-website-success.PNG)

### 10. Transaksi jual beli tidak dilakukan setiap hari, oleh karena itu akses internet dibatasi hanya dapat diakses setiap hari Senin-Kamis pukul 07.00-11.00 dan setiap hari Selasa-Jum’at pukul 17.00-03.00 keesokan harinya (sampai Sabtu pukul 03.00)
waktu akses harus disetting untuk mengontrol proxy-server  :
#### Konfigurasi Squid-Acl
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no10_config-squid-acl.PNG)
waktu akses harus dideteksi untuk pelarangan akses oleh squid-conf  :
#### Konfigurasi Squid.conf
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no10_config-squid.PNG)
#### Tes Pergantian Waktu Untuk Diperbolehkan Akses
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no10_CLI-change-time_enterSuccess.PNG)
#### Hasil Test
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/tree/main/img)
#### Hasil Test - Dilarang Akses
![](https://github.com/tsnzzhr/Jarkom-Modul3-B08-2021/blob/main/img/modul3_no10_loguetown_RESULT_forbidden_403.PNG)
