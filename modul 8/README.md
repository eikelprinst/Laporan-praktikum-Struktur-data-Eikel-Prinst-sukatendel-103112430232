# <h1 align="center">Laporan Praktikum Modul 8 <br> Queue</h1>
<p align="center">Eikel Prinst Sukatendel - 103112430232</p>

## Dasar Teori

Queue atau antrean merupakan salah satu struktur data linear yang konsep kerjanya menyerupai antrean dalam kehidupan sehari-hari, seperti antrean saat membeli tiket atau menunggu giliran pelayanan. Pada struktur data ini berlaku prinsip First In, First Out (FIFO), yang berarti elemen yang pertama kali dimasukkan ke dalam antrean akan menjadi elemen pertama yang dikeluarkan. Oleh karena itu, proses penambahan elemen hanya dilakukan pada satu sisi antrean yang disebut Tail, sedangkan proses penghapusan atau pengambilan elemen dilakukan dari sisi lainnya yang disebut Head.

Operasi utama yang terdapat pada Queue adalah Enqueue dan Dequeue. Enqueue digunakan untuk menambahkan elemen baru ke dalam antrean dan selalu dilakukan pada bagian Tail. Sementara itu, Dequeue berfungsi untuk menghapus atau mengambil elemen dari antrean dan selalu dilakukan pada bagian Head. Selain kedua operasi tersebut, terdapat operasi pendukung seperti IsEmpty untuk mengecek apakah antrean kosong dan IsFull untuk mengetahui apakah antrean sudah penuh, terutama pada implementasi Queue berbasis array.

## Guided

### soal 1

Program C++ ini mengimplementasikan struktur data Queue menggunakan array dengan ukuran tetap. Queue bekerja berdasarkan prinsip First In, First Out (FIFO), di mana data yang pertama masuk akan menjadi data pertama yang keluar. Program menggunakan dua variabel penanda, yaitu head untuk menunjukkan elemen terdepan dan tail untuk menunjukkan elemen terakhir dalam antrean.

Operasi utama yang disediakan adalah enqueue untuk menambahkan data ke bagian belakang queue dan dequeue untuk menghapus data dari bagian depan queue. Selain itu, terdapat fungsi untuk mengecek kondisi kosong dan penuh agar operasi tidak menimbulkan error. Karena queue diimplementasikan menggunakan array statis, proses dequeue dilakukan dengan cara menggeser elemen ke depan agar posisi head tetap di indeks awal. Program ini cocok digunakan untuk memahami konsep dasar queue berbasis array secara sederhana.

```go
#include <iostream>
using namespace std;

#define MAX 5

struct Queue {
    int data[MAX];
    int head, tail;
};

// Inisialisasi queue
void buatQueue(Queue &Q) {
    Q.head = Q.tail = -1;
}

// Cek kosong
bool isEmpty(Queue Q) {
    return (Q.head == -1);
}

// Cek penuh
bool isFull(Queue Q) {
    return (Q.tail == MAX - 1);
}

// Tampilkan queue
void tampilQueue(Queue Q) {
    if (isEmpty(Q)) {
        cout << "Queue kosong\n";
    } else {
        cout << "Queue : ";
        for (int i = Q.head; i <= Q.tail; i++) {
            cout << Q.data[i] << " ";
        }
        cout << endl;
    }
}

// Enqueue
void enqueue(Queue &Q, int x) {
    if (isFull(Q)) {
        cout << "Queue penuh!\n";
        return;
    }

    if (isEmpty(Q)) {
        Q.head = Q.tail = 0;
    } else {
        Q.tail++;
    }

    Q.data[Q.tail] = x;
    cout << x << " masuk ke queue\n";
}

// Dequeue
void dequeue(Queue &Q) {
    if (isEmpty(Q)) {
        cout << "Queue kosong!\n";
        return;
    }

    cout << Q.data[Q.head] << " keluar dari queue\n";

    if (Q.head == Q.tail) {
        Q.head = Q.tail = -1;
    } else {
        for (int i = Q.head; i < Q.tail; i++) {
            Q.data[i] = Q.data[i + 1];
        }
        Q.tail--;
    }
}

// Main
int main() {
    Queue Q;
    buatQueue(Q);

    enqueue(Q, 5);
    enqueue(Q, 2);
    enqueue(Q, 7);
    tampilQueue(Q);

    dequeue(Q);
    tampilQueue(Q);

    enqueue(Q, 4);
    enqueue(Q, 9);
    tampilQueue(Q);

    dequeue(Q);
    dequeue(Q);
    tampilQueue(Q);

    return 0;
}

```

## Unguided

### Soal 1

copy paste soal nomor 1 disini

```go
#include <iostream>
using namespace std;

#define MAX 5
typedef int infotype;

struct Queue {
    infotype info[MAX];
    int head;
    int tail;
};

// inisialisasi queue kosong
void CreateQueue(Queue &Q) {
    Q.head = -1;
    Q.tail = -1;
}

// cek apakah queue kosong
bool isEmptyQueue(Queue Q) {
    return (Q.head == -1 && Q.tail == -1);
}

// cek apakah queue penuh
bool isFullQueue(Queue Q) {
    return (Q.tail == MAX - 1);
}

// operasi enqueue
void enqueue(Queue &Q, infotype x) {
    if (isFullQueue(Q)) {
        cout << "Queue penuh, data tidak dapat ditambahkan.\n";
    } else {
        if (isEmptyQueue(Q)) {
            Q.head = Q.tail = 0;
        } else {
            Q.tail++;
        }
        Q.info[Q.tail] = x;
        cout << "Data " << x << " berhasil dimasukkan ke queue.\n";
    }
}

// operasi dequeue
infotype dequeue(Queue &Q) {
    if (isEmptyQueue(Q)) {
        cout << "Queue kosong, tidak ada data yang dihapus.\n";
        return -1;
    }

    infotype x = Q.info[Q.head];

    if (Q.head == Q.tail) {
        CreateQueue(Q);
    } else {
        for (int i = Q.head; i < Q.tail; i++) {
            Q.info[i] = Q.info[i + 1];
        }
        Q.tail--;
    }

    cout << "Data " << x << " berhasil dikeluarkan dari queue.\n";
    return x;
}

// menampilkan isi queue
void printInfo(Queue Q) {
    cout << Q.head << " - " << Q.tail << "\t| ";
    if (isEmptyQueue(Q)) {
        cout << "empty queue";
    } else {
        for (int i = Q.head; i <= Q.tail; i++) {
            cout << Q.info[i] << " ";
        }
    }
    cout << endl;
}

int main() {
    Queue Q;
    CreateQueue(Q);

    cout << "-----------------------------------" << endl;
    cout << " H - T \t| Queue Info" << endl;
    cout << "-----------------------------------" << endl;

    printInfo(Q);

    enqueue(Q, 5);  printInfo(Q);
    enqueue(Q, 2);  printInfo(Q);
    enqueue(Q, 7);  printInfo(Q);

    dequeue(Q);     printInfo(Q);

    enqueue(Q, 4);  printInfo(Q);

    dequeue(Q);     printInfo(Q);
    dequeue(Q);     printInfo(Q);
    dequeue(Q);     printInfo(Q);

    return 0;
}

```

> Output
> ![Screenshot bagian x](output/screenshot_soal1.png)
> %% Untuk mencantumkan screenshot, tidak boleh ada spasi di urlnya `()`, penamaan file bebas asal gak sara dan mudah dipahami aja,, dan jangan lupa hapus komen ini yah%%

Penjelasan 
  Program di atas merupakan implementasi struktur data Queue menggunakan array statis dengan kapasitas maksimal tertentu. Queue bekerja berdasarkan prinsip First In First Out (FIFO), di mana elemen yang pertama kali masuk akan menjadi elemen pertama yang keluar. Struktur Queue memiliki dua penunjuk, yaitu head sebagai penanda elemen terdepan dan tail sebagai penanda elemen paling belakang. Ketika queue masih kosong, kedua penunjuk tersebut diinisialisasi dengan nilai -1 untuk menandakan bahwa belum ada data yang tersimpan.

### Soal 2

soal nomor 2A

```go
#include <iostream>
using namespace std;

#define MAX 5
typedef int infotype;

struct Queue {
    infotype info[MAX];
    int head;
    int tail;
};

// Inisialisasi queue kosong
void CreateQueue(Queue &Q) {
    Q.head = -1;
    Q.tail = -1;
}

// Mengecek apakah queue kosong
bool isEmptyQueue(Queue Q) {
    return (Q.head == -1 && Q.tail == -1);
}

// Mengecek apakah queue benar-benar penuh
bool isFullQueue(Queue Q) {
    return (Q.head == 0 && Q.tail == MAX - 1);
}

// Operasi enqueue (menambah data)
void enqueue(Queue &Q, infotype x) {
    if (isFullQueue(Q)) {
        cout << "Queue penuh, tidak dapat menambah data." << endl;
        return;
    }

    if (isEmptyQueue(Q)) {
        Q.head = Q.tail = 0;
        Q.info[Q.tail] = x;
    } else {
        if (Q.tail == MAX - 1) {
            // Mekanisme geser (penuh semu)
            int indeksBaru = 0;
            for (int i = Q.head; i <= Q.tail; i++) {
                Q.info[indeksBaru++] = Q.info[i];
            }
            Q.head = 0;
            Q.tail = indeksBaru - 1;
        }
        Q.tail++;
        Q.info[Q.tail] = x;
    }

    cout << "Data " << x << " berhasil ditambahkan." << endl;
}

// Operasi dequeue (menghapus data)
infotype dequeue(Queue &Q) {
    if (isEmptyQueue(Q)) {
        cout << "Queue kosong, tidak ada data yang dihapus." << endl;
        return -1;
    }

    infotype x = Q.info[Q.head];

    if (Q.head == Q.tail) {
        CreateQueue(Q);
    } else {
        Q.head++;
    }

    cout << "Data " << x << " berhasil dikeluarkan." << endl;
    return x;
}

// Menampilkan isi queue
void printInfo(Queue Q) {
    cout << Q.head << " - " << Q.tail << "\t| ";
    if (isEmptyQueue(Q)) {
        cout << "empty queue";
    } else {
        for (int i = Q.head; i <= Q.tail; i++) {
            cout << Q.info[i] << " ";
        }
    }
    cout << endl;
}

int main() {
    Queue Q;
    CreateQueue(Q);

    cout << "-----------------------------------" << endl;
    cout << " H - T \t| Queue Info" << endl;
    cout << "-----------------------------------" << endl;

    printInfo(Q);

    enqueue(Q, 5); printInfo(Q);
    enqueue(Q, 2); printInfo(Q);
    enqueue(Q, 7); printInfo(Q);

    dequeue(Q);    printInfo(Q);

    enqueue(Q, 4); printInfo(Q);

    dequeue(Q);    printInfo(Q);
    dequeue(Q);    printInfo(Q);
    dequeue(Q);    printInfo(Q);

    return 0;
}

```

> Output
> ![Screenshot bagian x](output/screenshot_soal2A.png)

penjelasan kode

Operasi utama dalam program ini adalah enqueue dan dequeue. Operasi enqueue digunakan untuk menambahkan elemen ke bagian belakang queue. Jika posisi tail sudah berada di indeks terakhir array tetapi masih tersedia ruang di depan (head tidak berada di indeks 0), maka dilakukan mekanisme penggeseran elemen (penuh semu) agar data dapat ditambahkan tanpa membuang ruang kosong. Sementara itu, operasi dequeue hanya memindahkan penunjuk head ke depan tanpa perlu menggeser seluruh elemen array, sehingga lebih efisien. Fungsi printInfo digunakan untuk menampilkan kondisi queue secara visual, termasuk posisi head, tail, dan isi data yang tersimpan.

soal nomor 2B

```go
#include <iostream>
using namespace std;

#define MAX 5
typedef int infotype;

struct Queue {
    infotype info[MAX];
    int head;
    int tail;
};

// Membuat queue kosong
void CreateQueue(Queue &Q) {
    Q.head = -1;
    Q.tail = -1;
}

// Mengecek apakah queue kosong
bool isEmptyQueue(Queue Q) {
    return (Q.head == -1 && Q.tail == -1);
}

// Mengecek apakah queue penuh (Circular Queue)
bool isFullQueue(Queue Q) {
    return ((Q.tail + 1) % MAX == Q.head);
}

// Menambahkan elemen ke queue (enqueue)
void enqueue(Queue &Q, infotype x) {
    if (isFullQueue(Q)) {
        cout << "Queue penuh, data tidak dapat ditambahkan." << endl;
        return;
    }

    if (isEmptyQueue(Q)) {
        Q.head = Q.tail = 0;
    } else {
        Q.tail = (Q.tail + 1) % MAX;
    }

    Q.info[Q.tail] = x;
    cout << "Data " << x << " berhasil ditambahkan." << endl;
}

// Menghapus elemen dari queue (dequeue)
infotype dequeue(Queue &Q) {
    if (isEmptyQueue(Q)) {
        cout << "Queue kosong, tidak ada data yang dihapus." << endl;
        return -1;
    }

    infotype x = Q.info[Q.head];

    if (Q.head == Q.tail) {
        CreateQueue(Q);
    } else {
        Q.head = (Q.head + 1) % MAX;
    }

    cout << "Data " << x << " berhasil dikeluarkan." << endl;
    return x;
}

// Menampilkan isi queue
void printInfo(Queue Q) {
    cout << Q.head << " - " << Q.tail << "\t| ";

    if (isEmptyQueue(Q)) {
        cout << "empty queue";
    } else {
        int i = Q.head;
        while (true) {
            cout << Q.info[i] << " ";
            if (i == Q.tail) break;
            i = (i + 1) % MAX;
        }
    }
    cout << endl;
}

int main() {
    Queue Q;
    CreateQueue(Q);

    cout << "-----------------------------------" << endl;
    cout << " H - T \t| Queue Info" << endl;
    cout << "-----------------------------------" << endl;

    printInfo(Q);

    enqueue(Q, 5); printInfo(Q);
    enqueue(Q, 2); printInfo(Q);
    enqueue(Q, 7); printInfo(Q);

    dequeue(Q);    printInfo(Q);

    enqueue(Q, 4); printInfo(Q);

    dequeue(Q);    printInfo(Q);
    dequeue(Q);    printInfo(Q);
    dequeue(Q);    printInfo(Q);

    return 0;
}

```

> Output
> ![Screenshot bagian x](output/screenshot_soal2B.png)

Operasi enqueue pada program ini dilakukan dengan menggeser penunjuk tail secara melingkar menggunakan operasi modulo, tanpa perlu menggeser seluruh isi array. Sementara itu, operasi dequeue hanya memindahkan penunjuk head ke posisi berikutnya secara melingkar, sehingga proses penghapusan data menjadi lebih efisien. Fungsi printInfo dirancang khusus untuk menampilkan isi queue dengan cara menelusuri elemen mulai dari head hingga tail secara melingkar. Dengan pendekatan ini, circular queue mampu mengatasi masalah “penuh semu” yang sering terjadi pada implementasi queue array biasa.

## Referensi

1.Main, M. (2011). Data structures and other objects using Java (4th ed.). Addison-Wesley.
2.Mishra, R. K., & Singh, R. (2015). Research paper on queues. International Journal of Innovative Research in Technology (IJIRT), 1(8), 65-68.
