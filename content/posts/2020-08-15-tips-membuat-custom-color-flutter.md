---
title: Tips Membuat Custom Warna Flutter
img: ../../img/200815/www.thengoding.com.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Flutter, Tips, Mobile]
---

Holaaaa sahabat ngoding semua, kali ini saya mau nulis tentang hal yang ga kalah menarik nih yaitu [tips membuat custom warna di flutter]({{site.url}}/2020/08/15/tips-membuat-custom-color-flutter).

Standartnya di flutter sudah ada warna bawaan yang ada pada MaterialColor class, namun jika kita menghendaki pewarnaan sendiri pada aplikasi kita, kita harus membuat beberapa daftarnya dulu dan kebayang jika kita harus menulisnya manual setiap kita butuh warnanya, nah pada tulisan kali ini saya akan bebagi tips yang saya gunakan untuk membuat custom warna sendiri. yok langsung lanjut ke tutorialnya.

## Langkah 1 ##
Buatlah sebuah file dengan nama `custom_color.dart` , disni kita akan selalu menggunakan file ini untuk mewarnai widget kita baik itu text maupun widget2 lain yang dapat diberikan warna.

## Langkah 2 ##
Kumpulkan semua warna yang temen2 butuhkan dalam membuat aplikasinya, sebagai contoh, lihatlah pada gambar dibawah, asumsinya kita sudah punya wana yang kita inginkan sebagai warna primary (utama) aplikasi kita.

![warna]({{site.url}}/img/200815/color.png)


50 : #FEECEB

100 : #FCC7C3

200 : #FAA19B

300 : #F88279

400 : #F66257

500 : #F44336

600 : #D63B2F

700 : #B73229

800 : #992A22

900 : #7A221B

A100: #FCC7C3

A200: #FAA19B

A400: #F66257

A700: #B73229

## Langkah 3 ##

Kita masukan semua kode warna yang sudah kita kumpulkan pada kelas `custom_color.dart` dan hasilnya seperti ini : 

```dart
        class CustomColor{
            static final _primary = 0xffF66257;             
                                                        
            final colorPrimary = MaterialColor(_primary, {  
                    50: Color(0xffFEECEB),                        
                    100: Color(0xffFCC7C3),                       
                    200: Color(0xffFAA19B),                       
                    300: Color(0xffF88279),                       
                    400: Color(_primary),                         
                    500: Color(0xffF44336),                       
                    600: Color(0xffD63B2F),                       
                    700: Color(0xffB73229),                       
                    800: Color(0xff992A22),                       
                    900: Color(0xff7A221B),                       
            });                                              
        }
```

kelas ini sudah bisa temen2 gunakan pada kelas *MyApp* atau pada *theme* property setiap widget yang hendak diwarnai dengan warna ini.

Selanjutnya kita akan menambahkan warna lain selain primary aplikasi, sebagia contoh warna `putih`, `hitam` dan `biru` maka kita akan mengedit kelas CustomColor menjadi seperti dibawah ini

```dart

    class CustomColor {
         final colorPrimary = MaterialColor(_primary, {                           
                50: Color(0xffFEECEB),                                                 
                100: Color(0xffFCC7C3),                                                
                200: Color(0xffFAA19B),                                                
                300: Color(0xffF88279),                                                
                400: Color(_primary),                                                  
                500: Color(0xffF44336),                                                
                600: Color(0xffD63B2F),                                                
                700: Color(0xffB73229),                                                
                800: Color(0xff992A22),                                                
                900: Color(0xff7A221B),                                                
            });                                                                       
                                                                                        
            final ColorSwatch colors = ColorSwatch(_primary, {                       
                'hitam' : Color(0xff000000),                                           
                'putih' : Color(0xffffffff),                                           
                'biru'  : Color(0xFF2196F3)                                            
            });                                                                       
                                                                
    }

```
nah sekarang kita sudah punya warna template yang akan kita gunakan pada aplikasi kita. selanjutnya adalah cara penggunaanya.

## Langkah 4 Cara Penggunaan ##

kita asumsikan akan menggunakan warna sebagai warna base aplikasi kita, maka yang harus temen2 lakukan adalah

1. Buka file `main.dart` temen2 kemudian carilah  *ThemeData* kemudian masukan warna yang sudah kita buat pada property `primarySwatch : new CustomColor().colorPrimary`

2. Cara mewarnai widget dengan custom color kita adalah: 

```dart
        final myTheme = new CustomColor();

        _contohWidget(){
            return Container(
                height : 100,
                width: 100,
                color : myTheme.colors['putih']
            );
        }
```

jika temen2 ingin menggunakan warna utama, tinggal paggil aja `myTheme.colors`, maka yang dipanggil adalah warna yang di set pada default colornya.

# Masalah Yang Akan Timbul #

Masalah yang akan timbul jika temen2 menggunakan tips ini adalah : 

Jika jumlah warna yang digunakan banyak akan susah mengingatnya,

Solusi : Update file `custom_color.dart` menjadi seperti ini

```dart
    class CustomColor {
        final colorPrimary = MaterialColor(_primary, {                           
            50: Color(0xffFEECEB),                                                 
            100: Color(0xffFCC7C3),                                                
            200: Color(0xffFAA19B),                                                
            300: Color(0xffF88279),                                                
            400: Color(_primary),                                                  
            500: Color(0xffF44336),                                                
            600: Color(0xffD63B2F),                                                
            700: Color(0xffB73229),                                                
            800: Color(0xff992A22),                                                
            900: Color(0xff7A221B),                                                
        });                                                                       
                                                                                    
        final ColorSwatch colors = ColorSwatch(_primary, {                       
            HITAM : Color(0xff000000),                                           
            PUTIH : Color(0xffffffff),                                           
            BIRU  : Color(0xFF2196F3)                                            
        });                                                                       
                                                            
    }

    const String HITAM = "hitam";
    const String PUTIH = "putih";
    const String BIRU = "BIRU";
```

***NOTED***  pastikan penulisan variabel constanta ada diluar kelas agar tidak perlu menuliskan nama kelasnya.

Cara memanggilanya seperti ini

```dart
        final myTheme = new CustomColor();

        _contohWidget(){
            return Container(
                height : 100,
                width: 100,
                color : myTheme.colors[HITAM]
            );
        }
```
Dengan begini temen2 tidak perlu menghfal nama dari warna yang kita definisikan.


## Tambahan ##

Yang terakhir adalah, saya sangat menyarankan agar teman-teman menggunakan **Singleton** Method karena color ini akan dipanggil disemua kelas yang butuh render ui, untuk itu untuk mempercepat proses rendernya kita tidak akan menginisialisi lagi file custom color kita, edit class `CustomColor` menjadi seperti ini :

```dart
        class CustomColor {
            
            static final CustomColor _instance = CustomColor._internal();
                                                                   
            factory CustomColor() {                                         
            return _instance;                                                
            }                                                                  
                                                                            
            CustomColor._internal(); 

            final colorPrimary = MaterialColor(_primary, {                           
                50: Color(0xffFEECEB),                                                 
                100: Color(0xffFCC7C3),                                                
                200: Color(0xffFAA19B),                                                
                300: Color(0xffF88279),                                                
                400: Color(_primary),                                                  
                500: Color(0xffF44336),                                                
                600: Color(0xffD63B2F),                                                
                700: Color(0xffB73229),                                                
                800: Color(0xff992A22),                                                
                900: Color(0xff7A221B),                                                
            });                                                                       
                                                                                        
            final ColorSwatch colors = ColorSwatch(_primary, {                       
                HITAM : Color(0xff000000),                                           
                PUTIH : Color(0xffffffff),                                           
                BIRU  : Color(0xFF2196F3)                                            
            });                                                                       
                                                                
        }

        const String HITAM = "hitam";
        const String PUTIH = "putih";
        const String BIRU = "biru";
```

Maka dengan begini mau berapa kalipun temen2 meng-inisialisasi kelas `CustomColor` semua property yang dipanggil adalah dari kode proses yang sama. Jika temen2 ingin tahu lebih tentang kenapa kita mesti menggunakan singleton kasih aku tahu ya, saya akan dengan senang hati menulisnya untuk kalian..

Akhir kata, jangan lupa control+s ya :-) ....


>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>