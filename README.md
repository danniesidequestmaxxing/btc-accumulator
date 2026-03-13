# CRYPTO/ACC — BTC & ETH Accumulator Strategy Dashboard

A simulator and calculator for BTC and ETH accumulator structured products offered to institutional investors. Built for evaluating Metalpha's accumulator term sheets across different market scenarios.

## What is an Accumulator?

An accumulator is a structured product where the buyer commits to purchasing a fixed notional of crypto at a discounted **strike price** over a set tenor (3–12 months). The key mechanics:

- **Strike Price** — Buy crypto below spot (e.g. 72–90% of spot depending on tenor)
- **Knock-Out (KO)** — If price rises above KO level (110–140% of spot), the contract terminates early
- **2x Leverage Below Strike** — If price drops below strike, the buyer must purchase 2x the normal amount
- **Guaranteed Period** — Some variants guarantee accumulation for a fixed number of weeks regardless of KO

## Features

### BTC Accumulator
- **3 product variants**: Standard, Guaranteed (4W), Guaranteed (26W)
- 14 term sheet configurations per variant (3/6/9/12M tenors × 110–140% KO levels)
- All parameters editable (strike %, KO %, margin %)

### ETH Accumulator
- **Guaranteed (4W) variant** with 14 term sheet configurations
- Independent ETH spot price, portfolio, and scenario modeling

### Shared Capabilities
- **Live price feed** from CoinGecko API with manual override + slider
- **Monte Carlo simulation** — 1,000 GBM paths per scenario (seeded PRNG for reproducibility)
- **3-scenario framework** — Bearish, Base, Bullish with configurable probability weights and price ranges
- **DCA vs Accumulator comparison** — Probability-weighted expected P&L across all scenarios
- **Position strategy tools** — Hold analysis P&L chart + range trading calculator
- **Decision engine** — Automated recommendations for DCA vs accumulator allocation, hold vs trade, and risk assessment
- Editable portfolio inputs (holdings, avg cost, cash allocation)

## Tech Stack

Single-file HTML dashboard — no build step, no dependencies to install.

- **Tailwind CSS** (CDN) — utility-first styling
- **Chart.js** + annotation plugin — scenario charts, comparison bars, P&L curves
- **CoinGecko API** — live BTC + ETH prices
- **Vanilla JS** — Monte Carlo engine with xorshift128 PRNG + Box-Muller transform

## Usage

Open `index.html` in a browser, or visit the live deployment:

**[btc-accumulator.vercel.app](https://btc-accumulator.vercel.app)**

## Disclaimer

This tool is for simulation and educational purposes only. It is not financial advice. Accumulator products carry significant risk including forced 2x purchases below strike and early termination via knock-out. Consult a qualified financial advisor before entering any structured product.
