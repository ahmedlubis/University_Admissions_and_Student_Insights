# 🎓 Dataset Sistem Informasi Akademik

## 📖 Ringkasan Dataset

Dataset ini merepresentasikan beberapa proses bisnis utama dalam sistem informasi akademik perguruan tinggi, mencakup seluruh siklus hidup mahasiswa—mulai dari penerimaan mahasiswa baru (admisi), aktivitas akademik, kelulusan, hingga data master program studi.

Database ini terdiri dari empat dataset yang saling terhubung dan dapat dihubungkan menggunakan identifikasi mahasiswa seperti **Nomor Induk Mahasiswa (NIM)** serta informasi program studi.

---

## 🗂️ Deskripsi Dataset

### 1. Data Admisi (`admisi.csv`)

Tabel ini mencatat proses penerimaan mahasiswa baru di universitas. Tabel memuat informasi pendaftaran calon mahasiswa beserta atribut yang menunjukkan status akhir penerimaan dari setiap pendaftar. Pendaftar yang berhasil lolos seleksi dan resmi mendaftar ulang sebagai mahasiswa akan mendapatkan Nomor Induk Mahasiswa (NIM).

**Karakteristik Utama:**
* Mencatat data pendaftaran pendaftar
* Menunjukkan status penerimaan (lolos/tidak)
* Menghasilkan NIM untuk pendaftar yang diterima
* NIM dirancang sebagai **Smart Key**, yang secara unik mengidentifikasi setiap mahasiswa sepanjang siklus akademik mereka

---

### 2. Data Aktivitas Perkulihan (`aktivitas-perkuliahan.csv`)

Tabel ini mencatat aktivitas akademik mahasiswa selama masa studi. Tabel mencakup pengambilan mata kuliah, catatan semester, program remedial, beban sks, dan nilai huruf yang diperoleh pada setiap mata kuliah. Nilai yang tercatat kemudian dikonversi menjadi bobot nilai numerik untuk menghitung Indeks Prestasi Kumulatif (IPK) mahasiswa.

#### Perhitungan IPK

IPK kumulatif dihitung menggunakan rumus rata-rata tertimbang standar:

$$\text{IPK} = \frac{\sum (\text{Bobot Nilai} \times \text{SKS})}{\sum \text{SKS}}$$

*Keterangan:*
* **Bobot Nilai** = Nilai numerik yang disesuaikan dengan nilai huruf
* **SKS** = Bobot kredit dari setiap mata kuliah

#### Format Kode Semester

Kode semester mengikuti format: `[Tahun Akademik (4 digit)][Kode Semester (1 digit)]`

* **Contoh:** `20251`
  * **Tahun Akademik:** 2025/2026
  * **Semester:** Ganjil

#### Klasifikasi Kode Semester

| Kode | Jenis Semester |
| :---: | :--- |
| **1** | Semester Ganjil |
| **2** | Semester Genap |
| **3** | Remedial Ganjil |
| **4** | Remedial Genap |

#### Konversi Nilai Huruf

| Nilai Huruf | Bobot Nilai |
| :---: | :---: |
| **A** | 4.00 |
| **A-** | 3.70 |
| **B+** | 3.30 |
| **B** | 3.00 |
| **B-** | 2.70 |
| **C+** | 2.30 |
| **C** | 2.00 |
| **D** | 1.00 |
| **E** | 0.00 |

---

### 3. Data Kelulusan (`peserta-wisuda-tervalidasi.csv`)

Tabel ini mencatat mahasiswa yang telah berhasil menyelesaikan seluruh persyaratan akademik dan telah divalidasi secara resmi sebagai peserta upacara wisuda.

**Karakteristik Utama:**
* Mencatat kelayakan kelulusan
* Menunjukkan mahasiswa yang telah memenuhi seluruh persyaratan akademik
* Berisi informasi peserta wisuda yang tervalidasi
* Merepresentasikan tahap akhir dari siklus hidup akademik mahasiswa

---

### 4. Data Master Program Studi (`homebase.csv`)

Tabel ini berfungsi sebagai dataset referensi utama untuk klasifikasi akademik institusi. Tabel ini menyediakan informasi terstandarisasi mengenai fakultas, jenjang pendidikan, dan program studi.

Dataset ini utamanya digunakan sebagai tabel acuan (reference) untuk mengintegrasikan dan mengkategorikan catatan akademik di seluruh dataset lainnya.

**Karakteristik Utama:**
* Informasi fakultas
* Klasifikasi jenjang pendidikan
* Informasi program studi
* Data acuan (master) untuk pelaporan akademik

---

## 📌 Relasi Dataset

Keempat dataset ini secara kolektif menggambarkan perjalanan akademik lengkap seorang mahasiswa:

```text
Admisi
  │
  ▼
Mahasiswa (NIM)
  │
  ▼
Aktivitas Perkuliahan
  │
  ▼
Wisuda / Kelulusan
