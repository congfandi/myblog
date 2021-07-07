---
title: Membuat Copyright Otomatis Android Studio #judul postingan
img:  200915/cover.jpg #gambar postingan taruh di assets/img dan langsung call nama imagenya
layout: post #default jangan diganti
author: Cong Fandi #default me
author-img : congfandi.jpeg #default me
author-detail : iOS Developer, Android Developer, Web Developer # default me
fig-caption: Tips #default me
tags: [Android Studio, Tips] # tags dalam array [Developer, Web, Tips]
---
Halo Sobat Ngoding Semua, Pada tulisan kali ini saya tidak akan membahas tentang ngoding, tapi saya ingin menulis tentang sebuah tool yang sangat berguna saat kalian berkolaborasi dengan team kalian, tujuannya simple, **Membedakan mana yang merupakan pekerjaan kalian dan mana yang bukan** . Dengan begitu apaabila ada file pekerjaan yang sedikit susah unutk difahami, kalian bisa langsung mengetahui siapa yang mengerjakannya.. oke kita mulai Tutorialnya.

# Mengaktifkan Plugin Copyright
1. Buka Project anda menggunakan **Android Studio**
2. Buka menu **Preferences**
![Preferences]({{site.url}}/assets/img/200915/1.png)

3. Masuk ke menu Plugin
![Preferences]({{site.url}}/assets/img/200915/2.png)

4. Cari dan install plugin _Copyright_

# Memasang Copyright template
1. Buka Menu **Editor** dari **Preferences** Menu

2. Masuk Ke menu **Copyright**
![Preferences]({{site.url}}/assets/img/200915/3.png)

3. Tambahkan Profile
![Preferences]({{site.url}}/assets/img/200915/4.png)

```
    $project.name
    $file.fileName
    Created by Cong Fandi on $today.day/$today.month/$today.year
    email 	    : congfandi@gmail.com
    website 	: https://www.thengoding.com 
    Copyright © $today.year Cong Fandi. All rights reserved.
```

4. Kembali ke menu **Copyright**

![Preferences]({{site.url}}/assets/img/200915/5.png)

5. Pilih Profile yang sudah kita buat tadi

![Preferences]({{site.url}}/assets/img/200915/6.png)

# Cara Menggunakan Copyright template
1. Buat sebuah **file** baik itu dart, java,kotlin maupun xml maka secara otomatis filenya akan ada tulisan copyrightnya

![Preferences]({{site.url}}/assets/img/200915/7.png)

2. Atau kalian bisa menggunakan pada file yang sudah ada dengan cara 
    - Klik Kanan pada folder yang ingin di update copyrightnya
    - pilih menu **Update Copyright**
    - Selesai...

    ![Preferences]({{site.url}}/assets/img/200915/8.png)

Cukup mudah bukan....

Oh iya, kalian bisa lho menambahkan parameetr selain dari yang aku tulis, kalian bisa mengunjungi situs ini [Copyright Profile](https://www.jetbrains.com/help/idea/copyright-profiles.html#profile_page).

Cukup sekian, sampai ketemu pada artikel selanjutnya.. akhir kata..

Yuk belajar ngoding bareng...!

<br>
<br>
>Sekedar ingin berbagi, dan bukan yang paling mampu<small> - Penulis</small>

