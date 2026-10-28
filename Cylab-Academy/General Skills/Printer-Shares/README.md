# Printer Shares - General Skills

> **Author:** Zenka Yahuda Kurnia Putra <br>
> **Challenge:** SMB Anonymous Enumeration & Misconfigured File Sharing <br>
> **Platform:** Cylab Security Academy

---

<img width="828" height="670" alt="Screenshot From 2026-10-28 22-11-51" src="https://github.com/user-attachments/assets/205ec915-62fe-4431-9380-76fcf442fb5b" />

---

## Executive Summary

Diberikan sebuah layanan berbagi file berbasis SMB (Server Message Block) pada sebuah perangkat printer jaringan. Disini, saya mengeksploitasi konfigurasinya yang rentan berupa akses tamu (guest access) yang dibiarkan terbuka secara publik tanpa memerlukan kata sandi, ini memungkinkan Attacker untuk melakukan enumerasi folder dan mengunduh file sensitif secara langsung

---

## Technical Report

Pertama, saya melakukan koneksi ke Netcatnya, supaya saya bisa terhubung dengan SMB nya, setelah itu, saya melakukan koneksi ke SMB nya untuk melihat apa isi dari SMB tersebut, caranya dengan perintah : 
```text
smbclient -L //<host> -p <port> -N #ketik sudo apt install smbclient kalau belum punya
```

`-L` sendiri disini artinya ialah List, yakni saya akan melihat list isi dari SMB nya, dan `-N` disini artinya adalah No password, alias anonymous login

<img width="1117" height="411" alt="Screenshot From 2026-10-28 22-15-09" src="https://github.com/user-attachments/assets/bf983381-f711-4015-bc90-ac6c91b60e11" />

Setelah mengetahui isinya bahwa ada Disk shares disana, saya langsung mengganti perintah smbclient nya dengan perintah berikut : 
```text
smbclient //<host>/shares -p <port> -N
```

Setelah itu, saya mengecek isinya dengan perintah `ls`, dan benar aja, disana terdapat `flag.txt`, tanpa pikir panjang, saya langsung memasukkan perintah `get` untuk mengambil flagnya
```text
get flag.txt
```

<img width="1067" height="360" alt="Screenshot From 2026-10-28 22-15-25" src="https://github.com/user-attachments/assets/41a90fe9-8c9e-45fe-ad1b-dc8066a1cdc2" />

Setelah itu, exit SMB nya kemudian buka isi `flag.txt` nya dengan perintah `cat`, disana saya mendapatkan flagnya

<img width="535" height="211" alt="Screenshot From 2026-10-28 22-15-37" src="https://github.com/user-attachments/assets/9d22f0ad-78f8-483a-a97f-d52d6c485da0" />

---

## Conclusion

Kesalahan terbesar pada layanan SMB ini adalah buruknya konfigurasi kontrol akses layanan, yang mengizinkan akses anonim (anonymous/guest login) boleh masuk tanpa password. Mirisnya, perangkat jaringan seperti printer kantor sering kali luput dari pengawasan keamanan dan sering menyimpan data sensitif. Administrator harus selalu memastikan untuk menonaktifkan fitur guest share, menerapkan autentikasi kredensial yang ketat, serta membatasi akses jaringan agar direktori bersama tidak terekspos secara bebas ke publik

---

## Flag

```text
academy{5mb_pr1nter_5h4re5_6f6353d3}
