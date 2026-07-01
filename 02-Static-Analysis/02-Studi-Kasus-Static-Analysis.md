# 🔬 Studi Kasus Static Analysis

> *"A Reverse Engineer doesn't just read instructions—they reconstruct the story behind the program."*

---

# 📖 Pendahuluan

Setelah memahami konsep dasar Static Analysis, langkah berikutnya adalah menerapkannya pada sebuah **binary executable**.

Melalui studi kasus, kita belajar bagaimana menghubungkan berbagai informasi yang ditemukan, seperti string, fungsi, Assembly, dan alur program, menjadi sebuah pemahaman yang utuh mengenai cara kerja aplikasi.

Berbeda dengan teori, studi kasus menuntut kemampuan berpikir analitis dan membangun hipotesis berdasarkan bukti yang ditemukan. :contentReference[oaicite:0]{index=0}

---

# 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, Anda diharapkan mampu:

- Menganalisis executable secara sistematis.
- Mengidentifikasi fungsi penting dalam program.
- Memanfaatkan Strings dan Cross References.
- Membaca logika program melalui Assembly.
- Mendokumentasikan hasil analisis.

---

# 📂 Studi Kasus

Misalkan kita memiliki executable berikut.

```text
password_checker.exe
```

Target kita bukan langsung mengetahui password yang benar.

Sebaliknya, kita ingin memahami:

- Apa fungsi program?
- Bagaimana proses validasi dilakukan?
- Bagaimana alur program bekerja?
- Apa saja API yang digunakan?

---

# 🛠 Workflow Analisis

Static Analysis biasanya dilakukan secara bertahap.

```text
Executable
      │
      ▼
Identifikasi File
      │
      ▼
Analisis Header
      │
      ▼
Analisis Sections
      │
      ▼
Mencari Strings
      │
      ▼
Melihat Cross References
      │
      ▼
Membaca Assembly
      │
      ▼
Membangun Hipotesis
```

Setiap langkah memberikan petunjuk yang akan membantu memahami perilaku program.

---

# 🔍 Langkah 1 — Overview Program

Sebelum membaca Assembly, lakukan observasi terhadap executable.

Beberapa informasi yang dapat diperoleh:

- Nama file
- Ukuran file
- Arsitektur (32-bit / 64-bit)
- Compiler
- Entry Point
- Library yang digunakan

Contoh:

```text
Architecture : x64

Compiler : Microsoft Visual C++

Entry Point : 0x140001000
```

Informasi awal ini membantu menentukan pendekatan analisis yang akan digunakan.

---

# 🔍 Langkah 2 — Melihat Strings

Strings sering kali memberikan petunjuk mengenai fungsi program.

Misalnya ditemukan:

```text
Enter Password

Access Granted

Access Denied
```

Dari informasi tersebut dapat diduga bahwa program memiliki mekanisme autentikasi.

Namun, analisis tidak berhenti di sini. Kita perlu mengetahui **di mana string tersebut digunakan**. :contentReference[oaicite:1]{index=1}

---

# 🔍 Langkah 3 — Menelusuri Cross References (Xrefs)

Misalkan string berikut ditemukan:

```text
Enter Password
```

Kemudian dilakukan pencarian **Cross References**.

```text
main()

↓

checkPassword()

↓

strcmp()

↓

result()
```

Dengan melihat Xrefs, kita dapat mengetahui hubungan antara string dengan fungsi-fungsi yang menggunakannya.

Ini membantu membangun gambaran mengenai alur program. :contentReference[oaicite:2]{index=2}

---

# 🔍 Langkah 4 — Membaca Assembly

Misalnya ditemukan instruksi berikut.

```asm
cmp eax,1
je success

jmp failed
```

Interpretasi:

```text
Bandingkan nilai EAX dengan 1.

Jika sama → masuk ke fungsi success.

Jika tidak → menuju fungsi failed.
```

Instruksi sederhana seperti ini sering digunakan untuk proses validasi.

---

# 🔁 Analisis Loop

Contoh:

```asm
mov ecx,0

loop:

inc ecx

cmp ecx,8

jl loop
```

Dari pola tersebut dapat diperkirakan bahwa program melakukan proses yang diulang sebanyak delapan kali.

Dalam praktik Reverse Engineering, penting untuk memperhatikan register yang digunakan pada loop karena kesalahan interpretasi dapat menyebabkan kesimpulan yang keliru. :contentReference[oaicite:3]{index=3}

---

# 🧠 Membangun Hipotesis

Static Analysis bukan hanya membaca kode, tetapi juga menyusun hipotesis berdasarkan bukti.

Contoh:

### Bukti

```text
strcmp()

↓

Access Granted
```

Hipotesis:

> Program membandingkan input pengguna dengan suatu nilai untuk menentukan apakah autentikasi berhasil.

---

### Bukti

```text
AES_encrypt()
```

Hipotesis:

> Program kemungkinan melakukan proses enkripsi.

---

### Bukti

```text
CreateFile()

↓

WriteFile()
```

Hipotesis:

> Program membuat dan menulis data ke sebuah file.

Semua hipotesis harus didukung oleh bukti yang ditemukan selama analisis.

---

# 📝 Dokumentasikan Hasil Analisis

Selama proses analisis, biasakan mencatat:

- Fungsi penting.
- String menarik.
- API yang digunakan.
- Dugaan fungsi setiap blok kode.
- Pertanyaan yang belum terjawab.

Memberikan komentar pada disassembly dan mencatat asumsi akan memudahkan saat melakukan analisis lanjutan maupun validasi di tahap berikutnya. :contentReference[oaicite:4]{index=4}

---

# ⚠️ Keterbatasan Static Analysis

Walaupun sangat bermanfaat, Static Analysis memiliki beberapa keterbatasan.

Misalnya:

- Tidak dapat melihat perubahan memori saat runtime.
- Tidak dapat mengamati input pengguna secara langsung.
- Sulit mengetahui perilaku program yang bergantung pada kondisi tertentu.
- Tidak dapat memastikan seluruh hipotesis tanpa pengujian.

Karena itu, hasil Static Analysis sebaiknya divalidasi melalui **Dynamic Analysis**, di mana program dijalankan dan diamati secara langsung. :contentReference[oaicite:5]{index=5}

---

# 💡 Tips Reverse Engineering

Saat melakukan Static Analysis:

- Mulailah dari informasi umum.
- Jangan langsung membaca seluruh Assembly.
- Cari Strings yang menarik.
- Gunakan Cross References.
- Dokumentasikan setiap temuan.
- Bangun hipotesis berdasarkan bukti, bukan asumsi.

---

# 📝 Kesimpulan

Studi kasus Static Analysis mengajarkan bahwa Reverse Engineering bukan sekadar membaca Assembly, tetapi menghubungkan berbagai petunjuk menjadi pemahaman yang utuh mengenai sebuah program.

Melalui analisis terhadap Strings, Cross References, Assembly, dan struktur executable, seorang Reverse Engineer dapat menyusun hipotesis mengenai fungsi dan tujuan program. Hasil analisis ini kemudian menjadi dasar untuk tahap berikutnya, yaitu **Dynamic Analysis**, guna memverifikasi apakah hipotesis tersebut sesuai dengan perilaku program saat dijalankan. :contentReference[oaicite:6]{index=6}

---

# 🚀 Selanjutnya

➡️ **Section 3 – Teknik Analisis Dinamis**

Pada section berikutnya, kita akan menjalankan executable dalam lingkungan yang aman untuk mengamati perilaku program secara langsung, memvalidasi hipotesis dari Static Analysis, serta memahami bagaimana program bekerja saat runtime.
