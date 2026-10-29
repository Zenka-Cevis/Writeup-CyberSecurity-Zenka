# PcapPoisoning - Forensics

> **Author:** Zenka Yahuda Kurnia Putra <br>
> **Challenge:** Network Traffic Analysis & PCAP Inspection <br>
> **Platform:** Cylab Security Academy

---

<img width="840" height="517" alt="Screenshot From 2026-10-29 14-32-54" src="https://github.com/user-attachments/assets/f2fe8437-9a8e-4e61-97ce-70bf095a378d" />

---

## Executive Summary

Diberikan sebuah file pcap alias Packet Capture yang merekam lalu lintas sebuah jaringan. challange ini menuntut saya untuk menganalisis secara mendalam terhadap paket data tersebut untuk menemukan informasi sensitif seperti flag yang tersembunyi di dalam aliran komunikasi jaringan tersebut

---

## Technical Report

Pertama, saya mendownload file pcap nya, kemudian saya membuka file itu menggunakan tool `Wireshark`, pada halaman awal, saya tidak menemukan sesuatu yang menyimpan informasi sensitif, bahkan saat saya follow streamnya, saya ga nemu apa apa

<img width="1920" height="1080" alt="Screenshot From 2026-10-29 14-33-16" src="https://github.com/user-attachments/assets/54ddd3ff-c2b9-4b88-8e7a-529beffed16b" />

Sampai akhirnya saya terus scrolling ke bawah, dan menemukan protokol TCP yang cukup mencurigakan, soalnya warna nya berwarna merah, saya ga tau itu error atau kenapa dan itu panjang sekali, nah tepat pada bagian atasnya, saya nemu flag nya, tapi karena ribet buat di copy, disini saya memanfaatkan fitur `strings` pada filenya 

<img width="1920" height="575" alt="Screenshot From 2026-10-29 14-34-14" src="https://github.com/user-attachments/assets/09e694db-6bd1-415c-9a4a-830f4fb3f9b7" />

Masuk ke terminal tempat si file pcap berada, kemudian saya mengetik perintah berikut : 
```text
strings trace.pcap | grep "academy"
```

Setelah saya memasukkan perintah tersebut, saya mendapatkan flagnya

<img width="696" height="107" alt="Screenshot From 2026-10-29 14-35-25" src="https://github.com/user-attachments/assets/38dd8daa-079c-4966-b7bd-326c7e435229" />

---

## Conclusion
Kerentanan pada challange ini murni terletak pada pengiriman data yang tidak terenkripsi `plaintext traffic` di dalam jaringan, sehingga informasi sensitif seperti kredensial atau flag dapat dibaca dengan mudah menggunakan teknik ekstraksi string sederhana atau analisis paket via `Wireshark`. Pengamanan jaringan modern sekarang mewajibkan penggunaan enkripsi transport layer seperti TLS/SSL supaya mencegah pengintaian data (packet sniffing), simpelnya seperti HTTPS pada sebuah web, bukan HTTP :)

---

## Flag

```text
academy{P64P_4N4L7S1S_SU55355FUL_7a51913b}
