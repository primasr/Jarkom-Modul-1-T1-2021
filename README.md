# Laporan Resmi Jarkom Modul 1
## _Anggota Kelompok_

1. Prima Secondary R (0531194000001)
2. Asiyah Hanifah (05311940000002)
3. Widya Inayatul L (05311940000010)
---
## 1. Sebutkan webserver yang digunakan pada "ichimarumaru.tech"! 

mengisi dan menggunakan filter  ```http.host contains"ichimarumaru.tech"```

![unnamed](https://user-images.githubusercontent.com/73151978/134696145-92191171-c0ee-4f32-a879-5c7c179c177c.png)

Kemudian follow TCP nya sehingga didapat Server yang digunakan adalah nginx/1.18.0 (Ubuntu)

![unnamed (1)](https://user-images.githubusercontent.com/73151978/134696352-b1f7157f-f7c4-4341-a516-5243e5c5e463.png)

## 2. Temukan paket dari web-web yang menggunakan basic authentication method!

Mengisi filter dengan ```http.authbasic```

![unnamed (2)](https://user-images.githubusercontent.com/73151978/134696954-f40fee6e-844d-49ed-bc7b-901666619a28.png)

Didapatkan kredensial berupa username dan password secara berurutan adalah ```kuncimenujulautan``` dan ```tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN```

## 3. Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!

Kita lakukan login menggunakan username dan password pada soal 2. Sehingga menampilkan sebuah website pada gambar dibawah ini

![unnamed (3)](https://user-images.githubusercontent.com/73151978/134697284-8380274e-e959-4c26-b96f-8dec80ee7343.png)

Dengan jawaban HIJAU PUTIH, HIJAU, ORANGE PUTIH, BIRU, BIRU PUTIH, ORANGE, COKLAT PUTIH, COKLAT

## 4. Temukan paket mysql yang mengandung perintah query select!

Di sini kami memasukkan ```filter mysql.query``` pada wireshark untuk menemukan paket mysql dengan perintah query select yang ditemukan dengan melihat request command query pada paket-paketnya.

![unnamed (4)](https://user-images.githubusercontent.com/73151978/134697552-2588fd0d-5926-40cb-b474-615808023a7a.png)
![unnamed (5)](https://user-images.githubusercontent.com/73151978/134697562-ef8ff333-fc56-421d-8292-e0ae292db245.png)

## 5. Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!

Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!

Di sini kami memasukkan filter mysql.query pada wireshark untuk menemukan paket mysql dengan perintah query insert yang ditemukan dengan melihat request command query pada paket-paketnya.

![unnamed (6)](https://user-images.githubusercontent.com/73151978/134697803-69ba296c-d1a2-4591-a3ff-1b6b8161c188.png)

Kemudian kami masuk ke link ```portal.ichimarumaru.tech``` dan memasukkan users beserta passwordnya. Dari gambar diatas, didapatkan kredensial berupa username dan password secara berurutan adalah ```akakanomi``` dan ```pemisah4lautan```

![unnamed (7)](https://user-images.githubusercontent.com/73151978/134697809-be47eb45-5819-46f1-9331-93e21d9b15ee.png)

Lalu portal.ichimarumaru.tech akan menampilkan sebuah website seperti dibawah

![unnamed (8)](https://user-images.githubusercontent.com/73151978/134697814-8efe5c80-7abd-42b9-9554-96735580587b.png)

Dengan jawaban ORANGE PUTIH, ORANGE, HIJAU PUTIH, BIRU, BIRU PUTIH, HIJAU, COKLAT PUTIH, COKLAT

## 6. Cari username dan password ketika melakukan login ke FTP Server!

Karena meminta username dan password, maka request commandnya pasti USER atau PASS. Maka, kita tinggal memasukkan filter 

```sh
ftp.request.command == USER || ftp.request.command == PASS
```

![6.1](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/6.1.png)

> Didapatkan Username dan Password secara berurutan adalah `secretuser` dan `aku.pengen.pw.aja`

## 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

Kita jalankan command, 
```sh
frame.contains “Real.pdf”. 
```

Maka akan tampil filter seperti gambar dibawah

![7.1](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/7.1.png)

Setelah itu, tinggal kita `Klik Kanan > Follow > Follow TCP`.

Lalu, akan muncul seperti gambar dibawah. Untuk menyimpan file `zip` nya, kita perlu mengubahnya ke `Raw` terlebih dahulu. Setelah itu, tinggal `Save as ..`

![7.2](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/7.2.png)

Gambar dibawah menunjukkan isi dari file zip nya

![7.3](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/7.3.png)

![7.4](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/7.4.png)

Setelah dibuka…. Dang~ Kena Rick Roll

![7.5](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/7.5.png)

## 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!

Masukkan filter dibawah, untuk mendapatkan request apa saja yang terjadi pada FTP

```sh
ftp.request.command
```

![8.1](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/8.1.png)

Setelah menjalankan perintah `ftp.request.command` , tidak menunjukkan trafik yang melakukan pengambilan file dari FTP (pengambilan file itu punya format `RETR`)

Trafik yang ada hanyalah `PASV` dan `STOR`

> Maka, tidak ditemukan proses pengambilan file dari FTP yang ada!

## 9. Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

Tinggal jalankan command dibawah, lalu akan ter-filter seperti gambar dibawah

```sh
ftp-data
```

![9.1](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/9.1.png)

Setelah itu, tinggal kita `Klik Kanan > Follow > Follow TCP`.

Lalu, akan muncul seperti gambar dibawah. Untuk menyimpan file `zip` nya, kita perlu mengubahnya ke `Raw` terlebih dahulu. Setelah itu, tinggal `Save as ..`

![9.2](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/9.2.png)

Saat akan di _extract_, ternyata file zip tersebut memerlukan sebuah password. Password bisa didapatkan pada nomor 10

![9.3](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/9.3.png)

Setelah mendapatkan password dari nomor 10, kita masukkan saja ke form password pada file `.zip` nya tadi

Setelah dibuka, isi dari filenya adalah seperti pada gambar berikut

![9.4](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/9.4.png)

## 10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

Tinggal jalankan command dibawah, lalu akan ter-filter seperti gambar dibawah

```sh
ftp-data
```

![10.1](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/10.1.png)

Setelah itu, tinggal kita `Klik Kanan > Follow > Follow TCP`.

Setelah di follow, keluar tulisan begini. Berarti, password ada di `bukanapapa.txt`

![10.2](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/10.2.png)

Tinggal kita Follow TCP lagi untuk trafik pada `bukanapapa.txt` nya

![10.3](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/10.3.png)

![10.4](https://raw.githubusercontent.com/primasr/Jarkom-Modul-1-T1-2021/main/screenshot/10.4.png)

> Passwordnya adalah `d1b1langbukanapaapajugagapercaya`

## 11. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80! 
Disini karena diminta untuk menampilkan wireshark yang hanya mengambil paket yang berasal dari port 80. Kami menggunakan filter
```sh
src port 80
```
Sehingga didapat paket-paket yang berasal dari port 80 sebagai berikut.

## 12. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
Kemudian karena pada soal ini diminta untuk menampilkan wireshark hanya mengambil paket yang mengandung port 21. Kami menggunakan filter
```sh
tcp==port21
```
Berikut adalah paket-paket yang mengandung port 21.

## 13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!
Untuk soal ini diminta untuk menampilkan paket yang menuju port 443. Dan kami menggunakan filter 
```sh
dst port 443
```
## 14. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!
Selanjutnya pada soal ini diminta untuk menampilkan wireshark yang hanya mengambil paket yang tujuannya ke kemenag.go.id. Kami menggunakan filter
```sh
host kemenag.go.id
```
Berikut adalah paket yang tujuannya ke kemenag.go.id.
## 15. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
Selanjutnya pada soal ini diminta untuk menampilkan wireshark yang hanya mengambil paket yang berasal dari ip komputer kami masing-masing. Kami menggunakan filter
```sh
src host 192.168.1.118
```
Berikut adalah wireshark yang hanya mengambil paket yang berasal dari ip komputer kami.
![15.1](https://github.com/primasr/Jarkom-Modul-1-T1-2021/screenshoot/15.1.png)
