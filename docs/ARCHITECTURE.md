# AI Scalper Pro - System Architecture

## 1. Top-Down Bias Engine
The strategy utilizes a macro-to-micro analytical approach. It never takes a position against the institutional flow.
- **Trend Filter**: 15-minute timeframe closing price vs `HTF EMA 200`.
- **Institutional Volume**: Price location relative to `VWAP` (Volume Weighted Average Price) establishes true buying/selling pressure.

## 2. Liquidity Zones (Smart Money Concepts)
The script dynamically processes arrays of maximum 5-15 boxes for:
- **Order Blocks (OB)**: Tracks the last aggressive pivot points causing significant displacements.
- **Fair Value Gaps (FVG)**: Monitors 3-candle imbalance zones where algorithmic liquidity is absent.

## 3. Confluence Scoring Matrix
Rather than relying on single indicators, the core logic sums boolean values into a dynamic `score` (0 to 8).
The equation requires `score >= i_strat_min_score` (User default: 5).
Components evaluated per bar:
1. `htf_bull` (Price > EMA 200)
2. `vwap_bias` (Price > VWAP)
3. `ema_fast_bias` (Price > EMA 21)
4. `bull_div` (RSI Pivot-Based Divergence)
5. `vsa_manip` (Volume Spread Anomaly / Fakeout)
6. `bull_pin` (Rejection Diamonds)
7. `session_active` (London/US Volume overlay)
8. `bull_sweep` (Water droplets / sweeping stops below structure)

## 4. Execution Gateway
When the Confluence Score condition is met AND the price is at a valid Demand/Supply Order Block (or has performed a liquidity sweep), the `sig_buy` / `sig_sell` triggers.
The `strategy.entry` function fires sequentially.
