# Midterm Project — Visualisasi Data (CAK4XBB3)

**Topik:** Analisis Tren Harga Saham Bank Besar Indonesia (BBCA, BBRI, BMRI, BBNI) 2014–2024

**Sumber data:** [Dataset Saham Bank Indonesia 2014–2024 (Kaggle)](https://www.kaggle.com/datasets/cmglonly/dataset-saham-bank-indonesia-2014-2024/data)
— data harian (hari bursa), 8 Des 2014 – 3 Des 2024, kolom `Date, Adj Close, Close, High, Low, Open, Volume`.

Ketentuan lengkap tugas: [`docs/Midterm Project.pdf`](docs/Midterm%20Project.pdf)

## Struktur Folder

```
├── dataset/                  ← 4 CSV saham (JANGAN diubah)
├── kerja/                    ← notebook kerja tiap anggota
│   ├── A_setup_data.ipynb
│   ├── B_line_area.ipynb
│   ├── C_multi_seasonal.ipynb
│   └── D_tren.ipynb
├── figures/                  ← semua PNG hasil plot (dipakai di laporan & slide)
├── ai/                       ← screenshot & prompt AI, satu subfolder per anggota
├── deliverables/             ← Laporan.pdf, Slide, Deklarasi_AI.pdf, prompt.md
├── docs/                     ← dokumen penugasan
└── Midterm_Kelompok_X.ipynb  ← notebook FINAL gabungan
```

## Pembagian Tugas

| Anggota | Tanggung jawab | Notebook | Bagian laporan |
|---|---|---|---|
| A — **Aprilianza** | Setup data, profil dataset, **integrasi & cek Run All** | `kerja/A_setup_data.ipynb` | 1. Pendahuluan, 2. Dataset |
| B — **Arfi** | Line plot + Area plot (stacked volume) | `kerja/B_line_area.ipynb` | 3. Visualisasi (Line, Area) |
| C — **Jeany** | Multiple time series (direct labeling) + Seasonal/Calendar heatmap | `kerja/C_multi_seasonal.ipynb` | 3. Visualisasi (Multi, Seasonal) |
| D — **Irgi** | Moving average (≥2 window + trade-off NaN) + fitting `np.polyfit` | `kerja/D_tren.ipynb` | 4. Analisis Tren |
| E — **Bill** | Laporan, slide (≤10), video (≤10 menit), deklarasi AI, daftar pustaka | — | 5. Kesimpulan + penyusunan |

## Kontrak Bersama (wajib diikuti agar mudah digabung)

1. **Sel setup** dibuat Aprilianza (Anggota A) dan dipakai *persis sama* di paling atas semua notebook kerja. Variabel yang disediakan:
   - `df_all` — long format: `Date, Ticker, Open, High, Low, Close, Adj Close, Volume`
   - `adj_wide` — pivot Adj Close (index `Date`, kolom = ticker)
   - `vol_wide` — pivot Volume
   - `WARNA` — dict warna tetap per bank (BBCA biru, BBRI oranye, BMRI aqua, BBNI kuning)
   - `HARI_DIBUANG` — tanggal placeholder hari libur (Volume 0, harga datar) yang sudah dibuang
   - `simpan_fig(fig, nama)` dan `format_tanggal(ax)` — helper simpan gambar & sumbu tahun
   - Analisis memakai **`Adj Close`** (sudah disesuaikan dividen/split), bukan `Close`
   - Sel setup sudah terpasang di semua notebook `kerja/` dan notebook final; bisa jalan di Colab (data otomatis diambil dari GitHub)
2. **Jangan ubah** variabel bersama; variabel tambahan pakai prefix bagian (`b_`, `c_`, `d_`).
3. Path data relatif: dari `kerja/` pakai `../dataset/`, dari root pakai `dataset/`.
4. Simpan gambar ke `figures/NN_nama.png`:
   `01–02` = B, `03–04` = C, `05–06` = D.
5. Setiap plot diikuti sel markdown **Insight:** (2–3 kalimat) — dipakai langsung di laporan.
6. Sebelum push: **Restart & Run All** notebook kamu harus tanpa error.
7. Jika memakai AI: simpan screenshot (nama platform + prompt + respons) dan prompt ke `ai/<nama>/` (mis. `ai/arfi/`), lalu setor 1 baris tabel deklarasi ke Bill (Anggota E).

## Alur Kerja Git

```bash
git pull                     # selalu sebelum mulai
# kerjakan HANYA notebook bagianmu
git add kerja/B_line_area.ipynb figures/01_*.png figures/02_*.png
git commit -m "B: line plot BBCA"
git push
```

Hanya Aprilianza (Anggota A) yang mengedit `Midterm_Kelompok_X.ipynb` (untuk menghindari konflik notebook).

## Urutan Pengerjaan

1. Sepakati pertanyaan riset & konvensi; A push sel setup.
2. B, C, D kerjakan bagian masing-masing; E siapkan template laporan & slide.
3. A gabungkan ke notebook final: Setup → B → C → D → Kesimpulan → Deklarasi AI → Daftar Pustaka; cek Run All.
4. E finalisasi laporan & slide.
5. Rekam video; E kumpulkan deklarasi AI.

## Checklist Pengumpulan

- [ ] Notebook `.ipynb` final — Run All tanpa error
- [ ] Laporan PDF 3–5 halaman
- [ ] Slide maks. 10 (PDF/PPTX)
- [ ] Video presentasi maks. 10 menit
- [ ] Deklarasi AI (PDF) + screenshot (image) + prompt (MD)
