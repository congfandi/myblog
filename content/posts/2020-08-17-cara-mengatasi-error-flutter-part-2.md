---
title: Cara Mengatasi Error Pada Flutter Part 2
img: 200817/crash2.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Flutter, Tips, Mobile]
---

Melanjutkan pembahasan [Cara Mengatasi Error Flutter Part 1]({{site.url}}/2020/08/16/cara-mengatasi-error-flutter-part-1),namun pada tulisan ini yang akan kita tulis adalah widget **COLUMN**. Sebenarnya error pada **COLUMN** itu sama persis dengan yang terjadi pada row, namun jika row perhitungannya kesamping dan column perhitungannya kebawah. Berikut macam-macam error yang ada pada widget **COLUMN**.

## Error Saat ada List didalam Column ##

```dart
        Column(
          children :[
            Text("this is title"),
            ListView.builder(
               itemBuilder:(c,i)=>Text("halo")
            )
          ]
        )
```

Saat kode ini dijalankan, akan terjadi error pada aplikasi, yakni tidak dapat menampilkan apa2 pada layout karen **ListView** tidak memiliki tinggi. cara mengatasinya adalah sebagai berikut: 

1. Menambahkan tinggi dengan widget container

```dart
    Column(
          children :[
            Text("this is title"),
            Container(
              height : 300,
              child : ListView.builder(
                    itemBuilder:(c,i)=>Text("halo")
                )
            )
          ]
    ),
```

2. Menambahkan tinggi dengan widget Flexible

```dart
    Column(
          children :[
            Text("this is title"),
            Flexible(
              child : ListView.builder(
                    itemBuilder:(c,i)=>Text("halo")
                )
            )
          ]
        ),
```

3. Menambahkan tinggi dengan widget Expaneded

```dart
    Column(
          children :[
            Text("this is title"),
            Expanded(
              child : ListView.builder(
                    itemBuilder:(c,i)=>Text("halo")
                )
            )
          ]
        ),
```

Sekilas antara Flexible dan Expanded tidak ada perbedaan, akan tetapi perbedaannya ada pada 

- Flexible membuat tinggi menjadi seesuai contentnya
- Expanded membuat listview memiliki tinggi setinggi sisa layar yang belum ditempati widget lainnya

Pada contoh diatas tidak terdapat perbedaan karena panajang widgetnya sama yakni unlimited.

Selanjutnya pada part 3, kita akan membahas solusi list didalam list.

>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>