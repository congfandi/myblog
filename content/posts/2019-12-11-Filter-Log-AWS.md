---
title: Filter Log AWS
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, AWS, Tutorial]
---

Hallo guys, kali ini saya mau share tentang filter AWS logging , ini sangat bermanfaat bagi kalian yang sedang menggunakan AWS sebagai server kalian,
<!--more-->   
oke kita langsung saja pada pembahasan,


sebagai contoh kasus kita memiliki logging dengan type json seperti dibawah ini

```json
{

"statusCode" : 200,

"message" : "succes",

"data": {

           "resultCode":120,

     }

 "result" : [

                  {

                     "id": 12,

                  }

              ]

}
```

Untuk memfilter berdasarkan `statusCode` saja maka yang harus diketik pada filter seperti dibawah ini

```json
{$.statusCode = 200}
```

Untuk memfilter berdasarkan `resultCode`

```json
{$.data.resultCode = 120}
```

Untuk memfilter berdasarkan resultnya, maka yang harus diketik adalah

```json
{$.result[0].id = 12}
```

Sekian tutorial kali ini semoga bermanfaat.

Jika ada yang mau didiskusikan silahkan hubungi saya lewat semua social media yang saya sertakan di blog ini.

>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


