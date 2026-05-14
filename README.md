# DeepLOB Transformer

Transformer-enhanced DeepLOB implementation for high-frequency limit order book prediction on the FI-2010 dataset.

This project reproduces and extends the DeepLOB architecture by replacing the original LSTM module with a Transformer encoder while preserving the CNN + Inception feature extractor.

Original Paper:
https://arxiv.org/pdf/1808.03668

Original Github Repo:
https://github.com/zcakhaa/DeepLOB-Deep-Convolutional-Neural-Networks-for-Limit-Order-Books/tree/master

---

## Project Overview

The project investigates deep learning approaches for short-term mid-price movement prediction using limit order book (LOB) data.

Models implemented:
- Original DeepLOB (CNN + Inception + LSTM)
- Attention DeepLOB (CNN + Inception + Self-Attention)
- Feature-engineered DeepLOB with imbalance signals

Experiments include:
- architecture ablation studies,
- market microstructure feature engineering,
- confidence-threshold trading simulation,
- classification and trading metric evaluation.

---

## Dataset

Dataset:
- FI-2010 Limit Order Book Benchmark Dataset

Prediction task:
- classify future mid-price movement into:
  - Downward
  - Stationary
  - Upward

---

## Architecture

### Original DeepLOB

LOB Input
→ CNN Blocks
→ Inception Modules
→ LSTM
→ Classification Head

### Attention DeepLOB

LOB Input
→ CNN Blocks
→ Inception Modules
→ Transformer Encoder
→ Classification Head

---

## Results

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---|---|---|---|
| Original DeepLOB | 75.62% | 73.85% | **73.94%** | 73.85% |
| Feature Engineered DeepLOB | 74.53% | 72.68% | 72.21% | 72.43% |
| Attention DeepLOB | **76.37%** | **75.03%** | 73.58% | **74.13%** |

Key findings:
- Replacing the LSTM with a Transformer encoder improved predictive accuracy.
- Explicit imbalance features slightly degraded performance, suggesting the CNN backbone already captured liquidity imbalance implicitly.
- Classification improvements did not directly translate into profitable trading performance under naïve execution assumptions.

---

## Trading Simulation

A simplified trading simulator was implemented using model predictions as directional signals.

Assumptions:
- Long/short trading
- Fixed 1-share position sizing
- Mid-price execution
- No transaction costs
- No slippage
- Confidence-threshold signal filtering

Trading metrics evaluated:
- Sharpe ratio
- Win rate
- Total PnL
- Trade frequency

---

## Future Improvements

- Confidence-calibrated trading strategies
- Multi-horizon forecasting
- Temporal order-flow features
- Probabilistic position sizing
- Transaction cost modeling
- Cross-asset generalization

---

## References

- DeepLOB: Deep Convolutional Neural Networks for Limit Order Books
- FI-2010 Benchmark Dataset
