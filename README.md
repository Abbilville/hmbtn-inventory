# Harvest Moon: Back to Nature Supermarket
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

<details>
<summary>Pertanyaan untuk Tugas 8</summary>
<ol>
  <li>Jelaskan perbedaan antara <code>Navigator.push()</code> dan <code>Navigator.pushReplacement()</code>, disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!</li>
  <ul>
    <li><code>Navigator.push()</code> digunakan jika kita ingin ganti halaman dan jika back maka akan kembali ke halaman sebelumnya, biasanya dipakai ketika sedang di home dan ingin pergi ke halaman lihat keranjang, maka kita bisa kembali ke home lagi jika menekan back.</li>
    <li><code>Navigator.pushReplacement()</code> digunakan jika kita ingin ganti halaman baru dan tidak bisa kembali ke halaman sebelumnya, biasanya dipakai di bagian login, maka jika sudah selesai login kita pushReplacement ke home sehingga tidak bisa back lagi ke halaman login.</li>
    <li>Berikut contoh gambar penggunaan <code>Navigator.push()</code> dan <code>Navigator.pushReplacement()</code> yang saya ambil dari web technicalfeeder.</li>
    <img src="https://www.technicalfeeder.com/images/page-transition-stack2.drawio.png?ezimgfmt=ng:webp/ngcb1"> <br>
  </ul>
  
  <li>Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!</li>
    <ul>
      <li><b>Single-child Layout Widgets</b></li>
          Widget yang hanya dapat memiliki satu anak (child). Widget ini digunakan ketika hanya perlu menempatkan satu widget dalam satu tempat. Widget ini terdiri atas: Align, AspectRatio, Baseline, Center, ConstrainedBox, Container, CustomSingleChildLayout, Expanded, FittedBox, FractionallySizedBox, IntrinsicHeight, IntrinsicWidth, LimitedBox, Offstage, OverflowBox, Padding, SizedBox, SizedOverflowBox, dan Transform. Widget yang sering digunakan adalah Container yaitu sebagai wadah suatu widget lainnya.
      <li><b>Multi-child Layout Widgets</b></li>
          Widget yang dapat memiliki lebih dari satu anak (children). Widget ini digunakan ketika perlu menempatkan banyak widget dalam satu tempat. Widget ini terdiri atas: Column, CustomMultiChildLayout, Flow, GridView, IndexedStack, LayouyBuilder, ListBody, ListView, Row, Stack, Table, dan Wrap. Widget yang paling sering digunakan adalah Row yaitu untuk menaruh widget secara horizontal dan Column untuk menaruh widget secara vertikal.
      <li><b>Sliver Widgets</b></li>
          Widget yang digunakan untuk scrollable area, digunakan jika ingin membuat widget lain dapat di-scroll agar menciptakan fitur yang dinamis. Widget ini terdiri atas: CupertinoSliverNavigationBar, CustomScrollView, SliverAppBar, SliverChildBuilderDelegate, SliverChildListDelegate, SliverFixedExtentList, SliverGrid, SliverList, SliverPadding, SliverPersistentHeader, dan SliverToBoxAdapter.
    </ul>
  <li>Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!</li>
      Elemen input yang digunakan untuk tugas kali ini hanyalah <code>TextFormField</code>. Penggunaan TextFormField dapat memastikan bahwa pengguna dapat memasukkan data dengan mudah dan dapat memvalidasi atau memastikan bahwa data yang dimasukkan sesuai dengan format yang diharapkan. Selain itu, Widget ini juga digunakan agar terintegrasi dengan widget parentnya yaitu <code>Form</code>.
  <li>Bagaimana penerapan clean architecture pada aplikasi Flutter?</li>
      Tugas ini menggunakan prinsip <i>clean architecture</i> pada pengembangan Flutter dengan mengelompokkan file berdasarkan fungsionalitasnya masing-masing. Sebagai contoh, folder "screens" berisi file yang mendefinisikan tampilan layar dan folder "widgets" berisi file yang mengimplementasikan widget yang dapat digunakan di berbagai layar. Pengelompokan ini merupakan bentuk dari <i>refactoring file</i> dalam konteks <i>clean architecture</i>.
  <li>Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)</li>
    <ul>
      <li>Membuat satu halaman baru pada aplikasi, yaitu halaman formulir tambah item baru dan memakai empat elemen input, yaitu name, price, amount, dan description. Kemudian form tersebut harus memiliki tombol save serta inputnya harus divalidasi sesuai dengan tipe datanya serta input tidak boleh kosong. <br>
        di dalam <code>screens/shoplist_form.dart</code>:
        
        import 'package:flutter/material.dart';
        import 'package:hmbtn_supermarket/widgets/left_drawer.dart';
        import 'package:hmbtn_supermarket/widgets/item_card.dart';
        import 'package:hmbtn_supermarket/screens/menu.dart';
        
        List<Item> cart = [];
        
        class ShopFormPage extends StatefulWidget {
          const ShopFormPage({super.key});
        
          @override
          State<ShopFormPage> createState() => _ShopFormPageState();
        }
        
        class _ShopFormPageState extends State<ShopFormPage> {
          final _formKey = GlobalKey<FormState>();
          String _name = "";
          int _price = 0;
          int _amount = 0;
          String _description = "";
        
          @override
          Widget build(BuildContext context) {
            return Scaffold(
              ...
              child: TextFormField(
                decoration: InputDecoration(
                  hintText: "Nama Item",
                  labelText: "Nama Item",
                  border: OutlineInputBorder(
                    borderRadius: BorderRadius.circular(5.0),
                  ),
                ),
                onChanged: (String? value) {
                  setState(() {
                    _name = value!;
                  });
                },
                validator: (String? value) {
                  if (value == null || value.isEmpty) {
                    return "Nama tidak boleh kosong!";
                  }
                  return null;
                },
              ),
            ),
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: TextFormField(
                decoration: InputDecoration(
                  hintText: "Harga",
                  labelText: "Harga",
                  border: OutlineInputBorder(
                    borderRadius: BorderRadius.circular(5.0),
                  ),
                ),
                onChanged: (String? value) {
                  setState(() {
                    _price = int.parse(value!);
                  });
                },
                validator: (String? value) {
                  if (value == null || value.isEmpty) {
                    return "Harga tidak boleh kosong!";
                  }
                  if (int.tryParse(value) == null) {
                    return "Harga harus berupa angka!";
                  }
                  return null;
                },
              ),
            ),
            ... (input yang lainnya)

            (save button)
            Align(
              ...
                  actions: [
                    TextButton(
                      child: const Text('OK'),
                      onPressed: () {
                        Navigator.pop(context);
                      },
                    ),
                  ],
                );
              },
            );
            _formKey.currentState!.reset();
          }
        },
        child: const Text(
          "Save",
          style: TextStyle(color: Colors.white),
            ...
</li>
      <li>Mengarahkan pengguna ke halaman form tambah item baru ketika menekan tombol Tambah Item pada halaman utama. Ini dapat dilakukan dengan mengubah kode pada file <code>shop_card.dart</code> seperti ini:

      import 'package:hmbtn_supermarket/screens/shoplist_form.dart';

      ...
      // Navigate ke route yang sesuai (tergantung jenis tombol)
          if (item.name == "Tambah Item") {
            Navigator.push(
                context,
                MaterialPageRoute(
                  builder: (context) => const ShopFormPage(),
                ));
          }
        
</li>
      <li>Memunculkan data sesuai isi dari formulir yang diisi dalam sebuah pop-up setelah menekan tombol Save pada halaman formulir tambah item baru. Hal ini dapat dilakukan dengan menambahkan code di save button ketika tombol tersebut ditekan maka akan menampilan widget AlertDialog yang akan memunculkan data dari input yang sudah di isi seperti ini:

      ...
      if (_formKey.currentState!.validate()) {
        cart.add(Item(_name, _price, _amount, _description));
        showDialog(
          context: context,
          builder: (context) {
            return AlertDialog(
              title: const Text('Item berhasil tersimpan'),
              content: SingleChildScrollView(
                child: Column(
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    Text('Nama: $_name'),
                    Text('Harga: $_price'),
                    Text('Jumlah: $_amount'),
                    Text('Deskripsi: $_description'),
                  ],
                ),
              ),
        ...
</li>
      <li>Membuat drawer yang memiliki tombol untuk mengarahkan ke halaman utama dan menambahkan item. Membuat file dengan nama <code>left_drawer.dart</code> dan taruh di folder widgets sebab drawer dapat digunakan berkali-kali. <br>
      di dalam <code>widgets/left_drawer.dart</code>
      import 'package:flutter/material.dart';
      import 'package:hmbtn_supermarket/screens/menu.dart';
      import 'package:hmbtn_supermarket/screens/shoplist_form.dart';
      import 'package:hmbtn_supermarket/screens/shoplist_cart.dart';
      
      class LeftDrawer extends StatelessWidget {
        const LeftDrawer({super.key});
      
        @override
        Widget build(BuildContext context) {
          return Drawer(
              ...
              ListTile(
                leading: const Icon(Icons.home_outlined),
                title: const Text('Halaman Utama'),
                // Bagian redirection ke MyHomePage
                onTap: () {
                  Navigator.pushReplacement(
                      context,
                      MaterialPageRoute(
                        builder: (context) => MyHomePage(),
                      ));
                },
              ),
              ListTile(
                leading: const Icon(Icons.add_shopping_cart),
                title: const Text('Tambah Item'),
                // Bagian redirection ke ShopFormPage
                onTap: () {
                  Navigator.pushReplacement(
                      context,
                      MaterialPageRoute(
                        builder: (context) => const ShopFormPage(),
                      ));
                },
              ...
</li>
        <br>Cara mengimplementasikannya hanya dengan menambahkan drawer: const LeftDrawer(); seperti ini:
        
        import 'package:hmbtn_supermarket/widgets/left_drawer.dart';
        ...
        Widget build(BuildContext context) {
          return Scaffold(
            appBar: AppBar(
              ...
            drawer: const LeftDrawer(),
</ol>

# References
<ol>
  <li><a href="https://www.technicalfeeder.com/2021/11/flutter-page-transition/">Flutter Page Transition</a></li>
  <li><a href="https://docs.flutter.dev/ui/widgets/layout">Layout Widgets</a></li>
</ol>
</details>

<details>
<summary>Pertanyaan untuk Tugas 9</summary>
<ol>
  <li>Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?</li>
  Kita bisa melakukan pengambilan data JSON tanpa membuat model terlebih dahulu. Hal ini sering disebut sebagai "parsing JSON dynamically" di mana kita mengambil data JSON dan mengakses nilainya langsung dari data yang dihasilkan oleh fungsi jsonDecode. Kelebihannya adalah jika kita hanya membutuhkan beberapa bagian data atau hanya data sementara hal ini dapat dilakukan dengan cepat. <br>
  <li>Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.</li>
  <code>CookieRequest</code> dalam Flutter atau pengembangan aplikasi web biasanya merujuk pada permintaan HTTP yang melibatkan pengelolaan cookie. Ini merupakan objek yang digunakan untuk memodifikasi, mengelola, atau menambahkan informasi cookie ke permintaan HTTP yang akan dikirim ke server. Ketika instance CookieRequest dibagikan ke berbagai komponen dalam aplikasi Flutter, hal itu biasa dilakukan untuk pengelolaan autentikasi dan sesi pengguna. Jika suatu aplikasi membutuhkan autentikasi pengguna atau menggunakan sesi, <code> CookieRequest</code> bisa mengelola cookies yang diperlukan untuk mengidentifikasi pengguna yang masuk. Memiliki instance yang dibagikan memastikan bahwa setiap komponen dalam aplikasi menggunakan logika yang sama dalam penanganan cookies autentikasi.
  <li>Jelaskan mekanisme pengambilan data dari JSON hingga dapat ditampilkan pada Flutter.</li>
  <ul>
    <li>Mengambil data dari server. Pada tugas ini contohnya, Saya mem-parse data json yang ada pada aplikasi deployment web Saya sebelumnya.</li>
    <li>Melakukan decode sehingga hasil parsenya menjadi bentuk json<br>
    <code>var data = jsonDecode(utf8.decode(response.bodyBytes));</code></li>
    <li>Konversikan data json tersebut menjadi object yang sudah kita buat modelnya sebelumnya</li>
    <li>Terakhir, untuk menampilkan datanya di Flutter, kita dapat menggunakan widget yang sudah ada di Flutter yaitu FutureBuilder dengan futurenya adalah ketiga step di atas dan buildernya untuk menampilkan datanya. Widget ini sangat berguna ketika ingin menampilkan data dari operasi asinkron seperti mengambil data dari server atau melakukan perhitungan yang memerlukan waktu.</li>
  </ul>
  <li>Jelaskan mekanisme autentikasi dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.</li>
  <ul>
    <li>Input data username dan password</li>
    <li>Melakukan request autentikasi ke Django dengan menggunakan CookieRequest</li>
    <li>Django akan memproses permintaan dari Flutter</li>
    <li>Jika informasi yang diberikan oleh pengguna benar, Django akan menghasilkan token autentikasi atau membuat sesi untuk pengguna tersebut. Token atau sesi ini nantinya akan digunakan untuk mengidentifikasi pengguna yang telah terautentikasi</li>
    <li>Django mengirimkan response kembali ke Flutter. Response ini mungkin berisi token atau informasi lain yang menandakan keberhasilan atau kegagalan autentikasi</li>
  </ul>
  <li>Sebutkan seluruh widget yang kamu pakai pada tugas ini dan jelaskan fungsinya masing-masing.</li>
  <ul>
    <li>Pada file <code>login.dart</code></li>
    <ul>
      <li>LoginPage (Stateless Widget), untuk menampilkan halaman login</li>
      <li>SizedBox, untuk membuat box yang ukurannya fixed</li>
    </ul>
    <li>Pada file <code>list_item.dart</code></li>
    <ul>
      <li>ItemPage (Stateless Widget), untuk menampilkan halaman kumpulan item</li>
      <li>ItemDetailsPage (Stateless Widget), untuk menampilkan halaman detail item</li>
      <li>FutureBuilder, untuk menampilkan data dari operasi asinkron seperti mengambil data dari server atau melakukan perhitungan yang memerlukan waktu</li>
      <li>ListView.builder, untuk menampilkan daftar item secara dinamis berdasarkan sumber data yang bersifat berulang, seperti list atau array</li>
      <li>Expanded, widget agar mengexpand childnya sampai batasnya</li>
    </ul>
  </ul>
  <li>Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).</li>
  <ul>
    <li>Membuat app baru pada aplikasi django sebelumnya dan beri nama <code>authentication</code> serta tambahkan kode ini di <code>views.py</code> dan jangan lupa untuk routing ke <code>urls.py</code>

    from django.shortcuts import render
    from django.contrib.auth import authenticate, login as auth_login
    from django.http import JsonResponse
    from django.views.decorators.csrf import csrf_exempt
    from django.contrib.auth import logout as auth_logout

    @csrf_exempt
    def login(request):
        username = request.POST['username']
        password = request.POST['password']
        user = authenticate(username=username, password=password)
        if user is not None:
            if user.is_active:
                auth_login(request, user)
                # Status login sukses.
                return JsonResponse({
                    "username": user.username,
                    "status": True,
                    "message": "Login sukses!"
                    # Tambahkan data lainnya jika ingin mengirim data ke Flutter.
                }, status=200)
            else:
                return JsonResponse({
                    "status": False,
                    "message": "Login gagal, akun dinonaktifkan."
                }, status=401)

        else:
            return JsonResponse({
                "status": False,
                "message": "Login gagal, periksa kembali email atau kata sandi."
            }, status=401)
        
    @csrf_exempt
    def logout(request):
        username = request.user.username

        try:
            auth_logout(request)
            return JsonResponse({
                "username": username,
                "status": True,
                "message": "Logout berhasil!"
            }, status=200)
        except:
            return JsonResponse({
            "status": False,
            "message": "Logout gagal."
            }, status=401)
</li>
<br>
    <li>Tambahkan juga fungsi untuk create item tapi dari flutter di <code>main/views.py</code> seperti ini

    ...
    @csrf_exempt
    def create_item_flutter(request):
        if request.method == 'POST':
            
            data = json.loads(request.body)

            new_item = Item.objects.create(
                user = request.user,
                name = data["name"],
                price = int(data["price"]),
                amount = int(data["amount"]),
                description = data["description"],
                category = data["category"]
            )

            new_item.save()

            return JsonResponse({"status": "success"}, status=200)
        else:
            return JsonResponse({"status": "error"}, status=401)
</li>
    <li>Selanjutkan integrasikan autentikasi yang pada Flutter ke aplikasi django yang sudah kita tambahkan fitur untuk autentikasinya barusan. Buat file baru yaitu <code>lib/screens/login.dart</code> dan isi dengan kode ini

    import 'package:hmbtn_supermarket/screens/menu.dart';
    import 'package:flutter/material.dart';
    import 'package:pbp_django_auth/pbp_django_auth.dart';
    import 'package:provider/provider.dart';

    void main() {
      runApp(const LoginApp());
    }

    class LoginApp extends StatelessWidget {
      const LoginApp({super.key});

      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: 'Login',
          theme: ThemeData(
            primarySwatch: Colors.blue,
          ),
          home: const LoginPage(),
        );
      }
    }

    class LoginPage extends StatefulWidget {
      const LoginPage({super.key});

      @override
      // ignore: library_private_types_in_public_api
      _LoginPageState createState() => _LoginPageState();
    }

    class _LoginPageState extends State<LoginPage> {
      final TextEditingController _usernameController = TextEditingController();
      final TextEditingController _passwordController = TextEditingController();

      @override
      Widget build(BuildContext context) {
        final request = context.watch<CookieRequest>();
        return Scaffold(
          appBar: AppBar(
            title: const Text('Login'),
          ),
          body: Container(
            padding: const EdgeInsets.all(16.0),
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                TextField(
                  controller: _usernameController,
                  decoration: const InputDecoration(
                    labelText: 'Username',
                  ),
                ),
                const SizedBox(height: 12.0),
                TextField(
                  controller: _passwordController,
                  decoration: const InputDecoration(
                    labelText: 'Password',
                  ),
                  obscureText: true,
                ),
                const SizedBox(height: 24.0),
                ElevatedButton(
                  onPressed: () async {
                    String username = _usernameController.text;
                    String password = _passwordController.text;

                    // Cek kredensial
                    // Untuk menyambungkan Android emulator dengan Django pada localhost,
                    // gunakan URL http://10.0.2.2/
                    final response =
                        await request.login("https://abbilhaidar-farras-tugas.pbp.cs.ui.ac.id/auth/login/", {
                      'username': username,
                      'password': password,
                    });

                    if (request.loggedIn) {
                      String message = response['message'];
                      String uname = response['username'];
                      // ignore: use_build_context_synchronously
                      Navigator.pushReplacement(
                        context,
                        MaterialPageRoute(builder: (context) => MyHomePage()),
                      );
                      // ignore: use_build_context_synchronously
                      ScaffoldMessenger.of(context)
                        ..hideCurrentSnackBar()
                        ..showSnackBar(SnackBar(
                            content: Text("$message Selamat datang, $uname.")));
                    } else {
                      // ignore: use_build_context_synchronously
                      showDialog(
                        context: context,
                        builder: (context) => AlertDialog(
                          title: const Text('Login Gagal'),
                          content: Text(response['message']),
                          actions: [
                            TextButton(
                              child: const Text('OK'),
                              onPressed: () {
                                Navigator.pop(context);
                              },
                            ),
                          ],
                        ),
                      );
                    }
                  },
                  child: const Text('Login'),
                ),
              ],
            ),
          ),
        );
      }
    }
</li>
    <li>Selanjutnya pada <code>lib/main.dart</code> ubah kodenya menjadi seperti ini:

    import 'package:flutter/material.dart';
    import 'package:hmbtn_supermarket/screens/login.dart';
    import 'package:pbp_django_auth/pbp_django_auth.dart';
    import 'package:provider/provider.dart';

    void main() {
      runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
      const MyApp({super.key});

      // This widget is the root of your application.
      @override
      Widget build(BuildContext context) {
        return Provider(
            create: (_) {
              CookieRequest request = CookieRequest();
              return request;
            },
            child: MaterialApp(
              title: 'Home Page',
              theme: ThemeData(
                colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo),
                useMaterial3: true,
              ),
              home: const LoginPage(),
            ));
      }
    }
</li>
    <li>buat folder baru yaitu <code>models</code> dan buat 2 file dart di dalamnya yaitu <code>item.dart</code> dan <code>list_item.dart</code> isi dengan ini:

    item.dart:
    import 'dart:convert';

    List<Item> itemFromJson(String str) => List<Item>.from(json.decode(str).map((x) => Item.fromJson(x)));

    String itemToJson(List<Item> data) => json.encode(List<dynamic>.from(data.map((x) => x.toJson())));

    class Item {
        String model;
        int pk;
        Fields fields;

        Item({
            required this.model,
            required this.pk,
            required this.fields,
        });

        factory Item.fromJson(Map<String, dynamic> json) => Item(
            model: json["model"],
            pk: json["pk"],
            fields: Fields.fromJson(json["fields"]),
        );

        Map<String, dynamic> toJson() => {
            "model": model,
            "pk": pk,
            "fields": fields.toJson(),
        };
    }

    class Fields {
        int user;
        String name;
        int amount;
        String description;
        int price;
        String category;

        Fields({
            required this.user,
            required this.name,
            required this.amount,
            required this.description,
            required this.price,
            required this.category,
        });

        factory Fields.fromJson(Map<String, dynamic> json) => Fields(
            user: json["user"],
            name: json["name"],
            amount: json["amount"],
            description: json["description"],
            price: json["price"],
            category: json["category"],
        );

        Map<String, dynamic> toJson() => {
            "user": user,
            "name": name,
            "amount": amount,
            "description": description,
            "price": price,
            "category": category,
        };
    }

    list_item.dart
    import 'package:flutter/material.dart';
    import 'package:http/http.dart' as http;
    import 'dart:convert';
    import 'package:hmbtn_supermarket/models/item.dart';
    import 'package:hmbtn_supermarket/widgets/left_drawer.dart';

    class ItemPage extends StatefulWidget {
      const ItemPage({Key? key}) : super(key: key);

      @override
      // ignore: library_private_types_in_public_api
      _ItemPageState createState() => _ItemPageState();
    }

    class _ItemPageState extends State<ItemPage> {
      Future<List<Item>> fetchProduct() async {
        var url = Uri.parse('https://abbilhaidar-farras-tugas.pbp.cs.ui.ac.id/json/');
        var response = await http.get(
          url,
          headers: {"Content-Type": "application/json"},
        );

        // melakukan decode response menjadi bentuk json
        var data = jsonDecode(utf8.decode(response.bodyBytes));

        // melakukan konversi data json menjadi object Product
        List<Item> listItem = [];
        for (var d in data) {
          if (d != null) {
            listItem.add(Item.fromJson(d));
          }
        }
        return listItem;
      }

      void _showItemDetails(Item item) {
        Navigator.push(
          context,
          MaterialPageRoute(
            builder: (context) => ItemDetailsPage(item: item),
          ),
        );
      }

      @override
      Widget build(BuildContext context) {
        return Scaffold(
            appBar: AppBar(
              title: const Text('Items'),
            ),
            drawer: const LeftDrawer(),
            body: FutureBuilder(
                future: fetchProduct(),
                builder: (context, AsyncSnapshot snapshot) {
                  if (snapshot.data == null) {
                    return const Center(child: CircularProgressIndicator());
                  } else {
                    if (!snapshot.hasData) {
                      return const Column(
                        children: [
                          Text(
                            "Tidak ada data item.",
                            style:
                                TextStyle(color: Color(0xff59A5D8), fontSize: 20),
                          ),
                          SizedBox(height: 8),
                        ],
                      );
                    } else {
                      return ListView.builder(
                          itemCount: snapshot.data!.length,
                          itemBuilder: (_, index) => Container(
                                margin: const EdgeInsets.symmetric(
                                    horizontal: 16, vertical: 12),
                                padding: const EdgeInsets.all(20.0),
                                child: Column(
                                  mainAxisAlignment: MainAxisAlignment.start,
                                  crossAxisAlignment: CrossAxisAlignment.start,
                                  children: [
                                    InkWell(
                                      // Area responsive terhadap sentuhan
                                      onTap: () {
                                        _showItemDetails(snapshot.data![index]);
                                      },
                                      child: Container(
                                        margin: const EdgeInsets.all(8),
                                        padding: const EdgeInsets.all(12),
                                        decoration: BoxDecoration(
                                          color: Colors.white,
                                          borderRadius: BorderRadius.circular(8.0),
                                          boxShadow: [
                                            BoxShadow(
                                              color: Colors.grey.withOpacity(0.5),
                                              spreadRadius: 2,
                                              blurRadius: 4,
                                              offset: const Offset(0,
                                                  2), // changes position of shadow
                                            ),
                                          ],
                                        ),
                                        child: Center(
                                          child: Column(
                                            children: [
                                              Row(
                                                children: [
                                                  Expanded(
                                                    child: Container(
                                                      padding:
                                                          const EdgeInsets.all(5),
                                                      decoration: BoxDecoration(
                                                        color:
                                                            Colors.indigo.shade200,
                                                        borderRadius:
                                                            BorderRadius.circular(
                                                                4.0),
                                                      ),
                                                      child: Text(
                                                        "${snapshot.data![index].fields.name}",
                                                        textAlign: TextAlign.center,
                                                        style: const TextStyle(
                                                          color: Colors.white,
                                                          fontWeight:
                                                              FontWeight.bold,
                                                        ),
                                                        overflow:
                                                            TextOverflow.ellipsis,
                                                      ),
                                                    ),
                                                  ),
                                                ],
                                              ),
                                              Column(
                                                children: [
                                                  Text(
                                                    'Harga: ${snapshot.data![index].fields.price}G',
                                                    overflow: TextOverflow.ellipsis,
                                                  ),
                                                  Text(
                                                    'Jumlah: ${snapshot.data![index].fields.amount}',
                                                    overflow: TextOverflow.ellipsis,
                                                  ),
                                                  Text(
                                                    'Deskripsi: ${snapshot.data![index].fields.description}',
                                                    overflow: TextOverflow.ellipsis,
                                                  ),
                                                  Text(
                                                    'Kategori: ${snapshot.data![index].fields.category}',
                                                    overflow: TextOverflow.ellipsis,
                                                  ),
                                                ],
                                              ),
                                            ],
                                          ),
                                        ),
                                      ),
                                    ),
                                  ],
                                ),
                              ));
                    }
                  }
                }));
      }
    }

    class ItemDetailsPage extends StatelessWidget {
      final Item item;

      const ItemDetailsPage({Key? key, required this.item}) : super(key: key);

      @override
      Widget build(BuildContext context) {
        return Scaffold(
          appBar: AppBar(
            title: Text(item.fields.name),
          ),
          body: SingleChildScrollView(
            padding: const EdgeInsets.all(16.0),
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: [
                Text('Harga: ${item.fields.price}G'),
                Text('Jumlah: ${item.fields.amount}'),
                Text('Deskripsi: ${item.fields.description}'),
                Text('Kategori: ${item.fields.category}'),
                // Add more details as needed
              ],
            ),
          ),
        );
      }
    }
</li>
    <li>Lalu sekarang ubah kode pada <code>widget/shoplist_form.dart</code> yaitu pada bagian <code>onPressed()</code> seperti ini agar dapat membuat serta menyimpan item:

    onPressed: () async {
      cart.add(Item(_name, _price, _amount, _description, _category));
      if (_formKey.currentState!.validate()) {
        // Kirim ke Django dan tunggu respons
        final response = await request.postJson(
            "https://abbilhaidar-farras-tugas.pbp.cs.ui.ac.id/create-flutter/",
            jsonEncode(<String, String>{
              'name': _name,
              'price': _price.toString(),
              'amount': _amount.toString(),
              'description': _description,
              'category': _category,
            }));
        if (response['status'] == 'success') {
          ScaffoldMessenger.of(context)
              .showSnackBar(const SnackBar(
            content: Text("Produk baru berhasil disimpan!"),
          ));
          Navigator.pushReplacement(
            context,
            MaterialPageRoute(builder: (context) => MyHomePage()),
          );
        } else {
          ScaffoldMessenger.of(context)
              .showSnackBar(const SnackBar(
            content:
                Text("Terdapat kesalahan, silakan coba lagi."),
          ));
        }
      }
    },
</li>
  </ul>
</ol>

# References
</details>