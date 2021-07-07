---
title: Langkah langkah memasang google analytics pada web
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Web, Tips]
---

*Langkah langkah memasang google analytics pada web*

Bismillah, sudah 2 bulanan lebih saya belum nulis lagi. Alhamdulillah baru ada kesempatan untuk bercerita kepada sobat ngoding semuanya. Kali ini saya ingin berbagi tips seputar web analytics, dimana hal ini sobat butuhkan untuk melihat jumlah pengunjung web kita tanpa membebani kinerja aplikasi kita. Tulisan ini bermula saat ada seorang web yang bertanya disebuah komunitas tentang bagaimana mengetahui jumlah pengunjung tanpa mempengaruhi performa aplikasi dan inilah jawabannya.
<!--more-->

OKe kita mulai saja seperti biasanya :

## Simulasi ##

1. Sudah punya sebuah web
2. Punya akses ke cpanel/resource controller/file dir dari web


## Langkah Langkah memasang Firebase Analitycs ##

1. Buka Web [Firebase Console](https://console.firebase.google.com/), silahkan daftar dulu jika belum punya.
2. Buat Project dengan nama yang temen temen inginkan
    ![BuatProject]({{ site.baseurl }}/img/200731/1.png)
3. Tambahkan Aplikasi pada halaman dashboard firebase console
    ![BuatProject]({{ site.baseurl }}/img/200731/2.png)
4. Pilih Tambahkan aplikasi
    ![BuatProject]({{ site.baseurl }}/img/200731/3.png)
5. Setelah itu, masukan nama aplikasi dan pilih selanjutnya
    ![BuatProject]({{ site.baseurl }}/img/200731/4.png)
6. Jika sudah terlihat barisan kode javaScript, ambil code tersebut
    ![BuatProject]({{ site.baseurl }}/img/200731/5.png)
7. Masuk ke cpanel web sobat ngoding, dan carilah file index.html/
index.php/ file yang di jalankan pada halaman pertama atau pada semua halaman
8. Masukan kode yang sudah di copy dari firebase console.


## Langkah Langkah melihat hasilnya ##

1. Pada halaman firebase console dapat dilihat pada dashboard analytics
    ![BuatProject]({{ site.baseurl }}/img/200731/6.png)
2. atau dapat mengunjungi halaman [Google Analytics](https://analytics.google.com/analytics/web/)
     ![BuatProject]({{ site.baseurl }}/img/200731/7.png)
3. *Biasanya aplikasi tidak langsung menampilkan hasil, butuh waktu paling tidak 1x24 jam*


Sekian sobat ngoding tutorial singkat mengenai cara memasang analytics di website kita, jika ingin bertanya atau diskusi dapat menghubungi saya di media social yang sudah saya pasang pada blog ini, Semoga ngodingmu hari ini menyenangkan.


>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>

