---
title: Info Gempa - Membuat list
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, iOS, SwiftUI, Tutorial]
---

Pada tutorial kali ini, kita akan membuat list pada halaman utama aplikasi
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


Oke kita langsung saja ke TKP :-D 

##  langkah-langkah ##

1. Buka file `ContentView.swift`
   
2. Ganti Code Berikut
    
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

    menjadi seperti ini

    **After**

    ```swift
        import SwiftUI

        struct ContentView: View {
            var body: some View {
                List{
                    ForEach(0...10,id: \.self){ index in
                        Text("halo \(index)")
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

sehingga tampilannya akan seperti dibawah ini

![list]({{ site.baseurl }}/img/191217/list.png)

cukup sekian pembahasan pembuatan list, selanjutnya kita akan membahas pembuatan item pada list yang kita buat pada tutorial ini.. sampai jumpa di tutorial selanjutnya...


>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


