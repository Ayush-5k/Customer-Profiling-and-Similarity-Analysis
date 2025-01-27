# Customer Segmentation and Lookalike Model

This repository contains the implementation of a **Lookalike Model** for customer segmentation and recommendation. The task involves building a model to recommend the top 3 similar customers based on their transaction history and profiles. The dataset includes customer information, product details, and transaction history.

## Objective

The objective of this assignment is to:
- Build a **Lookalike Model** that takes a user's information as input and recommends 3 similar customers based on their profile and transaction history.
- Evaluate the quality of the recommendations using clustering and similarity measures.
- Form a **Lookalike.csv** which contains a map from `CustomerID` to a list of similar customers and their respective similarity scores.

## Overview

The approach followed includes:
1. **Data Preprocessing**:
   - Merged customer, product, and transaction data.
   - Performed aggregation to create customer profiles, including total spending, number of transactions, and most frequent product category.

2. **Clustering**:
   - Applied clustering algorithms to segment customers based on their transaction behavior.
   - Used K-Means clustering for segmenting the customers into meaningful groups.

3. **Lookalike Model**:
   - Built a model that computes similarity between customer profiles using **cosine similarity**.
   - For each customer, the top 3 similar customers are recommended based on the cosine similarity of their profile features.

4. **Evaluation**:
   - Evaluated the quality of the clustering using the **Davies-Bouldin Index (DB Index)** and **Silhouette Score**.
   - Generated a **Lookalike.csv** containing the top 3 lookalikes for each customer.

---

## Steps Involved

### 1. Data Preprocessing

- **Loading Data**:
  - Loaded three CSV files: `Customers.csv`, `Products.csv`, and `Transactions.csv`.
  
- **Merging Data**:
  - Merged the data on `CustomerID` and `ProductID` to create a comprehensive dataset for each transaction.

- **Aggregating Customer Profiles**:
  - Aggregated data to calculate:
    - **Total Spending** (`TotalValue`): The total amount spent by each customer.
    - **Transaction Count** (`TransactionID`): The number of transactions made by each customer.
    - **Average Transaction Price** (`TransactionPrice`): The average price of each transaction.
    - **Most Frequent Category**: The most frequent product category purchased by each customer.
    - **Most Recent Transaction Date** (`TransactionDate`): The latest transaction date.

- **Feature Engineering**:
  - One-hot encoded categorical features such as **Region** and **Category**.
  - Standardized numerical features like **Total Spending**, **Transaction Count**, and **Average Transaction Price**.

### 2. Clustering

- **K-Means Clustering**:
  - Applied **K-Means** clustering algorithm to segment customers into meaningful groups.
  - Evaluated the number of clusters formed based on business logic and data characteristics.
  - Calculated clustering metrics such as **Inertia** and **Silhouette Score**.

- **DB Index Calculation**:
  - Calculated the **Davies-Bouldin Index** (DB Index) to assess the quality of the clustering results.

### 3. Lookalike Model

- **Cosine Similarity**:
  - Used **Cosine Similarity** to compute the similarity between customer profiles.
  - For each customer, the top 3 similar customers were identified based on their transaction history and profile features.

- **Generating Lookalike.csv**:
  - Created a `Lookalike.csv` that contains:
    - `CustomerID`: The ID of the customer.
    - `Lookalikes`: A list of the top 3 similar customers and their respective similarity scores.

### 4. Evaluation

- **Cluster Quality Evaluation**:
  - **Silhouette Score**: Measures how well-separated the clusters are.
  - **Davies-Bouldin Index**: Measures the clustering quality with a lower value indicating better clustering.

---

## Files

1. **Customers.csv**: Contains customer information such as `CustomerID`, `Region`, `CustomerName`, etc.
2. **Products.csv**: Contains product details such as `ProductID`, `Category`, and `Price`.
3. **Transactions.csv**: Contains transaction details including `CustomerID`, `ProductID`, `TransactionID`, and `TransactionDate`.
4. **Lookalike.csv**: The final output file containing customer IDs and their top 3 lookalikes with similarity scores.
5. **Clustering Report**: A report detailing the number of clusters, DB Index value, silhouette score, and other relevant metrics.

---

## Results

- **Number of Clusters**: 5 (chosen after evaluating the dataset).
- **Davies-Bouldin Index**: Calculated to assess clustering quality.
- **Silhouette Score**: Measures cluster separation quality.
- **Top 3 Lookalikes**: For each customer, the top 3 similar customers based on profile similarity were recommended.

---

## Example Lookalike.csv

| CustomerID | Lookalikes                                           |
|------------|------------------------------------------------------|
| C0001      | [("C0005", 0.92), ("C0010", 0.89), ("C0012", 0.85)] |
| C0002      | [("C0007", 0.88), ("C0015", 0.83), ("C0020", 0.81)] |
| C0003      | [("C0008", 0.90), ("C0014", 0.87), ("C0018", 0.85)] |

---

## Instructions to Run

1. Clone the repository to your local machine:

   ```bash
   git clone https://github.com/Ayush-5k/Customer-Profiling-and-Similarity-Analysis
