# Data Transformation Workflow — HR Employee Attrition Report  
Author: Rutuja Patil  
Dataset Source: https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset  

---

## 1️⃣ Import Dataset
- Download CSV from Kaggle  
- Power BI → Home → Get Data → Text/CSV  
- Load into Power BI  

---

## 2️⃣ Rename Columns  
To improve readability. Examples:

| Original Name | New Name |
|---------------|-----------|
| MonthlyIncome | Monthly Income |
| YearsAtCompany | Years At Company |
| WorkLifeBalance | Work-Life Balance |
| EnvironmentSatisfaction | Environment Satisfaction |

Rename all columns similarly for clarity.

---

## 3️⃣ Remove Irrelevant Columns  
These columns contain the same value for all rows or provide no analytical value:

- EmployeeCount  
- Over18  
- StandardHours  

Remove via: **Power Query → Remove Columns**.

---

## 4️⃣ Create New Columns

### ➤ Age Group (Calculated Column)
```DAX
Age Group =
SWITCH(
    TRUE(),
    'HR-Employee-Attrition'[Age] < 25, "Under 25",
    'HR-Employee-Attrition'[Age] < 35, "25–34",
    'HR-Employee-Attrition'[Age] < 45, "35–44",
    'HR-Employee-Attrition'[Age] < 55, "45–54",
    "55+"
)
Salary Band (Calculated Column)
Salary Band =
SWITCH(
    TRUE(),
    'HR-Employee-Attrition'[Monthly Income] < 3000, "Low (<3k)",
    'HR-Employee-Attrition'[Monthly Income] < 6000, "Medium (3k–6k)",
    'HR-Employee-Attrition'[Monthly Income] < 9000, "High (6k–9k)",
    "Very High (9k+)"
)

5️⃣ Fix Data Types

Ensure each column has the correct data type:

Age → Whole Number

Monthly Income → Whole Number

Satisfaction Fields → Whole Number (1–4)

Attrition → Text

Gender → Text

OverTime → Text

Use: Model View → Data Type.

6️⃣ Visualization Setup

All KPIs use DAX measures (not raw fields).

Tooltip uses average measures for correct aggregation.

Slicers used: Department, Job Role, Gender, Education Field, Attrition.

7️⃣ Tooltip Page Setup

Create a new page → Page size → Tooltip

Insert cards for tooltip:

Job Role

Department

Avg Monthly Income

Avg Age

Avg Work-Life Balance

Avg Job Satisfaction

Enable: Format → Page → Tooltip → ON

Assign tooltip to visuals (Format → General → Tooltip).

8️⃣ Reset Filters Button

Insert → Buttons → Clear all slicers

Works normally in Power BI Service

In Desktop use Ctrl + Click

9️⃣ Export Screenshots

Export as PDF (optional)

Use Snipping Tool to capture PNG images

Save them in /exports/ folder for GitHub

🔟 Summary

This workflow ensures any user can reproduce the entire HR Attrition Power BI report from the raw dataset.
It documents all column transformations, DAX logic dependencies, data cleaning steps, and modeling choices.

