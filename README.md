# ⚡ Watt Monitor

Dashboard monitor pemakaian listrik rumah — single HTML file, no install needed.

## Fitur

### 📅 Bulanan (Monthly View)
- KPI cards: total kWh, estimasi tagihan, rata-rata harian, hari puncak
- Bar chart pemakaian harian dengan highlight hari >130% rata-rata
- Doughnut chart distribusi Pagi–Sore vs Malam
- Form input data harian (kWh pagi + malam per tanggal)

### 📊 Tahunan (Annual View)
- KPI: total kWh & tagihan YTD, bulan tertinggi & terendah
- Bar chart tren bulanan + line chart biaya per bulan
- Perbandingan Semester 1 vs Semester 2
- Tabel ringkasan semua bulan

### 🏠 Perangkat (Devices View)
- 8 perangkat terpantau: AC, Kulkas, TV, Mesin Cuci, Pompa Air, Lampu, Komputer, Lainnya
- Doughnut chart proporsi konsumsi
- Bar usage per perangkat + estimasi biaya bulanan

### ⚙️ Pengaturan Tarif
Preset tarif PLN 2025:

| Golongan | Daya | Tarif |
|----------|------|-------|
| R-450 | 450 VA | Rp 415/kWh |
| R-900 | 900 VA | Rp 1.352/kWh |
| R-1300 | 1300 VA | Rp 1.444,70/kWh |
| R-2200 | 2200 VA | Rp 1.444,70/kWh |
| R-3500 | 3500–5500 VA | Rp 1.699,53/kWh |
| R-6600 | 6600 VA ke atas | Rp 1.699,53/kWh |
| Custom | — | Input manual |

### 🖨️ Export PDF
Print semua view sekaligus dengan stylesheet light-mode khusus cetak.

## Tech Stack

- Vanilla HTML/CSS/JS — zero dependencies, zero build step
- [Chart.js 4.4.1](https://www.chartjs.org/) — semua chart
- Google Fonts: Space Mono + Syne

## Cara Pakai

```bash
# Buka langsung di browser
open index.html
```

Tidak perlu server, npm, atau build process. Cukup buka `index.html`.

## Input Data

1. Klik tab **Bulanan**
2. Scroll ke form **Tambah Data Pemakaian**
3. Pilih bulan & tanggal, isi kWh Pagi dan/atau kWh Malam
4. Klik **Simpan**

Data tersimpan di memori sesi (refresh = reset). Untuk data permanen, tambahkan ke array `monthlyData` dan `dailyData` di dalam `<script>`.
