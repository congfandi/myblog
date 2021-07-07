---
title:  Upload Aplikasi flutter ke playstore part 1
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Flutter, Android, Tutorial]
---


Hi sobat ngoding, kali ini saya khsus membahas cara upload aplikasi yang dibuat menggunakan flutter ke playstore. Cara uploadnya saya bagi menjadi 2 bagian, yang pertama ini adalah khusus bagaimana cara membuat `app-release.apk` untuk bisa dimasukan ke ke playstore.
 <!--more-->
Sebenarnya flutter sudah membahas tatacara nya ada di blognya flutter cuman pada blog saya ini akan saya tambahkan beberapa hal yang tidak dibahas disana, seperti biasa kita mulai saja tutorial nya dengan simulasi

## Simulasi ##

1. Sudah punya akun google play console, kalau belum punya beli dulu disini [https://play.google.com/](https://play.google.com/apps/publish/)

2. Sudah ada project flutter


## Langkah -  langkah ##

1. ### Pastikan Package kalian benar ###
   
   Memastikan nama package kalian benar adalah langkah yang paling penting menurut saya pribadi, karena nama package tidak dapat diganti setelah aplikasi kalian masuk ke playstore, untuk mengganti nama package apabila ada kesalahan, teman-teman dapat merubahnya, tutorialnya ada pada blog ini juga atau klik aja bagian disni [Cara mengganti nama package](https://thengoding.com/2020/01/01/mennganti-nama-package-android-studio-project/)

2. ### Buat `Key Store` File ###
   
   Membuat *Key Store* adalah langkah yang penting juga karena playstore dapat menerima aplikasi apabila key store disertakan pada aplikasi sobat, untuk membuat key store, dapat mengunjungi halaman [ini](https://thengoding.com/2020/01/12/cara-membuat-keystore/)

3. ### Buat `key.propertise` ###
   
   Buatlah file ini pada lokasi berikut `app dir>/android/key.properties` kemudian isi filenya menjadi seperti ini 

   ```gradle
      storePassword=<password from previous step>
      keyPassword=<password from previous step>
      keyAlias=key
      storeFile=<location of the key store file, such as /Users/<user name>/key.jks>
   ```
4. ### Edit file `<app dir>/android/app/build.gradle` ###
   
   Ada beberapa step untuk meng edit file gradle ini, 

   a. Ganti

        
            android {
        
        
    menjadi

        
            def keystoreProperties = new Properties()
            def keystorePropertiesFile = rootProject.file('key.properties')
            if (keystorePropertiesFile.exists()) {
                keystoreProperties.load(new FileInputStream(keystorePropertiesFile))
            }

            android {
        

    b. Ganti

        
            buildTypes {
                release {
                    // TODO: Add your own signing config for the release build.
                    // Signing with the debug keys for now,
                    // so `flutter run --release` works.
                    signingConfig signingConfigs.debug
                }
            }
        

    Menjadi

        
            signingConfigs {
                release {
                    keyAlias keystoreProperties['keyAlias']
                    keyPassword keystoreProperties['keyPassword']
                    storeFile keystoreProperties['storeFile'] ? file(keystoreProperties['storeFile']) : null
                    storePassword keystoreProperties['storePassword']
                }
            }
            buildTypes {
                release {
                    signingConfig signingConfigs.release
                }
            }
        

5. ### Ganti APP Icon ###

    Untuk mengganti icon, sudah saya tulis pada bagian yang lain yaitu pada tulisan saya ini [Mengganti Icon aplikasi android](https://thengoding.com/2020/01/13/mengganti-icon-aplikasi-android/)

6. ### Mengetikkan perintah pada terminal ###
   
   Ini adalah bagian akhir dari tulisan saya ini, silahkan buka terminal pada `directory` project teman teman, baik Linux/Mac atau Windows caranya sama aja,

    *membuat apk release*
    - flutter clean
    - flutter build apk --release 
  
    *membuat apk debug*
    - flutter clean
    - flutter build apk --debug

    *membuat app bundle*
    - flutter clean
    -  flutter build appbundle --target-platform android-arm,android-arm64,android-x64

7. Tunggu hingga proses pembuatan apk selesai, jika sukses hasil apka teman-teman akan ada pada folder `build/app/outputs/apk/release/app-release.apk`
   





>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


