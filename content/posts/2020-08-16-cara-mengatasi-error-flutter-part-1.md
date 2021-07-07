---
title: Cara Mengatasi Error Pada Flutter Part 1
img: 200817/crash1.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Flutter, Tips, Mobile]
---

Bismillah, Kali ini saya ingin berbagi tips seputar cara mengatasi error pada widget flutter. Ada berbagai macam error yang akan sobat ngoding jumpai saat membuat aplikasi dengan flutter, salah satunya adalah error widget, errror ini yang akan kita bagas dan akan saya bagi dengan beberapa tulisan, pada tulisan ini saya akan membahas tentang error yang terjadi pada widget **ROW**. Pada widget Row terdapat beberapa error yaitu : 

## Error Saat ada tulisan atau text sejajar ##
Saat ada text yang sejajar dalam row, dan panjang textnya melebihi ukuran dari layar, yang terjadi adalah error, sebagai contoh kasus.

```dart
    Row(
        children:[
            Text("Ini adalah contoh tulisan sejajar pertama yang akan saya tampilkan dilayar telepon"),
            Text("Ini adalah contoh tulisan sejajar kedua yang akan saya tampilkan dilayar telepon"),
        ]
    )
```

cara mengatasi ini dengan memberikan ukuran pada textnya yaikut ukuran lebar, bisa dengan membagi layar sama persis, solusinya sebagai berikut

- Solusi 1, membuat layar bisa dibagi 2 dengan ***MediaQuery***
```dart
        Row(
            children:[
                Container(
                    width: MediaQuery.of(context).size.width/2,
                    child:Text("Ini adalah contoh tulisan sejajar pertama yang akan saya tampilkan dilayar telepon")
                ),
                Container(
                    width: MediaQuery.of(context).size.width/2,
                    child:Text("Ini adalah contoh tulisan sejajar kedua yang akan saya tampilkan dilayar telepon")
                ),
            ]
        )
```

- Soluasi 2, Membagi layar menjadi 2  sama persis dengan ***Expanded***,
Expanded ini akan mengambil ukuran layar yang kosong,  misal sisa layar adalah 70% , maka sebanyak itulah yang akan diambil oleh Expanded Widget ini, namun apabila ada 2 Expaneded maka layar akan dibagi menjadi 2 sama persis, kecuali dtambah dengan atribut **flex**

    ```dart
            Row(
                children:[
                    Expanded(
                        child:Text("Ini adalah contoh ")
                    ),
                    Expanded(
                        child:Text("Ini adalah contoh tulisan sejajar kedua yang akan saya tampilkan dilayar telepon")
                    ),
                ]
            )
    ```

Jika Widget Expaneded ditambah dengan atribut **flex**, maka lebarnya akan menyesuaikan pada ukuran flexnya, contoh, flex:30,flex:70, maka layarnya akan dibagi menjadi 30% dan 70%, selamat mencoba ..

- Solusi 3 dan yang terakhir adalah dengan membagi layar sesuai dengan ukuran contentnya yaitku dengan widget ***Flexible***
```dart
        Row(
            children:[
                Flexible(
                    child:Text("Ini adalah contoh ")
                ),
                Flexible(
                    child:Text("Ini adalah contoh tulisan sejajar kedua yang akan saya tampilkan dilayar telepon")
                ),
            ]
        )
```
Widget FLexible ini akan mengambil ukuran layar selebar contentnya, kalau istilahnya lebarnya menyesuaikan pada isinya.

Sebenarnya kebanyakan error pada layouting flutter disebabkan karena tidak menemukan lebar pada pembungkus widgetnya.

Selanjutnya kita akan membahas pada widget Column.

[Cara Mengatasi Error Flutter Part 2]({{site.url}}/2020/08/17/cara-mengatasi-error-flutter-part-2/)

>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>