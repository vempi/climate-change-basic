## 🗂️ Struktur Repo

```
📦 Data demo
 ┣ 📊 obs_bmkg.csv                            ← Contoh format obs BMKG
 ┣ 📊 era5_yogyakarta.csv                     ← Contoh format ERA5 (nearest point)
 ┣ 📊 gcm_future.csv                          ← Contoh format GCM future
```

---

## 📊 Format Data CSV

Tiga file CSV dibutuhkan dengan format berikut. Pastikan **kolom dan satuan sudah sesuai** sebelum dimasukkan ke notebook.

---

### 1. `obs_bmkg.csv` — Observasi BMKG Yogyakarta

Data suhu harian dari stasiun BMKG sebagai **target (Y)** model.

```
date,suhu_obs
2000-01-01,27.4
2000-01-02,27.1
...
```

| Kolom | Tipe | Satuan | Keterangan |
|---|---|---|---|
| `date` | string | `YYYY-MM-DD` | Tanggal pengamatan |
| `suhu_obs` | float | °C | Suhu rata-rata harian |

> 📌 Sumber: Stasiun BMKG Yogyakarta. Ajukan permohonan data resmi ke BMKG atau akses via [SIKU BMKG](https://siku.bmkg.go.id).

---

### 2. `era5_yogyakarta.csv` — ERA5 Historical (nearest point)

Data ERA5 yang sudah diekstrak pada titik terdekat stasiun BMKG sebagai **prediktor (X)** saat training.

```
date,t2m,d2m,sp,ssrd,ws10
2000-01-01,26.1,22.4,918.3,185.2,1.8
2000-01-02,25.8,21.9,917.8,190.5,2.1
...
```

| Kolom | Tipe | Satuan | Keterangan | Konversi dari ERA5 raw |
|---|---|---|---|---|
| `date` | string | `YYYY-MM-DD` | Tanggal | — |
| `t2m` | float | °C | Suhu udara 2m | Kelvin − 273.15 |
| `d2m` | float | °C | Dewpoint temperature 2m | Kelvin − 273.15 |
| `sp` | float | hPa | Surface pressure | Pa ÷ 100 |
| `ssrd` | float | W/m² | Solar radiation downwards | J/m² ÷ 3600 |
| `ws10` | float | m/s | Wind speed 10m | √(u10² + v10²) |

> 📌 Sumber: [Copernicus Climate Data Store](https://cds.climate.copernicus.eu). Download via `cdsapi`, ekstrak nearest point dengan `xarray.sel(method='nearest')`.

---

### 3. `gcm_future.csv` — GCM Future (nearest point)

Data GCM proyeksi masa depan. **Nama kolom harus identik dengan `era5_yogyakarta.csv`** agar bisa langsung masuk ke model MLR.

```
date,t2m,d2m,sp,ssrd,ws10
2021-01-01,27.8,23.5,920.1,192.4,2.0
2021-01-02,27.5,23.1,919.6,197.8,2.3
...
```

| Kolom | Tipe | Satuan | Keterangan |
|---|---|---|---|
| `date` | string | `YYYY-MM-DD` | Tanggal proyeksi |
| `t2m` | float | °C | Sama seperti ERA5 — sudah dikonversi |
| `d2m` | float | °C | Sama seperti ERA5 |
| `sp` | float | hPa | Sama seperti ERA5 |
| `ssrd` | float | W/m² | Sama seperti ERA5 |
| `ws10` | float | m/s | Sama seperti ERA5 |

> 📌 Sumber: [CMIP6 ESGF Node](https://esgf-node.llnl.gov/search/cmip6/). Gunakan model `MPI-ESM1-2-LR`, eksperimen `historical` + `ssp245`, frekuensi `day`.

---

## ⚠️ Aturan Penting Format Data

```
✅ Format tanggal   : YYYY-MM-DD  (contoh: 2000-01-01)
✅ Satuan t2m, d2m  : °C          (BUKAN Kelvin)
✅ Satuan sp         : hPa         (BUKAN Pa)
✅ Satuan ssrd       : W/m²        (BUKAN J/m²)
✅ Tidak ada baris kosong di tengah file
✅ Kolom GCM future  IDENTIK dengan ERA5
✅ Periode obs_bmkg dan era5 HARUS overlap (untuk training)
```

---

## 🔄 Alur Metodologi (6 Step)

```
┌──────────────────────────────────────────────────────────────┐
│  STEP 1: Download data ERA5, Obs BMKG, GCM CMIP6             │
└───────────────────────────┬──────────────────────────────────┘
                            ↓
┌──────────────────────────────────────────────────────────────┐
│  STEP 2: Ekstrak nearest point ke koordinat stasiun BMKG     │
│          (-7.8°S, 110.37°E)                                  │
└───────────────────────────┬──────────────────────────────────┘
                            ↓
┌──────────────────────────────────────────────────────────────┐
│  STEP 3: Preprocessing                                       │
│          - Konversi satuan (K→°C, Pa→hPa, J/m²→W/m²)        │
│          - Agregasi harian (.resample('1D').mean())          │
│          - Merge ERA5 + Obs BMKG berdasarkan tanggal         │
└───────────────────────────┬──────────────────────────────────┘
                            ↓
┌──────────────────────────────────────────────────────────────┐
│  STEP 4: Training MLR                                        │
│          - Split 70/30 (shuffle=False untuk time series!)    │
│          - Standardisasi: StandardScaler (fit di train saja) │
│          - Fit: LinearRegression()                           │
└───────────────────────────┬──────────────────────────────────┘
                            ↓
┌──────────────────────────────────────────────────────────────┐
│  STEP 5: Validasi pada test period                           │
│          - RMSE, MAE, R², Bias                               │
│          - Scatter plot (obs vs pred)                        │
│          - Distribusi residual                               │
└───────────────────────────┬──────────────────────────────────┘
                            ↓
┌──────────────────────────────────────────────────────────────┐
│  STEP 6: Proyeksi GCM Future (2021–2060)                     │
│          - Prediktor dari GCM → scaler.transform()           │
│          - model.predict() → suhu proyeksi lokal             │
│          - Analisis anomali, tren, siklus musiman            │
└──────────────────────────────────────────────────────────────┘
```

---

## 📦 Dependencies

| Library | Versi | Kegunaan |
|---|---|---|
| `numpy` | ≥ 1.24 | Komputasi numerik |
| `pandas` | ≥ 2.0 | Manipulasi data tabular |
| `matplotlib` | ≥ 3.7 | Visualisasi dasar |
| `seaborn` | ≥ 0.12 | Visualisasi statistik |
| `scikit-learn` | ≥ 1.3 | Model MLR, scaler, metrik evaluasi |
| `xarray` | ≥ 2023.1 | Baca file ERA5/GCM format `.nc` |
| `netCDF4` | ≥ 1.6 | Backend netCDF untuk xarray |
| `cdsapi` | ≥ 0.6 | Download ERA5 dari Copernicus CDS |

Install semua sekaligus:
```bash
pip install -r requirements.txt
```

---

## 📍 Area Studi

| Parameter | Nilai |
|---|---|
| Lokasi | Kota Yogyakarta, DIY, Indonesia |
| Koordinat stasiun | 7.8°S, 110.37°E |
| Metode ekstraksi | `xarray.sel(method='nearest')` |
| Resolusi ERA5 | ~25 km (~0.25°) |
| Resolusi GCM | ~100–200 km (~1–2°) |
| Periode historis | 2000–2020 |
| Periode proyeksi | 2021–2060 (SSP2-4.5) |

---

## 📚 Referensi

- Wilby, R.L. & Wigley, T.M.L. (1997). Downscaling general circulation model output: a review of methods and limitations. *Progress in Physical Geography*.
- Maraun, D. et al. (2010). Precipitation downscaling under climate change. *Reviews of Geophysics*.
- Hersbach, H. et al. (2020). The ERA5 global reanalysis. *Quarterly Journal of the Royal Meteorological Society*.
- Eyring, V. et al. (2016). Overview of CMIP6. *Geoscientific Model Development*.

--
