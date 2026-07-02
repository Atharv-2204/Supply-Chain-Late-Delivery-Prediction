# 🚚 Supply Chain Analysis — Late Delivery Prediction

An end-to-end data science project analysing 180,519 real supply chain orders to uncover delivery bottlenecks and build a machine learning model that predicts late deliveries before they happen.

---

## 🎯 Project Objective

To answer two connected business questions:
1. **Diagnostic** — Where and why are deliveries running late? (shipping mode, region, product category)
2. **Predictive** — Can we build a model that flags high-risk orders *before* they ship, so operations teams can intervene proactively?

---

## 🗄️ Dataset

**Source:** [DataCo Supply Chain Dataset](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis) — Kaggle

| Detail | Info |
|---|---|
| Rows | 180,519 orders |
| Columns | 53 (reduced to relevant features after cleaning) |
| Domain | Global e-commerce logistics — multiple markets, regions, shipping modes |
| Tool used | Python (Pandas, Scikit-learn, Seaborn) in Jupyter Notebook |

---

## 🔑 Key Findings

1. **Over half of all orders arrive late** — the overall late delivery rate is **57.28%**, a significant operational issue affecting the majority of shipments.
2. **First Class shipping shows a 100% late delivery rate — but this reflects an unrealistic scheduling commitment, not poor carrier performance.** All 27,814 First Class orders are scheduled for just 1 day of shipment, while actual shipping time across the dataset averages 3.5 days. This points to a root-cause SLA problem rather than a fulfillment failure — the business is setting a delivery promise operations cannot realistically meet.
3. **Central Africa is the highest-risk region** — with a **60.7%** late delivery rate, regional logistics infrastructure appears to be a major delay driver.
4. **Late deliveries carry a real financial cost** — orders delivered late account for **$2,231,967** in total profit, representing significant value at risk from delivery failures.
5. **Random Forest was the best-performing predictive model**, achieving **70.18% accuracy** and a **0.760 ROC-AUC score**, meaningfully outperforming both Logistic Regression (0.726 ROC-AUC) and a single Decision Tree (0.750 ROC-AUC).
6. **Shipping mode and scheduled delivery days were the strongest predictors** of late delivery, based on Random Forest feature importance — more influential than product category or customer segment.

---

## 🛠️ Skills & Techniques Demonstrated

| Category | Techniques used |
|---|---|
| Data cleaning | Removing PII columns, handling missing values, date parsing, deduplication |
| Feature engineering | Delivery delay calculation, late-delivery binary flag, time-based features (month, day of week), profit margin % |
| Exploratory analysis | Grouped aggregations across shipping mode, region, and category; correlation heatmap |
| Visualization | Seaborn bar charts, monthly trend line charts, confusion matrix heatmap, feature importance chart |
| Machine learning | Logistic Regression, Decision Tree, Random Forest — trained, compared, and evaluated |
| Model evaluation | Accuracy, ROC-AUC, classification report, confusion matrix |
| Applied ML | Live prediction on a new sample order with safe handling of unseen categorical labels |
| Business translation | Region-by-region "best shipping mode" recommendation table generated directly from the model's underlying data |

---

## 📊 Business KPI Summary

```
==================================================
SUPPLY CHAIN KPI DASHBOARD
==================================================
Total Orders          : 180,519
Late Delivery Rate    : 57.28 %
Average Delay (days)  : 0.57
Total Sales           : $ 36,784,735
Total Profit          : $ 3,966,903
Avg Profit Margin (%) : 10.83
==================================================
```

---

## 🤖 Model Comparison

| Model | Accuracy | ROC-AUC |
|---|---|---|
| Logistic Regression | 69.24% | 0.726 |
| Decision Tree | 70.01% | 0.750 |
| **Random Forest (best)** | **70.18%** | **0.760** |

> **On model performance:** A ROC-AUC of 0.76 indicates moderate-to-good predictive power — the model meaningfully outperforms random guessing and provides a usable risk signal, but delivery delay is clearly influenced by real-world factors not captured in this dataset (e.g. live traffic, weather, carrier capacity on a given day). Rather than over-claiming accuracy, this is presented as a decision-support tool for flagging higher-risk orders, not a guarantee.

---

## 💡 What I Learned

- How to build a complete data science pipeline from raw CSV to a working predictive model — cleaning, feature engineering, EDA, modeling, and evaluation as connected stages rather than isolated exercises.
- The importance of comparing multiple models rather than committing to one algorithm — Random Forest's advantage over Logistic Regression only became clear through direct side-by-side ROC-AUC comparison.
- How to handle unseen categorical values at prediction time using a safe-encoding function, rather than letting the model crash on new data it hasn't seen before.
- That a moderate model score (70% accuracy) is still valuable and worth presenting honestly, rather than treating anything short of a very high score as a failure — model evaluation is about usefulness, not just the headline number.
- How to translate model output into an operational recommendation (the region-by-shipping-mode table) — turning a black-box prediction into something a logistics manager could actually act on.
- The difference between reporting a metric and diagnosing its cause — the First Class 100% late rate initially looked like a performance failure, but digging into the scheduling data revealed it was a root-cause SLA design issue (1-day promised shipping vs. a 3.5-day dataset average), which is a far more actionable insight for the business.

---

## 🚀 How to Run This Project

1. Clone this repository
2. Install dependencies: `pip install pandas numpy matplotlib seaborn scikit-learn`
3. Download `DataCoSupplyChainDataset.csv` from the [Kaggle dataset page](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis) and place it in the project folder
4. Open `Supply_chain_analysis.ipynb` in Jupyter Notebook or JupyterLab
5. Run all cells in order

---

## 🙋 About

Built by **[Your Name]** as part of a data analyst portfolio project.

- 🔗 LinkedIn: [your-linkedin-url]
- 📧 Email: your@email.com

---

*If you found this useful, please ⭐ star the repository!*
