# Attriton-Dashboard
This dashboard provides a complete analysis of employee attrition within an organization. It helps HR teams understand where workforce turnover is happening most, what factors contribute to attrition, and how demographic and behavioral patterns differ across employees. The goal is to support data-driven decisions that improve retention, employee satisfaction, and workforce planning.

# objective
The goal of this project is to analyze employee attrition and provide useful HR insights related to workforce distribution, employee satisfaction, work-life balance, and turnover trends. Identify departments with highest attrition, Understand age & gender trends in employee exits, Track overall employee count and quit ratio, Analyze job satisfaction and work-life balance, Make data-driven decisions to improve employee retention

# Steps Followed
1️⃣ Data Import:
 Loaded dataset into Power BI Desktop

2️⃣ Data Cleaning & Validation:
In Power Query:
Enabled Column Quality, Column Distribution, Column Profile
Switched profiling to Entire Dataset
Verified: ✅ No missing values ✅ No errors ✅ Correct data types

3️⃣ Data Modeling:
Converted Age, Monthly Income, Job Satisfaction to correct numeric type
Created calculated measures for KPIs
Built relationships between tables (if multiple tables existed)

4️⃣ Dashboard Design
Added visuals:
✅ Card KPIs → Total Employees, Employees Quit, Attrition %, Active Employees, Average Age
✅ Bar Chart → Attrition by Education
✅ Pie/Donut Chart → Attrition by Department & Age Group
✅ Clustered Column → Attrition by Age Group & Gender
✅ Matrix → Work-Life Balance by Job Role
✅ Gauge → Job Satisfaction score

5️⃣ Publishing
Report published to Power BI Service
Dashboard screenshot exported and added

# DAX Measures
1. Total Employees =
COUNTROWS(Employee)

2. Employees Quit =
CALCULATE(
    COUNTROWS(Employee),
    Employee[Attrition] = "Yes"
)

3. Active Employees =
CALCULATE(
    COUNTROWS(Employee),
    Employee[Attrition] = "No"
)

4. Attrition % =
DIVIDE([Employees Quit], [Total Employees], 0)

5. Average Age =
AVERAGE(Employee[Age])

6. Avg Job Satisfaction =
AVERAGE(Employee[JobSatisfaction])

7. Attrition by Department =
CALCULATE(
    COUNTROWS(Employee),
    Employee[Attrition] = "Yes",
    ALLEXCEPT(Employee, Employee[Department])
)

8. Male Attrition =
CALCULATE(
    COUNTROWS(Employee),
    Employee[Attrition] = "Yes",
    Employee[Gender] = "Male"
)
9. Female Attrition =
CALCULATE(
    COUNTROWS(Employee),
    Employee[Attrition] = "Yes",
    Employee[Gender] = "Female"
)
