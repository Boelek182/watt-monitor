# ⚡ Watt Monitor

Dashboard monitor pemakaian listrik rumah — single HTML file, no install needed.

## Fitur

### 📅 Bulanan (Monthly View)
- KPI cards: total kWh, estimasi tagihan, rata-rata harian, hari puncak
- Bar chart pemakaian harian dengan highlight hari >130% rata-rata
- Year selector (default 2026–2028, tambah tahun via +)
- Form input 1 row: Bulan + Tanggal + Total kWh + Simpan + Hapus
- Input **Total kWh** saja (split day/night otomatis)

### 📊 Tahunan (Annual View)
- KPI: total kWh & tagihan, bulan tertinggi & terendah
- Bar chart tren bulanan + Perbandingan Semester
- Line chart Tagihan per Bulan
- Tabel Ringkasan Bulanan (3 kolom center, sama besar) + baris TOTAL
- Year selector (sinkron dengan bulanan)

### 🏠 Perangkat (Devices View)
- CRUD perangkat: tambah, edit, hapus (nama, ikon, kWh, warna)
- Doughnut chart proporsi konsumsi (dinamis)
- KPI: total perangkat, konsumen terbesar, mode aktif (Demo/Data Saya)

### ⚙️ Pengaturan Tarif
Preset tarif PLN:

| Golongan | Daya | Tarif |
|----------|------|-------|
| R-450 | 450 VA | Rp 415/kWh |
| R-900 | 900 VA | Rp 1.352/kWh |
| R-1300 | 1300 VA | Rp 1.444,70/kWh |
| R-2200 | 2200 VA | Rp 1.444,70/kWh |
| R-3500 | 3500–5500 VA | Rp 1.699,53/kWh |
| R-6600 | 6600 VA ke atas | Rp 1.699,53/kWh |
| Custom | — | Input manual |

### 💾 Dual LocalStorage
Dua penyimpanan terpisah, tidak saling timpa:

| Key | Mode | Isi |
|-----|------|-----|
| `wattMonitor_demo` | 📊 Use Demo Data | Data contoh (5 bulan + 8 perangkat) |
| `wattMonitor_real` | 📝 Use My Data | Data real user |

- Gonta-ganti mode kapan saja via tombol header
- Masing-masing tetap aman saat switch
- First visit → modal pilih Demo atau Mulai Kosong

### 📆 Multi-Year
- Default: 2026, 2027, 2028
- Tombol **+ Tahun** untuk tambah tahun baru
- Data per tahun tersimpan terpisah di localStorage
- Year selector di view Bulanan & Tahunan

## Tech Stack

- Vanilla HTML/CSS/JS — zero dependencies, zero build step
- [Chart.js 4.4.1](https://www.chartjs.org/) — semua chart
- Google Fonts: Space Mono + Syne
- Web Storage API (localStorage) — persistensi data

## Cara Pakai

```bash
open index.html
```

Tidak perlu server, npm, atau build process.

## Input Data

1. Klik tab **Bulanan**
2. Pilih tahun & bulan
3. Isi tanggal + **Total kWh**
4. Klik **Simpan**

Data otomatis tersimpan ke localStorage sesuai mode aktif (Demo/My Data).

### Kelola Perangkat

1. Klik tab **Perangkat**
2. **+ Tambah** untuk perangkat baru
3. ✏️ edit, 🗑️ hapus
