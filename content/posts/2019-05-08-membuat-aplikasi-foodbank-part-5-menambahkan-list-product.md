---
title: Android Native Membuat aplikasi foodbank part-5 - Menambahkan list product
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Android, JAVA, Tutorial]
---

![Cover](/../img/covers/list.gif)
Oke, kita lanjutkan tutorial selanjutnya yaitu menambahkan list product dalam bentuk `list`.

Langkah - langkah nya adalah : 
<!--more-->   
1. Bukan file `HalamanList.java` dan hapus kode yang tidak diperlukan dan hasilnya harus nya seperti code dibawah

```java
    package id.gresikdev.foodbank.views;
    import android.os.Bundle;
    import android.support.v4.app.Fragment;
    import android.view.LayoutInflater;
    import android.view.View;
    import android.view.ViewGroup;
    import id.gresikdev.foodbank.R;

    public class HalamanList extends Fragment {

        public HalamanList() {
        }

        @Override
        public View onCreateView(LayoutInflater inflater, ViewGroup container,
                                Bundle savedInstanceState) {
            return inflater.inflate(R.layout.fragment_halaman_list, container, false);
        }

    }
```
2. buka `file fragment_halaman_list.xml` dan ubah codenya menjadi seperti dibawah ini
   ```xml
        <?xml version="1.0" encoding="utf-8"?>
        <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
            xmlns:tools="http://schemas.android.com/tools"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            tools:context=".views.HalamanList">

            <android.support.v7.widget.RecyclerView
                android:id="@+id/list_food"
                android:layout_width="match_parent"
                android:layout_height="match_parent" />
        </LinearLayout>
   ```
3. buat sebuah file pada folder `layout` dengan nama `item_food`
4. tambahkan code berikut pada file yang kamu buat
   ```xml
        <?xml version="1.0" encoding="utf-8"?>
            <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">

            <ImageView
                android:id="@+id/img_food"
                android:layout_width="match_parent"
                android:layout_height="200dp"
                android:scaleType="fitXY"
                android:src="@drawable/humberger" />

            <TextView
                android:id="@+id/txt_food_name"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginLeft="16.0dp"
                android:layout_marginTop="16.0dp"
                android:layout_marginRight="16.0dp"
                android:ellipsize="end"
                android:maxLines="1"
                android:text="Humberger"

                android:textColor="#000000"
                android:textSize="17.0dp" />

            <Button
                android:id="@+id/btn_ready_in"
                android:layout_width="150.0dp"
                android:layout_height="35.0dp"
                android:layout_gravity="right"
                android:layout_margin="16.0dp"
                android:background="@drawable/background_tombol"
                android:text="Ready in 26 min"
                android:textAllCaps="false"
                android:textColor="#FFFFFF" />
            </LinearLayout>
   ```
5. Download dan tambahkan gambar [disini](https://drive.google.com/drive/folders/1SaxTgSEMh2VeG6_9d3vhQy-dSWdmJbbz?usp=sharing) 
*Noted* : Gambar mungkin memiliki hak cipta, saya sarankan gunakan gambar lain yang sudah jelas tidak memiliki hak cipta agar aplikasi tidak ditolak di playstore.

6. Tambahkan file java pada folder *`model`* dengan nama `Food`.
7. Tambahkan kode berikut
   ```java
        package id.gresikdev.foodbank.models;
        import android.graphics.drawable.Drawable;

        public class Food {
            String foodName;
            Drawable foodImage;
            String foodDetail;
            String foodBtnTitle;
            int foodPrice;

            public Food(String foodName, Drawable foodImage, String foodDetail, String foodBtnTitle, int foodPrice) {
                this.foodName = foodName;
                this.foodImage = foodImage;
                this.foodDetail = foodDetail;
                this.foodBtnTitle = foodBtnTitle;
                this.foodPrice = foodPrice;
            }

            public Food() {
            }

            public String getFoodName() {
                return foodName;
            }

            public void setFoodName(String foodName) {
                this.foodName = foodName;
            }

            public Drawable getFoodImage() {
                return foodImage;
            }

            public void setFoodImage(Drawable foodImage) {
                this.foodImage = foodImage;
            }

            public String getFoodDetail() {
                return foodDetail;
            }

            public void setFoodDetail(String foodDetail) {
                this.foodDetail = foodDetail;
            }

            public String getFoodBtnTitle() {
                return foodBtnTitle;
            }

            public void setFoodBtnTitle(String foodBtnTitle) {
                this.foodBtnTitle = foodBtnTitle;
            }

            public int getFoodPrice() {
                return foodPrice;
            }

            public void setFoodPrice(int foodPrice) {
                this.foodPrice = foodPrice;
            }
        }
   ``` 
8. Tambahkan file java pada folder `adapter` dengan nama *`ListFoodController`*
9.  Edit dan tambahkan code dibawah ini
   ```java
            package id.gresikdev.foodbank.adapter;

            import android.content.Context;
            import android.support.annotation.NonNull;
            import android.support.v7.widget.RecyclerView;
            import android.view.LayoutInflater;
            import android.view.View;
            import android.view.ViewGroup;
            import android.widget.Button;
            import android.widget.ImageView;
            import android.widget.TextView;

            import java.util.ArrayList;

            import id.gresikdev.foodbank.R;
            import id.gresikdev.foodbank.models.Food;

            public class ListFoodController extends RecyclerView.Adapter<ListFoodController.ListFoodHolder> {


                private ArrayList<Food> listFood;
                private Context context;

                public ListFoodController(ArrayList<Food> listFood, Context context) {
                    this.listFood = listFood;
                    this.context = context;
                }

                @NonNull
                @Override
                public ListFoodHolder onCreateViewHolder(@NonNull ViewGroup viewGroup, int i) {
                    return new ListFoodHolder(LayoutInflater.from(context).inflate(R.layout.item_food, viewGroup, false));
                }

                @Override
                public void onBindViewHolder(@NonNull ListFoodHolder listFoodHolder, int i) {
                    Food myFood = listFood.get(i);
                    listFoodHolder.bind(myFood);
                }

                @Override
                public int getItemCount() {
                    return listFood.size();
                }

                class ListFoodHolder extends RecyclerView.ViewHolder {
                    ImageView foodImage;
                    TextView title;
                    Button foodInfo;

                    private ListFoodHolder(@NonNull View itemView) {
                        super(itemView);
                        foodImage = itemView.findViewById(R.id.img_food);
                        title = itemView.findViewById(R.id.txt_food_name);
                        foodInfo = itemView.findViewById(R.id.btn_ready_in);
                    }

                    void bind(Food food) {
                        foodImage.setImageDrawable(food.getFoodImage());
                        title.setText(food.getFoodName());
                        foodInfo.setText(food.getFoodBtnTitle());
                    }
                }
            }

   ```
10. Buka file `HalamanList.java` kemudian edit menjadi seperti dibawah ini
    ```java
            public class HalamanList extends Fragment {
            private ArrayList<Food> myFoods = new ArrayList<>();
            private RecyclerView mylistFood;
            private ListFoodController listAdapter;

            public HalamanList() {
            }

            private View myView;

            private void getFood() {
                for (int i = 0; i < 100; i++) {
                    myFoods.add(new Food("Food number " + i, getResources().getDrawable(R.drawable.donut), "detail food", "Ready in " + (10 * i) + " min", i));
                }
            }

            private void setView() {
                getFood();
                mylistFood = myView.findViewById(R.id.list_food);
                listAdapter = new ListFoodController(myFoods, getContext());
                mylistFood.setLayoutManager(new LinearLayoutManager(getContext()));
                mylistFood.setAdapter(listAdapter);
            }

            @Override
            public View onCreateView(LayoutInflater inflater, ViewGroup container,
                                    Bundle savedInstanceState) {
                myView = inflater.inflate(R.layout.fragment_halaman_list, container, false);
                setView();
                return myView;
            }

        }
    ```
    hasilnya harusnya seperti dibawah ini
    !["adfadf"](/../img/08-05-2019/list.gif)


    Oke, sekian pada modul kali ini sampai ketemu pada modul selanjutnya



>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>

