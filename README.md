# Jarkom-Modul-1-A10-2021

## No 1
Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!

**Cara 1 : Melihat Web nya langsung**  
Terlihat di web  "ichimarumaru.tech" sudah terlihat web server yang digunakan yaitu nginx.
[gambar]

**Cara 2 : Menggunakan Filter WireShark**  
Command : **http contains “ichimarumaru.tech”**  
Apabila command diatas kita eksekusi maka akan menghasilkan gambar berikut. Maksudnya disini adalah untuk mendapatkan ip dari ichimarumaru.tech saja. Sehingga mendapatkan hasil berikut :  
[gambar]  
Setelah mendapatkan IP hal yang harus kita lakukan adalah  
* Klik salah satu paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream

Hasilnya adalah sebagai berikut. Didapat bahwa webserver yang digunakan adalah **nginx**  
[gambar]

**Cara 3 :**  
Command : **http.host == ichimarumaru.tech**  
Http host berfungsi untuk mencari link dengan host ichimarumaru.tech. Hasil filter yang didapatkan adalah sebagai berikut :  
[gambar]  
Setelah mendapatkan IP hal yang harus kita lakukan adalah
* Klik salah satu paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream

Hasilnya adalah sebagai berikut. Didapat bahwa webserver yang digunakan adalah **nginx**  
[gambar]

## No 2
Temukan paket dari web-web yang menggunakan basic authentication method!  

Command : **http.authbasic**  
Dengan menggunakan command diatas kita dapat menemukan paket dari web-web yang menggunakan basic authentication method.  
[gambar]

## No 3
Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan
dari file .pcapng!  

Command : **http.host == basic.ichimarumaru.tech**  
Dengan command diatas maka didapatkan nantinya username dan password di bagian masuk Hypertext Transfer Protocol bagian authorization.  

Cara untuk mengetahui Password
* Masukkan Command
* Tekan salah satu paket
* Lihat dibagian hypertext transfer protocol
* Lihat bagian Authorization

Username serta password yang didapatkan adalah sebagai berikut  

Username : kuncimenujulautan  
Password : tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN  
[gambar]  
Setelah mendapatkan password maka kita akan masuk ke link tersebut. Setelah itu kita masukkan username serta password yang sudah kita dapatkan sebelumnya.  
[gambar]  
Setelah Login ternyata kita diminta untuk menyebutkan urutan konfigurasi pengkabelan T568A. Dimana konfigurasinya adalah sebagai berikut  
1. Putih Hijau
2. Hijau
3. Putih Orange
4. Biru
5. Putih Biru
6. Orange
7. Putih Coklat
8. Coklat  

[gambar]

## No 4
Temukan paket mysql yang mengandung perintah query select!  

**Cara 1 :**  
Command : **mysql.query && (frame contains "SELECT" || frame contains "select")**  
Apabila kita menjalankan kueri diatas maka akan menghasilkan kueri-kueri select.  
[gambar]  

**Cara 2 :**  
Kita bisa melakukan berbagai cara diantaranya dengan :  
Command : **tcp.stream eq 0**  

Dengan command diatas kita otomatis akan memfilter data yang awal masuk karena query select termasuk data pertama masuk. Berikut hasilnya  
[gambar]  
Setelah itu kita bisa mengambil dengan protokol yang bisa dilihat yaitu protocol Mysql karena kita diminta untuk mencari perintah mysql.  
Setelah mendapatkan IP hal yang harus kita lakukan adalah  
* Klik salah satu paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream

Dan hasilnya akan keluar bahwa disana sudah terlihat semua query Mysqlnya  
[gambar]  

**Cara 3 :**  
Command : **mysql**  
Kita bisa melakukan filtering dengan command ini untuk mendapatkan protocol yang hanya untuk Mysql.  
[gambar]  
Setelah itu kita bisa mengambil dengan protokol yang bisa dilihat yaitu protocol Mysql karena kita diminta untuk mencari perintah mysql.  
Setelah mendapatkan IP hal yang harus kita lakukan adalah  
* Klik paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream

[gambar]  

**Cara 4 :**  
Command : **mysql.command == 3**  
Apabila kita lakukan filtering ini maka kita akan mendapatkan kueri yang direquest dan disini kita bisa melihat query select disini  
[gambar]  
Setelah itu kita bisa mengambil dengan protokol yang bisa dilihat yaitu protocol Mysql karena kita diminta untuk mencari perintah mysql.  
[gambar]  

## No 5
Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan
password bisa didapat dari query insert pada table users dari file .pcap!  

**PASSWORD PALSU AGAK TERKECOH**  
[gambar]  
Setelah membaca soal lebih dalam ternyata memang salah penafsiran.  
**Cara 1 :**  
Command : **mysql.query && (frame contains "insert" || frame contains "INSERT")**  
Maka didapatkan hasil seperti berikut :  
Kita dapatkan bahwa :  
Username : akakanomi  
Password : pemisah4lautan  
[gambar]  

**Cara 2 :**  
Command : **mysql.command == 3**  
Dengan menuliskan command diatas kita sudah dapat paket Request Query. Sehingga bisa kita lakukan pencarian query.  
[gambar]  
Setelah paket ditemukan terdapat querynya yaitu  

“INSERT INTO users (username,password) VALUES (“akakanomi”, md5(“pemisah4lautan”))”  

Artinya dapat kita simpulkan bahwa :  
Username : akakanomi  
Password : pemisah4lautan  
[gambar]  

**Cara 3 :**  
Command : **tcp.stream eq 0**  
Apabila kita menggunakan command diatas kita mendapatkan paket yang diinginkan yaitu dengan protocol mysql  
[gambar]  
Setelah mendapatkan IP hal yang harus kita lakukan adalah  
* Klik paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream  

Kita dapatkan bahwa :  
Username : akakanomi  
Password : pemisah4lautan  
[gambar]  

Setelah dari Cara 1 dan Cara 2 mendapatkan username dan password maka kita akan login  
[gambar]  

Dan disini kita diminta untuk mengisikan urutan konfigurasi pengkabelan T568B. Urutannya adalah sebagai berikut :  
1. Putih Orange
2. Orange
3. Putih Hijau
4. Biru
5. Putih Biru
6. Hijau
7. Putih Coklat
8. Coklat  

[gambar]







## No 6

## No 7

## No 8

## No 9

## No 10

## No 11

## No 12

## No 13

## No 14

## No 15
