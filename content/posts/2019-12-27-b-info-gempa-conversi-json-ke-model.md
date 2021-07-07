---
title: Info Gempa - Conversi Json Ke Model
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, iOS, SwiftUI, Tutorial]
---

Pada pembahasan sebelumnya, kita sudah membahas bagaimana membuat sebuah model, sekarang kita masuk kepembahasan yang lebih menarik lagi, yaitu conversi json menjadi object pojo yang sudah kita buat.
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

## Langkah - langkah ##

1. Buka file `NetworkingManager.swift` yang sudah kita buat pada pembahasan [Koneksi API](https://thengoding.com/2019/12/27/6-info-gempa-koneksi-dengan-api/)

2. Edit file tersebut
   
   ## Before ##
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

   ## After ##
   ```swift
         import Foundation
         class NetworkingManager: ObservableObject {
             @Published var dataList = QuakeAPIList(features : [])
             
             init() {
                 
                 guard let url = URL(string : "https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/2.5_day.geojson") else {return}
                 
                 URLSession.shared.dataTask(with:url){
                     (data,_,_) in
                     guard let data = data else {return}
                     let dataList = try! JSONDecoder().decode(QuakeAPIList.self,from:data)
                     DispatchQueue.main.async{
                         self.dataList = dataList
                         print(dataList.features)
                     }
                 }.resume()
                 
             }
         }
   ```

3. Conversi selesai namun kita belum bisa melihat hasil dari aplikasi kita


Bagaimana, gampang bukan pemrograman swift :-) . yang susah itu perangkatnya .. heeee...




>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


