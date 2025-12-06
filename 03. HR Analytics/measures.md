# DAX Measures — HR Employee Attrition Report
Author: Rutuja Patil  
Source Dataset: https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset

---

## 📌 Total Employees
```DAX
Total Employees = COUNTROWS('HR-Employee-Attrition')

📌 Employees Left
Employees Left =
CALCULATE(
    COUNTROWS('HR-Employee-Attrition'),
    'HR-Employee-Attrition'[Attrition] = "Yes"
)
📌 Attrition Rate
Attrition Rate = DIVIDE([Employees Left], [Total Employees])

📌 Avg Monthly Income
Avg Monthly Income = AVERAGE('HR-Employee-Attrition'[Monthly Income])

📌 Avg Age
Avg Age = AVERAGE('HR-Employee-Attrition'[Age])

📌 Avg Job Satisfaction
Avg Job Satisfaction = AVERAGE('HR-Employee-Attrition'[JobSatisfaction])

📌 Avg Work-Life Balance
Avg Work-Life Balance = AVERAGE('HR-Employee-Attrition'[WorkLifeBalance])

📌 Avg Environment Satisfaction
Avg Environment Satisfaction = AVERAGE('HR-Employee-Attrition'[EnvironmentSatisfaction])

📌 Avg Years At Company
Avg Years At Company = AVERAGE('HR-Employee-Attrition'[YearsAtCompany])

📌 Employees Stayed
Employees Stayed =
CALCULATE(
    COUNTROWS('HR-Employee-Attrition'),
    'HR-Employee-Attrition'[Attrition] = "No"
)

Age Group (New column)

Age Group =
SWITCH(
    TRUE(),
    'HR-Employee-Attrition'[Age] < 25, "Under 25",
    'HR-Employee-Attrition'[Age] < 35, "25–34",
    'HR-Employee-Attrition'[Age] < 45, "35–44",
    'HR-Employee-Attrition'[Age] < 55, "45–54",
    "55+"
)


Salary Band (New column)

Salary Band =
SWITCH(
    TRUE(),
    'HR-Employee-Attrition'[Monthly Income] < 3000, "Low (<3k)",
    'HR-Employee-Attrition'[Monthly Income] < 6000, "Medium (3k–6k)",
    'HR-Employee-Attrition'[Monthly Income] < 9000, "High (6k–9k)",
    "Very High (9k+)"
)



