---
title: Mengganti Domain Github page dengan domain sendiri
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Github, Domain, Tutorial]
---

Tulisan ini request dari teman saya, tentang gimana cara set DNS github page dengan domain sendiri,

langsung aja tutorial nya...
<!--more-->

## Simulasi ##

1. Sudah punya github page, kalau belum bisa ikut tutorial di alamat ini [https://pages.github.com/](https://pages.github.com/)

2. Sudah punya domain sendiri, kalau belum punya silahkan beli dulu dtempat yang kamu suka,


## Langkah - langkah  pada bagian Github ##

1. Masuk ke github teman-teman atau klik link ini [github.com](github.com)

2. Masuk ke reposotory github page teman-teman

3. Masuk ke pengaturan, lihat gambar dibawah ini
   
   ![akungit]({{ site.baseurl }}/img/191215/pengaturan-github.png)

4. Scroll kebawah hingga ketemu tulisa `Custom Domain`

5. Masukan alamat domain yang sudah sobat beli, lihat gambar dibawah ini

  ![customer-domain]({{ site.baseurl }}/img/191215/custome-domain.png)


## Langkah - langkah pada domain kamu ##

1. Masuk `cpanel/clien tarea` domain teman-teman

2. Masuk ke pengaturan DNS

3. tambahkan setting berikut pada pengaturan DNS teman-teman

   |       Domain       |       Type       |         Destination        |
   |:------------------:|:----------------:|:--------------------------:|
   |       WWW          |       CNAME      |   *`congfandi`*.github.io  |
   |  *`mydomain.com`*  |        A         |   185.199.108.153          |
   |  *`mydomain.com`*  |        A         |   185.199.109.153          |
   |  *`mydomain.com`*  |        A         |   185.199.110.153          |
   |  *`mydomain.com`*  |        A         |   185.199.111.153          |

   Keterangan : 
     
     - Ganti *`congfandi`* dengan nama git page teman teman
     
     - Ganti *`mydomain.com`* dengan domain teman teman

Untuk mengaktifkan HTTPS nya, teman teman harus menunggu selama 1 x 24 jam , baru setelah itu secara otomatis HTTPS nya akan aktif, jika teman teman mengatur pada bagian `Enforce HTTPS` pada bagian setting `Github page`


Sekian tulisan saya kali ini, semoga dapat menambah wawasan teman-teman..

terima kasih sudah berkunjung :-) .




>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


