---
title: Tips Membuat Rest Api Client Flutter
img: 200822/cover.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Flutter, Tips, Rest Api, Developer]
---

Hola Sobat Ngoding, Kali ini saya ingin berbagi tips yang bisa kalian jadikan refrensi untuk membangun aplikasi kalian. Tips ini saya gunakan disemua aplikasi yang sudah saya bangung dengan flutter, dan tips ini sangat membantu aku banget dalam tracking error dan tracking log serta maintanance yang sangat mudah.

## Kebutuhan ##

Hal dasar yang kita butuhkan untuk membuat Rest API Client ini adalah HTTP, kalian bisa lihat documentasinya dimari ya [Documentasi HTTP](https://pub.dev/packages/http).


## Langkah-Langkah ##

1. Pasang dulu lib HTTP nya ya 

2. Buat folder dibawah lib dengan nama `api` atau apapun yang kalian inginkan

3. Buat 3 file dengan nama
- api_db.dart
- api_client.dart
- api.dart

4. Edit file `api.dart`,
Kita anggap kelas *Api.dart* adalah bapak dari kelas *ApiClient.dart* maka kita akan membuat abstrak kelas sebagai dasar kebutuhan dari kelas *ApiClient* nantinya, maka akan jadi seperti dibawah ini : 

```dart
import 'package:flutter/cupertino.dart';

abstract class Api {
  Future<void> get(
      {String url,
      Map<String, String> headers,
      VoidCallback callback(
          bool status, String message, Map<String, dynamic> response)});

  Future<void> post(
      {String url,
        Map<String, String> headers,
        Map<String, String> body,
        VoidCallback callback(
            bool status, String message, Map<String, dynamic> response)});

  Future<void> put(
      {String url,
        Map<String, String> headers,
        Map<String, String> body,
        VoidCallback callback(
            bool status, String message, Map<String, dynamic> response)});

  Future<void> delete(
      {String url,
        Map<String, String> headers,
        VoidCallback callback(
            bool status, String message, Map<String, dynamic> response)});
}

```

5. Edit file `api_client.dart` menjadi seperti ini guys :

```dart
import 'dart:convert';

import 'package:flutter/cupertino.dart';

import 'api.dart';
import 'api_db.dart';
import 'package:http/http.dart' as http;

class ApiClient extends Api implements ApiDb {
  static ApiClient _client = ApiClient._singleTon();

  factory ApiClient() {
    return _client;
  }

  ApiClient._singleTon();

  laporkanError(String judulError, String pesanError) {
//    buat method untuk laporan
  }

  @override
  Future<void> delete(
      {String url,
      Map<String, String> headers,
      Function(bool status, String message, Map<String, dynamic> response)
          callback}) async {
    http.delete(url, headers: headers).then((res) {
      callback(res.statusCode == 200,
          res.statusCode == 200 ? "Sukses" : "Gagal", jsonDecode(res.body));
      debugPrint("print apa aja yang kamu butuhkan");
    }).catchError((err) {
      callback(false, err.toString(), null);
      laporkanError("judulError", "pesanError");
    }).timeout(Duration(seconds: 30), onTimeout: () {
      callback(false, "Timeout", null);
      laporkanError("judulError", "pesanError");
    });
  }

  @override
  Future<void> get(
      {String url,
      Map<String, String> headers,
      Function(bool status, String message, Map<String, dynamic> response)
          callback}) async {
    http.get(url, headers: headers).then((res) {
      callback(res.statusCode == 200,
          res.statusCode == 200 ? "Sukses" : "Gagal", jsonDecode(res.body));
    }).catchError((err) {
      callback(false, err.toString(), null);
    }).timeout(Duration(seconds: 30), onTimeout: () {
      callback(false, "Timeout", null);
    });
  }

  @override
  Future<void> post(
      {String url,
      Map<String, String> headers,
      Map<String, String> body,
      Function(bool status, String message, Map<String, dynamic> response)
          callback}) async {
    http.post(url, headers: headers, body: body).then((res) {
      callback(res.statusCode == 200,
          res.statusCode == 200 ? "Sukses" : "Gagal", jsonDecode(res.body));
    }).catchError((err) {
      callback(false, err.toString(), null);
    }).timeout(Duration(seconds: 30), onTimeout: () {
      callback(false, "Timeout", null);
    });
  }

  @override
  Future<void> put(
      {String url,
      Map<String, String> headers,
      Map<String, String> body,
      Function(bool status, String message, Map<String, dynamic> response)
          callback}) async {
    http.put(url, headers: headers, body: body).then((res) {
      callback(res.statusCode == 200,
          res.statusCode == 200 ? "Sukses" : "Gagal", jsonDecode(res.body));
    }).catchError((err) {
      callback(false, err.toString(), null);
    }).timeout(Duration(seconds: 30), onTimeout: () {
      callback(false, "Timeout", null);
    });
  }
}

```

**Penjelasan**
kode 
```dart
static ApiClient _client = ApiClient._singleTon();

  factory ApiClient() {
    return _client;
  }

  ApiClient._singleTon();
```

adalah kode yang menunjukan bahwa kelas api client hanya boleh di inisialisasi sekali artinya *singleTon* metode ini akan membuat kelas apiclient hanya akan dipanggil dari 1 PID memory yang pertama kali intasiasi.


pada kode

 ```dart
 laporkanError(String judulError, String pesanError) {
//    buat method untuk laporan
  }
  ```
  digunakan untuk mentrack setiap ada error pada proses pemanggilan restApi ke server

  kode yang lain  adalah kode yang akan kita gunakan untuk melakukan proses transaksi antara server dan client.

## Penjelasan Method .then ##

  ```dart
  .then((res){

  })
  ```
metode ini digunakan untk menangkap response sukses berkomunikasi dengan server, baik itu 404 atau 200

## Penjelasan Method .catchError ##

```dart
.catchError((err) {
      callback(false, err.toString(), null);
    })
```
method ini akan menangkap semua error yang terjadi, baik karena error parsing atau karena error tidak dapat menghubungi server

## Penjelasan Method .timeOut ##

```dart
.timeout(Duration(seconds: 30), onTimeout: () {
      callback(false, "Timeout", null);
    });
```

Ini yang terakhir adalah error saat reques tidak dapat feedback dari server setelah 30detik, kalian bisa merubahnya sesuai kebutuhan kalian.



# Menambahkan BASE_URL dan EndPoint #

Untuk menambahkan BASE_URL dan EndPoint, temen2 buka dan edit file `api_db.dart` sebagai kumpulan dari semua endpoint yang kita miliki.
Lihatlah contoh dibawah:

```dart
class ApiDb {
  static const BASE_URL = "https://contoh-url.com";
  static const LOGIN = BASE_URL+"/login";
  static const REGISTER = BASE_URL"/register";
//  tambahkan sesuai kebutuhan temen2
}
```

# Cara Penggunaan #

Untuk menggunakan kelas yang sudah kita buat tadi, temen-temen bisa menggunakan dengan cara seperti dibawah

```dart
final ApiClient _client = new ApiClient();
login(){
    _clint.post(
        url:LOGIN,
        headers:{},
        body:{"username":"thengoding","password":"thengoding"},
        callback:(status,message,response){
            if(status){
                //Menuju halama utama
            }else{
                //Tampilkan errornya kenapa
            }
            return;
        }
    );
}
```

Semua Return yang diperoleh akan dilempar ke parameter `callback` dimana yang dilemapr berupa

status : Boolean

message : String

response : Map<String,dynamic>

# Kelebihan Menggunakan Tips ini #

1. Mudah Maintanancenya
2. Print Lognya cukup di satu kelas dan tidak perlu print log di tempat dia di instasiasi
3. Memudahkan Tracking Api Error Reporting
4. Menghindari Redundance Code

Cukup sekian kawan kawan tips flutter dari saya, semoga bermanfaat :-) ...

<br>
<br>
>Kode itu ibarat Cinta, Butuh dimengerti dan dafahami.. asik asik<small> - Penulis</small>