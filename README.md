

![work in progress](images/1000_F_84773798_DsBY5SMlNebYQH5hsQujbSrqwMn6XTcb.jpg)




# Business Objective:
The e-commerce company is expecting below analysis using the data

## Calculate Invoice amount or sale_amount or revenue for each transaction and item level
- Invoice Value =(( QuantityAvg_price)(1-Dicount_pct)*(1+GST))+Delivery_Charges

## Perform Detailed exploratory analysis
- Understanding how many customers acquired every month
- Understand the retention of customers on month on month basis
- How the revenues from existing/new customers on month on month basis
- How the discounts playing role in the revenues?
- Understand the trends/seasonality of sales by category, location, month etc…
- How number order varies and sales with different days?
- Calculate the Revenue, Marketing spend, percentage of marketing spend out of revenue, Tax, percentage of delivery charges by month.
- How marketing spend is impacting on revenue?
- Which product was appeared in the transactions?
- Which product was purchased mostly based on the quantity?


## Performing Customer Segmentation
- Heuristic (Value based, RFM) – Divide the customers into Premium, Gold, Silver, Standard customers and define strategy on the same.
- Scientific (Using K-Means) & Understand the profiles. Define strategy for each segment.

## Predicting Customer Lifetime Value (Low Value/Medium Value/High Value)
- First define dependent variable with categories low value, medium value, high value using customer revenue.
- Then perform Classification model

## Cross-Selling (Which products are selling together)
- You can perform exploratory analysis & market basket analysis to understand which of items can be bundled together.

## Predicting Next Purchase Day (How soon each customer can visit the store (0-30 days, 30-60 days, 60-90 days, 90+ days)
- For this, we need create dependent variable at customer level (average days per one transaction for only repeat customers and divide into groups 0-30 days, 30-60 days, 60-90 days and 90+ days) then build classification model to predict next purchase of given customer.


## Perform cohort analysis by defining below cohorts
- Customers who started in each month and understand their behaviour
- Which Month cohort has maximum retention?