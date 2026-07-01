# 🚀 Teknik Analisis Dinamis

> *"Static Analysis tells you what the code looks like. Dynamic Analysis tells you what the code actually does."*

---

# 📖 Pendahuluan

Dynamic Analysis adalah teknik menganalisis sebuah program dengan **menjalankannya secara langsung**. Berbeda dengan Static Analysis yang hanya memeriksa struktur executable, Dynamic Analysis memungkinkan kita mengamati bagaimana program berperilaku saat dieksekusi.

Melalui pendekatan ini, seorang Reverse Engineer dapat melihat perubahan register, penggunaan memori, pemanggilan fungsi, hingga alur kontrol program secara nyata. Informasi tersebut sangat berguna untuk memverifikasi hipotesis yang telah dibuat pada tahap Static Analysis. :contentReference[oaicite:1]{index=1}

---

# 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, Anda diharapkan mampu:

- Memahami konsep Dynamic Analysis.
- Mengetahui manfaat Dynamic Analysis.
- Mengenal workflow Dynamic Analysis.
- Memahami komponen penting yang diamati saat runtime.
- Mengenal dasar penggunaan debugger.

---

# 📌 Apa itu Dynamic Analysis?

Dynamic Analysis adalah proses menganalisis executable **dengan menjalankan program tersebut**.

Berbeda dengan Static Analysis, kita dapat melihat secara langsung bagaimana program:

- Memproses data.
- Mengubah isi register.
- Mengakses memori.
- Memanggil fungsi.
- Berinteraksi dengan sistem operasi.
- Merespons input pengguna.

---

# 🔄 Workflow Dynamic Analysis

```text
Executable (.exe)
        │
        ▼
Menjalankan Program
        │
        ▼
Breakpoint
        │
        ▼
Step Into / Step Over
        │
        ▼
Analisis Register
        │
        ▼
Analisis Memori
        │
        ▼
Mengamati Perilaku Program
        │
        ▼
Memvalidasi Hipotesis
```

---

# ⭐ Mengapa Dynamic Analysis Penting?

Dynamic Analysis memberikan informasi yang tidak dapat diperoleh hanya dari membaca executable.

Beberapa manfaatnya antara lain:

- Mengamati perilaku program secara langsung.
- Memvalidasi hasil Static Analysis.
- Mengetahui bagaimana data diproses.
- Melihat perubahan register dan memori.
- Memahami alur eksekusi program.

Karena itu, Dynamic Analysis menjadi pelengkap yang sangat penting dalam Reverse Engineering. :contentReference[oaicite:2]{index=2}

---

# 🧩 Komponen Penting dalam Dynamic Analysis

## 1. Breakpoint

Breakpoint digunakan untuk menghentikan eksekusi program pada instruksi tertentu.

Dengan breakpoint, analis dapat memeriksa kondisi program sebelum instruksi dijalankan.

---

## 2. Step Into

**Step Into** mengeksekusi satu instruksi dan masuk ke dalam fungsi yang dipanggil.

Contoh:

```text
main()

↓

checkPassword()

↓

strcmp()
```

Cocok digunakan ketika ingin mengetahui isi sebuah fungsi.

---

## 3. Step Over

**Step Over** juga mengeksekusi satu instruksi, tetapi tidak masuk ke dalam fungsi yang dipanggil.

Fungsi tersebut tetap dijalankan, namun debugger langsung melanjutkan ke instruksi berikutnya.

Digunakan ketika fungsi tersebut bukan fokus analisis.

---

## 4. Register

Saat program berjalan, debugger menampilkan isi register secara real-time.

Contoh:

```text
RAX = 00000001

RBX = 00000005

RCX = 00000008
```

Perubahan nilai register dapat menunjukkan bagaimana data diproses selama eksekusi. :contentReference[oaicite:3]{index=3}

---

## 5. Memory

Debugger juga memungkinkan kita melihat isi memori.

Melalui tampilan memori, kita dapat mengetahui:

- Input pengguna.
- Buffer.
- String.
- Data hasil dekripsi.
- Variabel program.

---

## 6. Call Stack

Call Stack menunjukkan urutan fungsi yang sedang dieksekusi.

Contoh:

```text
main()

↓

login()

↓

checkPassword()

↓

strcmp()
```

Call Stack membantu memahami bagaimana program berpindah dari satu fungsi ke fungsi lainnya.

---

# 🛠 Tools yang Umum Digunakan

Beberapa debugger yang sering digunakan dalam Dynamic Analysis:

- x64dbg
- WinDbg
- OllyDbg
- GDB (Linux)

---

# 🔍 Contoh Analisis

Misalkan program meminta password.

```text
Enter Password:
```

Langkah analisis:

1. Pasang breakpoint sebelum proses validasi.
2. Jalankan program.
3. Masukkan password sembarang.
4. Perhatikan perubahan register.
5. Amati isi memori.
6. Lihat hasil perbandingan pada instruksi `CMP`.

Dengan cara ini, kita dapat memahami bagaimana program melakukan proses autentikasi.

---

# ⚠️ Risiko Dynamic Analysis

Karena program benar-benar dijalankan, terdapat beberapa risiko.

Misalnya:

- Malware dapat menginfeksi sistem.
- Program dapat mengubah file.
- Program dapat mengakses jaringan.
- Program dapat memodifikasi registry.

Oleh karena itu, Dynamic Analysis sebaiknya dilakukan pada lingkungan yang terisolasi seperti **Virtual Machine** atau **Sandbox**. :contentReference[oaicite:4]{index=4}

---

# 🚫 Anti-Debugging

Beberapa program memiliki mekanisme **Anti-Debugging**.

Tujuannya adalah mendeteksi keberadaan debugger dan mengganggu proses analisis.

Contohnya:

- Menutup program secara otomatis.
- Mengubah alur eksekusi.
- Menampilkan hasil yang berbeda.
- Menyembunyikan perilaku sebenarnya.

Teknik ini sering ditemukan pada malware dan software yang memiliki sistem proteksi. :contentReference[oaicite:5]{index=5}

---

# 💡 Tips Melakukan Dynamic Analysis

- Lakukan Static Analysis terlebih dahulu.
- Gunakan Virtual Machine atau Sandbox.
- Pasang breakpoint pada fungsi penting.
- Amati perubahan register dan memori.
- Dokumentasikan setiap hasil pengamatan.
- Bandingkan hasil Dynamic Analysis dengan hipotesis dari Static Analysis.

---

# 📝 Kesimpulan

Dynamic Analysis memungkinkan seorang Reverse Engineer mengamati bagaimana sebuah program bekerja saat dijalankan. Dengan bantuan debugger, kita dapat melihat perubahan register, penggunaan memori, alur kontrol, dan interaksi program dengan sistem secara langsung.

Pendekatan ini sangat berguna untuk memvalidasi hasil Static Analysis, namun harus dilakukan secara hati-hati karena executable benar-benar dijalankan. Oleh sebab itu, penggunaan lingkungan yang aman seperti Virtual Machine merupakan praktik terbaik dalam melakukan Dynamic Analysis. :contentReference[oaicite:6]{index=6}

---

# 🚀 Selanjutnya

➡️ **02 - Studi Kasus Dynamic Analysis**

Pada materi berikutnya kita akan menerapkan Dynamic Analysis menggunakan debugger untuk mengamati perilaku sebuah executable secara langsung dan membandingkannya dengan hasil analisis statis.
