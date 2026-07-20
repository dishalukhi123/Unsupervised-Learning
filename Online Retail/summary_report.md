# Summary Report: Customer Segmentation via Unsupervised Learning

## Business Problem & Dataset
A large e-commerce company (analogous to Flipkart/Meesho) was sending identical
promotional emails to all customers, hurting conversion rates and increasing spam
complaints. The goal was to segment customers into meaningful groups so marketing
could target each group with relevant offers. We used the Online Retail II dataset
(UCI ML Repository), a real transactional dataset from a UK-based online retailer
covering ~1 million transactions between 2009 and 2011. After filtering to UK
customers with valid CustomerIDs and removing returns/invalid rows, [N] unique
customers remained for analysis.

## RFM Feature Engineering & Preprocessing
For each customer we engineered three features: **Recency** (days since last
purchase, relative to 2011-12-31), **Frequency** (number of unique invoices), and
**Monetary** (total spend). Raw RFM values were heavily right-skewed and contained
extreme outliers (a small number of wholesale-like buyers with very high order counts
and spend), so we winsorized values above Q3 + 3×IQR rather than dropping rows, to
retain all customers while limiting the influence of extreme points. Frequency and
Monetary were then log1p-transformed to reduce skew, and all three features were
standardized with StandardScaler, since K-Means, Agglomerative Clustering, and DBSCAN
are all distance-based and sensitive to feature scale.

## Algorithm Performance
We compared K-Means (tuned via elbow method and silhouette score), Agglomerative
Clustering (comparing ward, complete, and average linkage), and DBSCAN (tuned via
k-NN distance plot and a grid search over eps/min_samples), evaluated with Silhouette
Score, Davies-Bouldin Index, and Calinski-Harabasz Index. [Fill in: which algorithm
scored best and by how much]. This [did/did not] match business intuition, since
[K-Means/Agglomerative] produced compact, evenly-sized groups that mapped cleanly onto
recognizable customer behaviors, while DBSCAN's flexibility in shape came at the cost
of classifying [X]% of customers as unclustered noise.

## Customer Segments
1. **Champions** — Recent purchasers who buy often and spend the most; the top
   revenue-driving segment.
2. **Loyal Customers** — Consistent repeat buyers with moderate-to-high spend.
3. **At-Risk Customers** — Previously active but recency has grown; spend is
   moderate but declining engagement signals churn risk.
4. **Hibernating** — Long time since last purchase, low frequency and spend;
   effectively dormant customers.
5. **New Customers** — Very recent first purchase, low frequency so far; still
   forming a relationship with the brand.

## Next Steps
Beyond RFM, incorporating product category preferences, browsing and cart-abandonment
behavior, customer service/return history, and channel (app vs. web) data would enable
richer, behavior-based segmentation. A natural next iteration is semi-supervised
refinement — using these unsupervised clusters as weak labels to train a supervised
classifier — and deploying the saved pipeline (`rfm_scaler.pkl` +
`customer_segmentation_model.pkl`) behind a real-time scoring API so new customers can
be assigned a segment and targeted offer immediately after their first purchase.

---
*Word count target: ~400–500 words. Fill in the bracketed [ ] placeholders with your
actual numbers once you've run the notebook on the full dataset.*
