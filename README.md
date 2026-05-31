# ⚡ Watt Monitor

Dashboard monitor pemakaian listrik rumah — single HTML file, no install needed.

## Fitur

### 📅 Bulanan (Monthly View)
- KPI tiap card: **Kalender (kiri) | Real PLN (kanan)** + delta % vs bulan lalu
- Pemakaian Bulan Ini, Tagihan Estimasi, Rata-rata Harian (Kalender vs Real PLN)
- Hari Puncak (Kalender only)
- Bar chart pemakaian harian
- Year selector (default 2026–2028, + tambah tahun)
- Form input 1 row: Bulan + Tanggal + Total kWh (integer) + Simpan + Hapus

### 📊 Tahunan (Annual View)
- KPI: Total kWh & tagihan, Tertinggi & Terendah (Kalender vs Real PLN)
- **Tren Pemakaian per Bulan** — dual bar (Kalender + Real PLN)
- **Perbandingan Semester** — dual bar (Kalender + Real PLN)
- **Tagihan per Bulan** — dual line (Kalender + Real PLN)
- **Ringkasan Bulanan** — 5 kolom: Bulan, Pemakaian Kal/Real, Tagihan Kal/Real + TOTAL
- Year selector

### 🏠 Perangkat (Devices View)
- CRUD perangkat: tambah, edit, hapus (nama, ikon, kWh, warna)
- Doughnut chart proporsi konsumsi
- KPI: total perangkat, konsumen terbesar, mode aktif (Demo/Data Saya)

### 📅 Master Periode PLN
- Atur periode billing sesuai cara PLN (start month/day, end month/day)
- 12 periode default (26–25 tiap bulan)
- **Tambah Periode Kustom**: pilih bulan + tahun + start/end date
- Edit inline, reset, hapus periode kustom
- `getRealKwh(month)` hitung ulang dari dailyData berdasarkan periode

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
Dua penyimpanan terpisah:

| Key | Mode |
|-----|------|
| `wattMonitor_demo` | 📊 Use Demo Data |
| `wattMonitor_real` | 📝 Use My Data |

- Gonta-ganti mode kapan saja via tombol header
- First visit → modal pilih Demo atau Mulai Kosong

### 📆 Multi-Year
- Default: 2026, 2027, 2028
- Tombol **+ Tahun** untuk tambah tahun baru
- Data per tahun terpisah di localStorage

### 📊 Data Model
- `dailyData[month][day]` — sumber utama, integer kWh
- `getMonthlyTotal(m)` — hitung total kalender dari dailyData
- `getRealKwh(month)` — hitung total real PLN dari `billingConfig[month]` atau custom period
- `sumPeriod(p)` — jumlahkan dailyData dalam range startM/startD – endM/endD
- `DEMO_TOTALS` — `[285,262,298,310,327,0,0...]` untuk seed demo

## Tech Stack
- Vanilla HTML/CSS/JS — zero dependencies
- Chart.js 4.4.1 — semua chart
- Google Fonts: Space Mono + Syne
- Web Storage API (localStorage)

## Cara Pakai
```bash
open index.html
```

## Input Data
1. Tab **Bulanan** → pilih tahun & bulan
2. Isi tanggal + **Total kWh** (integer)
3. Klik **Simpan** — otomatis tersimpan di localStorage

## Atur Periode PLN
1. Klik badge `📅 Periode PLN` di header
2. Edit start/end date per bulan (inline)
3. Klik **+ Tambah Periode Kustom** untuk periode tambahan (pilih bulan & tahun)
4. Klik **Simpan Semua**
