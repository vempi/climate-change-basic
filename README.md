# Climate Change Basic

Materi praktikum analisis perubahan iklim menggunakan Python — untuk Mata Kuliah Perubahan Iklim dan Bencana Keairan.

Setiap modul berisi Jupyter Notebook dengan data sintetis siap pakai, dapat dijalankan langsung di Google Colab tanpa instalasi.

---

## Modul

| No | Topik | Notebook |
|----|-------|----------|
| 01 | [Data Proyeksi Iklim](01_Data-Proyeksi/) | Eksplorasi data historis & proyeksi GCM (CMIP6), skenario SSP2-4.5 & SSP5-8.5 |
| 02 | [Climate Extreme Indices](02_Climate-Extreme-Indices/) | Penghitungan indeks ETCCDI untuk suhu (TXx, TX90p, dll.) dan curah hujan (Rx1day, CDD, dll.) |
| 03 | [Analisis Tren](03_Trend-Analysis/) | Deteksi tren dengan uji Mann-Kendall dan estimasi Sen's Slope |
| 04 | [Bias Correction](04_Bias-correction/) | Koreksi bias data GCM terhadap observasi (downscaling statistik) |

---

## Cara Pakai

**Opsi 1 — Google Colab (direkomendasikan):**
Klik badge "Open in Colab" di README masing-masing modul.

**Opsi 2 — Lokal:**
```bash
pip install -r <nama-modul>/requirements.txt
jupyter notebook <nama-modul>/MAIN_*.ipynb
```

---

## Catatan

Semua notebook menggunakan **data sintetis** untuk keperluan pembelajaran.
Untuk penelitian nyata, gunakan data dari BMKG, ERA5 (Copernicus CDS), atau CHIRPS.
