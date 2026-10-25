# Flag Hunters - Reverse Engineering

> **Author:** Zenka Yahuda Kurnia Putra  
> **Challenge:** Control flow injection  
> **Platform:** Cylab Security Academy
---
<img width="822" height="646" alt="Screenshot From 2026-10-14 10-15-00" src="https://github.com/user-attachments/assets/3cf6bdfa-749c-48eb-bb0e-9ba8e384ce3d" />

---

## Executive Summary

Diberikan sebuah program berbasis teks yang memproses lirik dan input pengguna, di mana program tersebut memiliki kerentanan akibat tidak adanya sanitasi pada input user. Kerentanan ini memungkinkan saya untuk menyisipkan perintah `control flow injection`, sehingga saya dapat memanipulasi penunjuk baris `(instruction pointer)` untuk melompat ke bagian awal program dan mengambil flag, karena flagnya tersimpan di bagian awal program

---

## Technical Report

Saya mendownload file source code program yang diberikan, dan melakukan analisa pada codenya, disana saya menemukan titik krusial, yang dimana ini bisa menyebabkan seseorang melakukan serangan `control flow injection`
```text
elif re.match(r"CROWD.*", line):
    crowd = input('Crowd: ')
    song_lines[lip] = 'Crowd: ' + crowd
```

Disana, program menerima apapun yang user ketik melalui fungsi `input()` tanpa ada proses penyaringan (sanitization), pembersihan karakter, atau pengecekan apakah input mengandung simbol berbahaya. Input user langsung digabungkan ke dalam elemen `array song_lines`

Kemudian, Program juga memiliki fitur untuk memecah kalimat berdasarkan tanda titik koma (;) supaya bisa menjalankan beberapa instruksi dalam satu baris. Karena input user digabungkan lebih dulu ke dalam baris tersebut, tanda titik koma apa pun yang user ketik akan ikut diproses sebagai pemisah perintah oleh program
```text
for line in song_lines[lip].split(';'):
```

Tanpa pikir panjang, saya melakukan koneksi `Netcat` ke program nya, disana saya diminta memasukkan input ke dalam variabel `Crowd`, karena flag tersimpan di program bagian awal, saya cukup memerintahkan program untuk pergi ke bagian awal dengan cara mengetik : 
```text
;RETURN 0
```

<img width="587" height="467" alt="Screenshot From 2026-10-14 10-16-57" src="https://github.com/user-attachments/assets/e4348fb3-dc99-4a7b-884c-5e0b76287145" />

Setelah itu program akan memproses permintaan saya dan saya mendapatkan flagnya

<img width="655" height="391" alt="Screenshot From 2026-10-14 10-17-44" src="https://github.com/user-attachments/assets/d445fb74-6bc7-4eaf-a33c-7deef091bb0a" />

--- 

## Conclusion
Kelalaian dalam memvalidasi input teks yang dimasukkan oleh user sangat berbahaya. Dengan memanfaatkan celah `control flow injection` melalui karakter pemisah `;` untuk mengeksekusi instruksi lompatan kembali ke baris awal `;RETURN 0`, saya berhasil memotong alur eksekusi normal program dan mendapatkan flagnya

---

## Flag

```text
academy{70637h3r_f0r3v3r_4943a085}
