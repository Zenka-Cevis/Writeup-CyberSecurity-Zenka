# ping-cmd - General Skills

> **Author:** Zenka Yahuda Kurnia Putra <br>
> **Challenge:** Command Injection via Shell Chaining <br>
> **Platform:** Cylab Security Academy

---

<img width="831" height="661" alt="Screenshot From 2026-10-25 18-24-15" src="https://github.com/user-attachments/assets/e36e51c3-096e-46f7-823e-600bc08a3e05" />

---

## Executive Summary

Diberikan sebuah layanan remote berbasis teks (netcat) yang memiliki fungsi utama untuk melakukan `ping` ke IP address tertentu seperti `8.8.8.8`. Namun, setelah dilakukan analisa lebih mendalam, aplikasi server ini mengeksekusi perintah shell tanpa adanya sanitasi karakter khusus secara aman. Kerentanan Command Injection ini dapat dieksploitasi menggunakan *command chaining* yakni pemisah perintah `;` untuk mengeksekusi perintah sistem tambahan dan membaca isi file `flag.txt`

---

## Technical Report

Pertama, saya melakukan koneksi ke server menggunakan `netcat` pada alamat `xebec.cylabacademy.net` port `23799`. Di sana terdapat informasi bahwa server secara ketat hanya mengizinkan input `8.8.8.8`

Saya menduga filter keamanan yang diterapkan hanya memeriksa keberadaan substring `8.8.8.8` pada input tanpa memblokir karakter khusus shell seperti titik koma `;`. Nahh, untuk membuktikannya, saya mencoba menyisipkan perintah `ls` setelah input IP dengan format 
```text
8.8.8.8; ls
```

Ternyata benar, perintah `ping` berjalan normal dan langsung dilanjutkan dengan eksekusi `ls`, yang menampilkan isi direktori server yaitu file `flag.txt` dan `script.sh`

Setelah mengonfirmasi adanya kerentanan Remote Code Execution (RCE), saya langsung menjalankan perintah `cat flag.txt` dengan menyisipkannya kembali menggunakan format `8.8.8.8; cat flag.txt`. Begitu dijalankan, isi file `flag.txt` langsung tercetak di terminal dan saya mendaptkan flagnya
```text
8.8.8.8; cat flag.txt
```

<img width="1101" height="868" alt="Screenshot From 2026-10-25 18-28-00" src="https://github.com/user-attachments/assets/eabc4bf0-5ca7-48cd-b8ae-58fd070dcbd6" />

---

## Conclusion

Jangan pernah mengeksekusi input pengguna secara langsung ke dalam perintah shell sistem tanpa adanya sanitasi yang ketat. Pengecekan substring sederhana aja ga cukup untuk mencegah *Command Injection*. Developer harus selalu memvalidasi input menggunakan *whitelisting* secara ketat (misalnya format regex IPv4) atau menggunakan API eksekusi bawaan yang memisahkan argumen dari shell loader seperti `subprocess` tanpa `shell=True`

---

## Flag

```text
academy{p1nG_c0mm@nd_3xpL0it_su33essFuL_fe3fac88}
