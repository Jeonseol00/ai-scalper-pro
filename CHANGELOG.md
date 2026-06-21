# Changelog

All notable changes to this project will be documented in this file.

## [v1.1.0-PRO] - 2026-06-21
### Added
- **Dynamic Exit Visualization**: Plotted Active SL (Red) and Active TP (Green) dynamically triggering only during open positions.
- **RSI Pivot Divergence Validation**: Verified the mathematical integrity of the 5-candle lookback to ensure zero-repainting during backtest execution.

## [v1.0.0-PRO] - 2026-06-20
### Added
- **Core Strategy Engine**: Migrated from `indicator()` to `strategy()` framework for both BTC and XAU scripts.
- **Institutional Liquidity Metrics**: Implemented Order Blocks (Supply/Demand) and Fair Value Gaps (FVG) array processing.
- **Confluence Scoring System**: Developed an 8-factor mathematical scoring system (HTF, VWAP, EMA, Div, VSA, Pin Bar, Session, Sweep).
- **Risk Management Engine**: Integrated ATR-based SL/TP mapping to exact institutional targets.
- **Dashboard UI**: Comprehensive on-chart telemetry table.
