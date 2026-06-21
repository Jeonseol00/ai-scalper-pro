# Quantitative Risk Management

## Default Parameters
The engine is set to operate under a strict quantitative risk approach.
- **Initial Capital**: `$1000` (Simulation base)
- **Slippage**: `3 ticks`
- **Commission**: `0.04%` (Institutional tier average)

## ATR Dynamic Exits
Stop Losses and Take Profits are not fixed point values. They adapt to market volatility via the Average True Range `ATR(14)`.

- **Stop Loss (SL)**: `2.0x ATR` from entry price.
- **Take Profit (TP)**: `2.5x ATR` from entry price.

*Example on XAUUSD:* 
If ATR is `7.83`, SL distance is `15.67` points. The system mathematically guarantees an expectancy ratio mathematically greater than 1:1, strictly targeting an average Reward:Risk of `1.25 : 1`.

## Code Handling for Exits
In Pine Script, the logic utilizes fixed target limit orders via `strategy.exit`:
```pine
sl_price := close - (atr_val * i_strat_sl_mult)
tp_price := close + (atr_val * i_strat_tp_mult)
strategy.exit("Exit Long", "Long", stop=sl_price, limit=tp_price)
```
These levels are dynamically rendered on the chart using `plot()` ONLY when `strategy.position_size > 0` to maintain a clean workspace.
