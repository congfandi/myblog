---
title: Tutorial Membuat Speech Recognition di IOS #judul postingan
img:  210618/speech.jpg #gambar postingan taruh di assets/img dan langsung call nama imagenya
layout: post #default jangan diganti
author: Cong Fandi #default me
author-img : congfandi.jpeg #default me
author-detail : iOS Developer, Android Developer, Web Developer # default me
fig-caption: Developer #default me
tags: [Developer, iOS, iPhone]# tags dalam array [Developer, Web, Tips]
---


Hola sobat ngoding dimanapun kalian berada, kita berjumpa lagi dalam sebuah karya sederhana dari anak desa. Sudah lama sekali saya belum mempublikasikan sebuah tulisan karena kesibukan. Oke tanpa berbasa basi, kali ini saya akan sedikit sharing tentang sebuah teknologi yang dimliki oleh Apple sebut saja `Speech Recognition`. Speech recognition ini berbeda ya dengan "Si cantik" Siri yang sudah bisa digunakan secara luas pada platform yang dikeluarkan oleh Apple.

Ok yuk kita lanjut ke bagian bagian ngoding dulu.


## Kebutuhan / Prasyarat

Sebelum kalian melanjutkan, ada baiknya kita bahas dulu hal hal yang dibutuhkan untuk membuat tutorial kali ini, karena tidak semua platform dapat menjalankan hal ini.


|  Spesifikasi  | Keterangan      |
| :------------ |:---------------:|
| OS            | MacOs           |
| Editor/Tool   | Xcode           |
| Platform      | iPhone/iPhone Simulator |


Spesifikasi diatas hanyalah saran guys, jika kalian ada cara lain masih tetap bisa mengikuti tutorial ini.



### Membuat Layout 
Pembuatan layout ini akan kita lakukan dengan menggunakan storyboard, untuk hasilnya dapat kalian lihat pada gambar dibawah ini. 

Untuk langkah pertama ini silahkan kalian membuat project terlebih dahulu pada Xcode kailan, kemudian buka file `Main.storybord`.

*Pastikan buat project default agar nama file bisa sama dengan apa yang akan kita lakukan di project ini*

![Preferences]({{site.url}}/assets/img/210618/image1.png)

Gambar diatas adalah tampilan projcet secara keseluruhan. Idenya adalah jika kalian ucapkan 1 kata dalam bahasa ingris kita akan mengganti warnanya dengan warna yang kita ucapkan.


## Koneksikan layout yang kita buat dengan controller
![Preferences]({{site.url}}/assets/img/210618/image2.png)

Jika kalian berhasil mengkoneksikan component kalian pada controllerview, kalian dapat melihatnya dengan cara klik kanan pada component yang kalian inginkan dan akan terlihat seperti gambar diatas.

Berikan nama pada component kalian serperti pada gambar ini, tujuannya untuk meminimalisir error di code kalian

|  Komponen    | idName      |
| :------------ |:---------------:|
| View      | colorView           |
| Tombol Buat Speech  | startButton           |
| text mendeteksi warna      | detectedTextLabel |
|Click tombol speech| startButtonTapped|

Tabel diatas merepresentasikan nama variable yang akan kita tulis pada file `ViewController.swift`

## Inisialisasi kebutuhan speech recognition

Setelah selesai mengkoneksikan semua komponen yang kita pasang di `Main.storyboard` dengan `ViewController.swift`, kita lanjutkan dengan menginisialisasi semua kebutuhan kita terkait speech recognitionnya. Lihat pada gambar dibawah ini.


![Image3]({{site.url}}/assets/img/210618/image3.png)


berikut penjelasannya pada tabel dibawah ini

|  Variabel    | Keterangan      |
| :------------ |:---------------:|
|  let audioEngine| Kita gunakan untuk merekam suara kita|
|  let speechRecognizer| Kita gunakan untuk meminta user menyetujui aplikasi untuk menggunakan fitur speech recognition|
|  let request |Kita gunakan untuk meminta user menyetujui aplikasi untuk menggunakan fitur microphone|
|  var recognitionTask|Kita gunakan untuk melakukan proses pengenalan suara|
|  var isRecording |kita gunakan untuk membuat flag antara sedang merekam atau tidak dalam sedang merekam|


## Membuat rekaman suara dengan menekan tombol 
```swift
    @IBAction func startButtonTapped(_ sender: UIButton) {
        if isRecording == true {
            cancelRecording()
            isRecording = false
            startButton.backgroundColor = UIColor.gray
        } else {
            self.recordAndRecognizeSpeech()
            isRecording = true
            startButton.backgroundColor = UIColor.red
        }
    }
```

## Membuat fungsi pembatalan rekaman suara
```swift
    func cancelRecording() {
        recognitionTask?.finish()
        recognitionTask = nil
        
        // stop audio
        request.endAudio()
        audioEngine.stop()
        audioEngine.inputNode.removeTap(onBus: 0)
    }
```

## Mengecek permission dari speech library
```swift
 func requestSpeechAuthorization() {
        SFSpeechRecognizer.requestAuthorization { authStatus in
            OperationQueue.main.addOperation {
                switch authStatus {
                case .authorized:
                    self.startButton.isEnabled = true
                case .denied:
                    self.startButton.isEnabled = false
                    self.detectedTextLabel.text = "User denied access to speech recognition"
                case .restricted:
                    self.startButton.isEnabled = false
                    self.detectedTextLabel.text = "Speech recognition restricted on this device"
                case .notDetermined:
                    self.startButton.isEnabled = false
                    self.detectedTextLabel.text = "Speech recognition not yet authorized"
                @unknown default:
                    return
                }
            }
        }
    }
```

## Mengubah warna view saat ada kata sesuai warna yang diucapkan
```swift
    func checkForColorsSaid(resultString: String) {
        let finalColor = resultString.prefix(1).uppercased()+resultString.lowercased().dropFirst();
        print("warna \(finalColor)")
        guard let color = Color(rawValue: finalColor) else { return }
        colorView.backgroundColor = color.create
        self.detectedTextLabel.text = resultString
    }
```

## Membuat dialog saat speechrecognition tidak bisa digunakan atau error
```swift
    func sendAlert(title: String, message: String) {
        let alert = UIAlertController(title: title, message: message, preferredStyle: UIAlertController.Style.alert)
        alert.addAction(UIAlertAction(title: "OK", style: UIAlertAction.Style.default, handler: nil))
        self.present(alert, animated: true, completion: nil)
    }
```

## Membuat daftar warna yang akan kita tampilkan
```swift
    enum Color: String {
        case Red, Orange, Yellow, Green, Blue, Purple, Black, Gray

        var create: UIColor {
            switch self {
            case .Red:
                return UIColor.red
            case .Orange:
                return UIColor.orange
            case .Yellow:
                return UIColor.yellow
            case .Green:
                return UIColor.green
            case .Blue:
                return UIColor.blue
            case .Purple:
                return UIColor.purple
            case .Black:
                return UIColor.black
            case .Gray:
                return UIColor.gray
            }
        }
    }
```

## Mulai perekaman suara dan mengkonversinya menjadi string
```swift
func recordAndRecognizeSpeech() {
        let node = audioEngine.inputNode
        let recordingFormat = node.outputFormat(forBus: 0)
        node.installTap(onBus: 0, bufferSize: 1024, format: recordingFormat) { buffer, _ in
            self.request.append(buffer)
        }
        audioEngine.prepare()
        do {
            try audioEngine.start()
        } catch {
            self.sendAlert(title: "Speech Recognizer Error", message: "There has been an audio engine error.")
            return print(error)
        }
        guard let myRecognizer = SFSpeechRecognizer() else {
            self.sendAlert(title: "Speech Recognizer Error", message: "Speech recognition is not supported for your current locale.")
            return
        }
        if !myRecognizer.isAvailable {
            self.sendAlert(title: "Speech Recognizer Error", message: "Speech recognition is not currently available. Check back at a later time.")
            // Recognizer is not available right now
            return
        }
        recognitionTask = speechRecognizer?.recognitionTask(with: request, resultHandler: { result, error in
            if let result = result {
                let bestString = result.bestTranscription.formattedString
                var lastString: String = ""
                for segment in result.bestTranscription.segments {
                    let indexTo = bestString.index(bestString.startIndex, offsetBy: segment.substringRange.location)
                    lastString = String(bestString[indexTo...])
                }
                self.checkForColorsSaid(resultString: lastString)
            } else if let error = error {
                self.sendAlert(title: "Speech Recognizer Error", message: "There has been a speech recognition error.")
                print(error)
            }
        })
    }
```

## Mengecek permision untuk merekam suara
```swift
    override func viewDidLoad() {
        super.viewDidLoad()
        self.requestSpeechAuthorization()//method ini juga bisa kita panggil saat tombol speech ditekan
    }
```


Dan tutorial berakhir xD . Seharusnya apilkasi kalian sudah dapat dijalankan dan untuk mencoba fitur tersebut, kalian cukup running aplikasi dan katakan warna dengan bahasa inggris sebagai contoh coba katakan 'Black'.


Sekian dulu Tutorial kali ini dan sampai jumpa di tutorial lainnya.

Link repo project ini bisa di download [disini](https://github.com/congfandi/speechrecognitionIos)

<br>
<br>
>Jika kau tidak mampu menahan sulitnya belajar, maka kau harus siap menahan perihnya kebodohan<small> - Imam Syafi'i</small>

