---
title: Info Gempa - Membuat Peta
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, iOS, SwiftUI, Tutorial]
---

Pada tutorial kali ini, kita akan membuat detail halaman yang merupakan tampilan peta atau map
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

1. Buat file baru dengan nama `DetailView.swift`
2. Tuliskan code dibawah ini
   
   ```swift
         import SwiftUI
         import Foundation
         import UIKit
         import MapKit

         struct DetailView: View {
             var lat = 1.0
             var long = 1.0
             var name = "Some Name"
             var mag = 1.0
             var body: some View {
                 ZStack(alignment: .top){
                     MapView(lat:lat,long:long,name:name,mag:mag)
                         .edgesIgnoringSafeArea(.all)
                     VStack(alignment: .center, spacing: 6){
                         Text(mag)
                             .font(.largeTitle)
                         Text(name)
                     }.clipShape(Rectangle())
                         .frame(width:nil,height: nil)
                         .padding(.all,20)
                         .background(Color.green)
                         .shadow(radius: 9)
                         .cornerRadius(9)
                         .opacity(0.8)
                 }
             }
         }

         struct MapView: UIViewRepresentable {
             var lat : double
             var long : double
             var name : String
             var mag : double
             
             func makeUIView(context: Context) -> MKMapView {
                 MKMapView(frame: .zero)
             }
             
             func updateUIView(_ uiView: MKMapView, context: Context) {
                 
                 let annotation = MKPointAnnotation()
                 
                 let coordinate = CLLocationCoordinate2D(latitude: lat, longitude: long)
                 
                 let span = MKCoordinateSpan(latitudeDelta: 1.0, longitudeDelta: 1.0)
                 
                 let region = MKCoordinateRegion(center: coordinate, span: span)
                 
                 uiView.setRegion(region, animated: true)
                 
                 annotation.coordinate = coordinate
                 annotation.title = name
                 annotation.subtitle = "Magnitude: \(mag)"
                 
                 uiView.addAnnotation(annotation)
                 
                 
             }
             
         }


   ```


3. Jalankan aplikasinya dan lihat hasilnya 
   
   ![map]({{ site.baseurl }}/img/191227/map.png)

>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


