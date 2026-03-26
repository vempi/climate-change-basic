# 🌤️ Climate Downscaling — Yogyakarta

Statistical downscaling suhu harian menggunakan **Multiple Linear Regression (MLR)** dengan data ERA5, Observasi BMKG, dan GCM (CMIP6).

---

## 🚀 Jalankan Langsung di Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/USERNAME/REPO_NAME/blob/main/climate_downscaling_yogyakarta.ipynb)

> ⚠️ Ganti `USERNAME` dan `REPO_NAME` sesuai akun GitHub kamu.

---

## 📋 Deskripsi

Notebook ini mendemonstrasikan alur **point-based statistical downscaling** untuk proyeksi iklim lokal Kota Yogyakarta, meliputi:

- Generate demo data ERA5, Observasi BMKG, dan GCM future
- Eksplorasi data (EDA) — time series, scatter, heatmap korelasi
- Training model Multiple Linear Regression
- Validasi statistik (RMSE, MAE, R², Bias)
- Proyeksi suhu masa depan (2021–2060)
- Analisis anomali dan siklus musiman

---

## 🗂️ Struktur Repo

```
📦 climate-downscaling-yogyakarta
 ┣ 📓 climate_downscaling_yogyakarta.ipynb   ← Notebook utama
 ┣ 📄 requirements.txt                        ← Dependensi Python
 ┗ 📄 README.md                               ← Dokumentasi ini
```

---

## ⚙️ Instalasi Lokal

### 1. Clone repo
```bash
git clone https://github.com/USERNAME/REPO_NAME.git
cd REPO_NAME
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Jalankan Jupyter
```bash
jupyter notebook climate_downscaling_yogyakarta.ipynb
```

---

## 📦 Dependencies

| Library | Kegunaan |
|---|---|
| `numpy` | Komputasi numerik |
| `pandas` | Manipulasi data tabular |
| `matplotlib` + `seaborn` | Visualisasi |
| `scikit-learn` | Model MLR & evaluasi |
| `xarray` + `netCDF4` | Baca file ERA5/GCM (.nc) |
| `cdsapi` | Download ERA5 dari Copernicus CDS |

---

## 🔄 Alur Metodologi

```
ERA5 (nearest point)  ──┐
                        ├──→ Training MLR ──→ Validasi (RMSE, R²)
Obs BMKG (stasiun)    ──┘                          ↓
                                         Aplikasi ke GCM Future
                                                   ↓
                                     Proyeksi Suhu Yogyakarta 2021–2060
```

---

## 📊 Prediktor yang Digunakan

| Variabel | Nama | Satuan |
|---|---|---|
| `t2m` | Suhu udara 2m | °C |
| `d2m` | Dewpoint temperature 2m | °C |
| `sp` | Surface pressure | hPa |
| `ssrd` | Solar radiation downwards | W/m² |
| `ws10` | Wind speed 10m | m/s |

---

## 📍 Area Studi

| | Nilai |
|---|---|
| Lokasi | Kota Yogyakarta, DIY, Indonesia |
| Koordinat | 7.8°S, 110.37°E |
| Metode ekstraksi | Nearest point dari grid ERA5 |

---

## 📌 Catatan

> Notebook ini menggunakan **demo data sintetis** untuk keperluan pembelajaran.  
> Untuk penelitian nyata, ganti dengan:
> - **ERA5** → download via [Copernicus CDS](https://cds.climate.copernicus.eu) menggunakan `cdsapi`
> - **Obs BMKG** → minta langsung ke Stasiun BMKG Yogyakarta atau via [SIKU BMKG](https://siku.bmkg.go.id)
> - **GCM** → download dari [CMIP6 ESGF](https://esgf-node.llnl.gov/search/cmip6/) (misal `MPI-ESM1-2-LR`, skenario `ssp245`)

---

## 📚 Referensi

- Wilby, R.L. & Wigley, T.M.L. (1997). Downscaling general circulation model output: a review of methods and limitations. *Progress in Physical Geography*.
- Maraun, D. et al. (2010). Precipitation downscaling under climate change. *Reviews of Geophysics*.
- Hersbach, H. et al. (2020). The ERA5 global reanalysis. *Quarterly Journal of the Royal Meteorological Society*.

---

## 👤 Author

Dibuat untuk keperluan skripsi S1 — Climate Downscaling Yogyakarta  
