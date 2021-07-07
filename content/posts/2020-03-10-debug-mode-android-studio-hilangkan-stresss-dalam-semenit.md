---
title: Debug Mode Android Studio hilangkan stress dalam semenit
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Android Studio, Tips]
---

Halo sobat ngoding semua, kali ini saya mau berbagi tentang sebuah cara yang bisa kalian lakukan untuk melakukan debug aplikasi kalian di android studio. Jangan perhatikan judulnya ya itu cuman buat seru seruan aja :-D.

Oke kita mulai dari latar belakang saya membuat tulisan ini, barangkali ada yang melakukan hal yang sama dengan yang saya lakukan.
<!--more-->
## Latar belakang ##
Teman-teman pembuat aplikasi yang menggunakan tool `Android Studio` sebagai editor pasti kenal dong dengan yang namanya *print("test")* dan *Log.e("haiiii")*. iya kedua script ini digunakan untuk menampilkan sebuah nilai atau melihat nilai atau mengetes script kita jalan atau tidak. Cukup menjengkelkan jika kita harus menjalankan dulu semua aplikasinya kemudian kita lihat hasilnya di `console` kita. 


## Solusi ##
Setelah saya bertanya kepada teman saya terkait cara yang enak (ingat bukan cara terbaik ya) buat debug mode di android studio, diapun menunjukkannya kepada saya dan ternyata android studio sudah menyediakannya dan sangat mudah untuk mengakses nya nama menu nya *Debug*


## Simulasi ##
Sekarang kita langsung aja ya ke simulasinya.

1. Buka project teman-teman (Android atau flutter)

2. Cari sebuah method yang kalian ingin cek nilai dari masing masing parameternya

![Preferances]({{ site.baseurl }}/img/200310/first.png)

Contoh pada gambar diatas adalah saya ingin melihat nilai dari parameter *_clockType* yang ditampilkan saat saya mengakses kelas `ClockInProvider`

3. Beri break point pada akhir method agar nilainya dapat di set dulu seperti pada gambar diatas

4. jalankan aplikasi dengan mengklik *Debug* bukan yang run, lihat gambar dibawah

![Preferances]({{ site.baseurl }}/img/200310/second.png)

5. Akses fitur atau menu yang menjalankan fungsi/method/kelas yang diberi tanda break point tadi

6. **Apliakasi akan terhendi dibreak point dan seolah2 aplikasi terhendi atau error atau bug, akan tetapi tidak, sebenarnya aplikasi berhenti karena adanya breakpoint tadi**

7. Sorot nilai dan lihat datanya (menggunakan cursor) dan nilai dari parameter akan muncul

8. Jika tidak muncul saat disorot yang kalian lakukan adalah

|>Klik kanan pada parameter > Evaluate Expression

dan hasilnya dapat dilihat dibawah ini

![Preferances]({{ site.baseurl }}/img/200310/last.png)


Kalian bisa memberikan banyak breakpoint pada 1 file atau 1 kelas baik berbeda2 maupun sama kelas.

Oh iya, jika kalian ingin melanjutkan tekan aja *F9* fungsi ini digunakan untuk next break point, jika tidak ada lagi aplikasi langsung jalan seperti biasa jika masih ada break point lagi dia akan ke break point selanjutnya.

Btw, terima kasih buat [Mas Umam](https://www.linkedin.com/in/muhammad-sa-idul-umam-47a56b183/) yang uda bersedia ngajarin saya cara debug mode di android studio, semoga ilmunya tambah berkah :-) .

Oke sobat ngoding cukup sekian dulu tulisan singkat saya kali ini, semoga bermanfaat.

>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


