# Hashcrack - Cryptography

> **Author:** Zenka Yahuda Kurnia Putra <br>
> **Challenge:** Hash Cracking & Dictionary Attack using `John The Ripper` <br>
> **Platform:** Cylab Security Academy

---
<img width="811" height="693" alt="Screenshot From 2026-10-13 11-03-51" src="https://github.com/user-attachments/assets/c08ee533-661b-41cc-ac5f-cb43f67ad251" />

---

## Executive Summary

Diberikan akses ke sebuah layanan jaringan berbasis `Netcat`, di mana sistem menyediakan beberapa string hash yaitu MD5, SHA-1, dan SHA-256 dari kata sandi yang lemah. Tantangan ini memungkinkan saya untuk melakukan serangan dictionary attack menggunakan Tool `John the Ripper`, sehingga saya dapat membongkar nilai hash tersebut dan mendapatkan flagnya

---

## Technical Report

Lakukan koneksi dengan `netcat`, disana saya dihadapkan dengan kode hash yang mana itu adalah passwordnya untuk melanjutkan langkah selanjutnya
```text
482c811da5d5b4bc6d497ffa98491e38
```

<img width="618" height="173" alt="Screenshot From 2026-10-13 11-07-15" src="https://github.com/user-attachments/assets/ea6c38ce-ad3d-4575-bd1c-a97c12f8fdaf" />

Copy kode hash itu, kemudian saya membawa nya ke `hash identifier` untuk mencari tahu jenis hash yang digunakan sebelum melakukan serangan dictionary attack, disana saya mendapatkan informasi bahwa kode hash itu berjenis MD5

<img width="672" height="143" alt="Screenshot From 2026-10-13 11-07-31" src="https://github.com/user-attachments/assets/56afca53-9ab6-437b-898b-9485ba3cdc75" />

Setelah tau jenis hash tersebut, saya membuka terminal, kemudian paste hash itu kedalam file txt, lalu lakukan serangan dictionary attack menggunakan tool `John The Ripper`, tepat disana, saya mendapatkan passwordnya yaitu `password123`
```text
$ john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash1.txt 
```

Setelah mensubmit langkah pertama, saya dihadapkan lagi kode hash yang kedua, seperti langkah pertama, saya melakukan identifikasi jenis hash menggunakan `hash identifier`, disana saya mendapatkan informasi bahwa hash tersebut menggunakan jenis `SHA1`
```text
b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3
```
<img width="888" height="278" alt="Screenshot From 2026-10-13 11-08-11" src="https://github.com/user-attachments/assets/70e8fdd9-3c46-4504-89a5-9e79a4158b21" />
<img width="847" height="133" alt="Screenshot From 2026-10-13 11-08-38" src="https://github.com/user-attachments/assets/f290fa43-47d8-4c57-ab49-0ca718d40677" />

Lakukan serangan dictionary attack menggunakan `John`, disana saya mendapatkan passwordnya yaitu `letmein`
```text
$ john --format=Raw-SHA1 --wordlist=/usr/share/wordlists/rockyou.txt hash2.txt 
```

<img width="920" height="322" alt="Screenshot From 2026-10-13 11-09-21" src="https://github.com/user-attachments/assets/5138ca25-1746-4b04-b1e7-4555558574fb" />

Terakhir, saya diberikan kode hash lagi, tanpa pikir panjang, saya bawa ke `hash identifier`, disana saya mendapatkan informasi bahwa hash tersebut menggunakan jenis SHA-256
```text
916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745
```

<img width="986" height="353" alt="Screenshot From 2026-10-13 11-10-22" src="https://github.com/user-attachments/assets/0d2c5d37-4080-4aa0-8602-983bfcea71bd" />
<img width="983" height="123" alt="Screenshot From 2026-10-13 11-10-43" src="https://github.com/user-attachments/assets/103bac5f-2e92-4449-8385-01f2eb8e0054" />

Lakukan serangan dictionary attack menggunakan `John`, disana saya mendapatkan passwordnya yaitu `qwerty098`
```text
$ john --format=Raw-SHA256 --wordlist=/usr/share/wordlists/rockyou.txt hash3.txt
```

<img width="985" height="333" alt="Screenshot From 2026-10-13 11-12-04" src="https://github.com/user-attachments/assets/ba39d71a-bff6-4f97-b8ae-4d53dbfaec96" />

Setelah berhasil ketiganya, saya mendapatkan flagnya

<img width="973" height="405" alt="Screenshot From 2026-10-13 11-12-33" src="https://github.com/user-attachments/assets/ac7387c4-b0c0-4f09-b0e0-dc369905ef90" />

---

## Conclusion
Hash yang kuat tidak menjamin aman jika passwordnya mudah, gunakan lah kombinasi hash yang kuat, namun tetap menggunakan password yang sulit supaya lebih aman

---

## Flag
```text
academy{UseStr0nG_h@shEs_&PaSwWDs!_35c6b1f4}
