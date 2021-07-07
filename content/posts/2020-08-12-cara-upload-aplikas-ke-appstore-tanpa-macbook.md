---
title: Cara Upload Aplikasi Ke AppStore tanpa Macbook
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Flutter, Tips, iOS, Iphone, Apple]
---

*Cara Upload Aplikasi Ke AppStore tanpa Macbook*


Bismillah, Kali ini saya ingin berbagi tentang bagaimana sih cara upload aplikasi ke appstore tanpa macbook, khusunya bagi pengguna flutter developer. Tutorial kali ini lebih dikhususkan bagi pengguna flutter sebeanarnya dan sebagai pengetahuan bagi temen temen bahwa appstore dan playstore itu bisa upload aplikasi tanpa harus menggunakan website resmi mereka dan ini legal ya.
<!--more-->

Sebelum kita mulai tutorialnya, ada beberapa hal yang harus kalian ketahui terlebih dahulu yaitu tentang [Codmagic](https://codemagic.io/start/), tool ini yang akan kita gunakan untuk upload aplikasi kita ke appstore. Tool ini merupakan tool yang biasa digunakan untuk proses CI/CD oleh seorang pengembang dan tool ini dapat mempercepat proses development dan dsitribusi aplikasi kita serta didalam codemagic juga terdapat tool untuk testing.
bagi kalian yang mau upload aplikasi ke appstore secara manual (dari xcode) bisa mengunjungi tulisan saya yang ini [Part1](https://thengoding.com/2020/01/15/upload-aplikasi-flutter-ke-appstore-part-1/),[Part2](https://thengoding.com/2020/01/16/upload-aplikasi-flutter-ke-appstore-part-2/) and [part3](https://thengoding.com/2020/01/16/upload-aplikasi-flutter-ke-appstore-part-3/).


## Persyaratan utama sebelum memulai 

- Sudah punya project flutter yang sudah di integrasikan dengan version control(gitlab,github,bitbucket,etc)
- Sudah punya akun apple developer
- sebuah macbook untuk integrasi awal (sekali aja pas setup)

## Langkah - Langkah setupa

1. Buka situs [Codmagic](https://codemagic.io/start/)
2. Login menggunakan akun sobat ngoding yang terhubung dengan project flutternya
3. Pilih Project flutter yang hendak diupload dengan Codemagic
4. Setting untuk trigger uploadnya, dan berikut penjelasannya

    ![Code Magic]({{ site.baseurl }}/img/200812/codemagic.png)

*a. Build Triggers*

Disini temen2 bisa setting untuk build ke appstore itu pas kapan, misal upload ke appstore saat ada pull request ke branch master, atau kalian bisa set * agar setiap ada aktivitas apapun akan diupload ke appstore

*b. Environment Variables*

Disni bisa teman teman gunakan untuk setup kondisi tertentu, saran saya untuk sementara temen2 kosongi dulu 

*c. Dependency Caching*

Untuk awal, temen temen kosongin aja dulu, untuk explorenya bisa temen2 pelajari di situs codemagic langsung

*d. Test*

Ini digunakan untuk testing sebelum di upload ke appstore,, misal temen2 mengharuskan aplikasi harus lolos testing dulu sebelum masuk ke appstore bisa di konfig disini ya, tapi kodenya dari kalian sendiri ada pada project/test di project flutter temen2, saran saya dikosongi atau jangan digunakan jika temen2 tidak menulis kode testing sama sekali.

*e. Build*

nah, disini yang urgent temen2. pada menu ini temen2 bisa memilih jenis xcode yang mau digunakan untuk mendeploy aplikasi kita... karena hasil deploy dari sinilah yang akan digunakan untuk diupload ke appstore..
    
Karena bagian ini bagian terpenting, saya bahas agak panjang yaaa...

Dimenu ini temen2 bisa memilih mau dibuild versi apa aja ? ada android ios dan web. temen2 tinggal aktifkan aja centangannya

Disini temen2 juga bisa memilih type nya, baik itu debug ataupun release dan profile

*g. Publish*

![Code Magic]({{ site.baseurl }}/img/200812/publish.png)

Nah yang terakhir temen2 dan yang paling bisa menetukan yang kalian sukses atau gagal.. perhatikan gambar diatas, yang saya berikan kotak merah itu bagian terpentignya.

## IOS Code Signing ##

Temen2 bisa mendapatkan IOS Code Signing (Code signing certificate,Provisioning profiles) bisa temen2 dapatkan dari [Apple Developer](https://developer.apple.com/account/resources/certificates/list) tapi ingat ya, kalian harus sudah membeli akun apple dev ya baru kalian bisa membuat IOS code signing.. dan untuk membuat Signing Certificate temen temen harus punya macbook untuk membuatnya.

untuk tutorial ini akan saya buat terpisah teman2. ditunggu saja ya :-) .

## App Store Connect ##

Masukan apple id developer temen2 dan jangan lupa ya aktifkan App Password,

untuk mengaktifkannya, temen2 bisa lakukan di [Apple ID](https://appleid.apple.com/account/manage), masuk ke menu *Keamanan* dan aktifkan *KATA SANDI KHUSUS APP* nah, dari sini kalian bakalan dapat kata sandi untuk aplikasi temen2,, silahkan masukan ke codemagic kembali.


Jika tidak ada yang gagal dalam proses setup, artinya aplikasi temen2 siap diupload ke appstore tanpa menggunakan macbook..

Sekian tutorial kali ini.. moga bermanfaat ya temen2 :-) ..

Semoga ngoding kalian menyenangkan :-).


>Jika kode kalian berjalan dengan baik, maka biarkanlah<small> - Steve Jobs</small>