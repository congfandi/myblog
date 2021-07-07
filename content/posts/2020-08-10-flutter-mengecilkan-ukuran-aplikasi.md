---
title: Tips Memperkecil Ukuran Aplikasi Flutter
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Flutter, Tips]
---

*Tips Memperkecil Ukuran Aplikias Flutter*

Hola sobat ngoding yang budiman.. masih semangat ngoding kan ? . Oke jadi kali ini saya mau nulis tentang pertanyaan yang sering muncul nih dikomunitas flutter indonesia dimana bnayak dari temen-temen komunitas bertanya bagaimana cara memperkecil ukuran aplikasi yang dibuat dengan flutter.
<!--more-->

Sebenarnya, pada situs [flutter](https://flutter.dev) sudah ada penjelasan tentang caranya, akan tetapi saya menyadari bahwa tidak semua orang memiliki kemampuan yang sama dalam menerima informasi. Ada yang dapat mnerima informasi dengan simulasi, ada juga dengan video dan ada juga yang lebih mudah menerima informasi dengan bentuk tulisan seperti ini, tentu saja kalian yang masih enak membaca tulisan ini adalah kalian yang masuk kedalam golongan yang ketiga, bener kan ? wkwwkwk... kalau [thengonding](https://thengoding.com) sendiri sih bergantung ya.. kalau informasi itu bener2 baru, maka saya butuh lihat videonya agar mengerti step by step nya, tapi kalau informasi itu saya sudah mengerti sebelumnya dan hanya butuh improvement dari yang sudah saya ketahui maka saya lebih suka membaca dari pada menonton, karena membaca meskipun di skip2 dapat ketangkep maksud dan tujuannya, nah itu juga yang menjadi alasan saya membangun website sederhana ini. Well, saya stop dulu deh ngocehnya biar kita bisa langsung bahas pada inti permasalahannya.


# Tips Memperkecil Ukuran Aplikasi flutter #

## 1 Menghapus Unused Resource ##
Menghapus unuse resource dapat dilakukan dengan 2 metode, manual dan otomatis, cara manual dapat dilakukan dengan menghapus sendiri file file yang tidak kalian butuhkan dan cara otomatis dapat kalian lakukan dengan menggunakan *Android Studio*. Caranya adalah
1. Klik Kanan pada Project
2. Klik Menu *Refactor*
3. Klik Menu *Remove Unused Resources*

## 2 Melakukan Optimse Import 
Tips ini tidak banyak berpengaruh sih pada ukuran app temen temen, tapi tips ini dapat melancarkan serang jantung pada aplikasi temen2 :-D, caranya ada 2, yang pertama adalah dengan manual dan otomatis, otomatis caranya dengan menggunakan *Android Studio*
1. Klik kanan pada folder *lib*
2. Klik *Optimise Import*

## 3 Analisa file yang paling besar dan hapus yang tidak perlu ##
Cara ini menurut saya pribadi lumayan ampuh banget dan ini sudah ditulis juga sama si jujel di situs berikut [Reduce APK Size](https://developer.android.com/topic/performance/reduce-apk-size)

## 4 Gunakan Build appbundle dan hindari build .apk (Untuk yang mau dirilis ke android)
Nah, ini cara yang terakhir nih.. jika kalian biasa menggunakan perintah berikut untuk membuat apk

```
    flutter build apk --release
```

artinya sudah saatnya kalian meninggalkan kebiasaan kalian ini dan ginakanlah command seperti ini

```
    flutter build appbundle --target-platform android-arm,android-arm64,android-x64
```

atau kalian bisa lebih memperkecil lagi dengan membuat target dari app kalian, kkodenya seperti ini:

```
    flutter build apk --target-platform android-arm,android-arm64,android-x64 --split-per-abi
```
dengan kode diatas, aplikasi dapat di reduce hingga 7mb akan tetapi tidak semua perangkat dapat menginstallnya karena saat selesai dibuild dengan kode diatas, aplikasi tebentuk menjadi 3 part dan menyesuaikan device yang ada.

Nah, cukup sekian sobat tips dari thengoding untuk kali ini, semoga ngodignmu menyenangkan :-) ...

Akhir kata, See You On The Next Chapter!

>Ngoding itu bakalan indah pada waktunya!<small> - The Ngoding</small>


