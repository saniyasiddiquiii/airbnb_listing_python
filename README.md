# airbnb_listing_python

# Airbnb New York 2024 — Exploratory Data Analysis (EDA) & Business Insights

## Project Overview

This project analyzes **20,770 Airbnb listings in New York City (2024)** using **Python, Pandas, NumPy, Matplotlib, and Seaborn**. The goal is to perform **Exploratory Data Analysis (EDA)**, clean the dataset, identify pricing patterns, evaluate neighborhood performance, and generate **business insights** that could help Airbnb improve pricing, inventory planning, and host performance analysis.

The project follows a real-world analytics workflow:

1. Data Loading
2. Data Exploration
3. Data Cleaning
4. Exploratory Data Analysis (EDA)
5. Data Visualization
6. Business Insights & Recommendations

---

# Business Problem

Airbnb operates thousands of listings across multiple neighborhoods in New York City. Decision-makers need to understand:

* Which neighborhoods generate higher-value listings?
* Which room types dominate the market?
* Are there pricing outliers affecting averages?
* Which hosts manage multiple listings?
* How available are listings throughout the year?
* What factors appear related to reviews and ratings?

This analysis aims to answer these questions and support **pricing strategy, inventory optimization, and neighborhood-level business planning**.

---

# Dataset Information

* **Dataset:** New York Airbnb Listings 2024
* **Rows:** 20,770
* **Columns:** 22
* **File Format:** CSV

### Key Features

* `price`
* `room_type`
* `neighbourhood_group`
* `neighbourhood`
* `availability_365`
* `number_of_reviews`
* `reviews_per_month`
* `rating`
* `bedrooms`
* `beds`
* `host_id`
* `host_name`

---

# Tools & Technologies

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Jupyter Notebook**

---

# Project Workflow

## 1. Importing Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

## 2. Loading the Dataset

```python
data = pd.read_csv('new_york_listings_2024.csv')
```

## 3. Initial Exploration

* `data.head()`
* `data.tail()`
* `data.shape`
* `data.info()`
* `data.describe()`

These steps help understand the structure of the dataset, data types, and summary statistics.

---

# Data Cleaning

The dataset was cleaned before analysis to improve data quality.

### Missing Values

```python
data.isnull().sum()
data.dropna(inplace=True)
```

### Duplicate Records

```python
data.duplicated().sum()
data.drop_duplicates(inplace=True)
```

### Data Type Conversion

```python
data['id'] = data['id'].astype(object)
data['host_id'] = data['host_id'].astype(object)
```

Identifier columns were converted from numeric to categorical (`object`) because they represent unique entities rather than values used for mathematical calculations.

---

# Exploratory Data Analysis (EDA)

The analysis focuses on understanding the distribution, relationships, and behavior of Airbnb listings across New York.

## Univariate Analysis

### Price Distribution

```python
sns.histplot(data['price'])
```

Objective:

* Identify pricing concentration
* Detect outliers
* Understand market spread

### Room Type Distribution

```python
data['room_type'].value_counts()
```

Objective:

* Determine the most common listing type
* Compare private rooms vs entire homes

### Neighborhood Distribution

```python
data['neighbourhood_group'].value_counts()
```

Objective:

* Measure inventory concentration across boroughs

---

# Business Questions Answered

## 1. What is the average Airbnb listing price in New York?

```python
data['price'].mean()
```

**Business Value:** Helps establish a baseline market price.

---

## 2. Which neighborhood group has the highest average listing price?

```python
data.groupby('neighbourhood_group')['price'].mean()
```

**Business Value:** Supports neighborhood-level pricing strategy.

---

## 3. Which neighborhood has the highest number of listings?

```python
data['neighbourhood'].value_counts().head(10)
```

**Business Value:** Identifies high-supply markets.

---

## 4. Which room type is most common?

```python
data['room_type'].value_counts()
```

**Business Value:** Helps understand customer demand and inventory mix.

---

## 5. Which room type generates the highest average price?

```python
data.groupby('room_type')['price'].mean()
```

**Business Value:** Supports product positioning and revenue optimization.

---

## 6. Which hosts manage the largest number of listings?

```python
data.groupby('host_name').size().sort_values(ascending=False).head(10)
```

**Business Value:** Identifies commercial or professional hosts.

---

## 7. How does listing availability vary across neighborhoods?

```python
data.groupby('neighbourhood_group')['availability_365'].mean()
```

**Business Value:** Indicates inventory utilization and occupancy potential.

---

## 8. What is the relationship between price and reviews?

```python
sns.scatterplot(x='price', y='number_of_reviews', data=data)
```

**Business Value:** Helps evaluate whether expensive listings receive fewer or more reviews.

---

## 9. Are there extreme pricing outliers?

```python
sns.boxplot(x=data['price'])
```

**Business Value:** Detects unrealistic prices that may distort averages.

---

## 10. Which neighborhoods combine high ratings with strong listing availability?

```python
data.groupby('neighbourhood_group')[['rating', 'availability_365']].mean()
```

**Business Value:** Identifies attractive markets for expansion or investment.

---

# Visualizations

The project includes multiple visualizations such as:

* Histogram of listing prices
* Box plot of prices
* Bar chart of room types
* Bar chart of neighborhood groups
* Scatter plot of price vs reviews
* Distribution plots for availability and ratings

These charts help communicate insights to business stakeholders effectively.

---

# Python Concepts Demonstrated

This project demonstrates practical Python skills commonly used in data analytics.

### DataFrames

```python
data.head()
```

### Indexing

```python
data['price']
```

### Aggregation

```python
data['price'].mean()
data['price'].max()
```

### Grouping

```python
data.groupby('room_type')['price'].mean()
```

### Missing Value Handling

```python
data.dropna(inplace=True)
```

### Duplicate Removal

```python
data.drop_duplicates(inplace=True)
```

### Type Casting

```python
data['host_id'].astype(object)
```

### Visualization

```python
sns.histplot()
sns.boxplot()
sns.scatterplot()
```

---

# Key Insights

* Listing prices show a **right-skewed distribution**, indicating a small number of very expensive properties.
* **Entire home/apartment** listings dominate the market.
* **Manhattan** tends to have higher average prices than other boroughs.
* Several hosts manage **multiple listings**, suggesting commercial host activity.
* Availability varies significantly across neighborhoods, indicating different occupancy patterns.
* Price outliers can heavily influence average calculations and should be considered when building pricing models.

---

# Business Recommendations

* Implement **neighborhood-specific pricing strategies** rather than city-wide pricing.
* Monitor **high-volume hosts** separately from individual hosts.
* Investigate **extreme price outliers** for data quality or luxury segmentation.
* Promote **highly rated neighborhoods** with strong availability to improve booking conversion.
* Use review and availability patterns to estimate **future occupancy trends**.

---

# Project Structure

```
Airbnb-NewYork-EDA/
│
├── airbnblistingprojectproject.ipynb
├── new_york_listings_2024.csv
├── README.md
└── visualizations/
```

---

# Skills Demonstrated

* Exploratory Data Analysis (EDA)
* Data Cleaning
* Business Analysis
* Data Visualization
* Statistical Summary
* Python Programming
* Pandas Operations
* GroupBy Analysis
* Analytical Thinking
* Business Insight Generation

---

# Conclusion

This project demonstrates how Python can be used to transform raw Airbnb listing data into actionable business insights. The analysis highlights pricing behavior, neighborhood performance, room-type distribution, and host activity, making it a strong portfolio project for **Business Analyst, Data Analyst, and Product Analyst roles**.
