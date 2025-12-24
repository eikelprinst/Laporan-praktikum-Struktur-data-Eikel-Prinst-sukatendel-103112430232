# <h1 align="center">Laporan Praktikum Modul 13 <br> MULTI LINKEDLIST</h1>
<p align="center">EIKEL PRINST SUKATENDEL - 103112430232</p>

## Dasar Teori
 Struktur ini terdiri dari list induk dan list anak, di mana setiap node pada list induk memiliki pointer tambahan yang mengarah ke kumpulan node anak, sehingga membentuk relasi satu ke banyak. Akibatnya, setiap operasi pada data anak harus diawali dengan pencarian node induk yang sesuai agar manipulasi data dapat dilakukan secara tepat.

Selain itu, modul ini juga memperkenalkan variasi linked list lainnya seperti Circular Linked List, yaitu linked list dengan struktur melingkar di mana node terakhir menunjuk kembali ke node pertama. Struktur ini sering digunakan pada sistem yang membutuhkan proses berulang secara terus-menerus, seperti antrian melingkar atau penjadwalan berbasis siklus.

## Guided

### soal 1

```go
#include <iostream>
#include <string>
using namespace std;

struct Child {
    string data;
    Child* next;
};

struct Parent {
    string data;
    Child* child;
    Parent* next;
};

Parent* newParent(string x) {
    return new Parent{x, nullptr, nullptr};
}

Child* newChild(string x) {
    return new Child{x, nullptr};
}

void addParent(Parent*& head, string x) {
    Parent* p = newParent(x);
    if (!head) head = p;
    else {
        Parent* temp = head;
        while (temp->next) temp = temp->next;
        temp->next = p;
    }
}

void addChild(Parent* head, string parent, string child) {
    while (head && head->data != parent)
        head = head->next;

    if (head) {
        Child* c = newChild(child);
        if (!head->child) head->child = c;
        else {
            Child* temp = head->child;
            while (temp->next) temp = temp->next;
            temp->next = c;
        }
    }
}

void display(Parent* head) {
    while (head) {
        cout << head->data;
        for (Child* c = head->child; c; c = c->next)
            cout << " -> " << c->data;
        cout << endl;
        head = head->next;
    }
}

int main() {
    Parent* list = nullptr;

    addParent(list, "Parent 1");
    addParent(list, "Parent 2");

    addChild(list, "Parent 1", "Child A");
    addChild(list, "Parent 1", "Child B");
    addChild(list, "Parent 2", "Child C");

    display(list);
    return 0;
}

```

> Output
> ![Screenshot bagian x](output/screenshot_soal1.png)
> %% Untuk mencantumkan screenshot, tidak boleh ada spasi di urlnya `()`, penamaan file bebas asal gak sara dan mudah dipahami aja,, dan jangan lupa hapus komen ini yah%%

Penjelasan

Program ini menerapkan Multi Linked List, yaitu struktur data yang menghubungkan beberapa linked list dalam hubungan bertingkat. Setiap node parent memiliki dua pointer, satu untuk menunjuk ke parent berikutnya dan satu lagi menuju linked list child yang dimilikinya. Struktur ini memungkinkan satu parent memiliki banyak child, sehingga cocok digunakan untuk merepresentasikan hubungan satu-ke-banyak, seperti kategori dan subkategori.

Proses penambahan child tidak dilakukan secara langsung, melainkan diawali dengan pencarian parent yang sesuai. Setelah parent ditemukan, child baru akan ditambahkan ke akhir list anak milik parent tersebut. Fungsi display digunakan untuk menampilkan seluruh struktur data secara berurutan, dimulai dari parent lalu diikuti semua child yang terhubung, sehingga hubungan antar data dapat terlihat dengan jelas dan terstruktur.

## Unguided

### Soal 1


```go
#include <iostream>
#include <string>
using namespace std;

struct Child {
    string data;
    Child* next;
};

struct Parent {
    string data;
    Child* child;
    Parent* next;
};

Parent* createParent(string x) {
    return new Parent{x, nullptr, nullptr};
}

Child* createChild(string x) {
    return new Child{x, nullptr};
}

void insertParent(Parent*& head, string x) {
    Parent* p = createParent(x);
    if (!head) head = p;
    else {
        Parent* temp = head;
        while (temp->next) temp = temp->next;
        temp->next = p;
    }
}

void insertChild(Parent* head, string parent, string child) {
    while (head && head->data != parent)
        head = head->next;

    if (head) {
        Child* c = createChild(child);
        if (!head->child) head->child = c;
        else {
            Child* temp = head->child;
            while (temp->next) temp = temp->next;
            temp->next = c;
        }
    }
}

void printAll(Parent* head) {
    while (head) {
        cout << head->data;
        for (Child* c = head->child; c; c = c->next)
            cout << " -> " << c->data;
        cout << endl;
        head = head->next;
    }
}

int main() {
    Parent* list = nullptr;

    insertParent(list, "Parent 1");
    insertParent(list, "Parent 2");

    insertChild(list, "Parent 1", "Child A");
    insertChild(list, "Parent 1", "Child B");
    insertChild(list, "Parent 2", "Child C");

    printAll(list);
    return 0;
}

```

> Output
> ![Screenshot bagian x](output/screenshot_soal1.png)
> %% Untuk mencantumkan screenshot, tidak boleh ada spasi di urlnya `()`, penamaan file bebas asal gak sara dan mudah dipahami aja,, dan jangan lupa hapus komen ini yah%%

Penjelasan 
  Program ini merupakan implementasi Multi Linked List, yaitu struktur data yang terdiri dari dua tingkat linked list: parent dan child. Setiap node parent menyimpan data serta pointer ke node parent berikutnya dan pointer ke awal linked list child yang dimilikinya. Dengan struktur ini, satu parent dapat memiliki banyak child, sehingga cocok untuk merepresentasikan hubungan satu ke banyak.

Penambahan child dilakukan dengan cara mencari parent yang sesuai terlebih dahulu, kemudian menyisipkan child ke akhir list anak milik parent tersebut. Fungsi printAll digunakan untuk menampilkan seluruh data secara terstruktur, dimulai dari parent lalu diikuti seluruh child yang terhubung
### Soal 2

soal nomor 2

```go
#include <iostream>
#include <string>
#include <iomanip>
using namespace std;

struct Data {
    string nama, nim;
    char jk;
    float ipk;
};

struct Node {
    Data info;
    Node* next;
};

struct List {
    Node* first;
};

Node* createNode(string nama, string nim, char jk, float ipk) {
    return new Node{{nama, nim, jk, ipk}, nullptr};
}

void createList(List& L) {
    L.first = nullptr;
}

void insertFirst(List& L, Node* P) {
    if (!L.first) {
        L.first = P;
        P->next = P;
    } else {
        Node* last = L.first;
        while (last->next != L.first)
            last = last->next;
        P->next = L.first;
        last->next = P;
        L.first = P;
    }
}

void insertLast(List& L, Node* P) {
    if (!L.first) insertFirst(L, P);
    else {
        Node* last = L.first;
        while (last->next != L.first)
            last = last->next;
        last->next = P;
        P->next = L.first;
    }
}

Node* findNode(List L, string nim) {
    if (!L.first) return nullptr;
    Node* P = L.first;
    do {
        if (P->info.nim == nim) return P;
        P = P->next;
    } while (P != L.first);
    return nullptr;
}

void insertAfter(Node* prec, Node* P) {
    if (prec) {
        P->next = prec->next;
        prec->next = P;
    }
}

void printList(List L) {
    if (!L.first) {
        cout << "List kosong\n";
        return;
    }

    cout << left << setw(12) << "Nama"
         << setw(10) << "NIM"
         << setw(6) << "JK"
         << setw(6) << "IPK" << endl;
    cout << "---------------------------------\n";

    Node* P = L.first;
    do {
        cout << left << setw(12) << P->info.nama
             << setw(10) << P->info.nim
             << setw(6) << P->info.jk
             << setw(6) << P->info.ipk << endl;
        P = P->next;
    } while (P != L.first);
}

int main() {
    List L;
    createList(L);

    insertFirst(L, createNode("Ali", "01", 'L', 3.3));
    insertFirst(L, createNode("Danu", "04", 'L', 4.0));
    insertLast(L,  createNode("Fahmi", "06", 'L', 3.45));
    insertLast(L,  createNode("Bobi", "02", 'L', 3.71));
    insertLast(L,  createNode("Gita", "07", 'P', 3.75));

    cout << "[Keadaan Awal]\n";
    printList(L);

    insertAfter(findNode(L, "07"), createNode("Cindi", "03", 'P', 3.5));
    insertAfter(findNode(L, "02"), createNode("Hilmi", "08", 'L', 3.3));
    insertAfter(findNode(L, "04"), createNode("Eli", "05", 'P', 3.4));

    cout << "\n[Hasil Akhir]\n";
    printList(L);

    return 0;
}

```

> Output
> ![Screenshot bagian x](output/screenshot_soal2.png)

penjelasan 
  Program ini mengimplementasikan Circular Singly Linked List untuk menyimpan data mahasiswa. Setiap node berisi informasi mahasiswa (nama, NIM, jenis kelamin, dan IPK) serta pointer next yang menghubungkan node ke node berikutnya secara melingkar, di mana node terakhir akan menunjuk kembali ke node pertama. Struktur ini memungkinkan proses penelusuran data dilakukan secara terus-menerus tanpa batas akhir.

Operasi utama yang disediakan meliputi insert di awal, insert di akhir, insert setelah node tertentu, serta pencarian berdasarkan NIM. Proses pencarian dilakukan dengan menelusuri list secara melingkar hingga kembali ke node awal


## Referensi

1.Laboratorium Informatika. (2025). Modul 13: Multi Linked List. Fakultas Informatika, Telkom University.
2.Frieyadie. (2016). Penerapan struktur data senarai berantai ganda (doubly linked list) untuk pembuatan sistem informasi rekam medis. Jurnal TECHNO Nusa Mandiri, 13(2), 108–114. https://doi.org/10.33480/techno.v13i2.152
