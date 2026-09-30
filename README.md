# PDF Sentence Extractor (Java)

Program Java sederhana yang membaca file PDF, memecah teks setiap halaman menjadi kalimat-kalimat, lalu menuliskan hasilnya ke file `output.txt`. Program ini memanfaatkan **Generics** dan dibuat sebagai tugas mata kuliah Pemrograman Berorientasi Objek.

## Fitur

- Membaca PDF per halaman menggunakan Apache PDFBox
- Memecah teks halaman menjadi kalimat dengan `BreakIterator` bawaan Java
- Menyimpan kalimat per halaman dalam class generic `Halaman<T>`
- Menulis hasil ke file `output.txt` (UTF-8)

## Teknologi

- Java (JDK 17 atau lebih baru disarankan)
- Maven
- Apache PDFBox 3.0.3
- IntelliJ IDEA

## Struktur Project

```
src/main/java/
├── Main.java            # Alur utama: baca PDF, pisah kalimat, tulis ke txt
├── PdfFileReader.java   # Membaca teks PDF per halaman
├── Halaman.java         # Class generic Halaman<T> (nomor halaman + isi)
├── Viewer.java          # (Opsional) Interface generic untuk menampilkan data
└── ConsoleViewer.java   # (Opsional) Implementasi Viewer lewat System.out
```

## Konsep Generics yang Digunakan

`Halaman<T>` adalah class generic yang menampung nomor halaman dan daftar isi bertipe `T`. Pada program ini `T` adalah `String` (satu kalimat), tetapi class yang sama dapat dipakai untuk tipe data lain tanpa menulis ulang.

```java
Halaman<String> h = new Halaman<>(1, listKalimat);
```

## Cara Menjalankan

1. Clone repository ini:
   ```bash
   git clone https://github.com/USERNAME/NAMA-REPO.git
   ```
2. Buka project di IntelliJ IDEA dan tunggu Maven selesai mengunduh dependency (klik **Load Maven Changes** jika diminta).
3. Letakkan file PDF di folder root project dengan nama `sample.pdf`.
4. Jalankan `Main.java`.
5. Hasil akan muncul di file `output.txt` pada folder root project.

## Contoh Output

```
=== Halaman 1 ===
1. Kalimat pertama pada halaman ini.
2. Kalimat kedua pada halaman ini.

=== Halaman 2 ===
1. Kalimat pertama pada halaman kedua.
```

## Catatan dan Keterbatasan

- Pemecah kalimat otomatis dapat memotong singkatan seperti "S.H." atau "M.Hum." di tengah.
- PDF yang memiliki watermark bisa menghasilkan huruf tambahan yang tidak beraturan pada hasil ekstraksi.
- PDF hasil scan (berupa gambar) tidak dapat dibaca karena PDFBox hanya mengekstrak teks, bukan melakukan OCR.
- File `sample.pdf` tidak disertakan di repository. Gunakan PDF milik sendiri.

## Pengembangan Selanjutnya

- Menampilkan hasil ke console atau GUI melalui `Viewer<T>`
- Mendukung format output lain seperti CSV atau JSON
- Meningkatkan akurasi pemecahan kalimat untuk singkatan

## Penulis

Dibuat oleh **Dzikri Ngesti Adjie Widodo** untuk tugas mata kuliah Struktur Data dengan Dosen Pengampu: Ir. Galih Wasis Wicaksono, S.kom. M.Cs.
