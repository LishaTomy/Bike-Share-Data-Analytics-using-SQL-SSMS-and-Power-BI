# Bike Share Data Analytics using SQL SSMS and Power BI
Conducted an end-to-end analysis of bike-share data to evaluate revenue performance, revenue trends, seasonal patterns, and rider demographics. Used SQL to clean, transform, and aggregate large datasets, and developed interactive Power BI dashboards to visualize yearly and seasonal revenue trends, rider segmentation, and usage behaviour.

## Project Overview  
This project delivers an interactive Power BI dashboard for **Toman Bike Share** to support data-driven decision-making through revenue, profit, seasonal trends, and rider demographics analysis.

## Tools Used
- SSMS (SQL Server Management Studio) for data analysis
- Power BI (Dashboard & visualizations)

---
## Data Source
Data is already provided in three csv files.

## Key Features
- Hourly revenue analysis
- Profit and revenue trends
- Seasonal performance insights
- Rider demographic breakdown  

## Dashboard Preview
<img width="1157" height="651" alt="image" src="https://github.com/user-attachments/assets/c5d4a09d-e53c-48fe-a046-2de5a64cc534" />

---

## Process & Methodology  

### **Loading dataset**  
- Loaded three datasets; `bike_share_yr_0`,  `bike_share_yr_1` and `cost_table` 

### Joining datasets to analyse the data  
```sql
with cte as (
select * from bike_share_yr_0
union all
select * from bike_share_yr_1)

select 
dteday,
season, 
a.yr, 
hr,
weekday,
rider_type,
riders,
price,
COGS,
riders*price as revenue,
riders*price - COGS as profit
from cte a
left join cost_table b
on a.yr=b.yr
```

### Business Insights from the dashboard

- It is evident from the dashboard that the sales in 2022 raise substancially when compared to 2021.
- There is a 25% increase in the year 2022, which effectively led to the increased revenue and profit.(4.99-3.99=1; 1/3.99=0.25)
- There is a 64% increase in the total rides compared to the previous year.
- The price elasticity is 64/25 = 2.56, which means there can be an increase of atmost 2.26in the price.
- Conservative Increase: Considering the substantial increase last year, a more conservative increase might be prudent to avoid hitting a price ceiling where demand starts to drop. An increase in the range of
10-15% could test the market's response without risking a significant loss of customers.
- Price Setting:
If the price in 2022 was $4.99, a 10% increase would make the new price about $5.49.A 15% increase would set the price at approximately $5.74.

### Recommendations

- Market Analysis: Conduct further market research to understand customer satisfaction, potential competitive changes, and the overall economic environment. This can guide whether leaning towards the lower or higher end of the suggested increase.
- Segmented Pricing Strategy: Consider different pricing for casual versus registered users, as they may have different price sensitivities.
- Monitor and Adjust: Implement the new prices, but be ready to adjust based on immediate customer feedback and sales data. Monitoring closely will allow you to fine-tune your pricing strategy without committing fully to a price that might turn out to be too high.
  

> :woman_technologist:Created by **Lisha Tomy** | Data Enthusiast & Analyst
