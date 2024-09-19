# Tugas Pertemuan 2


Nama : Hendra Latieful Maajid

NIM : H1D022018

Shift Baru: F


# Penjelasan Proses Passing Data dari Form ke Tampilan

## Komponen Utama

1. **FormData** (`form_data.dart`)
    - Widget yang menangani input pengguna
    - Menggunakan `TextFormField` untuk mendapatkan inputan nama, NIM, dan tahun lahir

2. **TampilData** (`tampil_data.dart`)
    - Widget yang menampilkan data yang telah diinput
    - Menerima data dari FormData sebagai parameter konstruktor

## Proses Passing Data

1. **Pengumpulan Data di FormData**
    - Data diinput oleh pengguna melalui `TextFormField`
    - Data disimpan dalam `TextEditingController`:
      ```dart
      final _namaController = TextEditingController(); //menyimpan input nama di controller
      final _nimController = TextEditingController(); //menyimpan input nim di controller
      final _tahunController = TextEditingController(); //menyimpan input tahun di controller
      ```

2. **Validasi Data**
    - Saat tombol "Simpan" ditekan, maka method `_submitForm()` dipanggil
    - Form divalidasi menggunakan `_formKey.currentState!.validate()`

3. **Persiapan Data untuk Passing**
    - Jika validasi berhasil, data diambil dari controller melalui:
      ```dart
      String nama = _namaController.text; 
      String nim = _nimController.text;
      int tahun = int.parse(_tahunController.text);
      ```

4. **Navigasi dan Passing Data**
    - Menggunakan `Navigator.push()` untuk berpindah ke `TampilData`
    - Data dilempar sebagai parameter konstruktor:
      ```dart
      Navigator.of(context).push(MaterialPageRoute(
        builder: (context) => TampilData(nama: nama, nim: nim, tahun: tahun),
      ));
      ```

5. **Penerimaan Data di TampilData**
    - `TampilData` menerima data melalui konstruktor:
      ```dart
      const TampilData({
        Key? key,
        required this.nama,
        required this.nim,
        required this.tahun,
      }) : super(key: key);
      ```

6. **Penggunaan Data di TampilData**
    - Data yang diterima digunakan untuk menampilkan hasil dari inputan pengguna:
      ```dart
      Text(
        nama,
        style: const TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
      ),
      Text(
        "NIM: $nim",
        style: const TextStyle(fontSize: 18, color: Colors.grey),
      ),
      Text(
        "Lahir Tahun: $tahun",
        style: const TextStyle(fontSize: 18, color: Colors.grey),
      ),
      ```

## Screenshot
Contoh :
![Lampiran Form](form.png)
![Lampiran Hasil](hasil.png)
