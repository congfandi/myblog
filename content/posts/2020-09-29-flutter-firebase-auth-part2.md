---
title: Flutter Firebase Auth Part 2 - Membuat UI/UX #judul postingan
img:  200920/cover2.jpg #gambar postingan taruh di assets/img dan langsung call nama imagenya
layout: post #default jangan diganti
author: Cong Fandi #default me
author-img : congfandi.jpeg #default me
author-detail : iOS Developer, Android Developer, Web Developer # default me
fig-caption: Developer #default me
tags: # tags dalam array [Developer, Web, Tips]
---
OKe sobat, melanjutkan dari pembahasan kita sebelumnya, yaitu [Flutter Firebase Auth Part 1 - Config Project]({{base_url}}/2020/09/30/flutter-firebase-auth-part1/), kali ini kita bahas tentang membangun UI nya ya sobat, lihatlah design dibawah ini

![Preferences]({{site.url}}/assets/img/200920/design.png)

## Menyiapkan Folder 

Susunan folder yang harus kalian buat adalah sebagai berikut (ini agar kalian terbiasa dengan design pattern yang clean ya guys, so ikuti aja dulu)

![Preferences]({{site.url}}/assets/img/200920/pattern.png)


## Menyiapkan Library

untuk library yang saya gunakan adalah sebagai berikut sobat

- provider: ^4.3.2+2
    
    Saya gunakan sebagai state managementnya

- firebase_auth: ^0.18.0+1

    Saya gunakan sebagai auth nya atau methode masuknya

- firebase_core: ^0.5.0

    Sejak awal tahun 2020, Firebase mewajibkan mengimport lib ini jika menggunakan salah satu lib dari firebase, saya sendiri tidak mengerti alasannya, silahkan diskusi dikolom diskusi ya bagi yang tahu alasannya

## Menyiapkan Code

### Template App

```dart

/*
 * abersoft_test
 *     app_theme.dart
 *     Created by Cong Fandi on 18/9/2020
 *     email 	    : congfandi@gmail.com
 *     website 	: https://www.thengoding.com
 *     Copyright © 2020 Cong Fandi. All rights reserved.
 */

import 'package:flutter/material.dart';

class AppTheme {
  static AppTheme _theme = AppTheme._singleTon();

  factory AppTheme() {
    return _theme;
  }

  AppTheme._singleTon();

  MaterialColor appColor = MaterialColor(0xFF2196F3, {
    50: Color(0xFFE3F2FD),
    100: Color(0xFFBBDEFB),
    200: Color(0xFF90CAF9),
    300: Color(0xFF64B5F6),
    400: Color(0xFF42A5F5),
    500: Color(0xFF2196F3),
    600: Color(0xFF1E88E5),
    700: Color(0xFF1976D2),
    800: Color(0xFF1565C0),
    900: Color(0xFF3549FB),
  });

  ColorSwatch appColors = ColorSwatch(0xFF2196F3, {
    tosca: Color(0xFF18FFFF),
    blue: Color(0xFF2196F3),
    black: Color(0xff000000),
    white: Color(0xffffffff),
    red: Color(0x1AFFFFFF),
  });

  Widget page(
      {@required BuildContext context,
      @required Widget content,
      ValueChanged onTapBack()}) {
    return Scaffold(
      body: Stack(
        alignment: Alignment.bottomCenter,
        children: [
          Container(
            width: double.infinity,
            height: double.infinity,
            child: Image.asset(
              'assets/images/bg.png',
              fit: BoxFit.cover,
            ),
          ),
          Container(
            width: MediaQuery.of(context).size.width,
            height: MediaQuery.of(context).size.height,
            child: Image.asset(
              'assets/images/foreground.png',
              fit: BoxFit.cover,
            ),
          ),
          content,
          if (onTapBack != null)
            Positioned(
              child: GestureDetector(
                onTap: () {
                  onTapBack();
                },
                child: Icon(
                  Icons.arrow_back,
                  color: appColors[white],
                ),
              ),
              top: 80,
              left: 16,
            )
        ],
      ),
    );
  }

  RoundedRectangleBorder buttonTheme() {
    return RoundedRectangleBorder(
        borderRadius: BorderRadius.all(Radius.circular(20)));
  }
}

const String tosca = "tosca";
const String blue = "blue";
const String black = "black";
const String white = "white";
const String red = "red";


```

### MyApp.dart

```dart

/*
 * abersoft_test
 *     my_app.dart
 *     Created by Cong Fandi on 18/9/2020
 *     email 	    : congfandi@gmail.com
 *     website 	: https://www.thengoding.com
 *     Copyright © 2020 Cong Fandi. All rights reserved.
 */

import 'package:abersoft_test/app/app_theme.dart';
import 'package:abersoft_test/views/auth/auth_view.dart';
import 'package:abersoft_test/views/dashboard/home_view.dart';
import 'package:abersoft_test/views/welcome_view.dart';
import 'package:firebase_auth/firebase_auth.dart';
import 'package:flutter/material.dart';

class MyApp extends StatelessWidget {
  final AppTheme _theme = new AppTheme();
  final routes = {
    "/welcome": (_) => WelcomeView(),
    "/auth": (_) => AuthView(),
    "/home": (_) => HomeView()
  };

  @override
  Widget build(BuildContext context) {
    FirebaseAuth auth = FirebaseAuth.instance;
    return MaterialApp(
      routes: routes,
      title: 'Abersoft Test',
      theme: ThemeData(
        primarySwatch: _theme.appColor,
        visualDensity: VisualDensity.adaptivePlatformDensity,
      ),
      initialRoute: auth.currentUser == null ? "/welcome" : "/home",
    );
  }
}

class CheckUser extends StatefulWidget {
  @override
  _CheckUserState createState() => _CheckUserState();
}

class _CheckUserState extends State<CheckUser> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: ListView.builder(
          itemBuilder: (c, i) => Container(
                child: Row(
                  children: [FlutterLogo(), Text("Data ke-$i")],
                ),
              ),itemCount: 4000,),
    );
  }
}


```

### Welcome View

```dart
/*
 * abersoft_test
 *     welcome_view.dart
 *     Created by Cong Fandi on 18/9/2020
 *     email 	    : congfandi@gmail.com
 *     website 	: https://www.thengoding.com
 *     Copyright © 2020 Cong Fandi. All rights reserved.
 */

import 'package:abersoft_test/app/app_theme.dart';
import 'package:flutter/material.dart';

class WelcomeView extends StatelessWidget {
  final AppTheme _theme = new AppTheme();

  @override
  Widget build(BuildContext context) {
    return _theme.page(
      context: context,
      content: Container(
        margin: EdgeInsets.only(left: 54, right: 54, bottom: 145),
        child: Column(
          mainAxisSize: MainAxisSize.min,
          children: [
            Container(
              width: double.infinity,
              height: 33,
              child: RaisedButton(
                shape: _theme.buttonTheme(),
                onPressed: () {
                  Navigator.pushReplacementNamed(context, '/auth',
                      arguments: "register");
                },
                child: Text("Register Account"),
              ),
            ),
            Container(
              margin: EdgeInsets.only(top: 44),
              width: double.infinity,
              height: 33,
              child: RaisedButton(
                shape: _theme.buttonTheme(),
                onPressed: () {
                  Navigator.pushReplacementNamed(context, '/auth',
                      arguments: "login");
                },
                child: Text("Login"),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

```

### Auth View (Login dan Register)

```dart

/*
 * abersoft_test
 *     auth_view.dart
 *     Created by Cong Fandi on 18/9/2020
 *     email 	    : congfandi@gmail.com
 *     website 	: https://www.thengoding.com
 *     Copyright © 2020 Cong Fandi. All rights reserved.
 */

import 'dart:io';

import 'package:abersoft_test/app/app_theme.dart';
import 'package:abersoft_test/states/auth/auth_state.dart';
import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';

class AuthView extends StatelessWidget {
  final AppTheme _theme = new AppTheme();

  Widget _loading() {
    return Platform.isAndroid
        ? Container(
            child: Center(
              child: CircularProgressIndicator(),
            ),
          )
        : Container(
            child: Center(child: CupertinoActivityIndicator()),
          );
  }

  @override
  Widget build(BuildContext context) {
    String argument = ModalRoute.of(context).settings.arguments;
    String title = argument == "login" ? "Login" : "Register new account";
    String buttonTitle = argument == "login" ? "Login" : "Create account";
    return _theme.page(
        context: context,
        content: Container(
          width: double.infinity,
          padding: EdgeInsets.only(top: 44, right: 54, left: 54, bottom: 70),
          decoration: BoxDecoration(
            color: _theme.appColors[white],
            borderRadius: BorderRadius.only(
              topRight: Radius.circular(50),
              topLeft: Radius.circular(50),
            ),
          ),
          child: ChangeNotifierProvider(
            create: (c) => AuthState(argument, context),
            child: Consumer<AuthState>(
              builder: (c, state, _) => Form(
                key: state.key,
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  mainAxisSize: MainAxisSize.min,
                  children: [
                    Text(
                      title,
                      style:
                          TextStyle(fontSize: 23, fontWeight: FontWeight.bold),
                    ),
                    Container(
                      margin: EdgeInsets.only(top: 39, bottom: 39),
                      child: TextFormField(
                        decoration: InputDecoration(labelText: "Email"),
                        validator: (value) => state.emailValidator(value),
                        controller: state.email,
                      ),
                    ),
                    Container(
                      margin: EdgeInsets.only(top: 0, bottom: 55),
                      child: TextFormField(
                        controller: state.password,
                        obscureText: true,
                        validator: (value) => state.passwordValidator(value),
                        decoration: InputDecoration(labelText: "Password"),
                      ),
                    ),
                    state.authProcess
                        ? _loading()
                        : Container(
                            width: double.infinity,
                            child: RaisedButton(
                              shape: _theme.buttonTheme(),
                              color: _theme.appColor[900],
                              textColor: _theme.appColors[white],
                              onPressed: () {
                                state.auth();
                              },
                              child: Text(buttonTitle),
                            ),
                          ),
                  ],
                ),
              ),
            ),
          ),
        ),
        onTapBack: () {
          Navigator.pushReplacementNamed(context, '/welcome');
          return;
        });
  }
}

```


### Home View

```dart

/*
 * abersoft_test
 *     home_view.dart
 *     Created by Cong Fandi on 18/9/2020
 *     email 	    : congfandi@gmail.com
 *     website 	: https://www.thengoding.com
 *     Copyright © 2020 Cong Fandi. All rights reserved.
 */

import 'package:firebase_auth/firebase_auth.dart';
import 'package:flutter/material.dart';

class HomeView extends StatelessWidget {
  final FirebaseAuth _auth = FirebaseAuth.instance;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Container(
        margin: EdgeInsets.all(23),
        child: Stack(
          children: [
            Center(
              child: Column(
                children: [
                  Row(
                    children: [
                      Expanded(
                        child: Container(),
                        flex: 1,
                      ),
                      Expanded(
                        flex: 6,
                        child: GestureDetector(
                          onTap: () {
                            _auth.signOut().then((value) {
                              Navigator.pushReplacementNamed(
                                  context, "/welcome");
                            });
                          },
                          child: Image.asset(
                            'assets/images/home.png',
                            height: 201,
                            width: 281.51,
                          ),
                        ),
                      ),
                      Expanded(
                        child: Container(),
                        flex: 2,
                      )
                    ],
                  ),
                  Container(
                    width: double.infinity,
                    child: Text(
                      "Welcome to the app",
                      style:
                          TextStyle(fontSize: 25, fontWeight: FontWeight.bold),
                      textAlign: TextAlign.center,
                    ),
                  ),
                  Padding(padding: EdgeInsets.only(top: 28)),
                  Container(
                    child: Text(
                      "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Egestas scelerisque porttitor turpis viverra lobortis convallis. Libero tristique donec turpis elit adipiscing sit faucibus tincidunt. Erat porttitor amet, nibh id lorem. Volutpat quam vestibulum egestas ut odio odio. Nunc non, feugiat a diam at lacus augue. Sit lacus pharetra eget feugiat aliquam enim adipiscing. Purus nec tortor tellus, neque montes. Gravida ornare eu viverra libero. Vulputate massa turpis posuere nibh dolor pulvinar bibendum. Viverra scelerisque ut dignissim at sit s",
                      style: TextStyle(fontSize: 12),
                      textAlign: TextAlign.center,
                    ),
                  )
                ],
                mainAxisSize: MainAxisSize.min,
              ),
            )
          ],
        ),
      ),
    );
  }
}

```

Pada bagian ini , kode kalian pasti banyak yang error karena state nya belum kita buat. Oke kita akan membahas cara membuat statenya pada tulisan kita di chapter 3

[Flutter Firebase Auth Part 3 - Menambahkan Code Auth]({{base_url}}/2020/09/28/flutter-firebase-auth-part3/)

<br>
<br>
>S*Diakhir Chapter aku kasih bonus repo source code aplikasi*<small> - Penulis</small>

