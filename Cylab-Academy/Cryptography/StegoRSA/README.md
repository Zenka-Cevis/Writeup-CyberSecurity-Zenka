# StegoRSA - Cryptography

> **Author:** Zenka Yahuda Kurnia Putra <br>
> **Challenge:** Steganography Extraction & RSA Decryption <br>
> **Platform:** Cylab Security Academy

---
<img width="823" height="530" alt="Screenshot From 2026-10-20 15-30-39" src="https://github.com/user-attachments/assets/e9f424b0-6bc7-458a-b6ea-7ff10e0a767f" />

---

## Executive Summary
Diberikan dua buah file: pertama `flag.enc` yang berisi file flag terenkripsi, dan kedua `image.jpg` yang menyembunyikan private key dalam format terencode di dalam metadatanya. Setelah private key diekstrak dan didecode, kunci tersebut digunakan untuk mendekripsi `flag.enc` guna mendapatkan flagnya

---

## Technical Report

Download kedua file nya, disana saya mendapatkan 2 buah file, pertama `flag.enc` dan kedua adalah `image.jpg` dimana setelah dilihat gambarnya, itu cuman foto kunci doank tanpa petunjuk

Tanpa pikir panjang, saya ingin melihat metadata `image.jpeg` menggunakan tool `Exiftool` dan disana saya menemukan sebuah encode yang cukup mencurigakan di bagian comment nya

<img width="1920" height="1080" alt="Screenshot From 2026-10-20 15-31-12" src="https://github.com/user-attachments/assets/c8ab4ec5-d5e9-406e-90cf-8aa5fd726ff2" />

Saya copy encode itu dan membawanya ke `Cyberchef` disana saya mendapatkan `private key` yang diduga adalah kunci untuk mendekripsinya dan mendapatkan flagnya di dalam file `flag.enc`

<img width="1920" height="1080" alt="Screenshot From 2026-10-20 15-32-03" src="https://github.com/user-attachments/assets/23aa334e-96de-4fa9-ae30-8064a69fcec5" />

Saya copy private key itu, lalu memasukkannya nya ke dalam file txt

<img width="557" height="170" alt="Screenshot From 2026-10-20 15-35-45" src="https://github.com/user-attachments/assets/d9fe0e35-993f-44dc-b4ac-adba74df8e89" />

Kemudian saya mencari tahu di internet, cara decrypt sebuah file yang menyimpan sesuatu dimana private key nya sudah diketahui menggunakan `openssl`

<img width="850" height="506" alt="Screenshot From 2026-10-20 15-43-13" src="https://github.com/user-attachments/assets/abee58fc-a9a9-4a3a-83ae-45cc28db5caa" />

Setelah mengetahuinya, saya membuka terminal dan memasukkan command berikut : 
```text
openssl pkeyutl -decrypt -inkey <private.key> -in <file yang menyimpan flag> -out <isi dari file yang menyimpan flag>
Contoh : openssl pkeyutl -decrypt -inkey enkrip.txt -in flag.enc -out flag.txt
```

Setelah saya jalankan commandnya, saya mendapatkan flagnya

<img width="876" height="248" alt="Screenshot From 2026-10-20 15-42-38" src="https://github.com/user-attachments/assets/43674a7f-fcb8-4605-b287-f03082955db3" />

---

## Conclusion
Jangan menyimpan private key di metadata sebuah file, karena private key itu sifatnya sensitif dan bahaya jika tersebar

---

## Flag
```text
academy{rs4_k3y_1n_1mg_21d0a083}
