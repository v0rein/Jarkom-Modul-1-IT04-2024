# Jarkom-Modul-1-IT04-2024
|Nama  | NRP |
|--|--|
| Dionisius Marcell Putra Indranto | 5027231044 |
| Aswalia Novitriasari | 5027231012 |

## Content
### Advance Sanity Check
Yang sederhana dulu aja.

Step pengerjaan :
1. display filter ``` frame contains "username" ```
2. display filter ``` frame containts “.txt” ```
3. Open Clue3.txt, ada clue untuk membuka file ppt peraturan praktikum
4. Decode penword yang ada di ppt praktikum dari base64
nc 10.15.42.60 44000

![WhatsApp Image 2024-09-18 at 22 44 01_948fb8f2](https://github.com/user-attachments/assets/36387602-bc36-4a48-8144-1161248476f4)

### Illegal Breakthrough
Seorang full-stack developer bernama kevin sedang membuat sebuah web yang memiliki login page. Tetapi karena ia hanya digaji rendah, ia lupa untuk mengamankan web yang ia buat. Bantulah kevin untuk tracing dari jejak yang ditinggalkan oleh attacker.

Step pengerjaan :
1. Open TCP paling atas untuk melihat port.dst
2. display filter ``` frame contains "username" ``` >> Follow
3. display filter ``` http && ip.src eq 172.21.88.207 ``` >> Follow yang ada info FOUND
nc 10.15.42.60 46000

![WhatsApp Image 2024-09-18 at 22 44 01_f95ea7a3](https://github.com/user-attachments/assets/d2db0705-559b-45de-bed8-436249ee52b5)

### Packets Barrage
Setelah membantu kevin untuk tracing attacker, sekarang bantu lagi kevin untuk mencari apa yang dilakukan oleh attacker.
File sama seperti Illegal Breakthrough.

Step Pengerjaan :
1. ip.src http
2. display filter ``` http && ip.src eq 172.21.88.207 ``` >> Follow stream yang FOUND lalu lihat displayed
3. Follow stream di display filter yang sama di info bagian 200 OK
nc 10.15.42.60 47000

![WhatsApp Image 2024-09-18 at 22 44 01_3e104ed3](https://github.com/user-attachments/assets/28e4b28b-181f-4e30-87c5-8c7ce94acf3a)

### FTP LOGIN
Seseorang menemukan sebuah celah dalam sebuah server. Ia mencoba untuk melakukan brute force login dan ia berhasil masuk. Lakukan pemeriksaan untuk melihat apa yang dilakukan oleh orang tersebut!

Step pengerjaan :
1. display filter ``` ftp ```
2. Follow stream di bagian Login Successful
nc 10.15.42.60 49000

![WhatsApp Image 2024-09-18 at 22 43 59_d6c4f5d4](https://github.com/user-attachments/assets/df00d0b6-a077-400a-b7a1-8939bccdba5f)

### Surprise
Easy nevarrawr
Setelah mengetahui apa yang diketahui pada challenge sebelumnya, sekarang lakukan analisis untuk mengetahui apa yang sebenarnya terjadi.
File sama seperti FTP Login.

Step pengerjaan :
1. display filter ``` frame contains "Login" ```
2. Follow stream di bagian Login successful
3. Naikkan 1 stream menjadi stream 5 untuk melihat isi g0tcha.cpp dan mengcompile code tersebut
nc 10.15.42.60 48500

![WhatsApp Image 2024-09-18 at 23 59 06_0ca615d2](https://github.com/user-attachments/assets/2704564d-5176-4eb2-8534-c48fa0638c9d)


### Corporate Breach
Sebuah perusahaan IT support mendapatkan serangan oleh orang tidak dikenal. Bantulah perusahaan tersebut untuk melacak jejak yang ditinggalkan oleh attacker.

Step pengerjaan :
1. Follow packet teratas
2. dislay filter ``` frame contains "email" ```
nc 10.15.42.60 51000

![WhatsApp Image 2024-09-18 at 22 44 01_35d2499f](https://github.com/user-attachments/assets/d91bc4a8-1399-4d14-b3bd-e067c4bc43ca)

### Pegawai Negeri Sebelah
Kamu seorang data analisis diminta untuk memastikan ulang data-data dari beberapa pegawai

Step pengerjaan :
1. display filter ``` frame contains "nNnM%coQuF" ```
2. Follow stream lalu gunakan shortcut ``` CTRL+F ``` untuk mencari jawaban
nc 10.15.42.60 53000

![WhatsApp Image 2024-09-18 at 22 44 01_8da370bc](https://github.com/user-attachments/assets/2c26ede1-a555-4c49-94ab-06aaaa943449)

### EZ
Aku sedang mencoba bikin chat service tapi kayanya pesannya bisa di sniffing deh? coba temukan pesannya.

Step pengerjaan :
1. Follow stream packet TCP paling atas
2. Open packet TCP paling atas untuk melihat ip.dst
nc 10.15.42.60 54000

![WhatsApp Image 2024-09-18 at 22 44 01_83abf77f](https://github.com/user-attachments/assets/eda637a7-beb5-49ec-8674-9acf7237937b)

#### Rizzset
Aku sedang bereksperimen dengan suatu tools, kamu juga bisa menggunakannya untuk menjawab soal ini

Step pengerjaan :
1. display filter ``` frame contains www ```
2. Masukkan domain www.its.ac.id ke tools JARM
nc 10.15.42.60 59500

![WhatsApp Image 2024-09-18 at 22 44 03_cc8544f4](https://github.com/user-attachments/assets/f6e33805-2da6-46c0-bbb5-fe1ca853c4bd)

### Malicious Code
Ternyata sang attacker dengan sengaja meninggalkan sesuatu untuk dibaca oleh kamu. Lihat pesan apa yang ditinggalkan attacker.
File sama seperti Corporate Breach.

Step pengerjaan :
1. display filter ``` frame contains "login" ```
2. display filter ``` http && frame contains "Not Found" ```
3. Sort berdasarkan time dan kurangkan dengan beberapa packets yang mengambil waktu yang melebihi waktu rata-rata
4. display filter ``` http.request ``` >> Follow stream ke packet yang memiliki length berbeda dengan packet lain
5. display filter ``` http.request.method == "POST" ``` >> Lihat displayed
6. Lihat 5 packet terakhir yang memiliki length yang berbeda >> Follow HTTP stream
7. Dekripsi menggunakan ASCII decoder
nc 10.15.42.60 52000

![WhatsApp Image 2024-09-18 at 22 44 02_08ad1469](https://github.com/user-attachments/assets/99541780-f751-4fae-9e24-adb0ee2b5788)

### 22 Nightmare
Dicari rusa yang hilang.

Step pengerjaan :
1. display filter ``` ftp-data.command contains "STOR" ```
2. Export file Sh1k4.jpg & noko.py
3. Open file Sh1k4.jpg terdapat hidden message "NUN"
4. Open file noko.py dan masukkan NUN sebagai key input dan lakukan operasi XOR
nc 10.15.42.60 45000

![WhatsApp Image 2024-09-18 at 22 44 03_0b24f451](https://github.com/user-attachments/assets/802b9872-421b-4bed-a6ce-064296aff1a4)

### Gajah Terbang < Server Connect >
Pada perusahaan PT. +1000 Aura telah terjadi insiden yang besar, dimana seorang hengker berhasil masuk ke sistem database perusahaan tersebut, dan melakukan manipulasi sistem database mereka. Anda sebagai profesional Cyber Security Analyst ditugaskan untuk melakukan investigasi melalui log network yang berhasil tercapture!

nc 10.15.42.60 61000 


![Screenshot from 2024-09-18 11-41-19](https://github.com/user-attachments/assets/12aa7e58-411d-47b1-9cdc-bdd1e224059f)

![Screenshot from 2024-09-18 11-41-44](https://github.com/user-attachments/assets/f8ebf7d3-f732-4b80-ae1f-ad4319beba0d)

![Screenshot from 2024-09-18 11-46-11](https://github.com/user-attachments/assets/41cd7081-c8d0-4887-93d6-bbca89ba23c2)


![Screenshot from 2024-09-18 11-41-59](https://github.com/user-attachments/assets/e22c29d2-fd74-41d2-b742-16e6c66a48ab)

![Screenshot from 2024-09-18 13-46-04](https://github.com/user-attachments/assets/3f79a139-39f6-421b-b4ba-2795a5d3d792)

#### Langkah - langkah 
- kita filter dengan 'tcp.stream eq 3'
- lalu masukkan port "6969' sebagai jawaban di pertanyaan
- lalu kita filter lagi "tcp.stream eq 9" dibagian itu kita follow dan menemukan beberapa jawaban untuk pertanyaan selanjutnya
- untuk pertnyaan terakhir mengenai passworde, awalnya di decrypt dulu trus baru di submit

  
### Gajah Terbang < Attacker Recon >
Setelah berhasil menginvestigasi server yang berjalan, kamu diharuskan untuk mencari identitas dan mencari jejak apa saja yang telah dilakukan oleh penyerang! Kamu jago, pasti bisa let’s go temukan tersangkanya!!!
File sama seperti Gajah Terbang.

nc 10.15.42.60 62000 

![Screenshot from 2024-09-18 13-41-58](https://github.com/user-attachments/assets/5451bccc-d412-4362-9e1d-91305aeead32)

#### Langkah - Langkah
- tetep pada tcp stream eq 9 tadi, semua jawaban ada dibagian itu
- lalu ada pertanyaan yang harus di decrypt terlebih dahulu.

### InnerCE
omg, SIEM mendeteksi adanya serangan hacker yang berhasil mengupload webshell. sebagai analyst yang jago, kamu diharuskan membuat laporan insiden tersebut
nc 10.15.42.60 56000 

![Screenshot from 2024-09-22 05-50-05](https://github.com/user-attachments/assets/2b40c331-154a-4d00-8cfc-4535a683ad00)

![Screenshot from 2024-09-22 10-33-07](https://github.com/user-attachments/assets/c13a5661-0995-47d3-bc3e-0075d3a36330)
![Screenshot from 2024-09-22 10-35-10](https://github.com/user-attachments/assets/bbe3f140-42a9-404b-9e7e-429fe5ddc906)
![Screenshot from 2024-09-22 10-36-56](https://github.com/user-attachments/assets/ba22f68f-be33-446a-a9f7-c6d85394c48d)
![Screenshot from 2024-09-22 10-41-49](https://github.com/user-attachments/assets/4ecf7870-7709-487f-b56a-e4e37adac1e2)
