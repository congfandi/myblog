---
title: Flutter Firebase Auth Part 3 - Menambahkan Code Auth #judul postingan
img:  200920/cover3.jpg #gambar postingan taruh di assets/img dan langsung call nama imagenya
layout: post #default jangan diganti
author: Cong Fandi #default me
author-img : congfandi.jpeg #default me
author-detail : iOS Developer, Android Developer, Web Developer # default me
fig-caption: Developer #default me
tags: # tags dalam array [Developer, Web, Tips]
---
Oke sobat kali chapter ini kita bahas untuk menambahkan statenya pada masing masing halaman ya harusnya lebih sedikit dari sebelumnya.

oke kita langsung mulai saja ya..

## Menambahkan State

### Auth State
State ini adalah state untuk menghandle proses login dan proses register ya sobat. proses register dan proses login nya menggunakan lib firebase, jadi silahkan dipelajari ya, berikut kodenya

```dart
/*
 * abersoft_test
 *     auth_state.dart
 *     Created by Cong Fandi on 18/9/2020
 *     email 	    : congfandi@gmail.com
 *     website 	: https://www.thengoding.com
 *     Copyright © 2020 Cong Fandi. All rights reserved.
 */

import 'package:abersoft_test/app/app_theme.dart';
import 'package:firebase_auth/firebase_auth.dart';
import 'package:flutter/material.dart';

class AuthState with ChangeNotifier {
  bool authProcess = false;
  bool autoValidate = false;
  final TextEditingController email = TextEditingController();
  final TextEditingController password = TextEditingController();
  final key = GlobalKey<FormState>();
  final String argument;
  final BuildContext context;
  final AppTheme _theme = new AppTheme();

  AuthState(this.argument, this.context);

  auth() {
    if (key.currentState.validate()) {
      authProcess = true;
      notifyListeners();
      if (argument == "register")
        _register();
      else
        _login();
    } else {
      autoValidate = true;
      notifyListeners();
    }
  }

  FirebaseAuth _auth = FirebaseAuth.instance;

  _dialog(String message) {
    showDialog(
        context: context,
        child: AlertDialog(
          shape: _theme.buttonTheme(),
          content: Container(
            padding: EdgeInsets.all(16),
            decoration: BoxDecoration(
                borderRadius: BorderRadius.all(Radius.circular(40))),
            child: Column(
              mainAxisSize: MainAxisSize.min,
              children: [
                Text(
                  "Auth Failed",
                  style: TextStyle(fontSize: 23, fontWeight: FontWeight.bold),
                ),
                Padding(padding: EdgeInsets.only(top: 16)),
                Text(message),
                Container(
                  margin: EdgeInsets.only(top: 16),
                  width: 150,
                  height: 40,
                  child: RaisedButton(
                    color: _theme.appColors[red],
                    textColor: _theme.appColors[white],
                    onPressed: () {
                      Navigator.pop(context);
                    },
                    child: Text("OK"),
                    shape: _theme.buttonTheme(),
                  ),
                )
              ],
            ),
          ),
        ));
  }

  _login() {
    _auth
        .signInWithEmailAndPassword(email: email.text, password: password.text)
        .then((value) {
      authProcess = false;
      notifyListeners();
      print("hasil ${value.user.email}");
      Navigator.pushReplacementNamed(context, "/home");
    }).catchError((err) {
      authProcess = false;
      notifyListeners();
      print("hasil error $err");
      _dialog(err.toString());
    });
  }

  _register() {
    _auth
        .createUserWithEmailAndPassword(
            email: email.text, password: password.text)
        .then((value) {
      authProcess = false;
      notifyListeners();
      print("hasil ${value.user.email}");
      Navigator.pushReplacementNamed(context, "/home");
    }).catchError((err) {
      authProcess = false;
      notifyListeners();
      print("hasil error $err");
      _dialog(err.toString());
    });
  }

  String emailValidator(String value) {
    Pattern pattern =
        r'^(([^<>()[\]\\.,;:\s@\"]+(\.[^<>()[\]\\.,;:\s@\"]+)*)|(\".+\"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$';
    RegExp regex = new RegExp(pattern);
    if (!regex.hasMatch(value))
      return 'Email format is incorrect';
    else
      return null;
  }

  String passwordValidator(String value) {
    if (value.length < 6) return "Password minimal 6 character";
    return null;
  }
}

```


Cukup mudah bukan guys ? hanya dengan satu file kita sudah menghandle proses login dan proses register. Selamat mencoba ya, kalau sudah silahkan Running ya apliakasi kalian dan coba lihat hasilnya.

Untuk melihat hasilnya kalian bisa buka part ke 4 ya, cara melihat user yang login dan yang udah register

[Flutter Firebase Auth Part 4 - Melihat Hasil]({{base_url}}/2020/09/27/flutter-firebase-auth-part4/)

<br>
<br>
>*Diakhir Chapter aku kasih bonus repo source code aplikasi*<small> - Penulis</small>

