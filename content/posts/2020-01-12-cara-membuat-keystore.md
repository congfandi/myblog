---
title: Cara membuat Key Store File
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Flutter, Android, Tips]
---


Halo sobat ngoding, kali ini saya ingin menulis tentang cara membuat JKS file atau istilah kerenya *Key Store*. Sebagai intrudction, *Key Store file adalah file yang digunakan untuk mengupload aplikasi ke playstore* ini menurut pengertian saya probadi dan agar dapat dengan mudah difahami. Keystore ini sebagai kunci atau syarat agar aplikasi dapat diupload ke playstore, mennurut google, isi dari *Key Store* ini adalah penandatanganan aplikasi.
<!--more-->
Perlu di ingat bahwa , *_1 Key Store dapat dipasang di banyak aplikasi namun 1 aplikasi yang sudah tayang di playstore, Key Store nya tidak dapat diganti_*



## Cara Membuat Keystore ##
Keystore dapat dibuat dengan 2 cara,

Cara : 
1. Dengan Android Studio
   
2. Dengan Terminal/CMD


## Memebuat Keystore dengan Android Studio ##

1. Buka Project Android Studio anda (Project android bukan flutter)
   
2. Klik menu *Build->Generate Signed Bundle/APK*
   
    ![generate]({{ site.baseurl }}/img/200112/signed.png)

3. Pilih Next Saja
   
    ![generate]({{ site.baseurl }}/img/200112/choose.png)

4. Kemuadian Klik New
   
    ![generate]({{ site.baseurl }}/img/200112/new.png)

5. Kemudian isi sesuai dengan penjelasan dibawah ini
   
   ![generate]({{ site.baseurl }}/img/200112/field.png)

   *Key Store Path*

        Lokasi dimana keystore akan disimpan setelah selesai nanti

   *Password*

        Password untuk password *Key Store*nya

   *Confirm*

        Konfirmasi Password *Key Store* nya

   *Alias*

        Nama Alias dari *Key Store*

   *Password*

        Pasword Key nya

   *Confirm*

        Konfirmasi password Key nya

   *Validity(years)*

        Masa Berlaku *Key Store* nya dalam satuan tahun

   *First and last name*

        Nama lengkap pembuat keystore (boleh atas nama perusahaan)

   *Organization Unit*

        Unit Kerja

   *Organization*

        Divisi

   *City/Locality*

        Kota 

   *State or Province*

        Provinsi

   *Country Code*

        Kode Negara (ID) unutk indonesia (EN) untu English dst..

## Membuat Keystore dengan Terminal/CMD ##

1. Buka terminal (Mac/Linux) / CMD (Windows)
   
2. Jalankan perintah dibawah ini
   
   a. Mac atau Linux

        
        keytool -genkey -v -keystore ~/key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias key
        

   b. Windows

        
        keytool -genkey -v -keystore c:/Users/USER_NAME/key.jks -storetype JKS -keyalg RSA -keysize 2048 -validity 10000 -alias key
        
    Setelah itu isi field2 yang diminta seperti pada android studio diatas.

Dan sepertin itu temen2 cara membuat *Key Store*. temen2 dapat menggunakan *Key Store* tersebut untk mengupload aplikasi ke google play console.




>Kode Error itu seperti micin, jika kebanyakan dapat membahayakan :-D<small> - Penulis</small>


