Nama : Nur Alya Khairina
NPM : 2306275701
Kelas : PBP A

# SPARERAVEL
# Tugas 7
1. **Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.**
Sebelum itu, pengertian state adalah informasi yang dapat dibaca secara sinkronus saat widget dibuat dan mungkin berubah selama masa penggunaan widget. Jadi stateless widget adalah widget yang tidak berubah. Tampilan dan properti dari widget ini tetap sama sepanjang *lifetime* widget tersebut. Stateless widget tidak dapat mengubah state-nya selama aplikasi sedang berjalan. Sedangkan stateful widget merupakan widget yang dapat berubah. Widget ini dapat mengubah propertinya saat aplikasi berjalan. Stateful widget bersifat dinamis dan dapat mengubah tampilannya sebagai respons terhadap user. 

Perbedaan dari keduanya adalah, 
a. Stateless widget;
- Bersifat statis 
- Tidak bergantung akan perubahan data
- Hanya akan dirender satu kali
- Akan diperbarui jika hanya ketika data eksternal berubah
- Menangani konten statis

b. Stateful widget;
- Bersifat dinamis
- Diperbaru selama aplikasi berjalan berdasarkan interaksi user atau perubahan data
- Dapat me-render ulang jika ada perubahan 
- Menangani interaktif komponen (dinamis)

2. **Sebutkan widget apa saja yang kamu gunakan pada proyek ini dan jelaskan fungsinya.**
Widget yang saya gunakan pada tugas 7 ini antara lain;
- MaterialApp: Sebagai aplikasi utama yang mengatur tema, judul, dan halaman home
- Scaffold: Menyediakan struktur aplikasi dasar dengan AppBar dan body
- AppBar: Menampilkan bar navigasi bagian paling atas
- Column: Menyusuk widget secara vertikal
- Row: Menyusun widget secara horizontal (InfoCard)
- Padding: Memberikan jarak pada widget
- Text: Menampilkan teks
- GridView.count: Menampilkan widget dalam bentuk grid dengan kolom tetap
- Card: Membuat material desain card 
- InkWell: Menangani widget yang diklik atau ditekan.
- SnackBar: Menampilkan pesan di bagian bawah saat ItemCard ditekan 
- Center: Memusatkan anak-anak dari widget
- SizedBox: Membuat kotak denga dimensi tertentu

3. **Apa fungsi dari setState()? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.**
setState adalah method yang digunakan pada StatefulWidgets untuk memberi tahu bahwa status internal sebuah objek telah berubah. Ketika method ini dipanggil, maka widget akan mengalami rebuild sesuai data yang terbaru. Variabel yang terdapak adalah variabel dalam State yang digunakan untuk mengontrol tampilan aplikasi. 


4. **Jelaskan perbedaan antara const dengan final.**
Perbedaan antara const dan final adalah;
a. const
- Digunakan untuk nilai konstan yang diketahui sebelumnya
- Menentukan nilai yang sudah harus di tetapkan saat waktu kompilasi dan tidak dapat diubah
- Digunakan untuk variabel dan constructor, tidak dapat diterapkan pada kelas secara keseluruhan

b. final
- Hanya dapat diinisialisasi sekali
- Nilainya tidak dapat diubah setelah itu. 
- Nilainya dapat ditentukan saat runtime


5. **Jelaskan bagaimana cara kamu mengimplementasikan checklist-checklist di atas.**
1. Membuat proyek baru dengan nama spareravel_mobile dengan menjalankan kode;
```bash
flutter create spareravel_mobile
cd spareravel_mobile
```
2. Membuat file baru bernama `menu.dart` pada direktori `spareravel_mobile/lib`. Lalu menambahkan import;
```dart
import 'package:flutter/material.dart';
```
3. Dari file main.dart, pindahkan kode ke file menu.dart;
```dart
class MyHomePage ... {
    ...
}

class _MyHomePageState ... {
    ...
}
```
4. Menambahkan import dan mengubah kode pada main.dart dengan;
```dart
import 'package:mental_health_tracker/menu.dart';
...
home: MyHomePage(),
...
```

5. Mengubah kode pada `main.dart` dengan;
```dart
colorScheme: ColorScheme.fromSwatch(
          primarySwatch: Colors.blueGrey,  // Warna latar belakang utama
        ).copyWith(secondary: Colors.deepPurple[400]),
```
6. Mengubah kode di `menu.dart` menjadi
```dart
class MyHomePage extends StatelessWidget {
    MyHomePage({super.key});

    @override
    Widget build(BuildContext context) {
	return Scaffold(
	    ... // jangan copy titik-titik ini!
	);
    }
}
```

7. Menambahkan kode pada `menu.dart` dengan
```dart
class MyHomePage extends StatelessWidget {
    ...
    final List<ItemHomepage> items = [
          ItemHomepage("Lihat Daftar Produk", Icons.shopping_cart,Colors.yellow ),
          ItemHomepage("Tambah Produk", Icons.add, Colors.orange),
          ItemHomepage("Logout", Icons.logout, Colors.deepOrange),
      ];
    ...
}
 ...
 class ItemHomepage {
     final String name;
     final IconData icon;

     ItemHomepage(this.name, this.icon);
 }
 ...

```
8. Menambahkan tombol-tombol icon dan *snackbar* pada `menu.dart`
```dart
class ItemCard extends StatelessWidget {
  final ItemHomepage item; 
  const ItemCard(this.item, {super.key}); 
  @override
  Widget build(BuildContext context) {
    return Material(
      color: item.color,
      borderRadius: BorderRadius.circular(12),
      
      child: InkWell(
        onTap: () {
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(
              SnackBar(content: Text("Kamu telah menekan tombol ${item.name}!"))
            );
        },
        child: Container(
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 30.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
```



