---
title: Android Native Membuat Aplikasi Foodbank Part 1
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Android, JAVA, Tutorial]
---

![Cover](/../img/foodbank1/cover.png)
Bismillah, 

Tutorial kali ini khusus untuk teman-teman Universitas Muhammadiyah Gresik (UMG) yang mengadakan Event Tahunan **HRC**. Event ini diselengarakan oleh Himatif UMG dengan kerja sama dengan **GresikDev**.
<!--more-->
Pada tutorial ini, kita akan mencoba membuat sebuah aplikasi bank makanan (Foodbank) dimana Mockup dari aplikasi ini dapat dilihat [disini](https://www.behance.net/gallery/67347541/FoodBank-Restaurant-App-UI-Kit).

Oke kita mulai saja tutorialnya.

**Tutorial Membuat Foodbank**
1. Buat aplikasi dengan menggunakan **Android Studio**
2. Atur project seperti gambar 1
   ![Gambar 1](/../img/foodbank1/gambar1.png)
   *Gambar 1*

   saya sangat menyarankan teman-teman utntuk mengatur aplikasi seperti yang ada pada gambar 1.0 agar tidak terjadi error yang tidak di inginkan, jika ingin membuat yang berbeda silahkan tapi lakukan hal itu diluar kelas ya .
3. Setelah project selesai dibuat, Buatlah beberapa folder yang ada didalam `id.gresikdev.foodbank`  antara lain **models** , **views**, **controllers** seperti gambar 2
![Gambar 2](/../img/foodbank1/gambar2.png)
    *Gambar 2*

4. Masih didalam folder(istilah lainnya *package*) `id.gresikdev.foodbank` kita pindahkan file `MainActivity` kedalam *package* **views** kemudian buat beberapa *Activity* `LoginActivity`, `RegisterActivity`, `SplashActivity` dan `WelcomeActivity` dengan cara : Klik kanan pada *package* **views** => **New** => **Activity** => **Empty Activity**.
Struktur file dapat dilihat pada gambar 3.
![Gambar 3](/../img/foodbank1/gambar3.png)
*Gambar 3*

5. Jalankan aplikasi, maka aplikasi akan terlihat seperti gambar 4 
   ![Gambar 4](/../img/foodbank1/gambar4.png).
*Gambar 4*

Selanjutnya kita akan membuat agar aplikasi berjalan seperti ini
**SplashActivity** => **WelcomeActivity** => **LoginActivity**/**RegisterActivity**, langkah-langkahnya adalah sebagai berikut :
1. Buka file `AndroidManifest.xml` yang ada pada folder **manifests**
2. Edit file yang sebelumya 
   ```xml
    <activity android:name=".views.RegisterActivity"></activity>
    <activity android:name=".views.LoginActivity" />
    <activity android:name=".views.WelcomeActivity" />
    <activity android:name=".views.SplashActivity" />
    <activity android:name=".views.MainActivity">
        <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
    </activity>
   ```
   menjadi seperti ini
   ```xml
        <activity android:name=".views.RegisterActivity"></activity>
        <activity android:name=".views.LoginActivity" />
        <activity android:name=".views.WelcomeActivity" />
        <activity android:name=".views.MainActivity" />
        <activity android:name=".views.SplashActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
   ```
jika dijalankan, aplikasi tidak lagi mengarah pada *Activity* `MainActivity` akan tetapi sudah mengarah pada `SplashActivity`. langkah selanjutnya kita akan mrugah tampilan `SplashActivity`.

**Merubah Tampilan `SplashActivty`**
1. Buka File `activity_splash.xml`, file ini ada pada package *res* => *layout*
2. kemudian tuliskan code berikut pada tab *Teks*
   ```xml
        <?xml version="1.0" encoding="utf-8"?>
        <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
            xmlns:app="http://schemas.android.com/apk/res-auto"
            xmlns:tools="http://schemas.android.com/tools"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            tools:context=".views.SplashActivity">
            <ImageView
                android:src="@mipmap/ic_launcher"
                android:layout_centerInParent="true"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content" />
            <TextView
                android:text="Versi 1.0.0"
                android:layout_marginBottom="20.0dp"
                android:layout_centerHorizontal="true"
                android:layout_alignParentBottom="true"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content" />
        </RelativeLayout>
    ```
Saat aplikasi dijalankan, *activity* `SplashActivity` masih memiliki *toolbar* padahal seharusnya activity ini tidak memiliki toolbar lihat gambar 5.
![Gambar 5](/../img/foodbank1/gambar5.png)
*Gambar 5*

maka kita hilangkan dulu toolbarnya.

**Menghilangkan *toolbar* pada *activity* `SplashActivity`**
1. Buka file `styles.xml` yang ada pada package *res* => *values* => `styles.xml`
2. tambah kode berikut 
   ```xml
        <!--Tema tanpa toolbar-->
    <style name="tanpaToolbar" parent="Theme.AppCompat.Light.NoActionBar">
        <!-- Customize your theme here. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
        <item name="colorAccent">@color/colorAccent</item>
    </style>
   ```
3. buka lagi file `AndroidManifest.xml`, kemudian tambahkan kode berikut
   ````xml
        <activity android:name=".views.SplashActivity" android:theme="@style/tanpaToolbar">
   ```
kemudian jalankan aplikasi dan *toolbar* akan otomatis hilang. lihat gambar 6
![Gambar 6](/../img/foodbank1/gambar6.png)
*Gambar 6*

Langkah selanjutnya adalah membuat aplikasi secara otomatis berpindah halaman setelah 3 detik, oke kita mulai saja:

**Memindahkan halaman secara otomatis dalam 3 detik**
1. buka file `SplashActivity.java` 
2. buatlah method dengan nama *pergiKeWelcome*
    ```java
         private void pergiKeWelcome(){
        TimerTask task = new TimerTask() {
            @Override
            public void run() {
                startActivity(new Intent(SplashActivity.this,WelcomeActivity.class));
            }
        };
        Timer timer = new Timer("Pindah Halaman");
        timer.schedule(task,3000);
    }
    ```

Oke, sampai itu dulu tutorial kali ini selanjutnya kita akan membahas bagaimana mengubah tampilan di *activity* `WelcomeActivity.java` . Sampai jumpa dipertemuan selanjutnya

----

>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>



