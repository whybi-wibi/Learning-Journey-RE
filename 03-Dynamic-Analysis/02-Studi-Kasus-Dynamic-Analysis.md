# 🧪 Studi Kasus Dynamic Analysis

> *"Static Analysis builds the hypothesis. Dynamic Analysis proves it."*

---

# 📖 Pendahuluan

Setelah memahami konsep Dynamic Analysis, langkah berikutnya adalah menerapkannya pada sebuah **binary executable**.

Melalui studi kasus ini, kita akan mengamati bagaimana program berjalan secara langsung menggunakan debugger. Tujuan utamanya bukan hanya menjalankan program, tetapi juga memverifikasi hipotesis yang telah dibangun selama proses Static Analysis.

Dynamic Analysis memungkinkan seorang Reverse Engineer melihat bagaimana input diproses, bagaimana register berubah, serta bagaimana program mengambil keputusan pada saat runtime. :contentReference[oaicite:1]{index=1}

---

# 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, Anda diharapkan mampu:

- Menjalankan executable menggunakan debugger.
- Menggunakan breakpoint secara efektif.
- Memahami perbedaan Step Into dan Step Over.
- Mengamati perubahan register dan memori.
- Memvalidasi hipotesis dari Static Analysis.
- Mendokumentasikan hasil analisis.

---

# 📂 Studi Kasus

Misalkan kita memiliki executable berikut.

```text
password_checker.exe
```

Target analisis:

- Memahami proses autentikasi.
- Mengidentifikasi fungsi validasi password.
- Mengamati perubahan register.
- Mengetahui bagaimana input diproses.
- Memverifikasi hasil Static Analysis.

---

# 🔄 Workflow Dynamic Analysis

```text
Executable
      │
      ▼
Jalankan Debugger
      │
      ▼
Pasang Breakpoint
      │
      ▼
Masukkan Input
      │
      ▼
Step Through Program
      │
      ▼
Analisis Register
      │
      ▼
Analisis Memori
      │
      ▼
Verifikasi Hipotesis
```

---

# 🔍 Langkah 1 — Overview Program

Sebelum melakukan debugging, lakukan observasi terhadap executable.

Beberapa informasi awal yang perlu diketahui:

- Arsitektur program.
- Entry Point.
- Fungsi utama.
- Compiler.
- Hasil Static Analysis sebelumnya.

Informasi ini membantu menentukan lokasi yang tepat untuk memasang breakpoint.

---

# 🔍 Langkah 2 — Menentukan Breakpoint

Breakpoint digunakan untuk menghentikan eksekusi program pada bagian yang ingin dianalisis.

Contohnya:

```text
main()

↓

checkPassword()

↓

strcmp()
```

Breakpoint sebaiknya dipasang pada fungsi yang berkaitan dengan proses autentikasi atau logika utama program agar analisis lebih terarah. :contentReference[oaicite:2]{index=2}

---

# 🔍 Langkah 3 — Menjalankan Program

Setelah breakpoint dipasang:

1. Jalankan executable.
2. Masukkan input.
3. Tunggu hingga debugger berhenti pada breakpoint.

Pada titik ini kita dapat mulai mengamati kondisi program.

---

# 🔍 Langkah 4 — Mengamati Register

Debugger akan menampilkan isi register secara real-time.

Contoh:

```text
RAX = 00000001

RCX = 00000008

RDX = 00000000
```

Perhatikan perubahan nilai register sebelum dan sesudah instruksi tertentu karena perubahan tersebut sering kali menunjukkan bagaimana program memproses data atau melakukan perbandingan. :contentReference[oaicite:3]{index=3}

---

# 🔍 Langkah 5 — Step Into dan Step Over

Debugger menyediakan dua metode utama untuk menelusuri eksekusi program.

## Step Into

Masuk ke dalam fungsi yang dipanggil.

```text
main()

↓

checkPassword()

↓

strcmp()
```

Digunakan ketika ingin mengetahui isi fungsi secara detail.

---

## Step Over

Menjalankan fungsi tanpa masuk ke dalamnya.

```text
main()

↓

checkPassword()

↓

(next instruction)
```

Lebih efisien untuk melewati fungsi library atau bagian yang bukan fokus analisis. :contentReference[oaicite:4]{index=4}

---

# 🔍 Langkah 6 — Analisis Memori

Selain register, debugger juga memungkinkan kita melihat isi memori.

Contoh informasi yang dapat ditemukan:

- Password yang dimasukkan.
- Buffer input.
- Array karakter.
- Data hasil dekripsi.
- Variabel sementara.

Dengan mengamati memori, kita dapat memahami bagaimana data berubah selama eksekusi.

---

# 🔁 Uji dengan Berbagai Input

Satu kali eksekusi belum tentu cukup.

Cobalah beberapa variasi input:

```text
admin

password

123456

abcdef

admin123
```

Bandingkan perubahan:

- Register.
- Memori.
- Branching.
- Hasil autentikasi.

Melakukan pengujian berulang akan membantu menemukan pola perilaku program yang konsisten. :contentReference[oaicite:5]{index=5}

---

# 📝 Dokumentasikan Temuan

Selama proses analisis, catat informasi berikut:

- Lokasi breakpoint.
- Nilai register.
- Isi memori.
- Percabangan yang terjadi.
- Fungsi yang dipanggil.
- Hasil setiap pengujian.

Dokumentasi yang baik memudahkan proses analisis lanjutan dan membantu memastikan bahwa kesimpulan yang diambil didukung oleh bukti. :contentReference[oaicite:6]{index=6}

---

# ⚠️ Hal yang Perlu Diperhatikan

Dynamic Analysis dipengaruhi oleh kondisi runtime.

Beberapa faktor yang dapat memengaruhi hasil:

- Input pengguna.
- Konfigurasi sistem.
- Nilai register awal.
- Kondisi memori.
- Lingkungan eksekusi.

Karena itu, hasil dari satu kali eksekusi belum tentu mewakili seluruh perilaku program.

---

# 💡 Tips Dynamic Analysis

- Lakukan Static Analysis terlebih dahulu.
- Pasang breakpoint pada fungsi penting.
- Gunakan Step Into hanya ketika diperlukan.
- Perhatikan perubahan register dan memori.
- Lakukan pengujian dengan berbagai input.
- Dokumentasikan setiap hasil pengamatan.

---

# 📝 Kesimpulan

Studi Kasus Dynamic Analysis menunjukkan bagaimana seorang Reverse Engineer memvalidasi hasil Static Analysis melalui pengamatan langsung terhadap perilaku program saat runtime.

Dengan menggunakan debugger, analis dapat melihat perubahan register, memori, serta alur eksekusi secara detail. Pendekatan ini memungkinkan hipotesis yang sebelumnya hanya didasarkan pada hasil disassembly diuji secara nyata. Kombinasi Static Analysis dan Dynamic Analysis memberikan pemahaman yang lebih lengkap mengenai cara kerja sebuah program. :contentReference[oaicite:7]{index=7}

---

# 🚀 Selanjutnya

➡️ **Section 4 – Teknik Anti-Reverse Engineering**

Pada section berikutnya kita akan mempelajari berbagai teknik yang digunakan pengembang atau malware untuk menghambat proses Reverse Engineering, seperti packing, obfuscation, dan anti-debugging.
