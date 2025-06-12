# 📊 Custom Unsupervised Machine Learning Framework for Stock Segmentation

This project applies unsupervised learning techniques, specifically **K-Means clustering**, to group NSE 200 stocks based on historical risk-return characteristics. It was conducted as part of an MBA academic submission and was designed to assist in **data-driven portfolio decisions** for wealth management clients.

---

## 📁 Dataset
- **Source**: NSE 200 historical data (5 years till May 13, 2025)
- **Columns**:  
  `date`, `symbol`, `industry`, `sector_index`, `open`, `high`, `low`, `close`, `volume`, `sector_open`, `sector_high`, `sector_low`, `sector_close`, `sector_volume`
- **Frequency**: Daily OHLCV

---

## 🧪 Methodology

### ✔️ Preprocessing
- Handled missing values using `na.locf()` (forward fill)
- Filtered stocks with at least 200 observations
- Engineered key features:
  - `avg_return`: Mean of daily log returns
  - `sd_return`: Volatility
  - `max_drawdown`: Worst drawdown from peak
  - `avg_volume`: Trading activity
  - `return_autocorr`: Momentum signal (1-day autocorrelation)

### ✔️ Feature Scaling
- Standardized all features using z-score scaling
- Removed zero-variance variables

### ✔️ PCA
- Applied Principal Component Analysis
- Reduced dimensionality while preserving >65% variance

### ✔️ Clustering
- Optimal clusters determined via `NbClust` and scree analysis
- Final model: **K-Means with 5 clusters**

---

## 📈 Key Visualizations
- 📌 Missing value heatmap
- 📌 Volume distribution (log scale)
- 📌 Close price forward fill
- 📌 Feature scaling comparison (before vs after)
- 📌 PCA scree plot and cluster scatter plot
- 📌 Radar chart for cluster behavior

---

## 🧠 Cluster Interpretation

| Cluster | Avg Return | Volatility | Drawdown | Volume     | Interpretation                 |
|---------|------------|------------|----------|------------|--------------------------------|
| 1       | High       | High       | High     | Medium     | 📈 High-growth but volatile     |
| 2       | Moderate   | Moderate   | Mid      | High       | ✅ Momentum-driven              |
| 3       | Low        | Low        | Low      | Moderate   | 🛡️ Conservative/Stable picks    |
| 4       | Negative   | High       | Worst    | Low        | 🚫 Avoid — High risk, low reward |
| 5       | Low        | Very High  | Very Bad | Extreme    | ⚠️ Volume anomaly, speculative  |

---

## 💡 Use Case
Designed as an internal decision-support tool for wealth managers at **Hedge Equities** to align investment decisions with client risk profiles.

---

## 👨‍🎓 Author
Jeff Salim Pushpanath  
MBA, Business Analytics  
Project done under Christ University

---

## 📄 License
This project is for educational and non-commercial use only.
