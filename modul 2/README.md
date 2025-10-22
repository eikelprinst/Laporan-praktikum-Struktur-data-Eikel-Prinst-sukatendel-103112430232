# <h1 align="center">Laporan Praktikum Modul 2 <br> Pengenalan bahasa c++(Bagian Kedua)</h1>
<p align="center">EIKEL PRINST SUKATENDEL - 103112430232</p>

## Dasar Teori

Array merupakan kumpulan data dengan nama yang sama dan setiap elemen bertipe data sama.
Untuk mengakses setiap komponen / elemen array berdasarkan indeks dari setiap elemen.

Array Satu Dimensi
Adalah array yang hanya terdiri dari satu larik data saja. 

Cara pendeklarasian array satu dimensi:

tipe_data nama_var[ukuran]
Keterangan:

tipe_data → menyatakan jenis elemen array (int, char, float, dll).

ukuran → menyatakan jumlah maksimum array.
Contoh:

int nilai[10];

Menyatakan bahwa array nilai mengandung 10 elemen dan bertipe integer.
Dalam C++ data array disimpan dalam memori pada lokasi yang berurutan. Elemen pertama memiliki
indeks 0 dan selemen selanjutnya memiliki indeks 1 dan seterusnya. Jadi jika terdapat array dengan 5
elemen maka elemen pertama memiliki indeks 0 dan elemen terakhir memiliki indeks 4.

## Guided

### soal 1

aku mengerjakan fungsi tukar, menukar dua nilai variabel menggunakan pointer (call by address)

## Unguided

### Soal 1

copy paste soal nomor 1 disini

```go
#include <iostream>
using namespace std;

int main() {
    int m[3][3] = {{1,2,3},{4,5,6},{7,8,9}}, t[3][3];

    cout << "Matriks Awal:\n";
    for (int i=0;i<3;i++) {
        for (int j=0;j<3;j++) {
            cout << m[i][j] << " ";
            t[j][i] = m[i][j];
        }
        cout << endl;
    }

    cout << "\nMatriks Hasil Transpose:\n";
    for (int i=0;i<3;i++) {
        for (int j=0;j<3;j++)
            cout << t[i][j] << " ";
        cout << endl;
    }
}

```

> Output
> ![Screenshot bagian 1](output/screenshot_soal1.png)
> %% Untuk mencantumkan screenshot, tidak boleh ada spasi di urlnya `()`, penamaan file bebas asal gak sara dan mudah dipahami aja,, dan jangan lupa hapus komen ini yah%%

Fungsi Menukar baris menjadi kolom.

Proses: t[j][i] = m[i][j];

Kegunaan Untuk operasi matematika atau pengolahan data matriks.

### Soal 2

soal nomor 2A

```go
#include <iostream>
using namespace std;

void kuadratkan(int &x) { x *= x; }

int main() {
    int n = 5;
    cout << "Nilai awal: " << n << endl;
    kuadratkan(n);
    cout << "Nilai setelah dikuadratkan: " << n << endl;
}
```

> Output
> ![Screenshot bagian x](output/screenshot_soal2A.png)

Fungsi Mengubah nilai variabel secara langsung lewat referensi.

Proses: int &x → variabel asli ikut berubah.

Kegunaan: Efisien saat ingin memodifikasi nilai tanpa mengembalikannya.


## Referensi

1. https://en.wikipedia.org/wiki/Data_structure (diakses blablabla)
