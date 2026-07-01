# 🔍 Teknik Analisis Statis

> *"The safest way to understand a program is to inspect it before it runs."*

---

# 📖 Pendahuluan

Static Analysis adalah teknik menganalisis sebuah program **tanpa menjalankannya**. Pendekatan ini memungkinkan seorang Reverse Engineer mempelajari struktur, logika, serta karakteristik sebuah executable dengan aman, terutama ketika program yang dianalisis berpotensi berbahaya seperti malware.

Karena program tidak dieksekusi, risiko terhadap sistem menjadi sangat kecil. Oleh sebab itu, Static Analysis hampir selalu menjadi langkah pertama dalam proses Reverse Engineering. :contentReference[oaicite:0]{index=0}

---

# 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, Anda diharapkan mampu:

- Memahami konsep Static Analysis.
- Mengetahui manfaat Static Analysis dalam Reverse Engineering.
- Mengenal komponen penting yang dianalisis.
- Memahami alur kerja Static Analysis.
- Menyiapkan dasar sebelum melakukan studi kasus.

---

# 📌 Apa itu Static Analysis?

Static Analysis adalah proses mempelajari executable tanpa menjalankan program tersebut.

Informasi yang dapat diperoleh antara lain:

- Struktur executable
- Library yang digunakan
- String yang tersimpan
- Fungsi-fungsi program
- Import dan Export
- Alur logika program
- Indikasi perilaku program

Semua informasi tersebut diperoleh hanya dari hasil pembacaan file biner.

---

# 🔄 Workflow Static Analysis

```text
Executable (.exe)
        │
        ▼
Identifikasi File
        │
        ▼
Melihat Header
        │
        ▼
Analisis Section
        │
        ▼
Analisis Strings
        │
        ▼
Analisis Function
        │
        ▼
Cross References
        │
        ▼
Memahami Logika Program
```

---

# ⭐ Mengapa Static Analysis Penting?

Static Analysis memiliki beberapa keuntungan:

- Aman karena program tidak dijalankan.
- Cepat untuk memperoleh gambaran awal.
- Dapat menemukan indikator penting sebelum analisis dinamis.
- Membantu memahami struktur internal executable.
- Mengurangi risiko menjalankan malware.

Karena alasan tersebut, Static Analysis sering menjadi tahap awal dalam investigasi software maupun malware. :contentReference[oaicite:1]{index=1}

---

# 🧩 Komponen Penting dalam Static Analysis

## 1. File Header

Header berisi informasi penting mengenai executable, seperti:

- Arsitektur
- Entry Point
- Ukuran file
- Compiler
- Format executable

---

## 2. Sections

Beberapa section yang umum dijumpai:

| Section | Fungsi |
|----------|--------|
| `.text` | Kode program |
| `.data` | Data yang dapat diubah |
| `.rdata` | Data konstan |
| `.idata` | Import Function |
| `.rsrc` | Resource aplikasi |

---

## 3. Strings

String sering memberikan petunjuk mengenai perilaku program.

Contoh:

```text
Password
Login Failed
Administrator
cmd.exe
kernel32.dll
```

Dari string tersebut kita dapat memperkirakan fungsi program bahkan sebelum melihat Assembly.

---

## 4. Imports

Import menunjukkan API atau library yang digunakan.

Contoh:

```text
CreateFileA()
ReadFile()
WriteFile()
MessageBoxA()
```

Jika ditemukan fungsi seperti:

```text
InternetOpenURL()
```

kemungkinan program berkomunikasi melalui jaringan.

---

## 5. Functions

Disassembler biasanya akan mengenali fungsi-fungsi dalam executable.

Contoh:

```text
main()
login()
encrypt()
decrypt()
```

Analisis fungsi membantu memahami logika utama program.

---

## 6. Cross References (Xrefs)

Cross References menunjukkan hubungan antar fungsi, variabel, maupun string.

Contoh:

```text
main()

↓

login()

↓

encrypt()

↓

sendData()
```

Dengan melihat Xrefs, seorang analis dapat mengikuti alur eksekusi program secara lebih sistematis. :contentReference[oaicite:2]{index=2}

---

# 🧠 Membangun Hipotesis

Static Analysis bukan sekadar membaca Assembly.

Seorang Reverse Engineer harus mulai membangun hipotesis berdasarkan bukti yang ditemukan.

Contoh:

### Ditemukan:

```text
AES_encrypt()
```

Hipotesis:

> Program kemungkinan melakukan proses enkripsi.

---

### Ditemukan:

```text
strcmp()
```

Hipotesis:

> Program kemungkinan melakukan proses autentikasi atau validasi input.

---

### Ditemukan:

```text
WinExec()
```

Hipotesis:

> Program mungkin menjalankan proses lain.

Kemampuan menghubungkan bukti-bukti kecil menjadi gambaran besar merupakan salah satu keterampilan utama dalam Static Analysis. :contentReference[oaicite:3]{index=3}

---

# ⚠️ Tantangan Static Analysis

Tidak semua executable mudah dipahami.

Beberapa tantangan yang sering ditemui:

- Compiler Optimization
- Code Obfuscation
- Packed Executable
- Anti Reverse Engineering
- Nama fungsi yang hilang

Akibatnya, hasil disassembly bisa terlihat rumit atau tidak langsung mencerminkan logika program asli. :contentReference[oaicite:4]{index=4}

---

# 💡 Tips Melakukan Static Analysis

- Mulai dari informasi umum sebelum membaca Assembly.
- Periksa Header dan Section terlebih dahulu.
- Cari Strings yang menarik.
- Analisis Imports.
- Gunakan Cross References untuk menelusuri hubungan antar fungsi.
- Jangan langsung menyimpulkan; bangun hipotesis berdasarkan bukti.

---

# 📝 Kesimpulan

Static Analysis merupakan fondasi penting dalam Reverse Engineering karena memungkinkan seorang analis memahami struktur dan kemungkinan perilaku sebuah program tanpa harus menjalankannya.

Melalui analisis terhadap header, section, strings, imports, functions, dan cross references, seorang Reverse Engineer dapat menyusun hipotesis mengenai cara kerja program. Walaupun hasil analisis terkadang dipengaruhi oleh optimasi compiler atau teknik obfuscation, pendekatan ini tetap menjadi langkah awal yang aman dan efektif sebelum beralih ke Dynamic Analysis. :contentReference[oaicite:5]{index=5}

---

# 🚀 Selanjutnya

➡️ **02 - Studi Kasus Static Analysis**

Pada materi berikutnya kita akan menerapkan konsep-konsep di atas untuk menganalisis sebuah executable menggunakan tools Reverse Engineering.
