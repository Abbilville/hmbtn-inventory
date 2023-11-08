# Harvest Moon: Back to Nature Inventory
### Need Something for your farm?
---

**Creator: Abbilhaidar Farras Zulfikar** <br>
**Students ID: 2206026012** <br>
**Link: TBA** <br>

---
<details>
<summary>Pertanyaan untuk Tugas 7</summary>
<ol>
<li>Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter? <br>
  <ul>
    <li>Stateless Widget <br> 
      Widget yang keadaannya (<i>state</i>) tidak dapat diubah setelah mereka dibuat disebut sebagai <i>stateless widgets</i>. Widget ini bersifat tidak berubah setelah dibuat, artinya tidak peduli perubahan dalam variabel, ikon, tombol, atau pengambilan data, tidak akan mengubah keadaan aplikasi. Berikut adalah struktur dasar <i>stateless widget</i>: <br>
      
      class MyWidget extends StatelessWidget {
        const MyWidget({super.key});
      
        @override
        Widget build(BuildContext context) {
          return const Placeholder();
        }
      }

</li>
    <li>Stateful Widget <br>
    Widget yang <i>state</i> dapat diubah setelah mereka dibuat disebut <i>stateful widgets</i>. <i>States</i> ini dapat diubah dan dapat berubah berkali-kali selama mereka ada. Ini berarti bahwa keadaan aplikasi dapat berubah berkali-kali dengan berbagai set variabel, input, dan data yang berbeda. Di bawah ini adalah struktur dasar dari sebuah <i>stateful widget</i>: <br>

      class MyWidget extends StatefulWidget {
        const MyWidget({super.key});
      
        @override
        State<MyWidget> createState() => _MyWidgetState();
      }
      
      class _MyWidgetState extends State<MyWidget> {
        @override
        Widget build(BuildContext context) {
          return const Placeholder();
        }
      }

</li>
  </ul>
  
|Fitur|Stateless Widget|Stateful Widget|
|:---:|---|---|
|Kehandalan|Tidak menyimpan data state dan bergantung pada data yang diberikan saat dibuat.|Memiliki keadaan internal yang dapat berubah selama siklus hidup widget.|
|Perubahan State|Tidak dapat mengubah state secara langsung.|Dapat mengubah state dan membangun ulang tampilan saat state berubah.|
|Build Method|`build()` hanya dipanggil sekali saat widget dibuat.|`build()` dapat dipanggil berkali-kali saat state berubah.|
|Performa|Biasanya lebih efisien karena tidak ada perlu pembaruan state.|Dapat memiliki overhead performa karena pembaruan state dapat memicu pembaruan tampilan.|
|Contoh Penggunaan|Widget sederhana yang tidak memerlukan pembaruan berulang-ulang.|Digunakan ketika ada kebutuhan untuk mengelola dan memperbarui state seperti dalam formulir, animasi, dll.|
|Kelas Terkait|StatelessWidget|StatefulWidget|
|Contoh Widget Built-in|Text, Icon, Image|Checkbox, TextField, AnimatedContainer|
</li> <br>

<li>Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing! <br>
  <ul>
    <li><b>MyHomePage (StatelessWidget)</b>: Widget utama yang mewakili halaman beranda aplikasi. Widget ini akan menampilkan semua item dan memiliki tampilan yang dapat digulir.</li>
    <li><b>Scaffold</b>: Widget yang menyediakan kerangka dasar untuk halaman aplikasi. Ini termasuk AppBar, body, dan berbagai elemen UI lainnya.</li>
    <li><b>AppBar</b>: Widget yang digunakan untuk menampilkan bar atas aplikasi, yang mencakup judul dan latar belakang warna (backgroundColor).</li>
    <li><b>Icon</b>: Widget yang digunakan untuk menampilkan ikon yang sesuai dengan setiap item dalam kartu. Ikon ini diambil dari properti item.icon dan ditampilkan dengan ukuran dan warna yang sesuai.</li>
    <li><b>Text</b>: Widget yang digunakan untuk menampilkan teks yang sesuai dengan nama item. Teks ini diambil dari properti item.name dan ditampilkan dengan gaya teks yang sesuai.</li>
    <li><b>SingleChildScrollView</b>: Widget yang digunakan untuk membuat tampilan yang dapat digulir. Ini membungkus konten halaman agar dapat digulir jika terlalu panjang.</li>
    <li><b>Padding</b>: Widget yang digunakan untuk menambahkan jarak (padding) di sekitar kontennya. Dalam kasus ini, itu digunakan untuk memberikan jarak dari tepi halaman.</li>
    <li><b>Column</b>: Widget layout yang digunakan untuk menampilkan child widgets secara vertikal. Ini digunakan untuk mengatur tampilan beranda Anda.</li>
    <li><b>GridView.count</b>: Widget yang digunakan untuk membuat tata letak grid dengan jumlah kolom yang diberikan. Dalam kode ini, digunakan untuk menampilkan item dalam grid.</li>
    <li><b>ShopCard (StatelessWidget)</b>: Widget yang digunakan untuk membuat kartu yang akan menampilkan setiap item. Ini berisi ikon, teks, dan warna latar belakang yang sesuai.</li>
    <li><b>Material</b>: Widget yang memberikan tampilan Material Design ke kontennya. Ini digunakan di dalam ShopCard untuk memberikan warna latar belakang.</li>
    <li><b>InkWell</b>: Widget yang digunakan untuk membuat area responsif terhadap sentuhan. Dalam kasus ini, itu digunakan untuk mendeteksi ketika item diklik.</li>
    <li><b>SnackBar</b>: Widget yang digunakan untuk menampilkan pesan kilat ketika item diklik.</li>
    <li><b>MyApp (StatelessWidget)</b>: Widget utama yang digunakan untuk menginisialisasi aplikasi. Ini mengatur tema dan menentukan halaman beranda.</li>
    <li><b>MaterialApp</b>: Widget yang digunakan untuk mengkonfigurasi dan menampilkan aplikasi Flutter. Ini menyediakan berbagai pengaturan, termasuk tema dan halaman beranda.</li>
  </ul>
</li>
<br>
<li>Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial) <br>
  <ul>
    <li>Buat project flutter baru dan beri nama hmbtn_inventory dengan cara menjalankan kode <code>flutter create hmbtn_inventory; cd shopping_list</code> di terminal</li>
    <li>Buat file baru dan beri nama <code>menu.dart</code> pada folder <code>hmbtn_inventory/lib</code> lalu isi dengan kode berikut:

    import 'package:flutter/material.dart';
    
    class Item {
      final String name;
      final IconData icon;
      final Color color;
    
      Item(this.name, this.icon, this.color);
    }
    
    class MyHomePage extends StatelessWidget {
      MyHomePage({Key? key}) : super(key: key);
    
      final List<Item> items = [
        Item("Lihat Item", Icons.checklist, Colors.indigo.shade200),
        Item("Tambah Item", Icons.add_shopping_cart, Colors.indigo),
        Item("Logout", Icons.logout, Colors.indigo.shade900),
      ];
    
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            backgroundColor: Colors.indigo,
            title: const Text(
              'Inventory',
              style: TextStyle(color: Colors.white),
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
                      'Harvest Moon: Back to Nature Inventory', // Text yang menandakan toko
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
                    children: items.map((Item item) {
                      // Iterasi untuk setiap item
                      return ShopCard(item);
                    }).toList(),
                  ),
                ],
              ),
            ),
          ),
        );
      }
    }
    
    class ShopCard extends StatelessWidget {
      final Item item;
    
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

</li>
    <li>Kode tersebut sudah mengimplementasikan membuat tiga tombol sederhana dengan ikon dan teks menggunakan bantuan class tambahan yaitu Item.</li>
    <li>Untuk menampilkan snackbar, disini menggunakan widget InkWell yang mana dia responsive terhadap sentuhan sehingga kita dapat membuat jika dia ditekan maka akan memunculkan SnackBar tergantung dari item yang ditekan.</li>
    <li>Kemudian, ubah kode yang ada di <code>main.dart</code> menjadi:
      
      import 'package:flutter/material.dart';
      import 'package:hmbtn_inventory/menu.dart';
      
      void main() {
        runApp(const MyApp());
      }
      
      class MyApp extends StatelessWidget {
        const MyApp({super.key});
      
        @override
        Widget build(BuildContext context) {
          return MaterialApp(
            title: 'Home Page',
            theme: ThemeData(
              colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo),
              useMaterial3: true,
            ),
            home: MyHomePage(),
          );
        }
      }
      
</li>
    <li>Maka ketika dirun flutternya akan berfungsi dengan baik</li>
  </ul>
</li>
</ol>

# References
<ol>
  <li><a href="https://www.geeksforgeeks.org/flutter-stateful-vs-stateless-widgets/" style="text-decoration:none;">Flutter - Stateful vs Stateless Widgets</a></li>
  <li><a href="https://docs.flutter.dev/ui/widgets" style="text-decoration:none;">Widget Catalog</a></li>
</ol>
</details>

