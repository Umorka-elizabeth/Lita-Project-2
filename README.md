# Lita-Project-2
Customer Segmentation Analysis for a Subscription Service

 [Project Overview](#project-overview)
 
 [Data Description](#data-description)
 
 [Basic Statistics about the Dataset](#basic-statistics-about-the-dataset)
 
 [Methodology](#methodology)
 
 [Data Collection](#data-collection)
 
 [Data Manipulation](#data-manipulation)
 
 [Exploratory Data Analysis(EDA)](#exploratory-data-analysis(eda))

 [Data Analysis on Structured Query Language](data-analysis-on-structured-query-language)
 
 [Tools Used](#tools-used)
 
 [Dashbord Overview](#dashboard-overview)
 
 [Data Analysis and Insights Generation](#data-analysis-and-insights-generation)
 
 [Recommendation](#recommendation)
 
 [Conclusion](#conclusion)
   
### Project Overview
---
This project involves analysing customer data for a subscription service to identify subscription patterns and trends. The end result is to understand customer behaviour to subscription, identification of subscription types and the trends in subscription cancellation and renewals. This analysis was carried out based on the customer dataset provided for this project, which was used to derive our objectives and also provides relevant conclusion and recommendations.

### Data Description
---
The dataset includes the following fields:
1. CustomerID: Unique identifier for each customer
2. Customer Name: Individual customer's unique name
3. Region: An area of the country located for sales
5. Subscription Type: name to various subscription services rendered
6. Subscription Start:This is the begining date for a purchased subscription service
7. Subscrption End: Is the end date for a purchased subscription service
8. Canceled: It depict active and inactive subscription
9. Revenue: Total amount generated from subscription services rendered
10. Duration/day: 365 days
11. Duration/month: 12 months
12. Duration/year: 1 year

### Basic Statistics about the Dataset:
1. Total Revenue: N68M
2. Average Sales: N22.5M
5. Number of CustomersID: 34K
6. Subscription Type: 4

 ### Methodology
 ---
### Data Collection
The dataset for this analysis was provided by the Incubator Hub through LMS. The data was provided in Excel format, making it accessible for analysis.

### Data Manipulation
1. Data Cleaning:
Checked for Spelling Errors, Duplicate Values, and Blank Cells: Ensured data quality by correcting any spelling errors, removing duplicate entries, and addressing missing values.

2. Data Transformation:
Data Types and Formatting: Ensured all data fields were assigned the correct data types and well formated. New columns for subscription duration by day, month and year were added.

### Exploratory Data Analysis (EDA)
---
After cleaning the data in excel, pivot table was used for the analysis and then the cleaned data was exported to Structured Query Language for futher analysis and finaly to PowerBi for the creation of interactive dashboard. The following activities were carried out;
* Data Filtering and Segmentation: Filtering was done on Excel and pivot tables allows for segmentation by subscription type, most popular susbscriptiontype, average duration, cancellation and renewals which produces a great insight into the data. SQL's GROUP, WHERE and ORDER BY clauses filtered and grouped by product, region, monthly etc also revealed targeted insight while PowerBI segmented insights of Excel and SQL into an interesting report.
* Descriptive Analysis: Metrics calculation was done on Excel for the average subscription duration which reported a period of 12 months which is one year and the most popular subscription type is Basic. SQL queries were written for a futher insight into the subscription pattern and trends and PowerBI was used for visualisation dashboard.
* Dashboard Creation: Pivot table on Excel was used for the summarisation of the dataset and PowerBi dashboard visualizes the data using components like barchat, piechart, donut chart, table, area chart, tables, cards and slicer.

 ### Data Analysis on Structured Query Lanquage
 ---
 This is where we include some basic lines of queries during our analysis.

 To SELECT THE CUSTOMER DATASET TABLE 
 ```SQL
Select * from [dbo].[PROJECT 2 CUSTOMER DATA]
```
TO RETRIEVE TOTAL NUMBER OF CUSTOMERS FROM EACH REGION
```
SELECT REGION, COUNT(CUSTOMERID) AS CUSTOMERID FROM[dbo].[PROJECT 2 CUSTOMER DATA]
GROUP BY REGION
```
THE MOST POPULAR SUBSCRIPTION TYPE BY NUMBER OF CUSTOMERS
```
select top 1 subscriptiontype, count(distinct customerid) as total_customers from[dbo].[PROJECT 2 CUSTOMER DATA]
Group by SubscriptionType
```
CUSTOMERS WHO CANCELED THEIR SUBSCRIPTION WITHIN 6 MONTHS
```
SELECT customerID from[dbo].[PROJECT 2 CUSTOMER DATA]
WHERE datediff(month, subscriptionStart, subscriptionEnd)<=6
Group by customerID;
```
AVERAGE SUBSCRIPTION DURATION FOR ALL CUSTOMERS
```
SELECT AVG(datediff(day,subscriptionStart, subscriptionEnd)) as Avg_subscription_duration FROM[dbo].[PROJECT 2 CUSTOMER DATA]
```
CUSTOMERS WITH SUSBCRIPTION LONGER THAN 12 MONTHS
```
SELECT customerID FROM [dbo].[PROJECT 2 CUSTOMER DATA]
Where datediff(month, subscriptionStart, SubscriptionEnd)>12;
```
REVENUE BY SUBSSCRIPTION TYPE
```
SELECT Sum(Revenue) as Total_Revenue, subscriptionType as SubscriptionType from[dbo].[PROJECT 2 CUSTOMER DATA]
GROUP BY SubscriptionType
```
TOP 3 REGIONS BY SUBSCRIPTION CANCELLATION
```
SELECT TOP 3(REGION) AS REGION, Canceled AS SUBSCRIPTION_CANCELED FROM[dbo].[PROJECT 2 CUSTOMER DATA]
Order by Canceled;
```
TOTAL NUMBER OF ACTIVE AND CANCELED SUBSCRIPTION
```
SELECT COUNT(Canceled) AS SUBSCRIPTION_CANCELED FROM [dbo].[PROJECT 2 CUSTOMER DATA]
WHERE CANCELED = 0
```
```
SELECT COUNT(CANCELED) AS SUBSCRIPTION_ACTIVE FROM [dbo].[PROJECT 2 CUSTOMER DATA]
WHERE CANCELED = 1
```
 ### Tools used
 ---
1. Microsoft Excel: This is used for data cleaning, analysis and creating pivot visualization.
   [Download Here](https://www.microsoft.com)
2. Structured Query Language for quering data
5. PowerBI for dashboard visualization
   
 ### Dashboard Overview
 ![CUSTOMER VISUALIZATION DASHBOARD](https://github.com/user-attachments/assets/285dea79-06b5-4723-be11-b10c3110e29b)
 ![REVENUE TRENDS](https://github.com/user-attachments/assets/9aea3718-677b-4554-9b84-f30a5e415e73)

 ### Datalysis and Insights Generation
 This visualization reveals the segments, revenue trends, subscription pattern, cancellations and renewals of the Customer Subscription Service.
 
 - Subscription Segment/Performance: The barchart shows the subscription segments as shown by subscription types and revenue generated.
The Basic subscription type is the most popular type with the highest revenue of N34M which is 50% of the entire revenue generated while Premium and Standard type, each reported N17M revenue. It also reveals the regional revenue. East Region came top with a marginal revenue of N0.1M above other regions revenue of N16.9, N16.8 respectively.

- Subscription Segment/Customer behaviour: The total customers subscription is 34K with Basic type reporting 50% of the total number and remaining 50% was shared equally by Premium and Standard type. The regional subscription pattern by customers is on marginal level. The donut chart depicts that 25.12 % of the total subscription by customers was from East being the highest, followed by South, North and West reporting 25%, 24.96% and 24.92% respectively.

 - Subscription Trend: From the dashboard above, we could see at a glance that this customer service is operating at a downward trend from 2023 to 2024 at yearly, quartely and monthly basis.

- Subscription Cancellation & Active: This analysis number of active and cancelled subscription. The number of Active subscription as at the reporting period is 15,175 count with a corresponding revenue of N30M which is 45% of the entire revenue and canceled subscription is 18,612 with revenue of N37M representing 55% of the total revenue. This analysis is shown by the cards and the corresponding piechats and table which further explain in details.

- Subscription By Renewal: The table shows the subscription by renewal on yearly basis. Year 2023 reported the highest renewal of 20K count and the corresponding revenue of about N40M while year 2024 reported almost 14K count and revenue of about N27M for 8 months (January to August).
  
### Recommendation
---
1. Engage more on marketing to generate more customers to buy into subscriptiontype Premium and standard in order to measure up and beyond Basic subscriptiontype.
   
2. Basic is a Star and also a cash generating unit to the business, therefore, there is need for continuous investment in marketing and improvement to maintain a competitive position and growth.
   
4. Understanding customers interest for satisfaction and sales growth in their various region. The regions are all operating marginally, strategies should be deployed to enhance more sales in all the regions. For example, new packages for the different subscription types, discount allowed etc
   
5. Management should help to review the downward revenue trends and develop strategies for upward trend.

6. The basis for cancelled subscription should be looked into to avoid such huge amount of loss to the business.

7. Managenement should invest aggressive marketing to boost revenue in the last quarter of 2024 and subsequently. 

### Conclusion
---
The customer subscription service operates on a top and marginal level in all segments except for the challenge of renewal cancellation and the revenue trends. Our recommendation focus on investment in marketing to boost revenue, customers satisfaction to avoid cancellation as well as continuous growth. With the adoption of the aforementioned strategies, increase in revenue, customers retainership and sustainable growth will be achieved.
 


