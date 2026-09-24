# mpdw-prak

Repositori praktikum **Metode Peramalan Deret Waktu (MPDW) / Analisis Deret Waktu**, Semester 5.

Berisi kode `R Markdown`, data, dan output render tiap pertemuan, mencakup latihan kelas dan tugas individu/kelompok. Materi pertemuan terbaru diselaraskan dengan [repo sumber Praktikum STA1341](https://github.com/zeith001/Praktikum-STA1341).

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
    ├── Latihan/              # jika tersedia
    │   ├── *.Rmd              # sumber
    │   ├── *.html             # hasil knit
    │   └── data/              # dataset latihan
    └── Tugas/
        ├── *.Rmd              # sumber tugas
        ├── *.html             # hasil knit
        └── data/              # dataset tugas
```

**Aturan format** (dipakai untuk semua pertemuan berikutnya):

1. Satu folder per pertemuan: `Pertemuan <n>/`.
2. Materi dipisah ke `Latihan/` dan `Tugas/` jika keduanya tersedia.
3. Data disimpan di subfolder `data/` materi terkait bila memungkinkan.
4. Path di dalam `.Rmd` relatif; jangan gunakan path absolut atau `setwd()`.
5. Sertakan HTML hasil render untuk setiap `.Rmd` yang sudah dirender.
6. Pertahankan nama file dari sumber materi bila menggantinya akan memutus referensi internal.

---

## Daftar Pertemuan

| Pertemuan | Topik | Materi |
|---|---|---|
| 1 | Eksplorasi deret waktu dan pemulusan | [Latihan](Pertemuan%201/Latihan/Latihan1.Rmd) · [Tugas](Pertemuan%201/Tugas/Tugas-Pertemuan-1.Rmd) |
| 2 | Regresi dan autokorelasi | [Latihan](Pertemuan%202/Latihan/Pertemuan-2.Rmd) · [Tugas](Pertemuan%202/Tugas/Tugas-Pertemuan-2.Rmd) |
| 3 | Regresi dengan peubah lag | [Latihan](Pertemuan%203/Latihan/Pertemuan-3.Rmd) · [Tugas](Pertemuan%203/Tugas/Tugas-Pertemuan-3.Rmd) |
| 4 | Pembangkitan proses ARMA | [Materi](Pertemuan%204/Pembangkitan-ARMA.Rmd) |
| 5 | Stasioneritas, tren, differencing, dan transformasi Box–Cox | [Latihan](Pertemuan%205/Latihan/Pertemuan-5.Rmd) · [Tugas](Pertemuan%205/Tugas/Tugas-Pertemuan-5.Rmd) |
| 6 | Pemodelan ARIMA, pendugaan parameter, diagnostik model, dan peramalan | [Latihan](Pertemuan%206/Latihan/Pertemuan-6.Rmd) |

Setiap materi memiliki hasil HTML dengan nama yang sama dan ekstensi `.html` di folder yang sama.

### Pertemuan 1

- **Latihan**: `Data_1.csv` dan `Data_2.csv` (data kelas). Alur: impor data, eksplorasi, split 80:20 train-test, pemodelan SMA/DMA dan SES/DES, perbandingan akurasi (SSE, MSE, RMSE, MAPE), pemulusan data musiman.
- **Tugas**: **Daily Total Sunspot Number** dari [SILSO](https://www.sidc.be/SILSO/datafiles), World Data Center, Royal Observatory of Belgium. Kelompok mengambil 500 observasi harian terakhir, dibagi ke 5 anggota (100 observasi/orang). Bagian yang dikerjakan: **observasi ke-101-200**, periode **27 Juni 2025 - 4 Oktober 2025**.

### Pertemuan 5

- **Latihan** mengikuti materi sumber terbaru tentang stasioneritas dalam rataan dan ragam, simulasi tren, differencing, partisi data, dan transformasi Box–Cox.
- **Tugas** membangkitkan serta menganalisis proses MA(2), AR(2), dan ARMA(2,2).

### Pertemuan 6

- **Latihan** mencakup identifikasi, pendugaan parameter, diagnostik sisaan, overfitting, dan peramalan ARIMA pada data bangkitan dan kurs.

---

## Cara Menjalankan

1. Clone repositori, lalu buka `mpdw-prak.Rproj` di RStudio (working directory otomatis ke root).
2. Install package yang dibutuhkan:

```r
install.packages(c("forecast", "graphics", "TTR", "TSA", "aTSA", "rio", "ggplot2", "dplyr", "lmtest", "orcutt", "HoRM", "dLagM", "dynlm", "MLmetrics", "car", "tsibble", "tseries", "MASS"))
```

3. Buka `.Rmd` yang diinginkan, lalu **Knit**. Working directory chunk mengikuti lokasi file `.Rmd`, sehingga `data/...` langsung terbaca.

### Package yang Digunakan

| Package | Kegunaan |
|---|---|
| `forecast`, `TTR`, `TSA` | Peramalan, pemulusan, dan analisis deret waktu |
| `aTSA` | Analisis dan diagnostik deret waktu (Pertemuan 6) |
| `graphics`, `ggplot2` | Visualisasi |
| `rio` | Impor data lintas format |
| `dplyr`, `lmtest`, `orcutt`, `HoRM`, `dLagM`, `dynlm`, `MLmetrics`, `car` | Regresi, autokorelasi, dan ukuran akurasi (Pertemuan 2–3) |
| `tsibble`, `tseries`, `MASS` | Data deret waktu, uji stasioneritas, dan transformasi Box–Cox (Pertemuan 5–6) |

---

## Catatan

- File hasil kerja RStudio (`.Rproj.user/`, `.Rhistory`, `.RData`, `.Ruserdata`) di-ignore lewat `.gitignore`, jangan di-commit.
- Data mentah berukuran besar sebaiknya di-subset dulu sebelum masuk repo.
