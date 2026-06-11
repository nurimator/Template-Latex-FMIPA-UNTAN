# Template LaTeX FMIPA UNTAN

Template LaTeX **unofficial** ini dirancang sebagai alternatif penulisan tugas akhir (Skripsi) di Fakultas Matematika dan Ilmu Pengetahuan Alam (FMIPA) Universitas Tanjungpura, yang merupakan hasil konversi dari acuan format Template Microsoft Word. Tersedia dalam dua versi: Bahasa Indonesia (`[ID]`) dan Bahasa Inggris (`[EN]`).

## Persyaratan (Requirements)

Untuk menggunakan template ini, Anda harus menggunakan:
- **Compiler:** `XeLaTeX` (Wajib, karena menggunakan paket `fontspec` untuk font Times New Roman).
- **Bibliography Processor:** `Biber` (Bukan BibTeX).

## Struktur Proyek

```text
.
├── LaTeX_FMIPA_UNTAN_[ID]/       # Versi Bahasa Indonesia (Utama)
│   ├── main.tex                  # File utama (ID)
│   ├── skripsi_style.sty         # Style & Packages (ID)
│   ├── pustaka.bib               # Database bibliografi (ID)
│   ├── 0-bagian-awal/            # Bagian Awal
│   │   ├── cover.tex             # Sampul Luar
│   │   ├── judul.tex             # Halaman Judul
│   │   ├── pengesahan.tex        # Lembar Pengesahan
│   │   ├── integritas.tex        # Pernyataan Integritas
│   │   ├── abstrak.tex           # Abstrak (Indo)
│   │   ├── abstract.tex          # Abstract (English)
│   │   ├── prakata.tex           # Kata Pengantar
│   │   └── persembahan.tex       # Halaman Persembahan
│   ├── 1-bagian-isi/             # Bagian Isi
│   │   ├── bab1.tex              # Bab I Pendahuluan
│   │   ├── bab2.tex              # Bab II Tinjauan Pustaka
│   │   ├── bab3.tex              # Bab III Metode Penelitian
│   │   ├── bab4.tex              # Bab IV Hasil dan Pembahasan
│   │   └── bab5.tex              # Bab V Penutup
│   ├── 2-bagian-akhir/           # Bagian Akhir
│   │   ├── pustaka.tex           # Daftar Pustaka
│   │   └── lampiran.tex          # Lampiran
│   └── assets/                   # Folder Aset
│       ├── images/               # Gambar (JPG, PNG)
│       └── pdfs/                 # Logo & Dokumen PDF
├── LaTeX_FMIPA_UNTAN_[EN]/       # Versi Bahasa Inggris
│   └── (Struktur folder sama dengan versi [ID], hanya berbeda bahasa)
└── README.md
```


## Cara Penggunaan Dasar

### 1. Membuat Section dan Subsection
Gunakan perintah standar LaTeX untuk membagi naskah:
```latex
\section{Metode Karakterisasi Material}
\subsection{X-Ray Diffraction (XRD)}
```
*Catatan: Level subsection diatur agar memiliki garis bawah (underline) sesuai standar template ini.*

### 2. Menulis Persamaan Matematika (Equation)
Gunakan environment `equation` untuk persamaan yang diberi nomor:
```latex
\begin{equation}
    E = mc^2
    \label{eq:einstein}
\end{equation}
```
Untuk merujuk ke persamaan tersebut di dalam teks, gunakan `\eqref{eq:einstein}`.

### 3. Menambahkan Gambar
Letakkan file gambar di folder `assets/images/`.
```latex
\begin{figure}[htbp]
    \centering
    \includegraphics[width=0.5\textwidth]{assets/images/gambar_1.jpg}
    \caption{Judul Gambar}
    \label{fig:gambar1}
\end{figure}
```
Rujuk dengan: `Gambar \ref{fig:gambar1}`.

### 4. Membuat Tabel
Gunakan format `booktabs` untuk tampilan profesional (tanpa garis vertikal):
```latex
\begin{table}[htbp]
    \centering
    \caption{Contoh Tabel}
    \begin{tabular}{ccc}
        \toprule
        Kolom 1 & Kolom 2 & Kolom 3 \\
        \midrule
        Data A & 10 & 20 \\
        Data B & 30 & 40 \\
        \bottomrule
    \end{tabular}
    \label{tab:tabel1}
\end{table}
```

**Tips Tabel Lebar:**
Jika tabel memiliki banyak kolom hingga melewati batas margin, Anda bisa membungkus `tabular` dengan `\resizebox`:
```latex
\begin{table}[htbp]
    \centering
    \caption{Tabel yang Sangat Lebar}
    \resizebox{\textwidth}{!}{%
        \begin{tabular}{llllllll}
            \toprule
            ... banyak kolom ... \\
            \bottomrule
        \end{tabular}%
    }
\end{table}
```
Rujuk dengan: `Tabel \ref{tab:tabel1}`.

### 5. Sitasi dan Daftar Pustaka
Template ini menggunakan `biblatex` dengan gaya `authoryear`.
- **Menambahkan referensi:** Edit file `pustaka.bib` (ID) atau `references.bib` (EN).
- **Cara Sitasi:**
    - `\textcite{key}` -> Penulis (Tahun)
    - `\parentcite{key}` -> (Penulis, Tahun)
- **Daftar Pustaka:** Akan otomatis terbuat di bagian akhir melalui file `2-bagian-akhir/pustaka.tex`.

### 6. Referensi Silang (Cross-referencing)
Selalu gunakan `\label{tag}` setelah caption atau di dalam persamaan, lalu gunakan `\ref{tag}` atau `\eqref{tag}` untuk memanggilnya. Pastikan tag unik (misal: `fig:`, `tab:`, `eq:`, `chap:`).

### 7. Lampiran (Appendix)
Untuk menambahkan item di Daftar Lampiran, gunakan perintah khusus:
```latex
\appendixitem{Judul Lampiran Anda}
```

### 8. Personalisasi Identitas
Data seperti Judul, Nama, dan NIM dapat diubah langsung pada file di folder `0-bagian-awal/` (ID) atau `0-front-matter/` (EN), khususnya pada file:
- `cover.tex`
- `judul.tex` (atau `title.tex`)
- `pengesahan.tex` (atau `approval.tex`)

## Cara Kompilasi

### 1. Menggunakan Overleaf (Paling Mudah)
Jika Anda tidak ingin menginstal LaTeX secara lokal, Anda bisa mengunggah folder template ini ke Overleaf. **Penting:** Anda harus mengubah engine compiler agar font *Times New Roman* dapat terbaca:
1. Buka Proyek di Overleaf.
2. Klik tombol **Menu** di pojok kiri atas.
3. Pada bagian **Settings**, ubah **Compiler** menjadi `XeLaTeX`.
4. Klik **Recompile**.

### 2. Menggunakan Editor Lokal (VS Code / TeXstudio)

#### VS Code (LaTeX Workshop)
Gunakan ekstensi **LaTeX Workshop**. Cara termudah adalah menggunakan **tectonic.exe** dan **biber.exe**. Pastikan:
- Versi Tectonic dan Biber kompatibel satu sama lain.
- Path kedua executable tersebut sudah terdaftar dengan benar di `settings.json` VS Code Anda.
- Gunakan resep (recipe) yang menjalankan Tectonic -> Biber -> Tectonic.

### TeXstudio
Buka **Options** -> **Configure TeXstudio**:
- **Build**: Default Compiler ganti ke `XeLaTeX`.
- **Build**: Default Bibliography Tool ganti ke `Biber`.

---

## Disclaimer (Penyangkalan)

- Template ini adalah **unofficial** (bukan merupakan rilisan resmi) dan merupakan hasil konversi mandiri dari acuan template Microsoft Word.
- Template ini mungkin tidak mutakhir; aturan penulisan dan format template dapat berubah sewaktu-waktu sesuai kebijakan fakultas.
- Pengguna bertanggung jawab penuh untuk memeriksa kembali kesesuaian hasil akhir dengan aturan template terbaru yang berlaku.
- Pihak yang melakukan konversi template ini tidak bertanggung jawab (*not liable*) atas kesalahan format diakibatkan oleh penggunaan template ini, maupun yang diakibatkan oleh kelalaian atau ketidaktahuan dalam cara penggunaan template ini.

**Kontribusi:** Silakan lakukan pull request jika ingin memperbaiki format sesuai perkembangan aturan terbaru.
