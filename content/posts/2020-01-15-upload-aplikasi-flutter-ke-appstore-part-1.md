---
title: Upload Aplikasi Flutter ke Appstore Part 1
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Flutter, Tips]
---

Sebelumnya saya sudah membahas [Upload aplikasi flutter ke playstore](https://thengoding.com/2020/01/10/upload-aplikasi-flutter-ke-playstore-part-1/), saat nya kita membahas bagaiaman cara upload aplikasi flutter ke appstore. Sebenarnya flutter juga sudah membahas juga di blognya cara uploadnya ke appstore namun saya disini akan membahas lebih detail. 
<!--more-->
Seperti pada pembahasan [Upload aplikasi flutter ke playstore](https://thengoding.com/2020/01/10/upload-aplikasi-flutter-ke-playstore-part-1/) , kita akan membagi pembahasan kali ini menjadi 3 bagian, bagian pertama kita akan membahas pada sisi developer console nya dan bagian kedua kita bahas disisi appstore connect nya dan terakhir pada bagian xcode nya. Ada beberapa syarat yang harus kalian penuhi sebelum kalian mengupload aplikasi kalian ke appstore, syarat -syarat sebagai berikut : 

## Syarat Upload aplikasi ke appstore ##

1. Sudah memiliki akun apple developer

2. Memiliki Macbook/Imac

3. Memiliki Iphone/Ipad
   

Seperti biasa kita harus mulai dengan simulasinya dahulu

## Simulasi ##

1. Sudah ada project flutter
   
2. Sudah punya akun apple developer. Akun apple developer ini harus temen-temen beli dengan harga $99/tahun dan berbeda dengan playstore yang sekali beli untuk selamanya, akun apple developer harus diperpanjang setiap tahunnya.

3. Sudah punya Macbook/Imac dan Iphone/Ipad (Hal ini wajib dan tidak dapat di tolerir)


## Langkah - Langkah Pada bagian Apple Developer Console ##

1. Mac teman teman sudah terinstall certificate apple developer, jika belum silahkan lihat pada tutorial [Menambahkan Apple Developer Certificate](https://thengoding.com/2020/01/14/xcode-menambahkan-apple-developer-certificate/)

2. Masuk ke site [Apple Developer](https://developer.apple.com/) dan login

3. Pilih Menu Pilih Menu `Certifacates, Identifiers & Profiles`

4. Pada halaman `Certifacates, Identifiers & Profiles` , pilih Identifier dan buat identifier baru dengan mengklik tombol plus pada bagian kiri atas setelah nama identifier
    
    ![generate]({{ site.baseurl }}/img/200115/identifier.png)

5. Setelah itu, temen temen akan diminta memilih jenis identifier yang akan dibuat, pilih seperti pada gambar dibawah ini
   
   ![generate]({{ site.baseurl }}/img/200115/appid.png)

6. Setelah itu, teman teman akan diminta untuk memasukkan nama package aplikasi, hal ini sangat penting karena package tidak dapat diganti setelah tayang di appstore

    ![generate]({{ site.baseurl }}/img/200115/package.png)

7. Apabila sudah selesai maka identifier aplikasi teman-teman akan muncul seperti pada gambar dibawah ini
   
   ![generate]({{ site.baseurl }}/img/200115/list.png)


Cukup sekian teman teman, kita akan melanjutkan pembahasan pada tulisan selanjutnya, yaitu pada bagian Apple Store Connect. Sampai ketemu di tuisan saya selanjutnya dan akhit kata happy ngoding :-D


>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


