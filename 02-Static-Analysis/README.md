# 🔍 Section 2 - Static Analysis

> *"Understand the program before you execute it."*

Selamat datang di **Section 2 - Static Analysis**.

Pada section ini kita akan mempelajari bagaimana menganalisis sebuah executable **tanpa menjalankannya**. Static Analysis merupakan salah satu tahapan paling penting dalam Reverse Engineering karena membantu memahami struktur, logika, dan perilaku suatu program secara aman sebelum dilakukan analisis lebih lanjut.

Melalui materi pada section ini, Anda akan belajar mengumpulkan informasi dari executable menggunakan berbagai teknik seperti analisis header, section, strings, imports, functions, dan cross references.

---

# 🎯 Learning Objectives

Setelah menyelesaikan section ini, Anda diharapkan mampu:

- Memahami konsep Static Analysis.
- Mengetahui workflow Static Analysis.
- Mengidentifikasi komponen penting dalam executable.
- Membaca struktur program menggunakan hasil disassembly.
- Membangun hipotesis berdasarkan hasil analisis.
- Melakukan analisis awal terhadap sebuah binary executable.

---

# 📚 Learning Path

| No | Materi | Status |
|----|--------|:------:|
| 1 | Teknik Analisis Statis | ✅ |
| 2 | Studi Kasus Static Analysis | ✅ |

---

# 📖 Materi

## 1️⃣ Teknik Analisis Statis

Mempelajari konsep dasar Static Analysis, manfaatnya dalam Reverse Engineering, workflow analisis, serta berbagai komponen penting yang perlu diperhatikan ketika menganalisis executable.

**Materi yang dipelajari:**

- Pengertian Static Analysis
- Workflow Static Analysis
- File Header
- Sections
- Strings
- Imports
- Functions
- Cross References (Xrefs)
- Membangun Hipotesis

📄 **File:** `01-Teknik-Analisis-Statis.md`

---

## 2️⃣ Studi Kasus Static Analysis

Menerapkan konsep Static Analysis pada sebuah executable nyata untuk memahami bagaimana seorang Reverse Engineer menghubungkan berbagai petunjuk menjadi sebuah pemahaman mengenai logika program.

**Materi yang dipelajari:**

- Overview Program
- Analisis Strings
- Cross References (Xrefs)
- Membaca Assembly
- Analisis Loop
- Dokumentasi Hasil Analisis
- Keterbatasan Static Analysis

📄 **File:** `02-Studi-Kasus-Static-Analysis.md`

---

# 🗺️ Learning Flow

```text
Executable
      │
      ▼
Identifikasi File
      │
      ▼
Header Analysis
      │
      ▼
Section Analysis
      │
      ▼
Strings Analysis
      │
      ▼
Imports Analysis
      │
      ▼
Function Analysis
      │
      ▼
Cross References
      │
      ▼
Assembly Analysis
      │
      ▼
Build Hypothesis
```

---

# 💡 Key Takeaways

Sebelum melanjutkan ke Dynamic Analysis, pastikan Anda sudah memahami:

- Perbedaan Static Analysis dan Dynamic Analysis.
- Cara mengidentifikasi informasi penting dari executable.
- Fungsi Header, Sections, dan Imports.
- Cara menggunakan Strings dan Cross References.
- Dasar membaca Assembly sederhana.
- Cara menyusun hipotesis berdasarkan hasil analisis.

Kemampuan ini akan menjadi fondasi ketika mulai mengamati perilaku program secara langsung pada tahap berikutnya.

---

# 🚀 Next Section

➡️ **Section 3 – Dynamic Analysis**

Pada section berikutnya kita akan menjalankan executable di lingkungan yang aman untuk mengamati perilaku program secara langsung, melakukan debugging, serta memvalidasi hipotesis yang telah dibuat selama proses Static Analysis.

---

<div align="center">

**Section 2 Complete ✅**

*"Analyze first. Execute later."*

</div>
