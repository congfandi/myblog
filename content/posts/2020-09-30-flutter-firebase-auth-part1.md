---
title: Flutter Firebase Auth Part 1 - Config Project #judul postingan
img:  200920/cover1.jpg #gambar postingan taruh di assets/img dan langsung call nama imagenya
layout: post #default jangan diganti
author: Cong Fandi #default me
author-img : congfandi.jpeg #default me
author-detail : iOS Developer, Android Developer, Web Developer # default me
fig-caption: Developer #default me
tags: # tags dalam array [Developer, Web, Tips]
---

Hola sobat Ngoding yang budiman (Manusia Budi wkwkw), kali ini yuk kita main main dengan firebase. ini bisa kalian gunakan saat kalian ingin membuat aplikasi kalian harus ada login tapi kalian tidak memiliki team backend untuk mengerjakannya. Firebase tidak hanya menjadi alternatif untuk kita menyimpan datanya, tapi juga menjadi alternatif backend sementara yang dapat kalian gunakan untuk melakukan demo kepada calon pembeli atau calon customer kalian nantinya. OKe cukup dulu ya aku ngocehnya, capek ngetik panjang2 hahahaha..

*Diakhir Chapter aku kasih bonus repo source code aplikasi*

Kita mulai saja tutorialnya.

## Konfigurasi Project

1. Buka situs [Firebase](https://console.firebase.google.com/), dan buat akun disana
2. Didalam dashboard firebase, masuk ke menu ringkasan project atau dashboard
3. Klik tombol plus
4. Pilih Platform android atau ios
5. Konfig project, dan lihat pada gambar dibawah. Bagian yang saya centang wajib dilakukan ya

![Preferences]({{site.url}}/assets/img/200920/bagian1.png)

6. Masukan File *google-service.json* kedalam folder `project/android/app/`
7. Configurasi project selesai.


## Konfigurasi Auth atau User Login

1. Pada [Firebase](https://console.firebase.google.com/), buka menu `Authentication`
2. Pilih tab `Sigin method`
3. Aktifkan `Email/Sandi` (silahkan aktifkan yang lain sesuai kebutuhan kalian ya)
4. Konfigurasi Project Selesai.

Selanjutnya kita akan membahas part 2, yaitu menyiapkan UInya sobat.

[Flutter Firebase Auth Part 2 - Membuat UI/UX]({{base_url}}/2020/09/29/flutter-firebase-auth-part2/)
<br>
<br>
*Diakhir Chapter aku kasih bonus repo source code aplikasi*>
<small> - Penulis</small>

