---
title: Android Studio - Mengganti nama project 
img: 200101/cover.png
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer , Android Studio, Tips]
---

Halo sobat ngoding, awal tahun 2020 ini aku buka dengan tulisan sederhana ini... sebenanrnya hanya untuk mengisi waktu luang aja karena tanggal 1 pada liburan semua.
<!--more-->
Mengganti nama project pada android studio merupakan suatu tindakan yang perlu kamu tahu jika kamu adalah seorang developer android, kenapa begitu ? karena hal ini kamu butuhkan jika ternyata project yang kamu buat mengandung `typo` atau ternyata nama project yang sudah kamu tulis salah atau ingin menggantinya karena ada permintaan dari client. 

oke kita mulai saja langkah - langkahnya , namun seperti biasa kita tuliskan dulu simulasinya nya

## Simulasi ##

1. Sudah ada project android studio
   
2. Mennganti nama project dari 
   
   Sebelumnya : `My APlication`

   Menjadi : `My Application`

3. Kita mengganti karena ada typo tulisan


##  Langkah - Langkah ##

1. Ganti Tab project menjadi `Project files`

    ![TabProject]({{ site.baseurl }}/img/200101/tabproject.png)
   
2. Klik kanan pada root project

3. Refactor dengan cara
   
   - Klik kanan `Refactor` => `Rename` atau
        
    ![Rename]({{ site.baseurl }}/img/200101/refactor.png)
  
   - Tekan secara bersamaan pada keyboard `Shift` + `F6`
  
4. Ganti nama menjadi `MyApplication` dan pastikan untuk mencentang reference dan string name nya 
   

    ![rename]({{ site.baseurl }}/img/200101/rename.png)

5. Expand(Buka) `.idea` folder

6. Klik `.name` dan ganti menjadi `My Application`

    ![dotname]({{ site.baseurl }}/img/200101/dotname.png)

7. Klik `setting.gradle` 
   
8. Ganti `rootProject.name='My APlication'` menjadi `rootProject.name='My Application'`

9.  Terakhir restart android studio sobat ngoding dan, tara... berubahlah nama project kita


Untuk pembahasan penggantian packagename, akan dibahas dipostingan selanjutnya, atau langsung aja klik `Next Post` pada akhir tuisan ini, akhir kata ...

Selamat Ngoding :-D


>Coding itu tidak pernah sempurna, karena yang sempurna itu adalah manusianya<small> - Penulis</small>


