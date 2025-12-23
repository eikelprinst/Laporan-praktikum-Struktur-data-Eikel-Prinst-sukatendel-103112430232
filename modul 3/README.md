# <h1 align="center">Laporan Praktikum Modul 3&4 <br> ADP&Linkedlist</h1>
<p align="center">EIKEL PRINST SUKATENDEL - 103112430232</p>

## Dasar Teori
Abstract Data Type (ADT) adalah landasan konseptual dalam pemrograman yang mendefinisikan suatu TYPE struktur data beserta serangkaian PRIMITIF atau operasi dasar yang dapat dilakukan terhadapnya. Konsepnya berfokus pada "apa" yang dilakukan oleh data dan bukan "bagaimana" ia diimplementasikan secara internal, menjadikannya definisi yang Statik. Abstract Data Type yang lengkap mencakup delapan kelompok primitif, mulai dari Konstruktor untuk membentuk nilai type baru, Selector untuk mengakses komponen, Destruktor atau Dealokator untuk membebaskan memori, hingga operator relasional dan aritmatika. Dalam praktikum ini, prinsip Information Hiding dari ADT diwujudkan dengan memisahkan implementasi menjadi dua modul utama yaitu Spesifikasi (.h) yang berisi deklarasi type dan prototipe fungsi, dan Realisasi (.c atau .cpp) yang berisi kode program aktual dari primitif-primitif tersebut.

## Guided

### soal 1

Kode C++ ini mendemonstrasikan bagaimana konsep Abstract Data Type (ADT) diimplementasikan secara terstruktur untuk menerapkan prinsip Penyembunyian Informasi. Intinya, ADT mahasiswa dibagi menjadi tiga komponen file logis yaitu mahasiswa.h berfungsi sebagai kontrak ADT yang mendefinisikan struct dan mendeklarasikan prototipe juga fungsi-fungsi primitif seperti inputMhs, rata2, hanya menyatakan apa yang disediakan oleh ADT. mahasiswa.cpp menjadi badan yang menyediakan realisasi kode aktual dari primitif tersebut, menjelaskan bagaimana operasi input dan perhitungan dilakukan. Sementara itu, main.cpp bertindak sebagai program driver yang menggunakan ADT dengan hanya perlu menyertakan file .h dan memanggil fungsi secara langsung, tanpa perlu mengetahui detail implementasi di file .cpp, yang merupakan inti dari arsitektur modular yang bersih.

```go
#ifndef PELAJARAN_H
#define PELAJARAN_H
#include <string>
using namespace std;

// Tipe data pelajaran
struct pelajaran {
    string namaMapel;
    string kodeMapel;
};

// Fungsi untuk membuat data pelajaran
pelajaran create_pelajaran(string namaMapel, string kodeMapel);

// Prosedur untuk menampilkan data pelajaran
void tampil_pelajaran(pelajaran pel);

#endif

```

> Output
> ![Screenshot bagian x](output/screenshot_soal1.png)
> %% Untuk mencantumkan screenshot, tidak boleh ada spasi di urlnya `()`, penamaan file bebas asal gak sara dan mudah dipahami aja,, dan jangan lupa hapus komen ini yah%%

## Unguided

### Soal 1


```go
#ifndef MAHASISWA_H
#define MAHASISWA_H

#include <string>

using namespace std;

const int MAX_MHS = 10;

struct Mahasiswa {
    string nama, nim;
    int uts, uas, tugas;
    float nilaiAkhir;
};

void inputData(Mahasiswa &m);
float hitungNilai(const Mahasiswa &m);
void tampilData(const Mahasiswa &m);

#endif

```

> Output
> ![Screenshot bagian x](output/screenshot_soal1.png)
> %% Untuk mencantumkan screenshot, tidak boleh ada spasi di urlnya `()`, penamaan file bebas asal gak sara dan mudah dipahami aja,, dan jangan lupa hapus komen ini yah%%

Penjelasan 
  Kode di atas merupakan file header (.h) C++ yang digunakan untuk mendefinisikan struktur data dan deklarasi fungsi yang berkaitan dengan data mahasiswa. Struktur Mahasiswa berfungsi sebagai wadah untuk menyimpan identitas mahasiswa (nama dan NIM) serta nilai akademik seperti UTS, UAS, tugas, dan nilai akhir. Penggunaan struct memungkinkan pengelompokan data yang saling berhubungan agar lebih terorganisir dan mudah dikelola dalam program.

Selain itu, header guard (#ifndef, #define, #endif) digunakan untuk mencegah terjadinya pemanggilan ganda file header yang dapat menyebabkan error saat proses kompilasi. Deklarasi fungsi seperti inputData, hitungNilai, dan tampilData bertujuan untuk memisahkan antara definisi data dan implementasi logika program, sehingga kode menjadi lebih modular, mudah dipelihara, dan siap dikembangkan ke skala program yang lebih besar, misalnya pengolahan banyak data mahasiswa sekaligus.
### Soal 2

soal nomor 2

```go
package main

func main() {
	fmt.Println("kode untuk soal nomor 2A")
}
```

> Output
> ![Screenshot bagian x](output/screenshot_soal2A.png)

penjelasan 


soal nomor 2

```go
package main

func main() {
	fmt.Println("kode untuk soal nomor 2B")
}
```

> Output
> ![Screenshot bagian x](output/screenshot_soal2B.png)

penjelasan 


## Referensi

1. https://en.wikipedia.org/wiki/Data_structure (diakses blablabla)
