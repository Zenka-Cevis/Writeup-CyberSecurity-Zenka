# Riddle Registry - Forensics

> **Author:** Zenka Yahuda Kurnia Putra <br>
> **Challenge:** Information Disclosure using `Exiftool` <br>
> **Platform:** Cylab Security Academy

---
<img width="832" height="562" alt="Screenshot From 2026-10-16 09-13-01" src="https://github.com/user-attachments/assets/1c827bff-e570-4197-a2a7-f4f4b8322b15" />

---

## Executive Summary

Diberikan sebuah file berjenis pdf yang dimana file tersebut menyimpan informasi rahasia berupa flag, namun flag tidak langsung muncul begitu saja, melainkan harus dicari lebih detail yaitu menggunakan `Exiftool`

---

## Technical Report

Download file PDF nya, saat saya melihat isi file pdf nya, disana terdapat teks yang ditutupi warna hitam :v 

<img width="1920" height="1080" alt="Screenshot From 2026-10-16 09-12-41" src="https://github.com/user-attachments/assets/59a9690c-7de3-4fa0-ad4f-0266b20a6701" />

Namun clue bilang, jangan terkecoh dengan isi file nya, jadi langkah awal yang saya lakukan adalah mencari tahu informasi akan file tersebut, saya menggunakan `Exiftool` untuk melihat tentang file tersebut, dan benar saja, disana saya menemukan string `Base64` yang kemungkinan adalah petunjuk dari si flag atau mungkin flagnya langsung

<img width="921" height="543" alt="Screenshot From 2026-10-16 09-13-49" src="https://github.com/user-attachments/assets/a635f592-0784-4e86-9111-e77ce8786f3c" />

Saya copy string tersebut kemudian saya membawanya ke Cyberchef, menggunakan resep `From base64` disana saya langsung mendapatkan flagnya

<img width="1208" height="583" alt="Screenshot From 2026-10-16 09-14-15" src="https://github.com/user-attachments/assets/9e2ddf75-1305-43e1-89a8-8ea6b2b56df4" />

---

## Conclusion
Jangan simpan informasi sensitif ke dalam file, karena itu bisa di lihat menggunakan tool seperti `Exiftool`, kreator harus selalu menerapkan praktik higienitas data, seperti melakukan pembersihan metadata `(metadata stripping)` sebelum mempublikasikan file atau dokumen ke ranah publik. supaya tidak ada informasi privat yang bocor ke tangan pihak luar


---

## Flag

```text
academy{puzzl3d_m3tadata_f0und!_4770d4ec}
