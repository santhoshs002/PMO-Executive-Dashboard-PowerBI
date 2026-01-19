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

```

## 🔍 Key Insights
* **Portfolio Health:** Identified that **20% of active projects** were in "Red" status.
* **Financial Risk:** The "Red" projects accounted for a significant budget overrun, visualized instantly via conditional formatting.
* **Bottlenecks:** The 'Crisis View' slicer allows management to isolate failing projects in under 5 seconds.

## 📂 Project Files
* **[PMO Executive Dashboard.pbix](PMO%20Executive%20Dashboard.pbix):** The full Power BI source file with data model and DAX.
* **[PMO Executive Dashboard.png](PMO%20Executive%20Dashboard.png):** Screenshot of the final executive view.
* **[Project_List.csv](Project_List.csv):** Raw data source for project metadata.
* **[Project_Updates.csv](Project_Updates.csv):** Raw data source for weekly status reports.
* **[Project_List_CSV_Converted.xlsx](Project_List_CSV_Converted.xlsx):** Excel format of the project list.
* **[Project_Updates_CSV_Converted.xlsx](Project_Updates_CSV_Converted.xlsx):** Excel format of the updates data.
