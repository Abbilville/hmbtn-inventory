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
<li>Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial) <br>
  <ul>
    <li></li>
  </ul>
</li>
</ol>
---
# References
1. [Flutter - Stateful vs Stateless Widgets](https://www.geeksforgeeks.org/flutter-stateful-vs-stateless-widgets/ "GeeksforGeeks")
2. [Widget Catalog](https://docs.flutter.dev/ui/widgets "Flutter")
</details>

