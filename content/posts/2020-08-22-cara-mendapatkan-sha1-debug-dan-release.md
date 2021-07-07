---
title: Cara Mendapatkan SHA1 Android Debug dan Release
img: 200822/www.thengoding.com.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Tutorial,Developer,Android]
---

Hola ngoding, sudah pada tahu kan fungsi dari SHA-1 pada android, nah kali ini saya ingin berbagi tips simple nih cara mendapatkan SHA-1, cukup dengan menjalankan perintah pada terminal.

## Mode Debug

```
keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android 
```

Jalankan perintah ini pada terminal kalian, perintah ini dapat berjalan dengan baik pada Mac dan linux dengan syarat sudah terinstall JDK.

Pada sistem operasi windows, jalankan perintah ini didalam forlder java kalian


## Mode Release

```
keytool -list -v -keystore lokasikeystore -alias alisnya -storepass passnya -keypass passkeynya
```

Sama dengan sebelumnya, perintah ini juga berjalan dengan baik pada perangkat macbook dan linux, pada sistem operasi windows gunakan pada path jdk temen2.


## Hasil Yand didapat

Mode Debug

```
Alias name: androiddebugkey
Creation date: Jun 24, 2020
Entry type: PrivateKeyEntry
Certificate chain length: 1
Certificate[1]:
Owner: C=US, O=Android, CN=Android Debug
Issuer: C=US, O=Android, CN=Android Debug
Serial number: 1
Valid from: Wed Jun 24 17:44:02 WIB 2020 until: Fri Jun 17 17:44:02 WIB 2050
Certificate fingerprints:
         SHA1: 37:B7:D7:6F:32:07:8D:DC:1F:DE:8F:21:A3:45:65:D7:18:XX:9F:XX
         SHA256: 93:7A:D6:F8:DB:0C:B4:A8:9A:A4:01:32:96:F0:B7:CE:C2:2E:XX:XX:AC:0C:6B:D7:A3:B4:2A:38:4B:5F:CB:C6
Signature algorithm name: SHA1withRSA
Subject Public Key Algorithm: 2048-bit RSA key
Version: 1

Warning:
The JKS keystore uses a proprietary format. It is recommended to migrate to PKCS12 which is an industry standard format using "keytool -importkeystore -srckeystore /Users/thengoding/.android/debug.keystore -destkeystore /Users/thengoding/.android/debug.keystore -deststoretype pkcs12".

```


Mode Release

```
Alias name: thengoding
Creation date: Feb 25, 2018
Entry type: PrivateKeyEntry
Certificate chain length: 1
Certificate[1]:
Owner: CN=thengoding, OU=dinas thengoding, O=thengoding, L=thengoding, ST=jthengoding, C=69362
Issuer: CN=thengoding, OU=thengoding thengoding, O=thengoding, L=thengoding, ST=thengoding, C=69362
Serial number: thengoding
Valid from: Sun Feb 25 16:48:01 WIB 2018 until: Thu Feb 19 16:48:01 WIB 2043
Certificate fingerprints:
         SHA1: 06:88:XX:XX:5B:D2:XX:39:EC:0E:XX:98:CD:XX:1E:C4:3E:25:B7:55
         SHA256: 94:8B:8A:B8:6F:XX:XX:XX:XX:62:69:5E:F0:B0:5E:AE:ED:2A:0E:0D:21:47:1D:30:65:B6:C4:E7:93:70:47:60
Signature algorithm name: SHA256withRSA
Subject Public Key Algorithm: 2048-bit RSA key
Version: 3

Extensions: 

#1: ObjectId: 2.5.29.14 Criticality=false
SubjectKeyIdentifier [
KeyIdentifier [
0000: 26 A5 E4 DF 73 B7 E1 C6   6E AD 76 2C 86 01 2B 7C  &...s...n.v,..+.
0010: 16 94 AE C1                                        ....
]
]


Warning:
The JKS keystore uses a proprietary format. It is recommended to migrate to PKCS12 which is an industry standard format using "keytool -importkeystore -srckeystore siani.jks -destkeystore siani.jks -deststoretype pkcs12".

```


Ini adalah acara termudah yang bisa temen2 lakukan dan banyak lagi cara lainnya.. 

Selamat mencoba sobat ngoding :-) ..
<br>
<br>
>Koding dan error itu seperti sabun dan busa, beda tapi satu<small> - Penulis</small>