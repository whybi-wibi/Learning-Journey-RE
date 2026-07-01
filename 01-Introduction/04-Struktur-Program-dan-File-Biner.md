# 📦 Struktur Program dan File Biner

> *"Sebelum memahami bagaimana sebuah program bekerja, kita harus mengetahui bagaimana program tersebut disusun."*

---

# 📖 Pendahuluan

Ketika sebuah program selesai dikompilasi, hasilnya bukan lagi source code, melainkan sebuah **file executable (binary)**.

File executable berisi informasi yang dibutuhkan sistem operasi untuk menjalankan program, seperti:

- Instruksi program
- Data
- Informasi library
- Entry Point
- Header
- Section

Dalam Reverse Engineering, memahami struktur file biner merupakan langkah awal sebelum melakukan analisis lebih mendalam. Dengan mengetahui bagaimana sebuah executable disusun, seorang analis dapat menentukan lokasi kode, data, serta alur eksekusi program. :contentReference[oaicite:0]{index=0}

---

# 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, diharapkan mampu:

- Memahami apa itu file executable.
- Mengenal format PE dan ELF.
- Memahami struktur section pada executable.
- Mengetahui Entry Point sebuah program.
- Mengenal navigasi dasar menggunakan IDA Free.

---

# 📁 Apa itu File Executable?

File executable adalah file yang dapat dijalankan langsung oleh sistem operasi.

Contoh:

Windows

```text
.exe
.dll
.sys
```

Linux

```text
ELF
```

macOS

```text
Mach-O
```

Setiap sistem operasi memiliki format executable yang berbeda.

---

# 🪟 Portable Executable (PE)

Pada Windows, executable menggunakan format **Portable Executable (PE)**.

Struktur sederhananya:

```text
+----------------------+
| DOS Header           |
+----------------------+
| PE Header            |
+----------------------+
| Section Table        |
+----------------------+
| .text                |
+----------------------+
| .data                |
+----------------------+
| .rdata               |
+----------------------+
| .idata               |
+----------------------+
| .rsrc                |
+----------------------+
```

PE Header menyimpan informasi penting mengenai executable, termasuk alamat virtual section, ukuran kode, dan informasi lain yang digunakan oleh sistem operasi saat memuat program ke memori. :contentReference[oaicite:1]{index=1}

---

# 🐧 ELF (Executable and Linkable Format)

Pada Linux, executable menggunakan format **ELF (Executable and Linkable Format)**.

Walaupun berbeda format dengan PE, konsep dasarnya hampir sama.

ELF juga memiliki:

- Header
- Section
- Segment
- Entry Point

---

# 📚 Section pada Executable

Executable dibagi menjadi beberapa **section**, yang masing-masing memiliki fungsi tertentu.

| Section | Fungsi |
|----------|--------|
| `.text` | Berisi instruksi program (kode yang dieksekusi) |
| `.data` | Menyimpan data yang dapat diubah |
| `.rdata` | Menyimpan data konstan, seperti string |
| `.idata` | Menyimpan informasi Import Function |
| `.rsrc` | Menyimpan resource (ikon, gambar, dialog) |

---

## `.text`

Berisi kode Assembly hasil kompilasi.

Contoh:

```asm
mov eax,1
call printf
ret
```

Inilah bagian yang paling sering dianalisis oleh Reverse Engineer.

---

## `.data`

Berisi variabel yang nilainya dapat berubah selama program berjalan.

Contoh:

```c
int counter = 10;
```

---

## `.rdata`

Berisi data yang bersifat tetap (*read-only*).

Contohnya:

```text
"Login Successful"
"Username"
"Password"
```

String pada section ini sering menjadi petunjuk penting saat menganalisis sebuah program. :contentReference[oaicite:2]{index=2}

---

# 🚀 Entry Point

## Apa itu Entry Point?

Entry Point adalah alamat pertama yang dijalankan ketika sebuah program dieksekusi.

```text
Program Start
      │
      ▼
Entry Point
      │
      ▼
main()
```

Dalam praktik Reverse Engineering, menemukan Entry Point merupakan salah satu langkah pertama untuk memahami alur eksekusi program. Tools seperti IDA Free akan menampilkan lokasi Entry Point secara otomatis. :contentReference[oaicite:3]{index=3}

---

# 🔍 Navigasi Dasar pada IDA Free

IDA Free menyediakan berbagai fitur untuk mempermudah analisis file biner.

---

## 1. Functions Window

Menampilkan seluruh fungsi yang berhasil dikenali.

```
main
sub_140001000
printf
```

---

## 2. Strings Window

Menampilkan seluruh string yang terdapat di dalam executable.

Contoh:

```text
Login Failed
Administrator
Password
```

String sering menjadi petunjuk awal untuk memahami fungsi suatu program.

---

## 3. Cross References (Xrefs)

Cross References (**Xrefs**) menunjukkan di mana suatu fungsi, variabel, atau string digunakan.

Contoh:

```text
printf

Referenced from:

main()
login()
error_handler()
```

Fitur ini sangat membantu untuk melacak hubungan antarbagian program. :contentReference[oaicite:4]{index=4}

---

## 4. Graph View

Graph View menampilkan alur eksekusi program dalam bentuk diagram.

```text
          Start
            │
            ▼
        Compare
       /       \
     True     False
      │          │
      ▼          ▼
 Success      Failed
```

Tampilan ini lebih mudah dipahami dibanding hanya melihat instruksi Assembly secara linear. :contentReference[oaicite:5]{index=5}

---

## 5. Linear View

Menampilkan seluruh instruksi Assembly secara berurutan.

```asm
mov eax,1
cmp eax,2
jne failed
call success
```

Mode ini cocok untuk membaca instruksi secara detail.

---

# 🧠 Workflow Analisis Sederhana

Ketika membuka executable menggunakan IDA Free, alur analisis umumnya sebagai berikut:

```text
Open Executable
        │
        ▼
Lihat Entry Point
        │
        ▼
Cari main()
        │
        ▼
Lihat Strings
        │
        ▼
Gunakan Xrefs
        │
        ▼
Analisis Function
        │
        ▼
Pahami Logika Program
```

---

# 💡 Tips Reverse Engineering

Saat pertama kali membuka sebuah executable:

- Jangan langsung membaca seluruh Assembly.
- Mulailah dari **Entry Point**.
- Periksa daftar **Functions**.
- Cari **Strings** yang menarik.
- Gunakan **Xrefs** untuk melihat hubungan antar fungsi.
- Gunakan **Graph View** untuk memahami alur program.

Pendekatan ini akan membuat proses analisis menjadi lebih terstruktur dan efisien.

---

# 📝 Kesimpulan

Executable memiliki struktur internal yang dirancang agar sistem operasi dapat memuat dan menjalankan program dengan benar.

Dalam Reverse Engineering, memahami struktur file biner seperti **PE** atau **ELF**, mengenali fungsi setiap section, serta memanfaatkan fitur navigasi seperti **Strings**, **Cross References**, dan **Graph View** merupakan keterampilan dasar yang sangat penting. Dengan memahami struktur ini, seorang analis tidak hanya mengetahui **apa** isi file, tetapi juga **bagaimana** program bekerja pada level sistem. :contentReference[oaicite:6]{index=6}

---

# 🚀 Selanjutnya

➡️ **02 - Teknik Analisis Statis**
