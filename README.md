# 📞 Call Center Performance Dashboard
## 🧩 Problem Statement
## The call center manager needs a clear and interactive Power BI dashboard to monitor key performance metrics like customer satisfaction, call volumes, response times, and agent efficiency. The goal is to turn raw call data into actionable insights that help improve service quality, agent performance, and overall customer experience.
---
## 🧠 Overview

This Power BI dashboard provides a comprehensive view of the performance of a Call Centre over a 3-month period. It enables stakeholders to track key performance metrics, agent efficiency, customer satisfaction, and resolution rates. The dashboard empowers supervisors and managers to identify performance gaps, improve agent productivity, and enhance overall service quality.
---
### Data Modelling
![Image](https://github.com/user-attachments/assets/92d758a1-39f3-41b7-9ab4-892bee318da9)
---
###  Steps Followed
Step 1: Loaded the dataset (Call-Center-Dataset.xlsx) into Power BI Desktop using the Excel connector.

Step 2: Opened Power Query Editor and enabled Column Distribution, Column Quality, and Column Profile under the View tab to assess data cleanliness.

Step 3: Changed the default data profiling setting from 1000 rows to entire dataset to get a complete picture.

Step 4: Identified that most columns were clean, with very few or no null values. Some empty values were found in columns like Talk Duration, which were treated appropriately during analysis.

Step 5: For calculating Average Speed of Answer and Average Handle Time, null values were excluded as they were minimal (less than 1%) and wouldn't impact results significantly.

Step 6: Applied a consistent report theme from the View tab for visual appeal and uniformity.

Step 7: Created an interactive home page with key KPIs such as Calls Answered, Abandoned Calls, Avg. Speed of Answer, and Avg. Talk Duration using Card visuals.
![Image](https://github.com/user-attachments/assets/d999faf1-6be7-4990-8612-8d49df055ca3)

Step 8: Added slicers to allow the user to filter the report by Call Topic, Agent Name, and Date Range for deeper insights.
![Image](https://github.com/user-attachments/assets/915b9ac3-14d3-4626-92fb-32e49fa9da75)

Step 9: Designed a bar chart showing Topic-wise Call Volume Analysis to identify common reasons for customer calls and optimize resource planning.

Step 10: Built an Agent Performance Quadrant comparing Average Talk Time vs Calls Handled, helping the manager identify top-performing and underperforming agents visually.

Step 11: Created a Summary View showing Total Calls, Answered/Abandoned Split, and Customer Satisfaction Levels using stacked bar charts and KPIs.
---
## 📂 Measures (DAX)
## To calculate Total Calls Count

Total Calls = DISTINCTCOUNT('Data Table'[Call Id])

## To calculate Total Answered Calls

Total Answered Calls = CALCULATE([Total Calls],FILTER('Data Table','Data Table'[Answered (Y/N)]="Y"))

## To calculate Total Agents Count
Total Agents = DISTINCTCOUNT('Data Table'[Agent])

## To calculate Avg Speed of Answering(in Seconds)
Avg Speed of Answering = AVERAGE('Data Table'[Speed of answer in seconds])

## To calculate Avg Handling Time (in Minutes)
HandlingTimeMinutes = 
TIMEVALUE('Data Table'[AvgTalkDuration])*24*60

## To calculate CSAT %
CSAT % = CALCULATE(COUNTROWS('Data Table'),FILTER('Data Table','Data Table'[Satisfaction rating] IN {4,5}))/CALCULATE(COUNTROWS('Data Table'),FILTER('Data Table','Data Table'[Answered (Y/N)]="Y"))

## To calculate Resolved Calls
Resolved Calls = CALCULATE([Total Answered Calls],'Data Table'[Resolved]="Y")

## To calculate Unresolved Calls
Unresolved Calls = CALCULATE([Total Answered Calls],'Data Table'[Resolved]="N")

## To create a calculated column for Star Rating
Star Rating = REPT(UNICHAR(9733),('Data Table'[Satisfaction rating]))  

## To calculate Avg Speed of Answering
Avg Speed of Answering = AVERAGE('Data Table'[Speed of answer in seconds])
## 📊 Dashboard Pages

### 1. Home Page
- It is made for Quick navigation to the specific Reports.
- It shows the date range for the data is available
- Click on the buttons for navigating through Summary Report, Agent Performance Report, Topic Wise Calls Analysis
![Image](https://github.com/user-attachments/assets/d999faf1-6be7-4990-8612-8d49df055ca3)
### 2. Summary Report
- KPI's Total Calls, Total Answered Calls, Total Agent, Avg Speed of Answering Calls, Avg Handling Time, CSAT% gives quick status of 
  Call Center data.
- Charts like Total Calls by Weekdays, Total Calls by Topic, Total Calls and Total Answered Calls by Agent and Total calls by Time slot 
  provides the distribution of Total Calls.
- Summary Insights visual provide the narratives of Summary Report.
![Image](https://github.com/user-attachments/assets/6bc7450e-f151-4906-816d-0805d0c58104)
### 3. Agent Report
- Agent-wise performance based on Avg Speed of Answered Calls, Nos. of Resolved and Unresolved calls
- Detail Report for Agents Performance provide in detail performance based on Total Calls, Total Answered Calls, Resolved Calls, 
  Unresolved Calls, Avg. Speed
![Image](https://github.com/user-attachments/assets/97cddde5-2f1e-4e0b-8342-db456282dc4e)
### 4. Topic-Wise Calls Analysis
- Breakdown of calls by topic (e.g., Streaming, Technical Support, Payment Related, Admin Support, Contract Related).
- Trend and distribution visuals to spot high-volume topics.
- Topic wise Avg Speed of Answered Calls (In Second) - Provides the time consuming topics
![Image](https://github.com/user-attachments/assets/c04f8b9e-58aa-4d7a-b924-03b1fc2a7c1c)
---

## ⚙️ Tools & Technologies

- **Power BI Desktop**
- **Power Query (M Language)**
- **DAX (Data Analysis Expressions)**
- **Excel** for data source

---

## 📈 Key Insights

- Majority of calls were related to Billing and Technical Support.
- Average handling time and time to answer varied significantly by agent.
- Higher customer satisfaction was linked to faster resolution and shorter call times.
- Unresolved calls had notably lower feedback ratings.

---

## 🧰 Enhancements & Recommendations

- Introduce call-back option during peak hours to reduce waiting time.
- Conduct targeted training for low-performing agents.
- Use predictive analytics for proactive support on high-volume topics.
---

## 🙌 Acknowledgements

Thanks to the customer support team for maintaining detailed logs, enabling the creation of this insightful report.
---


