# 🚀 Section 3 - Dynamic Analysis

> *"Observe the program in action to understand what static analysis alone cannot reveal."*

Selamat datang di **Section 3 - Dynamic Analysis**.

Pada section ini kita akan mempelajari bagaimana menganalisis sebuah executable **dengan menjalankannya** di lingkungan yang aman menggunakan debugger.

Berbeda dengan **Static Analysis**, Dynamic Analysis memungkinkan kita melihat bagaimana sebuah program berperilaku saat runtime, mulai dari perubahan register, penggunaan memori, alur eksekusi, hingga interaksi dengan sistem operasi.

Melalui materi pada section ini, Anda akan belajar bagaimana memvalidasi hipotesis yang telah dibuat pada tahap Static Analysis dengan mengamati perilaku program secara langsung.

---

# 🎯 Learning Objectives

Setelah menyelesaikan section ini, Anda diharapkan mampu:

- Memahami konsep Dynamic Analysis.
- Memahami workflow Dynamic Analysis.
- Menggunakan debugger untuk mengamati runtime program.
- Menggunakan Breakpoint, Step Into, dan Step Over.
- Mengamati perubahan register dan memori.
- Memvalidasi hasil Static Analysis menggunakan Dynamic Analysis.

---

# 📚 Learning Path

| No | Materi | Status |
|----|--------|:------:|
| 1 | Teknik Analisis Dinamis | ✅ |
| 2 | Studi Kasus Dynamic Analysis | ✅ |

---

# 📖 Materi

## 1️⃣ Teknik Analisis Dinamis

Mempelajari konsep dasar Dynamic Analysis, manfaatnya dalam Reverse Engineering, workflow debugging, serta berbagai komponen penting yang diamati ketika sebuah program dijalankan.

**Materi yang dipelajari:**

- Pengertian Dynamic Analysis
- Workflow Dynamic Analysis
- Breakpoint
- Step Into
- Step Over
- Register
- Memory
- Call Stack
- Risiko Dynamic Analysis
- Anti-Debugging

📄 **File:** `01-Teknik-Analisis-Dinamis.md`

---

## 2️⃣ Studi Kasus Dynamic Analysis

Menerapkan Dynamic Analysis menggunakan debugger untuk memahami bagaimana sebuah executable bekerja saat runtime dan membandingkannya dengan hasil Static Analysis.

**Materi yang dipelajari:**

- Overview Program
- Menentukan Breakpoint
- Menjalankan Program
- Analisis Register
- Analisis Memory
- Step Into vs Step Over
- Dokumentasi Hasil Analisis
- Validasi Hipotesis

📄 **File:** `02-Studi-Kasus-Dynamic-Analysis.md`

---

# 🗺️ Learning Flow

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
Step Through Program
      │
      ▼
Analisis Register
      │
      ▼
Analisis Memory
      │
      ▼
Analisis Call Stack
      │
      ▼
Verifikasi Hipotesis
```

---

# 💡 Key Takeaways

Sebelum melanjutkan ke section berikutnya, pastikan Anda telah memahami:

- Perbedaan Static Analysis dan Dynamic Analysis.
- Cara menggunakan Breakpoint secara efektif.
- Perbedaan Step Into dan Step Over.
- Cara mengamati perubahan Register dan Memory.
- Pentingnya menjalankan analisis di lingkungan yang aman (Virtual Machine atau Sandbox).
- Cara memvalidasi hipotesis menggunakan hasil runtime.

Dynamic Analysis memberikan sudut pandang yang tidak dapat diperoleh hanya dengan membaca executable. Dengan menggabungkan hasil Static Analysis dan Dynamic Analysis, seorang Reverse Engineer dapat memahami bagaimana sebuah program benar-benar bekerja.

---

# 🚀 Next Section

➡️ **Section 4 – Anti-Reverse Engineering**

Pada section berikutnya kita akan mempelajari berbagai teknik yang digunakan pengembang perangkat lunak maupun malware untuk menghambat proses Reverse Engineering, seperti **packing**, **obfuscation**, **anti-debugging**, dan teknik perlindungan lainnya.

---

<div align="center">

**Section 3 Complete ✅**

*"Don't just read the code—watch it come to life."*

</div>
