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

   // Anggota dari array juga bisa bercampur dengan tipe data lain
   let baz = ["aku", 999, true, 0.085, null];
   console.log(baz); // Array [ "aku", 999, true, 0.085, null ]


   // akses elemen array menggunakan nomor indeks yg dimulai dari 0
   console.log(siswa[0]); // Andri
   console.log(siswa[1]); // Joko
   console.log(siswa[2]); // Sukma
   console.log(siswa[3]); // Rina
   console.log(siswa[4]); // Sari

   // mengubah nilai elemen array
   siswa[0] = "Dwiky";
   console.log(siswa) // array ["Dwiky", "Joko", "Sukma", "Rina", "Sari"]

   // array 2 dimensi
   let foo = [
               ["sedang","belajar","javascript"],
               ["selamat","pagi","dunia"],
               ["a","b","c","d","e"]
   ];
   console.log(foo[1][2]); // "dunia"
   console.log(foo[2][2]); // "c"

   foo[1][1] = "malam";
   console.log(foo[1]); // Array [ "selamat", "malam", "dunia" ]

   foo[2][5] = "f";
   foo[2][6] = "g";
   console.log(foo[2]); // Array [ "a", "b", "c", "d", "e", "f", "g" ]
   ```
   Tipe data array merupakan salah satu tipe data terpenting di dalam JavaScript. Saat masuk ke pembahasan tentang DOM, mayoritas element di dalam web browser                  diakses menggunakan array.
3. Date
4. RegExp
5. Map dan WeakMap* (ES6)
6. Set dan WeakSet* (ES6)

# Operator Javascript
Operator digunakan untuk memproses data yang sudah diinput ke dalam JavaScript.   
1. Operator Aritmatika
   ```javascript
   let foo;

   foo = +100;
   console.log(foo); // 100

   foo = -22;
   console.log(foo); // -22

   foo = 30 - 5;
   console.log(foo); // 30

   foo = 3.33 + 9.02;
   console.log(foo); // 12.35

   foo = 9 * 7;
   console.log(foo); // 63

   foo = 6 + 8 / 2 + 6;
   console.log(foo); // 16

   foo = 30 % 7;
   console.log(foo); // 2
   ```
   Urutan ‘kekuatan’ operator juga pengaruh di sini. Operator perkalian dan pembagian lebih kuat daripada operator penambahan dan pengurangan. Untuk menimpa urutan ini,        kita bisa menggunakan tanda kurung.
2. Operator Increment dan Decrement  
   Operator increment adalah sebutan untuk penulisan seperti i++. Perintah ini digunakan untuk menaikkan nilai variabel i sebanyak 1 angka. Perintah i++ adalah penulisan       singkat dari i = i + 1.

   Sedangkan operator decrement adalah sebutan untuk penulisan seperti i--. Fungsinya untuk menurunkan nilai variabel i sebesar 1 angka. Perintah i-- merupakan penulisan       singkat dari i = i - 1.

   Posisi peletakan tanda ++ dan -- bisa diawal maupun diakhir variabel, seperti ++i maupun i++. Keduanya berfungsi sama tapi dengan cara eksekusi yang sedikit berbeda.
   ```javascript
   let foo;

   foo = 7;
   console.log(++foo); // 8
   console.log(foo); // 8

   foo = 7;
   console.log(foo++); // 7
   console.log(foo); // 8

   foo = 7;
   console.log(--foo); // 6
   console.log(foo); // 6

   foo = 7;
   console.log(foo--); // 7
   console.log(foo); // 6
   ```
   Operator increment dan decrement ini sering digunakan untuk control structures perulangan.
3. Operator Perbandingan  
   Operator perbandingan berfungsi untuk memeriksa bagaimana hubungan sebuah nilai dengan nilai lain, apakah sama besar, tidak sama, lebih besar atau lebih kecil. Hasil        akhir dari perbandingan ini berupa tipe data boolean: true (benar) atau false (salah). Operator perbandingan banyak digunakan untuk membuat control flow pada kode           program, contohnya seperti conditional statements dan loops.

   Operator perbandingan terdiri dari: sama dengan (==), identik dengan (===), tidak sama dengan (!=), tidak identik dengan (!==), kurang dari (<), lebih dari (>), kurang      dari atau sama dengan (<=), lebih dari atau sama dengan (>=)

   Pada oprator perbandingan, prioritaskan menggunakan operator identik dengan (===) daripada sama dengan (==).

   **FALSY DAN TRUTHY VALUE**  
   Ketika nilai non-boolean digunakan dalam konteks boolean, seperti menggunakan operator perbandingan, kondisi pernyataan if, dan loops, nilai tersebut akan dipaksa           menjadi true atau false.

   Berikut daftar falsy value di dalam JavaScript:  
   • false  
   • null  
   • undefined  
   • 0  
   • NaN  
   • '' (string kosong)  
   • "" (string kosong)  
   
   Selain nilai-nilai diatas, akan di konversi menjadi truthy value, termasuk:  
   • true  
   • { } (object kosong)  
   • [ ] (array kosong)  
   • 42 (sembarang angka, termasuk angka negatif dan pecahan, selain angka 0)  
   • "foo" (sembarang string, selama bukan string kosong)  
   • infinity (termasuk -infinity)  
4. Operator Logika  
   Operator logika digunakan untuk membandingkan 2 kondisi logika, yakni logika benar (true) dan logika salah (false). Operator logika terdiri dari  
   • && (and)  
   • || (or)  
   • ! (not)  
   Operator && memiliki kekuatan yang lebih tinggi daripada ||. Untuk operasi logika, JavaScript menjalankan perintah tersebut dari kiri ke kanan, kecuali jika terdapat        operator && dan || dalam 1 operasi (operator && akan dijalankan terlebih dahulu).

   **KONSEP SHORT-CIRCUIT EVALUATION**  
   Ketika memproses operasi logika yang cukup panjang, JavaScript mengunakan konsep shortcircuit evaluation. Maksudnya, jika dengan memeriksa 1 nilai saja hasil operasi        tersebut sudah bisa diketahui, nilai - nilai lain tidak akan diperiksa.
   ```javascript
   let foo;

   // proses berjalan hanya sampai "true ||" krn dapat dipastikan apapun nilai setelah operator ||, hasil operasinya akan "true" 
   foo = true || false || true;
   console.log(foo); // true

   // demikian juga dengan operasi berikut
   foo = false && true && true;
   console.log(foo); // false
   ```
   Fitur short-circuit evaluation ini cukup penting dipahami karena sering digunakan dalam kode program lanjutan, misalnya dalam contoh berikut:
   ```javascript
   // fungsi alert() baru akan berjalan jika variabel bar bernilai true.
   let bar = false;
   let foo = bar && alert("Hello Indonesia");

   // karena JavaScript mendeteksi variabel bar bernilai true, sedangkan operatornya adalah &&.
   // Short-circuit tidak terjadi karena JavaScript harus memeriksa nilai berikutnya.
   // hasilnya fungsi alert dijalankan
   let bar = true;
   let foo = bar && alert("Hello Indonesia");
   ```
   Fitur short-circuit evaluation untuk operator logika ini juga sering digunakan ketika membuat trik khusus, dimana tipe data yang dibandingkan bukan boolean.
   
   **OPERASI LOGIKA NON BOOLEAN**  
   Salah satu fitur unik di dalam JavaScript adalah, jika operasi logika dijalankan untuk data non boolean, hasil akhir dari operasi ini juga bukan berupa boolean, tapi        nilai terakhir dari pemrosesan tersebut.
   ```javascript
   let foo = "Duniailkom" || "JavaScript";
   console.log(foo); // Duniailkom
   
   let foo = "Duniailkom" && "JavaScript";
   console.log(foo); // JavaScript
   
   let foo = true || "JavaScript";
   console.log(foo); // true
   
   let foo = false || "JavaScript";
   console.log(foo); // JavaScript
   
   let foo = "JavaScript" && false;
   console.log(foo); // false
   
   let foo = false && "JavaScript";
   console.log(foo); // false
   
   let foo = false || false && true || "JavaScript";
   console.log(foo); // JavaScript
   
   let foo = true || false && true || "JavaScript";
   console.log(foo); // true
   ```
   Konsep operasi logika non boolean di JavaScript ini sangat unik dan jarang ditemukan dalam bahasa pemrograman lain.
6. Operator String  
   Dalam JavaScript terdapat 1 operator yang digunakan untuk penyambungan string (string concatenation). Operator ini menggunakan karakter tambah ( + ). Jika data yang akan    disambung bukan bertipe string, akan dikonversi menjadi string secara otomatis.

   Operator + harus digunakan jika kita ingin menyambung string dengan sebuah variabel.

   Dengan fitur template string dari ECMAScript 6, kita bisa menulis semuanya di dalam string (menggabung string dan variabel dalam satu penulisan).
   
   **PENYAMBUNGAN STRING ATAU PENAMBAHAN ANGKA**  
   Di dalam JavaScript, operator penyambungan string dan penambahan angka (aritmatika) samasama menggunakan tanda tambah ( + ). Namun operator string lebih didahulukan.
   ```javascript
   let foo;
   
   foo = 10 + 10 + 9;
   console.log(foo); // 29
   
   foo = '10' + 10 + 9;
   console.log(foo); // 10109
   
   foo = 10 + '10' + 9;
   console.log(foo); // 10109
   
   foo = 10 + 10 + '9';
   console.log(foo); // 209
   ```
7. Operator Bitwise
8. Operator Assignment
   Operator assignment adalah operator yang digunakan untuk memasukkan nilai ke dalam sebuah variabel.
9. Operator Spread (ES6)
   Operator ini digunakan untuk berbagai keperluan yang berhubungan dengan array, salah satunya untuk menggabungkan array. Spread operator menggunakan tanda titik tiga         kali (…), kemudian diikuti dengan nama variabel.

   Selain untuk menggabungkan array, spread operator ini juga bisa digunakan untuk berbagai hal lain, misalnya di dalam function.

***Beberapa tipe data dalam javascript memiliki operator khusus, sesuai dengan ciri khasnya masing-masing.***  

Seperti, Tipe data number biasanya digunakan bersamaan dengan operator aritmatika. Tipe data string biasanya digunakan dengan operator string concatenation (penyambungan string), dst. Yang perlu menjadi perhatian, di dalam JavaScript sebuah tipe data akan berubah menjadi tipe data lain tergantung operator yang digunakan. Berikut daftar tipe data dan operatornya masing-masing:
| Tipe Data  | Operator |
| ---------- | -------- |
| Number     | Aritmatika |
| String     | string concatenation |
| Boolean    | perbandingan & logika |

# Struktur Logika dan Perulangan
Control flow in programming is the order in which a program's instructions are executed, and how a program moves from one statement to another. 

Control flow is guided by control structures, such as:
- Conditional statements: Use conditions like "if," "else if," and "else" to execute specific code blocks based on whether a condition is true or false.
- Loops: Repeat code until a condition is met.
- Function or method calls: Organize and reuse code.
 
By default, code in a program runs sequentially from top to bottom, one line at a time. However, control structures can divert this flow. Pada bab ini kita akan mempelajari salah 2 control structures pada javascript yaitu conditional statements dan loops (struktur logika dan perulangan).

## Conditional statements
Use conditions like "if," "else if," and "else" to execute specific code blocks based on whether a condition is true or false.
```javascript
let username = 22.3;

if (typeof username === "string") {
   console.log("Username string");
}
else if (typeof username === "number") {
   console.log("Username angka");
}
else {
   console.log("Username bukan string dan angka");
}

// nested if
let foo = 7;
console.log("nilai foo = "+ foo);

if (typeof foo === "number") {
   console.log("foo bertipe number");
   if (foo >= 10) {
      console.log("nilai foo besar dari 10");
   } else {
      console.log("nilai foo kecil dari 10");
   }
} else if (typeof foo === "string") {
   console.log("foo bertipe string");
} else {
   console.log("foo bukan bertipe number maupun string");
}

// switch case
let situs = "twitter";

switch (situs) {
   case "google":
      console.log('<a href="http://www.google.com">Situs Google<a>');
      break;
   case "facebook":
      console.log('<a href="http://www.facebook.com">Situs Facebook<a>');
      break;
   case "twitter":
      console.log('<a href="http://www.twitter.com">Situs Twitter<a>');
      break;
   case "duniailkom":
      console.log('<a href="http://www.duniailkom.com">Situs Duniailkom<a>');
      break;
   default:
      console.log("Situs tidak terdaftar");
}
```
Secara garis besar, setiap kode program yang dibuat dengan switch bisa dikonversi menjadi if else. Tapi sebaliknya belum tentu. Struktur switch hanya cocok untuk kondisi sederhana seperti mengecek apakah nilai variabel sama dengan string tertentu. Jika kondisi yang diperiksa sudah gabungan, misalnya menggunakan operator && atau ||, kita tidak bisa lagi menggunakan switch. Ini pula yang menjadi alasan struktur if lebih banyak digunakan daripada switch.

### Operator Conditional
JavaScript memiliki 1 operator conditional yang mirip seperti struktur if else.  
```javascript
let jumlah_barang = 1000;
let total;

if (jumlah_barang > 500) {
   total = jumlah_barang * 100;
} else {
   total = jumlah_barang * 150;
}

console.log(total); // 100000

// Jika menggunakan operator conditional, kode program diatas bisa diubah menjadi seperti ini:
let jumlah_barang = 501;
let total;

total = jumlah_barang > 500? jumlah_barang * 100 : jumlah_barang * 150;

console.log(total); // 100000
```
Operator conditional mempersingkat penulisan if else, namun seperti yang anda lihat, perlu dipahami dengan seksama.

## Loops
Perulangan atau dalam bahasa inggris disebut sebagai loop, adalah struktur kode program yang digunakan untuk mengulang beberapa baris perintah. Dengan menggunakan perulangan, sangat memudahkan kita menjalankan perintah yang sama secara terus menerus. 

Di dalam JavaScript terdapat 3 buah struktur perulangan, yakni for, while, dan do while. Kita akan mulai dari perulangan for terlebih dahulu.

### For
```javascript
// kode berikut akan menampilkan teks "haloooo dwiky" pada menu console sebanyak 10 kali
for (let i = 0; i < 10; i++) {
   console.log("haloooo dwiky");
}

// atau bisa juga seperti ini
for (let i = 1; i <= 10; i++) {
   console.log("haloooo dwiky");
}

// bagian start dan increment bisa dipindahkan di tempat lain
// penulisan seperti ini boleh dan valid, tapi memang jarang digunakan.
let i = 0;

for (; i < 10;) {
   console.log("haloooo dwiky");
   i++;
}
``` 
**PERULANGAN BERSARANG (NESTED LOOP)**  
Struktur seperti ini diperlukan untuk kode program yang cukup kompleks. Karena kompleksitasnya inilah ***sering dijadikan soal-soal latihan programming***.
```javascript
for (let i = 1; i <= 4; i++) {
   for (let j = 1; j <= 2; j++) {
      console.log("variabel i bernilai: "+ i +", variabel j bernilai: "+j);
   }
}
```
***Nested loop*** ini relatif jarang digunakan, tapi bukan tidak mungkin anda akan menemui masalah yang hanya bisa diselesaikan menggunakan nested loop.

**INFINITY LOOP**  
Infinity loop adalah perulangan yang berjalan terus menerus dan tidak akan pernah selesai. Ini biasanya terjadi karena kesalahan dari kita, programmer yang membuat kode program.
```javascript
// perulangan akan terus berjalan karena kondisi i > 10 selalu bernilai true
for (let i = 20; i > 10; i++) {
   console.log("Hello Indonesia");
}

// bagian increment harus diperbaiki agar loopingnya memiliki stopping condition
for (let i = 20; i > 10; i--) {
   console.log("Hello Indonesia");
}
```
**PERINTAH BREAK DAN CONTINUE**  
Perintah ***break*** dan ***continue*** digunakan untuk menghentikan sebuah perulangan sebelum waktunya, atau dengan kata lain perulangan berhenti secara prematur.
```javascript
// perulangan berhenti saat i = 5. yg tereksekusi hanya i = 1 hingga 4
for (var i = 1; i <= 10; i++) {
   if (i === 5) {
      break;
   }
   console.log("Hello JavaScript " + i);
}

// perulangan i = 5 diskip, kemudian perulangan kembali dieksekusi sampai selesai
for (var i = 1; i <= 10; i++) {
   if (i === 5) {
      continue;
   }
   console.log("Hello JavaScript " + i);
}
```
### while  
Pada prisipnya, perulangan while cocok digunakan untuk situasi dimana kita tidak tau berapa banyak perulangan yang mesti dijalankan. Strukturnya kurang lebih seperti perulangan for. Perulangan ini biasanya digunakan untuk proses menampilkan data yang digenerate secara dinamis. Misalnya kita membuat program yang mengambil suatu data dari situs facebook (menggunakan API - Application Programming Interface). Kita tidak tau berapa banyak baris tabel yang ingin diambil. Dalam situasi seperti ini, perulangan while bisa digunakan, dan tidak bisa menggunakan perulangan for (dulunya. sebelum ada ES6). 
```javascript
let foo = true;

while (foo) {
   statement;
   if (condition) {
      foo = false;
   }
}
```
Disini saya memiliki variabel foo yang berfungsi sebagai penentu perulangan. Variabel foo ini biasa disebut sebagai flag (bahasa inggris: bendera), karena jalan atau tidaknya perulangan bergantung kepada foo apakah berisi true atau false. Pada awal kode program, foo diisi true. Perulangan langsung berjalan karena saya tidak membuat kondisi apapun, tapi langsung menulis while (foo). Sekilas tampak akan terjadi infinity loop, karena kondisi while (true) akan selalu terpenuhi. Akan tetapi dalam kode program terdapat kondisi if:
```javascript
if (condition) {
   foo = false;
}
```
Jika condition untuk if ini terpenuhi, kita ubah nilai flag foo menjadi false, sehingga perulangan akan berhenti.

Secara umum, setiap perulangan for bisa dikonversi menjadi perulangan while, tapi tidak sebaliknya. sehingga perulangan for lebih sering digunakan.
### do while  
Perulangan do while sangat mirip seperti perulangan while. Bedanya, dalam perulangan do while, kondisi di cek diakhir block perulangan.
```javascript
let i = 1;

do {
   console.log("Hello Indonesia");
   i++;
} while (i <= 10);
```
Konsekuensi dari pengecekan yang dilakukan di akhir adalah, block perulangan setidaknya akan diproses 1 kali, walaupun kondisi tersebut sudah tidak dipenuhi sejak awal. Dalam prakteknya, Kita mungkin bakal jarang menemukan aplikasi dari do while. Kita akan banyak menggunakan perulangan for dan while.

---
### Menampilkan Element Array Dengan Perulangan.
Salah satu penggunaan terbanyak dari perulangan adalah untuk menampilkan element array.
```javascript
let siswa = ["Andri", "Joko", "Sukma", "Rina", "Sari"];
let jumlah_siswa = siswa.length;

console.log ("Jumlah siswa = " + jumlah_siswa);

// Menampilkan element array menggunakan perulangan for biasa
for (let i = 0; i < jumlah_siswa; i++){
   console.log(siswa[i]);
}

// Menampilkan element array menggunakan perulangan for of (ES6)
for (let i of siswa) {
   console.log(i);
}

/* jika menggunakan "for of" kita tidak memiliki cara untuk mengakses nilai index dari array tersebut.
Jika anda butuh mengakses index array, terpaksa menggunakan perulangan for biasa */
```

# Function
A function in JavaScript is **a reusable block of code that performs a specific task.** You define it once, and then you can run (or “call”) it whenever you need that task done in your program. In JavaScript, functions are first-class objects, because they can be passed to other functions, returned from functions, and assigned to variables and properties. 

> A programming language is said to have First-class functions when functions in that language are treated like any other variable. For example, in such a language, a function can be passed as an argument to other functions, can be returned by another function and can be assigned as a value to a variable.

```javascript
// format dasar pembuatan function
function function_name (argument1, argument2,...) {
   statement;
   statement;
   return value;
}
```

Argument adalah variabel yang berfungsi sebagai nilai input ke dalam function. Perintah return digunakan sebagai output function. Penulisan argument dan perintah return bersifat opsional dan boleh tidak ditulis.

## Membuat dan Memanggil Function
```javascript
// function declaration
function pagi(){
   console.log("Selamat Pagi");
   console.log("Good Morning");
   console.log("Ohayou Gozaimasu");
   console.log("Buenos Dias");
}

// memanggil/menjalankan function
/*Menjalankan fungsi dengan cara seperti ini dikenal dengan istilah
memanggil fungsi (calling a function). Istilah lain adalah running,
executing, invoking, atau dispatching a function.*/
pagi();
```

## Mengembalikan Nilai Function
```javascript
function pagi(){
   return "Selamat Pagi";
}

// cara lain
function pagi(){
 return "Selamat Pagi";
}

let salam = pagi();
console.log(salam); // "Selamat Pagi"

// atau bisa juga begini
function pagi(){
   return "Selamat Pagi";
}

console.log(pagi());
```

Selain mengembalikan nilai, efek lain dari perintah return adalah, akan langsung menghentikan function tersebut, seperti contoh berikut:
```javascript
function pagi(){
   return "Selamat Pagi";
   console.log ("Good Morning"); // tidak akan pernah di eksekusi
}

console.log(pagi()); // "Selamat Pagi"
```

kita juga bisa mengembalikan nilai dalam bentuk variabel
```javascript
function pagi(){
   let salam = "Selamat Pagi";
   return salam;
}

console.log(pagi()); // "Selamat Pagi"
```

Salah satu aturan dari perintah return adalah, kita hanya boleh mengembalikan 1 nilai saja, apakah itu 1 string, maupun 1 variabel. Jadi, bagaimana jika nilai yang dikembalikan ada banyak? ***Kita bisa memanfaatkan array***
```javascript
function pagi(){
   let salamPagi = ["Selamat Pagi", "Good Morning", "Ohayou Gozaimasu", "Buenos Dias" ];
   return salamPagi;
}

let salam = pagi();
console.log(salam);
// Array [ "Selamat Pagi", "Good Morning", "Ohayou Gozaimasu", "Buenos Dias" ]
```

## Argument Function
Fitur berikutnya dari function adalah argument, yakni mengirim satu atau beberapa nilai ke dalam function untuk diproses.
```javascript
function pagi(siapa){
   return "Selamat Pagi " + siapa;
}

console.log(pagi("Jakarta")); // Selamat Pagi Jakarta
console.log(pagi("Bandung")); // Selamat Pagi Bandung
console.log(pagi("Makassar")); // Selamat Pagi Makassar
```

JavaScript tidak membatasi berapa banyak argument yang bisa dikirim, selama nilai tersebut sesuai dengan banyaknya input yang diberikan. jika sebuah function butuh 3 argument sementara hanya menginput 2, nilai argument ke 3 secara default bernilai "undefined". jika sebuah function butuh 3 argument sementara kita memanggil lebih banyak argument dari yg dibutuhkan seperti 4, 5 dan seterusnya, nilai argument yg lain akan diskip.

Argument function mirip seperti variabel, tapi kita tidak perlu menulis keyword var.










