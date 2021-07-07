---
title: Membuat Gridlist Sendiri #judul postingan
img: 200919/cover.jpg #gambar postingan taruh di assets/img dan langsung call nama imagenya
layout: post #default jangan diganti
author: Cong Fandi #default me
author-img : congfandi.jpeg #default me
author-detail : iOS Developer, Android Developer, Web Developer # default me
fig-caption: Developer #default me
tags: [Developer, Flutter, Tips] # tags dalam array [Developer, Web, Tips]
---
Hola sobat ngoding, udah lama banget nih saya tidak menyapa temen-temen semua karena kesibukan ditempat kerja. Oke kali ini saya ingin membuat tutorial tentang membuat grislist sendiri nih di flutter. lho kenapa ko ini penting ? karena saya sendiri pernah membuat gridlist yang itemnya tidak bisa saya custom dan itu sangat merepotkan, akhirnya saya buat gridlist saya sendiri yang full custom dan dapat dengan mudah di maintanance.

Oke sebelum kita mulai, aku sedikit cerita dulu ya, 

Jadi gridlist kita ini sebeanrnya gabungan antara Row dan Colum, boleh Colum duluan atau boleh Row duluan.

Yuk kita langsung ke kodingan.

## Gridlist dengan Susunan Colum dan Row

```dart
    int pos = 0;
    Column(
            children: List.generate(
            10,
            (index) {
            return Row(
                children: List.generate(
                2,
                (index) {
                    pos++;
                    return Expanded(
                    child: pos >= 10
                        ? Container()
                        : Container(width:100,height:30,color:Colours.blue),
                    flex: 1,
                    );
                },
                ),
            );
            },
        ),
    )
```


## Gridlist dengan Susunan Row dan Colum

```dart
    int pos = 0;
    Row(
            children: List.generate(
            2,
            (i) {
                pos=i;
            return Column(
                children: List.generate(
                10/2,
                (j) {
                    pos+=2;
                    return Expanded(
                    child: pos >= 10
                        ? Container()
                        : Container(width:100,height:30,color:Colours.blue),
                    flex: 1,
                    );
                },
                ),
            );
            },
        ),
    )
```


bagaimana guys ? mudah bukan ?

oh iya, ada beberapa kode yang sengaja saya salahkan ya :-V, selamat ber eksplorasi dengan kode kode diatas..

<br>
<br>
>Sekedar ingin berbagi, dan bukan yang paling mampu<small> - Penulis</small>

