**Praktikum 1: PHP Framework (Codeigniter)**

Tujuan
1. Mahasiswa mampu memahami konsep dasar Framework.
2. Mahasiswa mampu memahami konsep dasar MVC.
3. Mahasaswa mampu membuat program sederhana menggunakan Framework Codeigniter4.
Instruksi Praktikum
1. Persiapkan text editor misalnya VSCode.
2. Buat folder baru dengan nama lab11_php_ci pada docroot webserver (htdocs)
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.
   
**Langkah-langkah Praktikum**

**Persiapan**

Sebelum memulai menggunakan Framework Codeigniter, perlu dilakukan konfigurasi pada
webserver. Beberapa ekstensi PHP perlu diaktifkan untuk kebutuhan pengembangan
Codeigniter 4.

Berikut beberapa ekstensi yang perlu diaktifkan:

• php-json ekstension untuk bekerja dengan JSON;
• php-mysqlnd native driver untuk MySQL;
• php-xml ekstension untuk bekerja dengan XML;
• php-intl ekstensi untuk membuat aplikasi multibahasa;
• libcurl (opsional), jika ingin pakai Curl.

Untuk mengaktifkan ekstentsi tersebut, melalu XAMPP Control Panel, pada bagian Apache
klik Config -> PHP.ini

![image](https://github.com/user-attachments/assets/1471658a-10fc-4b95-99dd-0f099e9b368a)

Pada bagian extention, hilangkan tanda ; (titik koma) pada ekstensi yang akan diaktifkan.
Kemudian simpan kembali filenya dan restart Apache web server.

![image](https://github.com/user-attachments/assets/0ac26a31-fddf-4cb7-af96-1d27aa95ad8c)



Instalasi Codeigniter 4

Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara manual
dan menggunakan composer. Pada praktikum ini kita menggunakan cara manual.

• Unduh Codeigniter dari website https://codeigniter.com/download
• Extrak file zip Codeigniter ke direktori htdocs/lab11_ci.
• Ubah nama direktory framework-4.x.xx menjadi ci4.
• Buka browser dengan alamat http://localhost/lab11_ci/ci4/public/

![image](https://github.com/user-attachments/assets/4c0948b6-b6c8-4cc4-b1fd-5431877f9de3)


Menjalankan CLI (Command Line Interface)

Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk mengakses
CLI buka terminal/command prompt.

![image](https://github.com/user-attachments/assets/a5b8a71d-6798-49f4-80a0-dbb86f61db95)


Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat

(xampp/htdocs/lab11_php_ci/ci4/)
Perintah yang dapat dijalankan untuk memanggil CLI Codeigniter adalah:
php spark

![image](https://github.com/user-attachments/assets/7ff484af-a180-4eb2-9f89-fa0c17017509)


Mengaktifkan Mode Debugging

Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk mengetahui
pesan error apabila terjadi kesalahan dalam membuat kode program.
Secara default fitur ini belum aktif. Ketika terjadi error pada aplikasi akan ditampilkan pesan
kesalahan seperti berikut.

![image](https://github.com/user-attachments/assets/f48de0f6-8a1f-446a-b0e3-8e8228c994e3)


Semua jenis error akan ditampilkan sama. Untuk memudahkan mengetahui jenis errornya,
maka perlu diaktifkan mode debugging dengan mengubah nilai konfigurasi pada environment
variable CI_ENVIRINMENT menjadi development.

![image](https://github.com/user-attachments/assets/81ddb77e-157a-4c3e-a4a4-88fa541501ce)


Ubah nama file env menjadi .env kemudian buka file tersebut dan ubah nilai variable
CI_ENVIRONMENT menjadi development.

![image](https://github.com/user-attachments/assets/e4e7888b-1d4c-449c-8cff-d7946ba1ad8b)

Contoh error yang terjadi. Untuk mencoba error tersebut, ubah kode pada file
app/Controller/Home.php hilangkan titik koma pada akhir kode.

Struktur Direktori

Untuk lebih memahami Framework Codeigniter 4 perlu mengetahui struktur direktori dan file
yang ada.
Buka pada Windows Explorer atau dari Visual Studio Code -> Open Folder.
Terdapat beberapa direktori dan file yang perlu dipahami fungsi dan kegunaannya.

• .github folder ini kita butuhkan untuk konfigurasi repo github, seperti konfigurasi untuk
build dengan github action;

• app folder ini akan berisi kode dari aplikasi yang kita kembangkan;

• public folder ini berisi file yang bisa diakses oleh publik, seperti file index.php, robots.txt,
favicon.ico, ads.txt, dll;

• tests folder ini berisi kode untuk melakukan testing dengna PHPunit;

• vendor folder ini berisi library yang dibutuhkan oleh aplikasi, isinya juga termasuk kode
core dari system CI.

• writable folder ini berisi file yang ditulis oleh aplikasi. Nantinya, kita bisa pakai untuk
menyimpan file yang di-upload, logs, session, dll.

Sedangkan file-file yang berada pada root direktori CI sebagai berikut.
• .env adalah file yang berisi variabel environment yang dibutuhkan oleh aplikasi.

• .gitignore adalah file yang berisi daftar nama file dan folder yang akan diabaikan oleh Git.

• build adalah script untuk mengubah versi codeigniter yang digunakan. Ada versi release
(stabil) dan development (labil).

• composer.json adalah file JSON yang berisi informasi tentang proyek dan daftar library
yang dibutuhkannya. File ini digunakan oleh Composer sebagai acuan.

• composer.lock adalah file yang berisi informasi versi dari libraray yang digunakan aplikasi.
• license.txt adalah file yang berisi penjelasan tentang lisensi Codeigniter;

• phpunit.xml.dist adalah file XML yang berisi konfigurasi untuk PHPunit.

• README.md adalah file keterangan tentang codebase CI. Ini biasanya akan dibutuhkan
pada repo github atau gitlab.

• spark adalah program atau script yang berfungsi untuk menjalankan server, generate kode,
dll.

![image](https://github.com/user-attachments/assets/7e2cf65f-94e6-424c-819d-6a2f673deb69)


Fokus kita pada folder app, dimana folder tersebut adalah area kerja kita untuk membuat
aplikasi. Dan folder public untuk menyimpan aset web seperti css, gambar, javascript, dll.
Memahami Konsep MVC

Codeigniter menggunakan konsep MVC. 

MVC merupakan singkatan dari Model-View-Controller. 
MVC merupakan konsep arsitektur yang umum digunakan dalam pengembangan aplikasi.
Konsep MVC adalah memisahkan kode program berdasarkan logic proses, data, dan tampilan. 
Untuk logic proses diletakkan pada direktori Contoller, Objek data diletakkan pada
direktori Model, dan desain tampilan diletakkan pada direktori View.
Codeigniter menggunakan konsep pemrograman berorientasi objek dalam mengimplementasikan konsep MVC.

Model merupakan kode program yang berisi pemodelan data. 
Data dapat berupa database ataupun sumber lainnya.
View merupakan kode program yang berisi bagian yang menangani terkait tampilan user
interface sebuah aplikasi. didalam aplikasi web biasanya pasti akan berhubungan dengan html dan css.
Controller merupakaan kode program yang berkaitan dengan logic proses yang
menghubungkan antara view dan model.
Controller berfungsi untuk menerima request dan data
dari user kemudian diproses dengan menghubungkan bagian model dan view.

Routing dan Controller

Routing merupakan proses yang mengatur arah atau rute dari request untuk menentukan
fungsi/bagian mana yang akan memproses request tersebut. Pada framework CI4, routing
bertujuan untuk menentukan Controller mana yang harus merespon sebuah request. Controller
adalah class atau script yang bertanggung jawab merespon sebuah request.
Pada Codeigniter, request yang diterima oleh file index.php akan diarahkan ke Router untuk
meudian oleh router tesebut diarahkan ke Controller.
Router terletak pada file app/config/Routes.php

![image](https://github.com/user-attachments/assets/1e89abf4-820f-4ef2-82ba-654df3ce9041)


Pada file tersebut kita dapat mendefinisikan route untuk aplikasi yang kita buat.

Membuat Route Baru.

Tambahkan kode berikut di dalam Routes.php

![image](https://github.com/user-attachments/assets/233d69c5-35cf-4cde-8b02-c8146dab9bce)


Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan perintah
berikut.

![image](https://github.com/user-attachments/assets/237de081-fa83-48fe-b592-67a79059560f)


![image](https://github.com/user-attachments/assets/c282f8e0-65be-4a0d-8bf4-36a99b0eef4c)


Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url
http://localhost:8080/about

![image](https://github.com/user-attachments/assets/66c9c69f-bfa0-4f51-ab6f-4674284b4284)


Ketika diakses akan mucul tampilan error 404 file not found, itu artinya file/page tersebut tidak
ada. Untuk dapat mengakses halaman tersebut, harus dibuat terlebih dahulu Contoller yang
sesuai dengan routing yang dibuat yaitu Contoller Page.
Membuat Controller
Selanjutnya adalah membuat Controller Page. Buat file baru dengan nama page.php pada
direktori Controller kemudian isi kodenya seperti berikut.

![image](https://github.com/user-attachments/assets/0555dff0-6981-4c06-96d0-be8bfea15c8a)


Selanjutnya refresh Kembali browser, maka akan ditampilkan hasilnya yaotu halaman sudah
dapat diakses.

![image](https://github.com/user-attachments/assets/156444e3-ba8e-48b6-b0b7-398dcd7a3781)

Auto Routing
Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroute
dapat mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai true menjadi false.

![image](https://github.com/user-attachments/assets/cb52b1ae-dc90-4d72-81d6-291cb541d837)

Tambahkan method baru pada Controller Page seperti berikut.

![image](https://github.com/user-attachments/assets/d522985e-7adc-4543-88c8-4f196fd500e8)


Membuat View
Selanjutnya adalam membuat view untuk tampilan web agar lebih menarik. Buat file baru
dengan nama about.php pada direktori view (app/view/about.php) kemudian isi kodenya
seperti berikut.

![image](https://github.com/user-attachments/assets/63af2b16-728d-44b2-b005-424544d6ead8)


Ubah method about pada class Controller Page menjadi seperti berikut:

![image](https://github.com/user-attachments/assets/f2a5d768-5d8e-430f-beef-58d5e7421278)

Kemudian lakukan refresh pada halaman tersebut.

![image](https://github.com/user-attachments/assets/6891d6d3-d19f-4b3b-9679-5375cfbf3ba2)

Membuat Layout Web dengan CSS

Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada
codeigniter. Yang perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset css
dan javascript terletak pada direktori public.
Buat file css pada direktori public dengan nama style.css (copy file dari praktikum
lab4_layout. Kita akan gunakan layout yang pernah dibuat pada praktikum 4.

![image](https://github.com/user-attachments/assets/3f3ecd05-9395-423b-8833-be50dc0a3807)


Kemudian buat folder template pada direktori view kemudian buat file header.php dan
footer.php
File app/view/template/header.php

![image](https://github.com/user-attachments/assets/f088de18-4493-412c-be74-5297d75830d5)



File app/view/template/footer.php

![image](https://github.com/user-attachments/assets/bdafacd5-06a8-4ca4-b964-1c5c53df8a5a)


Kemudian ubah file app/view/about.php seperti berikut.

![image](https://github.com/user-attachments/assets/87a5c08e-5c30-4b35-aa18-797759a5aa52)


Selanjutnya refresh tampilan pada alamat http://localhost:8080/about

![image](https://github.com/user-attachments/assets/fb4c7ee1-fcda-4f27-8ff6-61843d9a5fe1)


**Pertanyaan dan Tugas**
Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga semua
link pada navigasi header dapat menampilkan tampilan dengan layout yang sama.

**Laporan Praktikum**
1. Buatlah repository baru dengan nama Lab7Web.
2. Kerjakan semua latihan yang diberikan sesuai urutannya.
3. Screenshot setiap perubahannya.
4. Buatlah file README.md dan tuliskan penjelasan dari setiap langkah praktikum beserta
screenshotnya.
5. Commit hasilnya pada repository masing-masing.
6. Kirim URL repository pada e-learning ecampus

---
---

**Praktikum 2: Framework Lanjutan (CRUD)**

Tujuan
1. Mahasiswa mampu memahami konsep dasar Model.
2. Mahasiswa mampu memahami konsep dasar CRUD.
3. Mahasaswa mampu membuat program sederhana menggunakan Framework Codeigniter4.
Instruksi Praktikum
1. Persiapkan text editor misalnya VSCode.
2. Buka kembali folder dengan nama lab7_php_ci pada docroot webserver (htdocs)
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.
Langkah-langkah Praktikum
Persiapan.
Untuk memulai membuat aplikasi CRUD sederhana, yang perlu disiapkan adalah database
server menggunakan MySQL. Pastikan MySQL Server sudah dapat dijalankan melalui
XAMPP.
Membuat Database: Studi Kasus Data Artikel
CREATE DATABASE lab_ci4;

![image](https://github.com/user-attachments/assets/ac5427bd-dece-45a7-b002-a80a89030ccd)


Konfigurasi koneksi database
Selanjutnya membuat konfigurasi untuk menghubungkan dengan database server. Konfigurasi
dapat dilakukan dengan du acara, yaitu pada file app/config/database.php atau menggunakan
file .env. Pada praktikum ini kita gunakan konfigurasi pada file .env.
 
![image](https://github.com/user-attachments/assets/d260fd01-ef10-4fae-9c15-a19d83faf166)


Membuat Model
Selanjutnya adalah membuat Model untuk memproses data Artikel. Buat file baru pada
direktori app/Models dengan nama ArtikelModel.php

![image](https://github.com/user-attachments/assets/1f660298-f298-443f-a8bb-539fe46fc020)


Membuat Controller
Buat Controller baru dengan nama Artikel.php pada direktori app/Controllers.

![image](https://github.com/user-attachments/assets/f625b8a5-baca-4558-8438-7f464523bbaf)


Membuat View
Buat direktori baru dengan nama artikel pada direktori app/views, kemudian buat file baru
dengan nama index.php.

![image](https://github.com/user-attachments/assets/c3c9b37d-cf83-4cfd-95f2-184a6400e936)


Selanjutnya buka browser kembali, dengan mengakses url http://localhost:8080/artikel

![image](https://github.com/user-attachments/assets/790b96f8-3d62-4aad-99b9-34f9e6d2bae3)


Belum ada data yang diampilkan. Kemudian coba tambahkan beberapa data pada database agar
dapat ditampilkan datanya.

![image](https://github.com/user-attachments/assets/d65b118d-7e7b-4593-a109-0d052376009d)


Refresh kembali browser, sehingga akan ditampilkan hasilnya.

![image](https://github.com/user-attachments/assets/8cca29ca-77cd-4c9d-bcc1-da914e521aa2)


Membuat Tampilan Detail Artikel
Tampilan pada saat judul berita di klik maka akan diarahkan ke halaman yang berbeda.
Tambahkan fungsi baru pada Controller Artikel dengan nama view().

![image](https://github.com/user-attachments/assets/763f1913-9b6a-49bd-b757-b81b49104203)


Membuat View Detail
Buat view baru untuk halaman detail dengan nama app/views/artikel/detail.php.

 ![image](https://github.com/user-attachments/assets/52d8a4ca-f40c-4673-9be2-014982564fcf)


Membuat Routing untuk artikel detail
Buka Kembali file app/config/Routes.php, kemudian tambahkan routing untuk artikel detail.
 
![image](https://github.com/user-attachments/assets/6d0ee55d-49cb-4e6c-b0a3-455c2e0a3ed0)


![image](https://github.com/user-attachments/assets/da271a2b-8077-4303-9d0d-a5922bf5c98a)



![image](https://github.com/user-attachments/assets/3dfb7e59-02d4-43ee-b799-f1a37062fbcf)


Membuat Menu Admin
Menu admin adalah untuk proses CRUD data artikel. Buat method baru pada Controller
Artikel dengan nama admin_index().

 ![image](https://github.com/user-attachments/assets/1806c0f0-2092-48b5-907d-b3e44ae45aba)


Selanjutnya buat view untuk tampilan admin dengan nama admin_index.php

 ![image](https://github.com/user-attachments/assets/22469552-0204-4e85-8e53-80b8ae9a967c)


Tambahkan routing untuk menu admin seperti berikut:
 
![image](https://github.com/user-attachments/assets/63e4e5b0-2232-4771-b41f-0d06c42cc564)


Akses menu admin dengan url http://localhost:8080/admin/artikel

![image](https://github.com/user-attachments/assets/cdf93297-52e9-4bf3-874c-2d433cd98dbe)


Menambah Data Artikel
Tambahkan fungsi/method baru pada Controller Artikel dengan nama add().

 ![image](https://github.com/user-attachments/assets/eb5ea5c0-6dc6-4a1a-9add-64cca00fdcae)


Kemudian buat view untuk form tambah dengan nama form_add.php
 
 ![image](https://github.com/user-attachments/assets/f2e64661-2f10-4776-8b3d-16fc41b11190)


Lihat hasil outputnya.

![image](https://github.com/user-attachments/assets/1ceb3311-2d2e-4d7e-aff3-f70ec2912cc8)


Mengubah Data
Tambahkan fungsi/method baru pada Controller Artikel dengan nama edit().
 
![image](https://github.com/user-attachments/assets/5fbe8cf9-c700-4b42-a797-e027353493d9)
)

Menghapus Data
Tambahkan fungsi/method baru pada Controller Artikel dengan nama delete().
![image](https://github.com/user-attachments/assets/288e1d55-a300-417e-a35c-a790c9f25071)


**Pertanyaan dan Tugas**

Selesaikan programnya sesuai Langkah-langkah yang ada. Anda boleh melakukan improvisasi.

Laporan Praktikum
1. Melanjutkan praktikum sebelumnya pada repository dengan nama Lab7Web.
2. Kerjakan semua latihan yang diberikan sesuai urutannya.
3. Screenshot setiap perubahannya.
4. Update file README.md dan tuliskan penjelasan dari setiap langkah praktikum beserta
screenshotnya.
5. Commit hasilnya pada repository masing-masing.
6. Kirim URL repository pada e-learning ecampus

---

---

**Praktikum 3: View Layout dan View Cell**

Tujuan
Setelah menyelesaikan praktikum ini, mahasiswa diharapkan dapat:
1. Memahami konsep View Layout di CodeIgniter 4.
2. Menggunakan View Layout untuk membuat template tampilan.
3. Memahami dan mengimplementasikan View Cell dalam CodeIgniter 4.
4. Menggunakan View Cell untuk memanggil komponen UI secara modular.
   
Instruksi Praktikum

1. Persiapkan text editor misalnya VSCode.
2. Buka kembali folder dengan nama lab7_php_ci pada docroot webserver (htdocs)
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.
   
Langkah-langkah Praktikum
Persiapan.

Pada praktikum sebelumnya kita telah menggunakan template layout dengan konsep parsial atau memecah bagian template menjadi beberapa bagian untuk kemudian di include pada view yang lain.
Praktikum kali ini kita akan mengunakan konsep View Layout dan View Cell untuk memudahkan dalam penggunaan layout.

Membuat Layout Utama
Buat folder layout di dalam app/Views/
Buat file main.php di dalam folder layout dengan kode berikut

![image](https://github.com/user-attachments/assets/6b0324a9-3518-46da-95f5-c8081633ce06)


Modifikasi File View
Ubah app/Views/home.php agar sesuai dengan layout baru:

![image](https://github.com/user-attachments/assets/6c22129a-31a4-4414-901b-9924130ab685)


Sesuaikan juga untuk halaman lainnya yang ingin menggunakan format layout yang baru

Menampilkan Data Dinamis dengan View Cell
View Cell adalah fitur yang memungkinkan pemanggilan tampilan dalam bentuk komponen
yang dapat digunakan ulang. Cocok digunakan untuk elemen-elemen yang sering muncul di
berbagai halaman seperti sidebar, widget, atau menu navigasi.

Membuat Class View Cell
Buat folder Cells di dalam app/
Buat file ArtikelTerkini.php di dalam app/Cells/ dengan kode berikut:

![image](https://github.com/user-attachments/assets/575a12b1-e4d1-4671-98c7-c267600ec1a3)


Membuat View untuk View Cell
Buat folder components di dalam app/Views/
Buat file artikel_terkini.php di dalam app/Views/components/ dengan kode berikut

![image](https://github.com/user-attachments/assets/b86b7838-8429-45e7-b754-d798bc7e7ea9)



**Pertanyaan Dan Tugas**

• Sesuaikan data dengan praktikum sebelumnya, perlu melakukan perubahan field pada
database dengan menambahkan tanggal agar dapat mengambil data artikel terbaru.

• Selesaikan programnya sesuai Langkah-langkah yang ada. Anda boleh melakukan
improvisasi.

• Apa manfaat utama dari penggunaan View Layout dalam pengembangan aplikasi?
View Layout adalah fondasi penting dalam desain UI aplikasi karena memastikan antarmuka terstruktur, adaptif, dan mudah dirawat, yang pada akhirnya meningkatkan kualitas dan pengalaman pengguna aplikasi.

• Jelaskan perbedaan antara View Cell dan View biasa.
View: Komponen UI biasa (seperti Label, Button, dll.) digunakan langsung dalam layout.

ViewCell: Wadah khusus untuk View, digunakan dalam list (seperti ListView) untuk menampilkan item data.

Kesimpulan:
View = untuk tampilan umum.
ViewCell = untuk tampilan item dalam daftar.

• Ubah View Cell agar hanya menampilkan post dengan kategori tertentu.



Laporan Praktikum
1. Melanjutkan praktikum sebelumnya pada repository dengan nama Lab7Web.
2. Kerjakan semua latihan yang diberikan sesuai urutannya.
3. Screenshot setiap perubahannya.
4. Update file README.md dan tuliskan penjelasan dari setiap langkah praktikum beserta
screenshotnya.
5. Commit hasilnya pada repository masing-masing.
6. Kirim URL repository pada e-learning ecampus

---

---

**Praktikum 4: Framework Lanjutan (Modul Login)**

Tujuan

1. Mahasiswa mampu memahami konsep dasar Auth dan Filter.
2. Mahasiswa mampu memahami konsep dasar Login System.
3. Mahasaswa mampu membuat modul login menggunakan Framework Codeigniter 4.
   
Instruksi Praktikum

1. Persiapkan text editor misalnya VSCode.
2. Buka kembali folder dengan nama lab7_php_ci pada docroot webserver (htdocs)
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.
   
Langkah-langkah Praktikum
Persiapan.

Untuk memulai membuat modul Login, yang perlu disiapkan adalah database server
menggunakan MySQL. Pastikan MySQL Server sudah dapat dijalankan melalui XAMPP.
Membuat Tabel: User Login
![image](https://github.com/user-attachments/assets/2514d6c6-9372-420e-b1cf-84d9bb736a93)

Membuat Tabel User

![image](https://github.com/user-attachments/assets/36ed2f2a-6d98-4e3c-bfb5-4c84054b3141)

Membuat Model User

![image](https://github.com/user-attachments/assets/27040a0a-d955-44a3-ae01-6e3bc339cd43)

Selanjutnya adalah membuat Model untuk memproses data Login. Buat file baru pada direktori
app/Models dengan nama UserModel.php
 
Membuat Controller User

Buat Controller baru dengan nama User.php pada direktori app/Controllers. Kemudian
tambahkan method index() untuk menampilkan daftar user, dan method login() untuk proses
login.

 ![image](https://github.com/user-attachments/assets/b2d6025c-bcc6-4bb2-8080-d5ddb2b8693b)

Membuat View Login

Buat direktori baru dengan nama user pada direktori app/views, kemudian buat file baru dengan nama login.php.

 ![image](https://github.com/user-attachments/assets/6db59224-a52c-4778-9ec0-917368ad870f)

Membuat Database Seeder

Database seeder digunakan untuk membuat data dummy. Untuk keperluan ujicoba modul
login, kita perlu memasukkan data user dan password kedaalam database.
Untuk itu buat database seeder untuk tabel user.
Buka CLI, kemudian tulis perintah berikut:

 ![image](https://github.com/user-attachments/assets/dac8b9db-68be-4c25-91ea-bf5f8f47c90f)

Selanjutnya, buka file UserSeeder.php yang berada di lokasi direktori
/app/Database/Seeds/UserSeeder.php kemudian isi dengan kode berikut:

 ![image](https://github.com/user-attachments/assets/7255734e-0f75-4e29-8cdd-8e80350fa23f)

Selanjutnya buka kembali CLI dan ketik perintah berikut:

 ![image](https://github.com/user-attachments/assets/72024936-42b5-4000-8378-c31125917478)

Uji Coba Login
Selanjutnya buka url http://localhost:8080/user/login seperti berikut:
 
![image](https://github.com/user-attachments/assets/62cdf579-ba73-457a-8cdb-da1ea490cafb)


Menambahkan Auth Filter
Selanjutnya membuat filer untuk halaman admin. Buat file baru dengan nama Auth.php pada
direktori app/Filters.

 ![image](https://github.com/user-attachments/assets/9eb64fc1-2f1e-4869-84a8-a65b883e2912)

Selanjutnya buka file app/Config/Filters.php tambahkan kode berikut:
 
 ![image](https://github.com/user-attachments/assets/7f74fbd0-b067-49fa-ad11-0669f0dfba92)

![image](https://github.com/user-attachments/assets/649b1396-017a-4298-94ca-c1c66814e2cb)

Selanjutnya buka file app/Config/Routes.php dan sesuaikan kodenya.

 ![image](https://github.com/user-attachments/assets/1ccfec77-fd2b-44a8-9f95-39baabc84381)

Percobaan Akses Menu Admin

Buka url dengan alamat http://localhost:8080/admin/artikel ketika alamat tersebut diakses
maka, akan dimuculkan halaman login.
 
![image](https://github.com/user-attachments/assets/8ce2e976-83e1-4c7d-b406-5b78f0e7cc63)

Fungsi Logout

![image](https://github.com/user-attachments/assets/bb3174ae-a4f9-42eb-8cfa-24b6379f3593)

Tambahkan method logout pada Controller User seperti berikut:
 
**Pertanyaan dan Tugas**

Selesaikan programnya sesuai Langkah-langkah yang ada. Anda boleh melakukan improvisasi.

Laporan Praktikum

1. Melanjutkan praktikum sebelumnya pada repository dengan nama Lab7Web.
2. Kerjakan semua latihan yang diberikan sesuai urutannya.
3. Screenshot setiap perubahannya.
4. Update file README.md dan tuliskan penjelasan dari setiap langkah praktikum beserta
screenshotnya.
5. Commit hasilnya pada repository masing-masing.
6. Kirim URL repository pada e-learning ecampus

---

---

**Praktikum 5: Pagination dan Pencarian**

Tujuan

1. Mahasiswa mampu memahami konsep dasar Pagination.
2. Mahasiswa mampu memahami konsep dasar Pencarian.
3. Mahasaswa mampu membuat Paging dan Pencarian menggunakan Framework
Codeigniter 4.
Instruksi Praktikum
1. Persiapkan text editor misalnya VSCode.
2. Buka kembali folder dengan nama lab7_php_ci pada docroot webserver (htdocs)
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.
Langkah-langkah Praktikum
Membuat Pagination
Pagination merupakan proses yang digunakan untuk membatasi tampilan yang panjang
dari data yang banyak pada sebuah website. Fungsi pagination adalah memecah tampilan
menjadi beberapa halaman tergantung banyaknya data yang akan ditampilkan pada
setiap halaman.
Pada Codeigniter 4, fungsi pagination sudah tersedia pada Library sehingga cukup mudah
menggunakannya.
Untuk membuat pagination, buka Kembali Controller Artikel, kemudian modifikasi kode
pada method admin_index seperti berikut.

 ![image](https://github.com/user-attachments/assets/15572fc6-b465-4816-96d5-18468a33e370)

Kemudian buka file views/artikel/admin_index.php dan tambahkan kode berikut
dibawah deklarasi tabel data.

 ![image](https://github.com/user-attachments/assets/efb35ad5-a14f-42fa-b2b3-b797dc50da3a)

Selanjutnya buka kembali menu daftar artikel, tambahkan data lagi untuk melihat
hasilnya.

 ![image](https://github.com/user-attachments/assets/89d51c47-3409-4a01-83e2-9bb74f85057b)

Membuat Pencarian

Pencarian data digunakan untuk memfilter data.
Untuk membuat pencarian data, buka kembali Controller Artikel, pada method
admin_index ubah kodenya seperti berikut:

 ![image](https://github.com/user-attachments/assets/ed718436-eda2-4463-ae45-3ad23d579d4c)

Kemudian buka kembali file views/artikel/admin_index.php dan tambahkan form
pencarian sebelum deklarasi tabel seperti berikut:

 ![image](https://github.com/user-attachments/assets/042768c8-ebda-4c9f-a30c-19eaea87798b)

Dan pada link pager ubah seperti berikut.

 ![image](https://github.com/user-attachments/assets/8ad20e41-087a-4e3e-b442-c0f74a25f64c)

Selanjutnya ujicoba dengan membuka kembali halaman admin artikel, masukkan kata
kunci tertentu pada form pencarian.

 ![image](https://github.com/user-attachments/assets/a9fc5dc6-b645-4b30-ac2a-1b73392fb9c1)

**Pertanyaan dan Tugas**

Selesaikan programnya sesuai Langkah-langkah yang ada. Anda boleh melakukan
improvisasi.

Laporan Praktikum

1. Melanjutkan praktikum sebelumnya pada repository dengan nama Lab7Web.
2. Kerjakan semua latihan yang diberikan sesuai urutannya.
3. Screenshot setiap perubahannya.
4. Update file README.md dan tuliskan penjelasan dari setiap langkah praktikum
beserta screenshotnya.
5. Commit hasilnya pada repository masing-masing.
6. Kirim URL repository pada e-learning ecampus

---

---

**Praktikum 6: Upload File Gambar**

Tujuan

1. Mahasiswa mampu memahami konsep dasar File Upload.
2. Mahasaswa mampu membuat File Upload menggunakan Framework Codeigniter 4.
Instruksi Praktikum
1. Persiapkan text editor misalnya VSCode.
2. Buka kembali folder dengan nama lab7_php_ci pada docroot webserver (htdocs)
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.
Langkah-langkah Praktikum
Upload Gambar pada Artikel
Menambahkan fungsi unggah gambar pada tambah artikel.
Buka kembali Controller Artikel pada project sebelumnya, sesuaikan kode pada method
add seperti berikut:

 ![image](https://github.com/user-attachments/assets/0523bb8b-3238-4760-9c64-110a1910ab7f)

Kemudian pada file views/artikel/form_add.php tambahkan field input file seperti
berikut.

 ![image](https://github.com/user-attachments/assets/e4e5b012-9ccc-42c9-bd90-02af216f1b3e)

Dan sesuaikan tag form dengan menambahkan ecrypt type seperti berikut.

 ![image](https://github.com/user-attachments/assets/0e8756e1-5db7-4a91-88cb-83271ec76d07)

Ujicoba file upload dengan mengakses menu tambah artikel.

 ![image](https://github.com/user-attachments/assets/5684a6c8-3427-431d-b8c4-0ac1da237677)

Pertanyaan dan Tugas

Selesaikan programnya sesuai Langkah-langkah yang ada. Anda boleh melakukan
improvisasi.

Laporan Praktikum

1. Melanjutkan praktikum sebelumnya pada repository dengan nama Lab11Web.
2. Kerjakan semua latihan yang diberikan sesuai urutannya.
3. Screenshot setiap perubahannya.
4. Update file README.md dan tuliskan penjelasan dari setiap langkah praktikum
beserta screenshotnya.
5. Commit hasilnya pada repository masing-masing.
6. Kirim URL repository pada e-learning ecampus

---

---

**Praktikum 7: Relasi Tabel dan Query Builder**

Tujuan

1. Mahasiswa mampu memahami konsep relasi antar tabel dalam database.
2. Mahasiswa mampu mengimplementasikan relasi One-to-Many.
3. Mahasiswa mampu melakukan query dengan join tabel menggunakan Query Builder.
4. Mahasiswa mampu menampilkan data dari tabel yang berelasi.
   
Instruksi Praktikum

1. Persiapkan text editor (VSCode).
2. Buka kembali folder proyek lab7_php_ci.
3. Ikuti langkah-langkah praktikum berikut:
   
Relasi Tabel dan Query Builder
Praktikum ini merupakan kelanjutan dari praktikum sebelumnya, dimana kita akan
memperdalam pemahaman tentang Model, Relasi Tabel dan Joining, serta penggunaan Query Builder dalam CodeIgniter 4.

• Model: Dalam CodeIgniter, Model adalah bagian dari arsitektur MVC (Model-View-
Controller) yang bertugas untuk berinteraksi dengan database. Model menyediakan cara

untuk mengambil, menyimpan, mengubah, dan menghapus data dari database.
• Relasi Tabel: Relasi tabel digunakan untuk menghubungkan data antar tabel dalam
database. Dalam praktikum ini, kita akan fokus pada relasi One-to-Many, di mana satu kategori dapat memiliki banyak artikel.

• Query Builder: Query Builder adalah fitur yang disediakan oleh CodeIgniter untuk
membuat query database dengan cara yang lebih mudah dan aman. Dengan Query Builder,
kita dapat melakukan join tabel, memfilter data, dan mengurutkan hasil tanpa harus menulis query SQL secara manual. Dengan memahami konsep-konsep ini, Anda akan mampu membangun aplikasi web yang lebih kompleks dan efisien.

Langkah-langkah Praktikum
1. Persiapan
   
Pastikan MySQL Server sudah berjalan, dan buka database `lab_ci4

2. Membuat Tabel Kategori
Kita akan membuat tabel baru bernama `kategori` untuk mengkategorikan artikel.
Struktur Tabel `kategori`:

 ![image](https://github.com/user-attachments/assets/45b41d8c-beb9-42d7-9b92-dd43a11875bb)

Jalankan query berikut:

 ![image](https://github.com/user-attachments/assets/60625592-3180-454c-90ed-1714dbb9a87e)

3. Mengubah Tabel Artikel
Tambahkan foreign key `id_kategori` pada tabel `artikel` untuk membuat relasi dengan tabel
`kategori`.
Query untuk menambahkan foreign key:

 ![image](https://github.com/user-attachments/assets/af669284-5981-4d60-b2e2-714a44540015)

4. Membuat Model Kategori
Buat file model baru di `app/Models` dengan nama `KategoriModel.php`:

 ![image](https://github.com/user-attachments/assets/dd38d233-4d15-417e-a3a7-88c111c59965)

5. Memodifikasi Model Artikel
Modifikasi `ArtikelModel.php` untuk mendefinisikan relasi dengan `KategoriModel`:

 ![image](https://github.com/user-attachments/assets/ca640741-124d-40e7-a75f-fac7ab10702d)

Menambahkan method `getArtikelDenganKategori()` untuk mengambil data artikel beserta
nama kategorinya menggunakan join.
6. Memodifikasi Controller Artikel
Modifikasi `Artikel.php` untuk menggunakan model baru dan menampilkan data relasi:

 ![image](https://github.com/user-attachments/assets/928a0b90-3c86-4cc2-b5b7-539b03f29dcd)

7. Memodifikasi View
Buka folder view/artikel sesuaikan masing-masing view.
index.php

 ![image](https://github.com/user-attachments/assets/365a427e-69c1-497b-be1c-05bdcba18712)

admin_index.php

 ![image](https://github.com/user-attachments/assets/b50b139e-a580-48f9-9bd5-bed5e5f33267)

form_add.php

 ![image](https://github.com/user-attachments/assets/896fb81d-c8b5-48bd-a2b9-7c43568599b1)

form_edit.php

 ![image](https://github.com/user-attachments/assets/2edba617-3baf-4448-9de0-8114f38605b6)

8. Testing
Lakukan uji coba untuk memastikan semua fungsi berjalan dengan baik:
• Menampilkan daftar artikel dengan nama kategori.
• Menambah artikel baru dengan memilih kategori.
• Mengedit artikel dan mengubah kategorinya.
• Menghapus artikel.

1.	Tampilan daftar artikel dengan nama kategori.

 ![image](https://github.com/user-attachments/assets/8f3e1dc7-770e-45a7-83b9-36fcfc93cc10)

2.	Menambah artikel baru dengan memilih kategori.

![image](https://github.com/user-attachments/assets/349c577a-01fe-4501-a6a3-73b88e3f94d6)

3.	Mengedit artikel dan mengubah kategorinya.

 ![image](https://github.com/user-attachments/assets/08abf016-071b-4f89-be9e-7c89bc73acf1)

4.	Menghapus artikel.
 

**Pertanyaan dan Tugas**

1. Selesaikan semua langkah praktikum di atas.
2. Modifikasi tampilan detail artikel (artikel/detail.php) untuk menampilkan nama kategori
artikel.
3. Tambahkan fitur untuk menampilkan daftar kategori di halaman depan (opsional).
4. Buat fungsi untuk menampilkan artikel berdasarkan kategori tertentu (opsional).

Laporan Praktikum

1. Lanjutkan praktikum pada repository Lab7Web.
2. Kerjakan semua latihan sesuai urutan.
3. Screenshot setiap perubahan.
4. Update file README.md dengan penjelasan dan screenshot.
5. Commit hasil praktikum.
6. Kirim URL repository.
