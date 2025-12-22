# <h1 align="center">Laporan Praktikum Modul 7 <br> Stack</h1>
<p align="center">Eikel Prinst Sukatendel - 103112430232</p>

## Dasar Teori

Konsep Dasar Stack

Stack adalah struktur data yang bekerja dengan prinsip Last In First Out (LIFO), artinya data yang terakhir dimasukkan adalah data yang pertama dikeluarkan. Stack dapat dianalogikan seperti tumpukan buku, di mana buku yang paling atas akan diambil terlebih dahulu. Pada struktur Stack, akses data hanya dilakukan melalui satu sisi saja, yaitu bagian atas yang disebut Top. Stack dapat diimplementasikan menggunakan linked list (pointer) maupun array (tabel).

Operasi utama pada Stack terdiri dari Push dan Pop. Push adalah operasi untuk menambahkan data ke bagian atas Stack, sedangkan Pop adalah operasi untuk mengambil atau menghapus data dari bagian atas Stack. Pada implementasi berbasis pointer, Push dan Pop mirip dengan operasi insert first dan delete first pada linked list. Sementara itu, pada implementasi berbasis array, operasi dilakukan dengan menggeser indeks Top ke atas atau ke bawah.

## Guided

### soal 1

```go
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

// Cek apakah stack kosong
bool isEmpty(Node* top) {
    return top == nullptr;
}

// Push data ke stack
void push(Node*& top, int data) {
    Node* newNode = new Node;
    newNode->data = data;
    newNode->next = top;
    top = newNode;
}

// Pop data dari stack
int pop(Node*& top) {
    if (isEmpty(top)) {
        cout << "Stack kosong, tidak bisa pop!" << endl;
        return -1;
    }

    int dataPop = top->data;
    Node* temp = top;
    top = top->next;
    delete temp;

    return dataPop;
}

// Menampilkan isi stack
void show(Node* top) {
    if (isEmpty(top)) {
        cout << "Stack kosong." << endl;
        return;
    }

    cout << "TOP -> ";
    while (top != nullptr) {
        cout << top->data << " -> ";
        top = top->next;
    }
    cout << "NULL" << endl;
}

int main() {
    Node* stack = nullptr;

    push(stack, 10);
    push(stack, 20);
    push(stack, 30);

    cout << "Isi Stack:" << endl;
    show(stack);

    cout << "Pop data: " << pop(stack) << endl;

    cout << "Sisa Stack:" << endl;
    show(stack);

    return 0;
}

```

> Output
> ![Screenshot bagian x](output/screenshot_soal1.png)
> %% Untuk mencantumkan screenshot, tidak boleh ada spasi di urlnya `()`, penamaan file bebas asal gak sara dan mudah dipahami aja,, dan jangan lupa hapus komen ini yah%%

Penjelasan
  Program ini merupakan implementasi struktur data Stack menggunakan Linked List, di mana setiap elemen disimpan dalam sebuah node yang saling terhubung. Stack bekerja dengan prinsip Last In First Out (LIFO), sehingga data yang terakhir dimasukkan akan menjadi data pertama yang dikeluarkan. Pointer top digunakan untuk menunjuk elemen teratas dari stack, yang menjadi satu-satunya akses untuk operasi push dan pop.

Operasi push dilakukan dengan membuat node baru dan meletakkannya di posisi paling atas stack, sedangkan operasi pop mengambil data dari node teratas lalu menghapus node tersebut dari memori. Fungsi show digunakan untuk menampilkan isi stack dari atas ke bawah. Implementasi stack berbasis linked list ini bersifat dinamis karena tidak dibatasi ukuran tertentu dan memanfaatkan alokasi memori saat runtime.

## Unguided

### Soal 1


```go
#include <iostream>
using namespace std;

#define MAX_SIZE 20
typedef int infotype;

struct Stack {
    infotype info[MAX_SIZE];
    int top;
};

// Inisialisasi stack
void createStack(Stack &S) {
    S.top = -1;
}

// Cek stack kosong
bool isEmpty(Stack S) {
    return S.top == -1;
}

// Cek stack penuh
bool isFull(Stack S) {
    return S.top == MAX_SIZE - 1;
}

// Push data ke stack
void push(Stack &S, infotype X) {
    if (isFull(S)) {
        cout << "Stack penuh, push gagal." << endl;
        return;
    }
    S.top++;
    S.info[S.top] = X;
}

// Pop data dari stack
infotype pop(Stack &S) {
    if (isEmpty(S)) {
        cout << "Stack kosong, pop gagal." << endl;
        return -1;
    }
    return S.info[S.top--];
}

// Menampilkan isi stack
void printInfo(Stack S) {
    if (isEmpty(S)) {
        cout << "[TOP] Stack kosong." << endl;
        return;
    }

    cout << "[TOP] ";
    for (int i = S.top; i >= 0; i--) {
        cout << S.info[i] << " ";
    }
    cout << endl;
}

// Membalik isi stack
void balikStack(Stack &S) {
    Stack temp;
    createStack(temp);

    while (!isEmpty(S)) {
        push(temp, pop(S));
    }

    while (!isEmpty(temp)) {
        push(S, pop(temp));
    }
}

int main() {
    Stack S;
    createStack(S);

    push(S, 3);
    push(S, 4);
    push(S, 8);
    pop(S);
    push(S, 2);
    push(S, 3);
    pop(S);
    push(S, 9);

    cout << "Isi Stack:" << endl;
    printInfo(S);

    cout << "Stack setelah dibalik:" << endl;
    balikStack(S);
    printInfo(S);

    return 0;
}

```

> Output
> ![Screenshot bagian x](output/screenshot_soal1.png)
> %% Untuk mencantumkan screenshot, tidak boleh ada spasi di urlnya `()`, penamaan file bebas asal gak sara dan mudah dipahami aja,, dan jangan lupa hapus komen ini yah%%

Penjelasan
Program ini merupakan implementasi struktur data Stack menggunakan array, di mana mekanisme kerjanya mengikuti prinsip Last In First Out (LIFO). Stack disimpan dalam array dengan batas maksimum tertentu, dan variabel top digunakan untuk menandai posisi elemen teratas. Operasi dasar yang disediakan meliputi push untuk menambahkan data ke stack dan pop untuk menghapus data dari stack, dengan pengecekan kondisi penuh dan kosong agar program berjalan aman.
### Soal 2

soal nomor 2

```go
#include <iostream>
using namespace std;

#define MAX_SIZE 20
typedef int infotype;

// ================= STACK =================
struct Stack {
    infotype info[MAX_SIZE];
    int top;
};

void createStack(Stack &S) {
    S.top = -1;
}

bool isEmptyStack(Stack S) {
    return S.top == -1;
}

bool isFullStack(Stack S) {
    return S.top == MAX_SIZE - 1;
}

void push(Stack &S, infotype X) {
    if (isFullStack(S)) {
        cout << "Stack penuh, push gagal." << endl;
        return;
    }
    S.info[++S.top] = X;
}

infotype pop(Stack &S) {
    if (isEmptyStack(S)) {
        cout << "Stack kosong, pop gagal." << endl;
        return -1;
    }
    return S.info[S.top--];
}

void printInfo(Stack S) {
    if (isEmptyStack(S)) {
        cout << "[TOP] Stack kosong." << endl;
        return;
    }
    cout << "[TOP] ";
    for (int i = S.top; i >= 0; i--) {
        cout << S.info[i] << " ";
    }
    cout << endl;
}

// ================= QUEUE =================
struct Queue {
    infotype info[MAX_SIZE];
    int head;
    int tail;
};

void createQueue(Queue &Q) {
    Q.head = 0;
    Q.tail = -1;
}

bool isEmptyQueue(Queue Q) {
    return Q.tail < Q.head;
}

bool isFullQueue(Queue Q) {
    return Q.tail == MAX_SIZE - 1;
}

void enqueue(Queue &Q, infotype X) {
    if (isFullQueue(Q)) return;
    Q.info[++Q.tail] = X;
}

infotype dequeue(Queue &Q) {
    if (isEmptyQueue(Q)) return -1;
    infotype X = Q.info[Q.head++];
    if (isEmptyQueue(Q)) createQueue(Q);
    return X;
}

// ================= OPERASI TAMBAHAN =================

// Membalik isi stack menggunakan queue
void balikStack(Stack &S) {
    Queue Q;
    createQueue(Q);

    while (!isEmptyStack(S)) {
        enqueue(Q, pop(S));
    }
    while (!isEmptyQueue(Q)) {
        push(S, dequeue(Q));
    }
}

// Push data secara terurut naik
void pushAscending(Stack &S, infotype X) {
    Stack Temp;
    createStack(Temp);

    while (!isEmptyStack(S) && S.info[S.top] > X) {
        push(Temp, pop(S));
    }

    push(S, X);

    while (!isEmptyStack(Temp)) {
        push(S, pop(Temp));
    }
}

// ================= MAIN =================
int main() {
    Stack S;
    createStack(S);

    pushAscending(S, 3);
    pushAscending(S, 4);
    pushAscending(S, 8);
    pushAscending(S, 2);
    pushAscending(S, 3);
    pushAscending(S, 9);

    cout << "Isi Stack:" << endl;
    printInfo(S);

    cout << "Stack setelah dibalik:" << endl;
    balikStack(S);
    printInfo(S);

    return 0;
}

```

> Output
> ![Screenshot bagian x](output/screenshot_soal2A.png)

penjelasan kode


soal nomor 3

```go
 #include <iostream>

using namespace std;

#define MAX_SIZE 20

typedef char infotype;

struct Stack {
    infotype info[MAX_SIZE];
    int top;
};

void createStack(Stack &S) {
    S.top = -1;
}

bool isEmpty(Stack S) {
    return S.top == -1;
}

bool isFull(Stack S) {
    return S.top == (MAX_SIZE - 1);
}

void push(Stack &S, infotype X) {
    if (isFull(S)) {
        cout << "Error: Stack penuh, tidak bisa PUSH." << endl;
        return;
    }
    S.top++;
    S.info[S.top] = X;
}

infotype pop(Stack &S) {
    if (isEmpty(S)) {
        return '\0'; 
    }
    infotype X = S.info[S.top];
    S.top--;
    return X;
}

void printInfo(Stack S) {
    if (isEmpty(S)) {
        cout << "[TOP] Stack kosong." << endl;
        return;
    }
    cout << "[TOP] ";
    for (int i = S.top; i >= 0; i--) {
        cout << S.info[i] << " ";
    }
    cout << endl;
}

struct Queue {
    infotype info[MAX_SIZE];
    int head;
    int tail;
};

void createQueue(Queue &Q) {
    Q.head = 0;
    Q.tail = -1;
}

bool isEmpty(Queue Q) {
    return Q.tail < Q.head;
}

bool isFull(Queue Q) {
    return Q.tail == (MAX_SIZE - 1);
}

void enqueue(Queue &Q, infotype X) {
    if (isFull(Q)) {
        cout << "Error: Queue penuh." << endl;
        return;
    }
    Q.tail++;
    Q.info[Q.tail] = X;
}

infotype dequeue(Queue &Q) {
    if (isEmpty(Q)) {
        return '\0';
    }
    infotype X = Q.info[Q.head];
    Q.head++;
    if (isEmpty(Q)) {
        createQueue(Q);
    }
    return X;
}

void balikStack(Stack &S) {
    Queue TempQ;
    createQueue(TempQ);

    while (!isEmpty(S)) {
        enqueue(TempQ, pop(S));
    }

    while (!isEmpty(TempQ)) {
        push(S, dequeue(TempQ));
    }
}

void pushAscending(Stack &S, infotype X) {
    Stack Temp;
    createStack(Temp);

    while (!isEmpty(S) && S.info[S.top] > X) {
        push(Temp, pop(S));
    }

    push(S, X);

    while (!isEmpty(Temp)) {
        push(S, pop(Temp));
    }
}


/**
 * @brief 
 */

void getInputStream(Stack &S) {
    cout << "";
    char ch;
    
    ch = cin.get();

    while (ch != '\n') {
        if (!isFull(S)) {
            push(S, ch);
        } else {
            cout << "\nStack penuh, input dihentikan." << endl;
            break; 
        }
        ch = cin.get();
    }
}

int main() {
    cout << "Hello world!" << endl;
    Stack S;
    createStack(S);
    getInputStream(S); 
    printInfo(S);
    cout << "balik stack" << endl;
    balikStack(S); 
    printInfo(S);
    return 0;
}
```

> Output
> ![Screenshot bagian x](output/screenshot_soal2B.png)

penjelasan
  Program ini mengimplementasikan Stack dan Queue berbasis array dengan tipe data char. Stack bekerja menggunakan prinsip LIFO (Last In First Out) dan memiliki operasi dasar seperti push, pop, pengecekan kosong dan penuh, serta fungsi untuk menampilkan isi Stack dari posisi TOP. Queue digunakan sebagai struktur bantu dengan prinsip FIFO (First In First Out).

## Referensi

1. Guna, L. A. (2022). Implementasi Prosedur dan Fungsi Dalam Bahasa Pemrograman Python. Jurnal Portal Data, 2(1). Diakses melalui https://ejurnal-bpptik.kominfo.go.id/index.php/jpd/article/view/118.
2. Ma’arif, A. (2021). Dasar pemrograman bahasa C++. Universitas Ahmad Dahlan
