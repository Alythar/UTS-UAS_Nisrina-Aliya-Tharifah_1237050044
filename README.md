# UTS-UAS NISRINA ALIYA THARIFAH_1237050044
## 1.1 Latar belakang
Membuat game pertama saya, tentu itu bukan hal yang mudah bahkan sebetulnya rumit bagi saya yang baru mengenal pemrograman terutama bidang informatika oleh karena itu saya ingin membuat game yang membuat playernya berpikir dengan berhitung.saya akan membuat game perhitungan atau masuk kategori matematika. 
## 1.2 Deskripsi dan alur cerita dari game
permainan dimulai dengan player dapat input score sesuai angka yang player inginkan yang nantinya player harus bisa menghasilkan total point yang sama sesuai dengan point yang player input diawal.
Didalam permainan terdapat 2 musuh berupa batu kotak yang bergerak random. Jika player bertabrakan dengan musuh maka permainan berakhir.

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
- player input score diawal
- player bisa bergerak (atas,bawah,kanan,kiri)
- player bisa mendapatkan point
- player bisa memilih optsi jawaban dari soal matematika
## 1.5 Desain User Interface
https://github.com/Alythar/UTS-UAS_Nisrina-Aliya-Tharifah_1237050044/issues/2#issue-2056450869

## 1.6 Flowchart
https://github.com/Alythar/UTS-UAS_Nisrina-Aliya-Tharifah_1237050044/issues/1#issuecomment-1869547123

## 1.7 Link Demo game
- screenshot dan gift screenrecord 
https://github.com/Alythar/UTS-UAS_Nisrina-Aliya-Tharifah_1237050044/issues/3#issuecomment-1871720706
- link youtube demo game
  dijadikan 2 video terpisah karena channel Youtube saya belum terverifikasi sehingga tidak dapat upload video durasi di atas 15 menit.
  - Part 1  https://youtu.be/7SDYCuz_3PE
  - Part 2  https://youtu.be/FjYccXB99dk

## 1.8 Kode Pemograman Game
package gameAliya;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import java.util.ArrayList;
import java.util.List;
import java.util.Random;

class Pemain {
    int x, y;

    public Pemain(int x, int y) {
       //parameter buat ngasih nilai awal posisi pas objek dibuat nanti 
        this.x = x;
        this.y = y;
        //merujuk ke variabel kelas
        //nilainya diterima dari konstruktor
    }
}

class Musuh {
    int x, y;

    public Musuh(int x, int y) {  
        this.x = x;
        this.y = y;
    }
}

class Poin {
    int x, y;

    public Poin(int x, int y) {
        this.x = x;
        this.y = y;
    }
}

public class MathGame extends JFrame implements KeyListener {
    // kelas turunan dari jframe yang bisa interaksi sama keyboard
    private int skorPemain;
    //untuk nyimpen score pemain pas main permainan
    private int skorInputPemain;
    //nyimpen score yang pemain input diawal

    private JTabbedPane tabbedPane;
    //nampilin tab di frame
    private JPanel panelPermainan;
    // tempat elemen yang ada untuk digambar

    private Pemain pemain;
    //objek pemain
    private List<Musuh> musuhList;
    //list yang nyimpen objek musuh
    private List<Poin> jerukList;
    //list buat nyimpen objek poin yang nilainya jeruk
    private List<Poin> semangkaList;
    //list buat nyimpen objek poin yang nilainya semangka
    private List<Poin> anggurList;
    //list buat nyimpen objek poin yang nilainya anggur


    private Timer timerMusuh;
    //timer untuk ngatur pergerakan musuh (acak)

    public MathGame(int skorAwal) {
       // kosntruktor
        this.skorInputPemain = skorAwal;
        this.skorPemain = 0;

        tabbedPane = new JTabbedPane();
        //objek tabbedpane buat nampilin tab layar permainan

        panelPermainan = new JPanel() {
            // objek untuk nampung elemen 
            @Override
            protected void paintComponent(Graphics g) {
                //gambar elemen pake objek Graphics
                // Graphics (g) untuk ngegambar
                super.paintComponent(g);
                gambarElemenPermainan(g);
            }
        };
        tabbedPane.addTab("Permainan", panelPermainan);

        pemain = new Pemain(100, 100);
        //bikin objek pemain posisinya di (100,100)
        musuhList = new ArrayList<>();
        //array buat nyimpen objek musuh
        jerukList = new ArrayList<>();
        //array buat nyimpen objek point yang nilainya jeruk
        semangkaList = new ArrayList<>();
        //array buat nyimpen objek point yang nilainya semangka
        anggurList = new ArrayList<>();
        //array buat nyimpen objek point yang nilainya anggur
        inisialisasiElemenPermainan();
        //manggil method untuk inisialisasi elemen permainan

        addKeyListener(this);
        //nambahin keylistener ke frame supaya bisa ada input keyboard
        setFocusable(true);
        //ngatur biar frame fokus
        setFocusTraversalKeysEnabled(false);

        timerMusuh = new Timer(1000, new ActionListener() {
            //bikin objek timer untuk ngatur gerakan si musuh acak setiap 1 detik(1000milidetik)
            @Override
            public void actionPerformed(ActionEvent e) {
                //mempresentasikan prisyiwa yg terjadi
                gerakMusuhSecaraAcak();
                panelPermainan.repaint();
                //gambar ulang pas ada pembaruan
            }
        });
        timerMusuh.start();
        //mulai pergerakan musuh

        getContentPane().add(tabbedPane);
        //nambahin contentpane ke frame pane
        mulaiLoopPermainan();
        //method untuk mulai permainanya
    }

    private void inisialisasiElemenPermainan() {
        //method buat inisialisasi elemen dipermainan pas posisi random
        Random rand = new Random();
        for (int i = 0; i < 2; i++) {
            musuhList.add(new Musuh(rand.nextInt(600), rand.nextInt(400)));
        }

        for (int i = 0; i < 3; i++) {
            jerukList.add(new Poin(rand.nextInt(600), rand.nextInt(400)));
            semangkaList.add(new Poin(rand.nextInt(600), rand.nextInt(400)));
            anggurList.add(new Poin(rand.nextInt(600), rand.nextInt(400)));
        }
    }
    //Loop for posisi musuh dan point (x,y)

    private void gambarElemenPermainan(Graphics g) {
        //method buat gambar elemen yang ada di panel
        g.setColor(Color.GREEN);
        g.fillRect(pemain.x, pemain.y, 20, 20);

        g.setColor(Color.BLACK);
        for (Musuh musuh : musuhList) {
            g.fillRect(musuh.x, musuh.y, 20, 20);
        }
        //netepin warna
        //gambar persegi sesuai ukuran dan posisi 

        g.setColor(Color.ORANGE);
        for (Poin jeruk : jerukList) {
            g.fillOval(jeruk.x, jeruk.y, 20, 20);
        }

        g.setColor(Color.RED);
        for (Poin semangka : semangkaList) {
            g.fillOval(semangka.x, semangka.y, 20, 20);
        }

        g.setColor(Color.MAGENTA);
        for (Poin anggur : anggurList) {
            g.fillOval(anggur.x, anggur.y, 20, 20);
        }
    }
    //netepin warna
    //gambar bulet dengan posisi dan ukuran

    private void gerakMusuhSecaraAcak() {
        //method untuk gerakin musuh secara acak di panel
        Random rand = new Random();

        for (Musuh musuh : musuhList) {
            int arah = rand.nextInt(4);

            switch (arah) {
                case 0:
                    musuh.y -= 5;
                    //kebawah
                    break;
                case 1:
                    musuh.x += 5;
                    //kanan
                    break;
                case 2:
                    musuh.y += 5;
                    break;
                    //atas
                case 3:
                    musuh.x -= 5;
                    //kiri
                    break;
            }
        }
    }

    private void mulaiLoopPermainan() {
        //method untuk mulai permainan (ngedeteksi tabrakan sama ngumpulin poin)
        Timer timer = new Timer(100, new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                //memperbarui kondisi permainan
                deteksiTabrakan();
                deteksiPengumpulanPoint();
                

                if (skorPemain == skorInputPemain) {
                    akhirPermain(true);
                } else if (skorPemain > skorInputPemain) {
                    akhirPermain(false);
                    //ngecek kondisi game over
                }
            }
        });
        timer.start();
    }

    private void deteksiTabrakan() {
        //ngedeteksi kalo pemainantabrakan sama musuh
        for (Musuh musuh : musuhList) {
            //lopnya buat objek musuh yang ada di musuhlist
            if (pemain.x < musuh.x + 20 && pemain.x + 20 > musuh.x &&
                pemain.y < musuh.y + 20 && pemain.y + 20 > musuh.y) {
                    ///ini sulit...tabrakan kan tumpang tindih terus ditambah 20
                    //supaya ngasih ruang tambahan biar klo kena daerah sekitaran situ brrt tabrakan
                akhirPermain(false);
                //klo nabrak atau tabrakan nnt argumenya false
            }
        }
    }

    private void deteksiPengumpulanPoint() {
        for (Poin jeruk : jerukList) {
            //loop utk objek jerus di dlm jeruk list
            if (pemain.x < jeruk.x + 20 && pemain.x + 20 > jeruk.x &&
                pemain.y < jeruk.y + 20 && pemain.y + 20 > jeruk.y) {
                    //konsep sama kaya method tabrakan
                skorPemain += 10;
                //klo tabrakan tambah poin 10
                jerukList.remove(jeruk);
                if (jerukList.isEmpty()) {
                    //masih bingung cara supaya kondisi point udh didapet sama dengan 3x
                    //jadi masih diisi empty
                    tampilkanPertanyaanMatematika("penjumlahan");
                    
                }
                break;
            }
        }
    
        for (Poin semangka : semangkaList) {
            if (pemain.x < semangka.x + 20 && pemain.x + 20 > semangka.x &&
                pemain.y < semangka.y + 20 && pemain.y + 20 > semangka.y) {
                skorPemain += 15;
                semangkaList.remove(semangka);
                if (semangkaList.isEmpty()) {
                    //masih bingung cara supaya kondisi point udh didapet sama dengan 3x
                    //jadi masih diisi empty
                    tampilkanPertanyaanMatematika("perkalian");
                }
                break;
            }
        }
    
        for (Poin anggur : anggurList) {
            if (pemain.x < anggur.x + 20 && pemain.x + 20 > anggur.x &&
                pemain.y < anggur.y + 20 && pemain.y + 20 > anggur.y) {
                skorPemain += 25;
                anggurList.remove(anggur);
                if (anggurList.isEmpty()) {
                    //masih bingung cara supaya kondisi point udh didapet sama dengan 3x
                    //jadi masih diisi empty
                    tampilkanPertanyaanMatematika("turunan");
                    
                }
                break;
            }
        }
    }

    private void tampilkanPertanyaanMatematika(String jenisSoal) {
        Random rand = new Random();
        //objekrandom buat angka acak
    
        int angka1 = rand.nextInt(10) + 1; // Angka random antara 1 dan 10
        int angka2 = rand.nextInt(10) + 1;
        // Angka random antara 1 dan 10 tambah satu biar ga keluar angka nol
        int jawabanBenar;
        String pertanyaan;
    
        switch (jenisSoal) {
            //buat nentuin jenis soal
            case "penjumlahan":
                jawabanBenar = angka1 + angka2;
                pertanyaan = "Berapakah hasil dari " + angka1 + " + " + angka2 + "?";
                break;
            case "perkalian":
                jawabanBenar = angka1 * angka2;
                pertanyaan = "Berapakah hasil dari " + angka1 + " * " + angka2 + "?";
                break;
            case "turunan":
                jawabanBenar = angka1 - angka2;
                pertanyaan = "Apa hasil turunan dari fungsi x^" + angka1 + " + " + angka2 + "?";
                break;
                //yang soal turunan masih belum tau cara nampilinya di terminal
            default:
                return; 
                // Jenis soal diluar dari yang diatas nanti keluar dari method
        }
    
        int jawabanSalah = rand.nextInt(10) + 1;
         // Jawaban salah pake random acak biar salah supaya ga ush input2 lagi
    
        while (jawabanSalah == jawabanBenar) {
            jawabanSalah = rand.nextInt(10) + 1;
             // takutnya jawaban salah hasil random sama kaya jawaban bener jadi dibuat while
             //buat masstiin aja
        }
    
        Object[] options = {jawabanBenar, jawabanSalah};
         // nampilih dua opsi jawaban
         //array indeks 0 jawaban bener indeks 1 salah
    
        int jawabanPlayer = JOptionPane.showOptionDialog(null, pertanyaan, "Pertanyaan Matematika",
                JOptionPane.DEFAULT_OPTION, JOptionPane.QUESTION_MESSAGE, null, options, options[0]);
    
        if (jawabanPlayer == 0) {
             // kondisi kalo jawaban player bener soalnya indeks ke 0
            JOptionPane.showMessageDialog(null, "Jawaban Benar! Permainan Berlanjut.");
        } else { 
            akhirPermain(false);
        }
    }
    

    private void akhirPermain(boolean isMenang) {
        if (isMenang) {
            JOptionPane.showMessageDialog(this, "Selamat, Anda menang!");
        } else {
            JOptionPane.showMessageDialog(this, "Maaf, Anda kalah. Coba lagi!");
        }
        
    }

@Override
    public void keyTyped(KeyEvent e) {
        // Menangani event key typed
        //belum tau cara ngeimplementasiinya
    }

    @Override
    public void keyReleased(KeyEvent e) {
        // Menangani event key released
        //blm tau cara implementasiinya
    }

    @Override
    public void keyPressed(KeyEvent e) {
        //nanganin kejadian waktu ketboard diteken
        
        int keyCode = e.getKeyCode();

        switch (keyCode) {
            case KeyEvent.VK_UP:
                pemain.y -= 5;
                break;
            case KeyEvent.VK_DOWN:
                pemain.y += 5;
                break;
            case KeyEvent.VK_LEFT:
                pemain.x -= 5;
                break;
            case KeyEvent.VK_RIGHT:
                pemain.x += 5;
                break;
        }

        panelPermainan.repaint();
        //gambar ulang perbarui posisi pemain
    }

    public static void main(String[] args) {
        int skorAwal = Integer.parseInt(JOptionPane.showInputDialog("Masukkan skor awal pemain:"));
        //input score awal pemain
        MathGame permainan = new MathGame(skorAwal);
        //inisialisasi gamenya
        JFrame frame = new JFrame("Permainan Matematika");
        //nyiapin frame utama buat setelah layar input score
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(800, 600);
 
        frame.add(permainan.tabbedPane);
        // nambahin tabe pane ke frame
        frame.setVisible(true);
        //nampilin frame
    }
}
//nisrina masih nyari cara supaya pas elemen poin diambil pointya ilang dari layar
//masih nyari yang kalo poin udah didapat 3x maka muncul pertanyaan matematika
//masih mempelajari macem macem "key" soalnya belum paham tapi udah dipake
//masih belum tahu cara bikin soal matematika berpangkatan di terminal



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

## 10. bagaimana game yang dibuat dapat didistribusikan dan digunakan oleh pengguna
- game disempurnakan terlebih dahulu 
- game dikonversi menjadi aplikasi agar dapat diakses dengan mudah oleh pengguna nantinya
-  membuat deskripsi mengenai game dengan menyertakan dokumentasi game 
- menguji coba game kepada beberapa orang dan meminta ulasanya.
- mempublikasikan game di platform maupun di media sosial dengan menyertakan deskripsi dan ulasan mengenai game.
