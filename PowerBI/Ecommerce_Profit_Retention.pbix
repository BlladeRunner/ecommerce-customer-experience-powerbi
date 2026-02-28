# 📦 E-commerce Customer Experience Analysis
Power BI | Data Modeling | Customer Analytics | Operational Insights

## 📌 Project Overview
This project analyzes how delivery delays impact customer satisfaction and business performance in an e-commerce environment.

The goal was not just to build dashboards, but to answer real business questions:
- Do late deliveries increase low review scores?
- Which sellers and regions contribute most to delivery delays?
- How much revenue is at risk due to operational inefficiencies?
- What concrete actions could improve customer experience?

The project was built entirely in Power BI, using Power Query for data transformation and a proper star schema data model.

## 🎯 Business Questions
- How strongly do delivery delays affect low review ratings?
- Which sellers have the highest late delivery rate?
- Which states/regions generate the most delayed orders?
- What percentage of delivered revenue is associated with late deliveries?
- What operational actions would have the highest business impact?

## 🗂 Dataset
Source: Brazilian E-commerce Public Dataset (Olist)

Tables used:
- Orders
- Order Items
- Reviews
- Customers
- Sellers
- Products
- Category Translation
The dataset includes:
- 100k+ orders
- Delivery timestamps
- Customer reviews (1–5 score)
- Seller-level operational data

## 🏗 Data Modeling
A proper star schema was implemented:

Fact Tables:
- fact_orders
- fact_order_items
- fact_reviews

Dimension Tables:
- dim_customer
- dim_seller
- dim_product
- dim_date

Power Query was used for:
- Data cleaning
- Date transformation
- Calculating delivery delay metrics
- Creating operational flags (Late / On-Time)

## 📊 Key KPIs
- Total Orders
- Delivered Orders
- Late Delivery %
- Average Delivery Days
- Average Review Score
- Low Rating %
- GMV (Delivered)
- GMV at Risk (Late Deliveries)
- Rating Gap (Late vs On-Time)

## 🔎 Core Insights
### 1️⃣ Late deliveries significantly increase low ratings
Low rating percentage is substantially higher for late deliveries compared to on-time deliveries.
Business Impact: Delivery reliability directly affects customer satisfaction.

### 2️⃣ A small number of sellers drive most delays
Top sellers with high order volume and high late rate create disproportionate operational risk.
Action: Implement seller-level SLA monitoring and performance scoring.

### 3️⃣ Revenue at Risk is measurable
A significant share of delivered GMV is associated with late deliveries.
Action: Improving logistics performance can directly protect revenue and brand perception.

### 4️⃣ Certain regions show structural delay patterns
Some states consistently show higher late delivery percentages.
Action: Investigate logistics partners and shipping routes in those regions.

### 5️⃣ Delay severity correlates with rating drop
The longer the delay bucket (4–7 days, 8–14 days, 15+), the higher the low rating percentage.
Action: Prioritize severe delay prevention.

## 🧠 Analytical Techniques Used
- Star schema modeling
- DAX measures for KPI calculation
- Segmented analysis (Late vs On-Time)
- Operational flag logic
- Revenue impact analysis
- Decomposition tree for driver analysis
- Drillthrough seller analysis

## 📈 Dashboard Pages
### 1️⃣ Executive Overview
High-level operational KPIs and delivery impact metrics.

### 2️⃣ Delay → Rating Analysis
Correlation between delivery delay and review score.

### 3️⃣ Seller & Region Risk Analysis
Operational risk identification by geography and seller.

### 4️⃣ Insights & Recommended Actions
Business-focused recommendations based on data findings.

## 🛠 Tools Used
- Power BI
- Power Query
- DAX
- Data modeling best practices

## 🚀 Business Recommendations
- Introduce seller-level SLA performance monitoring.
- Penalize or flag consistently late sellers.
- Optimize logistics routes in high-delay states.
- Implement early delay detection alert system.
- Use delay probability scoring to prevent customer dissatisfaction.

## 📎 Repository Structure
```
PowerBI/
    Ecommerce_Customer_Experience.pbix

Docs/
    overview.png
    delay_analysis.png
    seller_analysis.png
    insights.png

DAX/
    Measures.md

README.md
```

## 💡 What This Project Demonstrates
✔ Ability to translate business problems into analytical questions
✔ Data modeling using star schema
✔ Strong DAX KPI development
✔ Insight generation beyond visualizations
✔ Actionable business recommendations