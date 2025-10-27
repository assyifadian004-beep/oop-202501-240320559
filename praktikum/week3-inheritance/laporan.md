# Laporan Praktikum Minggu 3
Topik: [Tuliskan judul topik, misalnya "Class dan Object"]

## Identitas
- Nama  : [As Syifa Dian Rinesti]
- NIM   : [240320559]
- Kelas : [3DSRA]

---

## Tujuan
- Mahasiswa mampu menjelaskan konsep inheritance (pewarisan class) dalam OOP.
- Mahasiswa mampu membuat superclass dan subclass untuk produk pertanian.
- Mahasiswa mampu mendemonstrasikan hierarki class melalui contoh kode.
- Mahasiswa mampu menggunakan super untuk memanggil konstruktor dan method parent class.
- Mahasiswa mampu membuat laporan praktikum yang menjelaskan perbedaan penggunaan inheritance dibanding class tunggal.


---

## Dasar Teori
Inheritance adalah mekanisme dalam OOP yang memungkinkan suatu class mewarisi atribut dan method dari class lain.

- Superclass: class induk yang mendefinisikan atribut umum.
- Subclass: class turunan yang mewarisi atribut/method superclass, dan dapat menambahkan atribut/method baru.
- Super: digunakan untuk memanggil konstruktor atau method superclass.

Dalam konteks Agri-POS, kita dapat membuat class Produk sebagai superclass, kemudian Benih, Pupuk, dan AlatPertanian sebagai subclass. Hal ini membuat kode lebih reusable dan terstruktur.



---

## Langkah Praktikum
1. Membuat Superclass Produk
   Gunakan class Produk dari Bab 2 sebagai superclass.
2. Membuat Subclass
   Benih.java → atribut tambahan: varietas.
   Pupuk.java → atribut tambahan: jenis pupuk (Urea, NPK, dll).
   AlatPertanian.java → atribut tambahan: material (baja, kayu, plastik).
3. Membuat Main Class
   Instansiasi minimal satu objek dari tiap subclass.
   Tampilkan data produk dengan memanfaatkan inheritance.
4. Menambahkan CreditBy
   Panggil class CreditBy untuk menampilkan identitas mahasiswa.
5. Commit dan Push
   Commit dengan pesan: week3-inheritance.

---

## Kode Program


```java
package com.upb.agripos;

import com.upb.agripos.model.*;
import com.upb.agripos.util.CreditBy;

public class MainInheritance {
    public static void main(String[] args) {
        Benih b = new Benih("BNH-001", "Benih Padi IR64", 25000, 100, "IR64");
        Pupuk p = new Pupuk("PPK-101", "Pupuk Urea", 350000, 40, "Urea");
        AlatPertanian a = new AlatPertanian("ALT-501", "Cangkul Baja", 90000, 15, "Baja");

        System.out.println("Benih: " + b.getNama() + " Varietas: " + b.getVarietas());
        System.out.println("Pupuk: " + p.getNama() + " Jenis: " + p.getJenis());
        System.out.println("Alat Pertanian: " + a.getNama() + " Material: " + a.getMaterial());

        CreditBy.print("240320559", "As Syifa Dian Rinesti");
    }
}
```

---

## Hasil Eksekusi
(Sertakan screenshot hasil eksekusi program.  
![Screenshot hasil eksekusi week3](https://github.com/assyifadian004-beep/oop-202501-240320559/blob/main/praktikum/week3-inheritance/screenshots/SS-WEEK3.png)
)
---

## Analisis

- Jelaskan bagaimana kode berjalan.
   Program membuat objek dari subclass (Benih dan Pupuk) yang mewarisi atribut dan method dari AlatPertanian.
   Saat program dijalankan:
   - Konstruktor subclass memanggil konstruktor superclass dengan super().
   - Method tampilInfo() di superclass digunakan kembali dan ditambah informasi khusus di subclass.
   - Output menampilkan data lengkap masing-masing produk pertanian.
- Apa perbedaan pendekatan minggu ini dibanding minggu sebelumnya.
   Minggu sebelumnya fokus pada class dan object tanpa hubungan antar class (semua berdiri sendiri), sedangkan minggu ini menggunakan inheritance dimana ada hubungan superclass–subclass untuk reuse kode dan membentuk hierarki yang lebih terstruktur.
- Kendala yang dihadapi dan cara mengatasinya.
   Kendala: Error “class should be declared in a file named...” karena semua class disimpan dalam satu file.
   Solusi: Memisahkan setiap public class ke file terpisah sesuai nama class-nya.
   Kendala lain: Cannot find symbol akibat urutan kompilasi atau struktur folder salah.
   Solusi: Menyesuaikan struktur package (package com.upb.agripos.model;) dan menjalankan javac dari direktori java.

---

## Kesimpulan
(Pada praktikum minggu ini, mahasiswa memahami konsep inheritance dalam pemrograman berorientasi objek, yaitu pewarisan atribut dan method dari *superclass* ke *subclass*. Dengan inheritance, kode menjadi lebih efisien, mudah dipelihara, dan *terstruktur* melalui hubungan hierarki antar class. Praktikum ini juga menunjukkan bagaimana *subclass* dapat menambah atau memodifikasi perilaku superclass serta pentingnya pengelolaan file dan package agar program dapat berjalan dengan benar.
)

---

## Quiz
1. Apa keuntungan menggunakan inheritance dibanding membuat class terpisah tanpa hubungan?  
   **Jawaban:** 
   1. Menghindari penulisan kode berulang (reuse kode).
   2. Memudahkan pemeliharaan dan pengembangan program.
   3. Membuat struktur class lebih teratur dan logis (is-a relationship).
   4. Mendukung polymorphism untuk fleksibilitas program.

2. Bagaimana cara subclass memanggil konstruktor superclass?  
   **Jawaban:** 
   Subclass memanggil konstruktor superclass dengan menggunakan keyword super().
   - super() harus ditulis di baris pertama konstruktor subclass.
   - Digunakan untuk mengirim nilai ke konstruktor di superclass agar atribut yang diwarisi dapat diinisialisasi.

3. Berikan contoh kasus di POS pertanian selain Benih, Pupuk, dan Alat Pertanian yang bisa dijadikan subclass.
   **Jawaban:** 
   1. Pestisida → subclass dari ProdukPertanian atau AlatPertanian
   - Atribut khusus: jenisPestisida, kandunganAktif, ukuranBotol.
   2. Herbisida → subclass dari Pestisida
   - Atribut khusus: jenisGulmaTarget, waktuAplikasi.
   3. MesinPertanian → subclass dari AlatPertanian
   - Atribut khusus: dayaMesin, bahanBakar, kapasitasKerja.
   4. BibitSayuran → subclass dari Benih
   - Atribut khusus: jenisSayur, masaTanam, ketahananHama.
   5. SistemIrigasi → subclass dari AlatPertanTuliskan kesimpulan dari praktikum minggu iniian
   - Atribut khusus: tipeIrigasi, jangkauan, konsumsiAir.
