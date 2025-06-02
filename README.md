# Sales-Performance-Analysis-and-Insights-
This project analyzes retail sales data from the Superstore dataset to extract key business insights that can help improve sales, profitability, and regional performance.
Project Overview

Project Title:
Sales Performance Analysis: Retail Sales Dataset (Superstore)

Project Type:
Business Analytics Portfolio

Main Tools Used:

Python (Pandas, Matplotlib, Seaborn)

Jupyter Notebook

Excel / CSV 

Tableau or Power BI 




---

Dataset:

We will use the Superstore Sales Dataset, widely used for business analytics projects.

You can download it from:
Kaggle Superstore Dataset: https://www.kaggle.com/datasets/vivek468/superstore-dataset-final



---

Business Questions to Answer:

Which product categories bring in the highest revenue and profit?

Which regions are performing the best?

Are there specific states that are underperforming?

What is the relationship between discount and profit?

Can we identify sales trends over time?



---

README.md:

# Sales Performance Analysis

## Overview
This project analyzes sales data for a fictional Superstore company to derive business insights and help improve profitability.

## Dataset
- Source: Kaggle Superstore Dataset
- Contains information on orders, sales, profits, regions, categories, shipping mode, and customer segments.

## Tools Used
- Python: Pandas, NumPy, Matplotlib, Seaborn
- Tableau (optional): Advanced dashboards
- Jupyter Notebook

## Key Analysis Areas
- Sales and Profit Trends
- Regional Performance
- Product Category Analysis
- Discount Impact on Profit

## Business Insights
- Technology category yields the highest profit margins.
- Western region contributes the highest revenue.
- High discounts often correlate with reduced profit.
- Some states are running at negative profits — action needed.

## Folder Structure
- `data/`: Raw dataset.
- `notebooks/`: Jupyter notebook with full analysis.
- `visuals/`: Plots and charts used for storytelling.
- `dashboard/`: Tableau or Power BI dashboards.
- `requirements.txt`: Python libraries required.

## Author
Aman Bajpai — MSc Business Analytics


---

The Analysis:

# Import libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load data
data = pd.read_csv('data/superstore_sales.csv')

# Quick view
print(data.head())
print(data.info())
print(data.describe())

# Handle missing values
data.dropna(inplace=True)

# Sales by Category
category_sales = data.groupby('Category')['Sales'].sum().sort_values(ascending=False)
category_sales.plot(kind='bar', figsize=(8,6))
plt.title("Sales by Product Category")
plt.ylabel("Total Sales")
plt.xticks(rotation=45)
plt.tight_layout()
plt.savefig('visuals/sales_by_category.png')
plt.show()

# Profit by Region
region_profit = data.groupby('Region')['Profit'].sum().sort_values(ascending=False)
region_profit.plot(kind='bar', figsize=(8,6), color='orange')
plt.title("Profit by Region")
plt.ylabel("Total Profit")
plt.xticks(rotation=45)
plt.tight_layout()
plt.savefig('visuals/regional_sales.png')
plt.show()

# Discount vs Profit
plt.figure(figsize=(8,6))
sns.scatterplot(x='Discount', y='Profit', data=data)
plt.title('Discount vs Profit')
plt.savefig('visuals/profit_vs_discount.png')
plt.show()

# Time Series Sales Analysis
data['Order Date'] = pd.to_datetime(data['Order Date'])
monthly_sales = data.groupby(pd.Grouper(key='Order Date', freq='M'))['Sales'].sum()

plt.figure(figsize=(10,6))
monthly_sales.plot()
plt.title("Monthly Sales Over Time")
plt.ylabel("Sales")
plt.xlabel("Order Date")
plt.savefig('visuals/monthly_sales.png')
plt.show()

# Top 10 States by Loss
state_profit = data.groupby('State')['Profit'].sum().sort_values()
print(state_profit.head(10))

 Key Business Insights:

Western region contributes highest profit.

Technology segment is most profitable.

Excessive discounts reduce profitability.

Texas, Ohio and Pennsylvania show negative profits and need business intervention.

Monthly sales show seasonal patterns (Q4 being highest sales volume).
