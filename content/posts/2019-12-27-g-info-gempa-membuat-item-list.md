---
title: Info Gempa - Membuat Item List
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, iOS, SwiftUI, Tutorial]
---

Pada tutorial kali ini, kita akan membuat item list pada halaman utama aplikasi
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


setelah selesai membuat list, saatnya kita membuat item list sehingga nampak lebih bagus tampilannya, langkah - langkah nya adalah sebagai berikut : 

## Langkah - Langkah ##

1. Buka Project File temen - temen pada xcode
   
2. Klik kanan kemudian `New File`
   
   ![list]({{ site.baseurl }}/img/191217/new.png)
   
3. Pilih `SwiftUI`
   
   ![list]({{ site.baseurl }}/img/191217/swiftui.png)
   
4. Beli nama file yang kita buat dengan `ItemList`
   
5. Ganti code nya
    
    **Before**

      ```swift
           import SwiftUI

         struct ContentView: View {
             var body: some View {
                     Text("Hello, World!")
             }
         }

         struct ContentView_Previews: PreviewProvider {
             static var previews: some View {
                     ContentView()
                 }
         }
      ```

    Menjadi seperti ini 

    **After**

      ```swift
           import SwiftUI

           struct ItemList: View {
                   var body: some View {
                       HStack(alignment: .center, spacing: 9){
                           VStack(alignment: .leading){
                               Text("4.5")
                                   .foregroundColor(.white)
                                   .font(.headline)
                                   .bold()
                           }.frame(width:100,height:100)
                               .background(Color.green)
                               .clipShape(Circle())
                               .overlay(Circle().stroke(Color.gray,lineWidth: 1))
                               .shadow(radius: 10)
                           VStack{
                               Text("4KM Coba, Coba")
                                   .foregroundColor(.gray)
                                   .bold()
                               
                               Text("Time : 25 December 2019")
                                   .italic()
                                   .foregroundColor(.orange)
                                   .padding(.top,2)
                           }
                       }
                   }
               }

           struct ContentView_Previews: PreviewProvider {
               static var previews: some View {
                   ItemList()
               }
           }
      ```

6. Buka file `ContentView.swift` dan ganti menjadi seperti ini

    ```swift

        import SwiftUI
        struct ContentView: View {
            var body: some View {
                List{
                    ForEach(0...10,id: \.self){ index in
                    ItemList()
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
   
7. Maka tampilannya seperti dibawah ini

     ![list]({{ site.baseurl }}/img/191217/list-final.png) 
  


>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


