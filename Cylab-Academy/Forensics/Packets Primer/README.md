# Packets Primer - Forensics

> **Author:** Zenka Yahuda Kurnia Putra  
> **Challenge:** Network Traffic Analysis & Packet Capture Investigation  
> **Platform:** Cylab Security Academy
---
<img width="835" height="528" alt="Screenshot From 2026-10-10 15-56-19" src="https://github.com/user-attachments/assets/fc7c0920-db09-46f6-96d7-193b318a2796" />

---

## Executive Summary

Pada tantangan Network Forensics ini, saya diberikan sebuah file penangkapan paket jaringan `(.pcap)` yang di dalamnya menyimpan informasi rahasia. Tugasnya adalah menganalisis lalu lintas jaringan tersebut menggunakan tool `Wireshark` untuk menemukan keberadaan flag yang tersembunyi

---

## Technical Report

Saya mengunduh file `(.pcap)` tersebut lalu membukanya melalui `Wireshark`. Pada tahap awal pencarian, saya sempat mencoba melakukan pencarian string teks yakni menggunakan pintasan `Ctrl + F` dengan kata kunci `Flag` dan `Academy`. Namun, pencarian tersebut tidak membuahkan hasil

<img width="1920" height="1080" alt="Screenshot From 2026-10-10 16-03-38" src="https://github.com/user-attachments/assets/a06bbc30-823a-4246-b119-f871aba0c2de" />

Karena step pertama gagal, saya beralih memeriksa salah satu paket protokol TCP yang terekam. Saya mengklik kanan pada salah satu paket TCP tersebut, lalu memilih opsi `Follow` dan melanjutkan ke `TCP Stream`

<img width="1175" height="816" alt="Screenshot From 2026-10-10 16-03-59" src="https://github.com/user-attachments/assets/89a8a382-033f-4a40-8082-d89df36c4d9d" />

Ketika jendela TCP Stream terbuka, saya langsung menemukan teks flag yang terekam secara jelas di dalam aliran data jaringan tersebut tanpa terenkripsi

<img width="1175" height="816" alt="Screenshot From 2026-10-10 16-04-56" src="https://github.com/user-attachments/assets/f3131b11-c600-4e0e-8e38-79687c44294f" />

--- 

## Conclusion
File packet capture `(.pcap)` sering kali merekam komunikasi data mentah (plaintext) yang melintasi jaringan. Dengan memanfaatkan fitur `Follow TCP Stream` di Wireshark, saya dapat merekonstruksi percakapan atau aliran data TCP dengan mudah dan berhasil mendapatkan flag yang disembunyikan

---

## Flag

```text
academy{p4ck37_5h4rk_5b0c3582}
