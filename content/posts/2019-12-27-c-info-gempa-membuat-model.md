---
title: Info Gempa - Membuat Model
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, iOS, SwiftUI, Tutorial]
---

Pada pembahasan kali ini kita akan membahas bagaimana cara mmebuat model pada pemrograman `Swift` dengan menggunakan framework `SwiftUI`.
<!--more-->

## Daftar Isi ##

[Daftar Isi](https://thengoding.com/2019/12/27/j-info-gempa-daftar-isi/)


## Spesifikasi APlikasi ##

|  Spesifikasi  | Keterangan      |
| :------------ |:---------------:|
|  Bahasa       | Swift 5         |
| Framework     | SwiftUI         |
| Editor/Tool   | Xcode 11.3      |
| Platform      | IOS             | 


Model yang akan kita buat adalah sesuai dengan yang dibutuhkan oleh aplikasi dan menyesuaikan dengan `JSON`  yang di dapat dari [API GEMPA](https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/2.5_day.geojson).
Berikut data yang kita butuhkan untuk membuat aplikasi info gempa ini

## Kebutuhan Atribut Model ##

|     Atribut    |      Tipe Data      |       Keterangan        |  
| :--------------| :------------------:|:------------------------|
| mag            | Double              | Informasi kekuatan gempa|
| place          | String              | informasi tempat gempat |
| time           | Double              | informasi waktu gempa   |
| detail         | String              | URL detail gempa        |
| title          | String              | Informasi judul gempa   |
| type           | String              | Tipe Gempa              |
| coordinates    | List Double        | Lat Long gempa (Peta)  |


## Format JSON API ##

```json
    {
        "type": "Feature",
        "properties": {
            "mag": 4.3,
            "place": "291km N of Ndoi Island, Fiji",
            "time": 1577425336477,
            "updated": 1577426822040,
            "tz": -720,
            "url": "https://earthquake.usgs.gov/earthquakes/eventpage/us70006rfs",
            "detail": "https://earthquake.usgs.gov/earthquakes/feed/v1.0/detail/us70006rfs.geojson",
            "felt": null,
            "cdi": null,
            "mmi": null,
            "alert": null,
            "status": "reviewed",
            "tsunami": 0,
            "sig": 284,
            "net": "us",
            "code": "70006rfs",
            "ids": ",us70006rfs,",
            "sources": ",us,",
            "types": ",geoserve,origin,phase-data,",
            "nst": null,
            "dmin": 3.389,
            "rms": 0.85,
            "gap": 74,
            "magType": "mb",
            "type": "earthquake",
            "title": "M 4.3 - 291km N of Ndoi Island, Fiji"
        },
            "geometry": {
            "type": "Point",
            "coordinates": [
                            -178.4009,
                            -18.0347,
                            570.2
                ]
        },
        "id": "us70006rfs"
    }
```

## langkah - Langkah ##

1. Buat sebuah file dengan nama `Quake`
2. Copy dan paste code dibawah ini
   
   ```swift
         import Foundation

         struct Features : Decodable, Hashable{
             var properties : Properties
             var geometry : Geometry
         }

         struct Properties : Decodable, Hashable {
             var mag : Double
             var place  : String
             var time : Double
             var detail : String
             var title : String
         }

         struct Geometry : Decodable, Hashable {
             var type : String
             var coordinates : [Double]
         }

         struct QuakeAPIList : Decodable {
             var features : [Features]
         }
   ```

3. Model selesai dibuat,


## Penjelasan Model ##

1. `struct` menunjukan pojo/model
   
2. kelas `Features` dibuat karena atribut yang dibutuhkan ada didalam list dengan nama `Features`
   
3. kelas `Properties` dibuat karena atribut yang dibutuhkan ada dalan json object ini
   
4. kelas `Geometry` dibuat karena atribut `type` dan `coordinates` ada dalam json object ini
   
5. kelas `QuakeAPIList` dibuat untuk menampung seluruh return yang di dapat dari api untuk selanjutnya diconversi kedalam bentuk object



Oke sekian pada modul tutorial kali ini, selanjutnya kita akan mengconversi json menjadi pojo seperti yang sudah kita buat ini.


>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


