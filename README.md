
---

## DOCUMENTATION REPORT - FRESHMART ANALYTICS


<img width="1044" height="548" alt="Fabric Workflow" src="https://github.com/user-attachments/assets/4c6b0703-5d95-475c-8120-fb1bd8e19393" />


## Overall Approach

The project follows a full end-to-end data workflow within Microsoft Fabric, transforming raw sales data into actionable business insights for FreshMart’s leadership.

## 🏪 Steps
The process began by loading multiple Excel files (sales, products, customers, orders) into a Lakehouse. From there, I created a Dataflow Gen2 using Lakehouse.Contents() to access these files.

The dataflow served as the transformation layer, where I performed key data cleaning and enrichment steps — including column renaming, data type adjustments, and logic-based transformations to standardize and prepare the data for analysis.

Next, the cleaned data was loaded into a Warehouse. A Data Pipeline was set up to automate refresh operations, ensuring that whenever the dataflow updates, the warehouse and all downstream components remain in sync.

Within the SQL Warehouse, I used T-SQL to explore and validate the data, answering key analytical questions and ensuring data accuracy.

From there, I built a Semantic Model on top of the warehouse, defining essential DAX measures such as:

Total Sales Total Orders Average Order Value Distinct Customers Sales per Category

A calculated Date table (DimCalendar) was also created to support time-intelligence analysis and reporting consistency.

Finally, I designed an interactive Power BI report built directly on the semantic model, enabling FreshMart’s leadership to monitor performance metrics and uncover sales patterns in a clean, intuitive dashboard.


## ✅ Key Challenges & Solutions
Challenge Setting up seamless data movement between Lakehouse → Dataflow → Warehouse

How I overcame it Used Fabric Dataflow Gen2 and Pipelines to automate ingestion and refresh cycles.

Challenge Managing transformations (especially logical ones)

How I overcame it Performed transformations directly in Dataflow Gen2, leveraging its Power Query interface for better traceability and performance.

## Major Insights for Leadership
The resulting Power BI dashboard surfaces several critical insights:

Customer Behavior: Top-performing customer segments and repeat purchase trends.

Sales Efficiency: The Average Order Value (AOV) measure helps gauge transaction value and profitability trends.

Category Performance: Identifies high-performing product categories driving most sales.

Time-based Insights: Monthly and quarterly views reveal growth patterns and seasonal dips.

These insights empower FreshMart’s leadership to make data-driven decisions — optimizing marketing spend, managing inventory smarter, and refining customer engagement strategies.

## 🧩 Presentation / Demo Flow (10–15 minutes)

Data Ingestion 
Data Preparation 
Data Loading 
Data Exploration 
Semantic Model Visualization


Thank you, for reading up to this far! 🎉

May the Power BI with you ! 💡
