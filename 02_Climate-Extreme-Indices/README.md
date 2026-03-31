# Climate Extreme Indices — Yogyakarta

Penghitungan indeks iklim ekstrem (ETCCDI) untuk suhu dan curah hujan harian.

---

## 🚀 Jalankan Langsung di Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/USERNAME/REPO_NAME/blob/main/03_Climate-Extreme-Indices/MAIN_climate_extreme_indices.ipynb)

> ⚠️ Ganti `USERNAME` dan `REPO_NAME` sesuai akun GitHub kamu.

---

## 📋 Deskripsi

Notebook ini mendemonstrasikan penghitungan **Climate Extreme Indices** standar ETCCDI (*Expert Team on Climate Change Detection and Indices*), meliputi:

- Indeks ekstrem suhu: TXx, TNn, TX90p, TN10p
- Indeks ekstrem hujan: Rx1day, Rx5day, R95p, CDD, CWD
- Visualisasi tren tahunan tiap indeks
- Perbandingan nilai indeks antar dekade

---

## 🗂️ Struktur Folder

```
📦 03_Climate-Extreme-Indices
 ┣ 📓 MAIN_climate_extreme_indices.ipynb   ← Notebook utama
 ┣ 📄 requirements.txt                      ← Dependensi Python
 ┗ 📄 README.md                             ← Dokumentasi ini
```

---

## ⚙️ Instalasi Lokal

```bash
pip install -r requirements.txt
jupyter notebook MAIN_climate_extreme_indices.ipynb
```

---

## 📦 Dependencies

| Library | Kegunaan |
|---|---|
| `numpy` | Komputasi numerik |
| `pandas` | Manipulasi data tabular |
| `matplotlib` + `seaborn` | Visualisasi |

---

## 📊 Indeks yang Dihitung

### Indeks Suhu

| Indeks | Nama Lengkap | Definisi |
|---|---|---|
| TXx | Max Tmax | Nilai maksimum Tmax per tahun |
| TNn | Min Tmin | Nilai minimum Tmin per tahun |
| TX90p | Warm Days | % hari dengan Tmax > persentil 90 |
| TN10p | Cool Nights | % hari dengan Tmin < persentil 10 |

### Indeks Hujan

| Indeks | Nama Lengkap | Definisi |
|---|---|---|
| Rx1day | Max 1-day Precip | Curah hujan maksimum 1 hari per tahun |
| Rx5day | Max 5-day Precip | Curah hujan maksimum 5 hari berturutan per tahun |
| R95p | Very Wet Days | Total curah hujan pada hari > persentil 95 |
| CDD | Consecutive Dry Days | Hari kering berturutan terpanjang (hujan < 1 mm) |
| CWD | Consecutive Wet Days | Hari basah berturutan terpanjang (hujan ≥ 1 mm) |

---

## 📌 Catatan

> Notebook ini menggunakan **demo data sintetis** untuk keperluan pembelajaran.
> Untuk data nyata, gunakan data harian dari:
> - **BMKG** (Tmax, Tmin, RR harian stasiun)
> - **ERA5** reanalysis via Copernicus CDS
> - **CHIRPS** untuk curah hujan gridded

---

## 📚 Referensi

- Zhang, X. et al. (2011). Indices for monitoring changes in extremes based on daily temperature and precipitation data. *WIREs Climate Change*.
- Klein Tank, A.M.G. & Können, G.P. (2003). Trends in indices of daily temperature and precipitation extremes in Europe. *Journal of Climate*.

---

## 👤 Author

Dibuat untuk keperluan Mata Kuliah Perubahan Iklim dan Bencana Keairan
