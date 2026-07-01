# 🖥️ Dasar-Dasar Assembly 64-bit

> *"Assembly is the language of the processor. Understanding it means understanding what the computer is actually doing."*

---

# 📖 Pendahuluan

Assembly adalah bahasa pemrograman tingkat rendah (*low-level language*) yang menjadi jembatan antara **Machine Code** dan **High-Level Language** seperti C, C++, atau Python.

Dalam pengembangan perangkat lunak modern, programmer jarang menulis aplikasi menggunakan Assembly secara langsung. Namun, dalam **Reverse Engineering**, pemahaman terhadap Assembly menjadi keterampilan yang sangat penting karena hasil disassembly hampir selalu ditampilkan dalam bentuk instruksi Assembly. :contentReference[oaicite:0]{index=0}

---

# 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, diharapkan mampu:

- Memahami struktur dasar instruksi Assembly.
- Mengenal register pada arsitektur x86-64.
- Memahami operasi dasar pada data.
- Memahami bagaimana program melakukan percabangan dan perulangan.
- Membaca Assembly sederhana saat melakukan Reverse Engineering.

---

# 🏗️ Struktur Instruksi Assembly

Setiap instruksi Assembly umumnya memiliki format berikut:

```asm
Mnemonic Operand1, Operand2
```

Contoh:

```asm
mov eax, 5
```

Penjelasan:

| Bagian | Keterangan |
|---------|------------|
| mov | Instruksi (Mnemonic) |
| eax | Register tujuan |
| 5 | Nilai yang akan dipindahkan |

Artinya:

> Salin nilai **5** ke dalam register **EAX**.

---

Contoh lain:

```asm
add eax, ebx
```

Artinya:

```text
EAX = EAX + EBX
```

---

# 🧠 Register

## Apa itu Register?

Register adalah memori kecil yang berada langsung di dalam CPU.

Register memiliki kecepatan yang jauh lebih tinggi dibandingkan RAM sehingga digunakan processor untuk menyimpan data sementara ketika menjalankan instruksi.

---

## Register Umum (General Purpose Register)

| Register | Fungsi |
|----------|---------|
| RAX | Akumulator / hasil operasi |
| RBX | Base Register |
| RCX | Counter |
| RDX | Data Register |
| RSI | Source Index |
| RDI | Destination Index |
| RBP | Base Pointer |
| RSP | Stack Pointer |

---

## Contoh

```asm
mov rax,10
mov rbx,20
add rax,rbx
```

Hasil:

```text
RAX = 30
```

---

# ⚙️ Instruksi dan Operasi Data

Berikut beberapa instruksi Assembly yang paling sering dijumpai.

---

## MOV

Memindahkan data.

```asm
mov rax,5
```

---

## ADD

Penjumlahan.

```asm
add rax,10
```

---

## SUB

Pengurangan.

```asm
sub rax,2
```

---

## INC

Menambah satu.

```asm
inc rax
```

---

## DEC

Mengurangi satu.

```asm
dec rax
```

---

## MUL

Perkalian.

```asm
mul rbx
```

---

## DIV

Pembagian.

```asm
div rbx
```

---

## CMP

Membandingkan dua nilai.

```asm
cmp eax,ebx
```

Biasanya instruksi ini akan diikuti oleh instruksi **Jump**.

---

# 🔀 Kontrol Program

Kontrol program menentukan bagaimana alur eksekusi berpindah dari satu instruksi ke instruksi lainnya.

---

## JMP

Melompat tanpa syarat.

```asm
jmp label
```

---

## JE (Jump if Equal)

Melompat jika hasil perbandingan sama.

```asm
cmp eax,ebx
je sama
```

---

## JNE (Jump if Not Equal)

Melompat jika berbeda.

```asm
cmp eax,ebx
jne beda
```

---

## CALL

Memanggil fungsi.

```asm
call printf
```

---

## RET

Mengembalikan kontrol ke fungsi pemanggil.

```asm
ret
```

---

# 🔁 Contoh Percabangan

Kode C:

```c
if(a == b)
{
    printf("Sama");
}
```

Kurang lebih akan menjadi:

```asm
cmp eax,ebx
je sama

...

sama:
call printf
```

---

# 🔁 Contoh Perulangan

Kode C:

```c
for(int i=0;i<5;i++)
```

Assembly sederhananya:

```asm
mov ecx,0

loop:

inc ecx

cmp ecx,5

jl loop
```

Instruksi **JL (Jump if Less)** digunakan untuk kembali ke label `loop` selama nilai `ECX` masih kurang dari 5.

---

# 📚 Pola yang Sering Ditemui

Dalam Reverse Engineering, kita tidak perlu menghafal seluruh instruksi Assembly.

Yang lebih penting adalah mengenali pola seperti:

- Function Call
- Percabangan (if-else)
- Perulangan (loop)
- Operasi matematika
- Perbandingan nilai
- Akses memori

Kemampuan mengenali pola ini akan sangat membantu saat menganalisis program yang lebih kompleks. :contentReference[oaicite:1]{index=1}

---

# 💡 Tips Belajar Assembly

- Jangan mencoba menghafal seluruh instruksi.
- Fokus memahami fungsi register.
- Kenali pola instruksi yang sering muncul.
- Banyak berlatih membaca hasil disassembly.
- Gunakan tools seperti Ghidra atau x64dbg untuk melihat hubungan antara Assembly dan logika program.

---

# 📝 Kesimpulan

Assembly adalah bahasa yang digunakan processor untuk menjalankan instruksi secara langsung.

Dalam Reverse Engineering, tujuan utama mempelajari Assembly bukanlah menjadi programmer Assembly, melainkan mampu membaca dan menginterpretasikan logika sebuah program melalui pola instruksi yang dihasilkan compiler.

Dengan memahami struktur instruksi, register, operasi data, dan kontrol program, kita akan memiliki fondasi yang kuat untuk melanjutkan ke materi **PE File Structure**, **Static Analysis**, dan **Dynamic Analysis**. :contentReference[oaicite:2]{index=2}

---

# 🚀 Selanjutnya

➡️ **04 - Struktur Program dan File Biner**
