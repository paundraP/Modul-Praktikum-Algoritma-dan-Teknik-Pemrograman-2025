## Daftar Isi
- [Algoritma Sorting](#algoritma-sorting)
  + [Bubble Sort](#bubble-sort)
  + [Insertion Sort](#insertion-sort)
  + [Merge Sort](#merge-sort)
  + [Quick Sort](#quick-sort)
- [Algoritma Searching](#algoritma-searching)
  + [Linear Search](#linear-search)
  + [Binary Search](#binary-search)
- [Latihan](#latihan)

***

# Algoritma Sorting

## Bubble Sort

Algoritma **Bubble Sort** merupakan proses pengurutan yang secara berangsur-angsur berpindah ke posisi yang tepat, karena itulah dinamakan Bubble yang artinya gelembung. Algoritma ini akan mengurutkan data dari yang terbesar ke yang terkecil (_ascending_) atau sebaliknya (_descending_).

Secara sederhana, **algoritma Bubble Sort adalah pengurutan dengan cara pertukaran data dengan data di sebelahnya secara terus menerus hingga tidak ada lagi perubahan**. Bubble Sort adalah metode _sorting_ yang sederhana, namun merupakan metode pengurutan yang tidak efisien karena ketika mengurutkan data yang sangat besar akan sangat lambat prosesnya.

Sifat algoritma Bubble Sort adalah sebagai berikut:
1. Jumlah iterasi sama dengan banyaknya bilangan dikurang 1.
2. Di setiap iterasi, jumlah pertukaran bilangannya sama dengan jumlah banyaknya bilangan.
3. Dalam algoritma Bubble Sort, meskipun deretan bilangan tersebut sudah terurut, proses _sorting_ akan tetap dilakukan.
4. Tidak ada perbedaan cara yang berarti untuk teknik algoritma Bubble Sort _ascending_ dan _descending_.

![bubble](https://github.com/AlproITS/DasarPemrograman/blob/master/img/bubblesort.PNG)

**Implementasi Bubble Sort**:
```c
void swap(int *xp, int *yp) {
   int temp = *xp;
   *xp = *yp;
   *yp = temp;
}

void bubbleSort(int arr[], int n) {
   int i, j, swapped;        // dioptimasi dengan bool `swapped`:
   for (i = 0; i < n-1; i++) {
      swapped = 0;
      for (j = 0; j < n-i-1; j++) {
         if (arr[j] > arr[j+1]) {
            swap(&arr[j], &arr[j+1]);
            swapped = 1;
         }
      }
      if (swapped == 0)
         break;
   }
}
```

## Insertion Sort

**Insertion Sort** merupakan salah satu jenis sort yang mirip seperti saat kalian melakukan pengurutan kartu remi di tangan. Algoritma ini dua elemen data pertama, mengurutkannya, kemudian mengecek elemen data berikutnya satu persatu dan membandingkannya dengan elemen data yang telah diurutkan. Ide dasar dari algoritma ini adalah mencari tempat yang “tepat” untuk setiap elemen array.

Secara umum, langkah-langkah algoritma insertion sort adalah sebagai berikut.
1. Ambil elemen dari array ke-i.
2. Taruh di urutan sebelumnya ( arr[ …i-1] ) yang telah diurutkan di tempat yang sesuai.

![insertion](https://github.com/AlproITS/DasarPemrograman/blob/master/img/insertionsort.PNG)

**Implementasi Insertion Sort**:
```c
void insertionSort(int arr[]. int n) {
   int i, key, j;
   for (i = 1; i < n; i++) {
      key = arr[i];
      j = i-1;
    
      while (j >= 0 && arr[j] > key) {
         arr[j+1] = arr[j];
         j = j-1;
      }
      arr[j+1] = key;
   }
}
```


## Merge Sort

**Merge Sort** adalah algoritma sorting yang dilakukan secara rekursif dengan membagi array menjadi 2 bagian, melakukan merge-sort pada 2 bagian tersebut, lalu melakukan merge pada kedua array tersebut.

Secara formal, proses merge sort dapat dituliskan sebagai berikut:
```
Sort(L,R):

If(R > L):
  1. M = (L + R) / 2
  2. Sort(L,M)
  3. Sort(M + 1,R)
  4. Merge(L,R)
```

**Penjelasan lebih detail dan contoh implementasi**: [https://www.interviewbit.com/tutorial/merge-sort-algorithm/](https://www.interviewbit.com/tutorial/merge-sort-algorithm/)

Contoh alur rekursi untuk Merge Sort pada array dengan 8 elemen:

![merge](https://github.com/AlproITS/DasarPemrograman/blob/master/img/mergesort.PNG)

Pada setiap tahap, akan dilakukan proses _merge_. Proses _merge_ dilakukan dengan mengurutkan secara naif dengan memanfaatkan fakta bahwa kedua array hasil partisi sudah terurut.

Karena setiap kali rekursi ukuran array menjadi setengahnya, maka kedalaman maksimal rekursi adalah **log2(N)**.

Karena di setiap tahap rekursi total proses _merge_ yang dilakukan ada sebanyak N, maka total kompleksitas pengurutan menggunakan Merge Sort adalah **N log2(N)**.

## Quick Sort

Mirip seperti Merge Sort, **Quick Sort** adalah algoritma sorting yang dilakukan secara rekursif dan menggunakan prinsip Divide and Conquer.

Secara formal, proses Quick Sort dapat dituliskan sebagai berikut:
```
Sort(L,R)

If (R > L):

  1. M = Partisi(L,R). //M adalah index yang posisinya sudah fix.
  2. Sort(L,M - 1)
  3. Sort(M + 1,R)
```

Sedangkan untuk bagian partisi dapat dituliskan sebagai berikut:
```
Partisi(L,R):

  1. Pivot = arr[L]
  2. storeIndex = L + 1
  3. Iterasi i dari L + 1 sampai R, jika arr[i] < pivot, lanjut ke step 4.
  4. swap(arr[i],arr[storeIndex])
  5. storeIndex = storeIndex + 1
  6. Jika i masih kurang dari atau sama dengan R, kembali ke step 3. Jika tidak, lanjut ke step 7
  7. swap(arr[L],arr[storeIndex - 1])
  8. Return storeIndex - 1
```

Terkait proses partisi, terdapat berbagai cara dalam pemilihan pivot. Bisa saja menggunakan data paling kiri (seperti di atas), data paling kanan, atau data _random_, tergantung implementasi masing-masing.

**Penjelasan lebih detail dan contoh implementasi**: [https://www.interviewbit.com/tutorial/quicksort-algorithm/](https://www.interviewbit.com/tutorial/quicksort-algorithm/)

---

Jika dirata-rata, total kompleksitas dari Quick Sort adalah **O(N log2(N))**. Meskipun begitu, kompleksitas terburuk dari Quick Sort adalah **O(N2)**. Proses partisi dengan cara memilih index random sebagai pivot terbukti cukup efisien untuk membuat **Quick Sort** dilakukan dalam kompleksitas **O(N log2(N))**.

Merge Sort dan Quick Sort adalah algoritma _sorting_ yang paling umum dipakai karena memiliki efisiensi yang sangat baik meskipun terdapat algoritma yang lebih efisien seperti Radix Sort. Sedangkan untuk Bubble Sort dan Insertion Sort hampir tidak pernah dipakai. Algoritma tersebut sebaiknya hanya dipelajari untuk pengetahuan saja.

Di antara Merge Sort dan Quick Sort, penggunaan Quick Sort sering kali lebih dipilih dikarenakan Quick Sort adalah algoritma pengurutan yang bersifat _in-place_ yang berarti tidak membutuhkan memori tambahan dalam implementasinya, tidak seperti Merge Sort yang membutuhkan memori tambahan dengan ukuran yang linear terhadap array yang akan di-_sort_.

# Algoritma Searching

## Linear Search

Algoritma searching yang paling mudah untuk dipahami dan diimplementasikan adalah **Linear Search** atau biasa juga disebut dengan **Sequential Search**. Linear Search bekerja dengan melakukan pengecekan kepada semua elemen yang ada.

Secara garis besar, cara kerja Linear Search adalah:
1. Memeriksa item satu per satu.
2. Apabila ditemukan, maka “ketemu”.
3. Jika sampai akhir belum ditemukan, maka item yang dicari tidak ada.

**Implementasi Linear Search**
```c
int linearSearch(int arr[], int n, int item) {
   int i;
   for(i = 0; i < n; ++i) {
      if(item == arr[i])
         return 1;
   }
   return -1;
}
```

## Binary Search

**Binary Search** adalah teknik pencarian di mana untuk setiap iterasinya kita membagi _space_ pencarian menjadi hanya setengah dari _space_ pencarian awal hingga kita menemukan yang kita cari.

Untuk menerapkan teknik ini, kita harus memastikan bahwa data yang kita punya memiliki properti monoton naik atau turun ([https://en.wikipedia.org/wiki/Monotonic_function](https://en.wikipedia.org/wiki/Monotonic_function)).

![functions](https://github.com/AlproITS/DasarPemrograman/blob/master/img/functions.PNG)

> Gambar kiri dan tengah memiliki properti monoton serta gambar kanan tidak.

### Contoh 1

Ada array ukuran N (N <= 10^5), elemennya bisa sampai 10^9, arraynya sorted secara _ascending_.\
Ada Q query (Q <= 10^5). Tiap query dikasih angka K, jawab kalau K ada di array atau tidak.

**Solusi**\
![meme](https://github.com/AlproITS/DasarPemrograman/blob/master/img/meme-linser1.PNG)
![meme](https://github.com/AlproITS/DasarPemrograman/blob/master/img/meme-linser2.PNG)
![meme](https://github.com/AlproITS/DasarPemrograman/blob/master/img/meme-linser3.PNG)

Kata kunci: **Sorted**\
Karena arraynya _sorted_, berarti array tersebut memiliki properti monoton.

**Contoh**\
[2,3,8,10,13,17,28,35]

Cukup jelas kalau array-nya monoton. Sekarang bagaimana melakukan Binary Search-nya?

Misalkan kita mau mengecek apakah angka 13 ada di array atau tidak. (i.e.: target = 13)

1. _Space_ pencarian kita adalah index [1,8].
2. Sekarang kita bagi array jadi 2 bagian, index [1,4] dan index [5,8]. Untuk tau target ktia ada di array pertama atau kedua, kita tinggal mengecek nilai tengah dari _space_ pencarian kita saat ini yaitu di index **(1 + 8) / 2 = 4**.
   > Ini dibulatkan ke bawah karena index 4,5 tidak ada 🧐
3. Array pada index 4 bernilai 10. Karena kita tau bahwa array-nya _sorted_ secara _ascending_, berarti **index dari elemen 13 pasti berada di kanannya**.
4. Sekarang _space_ dari pencarian kita adalah index[5,8].
5. Bagi array menjadi 2 bagian lagi, [5,6] dan [7,8]. Lalu cek tengahnya lagi yaitu di index **(5 + 8) / 2 = 6**.
6. Array pada index 6 bernilai 17. Karena kita tahu bahwa array-nya _sorted_ secara _ascending_, berarti **index dari elemen 13 pasti berada di kirinya**.
7. Sekarang _space_ dari pencarian kita adalah index[5,5].
8. Karena hanya tinggal tersisa 1 index, **kita hanya perlu mengecek apakah index 5 bernilai 13 atau tidak**.

**Visualisasi dan contoh implementasi**: [https://csacademy.com/lesson/binary_search](https://csacademy.com/lesson/binary_search)

Perhatikan bahwa pada proses pencarian, kita selalu membagi _space_ pencarian kita menjadi setengahnya. Maka dari itu, pada kasus terburuknya, iterasi akan dilakukan sebanyak **log2(N)** kali.

### Contoh 2

Ada N segi empat berukuran a x b. Segi empatnya tidak dapat diputar. Tentukan ukuran persegi terbesar yang bisa memuat semua segi empat tadi.

**Solusi**

Pengisian segi empat yang optimal adalah seperti berikut.

![solusi](https://github.com/AlproITS/DasarPemrograman/blob/master/img/binser.PNG)

Dengan begitu, kita dapat membuat sebuah fungsi sebagai berikut:

<a href="https://www.codecogs.com/eqnedit.php?latex=f(x)&space;=&space;1,&space;jika&space;\frac{x}{a}&space;\times&space;\frac{x}{b}&space;\geq&space;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f(x)&space;=&space;1,&space;jika&space;\frac{x}{a}&space;\times&space;\frac{x}{b}&space;\geq&space;n" title="f(x) = 1, jika \frac{x}{a} \times \frac{x}{b} \geq n" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=f(x)&space;=&space;0,&space;jika&space;\&space;sebaliknya" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f(x)&space;=&space;0,&space;jika&space;\&space;sebaliknya" title="f(x) = 0, jika \ sebaliknya" /></a>

Dapat dilihat bahwa jika untuk suatu K, nilai f(K)= 1, maka pasti nilai **f(K + 1) = 1**. Yang artinya fungsi tersebut memiliki properti **monoton**.

Sekarang, kita hanya perlu mencari nilai K terkecil sehingga nilai **f(K) = 1**.

**Contoh implementasi**
```c
bool f(int k, int a, int b, int n) {
   return ((k/a) * (b/a) >= n);
}

int binser(int a, int b, int n) {
   int l = 1;
   int r = 100000;
   while (r - l > 1) {
      int mid = (l + r) >> 1;
      bool can = f(mid);
      if(can)
         r = mid;
      else
         l = mid + 1;
   }
   if (can(l))
      return l;
   else
      return r;
}
```

# Latihan

### Soal 1: [Binary Search](https://tlx.toki.id/problems/impl-search/C) (Straight Forward)

### Soal 2: [Lower Upper Bound](https://tlx.toki.id/problems/impl-search/D) (Straight Forward)

### Soal 3: [Hamburgers](https://codeforces.com/problemset/problem/371/C)
> Mirip dengan [Contoh 2](#contoh-2), tinggal cari fungsinya