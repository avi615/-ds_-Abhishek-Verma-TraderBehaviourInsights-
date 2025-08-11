THIS IS THE DATA SCIENCE PROJECT :TRADER BEHAVIOUR INSIGHTS 


BY : ABHISHEK VERMA


1.Objective:
To analyze historical trading data (~211K trades) and understand the relationship between trader performance and market sentiment.

To engineer meaningful features from raw trade records.

To build a predictive model that can classify/predict outcomes or patterns based on sentiment and trade attributes.

2. Data Overview
Size: 211,224 trades, 16+ original columns.

Content: Account ID, trade prices, sizes, timestamps, directions (Buy/Sell), PnL, fees, and market sentiment classification (Fear, Greed, Extreme Fear, Neutral, Extreme Greed).

3. Feature Engineering (Trade-Level)
You transformed raw trade logs into rich performance features:

Feature	Description
trade_pnl	Direct copy from Closed PnL (per-trade profit/loss).
size_usd	Position size in USD.
roi	Return on Investment per trade: trade_pnl / size_usd.
sign	Trade outcome — Win (1), Loss (-1), Break-even (0).
holding_time_hours	Hours a position was held (from Start_Position to Timestamp).
4. Aggregated Trader Performance Metrics
You grouped by Account to summarize historical performance:

Trade counts (total_trades, count_trades)

Profit & Loss totals (total_pnl, pnl_sum, pnl_per_trade)

Win rate (proportion of profitable trades)

ROI stats (avg_roi, median_roi)

Risk metrics (pnl_std, max_drawdown, Sharpe ratio)

Capital usage (avg_trade_size)

Profit factor (profit per losing trade)

5. Sentiment Analysis
Classified all trades into Fear, Greed, Extreme Fear, Neutral, Extreme Greed.

Frequency analysis: Fear most common, then Greed; extreme sentiments less common.

Transition patterns: Tracked how market moved from one sentiment state to another.

Created yearly sentiment proportion charts showing sentiment shifts over time.

Analyzed Fear & Greed Index trends to visualize cyclical nature of market emotions.

6. Model Building – Sentiment-Driven Prediction
Target: Trade outcome (profitable vs not profitable) or ROI prediction.

Features Used:
Encoded Sentiment, Side (buy/sell), Execution Price, Fee, Size USD, holding_time_hours.

Model Chosen: XGBoost Classifier (Gradient Boosting) — chosen for:

Handling non-linear feature interactions.

Good performance with categorical + numeric data.

Interpretability via feature importance and SHAP.

7. Model Evaluation
Classification Metrics: Accuracy, Precision, Recall, F1-score, AUC-ROC.

Confusion Matrix:

Strong at detecting losing trades (high True Negative rate).

Captured many wins, but some profitable trades missed.

Feature Importance:

Trade side (Side_Encoded)

Execution Price

Fee

Size USD

SHAP Analysis:

Trade direction & price have the largest impact on model predictions.

Fees negatively influence predicted profitability.

Trade size has smaller but still notable impact.

8. Visual Insights
Distribution Charts: Win rate, ROI, Max Drawdown.

Correlation Plots: Linking sentiment states to performance.

Bubble Charts: Comparing Sharpe Ratio, PnL, trade counts, and trade size.

Yearly Sentiment Stack Plot: Showing changes in sentiment dominance.

Fear & Greed Cycles: Highlighting peaks (greed) & troughs (fear) as potential opportunity/risk points.

9. Key Takeaways
Sentiment drives behavior: Most traders operate during Fear and Greed phases.

Direction matters most: Whether a trade is buy or sell strongly correlates with the outcome.

Profitability ≠ Win Rate: Some traders with moderate win rates still achieve high PnL (likely due to trade size or big wins).

Risk management is critical: Large drawdowns are rare but severe when they occur.

Adaptive strategies — tuning exposure and risk controls based on prevailing sentiment — could improve performance.
