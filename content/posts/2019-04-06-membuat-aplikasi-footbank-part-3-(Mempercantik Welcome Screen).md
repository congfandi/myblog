---
title: Android Native Membuat aplikasi foodbank part 3 - Mempercantik welcome screen
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Android, JAVA, Tutorial]
---
![Cover](/../img/06-04-2019/gift2.gif)
Pada tutorial kali ini, kita akan mempercantik tampilan Welcome Screen. Kita langsung saja pada tutorialnya.
<!--more-->

Langkah pertama, kita akan menambahkan icon indicator, yaitu tanda halaman yang sedang aktif :

1. Tambahkan icon titik warna *grey* dan warna *putih*
   - Klik kanan pada package *`res/drawable`*
   - Pilih *`New -> Vector Asset`*
   - Pilih icon *`ic_fiber_manual_record_black_24dp`*
   - Ganti nama menjadi *`ic_indicator_grey.xml`* kemudian ganti warnanya menjadi grey
   - Lakukan langkah yang sama dan ganti namanya menjadi *`ic_indicator_white.xml`* dan ubah warna menjadi warna putih
  
2. Buka file *`activity_welcome.xml`*, kemudian tambahkan kode berikut
   ```xml
        <LinearLayout
        android:layout_above="@id/btn_order_now"
        android:id="@+id/indicator"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="30.0dp"
        android:layout_centerHorizontal="true"
        android:orientation="horizontal">

                <ImageView
                    android:id="@+id/indictor1"
                    android:layout_width="15dp"
                    android:layout_height="15dp"
                    android:src="@drawable/ic_indicator_grey" />

                <ImageView
                    android:id="@+id/indictor2"
                    android:layout_width="15dp"
                    android:layout_height="15dp"
                    android:src="@drawable/ic_indicator_grey" />

                <ImageView
                    android:id="@+id/indictor3"
                    android:layout_width="15dp"
                    android:layout_height="15dp"
                    android:src="@drawable/ic_indicator_grey" />
            </LinearLayout>

        <Button
            android:layout_marginLeft="24.0dp"
            android:layout_marginRight="24.0dp"
            android:id="@+id/btn_order_now"
            android:layout_marginBottom="30.0dp"
            android:layout_alignParentBottom="true"
            android:text="Order Now"
            android:textColor="#FFFFFF"
            android:layout_width="match_parent"
            android:layout_height="40.0dp" />
   ```
   pada preview, harusnya tampil seperti gambar 1.
   ![Gambar 1](/../img/06-04-2019/gambar1.png)
   *Gambar 1*


**Mempercantik tombol `ORDER NOW`**

untuk mempercantik tombol order now, kita membutuhkan sebuah backgound, untuk itu kita akan membuat background terleibh dahulu, caranya : 
1. Klik kanan pada package *`res -> drawable`*
2. Pilih *`New -> Drawable resource file`*
3. Beri nama *`background_tombol`*
4. Buka dan ganti kodenya menjadi seperti ini
        
    ```xml
            <?xml version="1.0" encoding="utf-8"?>
            <shape xmlns:android="http://schemas.android.com/apk/res/android"
                android:shape="rectangle">
                <solid android:color="#FF9800" />
                <corners android:bottomRightRadius="24dp"
                    android:bottomLeftRadius="24dp"
                    android:topRightRadius="24dp"
                    android:topLeftRadius="24dp"/>
            </shape>
    ```

5. Tambahkan file yang telah dibuat kedalam tombol *`Order Now`* dengan cara menambahkan atribut baru kedalamnya 
   
    ```xml
            android:background="@drawable/background_tombol"
    ```
6. Harusnya tampilan tombol *`Order now`* sudah berubah sekarang


**Membuat Logic `Slider`**

membuat logic pada slider dihalaman welcome, caranya :

   1. Buka file *`WelcomeActivity.java`*
   2. Tambahkan kode berikut
        ```java
            public class WelcomeActivity extends AppCompatActivity {

                private ViewPager viewPager;
                private ImageView[] indicators = new ImageView[3];


                private void setIndicators() {
                    indicators[0] = findViewById(R.id.indictor1);
                    indicators[1] = findViewById(R.id.indictor2);
                    indicators[2] = findViewById(R.id.indictor3);
                }

                private void setIndicatorImage(int position) {
                    int iconWhite = R.drawable.ic_indicator_white;
                    int iconGrey = R.drawable.ic_indicator_grey;
                    indicators[0].setImageResource(position == 0 ? iconWhite : iconGrey);
                    indicators[1].setImageResource(position == 1 ? iconWhite : iconGrey);
                    indicators[2].setImageResource(position == 2 ? iconWhite : iconGrey);
                }

                private void setViewPager() {
                    viewPager = findViewById(R.id.viewpager);
                    viewPager.setAdapter(new WelcomeAdapter(this));
                    viewPager.addOnPageChangeListener(new ViewPager.OnPageChangeListener() {
                        @Override
                        public void onPageScrolled(int i, float v, int i1) {

                        }

                        @Override
                        public void onPageSelected(int i) {
                            setIndicatorImage(i);

                        }

                        @Override
                        public void onPageScrollStateChanged(int i) {

                        }
                    });
                    setIndicatorImage(0);
                }

                @Override
                protected void onCreate(Bundle savedInstanceState) {
                    super.onCreate(savedInstanceState);
                    setContentView(R.layout.activity_welcome);
                    setIndicators();
                    setViewPager();

                    //tombol order now
                    Button orderNow = findViewById(R.id.btn_order_now);
                    orderNow.setOnClickListener(new View.OnClickListener() {
                        @Override
                        public void onClick(View v) {
                            startActivity(new Intent(WelcomeActivity.this,LoginActivity.class));
                        }
                    });
                }
            }
        ```
   3. Kita akan menjelaskan maksud dari kode ini dikelas nanti.
   4. Silahkan jalankan aplikasi, seharusnya sudah selesai untuk mempercantik halaman *`Welcome`* dan akan terlihat seperti gift dibawah
   ![Gift](/../img/06-04-2019/cover.gif)


**Mempercantik halaman login**

halaman login dan register merupakan halaman yang sangat penting pada aplikasi ini, pada dasarnya tidak semua aplikasi membutuhkan halaman login dan halaman register.
Caranya sebagai berikut : 

1. Buka file *`activity_login.xml`*
2. Tambahkan kode berikut
   
   ```xml
        <?xml version="1.0" encoding="utf-8"?>
        <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
            xmlns:tools="http://schemas.android.com/tools"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:background="#FFB752"
            tools:context=".views.LoginActivity">

            <RelativeLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content">

                <ImageView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_margin="30.0dp"
                    android:src="@drawable/ic_arrow_back_black_24dp" />

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_centerHorizontal="true"
                    android:layout_marginTop="30.0dp"
                    android:text="Sig In"
                    android:textColor="#FFFFFF" />
            </RelativeLayout>

            <LinearLayout

                android:layout_centerHorizontal="true"
                android:gravity="center"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_alignParentBottom="true"
                android:layout_margin="24.0dp"
                android:orientation="vertical">
                <TextView
                    android:textSize="40.0dp"
                    android:textColor="#FFFFFF"
                    android:layout_centerHorizontal="true"
                    android:text="FoodBank"
                    android:layout_width="wrap_content"
                    android:layout_marginBottom="100.0dp"
                    android:layout_height="wrap_content" />
                <EditText
                    android:layout_width="match_parent"
                    android:layout_height="40.0dp"
                    android:layout_gravity="center"
                    android:background="@drawable/background_edittext"
                    android:gravity="center"
                    android:hint="Email Address"
                    android:textColor="#FFFFFF" />

                <EditText
                    android:layout_width="match_parent"
                    android:layout_height="40.0dp"
                    android:layout_gravity="center"
                    android:layout_marginTop="20.0dp"
                    android:background="@drawable/background_edittext"
                    android:gravity="center"
                    android:hint="Password"
                    android:textColor="#FFFFFF" />
                <Button
                    android:textColor="#FFFFFF"
                    android:text="SIGN IN"
                    android:background="@drawable/background_tombol"
                    android:layout_marginTop="20.0dp"
                    android:layout_width="match_parent"
                    android:layout_height="40.0dp" />

                <LinearLayout
                    android:layout_marginTop="10.0dp"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content">
                    <TextView
                        android:textColor="#000000"
                        android:text="Don't have account?"
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content" />
                    <TextView
                        android:id="@+id/txt_register"
                        android:layout_marginLeft="10.0dp"
                        android:textColor="#FFFFFF"
                        android:text="Register"
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content" />
                </LinearLayout>
        <TextView
            android:layout_marginTop="20.0dp"
            android:layout_marginBottom="20.0dp"
            android:text="OR"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" />
                <LinearLayout
                    android:layout_marginTop="10.0dp"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content">
                    <Button
                        android:textColor="#FFFFFF"
                        android:background="@drawable/background_facebook"
                        android:text="F"
                        android:layout_width="80.0dp"
                        android:layout_height="40.0dp" />
                    <Button
                        android:textColor="#FFFFFF"
                        android:text="G+"
                        android:background="@drawable/background_google"
                        android:layout_marginRight="16.0dp"
                        android:layout_marginLeft="16.0dp"
                        android:layout_width="80.0dp"
                        android:layout_height="40.0dp" />
                    <Button
                        android:textColor="#FFFFFF"
                        android:background="@drawable/background_twitter"
                        android:text="T"
                        android:layout_width="80.0dp"
                        android:layout_height="40.0dp" />
                </LinearLayout>
            </LinearLayout>
        </RelativeLayout>
   ```

3. *`Buatlah tulisan ` **Register** `dapat di klik dan arahkan fungsinya untuk membuka halaman register`* (Ini challenge untuk temen-temen)
4. tampilan login seharusnya seperti gambar 2
   ![Gambar2](/../img/06-04-2019/gambar2.png)

5. Untuk file `background_facebook.xml` , `background_google.xml`  dan `background_twitter.xml`  silahkan dibuat sesuai dengan yang kalian sukai.

**Mempercantik halaman Register**

Silahkan percantik halaman register sesuai dengan yang kalian sukai, punya saya, saya buat seperti gambar 3
![Gambar 3](/../img/06-04-2019/gambar3.png)


Hasil Akhir dari tutorial kali ini dapat dilihat pada gif dibawah

![Gift](/../img/06-04-2019/gift2.gif)

Ada banyak hal yang belum saya sampaikan pada tulisan ini, kita bahasnya dikelas ya, jika ada yang belum faham monggo ditanyakan.

Oke sekian dari saya, maaf atas kesalahan dan ketidak sempurnaan modulnya, sampai ketemu dikelas.


>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


