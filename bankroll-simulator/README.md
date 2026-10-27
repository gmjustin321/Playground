# 20-Year Bankroll Simulator

A single-page tool that projects a trading bankroll from today out to as many as 20 years. Set the time horizon, starting bankroll, size per trade (% of bankroll), trades per day, and trade results, and it compounds every trade across 1,000 simulated runs.

It is one static file, `index.html`, with no build step and no dependencies beyond Google Fonts.

## Deploy on Netlify

1. In Netlify, import the `Playground` repository from GitHub.
2. Leave the base directory and build command empty. The `netlify.toml` at the repository root publishes this folder.
3. Deploy. Every push to `main` redeploys the site.

## Run locally

Open `index.html` in any browser.

## Inputs

- **Starting bankroll** and **size per trade** (% of the bankroll at the time of each trade)
- **Time horizon**: 1 to 20 years. The time axis, key numbers and table all follow it.
- **Trades per day**, with options to skip weekends and NYSE market holidays
- **Trade results**, entered one of two ways:
  - **Win / loss**: win rate, average win and average loss. Trades win at random, so the chart shows a range of outcomes.
  - **One average**: a single P/L per trade, from -100% to +999,999,999%. Every trade returns exactly that, so the result is one line.
- **Position cap** (optional): a dollar limit on each trade. Once a position hits it, gains add up instead of compounding.

P/L is a percentage of the money in the trade, so -100% means the option expired worthless.

## What the chart shows

- **Median**: the middle outcome of 1,000 simulated runs
- **Range**: the middle 50% and 80% of runs
- **One run**: a single random path with real streaks and drawdowns (the refresh button draws a new one)
- **Mean**: the average of all runs, pulled up by a few very large outcomes

The key numbers below the chart include edge per trade, break-even win rate, Kelly size, typical worst drawdown, and the chance of ending below the starting bankroll.

## Limits

The simulator takes your stats as given. It assumes every win pays the average win, every loss costs the average loss, trades are independent, and the stats hold for the whole horizon. It does not backtest entries or look at market data, and it leaves out fees, slippage, taxes, deposits and withdrawals. Inputs are saved in the browser's local storage.
