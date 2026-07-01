# 🛠️ Learning Journey #2
# Technical Foundations of Reverse Engineering

> *"Before understanding malware or vulnerabilities, you need to understand the language of the machine."*

---

# 📖 Overview

Pada materi sebelumnya kita mempelajari konsep **Forward Engineering** dan **Reverse Engineering**.

Sekarang kita akan masuk ke fondasi teknis yang wajib dipahami oleh seorang Reverse Engineer.

Materi ini akan membahas:

- Bahasa Assembly
- Disassembler
- Decompiler
- Debugger

Keempat konsep tersebut merupakan dasar yang akan selalu digunakan ketika melakukan analisis terhadap sebuah executable.

---

# 📌 Mengapa Fondasi Ini Penting?

Ketika sebuah program dikompilasi, source code yang ditulis menggunakan bahasa seperti:

- C
- C++
- Java
- Go
- Rust

tidak lagi tersimpan di dalam file executable.

Yang tersisa hanyalah **Machine Code** yang hanya dapat dipahami oleh processor.

Tugas seorang Reverse Engineer adalah mencoba memahami kembali bagaimana program tersebut bekerja.

---

# 🔄 Dari Source Code ke Machine Code

```text
Source Code (C/C++)
        │
        ▼
Compiler
        │
        ▼
Machine Code
        │
        ▼
Executable (.exe)
```

Saat melakukan Reverse Engineering proses tersebut dibalik.

```text
Executable (.exe)
        │
        ▼
Disassembler
        │
        ▼
Assembly
        │
        ▼
Decompiler
        │
        ▼
Pseudo C Code
```

---

# 🧩 1. Bahasa Assembly

## Apa itu Assembly?

Assembly adalah bahasa pemrograman tingkat rendah (Low-Level Language) yang sangat dekat dengan bahasa mesin (Machine Code).

Assembly menggambarkan instruksi yang benar-benar dijalankan oleh processor.

Contohnya:

```asm
mov eax, 5
add eax, 3
ret
```

Instruksi di atas berarti:

1. Memasukkan angka **5** ke register **EAX**
2. Menambahkan **3**
3. Mengakhiri fungsi

---

## Mengapa Assembly Penting?

Assembly memungkinkan kita melihat apa yang benar-benar dilakukan oleh komputer, bukan hanya apa yang ditulis oleh programmer.

Dengan memahami Assembly kita dapat:

- Membaca logika program
- Memahami fungsi-fungsi penting
- Menemukan vulnerability
- Menganalisis malware
- Memahami exploit

---

## Tantangan Assembly

Assembly sering dianggap sulit karena:

- Tidak menggunakan variabel seperti bahasa tingkat tinggi.
- Banyak menggunakan register.
- Harus memahami memori.
- Harus memahami CPU Architecture.

Namun semakin sering berlatih, pola-pola instruksi akan semakin mudah dikenali.

---

# 🔎 2. Disassembler

## Apa itu Disassembler?

Disassembler adalah tools yang mengubah Machine Code menjadi instruksi Assembly sehingga dapat dibaca manusia.

Tanpa Disassembler, file executable hanyalah kumpulan byte.

Contoh:

Machine Code

```text
B8 05 00 00 00
```

Disassembler

```asm
mov eax,5
```

---

## Fungsi Disassembler

- Membaca Assembly
- Menemukan Function
- Melihat Call Graph
- Mengetahui Import API
- Melihat Struktur Program

---

## Contoh Tools

- Ghidra
- IDA Free
- Cutter
- Radare2
- Hopper

---

# 🧠 3. Decompiler

## Apa itu Decompiler?

Decompiler mencoba menerjemahkan Assembly menjadi kode tingkat tinggi (Pseudo Code).

Decompiler **tidak mengembalikan source code asli**, melainkan menghasilkan kode yang mudah dipahami manusia.

Contoh hasil decompiler:

```c
int add(int a, int b)
{
    return a + b;
}
```

Padahal source code asli mungkin berbeda.

---

## Fungsi Decompiler

- Memahami logika program lebih cepat.
- Mempermudah analisis fungsi.
- Mempercepat Malware Analysis.
- Membantu Vulnerability Research.

---

## Kelebihan

- Lebih mudah dipahami dibanding Assembly.
- Mempercepat analisis.

## Kekurangan

- Tidak selalu akurat.
- Nama variabel hilang.
- Komentar hilang.
- Struktur program dapat berubah.

---

## Contoh Tools

- Ghidra
- IDA Pro
- RetDec

---

# 🐞 4. Debugger

## Apa itu Debugger?

Debugger adalah tools yang memungkinkan kita menjalankan program langkah demi langkah (Step by Step).

Dengan Debugger kita dapat melihat apa yang terjadi saat program berjalan.

---

## Fungsi Debugger

- Menjalankan program per instruksi
- Melihat isi register
- Melihat isi memori
- Memasang breakpoint
- Mengubah nilai memori
- Menganalisis perilaku malware

---

## Contoh Tools

- x64dbg
- WinDbg
- OllyDbg

---

# 📊 Perbandingan

| Tools | Digunakan Saat | Hasil |
|--------|---------------|-------|
| Disassembler | Sebelum Program Dijalankan | Assembly |
| Decompiler | Sebelum Program Dijalankan | Pseudo C |
| Debugger | Saat Program Berjalan | Runtime Analysis |

---

# 💡 Hubungan Ketiga Tools

```text
Executable
      │
      ▼
Disassembler
      │
      ▼
Assembly
      │
      ├──────────────┐
      ▼              │
Decompiler           │
      │              │
      ▼              │
Pseudo Code          │
                     │
                     ▼
                 Debugger
                     │
                     ▼
            Runtime Behavior
```

Ketiga tools ini saling melengkapi.

- **Disassembler** membantu memahami detail instruksi.
- **Decompiler** membantu melihat logika program secara lebih mudah.
- **Debugger** membantu mengamati perilaku program saat dijalankan.

---

# 🎯 Kesimpulan

Fondasi teknis Reverse Engineering terdiri dari empat komponen utama:

- **Assembly** → Memahami bahasa yang dijalankan processor.
- **Disassembler** → Mengubah Machine Code menjadi Assembly.
- **Decompiler** → Mengubah Assembly menjadi Pseudo Code.
- **Debugger** → Mengamati perilaku program saat runtime.

Perlu diingat bahwa tools hanyalah alat bantu. Hasil analisis tidak selalu sempurna, sehingga seorang Reverse Engineer harus menggabungkan informasi dari berbagai tools dengan pemahaman logika pemrograman dan kemampuan berpikir analitis untuk memahami apa yang sebenarnya dilakukan oleh sebuah program.
