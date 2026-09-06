# Indian Market Data — NSE / BSE / MCX

Daily OHLC + volume + open interest for the Indian markets, plus the complete
instrument catalogue. Collected via the Groww Trade API.

## Contents

| Path | What |
|---|---|
| `instruments_master.csv` | **All 134,541 instruments** — NSE, BSE, MCX. Symbol, ISIN, lot size, tick size, expiry, strike, segment |
| `equity/` | Daily candles per stock (~12,700 NSE + BSE stocks) |
| `index/` | Daily candles per index (31) |
| `future/` | Daily candles per futures contract |

## File format

One CSV per instrument, named by its Groww symbol:

```
timestamp,open,high,low,close,volume,oi
2026-03-16T00:00:00,1420.5,1438.0,1415.2,1432.8,4821330,
```

## Collection notes

- **Daily interval.** The API caps any single request at 180 days regardless of
  interval, so history is fetched in 180-day windows.
- **Breadth-first.** Every instrument's most recent window was fetched before
  any older window, so coverage is even across instruments rather than deep for
  a few.
- **Resumable.** Collection is incremental; history extends backwards over time.

## Reproduce it yourself

The collector is open source:
**https://github.com/sahilempire/nifty-options-research-lab**
(`src/gab/data/bulk_download.py`)

You need your own Groww API subscription.

## Source and terms

Data originates from NSE/BSE/MCX via the Groww Trade API and remains subject to
the exchanges' and Groww's terms of use. Published here for research and
educational purposes. If you intend commercial use, obtain data licensed
directly from the exchanges.

No warranty of accuracy or completeness. Not investment advice.
