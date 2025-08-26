## Daftar Isi
- [Perulangan](#perulangan)
  - [Perulangan While](#perulangan-while)
  - [Perulangan Do-While](#perulangan-do-while)
  - [Perulangan For](#perulangan-for)
  - [Perulangan/Percabangan Bersarang (Nested)](#perulanganpercabangan-bersarang-nested)
- [Break and Continue](#break-and-continue)
  - [Break](#break)
  - [Continue](#continue)
- [Infinite Loop](#infinite-loop)
- [Array](#array)
  - [Pengenalan Array](#pengenalan-array)
  - [Deklarasi Array](#deklarasi-array)
  - [Inisialisasi Array](#inisialisasi-array)
  - [Mengakses Array](#mengakses-array)
  - [Dimensi Array](#dimensi-array)
    - [Array Satu Dimensi](#array-satu-dimensi)
    - [Array Multidimensi](#array-multidimensi)
- [String](#string)
  - [Pengenalan String](#pengenalan-string)
  - [Representasi String](#representasi-string)
  - [Fungsi-Fungsi String](#fungsi-fungsi-string)
    - [Fungsi `strcpy`](#fungsi-strcpy)
    - [Fungsi `strcat`](#fungsi-strcat)
    - [Fungsi `strcmp`](#fungsi-strcmp)
    - [Fungsi `strlen`](#fungsi-strlen)
- [Latihan Soal](#latihan-soal)
    - [Soal 1](#soal-1)
    - [Soal 2](#soal-2)
    - [Soal 3](#soal-3)
    - [Soal 4](#soal-4)
    - [Soal 5](#soal-5)
    - [Soal 6](#soal-6)
# Perulangan
Perulangan atau _looping_ memungkinkan kita untuk mengeksekusi potongan kode berulang-ulang hingga mencapai suatu kondisi. Ada 3 jenis perulangan dalam bahasa C, yaitu `while`, `do - while`, dan `for`.
## Perulangan While
Perulangan `while` adalah bentuk perulangan yang paling sederhana. Sintaksnya adalah sebagai berikut.
```c
//initial value misal, i = 0
while (<Ekspresi/Kondisi>) {
    // Potongan kode yang ingin dieksekusi
    .
    .
    .
    // increment/decrement misalnya, i++
}
```
Cara kerja perulangan `while` mirip dengan `if`. Jika pada **if** potongan kode akan dieksekusi **sekali saja** apabila ekspresi/kondisi bernilai **TRUE**, pada **while** potongan kode akan **terus dieksekusi** hingga ekspresi/kondisi menghasilkan **FALSE**.
Contoh
```c
#include <stdio.h>
int main()
{
    int i = 0;
    while (i < 10)
    {
        printf("Hello World! ke-%d \n",i);
        i++;
    }
    return 0;
}
```
Sehingga pada contoh di atas:
- Pada awalnya, **variabel `i`** bernilai 0. 
- Sequence selanjutnya adalah `while`, dan i bernilai kurang dari 10 (**TRUE**), maka kode didalam `while` akan dijalankan, yakni print Hello world ke-i. 
- Setelah melakukan print hello world, **variabel `i`** akan di increment, dan kembali ke statement `while` untuk memeriksa apakah **`i`** masih kurang dari 10 setelah di-increment
- Karena setelah **`i`** di-increment nilainya masih 1 dan kurang dari 10, maka `while` akan dijalankan lagi hingga **`i`** bernilai 10 yang berarti tidak memenuhi kondisi `while`.
## Perulangan Do-While
Sintaks dari perulangan `do – while` adalah sebagai berikut.
```c
do {
    // Potongan kode yang dieksekusi.
    .
    .
    // increment/decrement
} while (<Ekspresi/Kondisi>)
```
Cara kerja dari perulangan `do – while` mirip dengan perulangan `while`. Hanya saja, pada perulangan `do – while`, potongan kode dijamin akan dieksekusi tepat satu kali sebelum mengevaluasi ekspresi/kondisi.
Contoh
```c
#include <stdio.h>
int main()
{
    int num = 0;
    do
    {
        printf("Num sekarang adalah %d\n",num);
        printf("Masukkan bilangan integer positif (-1 untuk keluar ): ");
        scanf("%d", &num);
    } while (num != -1);
    return 0;
}
```
## Perulangan For
Perulangan `for` merupakan perulangan paling rumit diantara perulangan lainnya. Sintaksnya adalah sebagai berikut.
```c
for (init_statement; kondisi/ekspresi; end_statement) {
    //  Potongan kode yang dieksekusi
    .
    .
}
```
Cara kerjanya adalah sebagai berikut:
- Bagian `init_statement` digunakan untuk inisialisasi variabel yang akan digunakan dalam perulangan. Bagian ini hanya dijalankan sekali saka pada saat awal perulangan.
- Selanjutnya `kondisi/ekspresi` akan dievaluasi. Jika menghasilkan **TRUE**, maka akan mengeksekusi potongan kode. Jika menghasilkan **FALSE**, maka perulangan berhenti.
- Setelah potongan kode selesai dieksekusi, akan mengeksekusi bagian `end_statement`. Biasanya bagian ini digunakan sebagai **increment/decrement**.
- Lalu akan **mengevaluasi ekspresi/kondisi lagi**, dan begitu seterusnya.
Contoh
```c
#include <stdio.h>
int main()
{
    int i;
    //    init;condition; increment
    for (i = 0; i < 10  ; i++) {
        printf("Hello World!\n");
    }
}
```
1. Awalnya **`i`** bernilai 0
2. For statement akan memeriksa nilai **`i`** apakah kurang dari 10
3. Apabila **TRUE** maka jalankan kode dalam for block, yakni print hello world
4. Setelah command dalam block for selesai dijalankan, maka variabel **`i`** akan di-increment, dan diperiksa lagi.
5. Apabila **`i`** kurang dari 10, maka command dalam block dieksekusi, apabila tidak maka for loop akan berhenti
## Perulangan/Percabangan Bersarang (Nested)
Percabangan dan perulangan juga dapat dibuat secara bersarang (membuat percabangan/perulangan di dalam percabangan/perulangan), tentu saja menyesuaikan kebutuhan. Contoh berikut adalah perulangan `for` bersarang.
```c
int i, j;
for (i = 1; i <= 10; ++i) {
    // Statement yang ingin dijalankan pada level terluar
    for (j = 1; j <= 10; j++) {
        // Statement yang ingin dijalankan pada level terdalam
        // Percabangan di dalam perulangan
        if (i == 10) {
            // Lakukan sesuatu
        }
    }
    // Statement yang ingin dijalankan pada level terluar
}
```
# Break and Continue
Keyword `break` dan `continue` digunakan untuk mengendalikan (kontrol) alur pada perulangan. Berikut penjelasannya.
## Break
Perintah `break` digunakan untuk **menghentikan** perulangan (secara paksa). Apabila perintah `break` pada suatu perulangan dijalankan, maka perulangan tersebut akan **dihentikan (secara paksa) dari titik dimana perintah break muncul**.
Contoh
```c
#include <stdio.h>
int main()
{
	int i;
	for (i = 1; i <= 6; i++) {
		printf("%d\n", i);
		//   Jika i adalah 4, maka keluar dari perulangan
		if (i == 4) {
			break;
		}
	}
	return 0;
}
```
## Continue
Kebalikan dari perintah break, perintah `continue` digunakan untuk **melanjutkan perulangan**. Pada perulangan, apabila menemui perintah `continue`, maka perintah-perintah dibawah `continue` akan **diabaikan** dan **kembali akan mengevaluasi ekspresi/kondisi**. Sedangkan pada perulangan `for` akan langsung mengekekusi bagian end_statement kemudian mengevaluasi ekspresi/kondisi.
Contoh
```c
#include <stdio.h>
int main()
{
	int i;
    for (i = 1; i <= 6; i++) {
	    // Jika i adalah 4, maka abaikan perintah printf()
        if (i == 4) {
            continue;
        }
        printf("%d\n",i);
    }
    return 0;
}
```
# Infinite Loop
Infinite loop adalah kasus di mana perulangan tidak akan pernah berhenti. Hal ini terjadi karena perulangan tidak akan pernah menemui kondisi yang membuatnya berhenti. Contoh di bawah akan menghasilkan infinite loop.
```c
#include <stdio.h>
int main()
{
    int i;
    for (i = 1; i <= 100; i--) {
        // Perulangan tak akan pernah berhenti
    }
}
```
# Array
## Pengenalan Array
Array merupakan jenis struktur data yang menampung elemen betipe data sama secara sekuensial dengan ukuran (kapasitas) yang tetap (_fixed-size_). Bayangkanlah sebuah array sebagai sekumpulan elemen sejenis yang disusun secara berurutan pada satu _identifier_ (nama).
## Deklarasi Array
Array juga sama seperti variabel, perlu dideklarasikan terlebih dahulu sebelum bisa digunakan. Deklarasi array sama seperti variabel, hanya saja saat pendeklarasiannya perlu dituliskan ukurannya.
```
tipe_data identifier_array[size];
```
## Inisialisasi Array
Kita juga bisa menginisialisasi elemen-elemen pada array setelah dideklarasikan. Sintaksnya adalah seperti berikut.
```
tipe_data identifier_array[size] = {elem1, elem2, elem3, ....}
```
## Mengakses Array
Seperti yang telah dijelaskan sebelumnya, array disimpan secara sekuensial (pada blok memori secara berurutan). Lalu bagaimana kita mengakses tiap elemennya? Pengaksesan elemen pada array dilakukan dengan menuliskan _identifier_ array-nya lalu digabung dengan menggunakan operator subscript `[]` dengan menyertakan indeks didalamnya.

![akses_array](https://github.com/AlproITS/DP_modul-2/blob/master/img/Array_access.png)

Indeks pada array menggunakan _zero-based index_, yang artinya elemen pertama pada array ditunjukkan oleh indeks ke 0 (bukan ke 1) dan elemen terakhir ditunjukkan oleh indeks ke N-1 (misal N adalah panjang array).
Elemen-elemen pada array dapat diperlakukan sama seperti halnya variabel. Kita dapat melakukan assignment, operasi aritmatika, dan lain-lain.
Contoh:
```c
int main () 
{
  int a[10]; //Deklarasi Array
  
  int b[5] = {1, 2, 3, 4, 5}; //Inisialisasi Array
  
  a[0] = 50;
  a[1] = 20;
  
  printf("%d %d\n", a[0], a[1]);
  
  return 0;
}
```
Mengapa kita perlu array? Andaikan kita membutuhkan 1000 inputan data, kita tidak perlu membuat deklarasi variabel berjumlah 1000, misalkan variabel a1 hinga a1000. Namun, kita cukup menuliskan 1 identifier array berkapasitas 1000.
Contoh program tanpa array:
```c
int main () {
  int a, b, c, d, e; //Deklarasi 5 variabel integer
  
  scanf("%d %d %d %d %d", &a, &b, &c, &d, &e);
  
  printf("Bilangan pertama adalah %d\n", a);
  printf("Bilangan kedua adalah %d\n", b);
  printf("Bilangan ketiga adalah %d\n", c);
  printf("Bilangan keempat adalah %d\n", d);
  printf("Bilangan kelima adalah %d\n", e);
  return 0;
}
```
Bayangkan kita tidak hanya memasukkan 5 data, melainkan 1000 data, bagaimana kita mendeklarasikan semuanya dalam variabel dan kemudian mencetaknya? Maka dari itulah array digunakan.
Contoh program menggunakan array:
```c
int main () 
{
	int a[5], i; 
	for(i = 0; i < 5; i++) {
		scanf("%d", &a[i]); //Input array
	}
	for(i = 0; i < 5; i++) {
		prinf("Bilangan ke-%d adalah %d\n", i+1, a[i]; // Output array
	}
	return 0;
}
```
## Dimensi Array
### Array Satu Dimensi
Sebuah array dikatan berdimensi satu apabila tiap elemennya hanya menyimpan satu data/objek. Contoh-contoh pada penjelasan sebelumnya merupakan array satu dimensi.
Contoh array satu dimensi:
```c
int main()
{
	int arr[5];
	arr[0] = 4;
	arr[1] = 2;
	arr[2] = 3;
	return 0;
}
```
Jika diilustrasikan, maka array tersebut akan tampak seperti di bawah.

![array-satu-dimens](https://github.com/AlproITS/DP_modul-2/blob/master/img/1D_Array.png)
### Array Multidimensi
Sebuah array dikatakan multidimensional apabila tiap elemen array  menampung array lainnya. Apabila array satu dimensi hanya memiliki sebuah index, array multidimensi memiliki dua atau lebih index untuk mengakses elemen dalam array tersebut. 
Cara deklarasinya pun berbeda dari array satu dimensi. Kita memerlukan N buah kurung siku untuk membuat array dengan N-dimensi.
Berikut adalah contoh program dengan array dua dimensi:
```c
int main () 
{
	int matriks[5][6];
	matriks[2][3] = 100;
	matriks[1][4] = 200;
	return 0;
}
```
Apabila diilustrasikan, bentuk array dua dimensi layaknya baris dan kolom, seperti gambar di bawah.
![array-dua-dimensi](https://github.com/AlproITS/DP_modul-2/blob/master/img/2D_Array.png)

Selain bentuk dua dimensi, kita dapat membuat array hingga N-dimensi, sesuai kebutuhan.
# String
## Pengenalan String
Secara umum, string merupakan kumpulan dari satu atau lebih karakter. Spesifik pada bahasa C, string didefinisikan sebagai kumpulan karakter yang diakhiri oleh karakter null (`'\0'`).
Misalkan string `"Dasar"`, pada bahasa C direpresentasikan sebagai kumpulan karakter `'D'`, `'a'`, `'s'`, `'a'`, `'r'`, dan `'\0'`.
## Representasi String
Pada bahasa C, string direpresentasikan oleh array bertipe `char`.
Contoh pendeklarasian string:
```c
#include <stdio.h>
int main () 
{  
	char str[] = "Halo"; 
	return 0;
}
```
Contoh di atas akan mendeklarasikan string bernama str dengan kapasitas 5 karakter, di mana `str[0] = 'H'`, `str[1] = 'a'`, `str[2] = 'l'`, `str[3] = 'o'`, dan `str[4] = '\0'`.
Perhatikan bahwa str[4] berisi karakter '\0' (null character), walaupun dalam literal string di atas tidak ada karakter tersebut. 
Dalam bahasa C, karakter null digunakan untuk menandakan akhir dari sebuah string.
Contoh pendeklarasian string (2):
```c
#include <stdio.h>
int main () {
  
  char array[10];
  
  return 0;
}
```
Contoh di atas akan mendeklarasikan string bernama array yang dapat menampung maksimal 10 karakter, termasuk null character.
Untuk menerima input string dari user, kita dapat menggunakan `scanf` atau `gets`. Perintah `scanf` akan membaca inputan string dari user dan berhenti ketika ada whitespace ataupun interupsi dari pengguna. Sedangkan `gets` akan membaca satu baris kumpulan karakter hingga enter atau interupsi dari pengguna.
Contoh source code penggunaan `scanf` untuk membaca string:
```c
#include <stdio.h>
int main () {
  
	char arr[10];
	while(1)
	{
		scanf("%s", arr);
		printf("-- %s\n", arr);
	}
	return 0;
}
```
Contoh penggunaan `gets` untuk membaca string:
```c
#include <stdio.h>
int main () {
  
	char arr[100];
	while(true)
	{
		gets(arr);
		
		printf("-- %s\n", arr);
	}
  return 0;
}
```
String yang dibaca dengan mengunakan `scanf` atau `gets` akan secara otomatis memiliki null character di akhir.
## Fungsi-Fungsi String
Dalam bahasa pemrograman C, terdapat library yang dibuat dengan tujuan memudahkan pengguna dalam mengolah string. Library tersebut tersimpan dalam `<string.h>`, oleh karena itu, untuk mengakses library ini, diperlukan tambahan preprocessor, yaitu:
```c
#include <string.h>
```
Berikut adalah fungsi-fungsi yang dibagi berdasarkan kegunaannya dalam mengolah sebuah string (diambil dari www.cplusplus.com):
- **Copying**
  + `memcpy` (Copy block of memory)
  + `memmove` (Move block of memory)
  + `strcpy` (Copy string)
  + `strncpy` (Copy characters from string)
- **Concatenation**
  + `strcat` (Concatenate strings)
  + `strncat` (Append character from string)
- **Comparison**
  + `memcmp` (Compare two blocks of memory)
  + `strcmp` (Compare two strings)
  + `strcoll` (Compare two strings using locale)
  + `strncmp` (Compare characters of two strings)
  + `strxfrm` (Transform string using locale)
- **Searching**
  + `memchr` (Locate character in block of memory)
  + `strchr` (Locate first occurrence of character in string)
  + `strcspn` (Get span until character in string)
  + `strpbrk` (Locate characters in string)
  + `strrchr` (Locate last occurrence of character in string)
  + `strspn` (Get span of character set in string)
  + `strstr` (Locate substring)
  + `strtok` (Split string into tokens)
- **Other**
  + `memset` (Fill block of memory)
  + `strerror` (Get pointer to error message string)
  + `strlen` (Get string length)
Berikut adalah beberapa fungsi dan penjelasannya.
### Fungsi `strcpy` 
```c
char * strcpy ( char * destination, const char * source );
```
Fungsi strcpy digunakan untuk melakukan **copy** dari sebuah string ke string lainnya. 
Contoh penggunaan dalam kode program:
```c
#include <stdio.h>
#include <string.h>
int main () {
  
	char a[] = "Halo";
	char b[10];
	
	// Copy string a ke string b
	strcpy(b, a);
	
	printf("%s\n", b);
	
	return 0;
}
```
### Fungsi `strcat` 
```c
char * strcat ( char * destination, const char * source );
```
Fungsi strcat digunakan untuk melakukan penempelan sebuah string pada **akhir** string yang lain. 
Contoh penggunaan dalam kode program:
```c
#include <stdio.h>
#include <string.h>
int main () {
  
	char a[] = "Halo";
	char b[] = " Kawan";
	char c[20];
	
	// Copy string a ke string b
	strcpy(c, a);
	
	// Tempelkan string b ke akhir string c
	strcat(c, b);
	
	printf("%s\n", c);
	
	return 0;
}
```
### Fungsi `strcmp`
```c
int strcmp ( const char * str1, const char * str2 );
```
Fungsi `strcmp` digunakan untuk melakukan **pembandingan** sebuah string dengan string yang lain. Return value dari fungsi ini dapat berupa bilangan negatif, nol ataupun positif. Jika fungsi ini mengembalikan nilai negatif, maka *str1* memiliki tingkat leksikografi lebih kecil dari *str2*. Sedangkan jika fungsi ini mengembalikan nilai postifi, maka *str1* memiliki tingkat leksikografi lebih besar dari *str2*. Terakhir, jika return value-nya nol, maka *str1* sama dengan *str2*. 
Berikut adalah contoh penggunaan fungsi ini dalam kode progam:
```c
#include <stdio.h>
#include <string.h>
int main () {
  
    char a[] = "Halo";
	char b[] = "Hai";
	char c[] = "Halo";
	
	if(strcmp(a, b) == 0) printf("String a sama dengan b\n");
	else printf("String a tidak sama dengan b\n");
	
	if(strcmp(a, c) == 0) printf("String a sama dengan c\n");
	else printf("String a tidak sama dengan c\n");
	
	return 0;
}
```
### Fungsi `strlen`
```c
size_t strlen ( const char * str );
```
Fungsi `strlen` digunakan untuk mengetahui **panjang** dari sebuah string.
```c
#include <stdio.h>
#include <string.h>
int main () {
  
	char a[] = "Halo";
	
	printf("Panjang string a adalah %d\n", strlen(a));
	
	return 0;
}
```
# Latihan Soal
### Soal 1
Buat program yang mencetak kata `Ganjil` untuk bilangan ganjil, dan kata `Genap` untuk bilangan genap dari sebuah input.
**Sample Input**
```
1
```
**Sample Output**
```
Ganjil
```
### Soal 2
Buat program untuk mencetak asterisk, `*`, untuk bilangan genap, dan bilangan aslinya untuk bilangan ganjil, dari n buah bilangan mulai 1 s.d n.
**Sample Input**
```
6
```
**Sample Output**
```
1 * 3 * 5 *
```
    
### Soal 3
Buat program untuk mencetak asterisk, `*`, untuk bilangan prima, dan angka asli untuk bilangan non-prima dari n buah bilangan mulai 2 s.d n.
**Sample Input**
```
10
```
**Sample Output**
```
* * 4 * 6 * 8 9 10
```
### Soal 4
Buatlah program untuk mencetak N buah angka yang diinput secara terbalik. Input baris pertama adalah N yang merupakan banyaknya angka yang akan diinput. Baris berikutnya terdapat N buah angka (dipisahkan spasi).
**Sample Input**
```
5
1 4 3 2 9
```
**Sample Output**
```
9
2
3
4
1
```
### Soal 5
Buatlah sebuah program untuk menghitung jumlah huruf vokal yang terdapat pada sebuah string S. Panjang string S tidak melebihi 100 karakter dan terdiri dari huruf lowercase, uppercase dan spasi.
**Sample Input**
```
Dasar Pemograman Keren
```
**Sample Output**
```
A/a : 4
I/i : 0
U/u : 0
E/e : 3
O/o : 1
```
### Soal 6
Diberikan sebuah nama variabel dalam bentuk **snake_case**. Buatlah program untuk mengubah nama variabel tersebut menjadi bentuk **camelCase**. Nama variabel hanya terdiri dari huruf lowercase, uppercase, dan simbol underscore.
**Sample Input 1**
```
skor_pemain
```
**Sample Output 1**
```
skorPemain
```
**Sample Input 2**
```
VariabEl_Satu
```
**Sample Output 2**
```
variabelSatu
```