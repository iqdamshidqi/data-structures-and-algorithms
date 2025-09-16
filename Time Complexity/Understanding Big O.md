# Membedah Big O Notation: Mengukur Efisiensi Kode Anda 🧐

<img width="1346" height="974" alt="image" src="https://github.com/user-attachments/assets/ea9dffee-3979-47e1-bcff-f7354dcf432d" />


Pernahkah Anda bertanya-tanya mengapa beberapa program berjalan secepat kilat sementara yang lain terasa sangat lambat? Jawabannya sering kali terletak pada bagaimana kode tersebut ditulis dan seberapa efisien algoritmanya. Di sinilah **Big O Notation** berperan sebagai alat ukur yang sangat penting.

[cite\_start]Big O Notation adalah cara matematis untuk mendeskripsikan efisiensi suatu algoritma[cite: 14, 309]. [cite\_start]Secara spesifik, notasi ini mengukur **skenario terburuk (worst-case)** dari sebuah algoritma, yaitu berapa lama waktu (kompleksitas waktu) atau berapa banyak memori (kompleksitas ruang) yang dibutuhkan seiring dengan bertambahnya jumlah input[cite: 309, 310, 311].

[cite\_start]Alih-alih mengukur dalam detik atau byte (yang bisa berbeda tergantung pada perangkat keras), Big O menggunakan ekspresi matematika untuk menggambarkan bagaimana kinerja algoritma berubah saat ukuran input (`n`) meningkat[cite: 312, 314].

-----

### Tipe-Tipe Umum Kompleksitas Big O

Mari kita lihat beberapa jenis Big O yang paling umum, diurutkan dari yang tercepat hingga yang paling lambat.

#### 1\. $O(1)$ — Constant Time (Waktu Konstan) ⚡️

Ini adalah "juara" efisiensi. Algoritma dengan kompleksitas $O(1)$ membutuhkan waktu yang **sama** untuk selesai, tidak peduli seberapa besar ukuran inputnya.

  * **Analogi:** Seperti mengambil buku dari rak jika Anda sudah tahu persis nomor urutnya. Tidak peduli ada 10 buku atau 1.000 buku di rak itu, waktu yang Anda butuhkan untuk mengambilnya tetap sama.
  * [cite\_start]**Contoh Kode:** Mengakses elemen dalam sebuah list menggunakan indeksnya[cite: 328, 329].

<!-- end list -->

```python
# Tidak peduli berapa banyak warna di dalam list,
# operasi ini hanya butuh satu langkah.
colors = ['green', 'yellow', 'blue', 'pink', 'black', 'white']

def constant_example(items):
  # Mengambil item ke-3 (indeks 2)
  [cite_start]print(items[2]) # Operasi ini selalu O(1) [cite: 337]

constant_example(colors)
```

#### 2\. $O(\\log n)$ — Logarithmic Time (Waktu Logaritmik) 🚀

Ini adalah kompleksitas yang sangat efisien. Waktu eksekusinya meningkat sangat lambat seiring bertambahnya input. Algoritma ini bekerja dengan memotong separuh dari total data pada setiap langkahnya (prinsip "divide and conquer").

  * **Analogi:** Mencari nama di buku telepon atau kata di kamus. Anda tidak akan membaca dari halaman pertama. Anda akan membukanya di tengah, lalu menentukan apakah target Anda ada di paruh depan atau paruh belakang, dan mengabaikan separuh lainnya. Proses ini diulang hingga target ditemukan.
  * **Contoh Kode:** Pencarian Biner (Binary Search) pada data yang sudah terurut.

<!-- end list -->

```python
# Binary search membagi dua rentang pencarian di setiap langkah.
def binary_search(sorted_list, target):
    low = 0
    high = len(sorted_list) - 1
    while low <= high:
        mid = (low + high) // 2
        if sorted_list[mid] == target:
            return True
        elif sorted_list[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return False

numbers = [1, 5, 8, 10, 12, 15, 20, 22, 30]
print(binary_search(numbers, 15))
```

#### 3\. $O(n)$ — Linear Time (Waktu Linier) 🏃

[cite\_start]Kinerja algoritma ini tumbuh secara **linier** (lurus) seiring dengan bertambahnya ukuran input (`n`)[cite: 374]. Jika input bertambah dua kali lipat, waktunya juga akan bertambah sekitar dua kali lipat.

  * **Analogi:** Membaca judul setiap buku di satu rak untuk menemukan buku tertentu. Semakin banyak buku di rak (`n`), semakin lama waktu yang Anda butuhkan.
  * [cite\_start]**Contoh Kode:** Melakukan iterasi (looping) pada semua elemen dalam sebuah list[cite: 344, 345].

<!-- end list -->

```python
# Jumlah operasi print() akan sama dengan jumlah elemen (n).
# Jika n=4, ada 4 operasi. Jika n=100, ada 100 operasi.
[cite_start]colors = ['green', 'yellow', 'blue', 'pink'] # n = 4 [cite: 355]

def linear_example(items):
  [cite_start]for item in items: # Loop ini berjalan sebanyak n kali [cite: 357]
    print(item)

linear_example(colors)
```

#### 4\. $O(n \\log n)$ — Log-Linear Time (Waktu Log-Linier) ✨

Ini adalah titik terbaik untuk algoritma pengurutan (sorting) yang efisien. Kompleksitas ini lebih cepat dari $O(n^2)$ dan sering ditemukan pada algoritma yang memecah masalah menjadi bagian-bagian yang lebih kecil, menyelesaikannya secara terpisah, lalu menggabungkannya kembali.

  * **Analogi:** Mengurutkan setumpuk kartu ujian. Anda bisa membagi tumpukan menjadi dua, lalu membagi dua lagi, sampai Anda hanya memegang satu kartu (yang sudah "terurut"). Kemudian Anda menggabungkan kembali kartu-kartu itu secara berpasangan dalam urutan yang benar hingga seluruh tumpukan terurut.
  * **Contoh Kode:** Algoritma sorting efisien seperti Merge Sort, Quick Sort, atau Timsort (yang digunakan oleh fungsi `.sort()` bawaan Python).

<!-- end list -->

```python
# Algoritma sorting yang efisien seperti Timsort (yang digunakan Python)
# memiliki kompleksitas rata-rata dan terburuk O(n log n).
my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5]
my_list.sort() # Operasi ini secara internal sangat efisien
print(my_list)
```

#### 5\. $O(n^2)$ — Quadratic Time (Waktu Kuadratik) 🐢

[cite\_start]Waktu eksekusi algoritma ini sebanding dengan **kuadrat** dari ukuran input[cite: 387]. [cite\_start]Ini biasanya terjadi ketika ada loop di dalam loop (nested loop) pada data yang sama[cite: 380, 381]. Kinerjanya menurun drastis saat input bertambah.

  * **Analogi:** Membandingkan setiap buku di rak dengan setiap buku lainnya untuk mencari duplikat. Jika ada 10 buku, Anda melakukan sekitar 10x10 = 100 perbandingan.
  * [cite\_start]**Contoh Kode:** Loop bersarang untuk membandingkan setiap elemen dengan setiap elemen lainnya [cite: 379-382].

<!-- end list -->

```python
# Untuk n=3, ada 3x3 = 9 operasi.
# Untuk n=100, akan ada 100x100 = 10,000 operasi!
colors = ['green', 'yellow', 'blue']

def quadratic_example(items):
  for first_item in items:
    for second_item in items:
      print(first_item, second_item)

quadratic_example(colors)
```

#### Kompleksitas Lain yang Lebih Lambat (Perlu Dihindari) 🐌

  * **$O(2^n)$ — Exponential Time:** Waktu eksekusi berlipat ganda setiap kali ada penambahan satu elemen pada input. Algoritma ini menjadi tidak praktis dengan sangat cepat. Contohnya adalah penyelesaian rekursif naif untuk deret Fibonacci.
  * **$O(n\!)$ — Factorial Time:** Ini adalah "monster" dalam dunia kompleksitas. Waktu eksekusinya tumbuh secara faktorial dan hanya bisa digunakan untuk input yang sangat-sangat kecil (misalnya, kurang dari 10). Contohnya adalah menyelesaikan masalah *Traveling Salesman* dengan mencoba semua kemungkinan rute.

-----

### Visualisasi Perbandingan Big O

[cite\_start]Grafik di bawah ini menunjukkan bagaimana waktu eksekusi (jumlah operasi) meningkat seiring dengan bertambahnya ukuran input untuk setiap kompleksitas[cite: 323]. Perhatikan betapa cepatnya kurva $O(n^2)$ dan yang lebih lambat menanjak\!

Grafik ini dengan jelas menunjukkan bahwa algoritma dengan kompleksitas $O(1)$ dan $O(\\log n)$ adalah yang paling efisien untuk input berukuran besar, sementara $O(n^2)$ dan yang lebih buruk harus dihindari jika memungkinkan.

-----

### Cara Menghitung dan Menyederhanakan Big O

Saat menganalisis kode, Anda mungkin mendapatkan ekspresi yang kompleks. Untungnya, ada aturan sederhana untuk menyederhanakannya.

  * [cite\_start]**Aturan 1: Abaikan Konstanta** [cite: 493]
    [cite\_start]Big O berfokus pada laju pertumbuhan, jadi kita mengabaikan angka pengali[cite: 501].

      * $O(2n)$ menjadi $O(n)$
      * [cite\_start]$O(4+2n+2m)$ disederhanakan menjadi $O(n+m)$ [cite: 494]

  * [cite\_start]**Aturan 2: Abaikan Term Non-Dominan** [cite: 496]
    [cite\_start]Kita hanya peduli pada bagian yang paling lambat (yang paling cepat tumbuh) saat `n` menjadi sangat besar[cite: 504].

      * [cite\_start]$O(n + n^2)$ menjadi $O(n^2)$ karena $n^2$ tumbuh jauh lebih cepat daripada $n$[cite: 497, 505].

  * [cite\_start]**Aturan 3: Gunakan Variabel Berbeda untuk Input Berbeda** [cite: 495]
    [cite\_start]Jika sebuah fungsi memiliki dua input berbeda (misalnya, dua list dengan ukuran `n` dan `m`), gunakan kedua variabel tersebut dalam notasi Big O[cite: 495].

      * $O(n + m)$

Dengan memahami Big O Notation, Anda dapat membuat pilihan yang lebih cerdas saat merancang algoritma, memastikan program Anda tetap cepat dan responsif, bahkan saat berhadapan dengan data dalam jumlah besar. ✅
