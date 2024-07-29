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
     




