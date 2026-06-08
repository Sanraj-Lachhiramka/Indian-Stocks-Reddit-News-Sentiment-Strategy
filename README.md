# Indian Stocks Sentiment Investment Strategy

This project tests a simple sentiment-based investment strategy for Indian equities.

The notebook collects company-level news headlines, scores sentiment using VADER, ranks stocks monthly and compares an equal-weight sentiment portfolio against Nifty 50.

## Project Idea

The core question is:

Can public sentiment from free text sources help improve stock selection in the Indian market?

The strategy uses:

- Nifty 500 stock universe from NSE
- Google News RSS for company news headlines
- Optional Reddit data through PRAW
- Yahoo Finance price data through `yfinance`
- VADER sentiment scoring
- Monthly rebalancing
- Momentum and liquidity filters before final portfolio selection

## Workflow

1. Load the Nifty 500 universe.
2. Remove dummy NSE placeholder symbols.
3. Build search keywords for every stock.
4. Collect Google News headlines.
5. Score each headline using VADER sentiment.
6. Aggregate sentiment at stock-month level.
7. Rank stocks by sentiment signal.
8. Select sentiment candidates for the next month.
9. Apply momentum and liquidity filters.
10. Calculate equal-weight portfolio returns.
11. Compare with Nifty 50 and report performance metrics.

## Files

- `Indian_Stocks_Reddit_News_Sentiment_Strategy.ipynb` - main research notebook
- `requirements.txt` - Python dependencies
- `.gitignore` - ignores local notebook and environment files

## How To Run

Install dependencies:

```bash
pip install -r requirements.txt
```

Then open the notebook and run the cells from top to bottom.

Reddit data collection is optional. If using it, set:

```text
REDDIT_CLIENT_ID
REDDIT_CLIENT_SECRET
REDDIT_USER_AGENT
```

## Notes

This is a research and learning project, not investment advice.

The strategy can underperform Nifty 50 depending on data quality, market regime, and transaction costs. The main purpose is to demonstrate an end-to-end alternative-data workflow: data collection, sentiment analysis, signal construction, backtesting, and benchmark comparison.

## Limitations

- Google News RSS is not a complete historical news database, so headline coverage can be uneven across stocks and time periods.
- VADER is simple and explainable, but it is not finance-specific and may misunderstand market context.
- The backtest uses currently available index constituents, so there may be survivorship bias.
- Transaction costs, taxes, slippage and market impact are not fully modeled.
- Sentiment signals can be noisy, especially for stocks with low news volume.
- The benchmark is Nifty 50, while the stock universe is broader than Nifty 50, so performance comparison should be interpreted carefully.

## Future Work

- Use a finance-specific NLP model such as FinBERT or a model fine-tuned on Indian market headlines.
- Add transaction cost and slippage assumptions to make the backtest more realistic.
- Use historical index constituents to reduce survivorship bias.
- Add sector-neutral portfolio construction to avoid overexposure to one industry.
- Test different holding periods such as weekly, monthly and quarterly rebalancing.
- Combine sentiment with technical factors such as momentum, volatility and relative strength.
