# JS-summary
Repo untuk rangkuman materi Javascript dari berbagai sumber yg saya pelajari. jika saya lupa sesuatu terkait JS, saya hanya perlu membaca rangkuman ini untuk mengingatnya dengan cepat.

# Intro
JavaScript adalah bahasa pemrograman yg digunakan untuk memanipulasi element HTML dan membuat interaksi pada web. JavaScript menambahkan aspek “pemrograman” ke dalam HTML dan CSS. JavaScript dijalankan di sisi client. Ini artinya, untuk menjalankan JavaScript kita hanya butuh 2 aplikasi, yakni text editor dan web browser. Seiring dengan perkembangan JavaScript yang sangat pesat, saat ini JavaScript tidak hanya berjalan di client, tapi juga bisa berjalan di server (seperti PHP). Contoh penerapan JavaScript di server ini adalah node.js

Ketika belajar penerapan JavaScript sebagai client side programming, maka kita akan mempelajari 2 hal. JavaScript dan DOM (Document Object Model). JavaScript adalah bahasa pemrograman, sedangkan DOM adalah teknologi web yg memperlakukan dokumen html atau xml sebagai diagram pohon, dimana tiap simpulnya (node) adalah objek. Melalui objek ini lah kita bisa memanfaatkan JavaScript untuk memanipulasi elemen HTML.

# Sejarah dan Perkembangan JS
Sejak HTML diciptakan oleh Tim Berners-lee, banyak yg berlomba-lomba menciptakan aplikasi untuk menampilkan HTML (web browser). Saat itu kebanyakan web browser masih berbasis teks seperti MS-DOS. NCSA Mosaic menjadi browser grafis pertama dan terpopuler. Kemudian ada Mosaic Netscape, berganti jadi Netscape Navigator. Perusahaan yg menciptakan netscape navigator (netscape communications) menyadari bahwa web seharusnya bisa lebih dinamis, hidup dan interaktif. HTML butuh sebuah bahasa pemrograman tambahan untuk mampu membangun web yg dinamis. Singkat cerita netscape communications merekrut orang untuk membuat bahasa pemrograman tersebut. Hasilnya lahirlah Mocha > LiveScript > JavaScript (1995).

Microsoft tidak mau kalah, dia menciptakan bahasa pemrograman juga diberi nama JScript dan VBScript. Korban dari persaingan ini adalah web programmer. Supaya permasalahan JScript vs JavaScript tidak berlarut-larut, Netscape berinisiatif mengajukan sebuah standar mengenai bahasa pemrograman client side ini. Tujuannya agar JScript dan JavaScript mengikuti sebuah aturan yang baku. Harapannya web programmer tidak lagi dipusingkan terkait perbedaan implementasi JavaScript dari IE dengan Netscape. Netscape memilih badan standarisi ECMA International sebagai pihak yang akan mengembangkan bahasa pemrograman ini (1997).

**Tahun 1999 perkembangan EcmaScript sudah sampai versi ke 4 (ES4).** Kemudian tidak ada perkembangan apapun selama 10 tahun hingga 2009. Untungnya sekitar tahun 2005, kelompok Open Source dan komunitas programmer mencoba membuat sebuah revolusi untuk JavaScript. Hasilnya lahir lah berbagai fitur, teknologi dan library baru pada JavaScript seperti AJAX, Prototype, jQuery, Dojo Toolkit, dan MooTools.

**EcmaScript 5 (Desember 2009),** beberapa fitur baru: strict mode, accessors, dan JSON.  
**EcmaScript 6 (Juni 2015),** beberapa fitur baru: iterator baru, python-style generator, arrow function, binary data, typed arrays, collections (maps, sets and weak maps), promises untuk membuat asynchronous programming, penambahan function untuk tipe data number dan math, reflection, serta proxies (metaprogramming untuk virtual objects dan wrappers)  
**EcmaScript 7 (Juni 2016),** beberapa fitur baru: exponentiation operator (**) dan Array.prototype.includes.  

# Menjalankan Kode Program JavaScript
1. Tools: text editor dan web browser  
   Gunakan text editor khusus pemrograman seperti komodo edit atau VS Code daripada text editor bawaan Windows (Notepad) atau MacOS (TextEdit) karena memiliki fitur seperti     code completion dan inline error correction.  

   Web browser digunakan untuk menjalankan/memproses kode javascript. karena di dalam web browser, terdapat EcmaScript Engine yg berperan sebagai compiler untuk kode            javascript.  

2. Syntax (aturan penulisan) javascript
   - case sensitif (huruf kecil dan huruf besar dianggap berbeda)

3. Cara Menginput JavaScript ke dalam HTML  
   Karena sekarang kita sedang mempelajari penerapan javascript dari sisi client, jadi jika ingin menjalankan kode javascript kita harus menyisipkan javascript ke dalam         HTML. ini bisa dilakukan dengan 3 cara yaitu internal, eksternal dan inline  
   - inline  
     inline JavaScript artinya menempatkan kode JavaScript secara langsung ke dalam atribut tag HTML. Berikut contoh dari inline JavaScript:
     ```javascript
     <button onclick="alert('Sedang Belajar JavaScript');">
       Click me!
     </button>
     ```
   - internal  
     kode JavaScript ditulis di dalam tag `<script>`
     ```html
     <!DOCTYPE html>
     <html>
       <head>
         <meta charset="utf-8">
         <title> Belajar JavaScript </title>
         <script>
           // kode javascript disini
         </script>
       </head>
       <body>
         <h1>Belajar JavaScript</h1>
         <button> Click me! </button>
       </body>
     </html>
     ```
   - eksternal  
     membuat file khusus yang hanya berisi kode program JavaScript. File ini nantinya “dipanggil” oleh halaman HTML yang membutuhkan. Untuk memasukkan file JavaScript             kodeku.js ke dalam HTML, kita menggunakan atribut src dari tag `<script>`. Silahkan buat file HTML dengan kode berikut:
     ```html
     <!DOCTYPE html>
     <html>
       <head>
         <meta charset="utf-8">
         <title> Belajar JavaScript </title>
       </head>
       <body>
         <h1>Belajar JavaScript</h1>
         <script src="kodeku.js"></script>
       </body>
     </html>
     ```
   > Untuk web yang sebenarnya, External JavaScript merupakan metode input yang paling disarankan
   > 
   > Pertanyaan berikutnya, dimanakah sebaiknya kode JavaScript ini diletakkan? Apakah di bagian `<head>`, di awal tag `<body>`, atau tepat sebelum tag penutup `</body>`.
   > 
   > Lokasi penempatan ini dipengaruhi oleh 2 aspek: **performa** dan **eksekusi**.  
   > berkaitan dengan eksekusi, web browser menampilkan sebuah halaman web, yakni secara berurutan dari atas ke bawah, mulai dari baris pertama hingga baris terakhir.
   > 
   > Untuk website yang kompleks, file external JavaScript mungkin bukan hanya 1, tapi bisa 3 file, 9 file atau lebih. Biasanya, kode JavaScript ditempatkan di bagian atas,       yakni di dalam tag `<head>`. Jika seluruh file ini diletakkan di bagian `<head>`, bisa saja halaman web tampil “kosong” selama beberapa detik menunggu web browser            selesai mendownload file-file tersebut. Situasi ini dikenal dengan istilah Render-Blocking JavaScript. Solusi dari masalah ini adalah dengan memanggil file external          JavaScript dari bagian bawah tag `<body>`. Dengan demikian, kita memberi kesempatan web browser untuk memproses kode HTML terlebih dahulu, baru kemudian mendownload          file JavaScript. Efeknya, pengujung web bisa langsung melihat tampilan web selama proses ini, tidak hanya halaman kosong.
   > 
   > karena itu, berkaitan dengan masalah performa, beberapa developer web menyarankan meletakkan JavaScript dibagian bawah tag `<body>`, yakni sebelum tag penutup                `</body>`. Tapi ada pengecualian, jika terdapat kode yang harus dijalankan terlebih dahulu (seperti library jQuery), tempatkan di dalam tag `<head>`, agar bisa               langsung dieksekusi.

   Untungnya HTML5 hadir sebagai penyelamat. Dengan atribut **async** dan **defer**, kita bisa mengatur kapan (defer) dan bagaimana (async) file external JavaScript             diproses. Kedua atribut ini memungkinkan penulisan tag `<script>` tidak harus di bawah tag `<body>`.

   Tambahan atribut async dan defer dari HTML5 membawa perubahan terkait posisi terbaik peletakan kode JavaScript. Standar saat ini adalah menempatkan kode JavaScript di        bagian `<head>` dengan tambahan atribut async. Untuk kode JavaScript yang tidak terlalu penting (dan bisa menunggu), tambahkan atribut defer.

#  Aturan Dasar Penulisan (Syntax)
**statement**, sebutan untuk sebuah baris perintah JavaScript (biasanya diakhiri tanda titik koma)  

**case sensitive**, huruf kapital dan huruf biasa dianggap berbeda  

**whitespace**, berarti karakter “kosong” seperti spasi, tab, atau baris baru (new line) diabaikan dalam JS. Indenting (Penambahan karakter whitespace)  ini memang akan memperbesar ukuran file JavaScript. Tapi keuntungannya jauh lebih banyak. Kode program kita menjadi lebih mudah dibaca.  

**komentar**, kode program yang tidak akan dieksekusi oleh JavaScript. biasanya digunakan untuk membuat dokumentasi atau penjelasan tentang kode program yang ada. atau menonaktifkan beberapa baris kode program (biasanya untuk keperluan debugging).  
contoh:
```javascript
<script>
   // Ambil setiap element, simpan ke variabel
   var pesan = document.getElementById("pesan");
   var username = document.getElementById("username");
   
   // Buat regex untuk inputan minimal 6 karakter (digit dan angka)
   var pattern = /^[A-Za-z0-9]{6,}$/;
   
   /* Buat fungsi untuk mengecek username.
   Fungsi ini dibuat menggunakan regular expression */
   submit.onclick = function () {
      if (pattern.test(username.value)) {
         pesan.innerHTML = "Username sesuai";
         pesan.className= "betul"; // Artinya username sudah sesuai
      }
   };
</script>
```

# Variabel dan Konstanta
Saat menulis kode program, sering kali kita perlu mengelola data masukan (input) dan menghasilkan data baru (output). Agar dapat diproses, data disimpan ke dalam **variabel** atau **konstanta**.  

contoh:  

```javascript
var namaPanggilan; // deklarasi variabel
namaPanggilan = "loki"; // assignment: mengisi variabel dengan sebuah nilai menggunakan operator assignment

// inisialisasi variabel: deklarasi variabel dengan langsung memberi nilai awal
var namaPanggilan = "loki";

// cara baru membuat variabel di ES6
let namaLengkap = "Dwiky Loki";
const PI = 3.14;
```

- variabel dan konstanta = penampung data
- identifier (penamaan). contoh yg termasuk identifier: variabel, konstanta, function dan object.
- literal, sebuah nilai yg biasanya dimasukkan ke dalam identifier. ada string literal, numeric literal.
- karena variabel dan konstanta termasuk identifier, maka harus mengikuti aturan pembuatan identifier.
   - Bisa terdiri dari huruf, angka, garis bawah “ _ ” (underscore), dan tanda dollar “ $ “ (dollar sign). Selain itu, dianggap sebagai karakter ilegal (tidak boleh              digunakan)
   - Karakter pertama dari identifier tidak boleh berupa angka. Angka hanya bisa digunakan sebagai karakter kedua dan seterusnya.
   - Bersifat case sensitive, dimana huruf besar dan kecil dianggap berbeda.
   - Harus selain dari reserved keyword, yakni kata khusus yang berfungsi sebagai perintah di dalam pemrograman JavaScript, seperti var, while, function, dll
   ```javascript
   // Berikut contoh penulisan variabel yang salah:
   let 9naga; // diawali dengan angka
   let satu-satu; // terdapat karakter "-"
   let satu satu; // terdapat spasi
   let satu%lima; // terdapat karakter "%"
   let continue; // merupakan reserved keyword

   // Berikut contoh penulisan variabel yang benar:
   let aa123;
   let belajar_bahasa_javascript;
   let jumlahTotal;
   let $box;
   let _begin;
   ```
- standar pendeklarasian variabel dan konstanta saat ini menggunakan keyword `let` dan `const` bukan keyword `var` (fitur baru ES6)
- Sedapat mungkin selalu menambahkan keyword let saat membuat variabel. karena jika tidak, bisa mendatangkan bug yg tdk disangka-sangka. Secara teknis, juga ada perbedaan     mendasar berkaitan dengan variabel scope
- Berbeda dengan variabel yang menggunakan Camel Case, konstanta biasa ditulis menggunakan huruf besar dan garis bawah (underscore) sebagai pemisah kata. Tujuannya agar       mudah dibedakan dengan variabel. Aturan ini hanya kebiasaan programmer JavaScript. Tentu saja tetap bisa membuat konstanta dengan huruf kecil
  
# Tipe Data
Kalo sebelumnya kita belajar bahwa Variabel dan konstanta sebagai wadah untuk menampung data. Dalam JS, data itu sendiri terdiri dari beragam jenis, mulai dari angka, teks, hingga data yang kompleks seperti array dan object.

Agar memudahkan pemrosesan, JavaScript membedakan data menurut sifatnya atau dikenal sebagai tipe data. Secara garis besar, tipe data dalam JavaScript terdiri dari 2 kelompok, yakni **tipe data primitif (primitive type)** dan **tipe data object.**

## Tipe Data Primitive
Tipe data primitif disebut demikian karena tipe data ini “sederhana”. Di dalam JavaScript terdapat 6 tipe data primitif:
1. Number  
   Tipe data number adalah tipe data yang berisikan angka, baik itu angka bulat seperti 1, 5, 1000, -99, maupun angka pecahan seperti 1.55, 3.14, 0.0009. Di dalam              JavaScript, angka bulat dan pecahan digabung ke dalam tipe data number.

   Selain angka “normal”, JavaScript juga mendukung berbagai penulisan angka seperti scientific notation, bilangan desimal, biner, oktal, dan Heksadesimal.
   
   > bilangan biner, oktal dan heksadesimal sangat jarang digunakan di dalam web programming.  

   Selain “angka”, JavaScript memiliki 2 nilai yang termasuk tipe data number, yakni NaN dan Infinity. Kedua nilai ini hadir untuk menampung hasil matematika yang “tidak       umum”, seperti contoh berikut:
    
    ```javascript
   let foo;
    
   foo = 9 * "a";
   console.log(foo); // NaN
    
   foo = 9 / "a";
   console.log(foo); // NaN
    
   foo = 5 / 0;
   console.log(foo); // Infinity
    
   foo = -5 / 0;
   console.log(foo); // -Infinity
   ```
2. String
   Tipe data string adalah sebutan untuk data yang berisi teks. selain teks biasa, ada juga escape character, unicode character, template string
3. Boolean
   Tipe data Boolean adalah tipe data yang hanya mempunyai dua nilai, yakni true (benar) atau false (salah). Tipe data boolean sering digunakan untuk membuat alur logika       program (control flow).
4. Null dan Undifined
   Menyebut null dan undefined sebagai tipe data terasa kurang pas, karena kedua tipe data ini menyatakan “data yang tidak ada”. Null berarti "kosong" sementara undifined 
   menyatakan data yang tidak terdefinisi
5. Symbol* (ES6)  
> operator typeof
>
> operator typeof sangat erat dengan pembahasan tentang tipe data. Operator typeof digunakan untuk melihat tipe data dari sebuah variabel. Berikut contoh penggunaan           operator typeof:
> ```javascript
> let foo;
> console.log (typeof foo); // undefined
>
> foo = 199;
> console.log (typeof foo); // number
>
> foo = "Belajar JavaScript";
> console.log (typeof foo); // string
>
> foo = false;
> console.log (typeof foo); // boolean
>
> foo = null;
> console.log (typeof foo); // object
> ```
> Yang agak aneh, nilai null dianggap sebagai object. Ini memang sebuah pengecualian di dalam JavaScript.

## Tipe data Object
Object bisa disebut sebagai tipe data “khusus” yang prilaku dan isinya bermacam-macam. Adapun tipe data object bawaan JavaScript adalah:
1. Array  
   Array (dalam bahasa indonesia disebut juga sebagai larik) adalah tipe data yang berisi kumpulan tipe data lain.
   ```javascript
   // cara membuat array
   let siswa = ["Andri", "Joko", "Sukma", "Rina", "Sari"];

   // akses elemen array menggunakan nomor indeks yg dimulai dari 0
   console.log(siswa[0]); // Andri
   console.log(siswa[1]); // Joko
   console.log(siswa[2]); // Sukma
   console.log(siswa[3]); // Rina
   console.log(siswa[4]); // Sari

   // mengubah nilai elemen array

   ```
3. Date
4. RegExp
5. Map dan WeakMap* (ES6)
6. Set dan WeakSet* (ES6)








