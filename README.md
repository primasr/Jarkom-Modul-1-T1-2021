# Laporan Resmi Jarkom Modul 1
## _Anggota Kelompok_

- Prima Secondary Ramadhan  - 05311940000001
- Ifa
- Widya

## 1. Sebutkan webserver yang digunakan pada "ichimarumaru.tech"! 
## 2. Temukan paket dari web-web yang menggunakan basic authentication method!
## 3. Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!
## 4. Temukan paket mysql yang mengandung perintah query select!
## 5. Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!
## 6. Cari username dan password ketika melakukan login ke FTP Server!

Karena meminta username dan password, maka request commandnya pasti USER atau PASS. Maka, kita tinggal memasukkan filter 

```sh
ftp.request.command == USER || ftp.request.command == PASS
```

> Didapatkan Username dan Password secara berurutan adalah `secretuser` dan `aku.pengen.pw.aja`

## 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

Kita jalankan command, 
```sh
frame.contains “Real.pdf”. 
```

Maka akan tampil filter seperti gambar dibawah

Setelah itu, tinggal kita `Klik Kanan > Follow > Follow TCP`.

Lalu, akan muncul seperti gambar dibawah. Untuk menyimpan file `zip` nya, kita perlu mengubahnya ke `Raw` terlebih dahulu. Setelah itu, tinggal `Save as ..`

Gambar dibawah menunjukkan isi dari file zip nya

Setelah dibuka…. Dang~ Kena Rick Roll

## 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!

Masukkan filter dibawah, untuk mendapatkan request apa saja yang terjadi pada FTP

```sh
ftp.request.command
```

Setelah menjalankan perintah `ftp.request.command` , tidak menunjukkan trafik yang melakukan pengambilan file dari FTP (pengambilan file itu punya format `RETR`)

Trafik yang ada hanyalah `PASV` dan `STOR`

> Maka, tidak ditemukan proses pengambilan file dari FTP yang ada!

## 9. Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

Tinggal jalankan command dibawah, lalu akan ter-filter seperti gambar dibawah

```sh
ftp-data
```

Setelah itu, tinggal kita `Klik Kanan > Follow > Follow TCP`.

Lalu, akan muncul seperti gambar dibawah. Untuk menyimpan file `zip` nya, kita perlu mengubahnya ke `Raw` terlebih dahulu. Setelah itu, tinggal `Save as ..`

Saat akan di _extract_, ternyata file zip tersebut memerlukan sebuah password. Password bisa didapatkan pada nomor 10

Setelah mendapatkan password dari nomor 10, kita masukkan saja ke form password pada file `.zip` nya tadi

Setelah dibuka, isi dari filenya adalah seperti pada gambar berikut



## 10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

Tinggal jalankan command dibawah, lalu akan ter-filter seperti gambar dibawah

```sh
ftp-data
```

Setelah itu, tinggal kita `Klik Kanan > Follow > Follow TCP`.

Setelah di follow, keluar tulisan begini. Berarti, password ada di `bukanapapa.txt`

Tinggal kita Follow TCP lagi untuk trafik pada `bukanapapa.txt` nya

> Passwordnya adalah `d1b1langbukanapaapajugagapercaya`

## 11. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80! 
## 12. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
## 13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!
## 14. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!
## 15. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
