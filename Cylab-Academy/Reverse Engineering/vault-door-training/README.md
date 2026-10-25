# vault-door-training - Reverse Engineering

> **Author:** Zenka Yahuda Kurnia Putra  
> **Platform:** Cylab Security Academy
---
<img width="826" height="517" alt="Screenshot From 2026-10-14 15-24-25" src="https://github.com/user-attachments/assets/8388b917-c700-4721-b987-48f06f790407" />

---

## Executive Summary

Diberikan sebuah file yang dimana disana terdapat flag yang disembunyikan tanpa encode ataupun sesuatu yang menutupi flagnya

---

## Technical Report

Saya mendownload filenya, kemudian memeriksa jenis file nya terlebih dahulu 

<img width="642" height="166" alt="Screenshot From 2026-10-14 15-30-40" src="https://github.com/user-attachments/assets/6d149344-a410-4a56-9d8c-0416e2011eb4" />

Setelah mengetahui jenis file nya, saya membuka file tersebut di `VSCode` guna melihat isi dari file tersebut, namun secara tidak sengaja saya menemukan password atau flagnya yang tidak terbungkus apapun, jadi flag benar benar muncul secara mentah mentah

<img width="908" height="697" alt="Screenshot From 2026-10-14 15-30-53" src="https://github.com/user-attachments/assets/0144fd03-dc36-4154-93da-6dacad9913cf" />

Ambil flag tersebut, kemudian tinggal tambahkan format flagnya yaitu `academy{flag}` dan lab berhasil diselesaikan

--- 

## Conclusion
Jangan menaruh informasi sensitif di source code secara terang terangan

---

## Flag

```text
academy{w4rm1ng_Up_w1tH_jAv4_4cfa5369b93}
