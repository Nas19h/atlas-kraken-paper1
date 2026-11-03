# Atlas Kraken Paper Trader

A free, static, iPhone-friendly paper-trading dashboard using Kraken's public WebSocket v2 market data.

## What it does
- Watches BTC/USD, ETH/USD and SOL/USD.
- Uses 1-minute candles, EMA(9)/EMA(21) and RSI(14).
- Simulates long-only spot trades with $500 allocations.
- Assumes 0.40% fee per side and 0.05% slippage per side.
- Uses 0.5% stop loss, 0.8% take profit, momentum exit, and 5-minute time exit.
- Halts new entries if equity falls to $9,750.
- Stores paper account state in browser localStorage.

## Important limitations
- This is an experimental rules-based prototype, not a proven profitable strategy and not financial advice.
- It does not connect to a Kraken account, does not use API keys, and cannot place live orders.
- It is long-only. No margin, leverage, shorts, or withdrawals.
- Signals are evaluated on completed 1-minute candles. It is not a 10-second execution system.
- Fees/slippage are assumptions; actual fees, spread, fill quality and latency vary.
- Keep the dashboard open. iOS may suspend background tabs; it is not a 24/7 unattended service.
- State is stored locally in that browser. Clearing site data can erase it.

## Deploy free with GitHub Pages from an iPhone
1. Sign in to GitHub in Safari and create a **public** repository named `atlas-kraken-paper`.
2. Add this `index.html` file to the repository root.
3. Open repository **Settings → Pages**.
4. Under Build and deployment, choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
5. Wait for the Pages URL to appear, then open it in Safari and tap **Connect live prices**.
6. Add the page to your Home Screen if you want quick access.

No secrets or API keys are required. Do not add any Kraken API key to this project.

## Strategy notes
The initial entry rule is EMA9 > EMA21, RSI between 52 and 70, and close above EMA9. Exit rules are stop loss, take profit, EMA/RSI momentum deterioration, or maximum holding time. A hard account safety halt prevents new entries after a $250 loss from the initial $10,000 equity.

This simple baseline must be tested and reviewed before any consideration of live trading.
