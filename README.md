# Template LaTeX FMIPA UNTAN

[![Download ZIP (Bahasa Indonesia)](https://img.shields.io/badge/Download-Versi%20Indonesia-blue?style=for-the-badge&logo=github)](https://github.com/nurimator/Template-Latex-FMIPA-UNTAN/releases/download/v1.1.0/LaTeX_FMIPA_UNTAN_ID.zip)
[![Download ZIP (English Version)](https://img.shields.io/badge/Download-English%20Version-green?style=for-the-badge&logo=github)](https://github.com/nurimator/Template-Latex-FMIPA-UNTAN/releases/download/v1.1.0/LaTeX_FMIPA_UNTAN_EN.zip)

Halo! Template LaTeX **unofficial** ini saya buat sekadar untuk membantu teman-teman mahasiswa FMIPA UNTAN dalam menyusun tugas akhir (Skripsi) menggunakan LaTeX. Perlu diketahui bahwa saya hanya mahasiswa biasa yang mencoba mengonversi format dari Template Microsoft Word ke LaTeX, dan saya **bukan** bagian dari tenaga pendidik atau staf resmi kampus. (Selengkapnya silakan baca bagian [Disclaimer](#disclaimer-penafian)).

Template ini tersedia dalam dua versi: Bahasa Indonesia (`ID`) dan Bahasa Inggris (`EN`). Semoga bermanfaat! 

## Persyaratan (Requirements)

Untuk menggunakan template ini, Anda harus menggunakan:
- **Compiler:** `XeLaTeX` (Wajib, karena menggunakan paket `fontspec` untuk font Times New Roman).
- **Bibliography Processor:** `Biber`.

## Struktur Proyek

```text
.
├── LaTeX_FMIPA_UNTAN_ID/         # Versi Bahasa Indonesia (Utama)
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
├── LaTeX_FMIPA_UNTAN_EN/         # Versi Bahasa Inggris
│   └── (Struktur folder sama dengan versi ID, hanya berbeda bahasa)
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
- **Menambahkan referensi:** Edit file `pustaka.bib` (ID) atau `references.bib` (EN). Anda bisa mengekspor referensi dari Mendeley atau Zotero dalam format BibTeX (.bib).
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
Jika Anda tidak ingin menginstal LaTeX secara lokal, Anda bisa menggunakan layanan Overleaf:
1. Lakukan registrasi di [Overleaf.com](https://www.overleaf.com/) kemudian login.
2. Download template versi `.zip` melalui tautan di bagian atas halaman ini, atau _clone_ project ini kemudian _compress_ folder yang ingin digunakan ke dalam bentuk `.zip`.
3. Buat project baru pada Overleaf dengan mengeklik tombol **"New Project"**, kemudian pilih **"Upload Project"**.
4. Upload file `.zip` tersebut pada halaman yang disediakan.

**Penting:** Setelah proyek terbuka, Anda harus mengubah engine compiler agar font *Times New Roman* dapat terbaca dengan benar:
1. Klik tombol **Menu** di pojok kiri atas Overleaf.
2. Pada bagian **Settings**, ubah **Compiler** menjadi `XeLaTeX`.
3. Klik **Recompile**.

*Catatan: Overleaf memiliki batasan waktu kompilasi (timeout), terutama untuk akun gratis. Jika proyek Anda sudah lumayan besar (banyak gambar atau bab), Overleaf mungkin akan menolak untuk melakukan kompilasi. Dalam kondisi ini, sangat disarankan untuk melakukan kompilasi secara lokal (VS Code/TeXstudio).*

### 2. Menggunakan VS Code (LaTeX Workshop)
Gunakan ekstensi **LaTeX Workshop**. Cara termudah adalah menggunakan **tectonic.exe**. Pastikan path executable tersebut sudah terdaftar dengan benar di `settings.json` VS Code Anda. Berikut adalah contoh konfigurasinya:

```json
{
    "latex-workshop.latex.autoBuild.run": "never",
    "latex-workshop.latex.tools": [
        {
            "name": "tectonic",
            "command": "C:/path/to/your/tectonic.exe",
            "args": [
                "--synctex",
                "%DOC%.tex"
            ],
            "env": {}
        }
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "tectonic",
            "tools": [
                "tectonic"
            ]
        }
    ]
}
```
*Catatan:*
- *Sesuaikan path `"command"` dengan lokasi instalasi Tectonic di komputer Anda.*
- *Pastikan `biber.exe` diletakkan di folder yang sama dengan `tectonic.exe` dan versinya harus kompatibel.*
- *Saat ini template berjalan stabil pada **Tectonic v0.16.9** dan **Biber v2.17**. Anda bebas memakai versi/engine lain, namun versi ini direkomendasikan apabila Anda mengalami masalah kompatibilitas.*

### 3. Menggunakan TeXstudio
Buka **Options** -> **Configure TeXstudio**:
- **Build**: Default Compiler ganti ke `XeLaTeX`.
- **Build**: Default Bibliography Tool ganti ke `Biber`.

---

## Disclaimer (Penafian)

- Template ini adalah **unofficial** (bukan rilisan resmi) dan hanya merupakan hasil konversi mandiri yang saya lakukan dari acuan template Microsoft Word.
- Sebagai sesama mahasiswa, saya berusaha semaksimal mungkin agar formatnya sesuai, namun template ini mungkin tidak selalu mutakhir karena aturan bisa berubah sewaktu-waktu.
- Pengguna bertanggung jawab penuh untuk memeriksa kembali kesesuaian hasil akhir dengan aturan terbaru yang berlaku di program studi masing-masing.
- Saya selaku yang melakukan konversi tidak bertanggung jawab atas kesalahan format atau kendala teknis (yang dapat menyebabkan kerugian waktu) yang muncul akibat penggunaan template ini.

**Kontribusi:** Jika Anda menemukan kesalahan, silakan buka **Issue**. Selain itu, jika Anda ingin memperbaiki sendiri atau memperbarui format sesuai aturan terbaru, silakan lakukan **pull request**. Bantuan Anda sangat berarti bagi teman-teman mahasiswa lainnya!
