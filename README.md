# Data Analytics with SQL and BigQuery
Welcome to my portfolio of projects created to develop and demonstrate SQL and BigQuery skills.
This repository contains a number of practical tasks and analytical projects aimed at obtaining, processing, analyzing, and interpreting data using SQL queries.

## Table of Contents
- [Projects](#projects)
  - [SQL query 1: Email Analytics and Account Dynamics](#sql-query-1-email-analytics-and-account-dynamics)
  - [SQL query 2: : Daily Revenue & Advertising Cost](#sql-query-2--daily-revenue--advertising-cost)
- [Skills Demonstrated](#skills-demonstrated)
- [Tools Used](#tools-used)
- [Contact](#contact)

## Projects
The project focused on analyzing e-commerce data within BigQuery using a dedicated database.
The project developed a large number of SQL queries that were used to obtain new data sets, calculate basic metrics by account, etc. To demonstrate skills, various SQL operators were used to create queries, including CASE WHEN, views, CTE, UNION, and others.  
Diagram of relationships between tables in the database shown in Fig. 1.

<img width="1613" height="1080" alt="DB_diagram" src="https://github.com/user-attachments/assets/ec1cba86-6422-4585-b6ef-639c3ff4783f" />  
Fig. 1. - Database table.

A description of the tables presented in the database is given in the Table. 1.    
Table 1. - Description of the tables represented in the database 
<img width="746" height="525" alt="image" src="https://github.com/user-attachments/assets/93a50a1d-3169-46b9-b221-8a2839d4a77c" />


### SQL query 1: Email Analytics and Account Dynamics 
[View a SQL query 1](https://docs.google.com/document/d/1QUXVM-Cc6KNmyaLaGPXWmSHdN8rPljdV-tOMbZYpZL0/edit?usp=sharing)  
This SQL query is designed to create a dataset for further analysis of account creation dynamics and user activity in emails (sends, opens, transitions).
In addition, user behavior was analyzed by criteria such as send interval, account verification, and subscription status.
Based on the results, user activity was compared across countries, key markets were identified, and users were segmented based on several parameters.
This SQL query has a multi-level structure with multiple CTEs (WITH blocks) that sequentially combine data from different tables into a single aggregated model.
The query is built around the fact table email_sent(es), which serves as the core of the data model for this SQL query.
JOIN/LEFT JOIN operators were used to create a dataset based on the SQL query.
The SQL query results contain a set of grouping fields that cover categorical variables and key metrics for both accounts and emails. 

**The main grouping fields are:**  
 - date – for accounts, it displays the creation date, for emails – the sending date;
 - country – the user's country;
 - send_interval – the sending interval set by the account;
 - is_verified – the account verification status;
 - is_unsubscribed – the subscription status (whether the user has unsubscribed).

**Main metrics:**  
 - account_cnt – the number of accounts created;
 - sent_msg – the number of emails sent;
 - open_msg – the number of emails opened;
 - visit_msg – the number of clicks on links in emails.  

**Additional metrics (calculated based on the main ones):**
 - total_country_account_cnt – the total number of accounts created within the country;
 - total_country_sent_cnt – total number of emails sent within the country;
 - rank_total_country_account_cnt – country ranking by the number of accounts created;
 - rank_total_country_sent_cnt – country ranking by the number of emails sent.

To maintain the uniqueness of the sections and avoid conflicts due to different logic of using the date field, metrics for accounts and emails were calculated separately.
The query result is shown in the table (Table 1).  
Table 1. - Email Analytics and Account Dynamics

 <img width="1031" height="507" alt="image" src="https://github.com/user-attachments/assets/971dd17e-8b9f-41d5-a6c9-bfc63ad41193" />


A visualization has been created in Looker Studio that shows the total values by country for the following fields: account_cnt, total_country_sent_cnt, rank_total_country_account_cnt, and rank_total_country_sent_cnt.  
The graph in Fig. 1 shows the dynamics by date for the sent_msg field.

 <img width="1031" height="687" alt="image" src="https://github.com/user-attachments/assets/ec7246d8-f6c6-48e9-b69b-7cd456e71b3e" />

Fig. 1. The dynamics by date for the sent_msg field.

### SQL query 2: : Daily Revenue & Advertising Cost
[View a SQL query 2](https://docs.google.com/document/d/1ESbVJ_-_fNmBelrGhRFHCkBbp898t7lkD7CTmGVl3Qo/edit?usp=sharing)  
This SQL query aggregates daily revenue from products sold and daily advertising spend from paid search campaigns, then combines both datasets into a single table ready for analytics.
The purpose of this SQL query is to provide a single, daily view of business performance by combining two key metrics:
Revenue which is calculated based on product prices associated with fulfilled orders.
Advertising spend, which is collected from paid search spend reports.
This combined dataset is essential for analyzing company performance, calculating ROAS, marketing effectiveness, and tracking profitability trends over time.
This query was created to demonstrate the work of operators UNION ALL and JOIN.
Revenue query block:
Joins the sessions, orders, and products tables.
Matches sessions to orders via ga_session_id.
Associates order products to get product prices.
Calculates total daily revenue using SUM(price).
Ad cost query block:
Selects daily costs from the paid search cost table.
Aggregates costs using SUM(cost).
The UNION ALL operator joins both datasets.
A type_table (Revenue, cost) column is added to the query to distinguish between revenue and cost. Graphs have also been built to visualize data on advertising revenue and costs. The resulting table with data (Table 1).  
Table 1. - Daily revenue from products sold and daily advertising spend

<img width="1031" height="640" alt="image" src="https://github.com/user-attachments/assets/9158d5a9-5d99-4b4b-aeea-29194daea09a" />

Data Analysis Graph – Daily Revenue and Ad Cost (Fig. 1).
<img width="1031" height="664" alt="image" src="https://github.com/user-attachments/assets/038dd4d2-ce81-435b-8a3f-9b44db7cb677" />

Fig. 1. Daily Revenue and Ad Cost over time.


## Skills Demonstrated

## Tools Used

## Contact
Feel free to connect with me via LinkedIn:  
https://www.linkedin.com/in/oksana-olar-993709162/
