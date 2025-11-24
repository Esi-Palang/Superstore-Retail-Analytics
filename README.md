# Superstore-Retail-Analytics
Customer Segmentation & Churn Risk (Python  K-Means + Tableau)

This project analyses the classic **Superstore** retail dataset using Python, with a focus on:

- Sales & profit performance across **categories, sub-categories, regions, and time**
- **Seasonality** and monthly sales trends
- **Customer-level features** (Recency, Frequency, Monetary, AvgDiscount)
- **Customer segmentation** using K-Means clustering
- Identifying customers **at risk of churn** using inactivity (Recency)
- Preparing an **exported dataset with segment labels** for use in Tableau / BI tools

The workflow follows the **CRISP-DM** methodology:
1. Business Understanding  
2. Data Understanding  
3. Data Preparation  
4. Modelling (K-Means)  
5. Evaluation & Interpretation  
6. Deployment (segment export for dashboards)

## Files in this project

- `Superstore_Retail_Analytics_Enhanced.ipynb` – main analysis notebook (EDA, features, clustering, churn view)
- `Sample - Superstore.csv` – Superstore dataset used in this project
- `Superstore_Final_with_Segments.csv` – enriched dataset with customer segment labels (for Tableau / BI)
- `Superstore_CRISPDM_Report_Ehsan_Keikhavani.docx` – detailed CRISP-DM report with charts and insights *(local)*
- `Superstore_Retail_Analytics_Summary_Ehsan_Keikhavani.pdf` – 1–2 page summary report *(local)*

> File names can be adjusted to match your local setup. The notebook assumes the CSV is in the same folder.

## Main steps in the notebook

### 1. Data Understanding & EDA

- Inspect structure, data types, and basic statistics.
- Explore core numeric relationships (Sales, Profit, Quantity, Discount).
- Business-focused visualisations:
  - Sales & Profit by Category
  - Sales by Region (if added)
  - Top 10 Most Profitable Sub-Categories
  - Top & Bottom performing cities
  - Monthly Sales Trend
  - Seasonal Sales by Month
  - Product Demand vs Profit

### 2. Customer Behaviour Features (RFM-style)

- Convert `Order Date` to datetime and define a snapshot date.
- Aggregate data to customer level to compute:
  - `Recency` – days since last purchase
  - `Frequency` – number of unique orders
  - `Monetary` – total sales per customer
  - `AvgDiscount` – average discount level per customer
- Optionally, visualise distributions and correlations of these features.

### 3. Churn Risk (Inactivity-Based)

- Use Recency to identify customers who have not purchased for a long time.
- Rank and visualise the most inactive customers as a simple churn-risk indicator.

### 4. K-Means Customer Segmentation

- Standardise Recency, Frequency, Monetary, and AvgDiscount using `StandardScaler`.
- Evaluate different values of `k` using:
  - Elbow Method (inertia)
  - Silhouette Score
- Fit the final K-Means model and assign cluster labels to each customer.
- Visualise segments using scatter plots such as:
  - Frequency vs Monetary coloured by cluster
  - Recency vs Monetary coloured by cluster

### 5. Segment Interpretation & Export

- Build a cluster summary table with average Recency, Frequency, Monetary, and AvgDiscount.
- Interpret each segment (e.g. loyal high-value customers, at-risk low-value customers, discount-sensitive buyers).
- Merge segment labels back to the original transactions and export to `Superstore_Final_with_Segments.csv`.

## How to run

1. Place `Superstore.csv` in the same folder as the notebook.
2. Install dependencies:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn plotly
