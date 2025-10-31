# Online Retail Customer Clustering Assignment
## Based on Online Retail Dataset Analysis (Data Loading to K-Means Clustering)

---

## Question 1: Data Loading and Exploration


The Online Retail dataset contains transactional data from a UK-based e-commerce business from 01-12-2010 to 09-12-2011. The dataset has 541,909 rows and 8 columns.

### a) Load the Online Retail dataset using Pandas and display basic information:
- Show the shape of the dataframe
- Display the first 5 rows
- Show data types and missing values for each column
- Calculate the percentage of missing values

### b) Handle missing values appropriately:
- Identify which columns have missing data
- Remove rows with missing values
- Verify the new dataframe shape
- Convert `CustomerID` to string datatype

### c) Basic exploratory analysis:
- Create a bar plot showing sales distribution by day of the week (Monday-Sunday)
- Interpret which days have the highest sales volume
- What business insight can you derive from this?

---

## Question 2: Creating RFM Attributes


Recency, Frequency, and Monetary (RFM) analysis is a technique used to segment customers. You will create three new attributes from the raw transactional data.

### a) Amount (Monetary Value):
- Create a new column `Amount` by multiplying `Quantity × UnitPrice`
- Group by `CustomerID` and sum the total amount spent
- Display the first 10 customers with their total amount

### b) Frequency:
- Count the number of transactions (InvoiceNo) per customer
- Group by `CustomerID` and count
- Display the first 10 customers with their transaction frequency

### c) Recency:
- Convert `InvoiceDate` column to proper datetime format using `pd.to_datetime()`
- Find the maximum date in the dataset (most recent transaction date)
- **Calculate Recency** as the number of days between each customer's last purchase and the maximum date
- Group by `CustomerID` and find the minimum time difference (most recent purchase)
- Extract the number of days only from the timedelta

### d) Merge the three attributes:
- Create a final RFM dataframe by merging Amount, Frequency, and Recency
- Display the merged dataframe (first 10 rows)
- Calculate summary statistics (mean, median, std, min, max) for each attribute

### e) Explain the RFM Framework:
- What does Recency measure? Why is it important?
- What does Frequency measure? Provide interpretation
- What does Monetary value measure? Provide interpretation

---

## Question 3: Data Preprocessing for Clustering


Before applying K-Means, we need to preprocess the data.

### a) Outlier Detection and Removal:
- Create box plots for Amount, Frequency, and Recency
- Identify outliers using the IQR method (Q1 - 1.5×IQR, Q3 + 1.5×IQR)
- Remove outliers for all three attributes
- Report how many rows were removed

### b) Feature Standardization:
- Why is standardization necessary for K-Means clustering?
- Use `StandardScaler` from sklearn to standardize the RFM attributes
- Fit and transform the data
- Verify that the scaled data has mean ≈ 0 and std ≈ 1

### c) Data Verification:
- Display the scaled dataframe (first 10 rows)
- Confirm the shape of the scaled data matches the cleaned RFM data

---

## Question 4: Determining Optimal Clusters using Elbow Method


### a) Elbow Method:
- Fit K-Means models for k = 2, 3, 4, 5, 6, 7, 8
- Calculate the inertia (sum of squared distances) for each k
- Plot the Elbow curve (k vs Inertia)
- Identify the "elbow point" where the inertia starts to level off
- What is the optimal number of clusters? Justify your answer.

### b) Silhouette Analysis:
- Calculate the Silhouette Score for k = 2 to 8
- Display the scores in a table format
- Interpret what each score means
- Which k has the highest silhouette score?
- Compare this result with the Elbow method finding

### c) Final Model Selection:
- Based on both Elbow method and Silhouette analysis, choose the optimal k
- Fit K-Means with the optimal k value using `max_iter=50`
- Display the cluster labels for the first 10 customers

---

## Question 5: Cluster Interpretation (Conceptual)


### a) Based on your K-Means model:
- Calculate the mean values of Amount, Frequency, and Recency for each cluster
- What customer profiles can you identify from each cluster?

### b) Customer Segmentation:
- Describe what each cluster represents in business terms
- Which cluster represents "best customers"? Why?
- Which cluster might need marketing intervention? Why?

### c) Business Recommendations:
- What actionable insights can you derive from this segmentation?
- How could the company use these clusters for targeted marketing?

---

## Deliverables

Your submission should include:

1. **Python Code** with well-commented sections for each question
2. **Visualizations:**
   - Day-of-week sales distribution bar plot
   - Box plots for outlier detection
   - Elbow curve plot (k vs Inertia)
   - Silhouette scores plot
3. **Outputs:**
   - Summary statistics for RFM attributes
   - Cluster membership assignments
   - Mean RFM values per cluster
4. **Written Explanations** for conceptual questions

---

## Hints

- Use `pd.to_datetime()` with the correct format for date conversion
- For Recency: `maxdate - customer_date` gives timedelta, then `.dt.days` extracts days
- Silhouette score ranges from -1 to 1 (higher is better)
- The Elbow method looks for a "kink" in the curve
- K-Means is sensitive to feature scaling, hence standardization is essential

---

## Grading Rubric

| Question | Component | Marks | Criteria |
|----------|-----------|-------|----------|
| 1 | Data Loading | 5 | Correct loading, shape, dtypes |
| 1 | Missing Values | 5 | Proper handling and reporting |
| 1 | Exploratory Analysis | 5 | Visualization and insights |
| 2 | Amount Calculation | 8 | Correct formula and grouping |
| 2 | Frequency Calculation | 8 | Correct transaction count |
| 2 | Recency Calculation | 9 | Correct date diff and days extraction |
| 3 | Outlier Detection | 10 | IQR method, correct removal |
| 3 | Standardization | 5 | Correct scaling, verification |
| 3 | Data Verification | 5 | Correct shape and statistics |
| 4 | Elbow Method | 10 | Plot, elbow point identification |
| 4 | Silhouette Analysis | 7 | Scores, comparison with elbow |
| 4 | Final Model | 3 | Optimal k selection and fitting |
| 5 | Cluster Analysis | 10 | Mean values, profile interpretation |
| 5 | Business Context | 5 | Segmentation description |
| 5 | Recommendations | 5 | Actionable insights |
| **Total** | | **100** | |

---

## Additional Learning Outcomes

After completing this assignment, you should be able to:

- ✅ Load and explore transactional data using Pandas
- ✅ Create RFM features for customer segmentation
- ✅ Detect and handle outliers using statistical methods
- ✅ Standardize features for machine learning algorithms
- ✅ Determine optimal number of clusters using multiple methods
- ✅ Apply K-Means clustering to real-world data
- ✅ Interpret clustering results in business context
- ✅ Provide data-driven recommendations for marketing

---

## References

- Pandas Documentation: https://pandas.pydata.org/docs/
- Scikit-learn K-Means: https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html
- RFM Analysis: Customer Segmentation using RFM Analysis
- Silhouette Score: https://scikit-learn.org/stable/modules/generated/sklearn.metrics.silhouette_score.html

---

**Assignment Duration:** 2-3 hours  
**Difficulty Level:** Intermediate  
**Recommended for:** B.Sc. 2nd Semester onwards  
**Prerequisites:** Python basics, Pandas, NumPy, Scikit-learn fundamentals
