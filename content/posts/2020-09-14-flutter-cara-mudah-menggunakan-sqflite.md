---
title: Flutter - Cara mudah menggunakan SQFLITE #judul postingan
img:  200914/cover.jpg #gambar postingan taruh di assets/img dan langsung call nama imagenya
layout: post #default jangan diganti
author: Cong Fandi #default me
author-img : congfandi.jpeg #default me
author-detail : iOS Developer, Android Developer, Web Developer # default me
fig-caption: SQFLITE #default me
tags: [Flutter , Tips ] # tags dalam array [Developer, Web, Tips]
---

Halo sobat ngoding semuanya, kali ini saya ingin berbagi tentang cara simple menggunakan [SQFLITE]({{post.url}}) pada flutter. [SQFLITE]({{post.url}}) pada dasarnya sama seperti SQLITE pada android dan IOS.. cara penggunaannyapun sama yaitu menyimpan data kompleks di local. Jika kalian ingin membaca referensinya, silahkan buka [CONTOH](https://pub.dev/packages/sqflite/example) ini untuk mempelajari lebih lanjut.

Oke, Kita mulai saja tutorial kita pada kali ini : 

# 1. Pasang Library SQFLITE
 
version : [sqflite: ^1.3.1+1](https://pub.dev/packages/sqflite/install) atau klik link untuk mendapatkan yang paling baru,

# 2. Buat Folder

Pada folder _lib_ tambahkan beberapa folder, hal ini agar kita mudah memaintanance aja sih, kalian tidak membuatnya pun juga tidak masalah. truktur foldernya bisa kalian lihat pada gambar dibawah ini

![fodlder]({{site.url}}/assets/img/200914/folder.png)


# 3. Buat Kelas QUERY dari masing masing table yang akan dibuat

Pada bagian ini, kita akan membuat sebuah kelas query dari JSON yang nantinya akan kita buat sebagai model juga berikut JSON nya.

JSON User

```json
    {
        "id":123,
        "name":"congfandi",
        "address":"Pamekasan, Madura"
    }
```

JSON Country
```json
    {
        "id":123,
        "name":"indonesia"
    }
```

*Pastikan model dan query untuk membuat tablenya sama ya guys agar nanti dapat di casting dengan mudah menjadi sebuah model*

*class UserQuery*

```dart
class UserQuery {
  static const String TABLE_NAME = "users";
  static const String CREATE_TABLE =
      " CREATE TABLE IF NOT EXISTS $TABLE_NAME ( id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT , address TEXT ) ";
  static const String SELECT = "select * from $TABLE_NAME";
}
```

*class User* 

```dart
class User {
    String address;
    int id;
    String name;

    User({this.address, this.id, this.name});

    factory User.fromJson(Map<String, dynamic> json) {
        return User(
            address: json['address'], 
            id: json['id'], 
            name: json['name'], 
        );
    }

    Map<String, dynamic> toJson() {
        final Map<String, dynamic> data = new Map<String, dynamic>();
        data['address'] = this.address;
        data['id'] = this.id;
        data['name'] = this.name;
        return data;
    }
}
```


*class Country Query*

```dart
class CountryQuery {
  static const String TABLE_NAME = "countries";
  static const String CREATE_TABLE =
      " CREATE TABLE IF NOT EXISTS $TABLE_NAME ( id INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT ) ";
  static const String SELECT = "select * from $TABLE_NAME";
}
```

*Class Country*

```dart
class Country {
    int id;
    String name;

    Country({this.id, this.name});

    factory Country.fromJson(Map<String, dynamic> json) {
        return Country(
            id: json['id'], 
            name: json['NAME'],
        );
    }

    Map<String, dynamic> toJson() {
        final Map<String, dynamic> data = new Map<String, dynamic>();
        data['id'] = this.id;
        data['NAME'] = this.name;
        return data;
    }
}
```

pastikan sama dengan yang aku buat ya,, kalau udah bisa baru deh kalian bisa eksplorasi.


# 4. Buat Kelas DbHelper #

```dart
 import 'package:flutter_atomic_design/database/queries/country_query.dart';
import 'package:flutter_atomic_design/database/queries/user_query.dart';
import 'package:sqflite/sqflite.dart' as sqlite;
import 'package:sqflite/sqlite_api.dart';
import 'package:path/path.dart' as path;

class DbHelper {
  //membuat method singleton
  static DbHelper _dbHelper = DbHelper._singleton();

  factory DbHelper() {
    return _dbHelper;
  }

  DbHelper._singleton();

  //baris terakhir singleton

  final tables = [
    UserQuery.CREATE_TABLE,
    CountryQuery.CREATE_TABLE
  ]; // membuat daftar table yang akan dibuat

  Future<Database> openDB() async {
    final dbPath = await sqlite.getDatabasesPath();
    return sqlite.openDatabase(path.join(dbPath, 'thengoding.db'),
        onCreate: (db, version) {
      tables.forEach((table) async {
        await db.execute(table).then((value) {
          print("berashil ");
        }).catchError((err) {
          print("errornya ${err.toString()}");
        });
      });
      print('Table Created');
    }, version: 1);
  }

  insert(String table, Map<String, Object> data) {
    openDB().then((db) {
      db.insert(table, data, conflictAlgorithm: ConflictAlgorithm.replace);
    }).catchError((err) {
      print("error $err");
    });
  }

  Future<List> getData(String tableName) async {
    final db = await openDB();
    var result = await db.query(tableName);
    return result.toList();
  }
}

 ```


# 5. Testing DbHelper dengan Insert #

 Untuk melakukan testing database, silahkan temen2 panggil dimain class seperti code dibawah ini

 ```dart
 final DbHelper _helper = new DbHelper();
  @override
  void initState() {
    super.initState();
    _helper.insert(CountryQuery.TABLE_NAME, {"NAME":"Singapura"});
  }
 ```

 dan apabila ada terlihat tulisan berhasil seperti gambar dibawah artinya table sudah berhasil dibuat dan data sudah berhasil di insert ke local db kita..

 *Noted* Ini hanya muncul sekali apabila table belum dibuat ya.. jika table sudah terbuat sebelumnya, dia tidak akan muncul lagi.

 ![inser]({{site.url}}/assets/img/200914/create.png)

# 6. Print data yang sudah kesimpan #
Untuk melihat hasilnya,, silahkan ganti code untuk insert menjadi seperti dibawah ini

```dart
 final DbHelper _helper = new DbHelper();

  @override
  void initState() {
    super.initState();
    // _helper.openDB();
    // _helper.insert(CountryQuery.TABLE_NAME, {"NAME":"Singapura"});
    _helper.getData(CountryQuery.TABLE_NAME).then((value) {
      value.forEach((element) {
        Country country = Country.fromJson(element);
        print(country.toJson());
      });
    });
  }
```
dan jika hasilnya seperti dibawah ini, maka tandanya data kita sudah berhasil di insert ke locak DB kita..

![inser]({{site.url}}/assets/img/200914/get.png)


Bagaimana temen-temen ? cukup mudah bukan [Tutorial Sqflite ini]({{post.url}})..

Jika kalian ingin menlihat full code nya bisa dilihat di link berikut [GITHUB SOURCE](https://github.com/congfandi/simple_sqflite)

Sampai jumpa di tutorial selanjutnya.....

<br>
<br>
>Ngoding itu berat, tapi kamu pasti kuat!<small> - Penulis</small>

