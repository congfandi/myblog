---
title: Info Gempa - Finalisasi Project
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, iOS, SwiftUI, Tutorial]
---

Alhamdulillah sudah sampai dipenghujung tutorial, kali ini kita akan membahas finalisasi project hingga project dapat kita gunakan layaknya sebuah aplikasi.
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

langkah langkah kali ini kita akan membagi memjadi beberapa bagian, yaitu

## Memasukan Model kedalam list ##

1. Buka file `Itemlist`

2. Edit File tersebut menjadi seperti dibawah ini
   
   ```swift
         import SwiftUI

         struct ItemList: View {
             var data : Features
             var body: some View {
                 HStack(alignment: .center, spacing: 9){
                     VStack(alignment: .leading){
                         Text(String(data.properties.mag))
                             .foregroundColor(.white)
                             .font(.headline)
                             .bold()
                     }.frame(width:100,height:100)
                         .background(Color.green)
                         .clipShape(Circle())
                         .overlay(Circle().stroke(Color.gray,lineWidth: 1))
                         .shadow(radius: 10)
                     VStack{
                         Text(data.properties.place)
                             .foregroundColor(.gray)
                             .bold()
                         
                         Text("Time : \(convertTime(timesTamp: data.properties.time))")
                             .italic()
                             .foregroundColor(.orange)
                             .padding(.top,2)
                     }
                 }
             }
             
             func convertTime(timesTamp : Double) -> String {
                 let uniqTime = timesTamp / 1000
                 let date = Date(timeIntervalSince1970: uniqTime)
                 
                 let dateFormatter  = DateFormatter()
                 dateFormatter.timeZone = TimeZone(abbreviation: "GMT+7")
                 dateFormatter.locale = NSLocale.current
                 dateFormatter.dateFormat = "dd MMM yy hh:mm a"
                 
                 return dateFormatter.string(from: date)
             }
         }
   ```

3. Buka file `ContentView.swift` dan edit menjadi seperti dibawah ini
   
   ```swift
         import SwiftUI

         struct ContentView: View {
             @ObservedObject var networkingManager  = NetworkingManager()
             var body: some View {
                 NavigationView{
                     List(networkingManager.dataList.features,id: \.properties){ data in
                         NavigationLink(destination: DetailView(data: data)){
                             CellRow(data: data)
                         }.navigationBarTitle("Info Gempa")
                     }
                 }
             }
         }

         struct ContentView_Previews: PreviewProvider {
             static var previews: some View {
                 ContentView()
             }
         }
   ```

## Mendinamiskan Detail Map ##

Buka file `DetailView.swift` dan edit menjadi seperti dibawah ini

```swift
         import SwiftUI
         import Foundation
         import UIKit
         import MapKit

         struct DetailView: View {
             var data : Features
             var body: some View {
                 ZStack(alignment: .top){
                     MapView(data: data)
                         .edgesIgnoringSafeArea(.all)
                     VStack(alignment: .center, spacing: 6){
                         Text(String(data.properties.mag))
                             .font(.largeTitle)
                         Text(data.properties.place)
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
             var data: Features
             
             func makeUIView(context: Context) -> MKMapView {
                 MKMapView(frame: .zero)
             }
             
             func updateUIView(_ uiView: MKMapView, context: Context) {
                 
                 let annotation = MKPointAnnotation()
                 
                 let coordinate = CLLocationCoordinate2D(latitude: data.geometry.coordinates[1], longitude: data.geometry.coordinates[0])
                 
                 let span = MKCoordinateSpan(latitudeDelta: 1.0, longitudeDelta: 1.0)
                 
                 let region = MKCoordinateRegion(center: coordinate, span: span)
                 
                 uiView.setRegion(region, animated: true)
                 
                 annotation.coordinate = coordinate
                 annotation.title = data.properties.place
                 annotation.subtitle = "Magnitude: \(data.properties.mag)"
                 
                 uiView.addAnnotation(annotation)
                 
                 
             }
             
         }
```

Oke sekian tutorial dari saya, semoga bermanfaat bagi temen2  see you di tutorial selanjtnya yaaa... byeeee




>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


