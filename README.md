Nama : Nur Alya Khairina  
NPM : 2306275701  
Kelas : PBP A

# SPARERAVEL
# Tugas 7
1. **Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.**  
Sebelum itu, pengertian state adalah informasi yang dapat dibaca secara sinkronus saat widget dibuat dan mungkin berubah selama masa penggunaan widget. Jadi stateless widget adalah widget yang tidak berubah. Tampilan dan properti dari widget ini tetap sama sepanjang *lifetime* widget tersebut. Stateless widget tidak dapat mengubah state-nya selama aplikasi sedang berjalan. Sedangkan stateful widget merupakan widget yang dapat berubah. Widget ini dapat mengubah propertinya saat aplikasi berjalan. Stateful widget bersifat dinamis dan dapat mengubah tampilannya sebagai respons terhadap user. 

    Perbedaan dari keduanya adalah,  
    **a. Stateless widget;**
    - Bersifat statis 
    - Tidak bergantung akan perubahan data
    - Hanya akan dirender satu kali
    - Akan diperbarui jika hanya ketika data eksternal berubah
    - Menangani konten statis  

    **b. Stateful widget;**
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
- Membuat proyek baru dengan nama spareravel_mobile dengan menjalankan kode;
    ```bash
    flutter create spareravel_mobile
    cd spareravel_mobile
    ```
- Membuat file baru bernama `menu.dart` pada direktori `spareravel_mobile/lib`. Lalu menambahkan import;
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
- Menambahkan import dan mengubah kode pada main.dart dengan;
    ```dart
    import 'package:mental_health_tracker/menu.dart';
    ...
    home: MyHomePage(),
    ...
    ```

- Mengubah kode pada `main.dart` dengan;
    ```dart
    colorScheme: ColorScheme.fromSwatch(
            primarySwatch: Colors.blueGrey,  // Warna latar belakang utama
            ).copyWith(secondary: Colors.deepPurple[400]),
    ```
- Mengubah kode di `menu.dart` menjadi
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

- Menambahkan kode pada `menu.dart` dengan
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
- Menambahkan tombol-tombol icon dan *snackbar* pada `menu.dart`
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

# Tugas 8
1. **Apa kegunaan const di Flutter? Jelaskan apa keuntungan ketika menggunakan const pada kode Flutter. Kapan sebaiknya kita menggunakan const, dan kapan sebaiknya tidak digunakan?**  
Kegunaan `const` adalah untuk membuat objek yang bersifat konstanta atau atau tidak adapat berubah. Sehingga nilai dari objek sudah ditetapkan ketika waktu *compile* dan tidak akan bisa diubah saat *runtime*.  Dengan kata lain, *compiler* sudah mengetahui sebelumnya nilai apa yang akan disimpan dalam variabel tersebut.  

    Beberapa keuntungan penggunaan `const` pada *flutter code* yaitu:
    - Mempercepat *build time*: Saat menggunakan `const` maka Flutter mengetahui bahwa widget ini tidak akan berubah, sehingga memungkinkan uuntuk membuat widget satu kali dan memnggunakannya kembali kapanpun. Oleh karena itu, ini menghemat banyak waktu selama *rendering*. Sehingga, mengurangi penggunaan CPU dan mempercepat *rendering* widget
    - Meningkatkan keterbacaan dan mempermudah pemeliharaan aplikasi: Menggunakan `const`, berarti membuat objek yang tidak dapat diubah. Hal ini membuat kode lebih mudah untuk dipahami dan *developer* lain. Selain itu, ini juga mengurangi risiko perilaku yang tidak diharapkan dan membuat *debugging* menjadi lebih mudah
    - Meminimalkan penggunaan memori: `const` merupakan satu contoh widget yang *reuseable* sehingga signifikan mengurangi penggunaan memorii aplikasi.  
  
    Sebaiknya menggunakan `const`ketika memiliki data yang tidak akan berubah selama aplikasi berjalan seperti warna, ukuran font, dsb. Kemudian saat membuat widget yang tidak memerlukan state, seperti Text, Icon, atau Image. Lalu tidak menggunakan `const` ketika memiliki data yang dapat berubah selama aplikasi berjalan. Selain itu ketika membuat widget yang memerlukan *state* seperti TextField. 

2. **Jelaskan dan bandingkan penggunaan Column dan Row pada Flutter. Berikan contoh implementasi dari masing-masing layout widget ini!**   
`Column` dan `Row` adalah dua layout widget di Flutter yang memiliki fungsi untuk mengatur tata letak elemen-elemen children secara vertikal atau horizontal.  
Perbedaan dan contoh implementasinya adalah;  
**a. Column:**
- Menyusun elemen children secara vertikal (atas ke bawah).
    ```dart
    Column(
    children: [
        Text('Judul'),
        SizedBox(height: 14.0),
        Text('Deskripsi'),
        SizedBox(height: 14.0),
        ElevatedButton(
        onPressed: () {},
        child: Text('Tombol'),
        ),
    ],
    )
    ```  
    **b. Row:**
- Menyusun elemen children secara horizontal (kiri ke kanan).
    ```dart
    Row(
    children: [
        Icon(Icons.arrow_back),
        SizedBox(width: 16.0),
        Text('Halaman Utama'),
        Spacer(),
        Icon(Icons.search),
        SizedBox(width: 16.0),
        Icon(Icons.more_vert),
    ],
    )
    ```  

3. **Sebutkan apa saja elemen input yang kamu gunakan pada halaman form yang kamu buat pada tugas kali ini. Apakah terdapat elemen input Flutter lain yang tidak kamu gunakan pada tugas ini? Jelaskan!**   
Elemen input yang saya gunakan adalah `TextFormField` yaitu elemen untuk menerima input teks dari pengguna. Beberapa elemen input yang tidak saya gunakan pada tugas ini antara lain;
    - Checkbox: elemen untuk menerima input boolean seperti, true atau false.
    - Switch: elemen *toggle* untuk mengubah status *active* or *non-active*. 
    - DropdownButton: elemen untuk memilih item dari list item. 
    - Radio: elemen untuk memiliki satu dari beberapa pilihan. 
    - Slider: elemen untuk memilih range dari sebuat *value*. 
4. **Bagaimana cara kamu mengatur tema (theme) dalam aplikasi Flutter agar aplikasi yang dibuat konsisten? Apakah kamu mengimplementasikan tema pada aplikasi yang kamu buat?**  
Pada Flutter, tema dapat diatur dengan menggunakan `ThemeData` pada widget `MaterialApp`. Jika sudah menggunakan tema global, maka aplikasi akan konsisten mengikuti warna dan gaya yang telah didefinisikan. Pada aplikasi saya, saya menggunakan
    ```dart
    theme: ThemeData(
            colorScheme: ColorScheme.fromSwatch(
            primarySwatch: Colors.blueGrey,  
            ).copyWith(secondary: ...,
            useMaterial3: true,
        ),
        )
    ```
    Tema aplikasi saya menggunakan `ColorScheme.fromSwatch` dengan warna utama `Colors.blueGrey`. Saya juga menggunakan `Material3` yang memastikan elemen-elemen pada desain aplikasi saya memberikan tampilan yang lebih modern dan harmonis.  
5. **Bagaimana cara kamu menangani navigasi dalam aplikasi dengan banyak halaman pada Flutter?**  
Untuk menangani navigasi saya menggunakan `Navigator. pushReplacement()` dan `Navigator.push().` Widget Navigator menampilkan halaman-halaman yang ada kepada layar seakan sebagai sebuah tumpukan (stack). Penggunaan `Navigator.pushReplacement() `memastikan bahwa user tidak dapat kembali ke halaman sebelumnya. Sedangkan `Navigator.push()` memungkinkan user untuk kembali ke halaman sebelumnya. `Navigator.push()` akan menambahkan *route* baru diatas *route* yang sudah ada pada atas stack, sedangkan `Navigator.pushReplacement()` menggantikan *route* yang sudah ada pada atas stack dengan *route* baru tersebut. Saya juga menggunakan `ListTile` untuk membuat item menu yang mengarahkan user ke halaman tambah produk atau ke halaman utama. 

# Tugas 9
**1. Jelaskan mengapa kita perlu membuat model untuk melakukan pengambilan ataupun pengiriman data JSON? Apakah akan terjadi error jika kita tidak membuat model terlebih dahulu?**
Perlu dibuatnya model untuk melakukan pengambilan ataupun pengiriman data JSON disebabkan jika  mengggunakan model;
- data JSON yang diambil atau dikirim memiliki tipe data yang sesuai, sehingga meminimalisir runtime error karena tipe data yang tidak sesuai, sehingga model membantu untuk menjaga konsistensi akan struktur data.
- Melakukan konversi JSON ke objek Dart dan konversi objek Dart menjadi JSON kembali lebih mudah karena ada `fromJson()` dan `toJson()`. Sehingga, ini membantu konversi data yang lebih aman dan terstruktur.
- Lebih mudah untuk mengelola dan mencari kesalahan data yang salah tipe atau kurang.

Kemudian jika tidak membuat model maka akan ada kemunginan kesalahan tipe data yang diterima, lalu tidak ada jaminan field akan terpenuhi semua, sehingga akan rentan terjadi runtime error. 

**2. Jelaskan fungsi dari library http yang sudah kamu implementasikan pada tugas ini**  
Library `http` berfungsi untuk berkomunikasi dengan Django, mengirim data (POST), mengambil data (GET) dari server, contohnya ketika mengambil daftar data Product dalam format JSON dari backend. Lalu library ini juga berfungsi untuk mengirim data product yang baru diinput oleh pengguna ke server untuk disimpan ke database dengan mengirim data JSON ke endpoint Django, lalu server akan menyimpan ke data base. Kemudian library ini juuga memastikan aplikasi menunggu dari server sebelum menampilkan data dan memberikan umpan balik berdasarkan status respons. 

**3. Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.**  
Beberapa fungsi dari CookieRequest yaitu untuk mengelola cookie auntentikasi, melakukan request http, menyimpan status apakan pengguna telah login atau belum sehingga membantu menjaga keamanan aplikasi dengan membatasi akses berdasarkan status login kemudian alasan mengapa perlu dibagikan karena untuk memastikan konsistensi autentikasi pada seluruh aplikasi, menghindari adanya login yang berulang, memudahkan management session. 
**4. Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.**
Menambahkan 
```dart
<uses-permission android:name="android.permission.INTERNET" />
``` 
Untuk memastikan aplikasi dapat mengakses internet yang merupakan syarat penggunaan http request.
Lalu, pengguna mengisi form pada aplikasi flutter yaitu pada aplikasi saya adalah `productentry_form.dart` kemudian data yang diisi, dilakukan validasi dengan menggunakan Form dan FormKey, lalu data tersebuut di-encode menjadi JSON dengan menggunakan jsonEncode. Flutter menggunakan library seperti http atau CookieRequest untuk mengirim POST request ke API Django. Selanjutnya Django akan memproses data yang diterima dengan membuat view yang menerima data dari permintaan POST, lalu data akan diserialize, validasi, lalu disimpan ke database. Kemudian, flutter akan melakukan GET request untuk mengambil data dari backend. Django memberikan respons yang berupa data JSON yang diambil dari database. Terakhir, data yang diterima akan diubah menjadi model Dart dengan `fromJson()`.

**5. Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.**
* Registrasi
    - Pengguna mengisi form registrasi, lalu flutter mengirimkan datanya ke API Django dengan menggunakan POST request, terakhir data di-encode dalam bentuk format JSON
    - Django menerima data dan memvalidasi data, jika valid maka akan disimpan ke database.  
* Login
    - Pengguna mengisi username dan password pada form, lalu flutter mengirimkan datanya ke API Django melalui POST request. Penggunaan CookieRequest dan http diperlukan untuk simpan cookie autentikasi pengguna. 
    - Django menggunakan authenticate untuk validasi, lalu jika valud django akan membuat session dan akan dikembalikan session ID ke Flutter. Lalu pengguna diarahkan ke halaman utama menu. 
* Menu
    - Flutter menampilkan tiga button, lalu jika memilih tambah produk maka akan menampilkan form untuk menambah produk, yang mana itu sudah terintegrasi ke database Django.
    - Jika memilih Lihat Daftar Produk maka dari Django akan dikirimkan ke Flutter data-data mana saja yang sesuai dengan user yang sedang login saat ini.
* Logout 
    - Flutter mengirimkan POST request ke logout django
    - Django menghapus session pengguna dan cookie session tersebut ikut dihapus. 
    - Flutter akna menghapus instance CookieRequest dan pengguna diarahkan ke halaman login kembali. 

**6. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).**
- Buat django-app bernama authentication, lalu tambahkan django-cors-headers ke requirements.txt, jalankan pip install django-cors-headers. Tambahkan corsheaders ke INSTALLED_APPS pada main project settings.py. Menambahkan corsheaders.middleware.CorsMiddleware ke MIDDLEWARE pada main project settings.py.
- Pada app authentication, buat method views.py untuk login, register, dan logout dengan memanfaatkan django.contrib.auth. Lalu lakukan routing pada urls.py pada folder authentication. Kemudian, menambahkan path auth pada urls.py root folder.
- Install package provider dan pbp_django_auth. Lalu saya gunakan package tersebut dengan modifikasi root widget untuk sediakan CookieRequest dan menggunakan Provider.
- Kemudian, pada folder screen, saya tambahkan file baru untuk menangani login dan register. Kemudian untuk bagian logout itu berada di 
- Ubah pada file main.dart dari home: MyHomePage() menjadi home: const LoginPage(). Namun, jika user belum pernah register maka akan diarahkan ke register page. 
- Melakukan flutter pub add http untuk menambahkan package http. Karena ingin memakai http request maka harus diperbolehkan akses internet pada Flutter dengan menggunakan 
```xml
<uses-permission android:name="android.permission.INTERNET" />
```
- Membuat model pada file `mood_entry.dart` yaitu name, price, description dan quantity.
- Melakukan fetch data dengan membuat file `list_productentry.dart` dengan memanfaatkan `fromJson()`dan fetchProduct.
- Membuat method view pada main/views.py untuk membuat create product pada Flutter, lalu lakukan routing.
- Hubungkan page productentry_form.dart dengan CookieRequest, lalu gunakan `postJson()` dengan model yang sudah dibuat.
- Buat file baru untuk menampilkan detail dari setiap product. Pada detail tersebut, menampilkan nama produk, harga produk, deskripsi, dan jumlah produk. Kemudian menambahkan button untuk kembali ke halaman daftar item. 
