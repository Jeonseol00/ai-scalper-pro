# AI Scalper Pro (BTC & XAU)

**Institutional-Grade AI-Assisted Scalping System for TradingView (Pine Script v5)**

Proyek ini adalah indikator dan strategi kuantitatif canggih yang dibangun untuk memberikan analisis likuiditas tingkat institusional dan sinyal eksekusi probabilitas tinggi untuk *scalping* (dioptimalkan untuk timeframe 15m).

## 🚀 Fitur Utama
1. **Smart Market Structure:** Deteksi cerdas untuk Order Blocks (Demand/Supply) dan Fair Value Gaps (FVG).
2. **Liquidity Sweeps:** Mengidentifikasi manipulasi pasar saat harga menyapu titik likuiditas (High/Low sebelumnya) untuk memicu pembalikan.
3. **RSI Divergence (Pivot-Based):** Mendeteksi divergensi indikator momentum dengan harga secara presisi. (Catatan: Menggunakan konfirmasi lookback 5 candle).
4. **Volume Spread Analysis (VSA):** Mengukur anomali volume dan pelemahan rentang harga.
5. **Dynamic Risk Management (ATR):** Kalkulasi *Stop Loss* (SL) dan *Take Profit* (TP) adaptif secara dinamis berdasarkan nilai *Average True Range* (ATR).

## 🧠 Confluence Scoring System
Jantung dari strategi ini adalah **Sistem Skor (1-8)**. Sistem tidak akan melakukan *blind-entry* berdasarkan satu sinyal tunggal. Sebaliknya, ia mengevaluasi 8 kondisi fundamental:
- HTF Bias (EMA 200)
- VWAP Bias
- Fast EMA Momentum
- RSI Divergence
- VSA Manipulation
- Rejection / Pin Bar
- Time Session (Asia/US)
- Liquidity Sweep

Jika skor konfluensi mencapai ambang batas minimum (default: `5`), maka sistem akan mengirimkan sinyal eksekusi atau `strategy.entry`.

## 🛠️ Visual & UI
- **Dashboard Cerdas:** Menampilkan tren, status likuiditas, skor konfluensi, dan sinyal secara *real-time*.
- **Active SL & TP Lines:** Secara visual menggambar garis target TP (Hijau) dan batas kerugian SL (Merah) di chart HANYA ketika perdagangan sedang berlangsung.
- **Level Harian:** Menggambar *Previous Day High* (PDH) dan *Previous Day Low* (PDL) sebagai referensi struktur, yang terpisah dari eksekusi trade.

## ⚙️ Cara Penggunaan di TradingView
1. Buka [TradingView](https://www.tradingview.com/).
2. Buka **Pine Editor** di bagian bawah layar.
3. Copy-Paste isi dari file `BTC_AI_Scalper_Pro.pine` atau `XAU_AI_Scalper_Pro.pine`.
4. Klik **Add to Chart** (Tambahkan ke Diagram).
5. (Sangat Penting) Buka **Settings (Corak/Style)** indikator dan pastikan:
   - *Trades on Chart* dimatikan jika Anda ingin melihat Segitiga Sinyal Kustom.
   - Atau biarkan menyala untuk melihat panah eksekusi *Strategy Tester* bawaan.

## ⚠️ Peringatan untuk Developer (Collaborators)
- **Lag Divergence:** Fungsi Divergence menggunakan `ta.pivotlow`/`ta.pivothigh` dengan *lookback* 5 candle. Secara matematis, ada jeda konfirmasi 5 candle. Sistem tidak *repainting* untuk *backtesting*, ia mengambil keputusan entry persis setelah sinyal terkonfirmasi.
- **Box Coordinates:** Di Pine Script v5, mengambil nilai batas box secara historis untuk *backtest* memiliki keterbatasan, sistem mengatasinya dengan evaluasi iterasi array *Order Block*.

---
*Created and maintained by [Gojo Titiw](https://gitlab.com/gojotitiw). Selamat berkontribusi!*
