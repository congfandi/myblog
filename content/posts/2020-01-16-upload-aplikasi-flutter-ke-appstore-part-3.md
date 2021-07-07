---
title: Upload Aplikasi Flutter ke Appstore Part 3
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Flutter, Tips]
---

Akhirnya masuk pada pembahasan yang terakhir yaitu, pada bagian XCODE nya, bagian ini adalah bagian yang terakhir dari pembahasan kali ini. pada bagian ini kita akan mempelajari bagaimana sih cara upload aplikasi ke appstore melalui XCODE, berbeda dengan playstore yang harus kita masukkan aplikasinya yang berupa .apk file, pada apple developer sudut pandang itu harus kita ubah karena yang melakukan upload aplikasi ke appstore adalah xcodenya dan kita tidak bisa upload aplikasi seperti layaknya playstore kecuali menggunakan CI/CD tool seperti `Codemagic`.
<!--more-->

Oke kita langsung saja pada tutorialnya :

## Simulasi ##

1. Sudah ada project flutter
   
2. Sudah punya akun apple developer. Akun apple developer ini harus temen-temen beli dengan harga $99/tahun dan berbeda dengan playstore yang sekali beli untuk selamanya, akun apple developer harus diperpanjang setiap tahunnya.

3. Sudah punya Macbook/Imac dan Iphone/Ipad (Hal ini wajib dan tidak dapat di tolerir)

## Langkah - Langkah Pada bagian XCODE ##

1. Buka `Terminal` pada folder project flutter temen temen

2. Jalankan perintah berikut
    
        flutter clean

        flutter build ios --release

3. tunggu hingga proses selesai

4. Buka file `dir project/ios/Runner.xcworkspace`

6. Setelah XCODE kebuka, hubungkan Iphone atau Ipad teman teman ke Mac

7. Jangan lupa pilih Iphone/Ipad teman teman, lihat pada gambardibawah
    
    ![generate]({{ site.baseurl }}/img/200116/pilih.png)

8. Pilih menu `Product-> Archive` dan tunggu hingga proses pengarchivan selesai, jika menu Archive tidak keluar, temen temen harus memilih Device teman teman baik Iphone maupun Ipad

    ![generate]({{ site.baseurl }}/img/200116/archive.png)

9. Setelah proses Arvhice selesai, akan muncul popup seperti dibawah ini

    ![generate]({{ site.baseurl }}/img/200116/popuparchive.png) 
    
10. Pilih  aplikasi yang akan du upload ke Appstore kemudian klik tombol `Distribure App`

11. Pilih `Appstore Connect` kemudian klik Tombol `Next` 

    ![generate]({{ site.baseurl }}/img/200116/connect.png) 

12. Pilih `Upload` kemudian klik tombol next hingga muncul permintaan Sigin ke appstore connect
    
    ![generate]({{ site.baseurl }}/img/200116/upload.png) 

13. Setelah muncul permintaan siginin, pilih `automatically manage sigiin` kemudian klik tombol next

14. Upload aplikasi temen temen dan tunggu hingga proses selesai.


Setiap aplikasi yang di upload ke appstore, dia tidak akan langsung tayang ke appstore, pasti akan masuk dulu ke halaman `Testflight` pada halaman appstore connect, setelah itu akan di review oleh team apple untuk di approve atau di reject apabila di approve maka teman teamn bisa memasukan ke appstore dengan memilihnya di menu appstore connect.

oke sekian tutorial kali ini semoga bermanfaat bagi temen teman sekalian, akhir kata jangan lupa ngoding hari ini ;-) .....



>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


