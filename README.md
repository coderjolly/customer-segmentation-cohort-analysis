# Credit Card Customer Segmentation

## Context
A financial institution (hereafter referred to as "FI Bank") aims to prioritize its credit card customer base in the upcoming financial year. The marketing research team ("MRT") at FI Bank has identified opportunities for enhancing market penetration. In light of this finding, the MRT proposes personalized campaigns to attract new customers and upsell to existing ones. Additionally, MRT indicates that customers perceive FI Bank's support services poorly. Consequently, the Operations team ("OT") intends to enhance the service delivery model to expedite resolution of customer queries. Recognizing these challenges, the heads of MRT and OT are requesting assistance.

## Problems/Objectives
Credit Card services present these problems:

- Market Penetration has to increase.
- Current FI Bank's Credit Card Services should increase and/or improve.
- FI Bank's Credit Card Customer Support is perceived as poor.
- FI Bank's Credit Card Customers Queries should be resolved faster.

## Process
Identify and classify the different segments in the existing customer base, based on their spending patterns, past interaction with the bank, and any other important data available. Specify the characteristics of each segment and notice the weak or strong patterns of each segment.
Provide recommendations to FI Bank for each segment based on items 1 and 2 above. These recommendations should include how to expand the market penetration (new and current customers) and how to improve the customer services. Possibly recommend what type of service feature is important for each segment.

**Data Dictionary**

The data provided is of various FI Bank's customers and their financial attributes like credit limit, the total number of credit cards the customer has, and different channels through which customers have contacted the bank for any queries (including visiting the bank, online and through a call center).

- Sl_No: Primary key of the records
- Customer Key: Customer identification number
- Average Credit Limit: Average credit limit of each customer for all credit cards
- Total credit cards: Total number of credit cards possessed by the customer
- Total visits bank: Total number of visits that the customer made (yearly) personally to the bank
- Total visits online: Total number of visits or online logins made by the customer (yearly)
- Total calls made: Total number of calls made by the customer to the bank or its customer service department (yearly)

## **Some Questions**

Q1. How can the customers be grouped/segmented (classified)?

Q2. What are the commonalities of each group/segment? ie:
- Total/Particular Interaction w/ FI Bank
- Total Credit Cards
- Average Credit Limit
  
Q3. What is the group/segment that has the most/least interactions/particular type of interaction with FI Bank?

Q4. Is there a relationship between Average Credit Limit/Total Credit Cards and customer satisfaction (assuming that the number of interactions is an indication of unsolved issues)?

Q5. What is the relationship between Average Credit Limit/Total Credit Cards to interactions/type of interactions with FI Bank (this question is partially addressed by Q2)?

Q6. What recommendations can be made for each group/segment to improve customer satisfaction (assuming that the number of interactions is an indication of unsolved issues)?

Q7. What recommendations can be made based on segment characteristics to increase market penetration/expand services to current customers?

With this set of questions, we address the problems introduced earlier and make recommendations to FI Bank.

## Technique
This is an unsupervised classification problem. 
- Perform the data preprocessing, EDA analysis, and feature engineering.
- Visualize features and observe relationships performing a uni and bivariate analysis.
- Classification using K-means Clustering
  Attempt classification of customers using K-means clustering and stimate the better number of clusters using the elbow method and observe silhouettes. Visualize the clusters.
- Classification using Hierarchical Clustering
  Attempt classification of customers using hierarchical clustering. Explore clustering with different linkage methods (i.e. single, complete, etc) and distances (i.e. euclidean, manhattan, etc) reviewing the cophenetic correlation and finding the ideal number of clusters. Visualize the clusters.
- Compare K-means vs. Hierarchical clustering results.
- Provide Insights and Recommendations.

### Data Preprocessing

The dataset is first cleaned and prepared:

- Unique identifiers like `Customer Key` are removed
- Missing values and duplicates are checked
- `StandardScaler` is used to normalize the numerical features

### Exploratory Data Analysis (EDA)

EDA is performed on core behavioral metrics such as:

- `Avg_Credit_Limit`
- `Total_Credit_Cards`
- `Total_visits_bank`
- `Total_visits_online`
- `Total_calls_made`

Each feature is explored using histograms and boxplots.

![eda-distribution](ss/eda-hist-box.png)

### Feature Scaling

All numerical features are standardized using Z-score normalization to ensure fair contribution during distance-based clustering:

- Mean = 0
- Standard Deviation = 1

This ensures variables with larger scales (like credit limit) do not dominate clustering.

### Clustering & Evaluation

#### K-Means Clustering
- The **Elbow Method** is used to determine the optimal number of clusters.
- Cluster cohesion is validated using the **Silhouette Score**.

![elbow-method](ss/elbow-method.png)
*Inertia plot using Elbow Method*

#### Hierarchical Clustering
- Dendrograms show how observations merge into clusters.
- Distance threshold lines help identify natural divisions.

![dendrogram](ss/hierarchical-dendrogram.png)

### PCA & Cluster Visualization

Dimensionality reduction via PCA is applied to reduce the features to two components for easy visualization of clusters.

![pca-kmeans](ss/pca-kmeans.png)
*Clusters visualized in 2D PCA space (KMeans)*

### Cluster Profiling

After clustering, each group is profiled to understand customer characteristics. For example:

- **Cluster 0**: High credit limit, low service usage — ideal premium customers
- **Cluster 1**: Moderate limits, high digital activity — tech-savvy base
- **Cluster 2**: Low limits, high support calls — operationally expensive segment

These insights help the bank optimize:

- Marketing strategy (e.g., target upselling campaigns)
- Support services (e.g., reduce call load through automation)
- Digital engagement programs

---

## Conclusion

By segmenting customers using clustering and behavioral metrics, FI Bank can:

- Personalize product offerings
- Enhance operational efficiency
- Increase customer satisfaction

Clustering uncovers hidden patterns that aren’t obvious from raw metrics alone, enabling data-driven strategy decisions.



