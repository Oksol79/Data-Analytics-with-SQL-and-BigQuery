# Data Analytics with SQL and BigQuery
Welcome to my portfolio of projects created to develop and demonstrate SQL and BigQuery skills.
This repository contains a number of practical tasks and analytical projects aimed at obtaining, processing, analyzing, and interpreting data using SQL queries.
## Table of Contents
- [Projects](#projects)
  - [Project 1: Email Analytics and Account Dynamics](#project-1-email-analytics-and-account-dynamics)
  - [Project 2: Name]()
- [Skills Demonstrated](#skills-demonstrated)
- [Tools Used](#tools-used)
- [Contact](#contact)

## Projects

### Project 1: Email Analytics and Account Dynamics 
[View a SQL query](https://docs.google.com/document/d/1QUXVM-Cc6KNmyaLaGPXWmSHdN8rPljdV-tOMbZYpZL0/edit?usp=sharing)  
An e-commerce database was used to perform the task, and queries were executed in BigQuery. As part of the project, a SQL query was developed to create a dataset to analyze the dynamics of account creation and user activity in emails (sending, opening, transitions).  
Additionally, user behavior was analyzed by categories such as sending interval, account verification, and subscription status. Based on the results, user activity in different countries was compared, key markets were identified, and users were segmented by a number of parameters.  
This SQL query has a multi-level structure with several CTEs (WITH blocks) that sequentially combine data from different tables into a single aggregated model. The query is built around the fact table email_sent(es), which serves as the core of the data model for this SQL query. JOIN/LEFT JOIN operators were used to create the dataset based on the SQL query.   
Diagram of relationships between tables in the database:
<img width="1613" height="1080" alt="DB_diagram" src="https://github.com/user-attachments/assets/ec1cba86-6422-4585-b6ef-639c3ff4783f" />

The SQL query results contain a set of grouping fields that cover categorical variables and key figures for both accounts and emails.  
The main grouping fields are:
 - date – for accounts, it displays the creation date, for emails – the sending date;
 - country – the user's country;
 - send_interval – the sending interval set by the account;
 - is_verified – the account verification status;
 - is_unsubscribed – the subscription status (whether the user has unsubscribed).

Main metrics:
 - account_cnt – the number of accounts created;
 - sent_msg – the number of emails sent;
 - open_msg – the number of emails opened;
 - visit_msg – the number of clicks on links in emails.

Additional metrics (calculated based on the main ones):
 - total_country_account_cnt – the total number of accounts created within the country;
 - total_country_sent_cnt – total number of emails sent within the country;
 - rank_total_country_account_cnt – country ranking by the number of accounts created;
 - rank_total_country_sent_cnt – country ranking by the number of emails sent.

To maintain the uniqueness of the sections and avoid conflicts due to different logic of using the date field, metrics for accounts and emails were calculated separately.

 <img width="1031" height="507" alt="image" src="https://github.com/user-attachments/assets/971dd17e-8b9f-41d5-a6c9-bfc63ad41193" />

A visualization has been created in Looker Studio that shows the total values by country for the following fields: account_cnt, total_country_sent_cnt, rank_total_country_account_cnt, and rank_total_country_sent_cnt.  
The graph shows the dynamics by date for the sent_msg field.

 <img width="1031" height="687" alt="image" src="https://github.com/user-attachments/assets/ec7246d8-f6c6-48e9-b69b-7cd456e71b3e" />


### Project 2: Name
[View Project]()  


## Skills Demonstrated

## Tools Used

## Contact
Feel free to connect with me via LinkedIn:  
https://www.linkedin.com/in/oksana-olar-993709162/
