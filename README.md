# mpdw-prak

Repositori praktikum **Metode Peramalan Deret Waktu (MPDW) / Analisis Deret Waktu**, Semester 5.

Berisi kode `R Markdown`, data, dan output render tiap pertemuan, mencakup latihan kelas dan tugas individu/kelompok.

- **Nama:** Nabeel Muhammad Diaz
- **RStudio Project:** `mpdw-prak.Rproj`

---

## Struktur Repositori

```
mpdw-prak/
├── mpdw-prak.Rproj          # RStudio project (buka lewat file ini)
├── README.md
├── .gitignore
└── Pertemuan <n>/
    ├── Latihan/
    │   ├── Latihan<n>.Rmd    # sumber
    │   ├── Latihan<n>.html   # hasil knit
    │   └── data/             # dataset latihan
    └── Tugas/
        ├── Tugas-Pertemuan-<n>.Rmd
        ├── Tugas-Pertemuan-<n>.html
        └── data/             # dataset tugas
```

**Aturan format** (dipakai untuk semua pertemuan berikutnya):

1. Satu folder per pertemuan: `Pertemuan <n>/`.
2. Di dalamnya selalu dipisah `Latihan/` dan `Tugas/`.
3. Data disimpan di subfolder `data/` masing-masing, **bukan** di root pertemuan.
4. Path di dalam `.Rmd` selalu **relatif**: `read.csv("data/namafile.csv")`. Jangan pakai path absolut atau `setwd()`.
5. Setiap `.Rmd` di-knit ke `.html` dan hasilnya ikut di-commit.
6. Gambar/plot hasil export disimpan sejajar dengan `.Rmd`-nya.

---

## Daftar Pertemuan

| Pertemuan | Topik | Latihan | Tugas |
|---|---|---|---|
| 1 | Eksplorasi deret waktu, pemulusan: SMA, DMA, SES, DES, pemulusan data musiman | [Latihan1.Rmd](Pertemuan%201/Latihan/Latihan1.Rmd) · [html](Pertemuan%201/Latihan/Latihan1.html) | [Tugas-Pertemuan-1.Rmd](Pertemuan%201/Tugas/Tugas-Pertemuan-1.Rmd) · [html](Pertemuan%201/Tugas/Tugas-Pertemuan-1.html) |

### Pertemuan 1

- **Latihan**: `Data_1.csv` dan `Data_2.csv` (data kelas). Alur: impor data, eksplorasi, split 80:20 train-test, pemodelan SMA/DMA dan SES/DES, perbandingan akurasi (SSE, MSE, RMSE, MAPE), pemulusan data musiman.
- **Tugas**: **Daily Total Sunspot Number** dari [SILSO](https://www.sidc.be/SILSO/datafiles), World Data Center, Royal Observatory of Belgium. Kelompok mengambil 500 observasi harian terakhir, dibagi ke 5 anggota (100 observasi/orang). Bagian yang dikerjakan: **observasi ke-101-200**, periode **27 Juni 2025 - 4 Oktober 2025**.

---

## Cara Menjalankan

1. Clone repositori, lalu buka `mpdw-prak.Rproj` di RStudio (working directory otomatis ke root).
2. Install package yang dibutuhkan:

```r
install.packages(c("forecast", "graphics", "TTR", "TSA", "rio", "ggplot2"))
```

3. Buka `.Rmd` yang diinginkan, lalu **Knit**. Working directory chunk mengikuti lokasi file `.Rmd`, sehingga `data/...` langsung terbaca.

### Package yang Digunakan

| Package | Kegunaan |
|---|---|
| `forecast` | Peramalan, `ses()`, `holt()`, `HoltWinters()`, ukuran akurasi |
| `TTR` | Moving average (`SMA`, `DMA`) |
| `TSA` | Fungsi pendukung analisis deret waktu |
| `graphics` | Plot dasar |
| `ggplot2` | Visualisasi |
| `rio` | Impor data lintas format (csv, xlsx, dll) |

---

## Catatan

- File hasil kerja RStudio (`.Rproj.user/`, `.Rhistory`, `.RData`, `.Ruserdata`) di-ignore lewat `.gitignore`, jangan di-commit.
- Data mentah berukuran besar sebaiknya di-subset dulu sebelum masuk repo.
