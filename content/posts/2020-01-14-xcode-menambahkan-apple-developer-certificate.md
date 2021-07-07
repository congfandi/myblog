---
title: XCODE - Menambahkan apple developer certificate
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Flutter, Tips]
---

Halo sobat ngoding, kali ini pembahasan kita tentang xcode nih.. tentang bagaimana cara menambahkan certificate apple developer pada perangkat macbook kita atau imac kita, ada banyak juga yang sudah membahas terkait masalah ini, akan tetapi saya ingin berbagi tentang bagaimana cara saya memasukan apple certificate ini. 
<!--more-->
Awalnya saya sangat kesulitan untuk melakukan hal ini karena minimnya dokumentasi dalam bahasa indonesia dan jarang juga ada orang yang membahas masalah ini. oke kita langsung mulai dengan simulasinya dulu : 


## Simulasi ##

1. Sudah memiliki perangkat (Macbook/Imac, Iphone atau Ipad)

2. Sudah memiliki akun Apple Developer (Silahakn daftar [disini](https://developer.apple.com/) dulu dengan harga $99/tahun)


## Langkah - langkah Pada perangkat Macbook/Imac ##

1. Buka aplikasi `Keychain Access` pada Mac teman teman
   
2. Pada menu `Keychain Access`, temen temen pilih `Certificate Assistant` kemudian `Request a Certificate From a Certificate Authority...`
   
   ![generate]({{ site.baseurl }}/img/200115/choose.png)

3. Akan muncul dialog meminta email dan lokasi dimana tempat akan menyimpan certoficate nya, seperti pada gambar dibawah ini, isi email dan lokasi penyimpanan pilih yang `Save To Disk`
   
    ![generate]({{ site.baseurl }}/img/200115/create.png)

4. Jika sukses, temen temen akan mendapat file dengan nama `CertificateSigningRequest.certSigningRequest`

Oke, Langkah pada bagian Macbook/Imac sudah selesai, sekarang kita akan masuk pada bagian Apple Developer Console nya.

## Langkah Langkah pada Apple Developer Console ##

1. Masuk ke site [Apple Developer](https://developer.apple.com/) dan login

2. Pilih Menu `Certifacates, Identifiers & Profiles` 
   
   ![generate]({{ site.baseurl }}/img/200115/menu.png)

3. Buat `Certificate` Baru dengan mengklik tombol plus (+) pada halaman `Certifacates, Identifiers & Profiles`  

    ![generate]({{ site.baseurl }}/img/200115/new.png)

4. Akan muncul pilihan yang lumayan banyak, karena kita akan membuat certificate, maka temen temen pilih yang `Apple Development` maka kita akan bebas membuat aplikasi disemua produk Apple.
   
   ![generate]({{ site.baseurl }}/img/200115/choosenext.png)

5. Kemudian temen temen pilih `certicate` yang sudah kita buat pada langkah langkah sebelumya, Kemudian next
   
   ![generate]({{ site.baseurl }}/img/200115/browse.png)

6. Setelah selesai mengenerate, klik tombol `Download` pada bagian kanan atas halaman dan akan menghasilkan file `Development.cer`

    ![generate]({{ site.baseurl }}/img/200115/download.png)

7. Setelah Selesai didownload, Buka File `Development.cer` yang sudah kita download, maka secara otomatis akan membuka aplikasi `Keychain Access` , dan apabila berhasil maka akan muncul certificate baru seperti pada gambar dibawah ini,

    ![generate]({{ site.baseurl }}/img/200115/final.png)

Masa berlaku certificatenya adalah setahun, jadi teman-teman dapat melihat certificate yang paling baru yang masuk pada Mac teman teman.

Nah, sekian tutorial bagaimana memasukan certificate apple developer ke perangkat mac kita, semoga artikel ini dapat membantu teman teman dalam membuat aplikasi.. akhir kata, jangan lupa ngoding ya hari ini :-) .


>Cinta adalah alasan terbaik untuk memulai sesuatu, maka cintailah koding agar kamu bisa memulainya dengan persiapan terbaik<small> - Penulis</small>


