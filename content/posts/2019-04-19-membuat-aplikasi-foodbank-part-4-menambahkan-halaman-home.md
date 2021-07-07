---
title: Android Native Membuat aplikasi foodbank part 4 - Menambahkan halam home
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Android, JAVA, Tutorial]
---
![Cover](/../img/covers/cover-19-04-2019.png)
Kita berjumpa lagi di pertemuan yang ke empat, tak terasa sudah sampai pada modul utama, yaitu menambahkan halaman utama aplikas.
<!--more-->
Oke kita langsung saja menuju tutorial.

**Menambahkan `Action` pada tombol login**
Silahkan berikan aksi pada tombol `login` yang ada pada halaman `LoginScreen`, dan arahkan menuju halaman `MainActivity`.


Jika sudah seksai, kita lanjut ke tutorial selanjutnya.

**Menambahkan `ActionBar` pada halaman `MainActivity`**

1. Tambahkan sebuah folder pada direktori `res` dengan cara 
   - Klik kanan pada folder `res`
   - Pilih `New`
   - Pilih `Android Resource Directory`
   - Atur seperti pada gambar 1
    ![gambar 1](/../img/19-04-2019/1.png)
    *Gambar 1*
2. Klik kanan pada folder `menu` yang sudah kalian buat kemudian tambahkan sebuah file dengan nama `mytoolbar` cara nya adalah sebagai berikut
    - Klik kanan folder `menu`
    - Pilih `New`
    - Pilih `menu resource file`
    - atur seperti gambar 2
    ![gambar 2](/../img/19-04-2019/2.png)
    *gambar 2*
3. Buka dan edit file `mytoolbar` seperti code berikut
   ```xml
        <menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">
            <item
                android:id="@+id/miCompose"
                android:icon="@drawable/keranjang"
                app:showAsAction="always"
                android:title="Keranjang">
            </item>
        </menu>
   ```
   
**Menambahkan `mytoolbar` kedalam halaman `MainActivity`**
1. Buka file `MainActivity`
2. tambahkan kode berikut tepat didalam kelas `MainActivity`
   ```java
         @Override
         public boolean onCreateOptionsMenu(Menu myMenu) {
            getMenuInflater().inflate(R.menu.mytoolbar, myMenu);
        return true;
        }
   ```
3. Silahkan jalankan aplikasinya dan lihat hasilnya.


**Menambahkan `Color`**

1. Buka file `colors.xml` yang ada pada folder `res/values`
2. Tambah kode berikut didalmnya
   ```xml
        <color name="colorOrange">#FD7D38</color>
        <color name="colorAbuabu">#E6E6E6</color>
   ```

**Menambahkan icon**

berikut nama-nama icon yang temen-temen butuhkan :
1. Icon untuk halaman list
   - ic_list_orange.xml
   - ic_list_white.xml
2. Icon untuk halaman grid
   - ic_grid_orange.xml
   - ic_grid_white.xml
3. Icon untuk halaman profil
   - ic_person_orange.xml
   - ic_person_white.xml

*Keterangan :*
  - [ ] Silahkan gunakan icon yang temen-temen suka dan warna yang temen-temen suka
  - [ ] Nama file disamakan dahulu, apabila sudah sukses dan tidak terjadi error dengan koding temen-temen silahkan edit sesuka hati.


**Menambahkan 3 tombol di bawah `Toolbar`**
1. Buka file `activity_main.xml`
2. Edit menjadi seperti code dibawah ini
   ```xml
        <?xml version="1.0" encoding="utf-8"?>
            <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
                xmlns:app="http://schemas.android.com/apk/res-auto"
                xmlns:tools="http://schemas.android.com/tools"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                tools:context=".views.MainActivity">

                <LinearLayout
                    android:id="@+id/layout_filter"
                    android:layout_width="match_parent"
                    android:layout_height="40.0dp"
                    android:background="#E6E6E6"
                    android:orientation="horizontal">

                    <RelativeLayout
                        android:id="@+id/btn_list"
                        android:layout_width="match_parent"
                        android:layout_height="match_parent"
                        android:layout_weight="1">

                        <ImageView
                            android:id="@+id/icon_list"
                            android:layout_width="wrap_content"
                            android:layout_height="wrap_content"
                            android:layout_centerInParent="true"
                            android:src="@drawable/ic_list_orange" />
                    </RelativeLayout>

                    <RelativeLayout
                        android:id="@+id/btn_grid"
                        android:layout_width="match_parent"
                        android:layout_height="match_parent"
                        android:layout_weight="1">

                        <ImageView
                            android:id="@+id/icon_grid"
                            android:layout_width="wrap_content"
                            android:layout_height="wrap_content"
                            android:layout_centerInParent="true"
                            android:src="@drawable/ic_grid_orange" />
                    </RelativeLayout>

                    <RelativeLayout
                        android:id="@+id/btn_profil"
                        android:layout_width="match_parent"
                        android:layout_height="match_parent"
                        android:layout_weight="1">

                        <ImageView
                            android:id="@+id/icon_profil"
                            android:layout_width="wrap_content"
                            android:layout_height="wrap_content"
                            android:layout_centerInParent="true"
                            android:src="@drawable/ic_person_orange" />
                    </RelativeLayout>
                </LinearLayout>

                <FrameLayout
                    android:id="@+id/container"
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:layout_below="@+id/layout_filter" />
            </RelativeLayout>
   ```
3. Hasil nya akan nampak seperti gambar 3
   ![Gambar 3](/../img/19-04-2019/3.png)
   *Gambar 3*

**Membuat logic tombol filter**
1. Buka file `MainActivity`
2. tambahkan kode berikut
   ```java
        RelativeLayout btnList, btnGrid, btnProfil;
        ImageView iconList, iconGrid, iconProfil;

        private void setFilter() {
            btnList = findViewById(R.id.btn_list);
            btnGrid = findViewById(R.id.btn_grid);
            btnProfil = findViewById(R.id.btn_profil);
            iconList = findViewById(R.id.icon_list);
            iconGrid = findViewById(R.id.icon_grid);
            iconProfil = findViewById(R.id.icon_profil);

            setBackgroundTombol(1);

            btnList.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    setBackgroundTombol(1);
                }
            });
            btnGrid.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    setBackgroundTombol(2);
                }
            });
            btnProfil.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    setBackgroundTombol(3);
                }
            });
        }

        private void setBackgroundTombol(int tombolYangDiKlik) {
            //Asumsi
            //tombolYangDiKlik == 1 maka yang di klik adalah tombol list
            //tombolYangDiKlik == 2 maka yang di klik adalah tombol grid
            //tombolYangDiKlik == 1 maka yang di klik adalah tombol profil
            btnList.setBackgroundColor(getResources().getColor(tombolYangDiKlik == 1 ? R.color.colorOrange : R.color.colorAbuabu));
            btnGrid.setBackgroundColor(getResources().getColor(tombolYangDiKlik == 2 ? R.color.colorOrange : R.color.colorAbuabu));
            btnProfil.setBackgroundColor(getResources().getColor(tombolYangDiKlik == 3 ? R.color.colorOrange : R.color.colorAbuabu));
            iconList.setImageDrawable(getResources().getDrawable(tombolYangDiKlik == 1 ? R.drawable.ic_list_white : R.drawable.ic_list_orange));
            iconGrid.setImageDrawable(getResources().getDrawable(tombolYangDiKlik == 2 ? R.drawable.ic_grid_white : R.drawable.ic_grid_orange));
            iconProfil.setImageDrawable(getResources().getDrawable(tombolYangDiKlik == 3 ? R.drawable.ic_person_white : R.drawable.ic_person_orange));
            getSupportFragmentManager()
                    .beginTransaction()
                    .replace(R.id.container, tombolYangDiKlik == 1
                            ? new HalamanList() : tombolYangDiKlik == 2
                            ? new HalamanGrid() :
                            new HalamanProfil())
                    .commit();
            }
   ```


**Membuat halaman *`HalamanList`*, *`HalamanGrid`* dan halaman *`HalamanProfile`***

1. Klik kanan pada folder `views`
2. Pilih `New`
3. Pilih Fragment
4. Pilih `Fragment(Blank)`
5. Atur **Sama Persis** dengan yang ada pada gambar 4
   ![Gambar 4](/../img/19-04-2019/4.png)
   *Gambar 4*
6. Buat halaman yang lain nya sesuai dengan yang ada pada koding teman-teman.

jika koding kaliasn sukses, seharusnya akan nampak seperti gift dibawah ini.

![Gift](/../img/19-04-2019/gif.gif)

Cukup sekian untuk tutorial kali ini, semoga dapat bermanfaat, maaf atas kekurangan yang ada.


>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


