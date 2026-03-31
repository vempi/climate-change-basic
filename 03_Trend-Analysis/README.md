# Analisis Tren Iklim — Yogyakarta

Deteksi tren iklim jangka panjang menggunakan **uji Mann-Kendall** dan estimasi besar tren dengan **Sen's Slope**.

---

## 🚀 Jalankan Langsung di Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/USERNAME/REPO_NAME/blob/main/04_Trend-Analysis/MAIN_trend_analysis.ipynb)

> ⚠️ Ganti `USERNAME` dan `REPO_NAME` sesuai akun GitHub kamu.

---

## 📋 Deskripsi

Notebook ini mendemonstrasikan analisis tren iklim jangka panjang, meliputi:

- Implementasi **uji Mann-Kendall** (non-parametrik) untuk deteksi tren
- Estimasi besar tren dengan **Sen's Slope**
- Aplikasi pada suhu, curah hujan, dan indeks ekstrem
- Visualisasi tren dengan confidence interval
- Tabel ringkasan hasil analisis

---

## 🗂️ Struktur Folder

```
📦 04_Trend-Analysis
 ┣ 📓 MAIN_trend_analysis.ipynb   ← Notebook utama
 ┣ 📄 requirements.txt             ← Dependensi Python
 ┗ 📄 README.md                    ← Dokumentasi ini
```

---

## ⚙️ Instalasi Lokal

```bash
pip install -r requirements.txt
jupyter notebook MAIN_trend_analysis.ipynb
```

---

## 📦 Dependencies

| Library | Kegunaan |
|---|---|
| `numpy` | Komputasi numerik |
| `pandas` | Manipulasi data tabular |
| `matplotlib` + `seaborn` | Visualisasi |
| `scipy` | Distribusi statistik (p-value) |

---

## 🔬 Metode

### Mann-Kendall Test
- Uji non-parametrik untuk deteksi tren monoton
- Tidak memerlukan asumsi distribusi normal
- Output: statistik S, Z, dan p-value
- H₀: tidak ada tren | H₁: ada tren (α = 0.05)

### Sen's Slope
- Estimasi besarnya tren (unit per tahun)
- Lebih robust terhadap outlier dibanding regresi linear
- Dihitung sebagai median dari semua pasangan kemiringan

---

## 📌 Catatan

> Notebook ini menggunakan **demo data sintetis** untuk keperluan pembelajaran.
> Untuk penelitian nyata, gunakan data observasi jangka panjang dari BMKG (≥ 30 tahun).

---

## 📚 Referensi

- Mann, H.B. (1945). Nonparametric tests against trend. *Econometrica*.
- Kendall, M.G. (1975). *Rank Correlation Methods*. Griffin, London.
- Sen, P.K. (1968). Estimates of the regression coefficient based on Kendall's tau. *Journal of the American Statistical Association*.

---

## 👤 Author

Dibuat untuk keperluan Mata Kuliah Perubahan Iklim dan Bencana Keairan
