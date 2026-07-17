# Unsupervised Learning — PR 1: Mall Customer Segmentation

## Project Overview
This project applies three unsupervised learning algorithms — **K-Means**, **Agglomerative Hierarchical Clustering**, and **DBSCAN** — to segment mall customers based on their annual income and spending behaviour.

## Dataset
- **Name:** Mall Customer Segmentation Data
- **Source:** Kaggle — https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python
- **File:** `Mall_Customers.csv` (200 rows, 5 columns)
- **Domain:** Retail / Customer Analytics

## Algorithms Used

### 1. K-Means Clustering
A centroid-based algorithm that partitions customers into `k` clusters by minimising within-cluster variance. Optimal `k` selected using the Elbow Method and Silhouette Score.
![Elbow Method](screenshots/elbow_method.png)

### 2. Agglomerative Hierarchical Clustering
A connectivity-based algorithm that builds a tree of nested clusters (visualised via a dendrogram) using Ward linkage, then cuts the tree at the chosen number of clusters.
![Dendrogram](screenshots/dendrogram.png)

### 3. DBSCAN
A density-based algorithm that groups points in dense regions and labels sparse, isolated points as noise, without requiring the number of clusters to be specified in advance.
![DBSCAN](screenshots/dbscan_clusters.png)

## Comparison
![Algorithm Comparison](screenshots/comparison_3panel.png)

## Tools Used
- Python 3.11
- pandas, numpy — data handling
- matplotlib, seaborn — visualisation
- scikit-learn — KMeans, AgglomerativeClustering, DBSCAN, metrics
- scipy — hierarchical linkage / dendrogram

## Video Walkthrough
🎥 [Video link here] — 5–10 min explanation covering scaling rationale, Elbow/Silhouette selection, dendrogram reading, DBSCAN parameter tuning, and business insights.

## Repository Structure
```
├── UL_PR1.ipynb          # Main analysis notebook
├── UL_PR1.html            # Exported HTML version
├── requirements.txt       # Python dependencies
├── README.md
└── screenshots/           # Key plots (Elbow, Dendrogram, k-distance, 3-panel comparison)
```

## How to Run
```bash
pip install -r requirements.txt
jupyter notebook UL_PR1.ipynb
```
Make sure `Mall_Customers.csv` (downloaded from the Kaggle URL above) is in the same directory.
