---
title: Upload project ke github
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Github, Tutorial]
---

Tutorial kali ini adalah cara sederhana memasukan peoject/folder/file kita ke github, gitlab atau bitbucket. Tutorial ini membahas secara sederhana saja, kita mulai saja.
<!--more-->
**Langkah-Langkah mengupload file ke github**
1. Daftar dulu ke [Github](https://github.com)
   
2. Pastikan komputer kalian sudah terinstall git, jika kalian menggunakan *Windows* tutorial nya [disini](https://www.petanikode.com/git-install/), bagi pengguna linux, ketikan saja perintah
   
        sudo apt-install git
   
    bagi penggunana mac, ketikkan saja perintah ini di terminal

    
        brew install git
    

    jika sudah terintall, pastikan git terinstall dengan baik dengan mengetikkan perintah ini di terminal

    
        git --version
    

    jika terminal kalian keluar tulisan seperti dibawah ini

    
        git version 2.21.0

    itu artinya komputer kalian sudah terinstall dengan baik.

3. Oke sekarang kita buat sebuah folder, di **Desktop** dengan nama **`Coba`**, 
4. Kemudian buat lah file didalamnya dengan nama **`README.md`** 
5. Dan isilah file itu dengan tulisan 

    ```md
        hai ini adalah file readme yang ada di folder git saya.
    ```

    Struktur folder nya dapat dilihat pada gambar 1

    ![Gambar 1](/../img/30-03-2019/gambar1.png)

6. Langkah selanjutnya adalah buka terminal kalian kemudian masuk ke direktori Desktop/Coba. Kalau di komputer saya saya(Mac) tinggal mengetikkan perintah ini

    ```terminal
    cd Desktop/Coba
    ```

7. Ketikkan perintah 
   ```
        git init
   ```
8. Buat repository pada akun github kalian
    ![Github](/../img/30-03-2019/cover.png)
    tombol **New** 
9.  Isi kolom sesuai dengn yang kalian mau, tapi saran saya disamakan dengan nama folder yang kalian buat.
![gambar 2](/../img/30-03-2019/gambar2.png)
untuk pengaturan yang tidak disebutkan di tutorial ini silahkan di atur sesuai kebutuhanmu.
10. Copy URL project seperti pada gambar dibawah
    ![Gambar 4](/../img/30-03-2019/gambar4.png)
11. Kembali lagi ke terminal dimana peoject mu berada
12. ketikkan perintah
        
        git remote add origin url_repository_kalian

13. kemudian ketikkan perintah

        git add .

14. dilanjutkan dengan perintah
    
        git commit -m "pesan kalian terserah"

15. kemudian yang terakhir adalah
    
        git push -u origin master

    jika berhasil, seharusnya kalian sudah bisa melihat hasilnya di repositori kalian seperti gambat dibawah ini

![gambar hasil](/../img/30-03-2019/sukses.png)


**Udate repository**
Tambahkan file appun di dalam direktory **Coba** kemudian jalankan perintah ini di terminal, jika berhasil seharusnya file yang kalian masuka tadi sudah bisa dilihat di repository kalian.
```
   1. git add .
```
```
   2. git commit -m "pesanmu"
```
```
   3. git push
```



Oke sekian dari saya, maaf atas kesalah typo tulisan jika ada dan maaf atas kesalahan kata jika ada kata yang menyinggung kalian, akhir kata. **Happy Coding**

>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


