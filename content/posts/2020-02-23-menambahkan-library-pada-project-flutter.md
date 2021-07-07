---
title: Menambahkan library pada project flutter
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Flutter, Tips]
---
Bismillah,

Hai sobat ngoding, kali ini saya bahas sedikit tentang bagaimana cara menambahkan library pada project flutter kita. Tidak sama dengan native project, flutter memiliki cara sendiri dalam menambahkan library, tentunya lebih mudah dan gampang daripada native code.
<!--more-->

Kita mulai dari tempat kita menambahkan library terlebih dahulu.
website tempat dimana kita mencari library flutter ada di 

[Flutter Lib](https://pub.dev/flutter/packages)

kamu bisa mencari library apapun yang kamu butuhkan disana mulai dari librari yang paling sederhana kayak menampilkan teks dengan warna hingga library yang paling kompleks seperti library buat chatting.


Contoh kasus kita mau memasukkan *library* `provider: ^4.0.4` kedalam aplikasi kita, maka yang harus kita lakukan adalah membuka file `pubspec.yaml` yang ada pada folder project kita.

selanjutnya kita paste saja `provider: ^4.0.4` tepat dibawah `dependencies` sejajar dengan  tulisan `flutter` lebih jelasmnya perhatikan gambar dibawah ini

![generate]({{ site.baseurl }}/img/200224/sejajar.png)

Kemudian ketikkan ini pada `terminal` atau `CMD` teman-teman

`flutter packages get`

jika muncul tulisan seperti ini

`Running "flutter pub get" in filter_provider...                     0.5s`

berarti library sukses ditambahkan



#kesalahan-kesalahan saat menambahkan library

1. Kesalahan indentasi (tidak sejajar dengan tulisan flutter dibawa dependencies)
   akan muncul seperti ini


 
                Error detected in pubspec.yaml:
                Error on line 26, column 12: Mapping values are not allowed here. Did you miss a colon earlier?
                ╷
                26 │    provider: ^4.0.4
                │            ^
                ╵
                Please correct the pubspec.yaml file at /Users/busol/Desktop/filter_provider/pubspec.yaml

   
2. Kesalahan karena library tidak ada di pub.dev

        
                Because filter_provider depends on provide ^4.0.4 which doesn't match any versions, version solving failed.
                pub get failed (1; Because filter_provider depends on provide ^4.0.4 which doesn't match any versions, version solving failed.)
        

Oke cukup sekian, semoga tulsian yang singkat ini dapat bermanfaat bagi teman teman pembaca sekalian, akhir kata ... See You On the next chapter :-D

>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


