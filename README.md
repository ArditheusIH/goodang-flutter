<details>
<summary>Getting Started</summary>
# goodang

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
</details>

<details>
<summary>Tugas 7</summary>
 <p>
 Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?</p>
 <p>
 Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing.
</p>
Scaffold: 
AppBar: 
Text: 
SingleChildScrollView: 
Padding: 
Column: 
GridView: 
Material: 
InkWell: 
Container: 
Center: 
Column: 
Icon: 
ScaffoldMessenger: 
SnackBar: 


 <p>
 Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial)
</p>


1. Membuat proyek flutter baru bernama goodang
```
flutter create goodang
```
2. Membuat file baru bernama `menu.dart` pada direktori shopping_list/lib. Lalu menambahkan kode berikut
```dart
import 'package:flutter/material.dart';
```
3. Menambahkan import ke `main.dart`
```dart
import 'package:goodang/menu.dart';
```
4. memindahkan kode dua class ini ke `menu.dart`
```dart
class MyHomePage ... {
    ...
}

class _MyHomePageState ... {
    ...
}
```
5. mengubah class `MyHomePage` menjadi Stateless
```dart
class MyHomePage extends StatelessWidget {
  MyHomePage({Key? key}) : super(key: key);
  ...
```
6. Membuat class baru bernama `ShopItem`
```dart
class ShopItem {
  final String name;
  final IconData icon;
  final Color color;

  ShopItem(this.name, this.icon, this.color);
}
```
attribute color digunakan untuk membuat setiap tombol bisa berbeda warna
7. Menambahkan 3 tombol `Lihat Item`, `Tambah Item`, dan `Logout` di bawah kode `MyHomePage({Key? key}) : super(key: key);`
```dart
final List<ShopItem> items = [
    ShopItem("Lihat Item", Icons.checklist, const Color.fromARGB(255, 63, 181, 81)),
    ShopItem("Tambah Item", Icons.add_box,const Color.fromARGB(255, 0, 0, 246)),
    ShopItem("Logout", Icons.logout, const Color.fromARGB(255, 255, 0, 0)),
];
```
8. Menambahkan kode ini di dalam `Widget build(BuildContext context)`
```dart
return Scaffold(
      appBar: AppBar(
        title: const Text(
          'Goodang',
        ),
      ),
      body: SingleChildScrollView(
        // Widget wrapper yang dapat discroll
        child: Padding(
          padding: const EdgeInsets.all(10.0), // Set padding dari halaman
          child: Column(
            // Widget untuk menampilkan children secara vertikal
            children: <Widget>[
              const Padding(
                padding: EdgeInsets.only(top: 10.0, bottom: 10.0),
                // Widget Text untuk menampilkan tulisan dengan alignment center dan style yang sesuai
                child: Text(
                  'PBP Shop', // Text yang menandakan toko
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 30,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ),
              // Grid layout
              GridView.count(
                // Container pada card kita.
                primary: true,
                padding: const EdgeInsets.all(20),
                crossAxisSpacing: 10,
                mainAxisSpacing: 10,
                crossAxisCount: 3,
                shrinkWrap: true,
                children: items.map((ShopItem item) {
                  // Iterasi untuk setiap item
                  return ShopCard(item);
                }).toList(),
              ),
            ],
          ),
        ),
      ),
    );
```
9. Membuat widget stateless baru untuk menampilkan card.
```dart
class ShopCard extends StatelessWidget {
  final ShopItem item;

  const ShopCard(this.item, {super.key}); // Constructor

  @override
  Widget build(BuildContext context) {
    return Material(
      color: item.color,
      child: InkWell(
        // Area responsive terhadap sentuhan
        onTap: () {
          // Memunculkan SnackBar ketika diklik
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));
        },
        child: Container(
          // Container untuk menyimpan Icon dan Text
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
}
```



</details>