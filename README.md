# TravelTide-Project
An insightful travel analytics project focused on customer segmentation and loyalty programs, utilizing data-driven methods to explore user behavior, travel preferences, and spending patterns.

## Overview
In today's competitive travel industry, customer loyalty is critical for success. The Traveltide project focuses on developing a robust and tailored loyalty program for Traveltide customers by understanding their travel behaviors, preferences, and needs. By utilizing data-driven insights and machine learning techniques, we segmented customers into distinct groups and proposed personalized perks aimed at enhancing customer satisfaction and loyalty.

## Project Goals
- Segment the customer base into meaningful groups based on travel behavior, spending, and demographics.
- Offer strategic recommendations for implementing an effective, data-driven loyalty program at Traveltide.

## Workflow Overview
### 1. Connecting to the Database
The data was retrieved from a PostgreSQL database using SQLAlchemy to establish a connection and perform SQL queries:
```python
import sqlalchemy as sa
import pandas as pd

#Create a connection to the PostgreSQL database

engine = sa.create_engine("postgresql://username:password@host/database")
connection = engine.connect()

#Load the data into pandas DataFrames

users = pd.read_sql_table('users', connection)
hotels = pd.read_sql_table('hotels', connection)
flights = pd.read_sql_table('flights', connection)
sessions = pd.read_sql_table('sessions', connection)
```

### 2. Data Preparation and Cleaning
This step involved cleaning the raw data, addressing missing values, and normalizing the numerical variables for the analysis:

```python
from sklearn.preprocessing import StandardScaler

#Scaling the relevant numerical features

scaler = StandardScaler()
scaled_data = scaler.fit_transform(data[['numeric_feature1', 'numeric_feature2', 'numeric_feature3']])``´

### 3. Feature Engineering and Dimensionality Reduction
To reduce the complexity of the dataset, Principal Component Analysis (PCA) was applied to transform the data into a more manageable number of dimensions while preserving the essential information:

```python
from sklearn.decomposition import PCA

#Dimensionality reduction using PCA

pca = PCA(n_components=2)
pca_transformed_data = pca.fit_transform(scaled_data)```

### 4. User Segmentation
K-Means clustering was employed to group customers based on their travel patterns and behaviors, allowing for more personalized loyalty program design:

```python
from sklearn.cluster import KMeans

#Applying K-Means to segment users into distinct clusters

kmeans = KMeans(n_clusters=6, random_state=42)
user_segments = kmeans.fit_predict(pca_transformed_data)```

### 5. Cluster Validation and Model Evaluation
To assess the quality of the clusters, the Silhouette Score was computed, offering insight into how well the data points fit within their assigned clusters:

```python
from sklearn.metrics import silhouette_score

#Evaluate clustering performance using the Silhouette Score

silhouette_avg = silhouette_score(pca_transformed_data, user_segments)
print(f'Silhouette Score: {silhouette_avg}')```

## Results

### Customer Segmentation & Perks
We identified six distinct customer segments, each with unique characteristics. Based on these insights, we proposed targeted perks for each group:

#### 1. Frequent Travelers (Group 0 & 2)

-Key Insight: High travel frequency, moderate hotel spend.
-Proposed Perk: 10% Flight Discount to encourage continued engagement.

#### 2. Senior Travelers (Group 1)

-Key Insight: Cost-effective, leisure-focused travel, lower flight frequency.
-Proposed Perk: 10% Discount on Leisure Activities to enhance their overall travel experience.

#### 3. Family Travelers (Group 3)

-Key Insight: Longer trips, higher luggage needs due to family travel.
-Proposed Perk: Free Checked Bags to alleviate the cost burden for families.

#### 4. Business Travelers (Group 4)

-Key Insight: High flight frequency, significant hotel spend, time-sensitive travel.
-Proposed Perk: Priority Check-in & Boarding to save time and enhance convenience.

#### 5. Young Adventurers (Group 5)

- Key Insight: Younger demographic, budget-conscious, shorter trips.
- Proposed Perk: 5% Discount on All Future Bookings to nurture loyalty and encourage frequent travel.

#### 6. Luxury Leisure Travelers (Group 6)

- Key Insight: High hotel spend, longer trip durations, luxury-focused travel.
- Proposed Perk: Free Hotel Night with Flight to reward high spending and encourage more bookings.

## Tools & Libraries Used
- Python for data manipulation and analysis
- Pandas for data processing
- NumPy for numerical computations
- Matplotlib & Seaborn for data visualization
- Scikit-Learn for machine learning (PCA, KMeans)
- SQLAlchemy for database interactions

## Conclusion and Recommendations
To further enhance Traveltide's loyalty program, we recommend implementing A/B testing to evaluate perk effectiveness, dynamically adjusting rewards based on evolving customer preferences, and introducing cross-segment offers to encourage users to explore different travel options. Personalized communication and real-time feedback will allow for more targeted engagement, while partnerships with external companies can expand the range of perks offered. By leveraging these strategies, Traveltide can ensure its loyalty program remains relevant and appealing, ultimately driving increased customer satisfaction, retention, and market competitiveness.








