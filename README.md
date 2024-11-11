# LITA-CAPSTONE-PROJECT-2

## Project Title 2: Customer Segmentation for a Subscription Service

### Project Summary
---
This project involves analyzing customer data for a subscription service to uncover customer behavior patterns, track subscription preferences, and identify key trends in cancellations and renewals.
This project involves:

- Data cleaning: Removing duplicates and data transformation
- Data exploration and analysis using Excel and pivot tables.
- Data querying using SQL (Structured Query Language).
- Visualization and dashboard creation in Power BI.

### Project Objectives
1. Segment customers by subscription type, region, and activity.
2. Analyze trends in cancellations and renewal rates.
3. Create a Power BI dashboard for interactive exploration of customer segments and trends.
4. Provide actionable insights for stakeholders.

### Tools Used
- **Microsoft Excel**: [Download Here](https://www.microsoft.com)
  1. Initial data exploration
  2. Pivot Tables
  3. Basic metrics calculations

  - **SQL**: Extracting deeper insights and answering key business questions [Download Here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- **PowerBI**: Building an interactive dashboard to visualize insights [Download Here](https://www.microsoft.com/en-us/power-platform/products/power-bi/downloads)
- **GitHub**: for Portfolio Building [Download Here](https://github.com)

### Data Collected
The dataset includes the following key columns;
- **CustomerID**: Unique identifier for each order.
- **CustomerName**: Name of the customer.
- **Region**: Geographic region of the customer.
- **SubscriptionType**: Type of subscription (e.g., Basic, Premium, Standard).
- **SubscriptionStart and SubscriptionEnd**: Start and end dates of the subscription.
- **Canceled**: Indicates whether the subscription was canceled.
- **Revenue**: Revenue generated from each customer.
- **Subscription Duration and other variations in duration** (e.g., days, months, years).

### Project Workflow
1. ## Excel Analysis
- **Subscription Patterns**: Using pivot tables to reveal trends in subscription types and cancellation behaviors.
- Calculated average sales per product and total revenue by region.
- **Average Subscription Duration**: Calculated to understand the lifespan of typical subscriptions.
- Identify the most popular subscription types.
- **Reports**: Additional insights and trends based on subscription type, duration, and region.

![Pivot Table](https://github.com/user-attachments/assets/4e20d466-b149-4ff3-b14e-e537f5575213)

![Pivot Table 1](https://github.com/user-attachments/assets/29cda0fc-65d2-403d-9924-684888e8b962)

![Pivot Table 2](https://github.com/user-attachments/assets/a024f524-1845-4017-a4e3-02a0ef32be90)

![Pivot Table 3](https://github.com/user-attachments/assets/845cc914-382e-4a8e-9068-5dc71b54ab7b)

![Pivot Table 4](https://github.com/user-attachments/assets/25c3d831-5448-4f02-925a-f787e3fb2289)

![Pivot Table 5](https://github.com/user-attachments/assets/8ff2e207-e631-4078-bf86-e990583fa1f1)


## 2. SQL Analysis
Using SQL, I extracted insights such as:
- **Total number of customers from each region.**

```SQL
SELECT Region, COUNT(CustomerID) AS Total_No_of_Customers
FROM [dbo].[Customer Data]
GROUP BY Region
```

![SQL CD](https://github.com/user-attachments/assets/30cd11d5-ec5d-4717-aa1d-aeb920b9e0df)

- **Find the most popular subscription type by the number of customers.**

```SQL
SELECT SubscriptionType,COUNT(CustomerID)AS NO_Of_Customers
FROM [dbo].[Customer Data]
GROUP BY SubscriptionType
```

![SQL CD 1](https://github.com/user-attachments/assets/58602cfe-b401-4a98-a584-eae144a6a995)

- **Find customers who canceled their subscription within 6 months**

```SQL
SELECT CustomerName,Canceled,SubscriptionStart
FROM [dbo].[Customer Data]
WHERE Canceled =0 AND MONTH(SubscriptionStart) <= 6
```

![SQL CD 2](https://github.com/user-attachments/assets/532a9aef-4b5d-4e2c-9b4a-c9dd55529338)


- **Calculate the average subscription duration for all customers**

```SQL
SELECT Count(CustomerID) As All_Customers,AVG(DATEDIFF(DAY,SubscriptionStart,SubscriptionEnd)) AS Average_Subscription_Duration
FROM [dbo].[Customer Data]
WHERE SubscriptionEnd IS NOT NULL
```

![SQL CD 3](https://github.com/user-attachments/assets/48a71259-a140-47e4-842d-e8b0b89d9bd9)

- **Find customers with subscriptions longer than 12 months.DATEDIFF**

```SQL
SELECT CustomerName,SubscriptionType,SubscriptionStart,SubscriptionEnd
FROM [dbo].[Customer Data]
WHERE DATEDIFF(MONTH,SubscriptionStart,SubscriptionEnd) >=12
```

![SQL CD 4](https://github.com/user-attachments/assets/107736b7-a00e-43a6-91aa-7159cbfe55aa)

- **calculate total revenue by subscription type**

```SQL
SELECT SubscriptionType,SUM(Revenue) AS Total_Revenue
	FROM[dbo].[Customer Data]
	GROUP BY SubscriptionType
```

![SQL CD 5](https://github.com/user-attachments/assets/356f3111-79b1-4ff7-bf0f-5a0f79b55da1)

- **Find the top 3 regions by subscription cancellations**

  ```SQL
  SELECT TOP 3 Region,Canceled
FROM [dbo].[Customer Data]
```

![SQL CD 6](https://github.com/user-attachments/assets/855dc0e8-e3a2-470b-943e-065f92d308dd)

- **Find the total number of active and canceled subscriptions**

```SQL
SELECT
SUM( CASE WHEN Canceled = 0 THEN 1 ELSE 0  END) AS ActiveSubscriptions,
SUM (CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
FROM [dbo].[Customer Data]
GROUP BY CustomerID
```

![SQL CD 7](https://github.com/user-attachments/assets/0afc9060-b5b8-4e6f-aaf7-696034621466)


## 3. PowerBi Dashboard

Using PowerBi, I created an interactive Power BI dashboard that visualizes key customer segments, cancellations, subscription trends and also included slicers for filtering data by region, subscription type, and status. 

The dashboard also includes:

- Customer segmentation by region and subscription type
- Revenue breakdown by subscription type
- Monthly Sales Trend
- Trends in subscription duration and cancellation rates











  







