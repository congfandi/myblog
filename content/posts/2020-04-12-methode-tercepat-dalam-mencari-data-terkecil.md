---
title: Methode Tercepat dalam mencari data terkecil
img: hipster.jpg
layout: post
author: Cong Fandi
author-img : congfandi.jpeg
author-detail : iOS Developer, Android Developer, Web Developer
fig-caption: Developer
tags: [Developer, Riset, Tips]
---
Bismillah, Halo sobat ngoding.....
Kali ini saya akan bercerita tentang kecepatan sebuah methode dalam mencari data terkecil dari kumpulan data training. Dalam riset ini saya membuat data training dengan menggunakan sebuah object buatan saya sendiri.

Awalnya saya hanya ingin mencari methode terbaik untuk menghitung dan mencari data dari sekumpulan data, tentunya saya memiliki banyak pilihan untuk menggunakan beberapa methode yang ada pada bahasa pemrograman dart. 
<!--more-->

Berikut hasil simulasi dan percobaan yang saya lakukan.

## Simulasi ##

1. Percobaan saya lakukan dengan menggunakan bahasa pemrograman dart

2. Editor yang  digunakan adalah online editor pada web [dartpad](https://dartpad.dev/)

3. Percobaan  dilakukan dengan menggunakan 10.000 data training

4. *Data yang dicari adalah data yang lebih dari 3 dan kurang dari 8*

5. Percobaan dilakukan dengan menghitung lama sebuah solusi(methode) dieksekusi

6. Percobaan dilakukan sebanyak 100x pada masing masing solusi

## Object Training Dalam bahasa dart ##

```dart
class Data {
  int lat;
  int lang;
  double jarak;

  Data({this.lat, this.jarak, this.lang});

  toJson() {
    return {'lat': lat, 'lang': lang, 'jarak': jarak};
  }
}
```

## Data Training ##

```dart
final dataTrainig = [];
```

## Solusi ##

Solusi yang diberikan dibedakan berdasarkan jenis-jenis Perulangan(for) yang ada pada bahasa pemrograman dart. Pada penelitian ini, terdapat 4 jenis jenis perulangan(solusi), antara lain : 

*Solusi 1*

```dart
solusi1() {
  double jarakTerdekat = double.infinity;
  Data dataTerdekat;
  dataTrainig.forEach((data) {
    if (data.jarak > 3.0 && data.jarak < 8.0) {
      if (data.jarak < jarakTerdekat) {
        jarakTerdekat = data.jarak;
        dataTerdekat = data;
      }
    }
  });
  return jarakTerdekat;
}
```

*Solusi 2*

```dart
solusi2() {
  double jarakTerdekat = double.infinity;
  Data dataTerdekat;
  for (Data data in dataTrainig) {
    if (data.jarak > 3.0 && data.jarak < 8.0) {
      if (data.jarak < jarakTerdekat) {
        jarakTerdekat = data.jarak;
        dataTerdekat = data;
      }
    }
  }
  return jarakTerdekat;
}
```

*Solusi 3*

```dart
solusi3() {
  double jarakTerdekat = double.infinity;
  Data dataTerdekat;
  for (var i = 0; i < dataTrainig.length; i++) {
    var data = dataTrainig[i];
    if (data.jarak > 3.0 && data.jarak < 8.0) {
      if (data.jarak < jarakTerdekat) {
        jarakTerdekat = data.jarak;
        dataTerdekat = data;
      }
    }
  }
  return jarakTerdekat;
}
```

*Solusi 4*

```dart
solusi4() {
  double jarakTerdekat = double.infinity;
  Data dataTerdekat;
  int totalData = dataTrainig.length;
  for (var i = 0; i < totalData; i++) {
    var data = dataTrainig[i];
    if (data.jarak > 3.0 && data.jarak < 8.0) {
      if (data.jarak < jarakTerdekat) {
        jarakTerdekat = data.jarak;
        dataTerdekat = data;
      }
    }
  }
  return jarakTerdekat;
}
```

*Solusi 5*

```dart
solusi5(double jarakTerdekat, int index, Data dataTerdekat) {
  final stopwatch = Stopwatch()..start();
  if (index < dataTrainig.length - 1) {
    if (jarakTerdekat > dataTrainig[index].jarak) {
      jarakTerdekat = dataTrainig[index].jarak;
      dataTerdekat = dataTrainig[index];
      index++;
      solusi5(jarakTerdekat, index, dataTerdekat);
    } else {
      index++;
      solusi5(jarakTerdekat, index, dataTerdekat);
    }
  } else {
      jarakTerdekat=dataTerdekat.jarak;
  }
  return jarakTerdekat;
}
```

## Methode Execution ##

```dart
void main() {

//simulasi jika ada 10.000 data
//asumsi data yang ada dalam area adalah diatas 3 dan dibawah 8
//jarak terkecil yang akan diambil

  for (var i = 0; i < 10000; i++) {
//    generate 10k Data
    dataTrainig
        .add(new Data(lat: i, lang: i, jarak: new Random().nextDouble() * 10));
  }

  for (var i = 0; i < 100; i++) {
//    finding Solution
    final stopwatch = Stopwatch()..start();
//        solusi1();
//        solusi2();
//        solusi3();
//        solusi4();
        solusi5(double.infinity, 0, new Data());
    print('${stopwatch.elapsed.toString().split(':')[2].split('.')[1]}');
  }
}

```

## Hasil ##

Hasil (Waktu dalam satuan millisecond(ms))
![Hasil Time](https://github.com/congfandi/riset/blob/master/Diagram%20Pencarian%20Data%20Terkecil%20dengan%205%20methode%20(1).png?raw=true)

Hasil (Rata-Rata Waktu(ms))
![Total WAktu](https://github.com/congfandi/riset/blob/master/Screen%20Shot%202020-04-12%20at%2017.47.44.png?raw=true)

Tabel Hasil

|Percobaan Ke|	Methode 1	|Methode 2	|Methode 3	|Methode 4	|Methode 5|
|:----------:|:----------:|:---------:|:---------:|:---------:|:-------:|
|1	|1069|1677|1727	|1350|2568|
|2	|573|	527	|2844	|1973|312|
|3	|166|	745	|282	|236|	278|
|4	|200|	698	|236	|166|	259|
|5	|201|	853	|243	|205|	247|
|6	|293|	525	|225	|193|	233|
|7	|466|	138	|215	|299|	251|
|8	|162|	122	|220	|228|	236|
|9	|157|	114	|204	|445|	228|
|10	|150|	110	|179	|166|	258|
|11	|148|	123	|165	|159|	553|
|12	|145|	118	|126	|135|	787|
|13	|148|	114	|119	|135|	498|
|14	|147|	114	|114	|136|	559|
|15	|148|	111	|111	|132|	648|
|16	|149|	112	|112	|128|	484|
|17	|154|	112	|115	|138|	549|
|18	|155|	109	|173	|128|	517|
|19	|155|	109	|154	|129|	501|
|20	|150|	109	|160	|139|	619|
|21	|149|	180	|183	|138|	559|
|22	|151|	115	|166	|138|	426|
|23	|152|	143	|166	|153|	585|
|24	|584|	154	|185	|152|	1193|
|25	|1209|126	|181	|187|	555|
|26	|541|	122	|189	|210|	430|
|27	|615|	133	|192	|209|	961|
|28	|748|	146	|320	|241|	302|
|29	|667|	2545|	510	|299|	215|
|30	|598|	271	|180	|520|	208|
|31	|434|	255	|170	|235|	208|
|32	|356|	369	|162	|282|	206|
|33	|346|	766	|159	|185|	200|
|34	|329|	429	|172	|215|	208|
|35	|319|	300	|566	|161|	216|
|36	|318|	292	|191	|155|	213|
|37	|310|	284	|205	|235|	327|
|38	|365|	335	|252	|168|	1090|
|39	|316|	267	|294	|169|	220|
|40	|316|	291	|204	|210|	213|
|41	|354|	213	|211	|218|	217|
|42	|370|	298	|152	|215|	215|
|43	|408|	439	|144	|437|	228|
|44	|864|	451	|141	|163|	272|
|45	|521|	312	|141	|159|	337|
|46	|506|	314	|150	|159|	297|
|47	|376|	288	|137	|156|	217|
|48	|342|	212	|139	|184|	215|
|49	|432|	286	|141	|166|	223|
|50	|421|	333	|154	|213|	271|
|51	|347|	307	|149	|163|	217|
|52	|342|	283	|140	|252|	221|
|53	|330|	292	|144	|245|	209|
|54	|333|	294	|186	|172|	206|
|55	|321|	430	|154	|172|	206|
|56	|384|	292	|146	|156|	210|
|57	|350|	368	|140	|158|	223|
|58	|328|	288	|148	|154|	206|
|59	|326|	214	|141	|160|	209|
|60	|337|	281	|183	|147|	202|
|61	|320|	294	|142	|148|	201|
|62	|318|	287	|189	|150|	213|
|63	|315|	209	|140	|166|	200|
|64	|316|	278	|142	|148|	200|
|65	|319|	285	|147	|154|	198|
|66	|314|	279	|141	|160|	199|
|67	|314|	276	|140	|150|	198|
|68	|317|	326	|144	|154|	213|
|69	|316|	383	|139	|150|	201|
|70	|366|	297	|135	|142|	204|
|71	|481|	290	|135	|148|	202|
|72	|325|	289	|141	|152|	213|
|73	|343|	359	|136	|237|	198|
|74	|324|	478	|141	|244|	204|
|75	|327|	660	|137	|169|	232|
|76	|311|	308	|151	|156|	228|
|77	|322|	320	|149	|153|	208|
|78	|311|	319	|135	|145|	208|
|79	|363|	438	|144	|148|	204|
|80	|312|	482	|141	|176|	205|
|81	|320|	289	|137	|157|	220|
|82	|308|	296	|135	|155|	203|
|83	|322|	287	|136	|155|	204|
|84	|308|	207	|145	|150|	209|
|85	|448|	278	|139	|162|	203|
|86	|321|	202	|146	|153|	205|
|87	|343|	433	|136	|164|	203|
|88	|318|	329	|145	|149|	202|
|89	|318|	556	|134	|152|	201|
|90	|322|	306	|135	|152|	202|
|91	|322|	439	|129	|157|	203|
|92	|484|	756	|218	|240|	278|
|93	|407|12020| 147	|234|	210|
|94	|342|	567	|145	|275|	209|
|95	|461|	450	|140	|186|	238|
|96	|356|	2663|	166	|162|	217|
|97	|466|	906	|153	|151|	221|
|98	|599|	1436|	142	|154|	207|
|99	|520|	368	|139	|148|	203|
|100|1172|367	|134	|151|	217|

## Kesimpulan ##

- Methode tercepat dalam menemukan data terkecil adalah methode ke 4 dan ke 3
- Methode yang paling lama dalam menemukan data terkecil adalah methode ke 2
- Methode 4 dan 3 tidak memiliki perbedaan yang signifikan
- Methode 1 dan 2 memiliki perbedaan waktu yang tidak terlalu jauh yakni 22.8 dan 31.1 persen. 

## Source Code ##
Source Code dapat dilihat pada link [Github](https://github.com/congfandi/riset)
>Penulis bukan orang yang paling mampu, hanya ingin berbagi saja. Semoga dapat mengambil manfaat<small> - Penulis</small>


