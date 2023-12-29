## 1.1 Latar belakang
Membuat game pertama saya, tentu itu bukan hal yang mudah bahkan sebetulnya rumit bagi saya yang baru mengenal pemrograman terutama bidang informatika oleh karena itu saya ingin membuat game yang membuat playernya berpikir dengan berhitung.saya akan membuat game perhitungan atau masuk kategori matematika. 
## 1.2 Deskripsi dan alur cerita dari game
permainan dimulai player bisa bergerak menggunakan keyboard.
Didalam permainan terdapat 2 musuh berupa batu bulat yang bergerak random. Jika player bertabrakan dengan musuh maka permainan berakhir.

Di dalam permainan terdapat 3 jenis point yang menyebar secara random:

Point jeruk yang memiliki nilai 10 point. Ketika player telah mendapatkan 3 kali point jeruk maka sistem akan menampilkan soal matematika penjumlahan dengan angka random dan sistem memberikan dua opsi jawaban. Jika player memilih pertanyaan yang benar maka permainan berlanjut namun jika player salah memilih jawaban maka game berakhir.

Point semangka yang memiliki nilai 15 point. Ketika player telah mendapatkan 3 kali point semangka maka sistem akan menampilkan soal matematika perkalian dengan angka random dan sistem memberikan dua opsi jawaban. Jika player memilih pertanyaan yang benar maka permainan berlanjut namun jika player salah memilih jawaban maka game berakhir.

Point anggur yang memiliki nilai 25 point. Ketika player telah mendapatkan 3 kali point anggur maka sistem akan menampilkan soal matematika turunan dengan angka random dan sistem memberikan dua opsi jawaban. Jika player memilih pertanyaan yang benar maka permainan berlanjut namun jika player salah memilih jawaban maka game berakhir.

Di akhir permainan, untuk menentukan kemenangan, jika point yang didapatkan player nilainya sama dengan score yang player input di awal maka player menang, namun jika ternyata point yang diperoleh player tidak sama dengan nilai score yang player input di awal maka player kalah.
## 1.3 branding dari game
a. nama
namanya inputScore
karena untuk game ini berfokus untuk menghasilkan point yang sesuai dengan score yang diinput pemain d awal.
b. target pengguna
game ini untuk semua kalangan terutama pelajar karena ini berkaitan dengan perhitungan. namun saya lebih menargetkan kepada orang orang yang sedang tidak ada kerjaan.
## 1.4 apa aja yang bisa player lakukan
-player input score diawal
-player bisa bergerak (atas,bawah,kanan,kiri)
-player bisa mendapatkan point
## 1.5 Desain User Interface
https://github.com/Alythar/UTS-UAS_Nisrina-Aliya-Tharifah_1237050044/issues/2#issue-2056450869
## 1.6 Flowchart
https://github.com/Alythar/UTS-UAS_Nisrina-Aliya-Tharifah_1237050044/issues/1#issuecomment-1869547123
## 1.7 Link Demo game
## 1.8 Kode Pemograman Game
## 2. konsep variable, data type dan operator pada bahasa pemrograman digunakan dalam pembuatan game ini
Pada game ini terdapat variabel, data type yang digunakan yaitu 
2.1 Di class MathGame
int skorPemain : Menyimpan skor pemain dalam permainan.
int skorInputPemain : Menyimpan skor input awal pemain.
JTabbedPane tabbedPane: Mewakili komponen GUI untuk tabbed pane.
JPanel panelPermainan: Mewakili panel permainan dalam tabbed pane.
int posisiPemainX, posisiPemainY: Menyimpan posisi pemain dalam koordinat x dan y.
List<Point> musuh, jeruk, semangka, anggur: Menyimpan posisi musuh, jeruk, semangka, dan anggur menggunakan kelas Point.
Timer timerMusuh: Digunakan untuk mengatur pergerakan musuh secara berkala.
2.2 Di luar class MathGame
Random rand: Membuat objek dari kelas Random untuk menghasilkan nilai acak.
Graphics g: untuk menggambar elemen permainan di panel.
ActionEvent, ActionListener: Untuk menangani kejadian dan membuat listener untuk timer.
KeyEvent, KeyListener: Untuk menangani kejadian tombol keyboard.
Timer timer: Untuk mengatur interval waktu dalam loop permainan.
boolean isMenang: Menandakan apakah permainan berakhir dengan kemenangan atau kekalahan.
2.3 Untuk Operator game ini terdapat operator Aritmatika untuk melakukan operasi matematika pada variabel numerik seperti penjumlahan ataupun perkalian untuk lebih jelasnya operator pada game ini yaitu :
Operator Aritmetika (+=, -=):
Digunakan untuk operasi penambahan dan pengurangan yang meringkas ekspresi. Contoh: posisiPemainY -= 5; (mengurangkan nilai posisiPemainY sebesar 5).
Operator Logika (&&):
Digunakan untuk menggabungkan dua kondisi dengan AND logika. Contoh: posisiPemainX < m.x + 20 && posisiPemainX + 20 > m.x (kedua kondisi harus benar).
Operator Increment dan Decrement (++, --):
Digunakan untuk menambah atau mengurangkan nilai variabel sebesar 1. Contoh: skorPemain++ (menambah nilai skorPemain sebesar 1).   
## 3. konsep boolean dan conditions pada bahasa pemrograman digunakan dalam pembuatan game ini
Boolean memberikan nilai true atau false, pengaplikasianya pada game ini yaitu ketika pemain mendapatkan total point yang nilainya sama dengan score yang pemain input diawal maka kondisi true dan pemain memenangkan permainan namun jika tidak maka kondisi false maka pemain kalah dalam permainan ini. 
## 4. konsep looping dan array pada bahasa pemrograman digunakan dalam pembuatan game ini
looping pada game ini yaitu digunakan pada untuk gerakan musuh yang setiap musuh diberi perintah pergerakan menggunakan random/acak. 
## 5.  konsep method pada bahasa pemrograman digunakan dalam pembuatan game ini
terdapat Methode inisialisasiElemenPermainan yang digunakan untuk mengatur posisi awal musuh, jeruk, semangka, dan anggur dengan membuat objek Point baru dan menambahkannya ke dalam list yang sesuai. kemudian Methode gerakMusuhSecaraAcak yang berisi logika untuk menggerakkan musuh secara acak dalam permainan. Methode deteksiTabrakan bertanggung jawab untuk mendeteksi tabrakan antara pemain dan musuh dalam permainan. Methode akhirPermainyang menangani kondisi akhir permainan, menampilkan pesan berdasarkan apakah pemain menang atau kalah.
## 6. konsep class pada bahasa pemrograman digunakan dalam pembuatan game ini 
class Pemain yang menginisialisasi elemen pemain
class musuh yang menginsisialisasi elemen musuh 
class poin yang menjadikan elemen point
class MathGame yang menjadi kelas utama 
## 7. Algoritma
- Inisialisasi Permainan:
Mendefinisikan variabel dan struktur data yang diperlukan seperti skor pemain, posisi pemain, musuh, dan poin.

- Membuat tampilan permainan menggunakan GUI Swing.
Loop Permainan:
Memulai loop permainan menggunakan Timer untuk mengatur pembaruan kondisi permainan secara berkala.
Dalam setiap iterasi loop, kondisi permainan diperbarui dengan memanggil metode-metode seperti deteksiTabrakan dan deteksiPengumpulanPoint.
Deteksi Tabrakan:

- Mengecek apakah pemain bertabrakan dengan musuh.
Jika tabrakan terdeteksi, memanggil metode akhirPermain untuk menentukan hasil permainan.

- Mendeteksi input keyboard dari pemain melalui metode keyPressed.
Menggerakkan posisi pemain sesuai input yang diterima.
Penggambaran Elemen Permainan:

- Menggunakan metode gambarElemenPermainan untuk menggambar pemain, musuh, dan poin di layar.
Setiap elemen diberi warna berbeda menggunakan setColor.
Penanganan Input Pemain:

- Mengimplementasikan KeyListener untuk menangani input keyboard dari pemain.
Menanggapi event key pressed dengan memperbarui posisi pemain.
Penanganan Akhir Permainan:

- Menampilkan pesan akhir permainan dan hasilnya (menang atau kalah).
Memberhentikan timer dan memberikan opsi untuk keluar dari permainan.

## 8. Penggunaan Array 
pada game ini diantaranya yaitu pada elemen musuh dan elemen poin (jeruk, semangaka,anggur) yang dimana array digunakan untuk menyimpan posisi dengan kordinat x,y
## 9. Pengembangan Algoritma
untuk pengembangan Algoritma sendiri yaitu saya menambahkan musuh ke dalam game, yang dimana musuh bergerak secara random dan jika player bertabrakan dengan musuh maka permainan berakhir. disini juga saya menambahkan rintangan pada design game ini yaitu untuk jalur jalan yang dilalui oleh pemain tidak lurus saja melainkan ada rintangan yang harus dilewati pemain.
