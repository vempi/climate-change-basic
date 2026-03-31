# Data Proyeksi Iklim — Yogyakarta

Eksplorasi data iklim historis dan proyeksi GCM (CMIP6) untuk suhu dan curah hujan harian.

---

## 🚀 Jalankan Langsung di Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/USERNAME/REPO_NAME/blob/main/02_Data-Proyeksi/MAIN_data_proyeksi.ipynb)

> ⚠️ Ganti `USERNAME` dan `REPO_NAME` sesuai akun GitHub kamu.

---

## 📋 Deskripsi

Notebook ini mendemonstrasikan cara membaca, mengeksplorasi, dan memvisualisasikan data proyeksi iklim, meliputi:

- Generate demo data observasi historis (suhu & curah hujan) dan GCM masa depan
- Statistik deskriptif dan perbandingan antar skenario
- Visualisasi time series, siklus musiman, dan distribusi data
- Perbandingan periode: historis vs near future vs far future

---

## 🗂️ Struktur Folder

```
📦 02_Data-Proyeksi
 ┣ 📓 MAIN_data_proyeksi.ipynb   ← Notebook utama
 ┣ 📄 requirements.txt            ← Dependensi Python
 ┗ 📄 README.md                   ← Dokumentasi ini
```

---

## ⚙️ Instalasi Lokal

```bash
pip install -r requirements.txt
jupyter notebook MAIN_data_proyeksi.ipynb
```

---

## 📦 Dependencies

| Library | Kegunaan |
|---|---|
| `numpy` | Komputasi numerik |
| `pandas` | Manipulasi data tabular |
| `matplotlib` + `seaborn` | Visualisasi |

---

## 🔄 Alur Notebook

```
Data Observasi (1990–2020)  ──┐
                               ├──→ Statistik Deskriptif
GCM SSP2-4.5 (2021–2060)   ──┤         ↓
                               ├──→ Visualisasi Time Series & Siklus Musiman
GCM SSP5-8.5 (2021–2060)   ──┘         ↓
                                  Perbandingan Periode & Skenario
```

---

## 📊 Skenario yang Digunakan

| Skenario | Deskripsi |
|---|---|
| Historis | Observasi / reanalysis 1990–2020 |
| SSP2-4.5 | Skenario emisi menengah (~+2°C pada 2100) |
| SSP5-8.5 | Skenario emisi tinggi (~+4°C pada 2100) |

---

## 📌 Catatan

> Notebook ini menggunakan **demo data sintetis** untuk keperluan pembelajaran.
> Untuk data nyata, gunakan:
> - **ERA5** → [Copernicus CDS](https://cds.climate.copernicus.eu)
> - **GCM CMIP6** → [ESGF Portal](https://esgf-node.llnl.gov/search/cmip6/)
> - **CHIRPS** (curah hujan) → [CHIRPS](https://www.chc.ucsb.edu/data/chirps)

---

## 📚 Referensi

- O'Neill, B.C. et al. (2016). The Scenario Model Intercomparison Project. *Geoscientific Model Development*.
- Eyring, V. et al. (2016). Overview of CMIP6. *Geoscientific Model Development*.

---

## 👤 Author

Dibuat untuk keperluan Mata Kuliah Perubahan Iklim dan Bencana Keairan
