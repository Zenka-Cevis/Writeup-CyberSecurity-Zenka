# hideme - Forensics

> **Author:** Zenka Yahuda Kurnia Putra <br>
> **Challenge:** Steganography using `zsteg` & `strings` <br>
> **Platform:** Cylab Security Academy

---
<img width="836" height="420" alt="Screenshot From 2026-10-21 22-55-06" src="https://github.com/user-attachments/assets/a8aef45a-221e-40e0-a03b-4e7a01d90dc7" />

---

## Executive Summary

Diberikan sebuah file berjenis `.png`, yang dimana file tersebut terlihat seperti gambar biasa, namun setelah dilakukan analisa lebih mendalam, disana terdapat data tersembunyi berupa arsip ZIP di bagian trailer filenya, yang dapat diekstrak atau dibaca langsung menggunakan string mentah untuk mendapatkan flag

---

## Technical Report

Pertama, download file png nya, kemudian saya memeriksa jenis file tersebut menggunakan perintah `file` dan menganalisis metadatanya menggunakan `exiftool`. Dari hasil pengecekan, terdapat peringatan bahwa ada data tambahan `(trailer data)` yang menempel setelah chunk akhir PNG

<img width="775" height="727" alt="Screenshot From 2026-10-21 22-57-16" src="https://github.com/user-attachments/assets/4ac59c3f-9a7b-4e6f-a876-b4068a8dd12d" />

Karena saya masih penasaran, saya mencoba menjalankan tool `zsteg` untuk melihat apakah ada data tersembunyi di dalam pixel gambar tersebut. Ternyata, benar saja, zsteg mendeteksi adanya arsip ZIP yang disisipkan pada bagian extradata lengkapnya dengan struktur direktori `secret/flag.png` di dalamnya.

<img width="1663" height="506" alt="Screenshot From 2026-10-21 22-57-39" src="https://github.com/user-attachments/assets/6a1072d6-9d6f-4e2d-86d3-a9fe8941734f" />

Secara prosedur forensik standar, data tersebut seharusnya dipisahkan kemudian di-unzip. Namun, karena data ZIP tersebut menempel langsung di bagian ujung file, saya langsung terbesit untuk menggunakan perintah `strings` agar lebih cepat. Begitu dijalankan, flag langsung muncul tanpa perlu repot-repot mengekstrak file ZIPnya

<img width="685" height="823" alt="Screenshot From 2026-10-21 22-57-55" src="https://github.com/user-attachments/assets/a1f51619-febe-467d-bb81-45e495f4ca08" />

---

## Conclusion
Jangan pernah menyisipkan file rahasia atau arsip tersembunyi di dalam file gambar, karena data tersebut sangat mudah dibaca menggunakan tools dasar seperti strings atau dianalisis lewat zsteg. Pembuat harus selalu memastikan kebersihan file dari data-data sisa, sebelum dibagikan ke publik

---

## Flag

```text
academy{Hiddinng_An_imag3_within_@n_ima9e_c55a7afe}
