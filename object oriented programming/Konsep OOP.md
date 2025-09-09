# **Pengenalan Object-Oriented Programming (OOP)**

OOP adalah paradigma pemrograman yang berpusat pada "objek" dan bukan hanya fungsi dan logika. Mari kita bedah konsep dasarnya.

#### **Definisi Kunci**

  * **Class**: Sebuah *blueprint* atau cetak biru yang mendefinisikan atribut (data) dan *method* (fungsi) dari objek.
  * **Object**: Instansi atau perwujudan nyata dari sebuah *class*. Objek memiliki semua sifat dan perilaku yang didefinisikan dalam *class*-nya.

#### **Perbandingan dengan Pemrograman Prosedural**

Sebelum OOP, kita mengenal Pemrograman Prosedural, di mana program dieksekusi baris per baris.

```python
# Contoh Pemrograman Prosedural
def fungsi_1(x):
    return x**2 + 1

def fungsi_2(x, h=10):
    return (fungsi_1(x + h) - fungsi_1(x)) / h

print(fungsi_1(5), fungsi_2(3))
```

Kelemahan utamanya adalah ketika program menjadi kompleks, fungsi-fungsi menjadi saling bergantung dan sulit dikelola, sering disebut sebagai "spaghetti code".

OOP mengatasi ini dengan **Enkapsulasi**, yaitu membungkus data (atribut) dan fungsi (*method*) yang relevan ke dalam satu unit (objek).

### **Hampir Semua di Python adalah Objek**

Tanpa disadari, kita selalu bekerja dengan objek di Python. Setiap tipe data, bahkan fungsi, adalah sebuah objek.

```python
N = 99
T = 'sembarang string'
print(type(N), type(T))

def fungsi_1(x):
    return x**2 + 1
print(type(fungsi_1))
```

Karena merupakan objek, mereka memiliki *method* (fungsi) dan *attribute* (properti).

```python
print(T.split())  # Memanggil method split() dari objek string
print(N.real)       # Mengakses attribute real dari objek integer
```

### **Membuat Class Sendiri**

Mari kita buat objek `Robot` kita sendiri.

```python
class Robot:
    def beriSalam(self):
        print('Assalamualaikum')

gundam = Robot()
gundam.beriSalam()
```

#### **Method `__init__` dan `self`**

  * `__init__`: *Method* khusus yang otomatis dijalankan saat sebuah objek dibuat. Ini digunakan untuk menginisialisasi atribut objek.
  * `self`: Merujuk pada instance objek itu sendiri. Ini memungkinkan kita untuk mengakses atribut dan *method* dari dalam *class*.

<!-- end list -->

```python
class Robot:
    # Class variable untuk menghitung jumlah robot
    jumlah = 0

    def __init__(self, tipe, tahun=2020):
        # Instance variables
        self.tipe = tipe
        self.tahun_produksi = tahun
        Robot.jumlah += 1

    def getDetails(self):
        return self.tipe, self.tahun_produksi

Android17 = Robot('dbz', tahun=1997)
Android18 = Robot('dbz')

print(f"Tipe Android 17: {Android17.tipe}")
print(f"Detail Android 18: {Android18.getDetails()}")
print(f"Jumlah robot saat ini: {Robot.jumlah}")
```

### **Contoh Kasus Sederhana: Sistem Perkuliahan**

Mari terapkan OOP untuk mengelola data mahasiswa dan kelas.

```python
class Mahasiswa:
    def __init__(self, nama, nilai):
        self.nama = nama
        self.nilai = nilai

    def nilai_mahasiswa(self):
        return self.nilai

class Kuliah:
    def __init__(self, nama, max_mahasiswa):
        self.nama = nama
        self.max_mahasiswa = max_mahasiswa
        self.mahasiswa = []

    def tambah_mahasiswa(self, mahasiswa):
        if len(self.mahasiswa) < self.max_mahasiswa:
            self.mahasiswa.append(mahasiswa)
            return True
        return "Error: Maaf kelas Penuh"

    def rerata_nilai(self):
        total_nilai = sum(siswa.nilai_mahasiswa() for siswa in self.mahasiswa)
        return total_nilai / len(self.mahasiswa)

# Inisialisasi objek
m1 = Mahasiswa('Udin', 77)
m2 = Mahasiswa('Ucok', 67)
kelas = Kuliah('Kalkulus', 2)

# Menambahkan mahasiswa ke kelas
kelas.tambah_mahasiswa(m1)
kelas.tambah_mahasiswa(m2)

# Menghitung rata-rata nilai
print(f"Nilai rata-rata kelas {kelas.nama} adalah = {kelas.rerata_nilai()}")
```

### **Inheritance (Pewarisan)**

*Inheritance* memungkinkan sebuah *class* (anak) untuk mewarisi atribut dan *method* dari *class* lain (induk). Ini mendorong penggunaan kembali kode (*code reusability*).

#### **Tipe-Tipe Inheritance**

1.  **Single Inheritance**: Satu *class* anak mewarisi dari satu *class* induk.
2.  **Multiple Inheritance**: Satu *class* anak mewarisi dari beberapa *class* induk.
3.  **Multilevel Inheritance**: Sebuah *class* mewarisi dari *class* anak lain (seperti hubungan Kakek -\> Ayah -\> Anak).
4.  **Hierarchical Inheritance**: Beberapa *class* anak mewarisi dari satu *class* induk yang sama.
5.  **Hybrid Inheritance**: Kombinasi dari dua atau lebih tipe *inheritance*.

#### **Contoh Sederhana Inheritance**

```python
class Ortu:
    def __init__(self, nama='Bambang', umur=40):
        self.nama = nama
        self.umur = umur

    def info(self):
        print(f"Nama = {self.nama}, Umur = {self.umur}")

class Anak(Ortu):  # Anak mewarisi dari Ortu
    def __init__(self, nama, umur, anakKe):
        super().__init__(nama, umur)  # Memanggil __init__ dari class Ortu
        self.anakKe = anakKe

    def info(self):  # Method Overriding
        print(f"Nama = {self.nama}, Umur = {self.umur}, anak Ke-{self.anakKe}")

sulung = Anak("Budi", 5, 1)
sulung.info()
```

### **Polimorfisme**

Polimorfisme berarti "banyak bentuk". Dalam OOP, ini merujuk pada kemampuan objek yang berbeda untuk merespons *method* yang sama dengan cara yang berbeda. Salah satu contohnya adalah **Method Overriding**, seperti pada contoh di atas di mana *method* `info()` di *class* `Anak` menggantikan implementasi dari *class* `Ortu`.

### **Studi Kasus: Katalog Buku**

Mari kita buat sistem sederhana untuk mengelola berbagai jenis buku menggunakan semua konsep yang telah kita pelajari.

```python
# Kelas Induk
class Buku:
    def __init__(self, judul, pengarang, tahun_terbit):
        self.judul = judul
        self.pengarang = pengarang
        self.tahun_terbit = tahun_terbit

    def deskripsi(self):
        return f"Judul: {self.judul}, Pengarang: {self.pengarang}, Tahun: {self.tahun_terbit}"

# Kelas Anak
class BukuFiksi(Buku):
    def __init__(self, judul, pengarang, tahun_terbit, genre):
        super().__init__(judul, pengarang, tahun_terbit)
        self.genre = genre

    def deskripsi(self):  # Method Overriding
        base_deskripsi = super().deskripsi()
        return f"{base_deskripsi}, Genre: {self.genre}"

# Kelas Anak
class BukuNonFiksi(Buku):
    def __init__(self, judul, pengarang, tahun_terbit, bidang_studi):
        super().__init__(judul, pengarang, tahun_terbit)
        self.bidang_studi = bidang_studi

    def deskripsi(self):  # Method Overriding
        base_deskripsi = super().deskripsi()
        return f"{base_deskripsi}, Bidang Studi: {self.bidang_studi}"

# Membuat objek
buku_fiksi = BukuFiksi("Harry Potter", "J.K. Rowling", 1997, "Fantasi")
buku_nonfiksi = BukuNonFiksi("Sapiens", "Yuval Noah Harari", 2011, "Sejarah")

# Menampilkan deskripsi
print(buku_fiksi.deskripsi())
print(buku_nonfiksi.deskripsi())
```
