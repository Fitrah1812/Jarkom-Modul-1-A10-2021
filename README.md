# Jarkom-Modul-1-A10-2021

## No 1
Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!

**Cara 1 : Melihat Web nya langsung**  

Terlihat di web  "ichimarumaru.tech" sudah terlihat web server yang digunakan yaitu nginx.

![gambar1](https://imgur.com/INIkghv.png)  

**Cara 2 : Menggunakan Filter WireShark**

Command : ```http contains “ichimarumaru.tech”```

Apabila command diatas kita eksekusi maka akan menghasilkan gambar berikut. Maksudnya disini adalah untuk mendapatkan ip dari ichimarumaru.tech saja. Sehingga mendapatkan hasil berikut :

![gambar2](https://imgur.com/rggLQHg.png)   

Setelah mendapatkan IP hal yang harus kita lakukan adalah  
* Klik salah satu paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream

Hasilnya adalah sebagai berikut. Didapat bahwa webserver yang digunakan adalah **nginx**

![gambar3](https://imgur.com/FukHiYt.png)  

**Cara 3 :** 

Command : ```http.host == ichimarumaru.tech ```

Http host berfungsi untuk mencari link dengan host ichimarumaru.tech. Hasil filter yang didapatkan adalah sebagai berikut :  

![gambar4](https://imgur.com/9b05veU.png) 

Setelah mendapatkan IP hal yang harus kita lakukan adalah
* Klik salah satu paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream

Hasilnya adalah sebagai berikut. Didapat bahwa webserver yang digunakan adalah **nginx** 

![gambar5](https://imgur.com/xaGUSl6.png)  

## No 2
Temukan paket dari web-web yang menggunakan basic authentication method!  

Command : ```http.authbasic  ```

Dengan menggunakan command diatas kita dapat menemukan paket dari web-web yang menggunakan basic authentication method.  

![gambar6](https://imgur.com/sQ8iH13.png)  

## No 3
Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan
dari file .pcapng!  

Command :``` http.host == basic.ichimarumaru.tech  ```

Dengan command diatas maka didapatkan nantinya username dan password di bagian masuk Hypertext Transfer Protocol bagian authorization.  

Cara untuk mengetahui Password
* Masukkan Command
* Tekan salah satu paket
* Lihat dibagian hypertext transfer protocol
* Lihat bagian Authorization

Username serta password yang didapatkan adalah sebagai berikut  

Username : kuncimenujulautan
Password : tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN 

![gambar7](https://imgur.com/d6gmumV.png)

Setelah mendapatkan password maka kita akan masuk ke link tersebut. Setelah itu kita masukkan username serta password yang sudah kita dapatkan sebelumnya.  

![gambar8](https://imgur.com/AOqt1RK.png) 

Setelah Login ternyata kita diminta untuk menyebutkan urutan konfigurasi pengkabelan T568A. Dimana konfigurasinya adalah sebagai berikut  
1. Putih Hijau
2. Hijau
3. Putih Orange
4. Biru
5. Putih Biru
6. Orange
7. Putih Coklat
8. Coklat  

![gambar9](https://imgur.com/1RkRrHU.png)  

## No 4
Temukan paket mysql yang mengandung perintah query select!  

**Cara 1 :**

Command :``` mysql.query && (frame contains "SELECT" || frame contains "select")  ```

Apabila kita menjalankan kueri diatas maka akan menghasilkan kueri-kueri select.  

![gambar10](https://imgur.com/QrCYBQg.png)  

**Cara 2 :** 

Command :``` tcp.stream eq 0  ```

Dengan command diatas kita otomatis akan memfilter data yang awal masuk karena query select termasuk data pertama masuk. Berikut hasilnya

![gambar11](https://imgur.com/n9cS0NV.png)

Setelah itu kita bisa mengambil dengan protokol yang bisa dilihat yaitu protocol Mysql karena kita diminta untuk mencari perintah mysql.  
Setelah mendapatkan IP hal yang harus kita lakukan adalah  
* Klik salah satu paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream

Dan hasilnya akan keluar bahwa disana sudah terlihat semua query Mysqlnya  

![gambar12](https://imgur.com/6Wj49yF.png)    

**Cara 3 :** 

Command :``` mysql ```

Kita bisa melakukan filtering dengan command ini untuk mendapatkan protocol yang hanya untuk Mysql. 

![gambar13](https://imgur.com/WjfrOUv.png)

Setelah itu kita bisa mengambil dengan protokol yang bisa dilihat yaitu protocol Mysql karena kita diminta untuk mencari perintah mysql.  
Setelah mendapatkan IP hal yang harus kita lakukan adalah  
* Klik paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream

![gambar14](https://imgur.com/NsOnr4G.png)    

**Cara 4 :** 

Command :``` mysql.command == 3 ``` 

Apabila kita lakukan filtering ini maka kita akan mendapatkan kueri yang direquest dan disini kita bisa melihat query select disini  

![gambar15](https://imgur.com/8Bj4et3.png) 

Setelah itu kita bisa mengambil dengan protokol yang bisa dilihat yaitu protocol Mysql karena kita diminta untuk mencari perintah mysql. 

![gambar16](https://imgur.com/YC6yEjt.png)    

## No 5
Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan
password bisa didapat dari query insert pada table users dari file .pcap!  

**PASSWORD PALSU AGAK TERKECOH** 

![gambar17](https://imgur.com/FyN4W6l.png)  

Setelah membaca soal lebih dalam ternyata memang salah penafsiran.

**Cara 1 :** 

Command :``` mysql.query && (frame contains "insert" || frame contains "INSERT")  ```

Maka didapatkan hasil seperti berikut :  

Username : akakanomi  
Password : pemisah4lautan  

![gambar18](https://imgur.com/qU52aZO.png)    

**Cara 2 :**

Command :``` mysql.command == 3  ```

Dengan menuliskan command diatas kita sudah dapat paket Request Query. Sehingga bisa kita lakukan pencarian query. 

![gambar19](https://imgur.com/ujHQndl.png)  

Setelah paket ditemukan terdapat querynya yaitu  

“INSERT INTO users (username,password) VALUES (“akakanomi”, md5(“pemisah4lautan”))”  

Artinya dapat kita simpulkan bahwa :  

Username : akakanomi  
Password : pemisah4lautan  

![gambar20](https://imgur.com/rIyrsFo.png)    

**Cara 3 :**

Command : ```tcp.stream eq 0 ```

Apabila kita menggunakan command diatas kita mendapatkan paket yang diinginkan yaitu dengan protocol mysql 

![gambar21](https://imgur.com/IFZavXN.png)  

Setelah mendapatkan IP hal yang harus kita lakukan adalah  
* Klik paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream  

Kita dapatkan bahwa :  

Username : akakanomi  
Password : pemisah4lautan 

![gambar22](https://imgur.com/n9bPgPM.png)    

Setelah dari Cara 1 dan Cara 2 mendapatkan username dan password maka kita akan login  

![gambar23](https://imgur.com/CuecDm9.png)    

Dan disini kita diminta untuk mengisikan urutan konfigurasi pengkabelan T568B. Urutannya adalah sebagai berikut :  
1. Putih Orange
2. Orange
3. Putih Hijau
4. Biru
5. Putih Biru
6. Hijau
7. Putih Coklat
8. Coklat  

![gambar24](https://imgur.com/EAMJzQm.png)  

## No 6
Cari username dan password ketika melakukan login ke FTP Server!  

**Cara 1 :** 

Command :``` ftp.request.command contains “USER”  ```

Apabila kita menjalankan command diatas maka kita akan mendapatkan User  

User : secretuser

![gambar25](https://imgur.com/Np5Yr6R.png)  

Command : ```ftp.request.command contains “PASS” ```

Apabila kita menjalankan command diatas maka kita akan mendapatkan Pass 

Pass : aku.pengen.pw.aja  

![gambar26](https://imgur.com/3yLJN46.png)  

**Cara 2 :**  

Command :``` ftp  ```

Setelah menjalankan command diatas kita akan mendapatkan data ftp setelah itu bisa kita lakukan CTRL F untuk Find. Berikut adalah tambilan untuk User

User : secretuser  

![gambar27](https://imgur.com/yJHl51w.png)  

Setelah menjalankan command diatas kita akan mendapatkan data ftp setelah itu bisa kita lakukan CTRL F untuk Find. Berikut adalah tambilan untuk Pass  

Pass: aku.pengen.pw.aja  

![gambar28](https://imgur.com/xrq3QRj.png)  

Secara keseluruhan didapatkan sebagai berikut :

User : secretuser  
Pass : aku.pengen.pw.aja  

## No 7
Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip.
Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")  

Command :``` tcp contains Real.pdf  ```

Dengan menggunakan command diatas contains berfungsi untuk seperti “where name like” di database. Sehingga dapatkan paket-paket yang berisi Real.pdf adalah sebagai berikut yaitu 201.zip  

![gambar29](https://imgur.com/ibiHCDX.png)  

Setelah mendapatkan IP hal yang harus kita lakukan adalah  
* Klik paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream
* Ubah show data as menjadi raw
* Setelah itu save data ke folder yang diinginkan
 
![gambar30](https://imgur.com/qCdNhII.png)  

Hasilnya didalam folder

![gambar31](https://imgur.com/oyKOr82.png)  

Setelah kita extract didapatkan data sebagai berikut : 

![gambar32](https://imgur.com/tjit8gD.png)  

## No 8
Cari paket yang menunjukan pengambilan file dari FTP tersebut!  

Command : ```ftp.request.command contains “RETR”  ```

Pengambilan file dari FTP adalah RETR. Dengan menggunakan **ftp.request.command contains “RETR”**. Datanya kosong. Sehingga dapat disimpulkan paket yang didownload tidak ada.  

![gambar33](https://imgur.com/Q0ssGq6.png)  

## No 9
Dari paket-paket yang menuju FTP terdapat indikasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!  

Command : ```ftp-data.command contains secret.zip``` 

Setelah kita menjalankan command diatas kita akan mendapatkan paket yang terdapat namanya secret.zip fungsinya agar bisa mendapatkan data yang kita inginkan. Yaitu kita menginkan secret.zip didapatlah bahwa ada uploadan paket secret.zip sehingga kita bisa langsung mengeksekusi.  

![gambar34](https://imgur.com/gkldoIp.png)  

Setelah mendapatkan IP hal yang harus kita lakukan adalah  
* Klik paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream
* Ubah show data as menjadi raw
* Setelah itu save data ke folder yang diinginkan

![gambar35](https://imgur.com/NTkADNr.png)  

hasilnya adalah sebagai berikut :  

![gambar36](https://imgur.com/8dN1Tk4.png)  

## No 10
Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut!
Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang
ada di "secret.zip"!  

**Cara 1 :**  

Pertama yang dilakukan adalah ctrl F untuk find history.txt 

![gambar37](https://imgur.com/Kdwu65w.png)  

Setelah itu klik kanan dan menemukan tail atau ekor

![gambar38](https://imgur.com/IROhsgs.png)  

Setelah itu buka ftp-data.command contains "bukanapaapa.txt"

![gambar39](https://imgur.com/j8V8iYl.png)  

Klik kanan follow TCP Stream  

![gambar40](https://imgur.com/ShLzBBa.png)  

convert raw dan save bukanapaapa.txt  

![gambar41](https://imgur.com/a1tEu9k.png)  

password : d1b1langbukanapaapajugagapercaya  

**Cara 2 :**  

Apabila kita lihat lebih dalam setelah kita mendapatkan secret.zip terdapat file yang bernama Wanted.pdf 

![gambar42](https://imgur.com/vTh8HO4.png)  

Dari sini saya berasumsi bahwa kunci secret.zip ini akan mengindikasi file Wanted.pdf ini juga oleh karena itu saya filter dengan menggunakan : 

Command :``` tcp contains “Wanted.pdf” ``` 

Setelah menjalan command diatas didapatkan hasil berikut :  

![gambar43](https://imgur.com/RJ6fjjO.png)  

Setelah itu membuka paket dengan tulisan history.txt  

![gambar44](https://imgur.com/DSiYY8s.png)  

Didapatkan hasil berikut. Dapat disimpulkan bahwa file history memiliki ekor bagian bukanapaapa.txt. . Selanjutnya saya memfilter dengan  

command :``` ftp-data.command contains “bukanapaapa.txt”  ```

Hasilnya adalah sebagai berikut :  

![gambar45](https://imgur.com/B2R3FoM.png)  

Selanjutnya kita menyimpan atau bisa dilihat saja keynya seperti berikut  

Setelah mendapatkan IP hal yang harus kita lakukan adalah  
* Klik paket
* Klik kanan
* Cari Tombol Follow
* Tekan TCP Stream
* Ubah show data as menjadi raw
* Setelah itu save data ke folder yang diinginkan

Sebenarnya passwordnya sudah kelihatan dari sini 

![gambar46](https://imgur.com/n2Lhozl.png)  

Saya akan save terlebih dahulu supaya bisa mendapatkan file.txtnya

![gambar47](https://imgur.com/TAQJmI5.png)  

Di folder akan didapatkan sebagai berikut : 

![gambar48](https://imgur.com/VszI1VC.png)  

Setelah itu kita masukkan passwordnya

![gambar49](https://imgur.com/KH42y99.png)  

Hasil secret.zip adalah sebagai berikut  

![gambar50](https://imgur.com/3FmFWAv.png)  

## No 11
Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!  

Menggunakan Capture Filter : ```src port 80  ```

![gambar51](https://imgur.com/73dmyhm.png)  

## No 12
Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

Pertama tama melakukan koneksi dari FileZilla client menuju ke server. 

Menggunakan capture filter: ```port 21  ```

![gambar52](https://imgur.com/5M0cctE.png)  

## No 13
Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!  

Menggunakan Capture filter : ```dst port 443  ```

![gambar53](https://imgur.com/yF6zyGh.png)  

## No 14
Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!  

Menggunakan capture filter: ```dst host kemenag.go.id```

![gambar54](https://imgur.com/HOzs483.png)  

## No 15
Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!  

Pertama menggunakan CMD untuk mengetahui IP sendiri. 

Menggunakan command : ```ipconfig ```

![gambar55](https://imgur.com/ix3VtRX.png)  

Kemudian, menggunakan capture filter pada wiresharknya.  

Menggunakan Filter :``` src host 192.168.100.142  ```

![gambar56](https://imgur.com/bfy6IaX.png)  
