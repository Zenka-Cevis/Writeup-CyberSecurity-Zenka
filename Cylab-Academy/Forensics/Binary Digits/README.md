# Binary Digits - Forensics

> **Author:** Zenka Yahuda Kurnia Putra  
> **Challenge:** Raw Binary Data Visualization & Image Recovery  
> **Platform:** Cylab Security Academy
---
<img width="846" height="482" alt="Screenshot From 2026-10-10 14-23-54" src="https://github.com/user-attachments/assets/d1e3536a-794a-4560-8206-7cbda6223a67" />

---

## Executive Summary

Diberikan sebuah file bernama `digits.bin` yang berisi deretan kode binary sangat panjang yang hanya terdiri dari angka 0 dan 1. Tugas nya adalah menganalisis serta mendecode file tersebut untuk mengungkap informasi berupa flag

---

## Technical Report

Saya mendownload file binary tersebut, kemudian saya menganalisa file itu, setelah saya buka, ternyata isi di dalamnya hanya berupa string binary mentah yang sangat panjang tanpa format teks yang bisa terbaca

<img width="1113" height="530" alt="Screenshot From 2026-10-10 14-59-51" src="https://github.com/user-attachments/assets/e020d146-9fa3-4760-85d3-966cc05121c4" /> 

Tanpa pikir panjang, saya membawa file tersebut ke platform `CyberChef` untuk dianalisis lebih lanjut. Di sana, saya menambahkan operasi `From Binary` dan dilanjut dengan `Render Image`. dan hasilnya menunjukkan bahwa kode binary tersebut ternyata menghasilkan sebuah image, yang dimana image nya berisikan sebuah flag

<img width="1541" height="948" alt="Screenshot From 2026-10-10 14-36-42" src="https://github.com/user-attachments/assets/35cc0448-3c19-4703-8222-58b214fecc72" />

Setelah itu, saya mendownload image nya agar bisa dibaca dengan jelas, dan saya mendapatkan flagnya

<img width="576" height="345" alt="Screenshot From 2026-10-10 14-37-14" src="https://github.com/user-attachments/assets/119f6f4e-8cd0-4e08-a3e4-f8a37201b652" /> 

--- 

## Conclusion
Deretan data biner mentah (0 dan 1) dalam file `digits.bin` pada dasarnya adalah representasi byte dari sebuah file gambar. Dengan menggunakan tool seperti `Cyberchef` dan menerapkan operasi konversi biner ke bentuk gambar (render image), saya berhasil mengekstrak isi file tersembunyi tersebut dan mendapatkan flag-nya

---

## Flag

```text
academy{h1dd3n_1n_th3_b1n4ry_1b150ee9}
