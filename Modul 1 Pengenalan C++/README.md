# <h1 align="center">Laporan Praktikum Modul X <br> Pengenalan C++</h1>
<p align="center">EIKEL PRINST SUKATENDEL - 103112430232</p>

## Dasar Teori

Dalam pengenalan bahasa C++ ini, dapat diketahui bahwasanya yang dimana kita dapat mengerti dalam fungsi input data yang dimana kita bisa membantu memecahkan program yang lebih kompleks dan efisien.
Ada beberapa contoh struktur data yang memiliki fungsi masing-masing
1.<iostream>: memberikan akses ke fungsi input dan output dalam C++
2.using namespace std :  bagian ini disebut deklarasi yang memberi tahu program untuk menggunakan namespace std yang berisi banyak fungsi dan objek standar.
3.int main() : bagian ini disebut deklarasi fungsi utama (main) yang merupakan pintu masuk eksekusi untuk program C++.

ini adalah bagian dasar dari pengertian struktur data


## Unguided

### soal 1

aku mengerjakan latihan menerima input-an dua buah yang bertipe float, kemudian memberikan output-an hasil penjumlahan, pengurangan, perkalian dan pembagian dari dua bilangan. dalam proses pembuatan C++, dimana ada terdapat dua bilangan dan saya pisah menjadi X dan Y. Yang dimana X adalah bilangan pertama sedangkan Y adalah bialangan kedua dan dijadikan penyatuan di antara dua bilangan. dalam penggabungan dua bilangan untuk melihat hasil outputnya itu menggunakan float.

## Unguided

### Soal 1

hasil 

```go
#include <iostream>
using namespace std;

int main(){
    float x, y;
    cout<< " masukkan bil pertama: ";
    cin>> x;
    cout<< " masukkan bil kedua: ";
    cin>> y;

    cout<< "Penjumlahan: " << x + y<< endl;
    cout<< "Pengurangan: " << x - y<< endl;
    cout<< "perkalian: " << x * y<< endl;
    if(y !=0)
        cout<< "Pembagian: "<< x / y<<endl;
    else
        cout<< "Pembagian tidak bisa dilakukan (Pembagi = 0)" << endl;

    return 0;
}
```

> Output
> ![Screenshot bagian x](output/)
> %% Untuk mencantumkan screenshot, tidak boleh ada spasi di urlnya `()`, penamaan file bebas asal gak sara dan mudah dipahami aja,, dan jangan lupa hapus komen ini yah%%

Penjelasan ttg kode kalian disini

### Soal 2

soal nomor 2A

```go
package main

func main() {
	fmt.Println("kode untuk soal nomor 2A")
}
```

> Output
> ![Screenshot bagian x](output/screenshot_soal2A.png)

penjelasan kode

Kalau adalanjutan di lanjut disini aja

soal nomor 2B

```go
package main

func main() {
	fmt.Println("kode untuk soal nomor 2B")
}
```

> Output
> ![Screenshot bagian x](output/screenshot_soal2B.png)

penjelasan bedanya sesuai soal

## Referensi

1. https://en.wikipedia.org/wiki/Data_structure (diakses blablabla)
