# 📊 PMO Executive Dashboard (Power BI)

**Role:** IT Business Analyst  
**Tools:** Power BI Desktop, DAX, Power Query, Excel  
**Domain:** Project Management Office (PMO) Strategy

## 📌 Project Overview
Designed and developed an interactive dashboard for the CIO to monitor a **$3.5M IT Project Portfolio**. The goal was to replace manual Excel tracking with a live view of "Budget Variance" and "Project Health" (RAG Status), enabling faster strategic decision-making.

![Dashboard Screenshot](PMO%20Executive%20Dashboard.png)

## 🛠️ Technical Implementation
### 1. Data Modeling
* Established a **One-to-Many Relationship** between the `Project_List` (Dimension Table) and `Project_Updates` (Fact Table) using the unique `ProjectID` key.

### 2. Key DAX Measures
I developed the following DAX measures to calculate real-time portfolio metrics:

```dax
/* 1. Total Portfolio Budget */
Total Budget = SUM(Project_List[TotalBudget])

/* 2. Actual Spend (Dynamic Logic - Gets max spend per project) */
Actual Spend = SUMX(Project_List, CALCULATE(MAX(Project_Updates[SpendToDate])))

/* 3. Budget Variance */
Budget Variance = [Actual Spend] - [Total Budget]
