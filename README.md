# Portfolio Project - Data Analytics with SQL and BigQuery

Welcome to my portfolio of projects created to develop and demonstrate SQL and BigQuery skills.
This repository contains a number of practical tasks and analytical projects aimed at obtaining, processing, analyzing, and interpreting data using SQL queries.

## Table of Contents
- [Projects](#projects)
  - [SQL query 1: Email Analytics and Account Dynamics](#sql-query-1-email-analytics-and-account-dynamics)
  - [SQL query 2: Session analysis](#sql-query-2-session-analysis)
  - [SQL query 3: Daily Revenue & Advertising Cost](#sql-query-3-daily-revenue--advertising-cost)
  - [SQL query 4: Filtering active sessions with a subquery](#sql-query-4-filtering-active-sessions-with-a-subquery)
  - [SQL query 5: Paid Search Traffic Performance Analysis](#sql-query-5-paid-search-traffic-performance-analysis)
  - [SQL query 6: Email Sending Distribution by Account and Month](#sql-query-6-email-sending-distribution-by-account-and-month)
- [Skills Demonstrated](#skills-demonstrated)
- [Tools Used](#tools-used)
- [Contact](#contact)

## Projects
The project focused on analyzing e-commerce data within BigQuery using a dedicated database.  
The project developed a large number of SQL queries to obtain new datasets, calculate basic metrics by account, etc. To demonstrate skills, various SQL operators were used to create queries, including CASE WHEN, views, CTE, UNION, and others.    
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

To maintain the uniqueness of the sections and avoid conflicts arising from different date-field logic, metrics for accounts and emails were calculated separately.  
The query result is shown in the table (Table 1).    
Table 1. - Email Analytics and Account Dynamics

 <img width="1031" height="507" alt="image" src="https://github.com/user-attachments/assets/971dd17e-8b9f-41d5-a6c9-bfc63ad41193" />


A visualization in Looker Studio shows the total values by country for the following fields: account_cnt, total_country_sent_cnt, rank_total_country_account_cnt, and rank_total_country_sent_cnt.    
The graph in Fig. 1 shows the dynamics by date for the sent_msg field.

 <img width="1031" height="687" alt="image" src="https://github.com/user-attachments/assets/ec7246d8-f6c6-48e9-b69b-7cd456e71b3e" />

Fig. 1. The dynamics by date for the sent_msg field.

### SQL query 2: Session analysis
[View a SQL query 2](https://docs.google.com/document/d/1C9qVZTdKhdjkMtM9nDOZaYBPhLp0DDmZYhK5_rq9lvQ/edit?usp=sharing)  

This query was created to analyze all sessions during which purchases were made.   
Using the query, you can determine:
1. Was the session associated with registered users?
To achieve this, CASE WHEN created two categories: registered (for users with accounts) and guest (for users without accounts).
2. All purchases by device type. To find this out, the data is aggregated separately for mobile and desktop.
3. Calculate revenue by:
   - total revenue from all sessions;
   - revenue from registered users;
   - revenue from unregistered users.
4. Percentage of revenue generated by registered sessions, which allows you to understand what share of revenue is generated by registered users.
5. Calculates the average revenue per session, in particular:
   - average check from registered users;
   - average check from unregistered users.
This allows you to answer the question: Do registered users generate more revenue per session on average?
6. The number of sessions of each type (with and without an account), which helps to assess the traffic structure.

The query results yielded the data shown in Table 1.  
Table 1. - Data about registered users and unregistered users 

<img width="1188" height="458" alt="image" src="https://github.com/user-attachments/assets/bc6e46a8-4611-4393-894f-6d07fecf198c" />

A visualization of session analysis for registered and unregistered users is shown in Fig. 1.

<img width="842" height="601" alt="image" src="https://github.com/user-attachments/assets/da76e64f-a98a-4a83-8ea1-2808854c9eb7" />

Fig. 1. Sessions by Device Type

Business conclusion.   
The results show that Desktop generates the most sessions among all devices. Desktop also brings in the highest revenue among both registered and unregistered users (guests). This means that the desktop audience is the most active and solvent.  
Registered users generate significantly more revenue on desktop than on other devices. In addition, revenue from registered users is significantly higher than from guests on any device.  
On mobile, the difference between registered and guest users is also noticeable, though smaller than on desktop. Mobile generates a significant volume of sessions but brings in less revenue, indicating a lower conversion rate or a lower average check.  
Tablet has a very low volume of sessions and revenue, so it can be ignored when making strategic product and marketing decisions.

So, registration directly correlates with high revenue - it is worth increasing the share of users who create an account.
To increase the number of registrations and revenue, it is recommended to:
  1. Invest in desktop development, as this is where the most users and the highest revenue are.
  2. Focus on increasing registrations on mobile, which can significantly increase mobile revenue, which is currently underutilized.
  3. Optimize mobile conversion to purchase, in particular, improve the quality of traffic and UX flow.

### SQL query 3: Daily Revenue & Advertising Cost
[View a SQL query 3](https://docs.google.com/document/d/1ESbVJ_-_fNmBelrGhRFHCkBbp898t7lkD7CTmGVl3Qo/edit?usp=sharing)  

This SQL query aggregates daily revenue from product sales and daily advertising spend from paid search campaigns, then combines the datasets into a single table ready for analytics.

The purpose of this SQL query is to provide a single, daily view of business performance by combining two key metrics:
 - Revenue, which is calculated based on product prices associated with fulfilled orders.
 - Advertising spend, which is collected from paid search spend reports.

This combined dataset is essential for analyzing company performance, calculating ROAS, marketing effectiveness, and tracking profitability trends over time.  
This query was created to demonstrate the functionality of the UNION ALL and JOIN operators.

Revenue query block:
 - Joins the sessions, orders, and products tables.
 - Matches sessions to orders via ga_session_id.
 - Associates order products to get product prices.
 - Calculates total daily revenue using SUM(price).

Ad cost query block:
 - Selects daily costs from the paid search cost table.
 - Aggregates costs using SUM(cost).
 - The UNION ALL operator joins both datasets.
   
A type_table (Revenue, cost) column is added to the query to distinguish between revenue and cost. Graphs have also been built to visualize data on advertising revenue and costs. 

Data Analysis Graph – Daily Revenue and Ad Cost (Fig. 1).
<img width="1031" height="664" alt="image" src="https://github.com/user-attachments/assets/038dd4d2-ce81-435b-8a3f-9b44db7cb677" />

Fig. 1. Daily Revenue and Ad Cost over time.

The resulting graph "Daily Revenue & Advertising Cost" shows the daily dynamics of advertising revenue and costs for the period from November 1, 2020, to January 24, 2021.
The results graph assesses the effectiveness of advertising risks and business profitability, for example, the level of revenue to costs, and trends.
When you analyze the entire return on investment, you see whether advertising delivers the expected results.  
Regarding trends, the graph allows you to assess specific relationships, such as whether revenue increases with rising advertising costs or remains steady despite changes in costs.
If revenue is growing and costs remain stable, this is a sign of an effective strategy.

### SQL query 4: Filtering active sessions with a subquery
[View a SQL query 4](https://docs.google.com/document/d/1ArgemVRPK9N3Mg-elkdBGjgQaxJ-G7Hlt3ZNCwcA4Is/edit?usp=drive_web&ouid=104269468961255412319)  

This query uses a subquery with a JOIN in BigQuery to identify sessions with more than 3 events.  
The subquery groups events by `ga_session_id` and selects only sessions with more than 3 events.  
The main query then joins these sessions back to the main table and counts only the `page_view` events that occurred within those sessions.  

The subquery is used to identify sessions with high user activity:

SELECT  
      ga_session_id,  
      COUNT(*) AS total_events  
    FROM `DA.event_params`  
    GROUP BY ga_session_id  
    HAVING COUNT(*) > 3  

In it, all events from the event_params table are grouped by the ga_session_id field, and the total number of events per session is then counted. The HAVING COUNT(*) > 3 condition selects only those sessions in which more than three events occurred.  
Thus, the subquery returns a list of ga_session_id values only for "active" sessions (sessions with high interaction).  

Then the main query:
- joins these active sessions using JOIN;
- filters events by type page_view;
- counts how many page views (page_view) occurred in active sessions.
  
Thus, the subquery acts as a filter, limiting the selection to only those sessions with a high level of interaction, and allows you to analyze page views only within them.

This approach allows you to focus your analysis on the most engaged users and assess how intensively they interact with the page content. This query demonstrates the use of:
- subqueries;
- aggregation (COUNT, GROUP BY);
- filtering with HAVING;
- JOINs;
- event-based analytics.

The query can be extended to analyze other event types, compare active and inactive sessions, or calculate the average number of views per session.

### SQL query 5: Paid Search Traffic Performance Analysis
[View a SQL query 5](https://docs.google.com/document/d/13FhsXUunZHguI2sCe2DpiUhbCJH0XSUDiNHOCSI9sqg/edit?usp=sharing)

This SQL query in Google BigQuery aggregates monthly paid search spend and actual order revenue, combining data from multiple sources, including ad spend, Google Analytics events, and order and product data.
The query enables you to compare ad spend with revenue by year and month, even if only one side (ad spend or revenue) is available for a given month. To correctly display time periods, the SQL function COALESCE() is used, which returns the first non-NULL value and ensures that the results are correctly combined after a FULL OUTER JOIN.

Query Logic:

1. Aggregation of marketing costs.  
In this part of the query, the year and month are extracted from the cost date, and the paid search costs are aggregated at the monthly level. The prepared data is used for further analysis.
2. Revenue calculation.  
Here, event-level data is aggregated monthly by combining Google Analytics events, orders, and products. The total revenue for each month is calculated.  
3. Data alignment.  
Costs and revenue are combined using a FULL OUTER JOIN, which allows you to save all months in the result, even if data from one source is missing. The COALESCE function is used to correctly align time dimensions.

Table 1 shows the query output, including revenues and costs by year and month.  

Table 1. - Revenues and Costs by Year and Month  

<img width="659" height="193" alt="image" src="https://github.com/user-attachments/assets/a65111fe-5d15-45ef-981c-f0abb9fe8596" />

Query result.  
As a result, a monthly financial summary table is generated, which can be used for:
 - analyzing the effectiveness of paid search campaigns;
 - calculating Return on Investment (ROI) and Return on Ad Spend (ROAS);
 - building dashboards;
 - financial and marketing analytics.

Figure 1 shows the monthly cost of paid search compared to revenue.  

<img width="807" height="458" alt="image" src="https://github.com/user-attachments/assets/cf1cb031-bdea-4e89-9752-532f3c1c84c8" />  

Figure 1. Monthly cost of paid search compared to revenue.

The dashboard shows a comparison of monthly paid search costs and revenue, enabling you to assess the campaign's profitability. The overall ROI was 53.94%, and the ROAS was 54.94%, indicating a positive return on investment. The graphs show fluctuations in costs and revenue by month. Notably, in January 2021, costs exceeded revenue, resulting in a 41.13% reduction in ROI. In contrast, in December 2020, the ROI reached 67.15% with stable revenue. The created visualization helps to quickly identify periods of effective and ineffective advertising for further budget optimization.  

### SQL query 6: Email Sending Distribution by Account and Month
[View a SQL query 6](https://docs.google.com/document/d/1HHUEueIWZs8scZxws5Svp7LhEoW28keuvlxI3UAnfsQ/edit?usp=sharing)

This SQL query analyzes email activity by account and month.
The query performs data aggregation and analytical calculations using window functions (SUM(COUNT(*)) OVER), as well as date processing and formatting.

The SQL query calculates the share of emails sent to each account in each month as a percentage of the total number of emails for that month, and also determines for each account the date of the first and last email sent within the month.  
The main functions of the SQL query are described below.  

1. Combining data from three tables:
 - email_sent - information about email sending events;
 - account_session - the relationship between accounts and sessions;
 - session - the base date of the session.
 
2. Calculating the actual date of sending the email based on the session date and the offset in days.

3. Grouping data by:
 - account_id;
 - month of sending (YYYY-MM).

4. For each account within the month:
 - calculates the share (%) of emails sent by this account out of the total number for the month;
 - determines the first and last date of sending the email in this month.

As a result, the SQL query allows you to:
 - estimate the contribution of each account to the total email traffic by month;
 - identify accounts with high or low activity;
 - Analyze the time frames of email activity for each account



## Skills Demonstrated
1. SQL for Analytics in Google BigQuery
2. Building Complex Queries with CTE
3. Aggregating and Transforming Event-Level Data
4. Working with Time Dimensions (Year / Month)
5. Combining Data from Multiple Sources
6. Processing Incomplete Data (INNER JOIN, LEFT JOIN, FULL OUTER JOIN)

## Tools Used
1. SQL (BigQuery)
2. Google Analytics data model
3. Marketing & Revenue analytics
   
## Contact
Feel free to connect with me via LinkedIn:  
https://www.linkedin.com/in/oksana-olar/
