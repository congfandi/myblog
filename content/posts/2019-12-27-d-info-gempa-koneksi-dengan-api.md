---
title: Info Gempa - Koneksi dengan API
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, iOS, SwiftUI, Tutorial]
---

Kita sudah selesai membuat membuat tampilan aplikasi, saatnya kita membuat koneksi dengan real data dengan menggunakan API
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


## langkah - Langkah ##

1. API daftar gempa dapat anda lihat pada link ini [API GEMPA](https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/2.5_day.geojson)
   
2. Buat file dan beri nama `NetworkingManager.swift`

3. Kemudian copy dan paste code dibawah ini
   
   ```swift
         import Foundation
         class NetworkingManager{
             
        
             init() {
                 
                 guard let url = URL(string : "https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/2.5_day.geojson") else {return}
                 
                 URLSession.shared.dataTask(with:url){
                     (data,_,_) in
                     guard let data = data else {return}
                     print(data)
                 }.resume()
                 
             }
         }

   ```

4. Koneksi dengan api sudah selseai, namun hasilnya belum bisa dilihat.. kita akan bahas pada modul selanjutnya








>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


