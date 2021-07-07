---
title: Firebase analytics debuging mode #judul postingan
img:  210701/banner.png #gambar postingan taruh di assets/img dan langsung call nama imagenya
layout: post #default jangan diganti
author: Cong Fandi #default me
author-img : congfandi.jpeg #default me
author-detail : iOS Developer, Android Developer, Web Developer # default me
fig-caption: Developer #default me
tags: [Developer, iOS, iPhone, Firebase]# tags dalam array [Developer, Web, Tips]
---

Halo sobat ngoding yang budiman, kali ini saya ingin berbagi tentang cara membuka debuging mode pada firebase analytics. Kenapa butuh debuging mode? karena saat developer mengimplementasikan firebase analytics kedalam aplikasi berupa mobile dan web, hasilnya tidak dapat dilihat secara langsung saat itu juga harus menunggu setidaknya seharian paling sedikit. Oelh sebab itu maka lahirlah sebiah metode yang disebut *DebugView* pada firebase console sehingga developer dapat melihat hasil dari implementasi firebase analytics.

Hasil dapat dilihat pada gambar dibawah ini :
![Firebase]({{site.url}}/assets/img/210701/firebase.png)

 Oke kita langsung saja pada tutorial.

## Langkah langkah

1. Kalian wajib buat dulu project kalian di [fierbase console](https://console.firebase.google.com/)

2. Kalian wajib implementasi firebase analytics di project kalian baik itu web maupun apps di android maupun di ios

3. Bagian ini yang sangat penting,


### Debuging mode di Android ###
- Buka terminal di root project temen temen
- Ketikkan perintah berikut ini

```terminal
    adb shell setprop debug.firebase.analytics.app package_name
```
ganti *package_name* dengan nama package apliksi temen temen.
- hasil kemudian restart aplikasi dan tunggu hasilnya setelah beberapa menit. dan jangan lupa di resfresh halaman debug consolenya ya.

### Debuging mode di IOS ###
- Buka XCODE temen temen
- masuk ke menu *edit schema* danlihat
- Tambahkan script berikut pada bagian *Argumnents* tab
- Kemudian pada menu *Arguments Passed On Lauch* tambahkan script berikut
    
    1. *-DIRDebugEnabled*
    2. *-FIRAnalyticsVerboseLoggingEnabled*
    3. *-FIRAnalyticsDebugEnable*
    
    Lengkapnya coba perhatikan gambar dibawah ini : 

    ![xcode config]({{site.url}}/assets/img/210701/xcode1.png)
- Restart aplikasi temen temen dengan cara menjalankan kembali dari xcode temen temen.

    
### Debuging mode di WEB ###
Cukup berbeda dengan cara yang ada di android dan ios, untuk mengaktifkan debuging mode di web app, kalian hanya perlu 
- Gunakan google chrome
- Masuk ke [google chrome store](https://chrome.google.com/webstore/search/Google%20analytics%20debuger)
- install extention [Google Analytics Debuger](https://chrome.google.com/webstore/search/Google%20analytics%20debuger)
- Selesai.


Untuk melihat hasilnya, teman teman cukup kembali ke firebase console teman teman dan tunggu beberapa menit, tentunya dalam keadaan kondisi aplikasi dirunning ya hasilnya dapat dilihat secara realtime sebagaimana pada gambar pertama.

Cukup sekian teman teman jika ada yang perlu untuk di diskusikan silahakn masukan pertanyaan dibawah atau bisa langsung chatting di bagian pojok kanan bawah.


*Source : [https://firebase.google.com/docs/analytics/debugview#web](https://firebase.google.com/docs/analytics/debugview#web)*
    


<br>
<br>
>Jika kau tidak mampu menahan sulitnya belajar, maka kau harus siap menahan perihnya kebodohan<small> - Imam Syafi'i</small>