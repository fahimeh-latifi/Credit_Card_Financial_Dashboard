Credit Card Financial Dashboard

Credit Card Transaction and Customer Analytics Dashboard built with Power BI.

Project Overview

This project presents a Credit Card Financial Dashboard that analyzes credit card transactions and customer data to provide insights into financial performance and customer behavior.

The dashboard helps stakeholders monitor key performance indicators such as:

Total Revenue

Transaction Volume

Customer Segmentation

Weekly Revenue Trends

Income and Age Distribution

The report consists of two main dashboards:

Credit Card Transaction Dashboard

Credit Card Customer Dashboard

These dashboards provide a weekly performance overview and support better decision-making through interactive visualizations.

Project Objective

The objective of this project is to develop a comprehensive weekly credit card dashboard that provides insights into key financial metrics and trends. This allows stakeholders to monitor operations and evaluate credit card performance effectively.

Dataset

The project uses two datasets:

credit_card.csv → contains credit card transaction information

customer.csv → contains customer demographic information

These datasets are included in this repository.

Dashboard Preview

You can view the dashboard in the following file:

credit_card_transaction_report.pdf

This file contains:

Credit Card Financial Dashboard – Transaction

Credit Card Financial Dashboard – Customer

Key DAX Calculations
Age Group Segmentation
AgeGroup =
SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"Unknown"
)
Income Group Segmentation
IncomeGroup =
SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] < 70000, "Medium",
"High"
)
Week Number
week_num2 =
WEEKNUM('public cc_detail'[week_start_date])
Revenue Calculation
Revenue =
'public cc_detail'[annual_fees] +
'public cc_detail'[total_trans_amt] +
'public cc_detail'[interest_earned]
Current Week Revenue
Current_week_Revenue =
CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] =
MAX('public cc_detail'[week_num2])
))
Previous Week Revenue
Previous_week_Revenue =
CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] =
MAX('public cc_detail'[week_num2]) - 1
))
Tools Used

Power BI

DAX

Excel

Data Modeling

Key Insights

The dashboard enables analysis of:

Revenue trends by week

Customer segmentation by income and age

Transaction distribution

Financial performance indicators

Author

Fahimeh Latifi

Data Analyst | Power BI | SQL | Data Visualization