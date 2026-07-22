# Customer Segmentation — Unsupervised Learning

## Project Overview
Segments UK customers of an online retailer (Online Retail II dataset) into meaningful
groups using RFM (Recency, Frequency, Monetary) features and three unsupervised
clustering algorithms: **K-Means**, **Agglomerative Hierarchical Clustering**, and
**DBSCAN**. Segments are translated into actionable marketing personas (e.g.
Champions, At-Risk, Hibernating).

## Dataset
- Source: UCI Online Retail II — https://archive.ics.uci.edu/dataset/502/online+retail+ii
  (Kaggle mirror: https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci)
- ~1M UK e-commerce transactions (2009–2011), filtered to `Country == 'United Kingdom'`
  with non-null `CustomerID`.

## How to Run
1. Download `online_retail_II.xlsx` (or the CSV version) into this folder.
2. `pip install -r requirements.txt`
3. Open `CustomerSegmentation_UnsupervisedLearning.ipynb` and run all cells top to bottom.
4. A few cells require you to manually pick a value after inspecting a plot
   (`k_optimal` after the elbow/silhouette plots, `optimal_eps` after the k-NN distance plot,
   `best_model`/`persona_map` after the metrics comparison table) — this is intentional and
   matches the exam's tuning-by-inspection steps.

## Outputs
- `rfm_scaler.pkl` — fitted StandardScaler
- `customer_segmentation_model.pkl` — best clustering model
- `summary_report.md` — written summary of findings

## Cluster Personas (example structure — fill in with your actual results)
| Cluster | Persona | Recency | Frequency | Monetary | Action |
|---|---|---|---|---|---|
| 0 | Champions | Low | High | High | Loyalty program invite |
| 1 | Loyal Customers | Low-Mid | Mid | Mid-High | Cross-sell bundles |
| 2 | At-Risk | Mid-High | Mid | Mid | Discount coupon (7-day expiry) |
| 3 | Hibernating | High | Low | Low | Win-back campaign |
| 4 | New Customers | Low | Low | Low-Mid | Onboarding series |




## 🏠 Home Page ( Recorded Video )

> [Add Screenshot Here](https://drive.google.com/drive/folders/1jALHllQdHXEeE-rQwBNdbGqjfXxMuBy8?q=type:video%20parent:1jALHllQdHXEeE-rQwBNdbGqjfXxMuBy8)

---
