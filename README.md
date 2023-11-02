# flutter_plugin_pubdev

Terdapat 2 laporan yaitu laporan praktikum dan soal Laporan Praktikum Manajemen Plug in kelas 3A dibawahnya.

<b>Praktikum Menerapkan Plugin di Project Flutter</b>

Langkah 1: Buat Project Baru
Buatlah sebuah project flutter baru dengan nama flutter_plugin_pubdev. Lalu jadikan repository di GitHub Anda dengan nama flutter_plugin_pubdev.
flutter baru dengan nama flutter_plugin_pubdev.
![Screenshot flutter_plugin_pubdev](images/1.jpg)
repository di GitHub dengan nama flutter_plugin_pubdev.
![Screenshot flutter_plugin_pubdev](images/2.jpg)

Langkah 2: Menambahkan Plugin
Tambahkan plugin auto_size_text menggunakan perintah berikut di terminal

flutter pub add auto_size_text
![Screenshot flutter_plugin_pubdev](images/3.jpg)

Jika berhasil, maka akan tampil nama plugin beserta versinya di file pubspec.yaml pada bagian dependencies.
![Screenshot flutter_plugin_pubdev](images/4.jpg)

Langkah 3: Buat file red_text_widget.dart
Buat file baru bernama red_text_widget.dart di dalam folder lib lalu isi kode seperti berikut.

import 'package:flutter/material.dart';

class RedTextWidget extends StatelessWidget {
  const RedTextWidget({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container();
  }
}
![Screenshot flutter_plugin_pubdev](images/5.jpg)

Langkah 4: Tambah Widget AutoSizeText
Masih di file red_text_widget.dart, untuk menggunakan plugin auto_size_text, ubahlah kode return Container() menjadi seperti berikut.

return AutoSizeText(
      text,
      style: const TextStyle(color: Colors.red, fontSize: 14),
      maxLines: 2,
      overflow: TextOverflow.ellipsis,
);
![Screenshot flutter_plugin_pubdev](images/6.jpg)

Setelah Anda menambahkan kode di atas, Anda akan mendapatkan info error. Mengapa demikian? Jelaskan dalam laporan praktikum Anda!
Karena terdapat 2 data invalid yaitu AutoSizeText karena metode tersebut belum terdefinisi pada redtextwidget tersebut dan text karena text masih belum terdefinisi pada redtextwidget tersebut.

Langkah 5: Buat Variabel text dan parameter di constructor
Tambahkan variabel text dan parameter di constructor seperti berikut.

final String text;

const RedTextWidget({Key? key, required this.text}) : super(key: key);
![Screenshot flutter_plugin_pubdev](images/7.jpg)
karena menambahkan variabel text tersebut text menjadi valid, selanjutnya saya menambahkan import 'package:auto_size_text/auto_size_text.dart'; agar AutoSizeTextnya valid.
![Screenshot flutter_plugin_pubdev](images/8.jpg)

Langkah 6: Tambahkan widget di main.dart
Buka file main.dart lalu tambahkan di dalam children: pada class _MyHomePageState

Container(
   color: Colors.yellowAccent,
   width: 50,
   child: const RedTextWidget(
             text: 'You have pushed the button this many times:',
          ),
),
Container(
    color: Colors.greenAccent,
    width: 100,
    child: const Text(
           'You have pushed the button this many times:',
          ),
),
![Screenshot flutter_plugin_pubdev](images/9.jpg)

Run aplikasi tersebut dengan tekan F5, maka hasilnya akan seperti berikut.
![Screenshot flutter_plugin_pubdev](images/10.jpg)

<b>Laporan Praktikum Manajemen Plug in kelas 3A</b>

1. Selesaikan Praktikum Menerapkan Plugin di Project Flutter diatas, lalu dokumentasikan dan push ke repository Anda berupa screenshot hasil pekerjaan beserta penjelasannya di file README.md!

Laporan berada diatas.

2. Jelaskan maksud dari langkah 2 pada praktikum tersebut!

Langkah menambahkan plugin menggunakan perintah flutter pub add adalah cara untuk memasukkan dependensi plugin tertentu ke dalam proyek Flutter. Plugin ini merupakan paket atau perpustakaan pihak ketiga yang dikembangkan oleh komunitas atau pihak lain yang menyediakan fungsi tambahan yang dapat digunakan dalam proyek Flutter.

Dengan menambahkan plugin tersebut, dapat mendapatkan akses ke fitur-fitur yang disediakan oleh plugin tersebut dalam aplikasi tanpa harus menulis kode dari awal atau mengembangkan fitur yang serupa secara manual. Ini memungkinkan untuk memperluas fungsionalitas aplikasi dengan mudah dan efisien.

Secara khusus, dalam kasus ini menggunakan perintah flutter pub add auto_size_text untuk menambahkan plugin "auto_size_text" ke proyek. Plugin ini, seperti namanya, menyediakan kemampuan untuk mengatur ukuran teks secara otomatis berdasarkan ruang yang tersedia dalam widget yang mengandung teks. Ini sangat berguna ketika ingin menghindari pemotongan teks atau overflow dalam antarmuka pengguna.

Setelah menjalankan perintah tersebut, dependensi untuk plugin "auto_size_text" akan ditambahkan ke file pubspec.yaml dalam bagian dependencies, dan dapat mulai menggunakan plugin ini dalam proyek Flutter. Dapat mengimpor plugin ini dan menggunakannya sesuai kebutuhan dalam kode aplikasi.

3. Jelaskan maksud dari langkah 5 pada praktikum tersebut!

Langkah 5 mengharuskan untuk menambahkan sebuah variabel bernama text dan parameter di konstruktor widget RedTextWidget. Tujuan dari langkah ini adalah:

Variabel text: Dengan menambahkan variabel text, menciptakan sebuah wadah (container) untuk teks yang akan ditampilkan oleh widget. Ini memungkinkan pengguna widget RedTextWidget untuk menentukan teks yang akan ditampilkan saat menggunakannya. Karena pada langkah 4, text belum valid karena belum terdefinisi.

Parameter di Konstruktor: Dengan menambahkan parameter required this.text di konstruktor RedTextWidget, memberikan cara bagi pengguna widget untuk mengirimkan nilai teks ketika mereka membuat atau menginstansiasi widget ini. Dengan demikian, widget dapat digunakan secara fleksibel untuk menampilkan berbagai teks yang berbeda berdasarkan kebutuhan aplikasi.

Secara keseluruhan, langkah ini memberikan fleksibilitas dalam penggunaan widget RedTextWidget, untuk menentukan teks yang akan ditampilkan, sehingga widget ini dapat digunakan untuk berbagai konten teks yang berbeda dalam aplikasi.

4. Pada langkah 6 terdapat dua widget yang ditambahkan, jelaskan fungsi dan perbedaannya!

RedTextWidget:
- Fungsi: Ini adalah custom widget yang menggabungkan teks dengan warna merah dan fitur autofit teks yang dikendalikan oleh plugin auto_size_text.
- Perbedaan: Widget ini menerima satu parameter yaitu text, yang memungkinkan untuk menentukan teks yang akan ditampilkan. Widget ini menggunakan autofit text untuk mengatur ukuran teks agar sesuai dengan ruang yang tersedia dalam wadahnya. Ini berguna jika ingin menghindari pemotongan teks atau overflow. Dalam contoh ini, menggunakan RedTextWidget untuk menampilkan pesan "You have pushed the button this many times:" dengan teks berwarna merah.

Text Widget:
- Fungsi: Text adalah widget bawaan Flutter yang digunakan untuk menampilkan teks. bisa mengatur style teks, seperti warna dan ukuran font, tetapi teks ini tidak secara otomatis menyesuaikan ukuran atau mengatasi jumlah baris.
- Perbedaan: Widget ini adalah widget bawaan Flutter yang hanya menampilkan teks sesuai dengan parameter yang diberikan. Dalam contoh ini, menggunakan Text untuk menampilkan pesan yang serupa dengan "You have pushed the button this many times:", tetapi teks ini tidak akan menyesuaikan ukuran atau jumlah baris secara otomatis.

Jadi, perbedaan utama antara keduanya adalah cara tampilan dan perilaku teks yang ditampilkan. RedTextWidget memiliki fitur autofit teks yang disediakan oleh plugin auto_size_text, sementara Text adalah widget dasar untuk menampilkan teks tanpa penyesuaian otomatis ukuran atau jumlah baris.

5. Jelaskan maksud dari tiap parameter yang ada di dalam plugin auto_size_text berdasarkan tautan pada dokumentasi ini !

penjelasan dari parameter-parameter yang ada dalam plugin auto_size_text berdasarkan dokumentasi yang diberikan:

- key: Parameter ini digunakan untuk mengontrol bagaimana satu widget menggantikan widget lain dalam pohon widget. Ini sering digunakan untuk pengujian widget dan manajemen widget.

- textKey: Parameter ini digunakan untuk mengatur kunci (key) untuk widget Text yang dihasilkan. Key digunakan untuk mengidentifikasi widget secara unik dan dapat digunakan dalam pengujian dan manajemen widget.

- style: Parameter ini digunakan untuk menentukan gaya (style) teks yang akan digunakan untuk widget. Dapat mengatur properti seperti warna, ukuran font, jenis font, dll.

- minFontSize: Parameter ini digunakan untuk menentukan batasan ukuran font teks minimum yang akan digunakan saat menyesuaikan ukuran teks secara otomatis. Ini memastikan teks tidak menjadi terlalu kecil.

- maxFontSize: Parameter ini digunakan untuk menentukan batasan ukuran font teks maksimum yang akan digunakan saat menyesuaikan ukuran teks secara otomatis. Ini memastikan teks tidak menjadi terlalu besar.

- stepGranularity: Parameter ini digunakan untuk mengatur langkah (step) dalam penyesuaian ukuran font berdasarkan batasan. Ini mengontrol seberapa sering ukuran font diperbarui.

- presetFontSizes: Parameter ini digunakan untuk menentukan daftar ukuran font yang telah ditentukan sebelumnya. Harus dalam urutan menurun. Jika diatur, maka minFontSize dan maxFontSize akan diabaikan.

- group: Parameter ini digunakan untuk mensinkronkan ukuran teks antara beberapa AutoSizeText sehingga ukuran teksnya tetap sama.

- textAlign: Parameter ini digunakan untuk mengatur cara teks diatur secara horizontal, seperti TextAlign.start, TextAlign.center, dan TextAlign.end.

- textDirection: Parameter ini digunakan untuk mengatur arah teks, yang mempengaruhi interpretasi nilai seperti TextAlign.start dan TextAlign.end.

- locale: Parameter ini digunakan untuk memilih jenis font yang berbeda berdasarkan bahasa atau lokasi. Ini berguna jika karakter Unicode dapat dirender secara berbeda tergantung pada bahasa atau lokasi.

- softWrap: Parameter ini mengatur apakah teks harus mematahkan baris pada pemisah baris lembut.

- wrapWords: Parameter ini mengatur apakah kata-kata yang tidak muat dalam satu baris harus dipisahkan. Jika diatur true, akan berperilaku seperti widget Text.

- overflow: Parameter ini mengatur bagaimana tampilan overflow harus diatasi. Contoh nilai yang mungkin adalah TextOverflow.ellipsis.

- overflowReplacement: Parameter ini digunakan jika teks melebihi batasan dan tidak muat dalam batasnya. Widget ini akan ditampilkan sebagai gantinya.

- textScaleFactor: Parameter ini mengatur jumlah piksel font untuk setiap piksel logis dan mempengaruhi minFontSize, maxFontSize, dan presetFontSizes.

- maxLines: Parameter ini mengatur jumlah maksimum baris yang diperbolehkan untuk teks.

- semanticsLabel: Parameter ini mengatur label semantik alternatif untuk teks yang ditampilkan. Ini berpengaruh pada aksesibilitas aplikasi.

6. Kumpulkan laporan praktikum Anda berupa link repository GitHub melalui Assignment ini !