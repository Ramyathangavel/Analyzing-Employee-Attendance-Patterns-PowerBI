# Analyzing-Employee-Attendance-Patterns-PowerBI
![Screenshot 2024-11-14 232152](https://github.com/user-attachments/assets/de2d628e-8058-480c-8b7d-18faf8164b9d)

# Power BI HR Analytics Dashboard Project

This project showcases the use of Power Query and DAX Queries to analyze employee attendance data and create a dynamic, insightful dashboard using Power BI. The goal of this project is to provide HR professionals with valuable insights into attendance patterns and highlight areas where improvements can be made to enhance workforce management and retention.

## Tools Used
- Power BI: A powerful tool for data visualization and dashboard creation, used to aggregate and display insights from employee data.
- Power Query: Used for data cleaning, transformation, and preparation before importing data into Power BI.
- DAX (Data Analysis Expressions): A powerful formula language used to create measures and columns that enable more advanced calculations and analysis.
- Data Modeling: Structuring data in Power BI to build relationships and ensure that visualizations are accurate and meaningful.

## Steps Involved in the Project

### 1. Data Preparation Using Power Query
The first step in this project was to gather and prepare the employee attendance data. Here's how Power Query was used to transform and clean the data:

Connecting Data:
- Opened the employee attendance data in Excel and connected to it via Power BI.

Data Transformation:
In Power Query, I cleaned and transformed the data by:
- Removing duplicate rows.
- Renaming columns for clarity and consistency.
- Changing data types where necessary to ensure that data is correctly interpreted by Power BI.
- Creating parameters to filter specific conditions (e.g., employee department or attendance status).
- Encapsulating transformation steps into a reusable function for future data sets.

By applying these cleaning steps, I ensured that the data was consistent, accurate, and ready for analysis in Power BI.

### 2. Exploring and Manipulating Data Using DAX Queries
Once the data was cleaned and loaded into Power BI, I used DAX queries to create dynamic measures and calculated columns. The following DAX functions were utilized:

COUNT: To count the total number of employees, or to count the number of absentee days.
```dax
EmployeeCount = COUNT('AttendanceData'[EmployeeID])
```

SUM: To calculate the total number of attendance days or total salary expenditures.
```dax
TotalAttendanceDays = SUM('AttendanceData'[AttendanceDays])
```

CALCULATE: Used for conditional aggregations based on filters. For example, calculating the average attendance rate by department.
```dax
AvgAttendanceByDept = CALCULATE(AVERAGE('AttendanceData'[AttendanceRate]), 'AttendanceData'[Department] = "Sales")
```

IF: Applied conditional logic, for example, flagging employees with low attendance rates.
```dax
LowAttendanceFlag = IF('AttendanceData'[AttendanceRate] < 0.75, "Low", "Satisfactory")
```

SWITCH: Used for categorizing data into more than two outcomes. For example, classifying employees into different levels of absenteeism.
```dax
AbsenteeismLevel = SWITCH(TRUE(), 
                       'AttendanceData'[AbsenceDays] <= 2, "Low", 
                       'AttendanceData'[AbsenceDays] <= 5, "Medium", 
                       "High")
```

DIVIDE: Safely performs division, preventing errors when the denominator is zero.
```dax
AbsenteeismRate = DIVIDE(SUM('AttendanceData'[AbsenceDays]), COUNT('AttendanceData'[EmployeeID]), 0)
```

Date-Time Functions: Applied date-time functions to calculate metrics such as employee tenure or average attendance over time.
```dax
Tenure = DATEDIFF('AttendanceData'[HireDate], TODAY(), YEAR)
```

### 3. Power BI Dashboard Visualization
With the data prepared and measures created, I designed an intuitive dashboard to visualize key HR metrics. The dashboard was designed to be informative, interactive, and easy to navigate. Below are the components included in the dashboard:

Dashboard Layout:
- The layout was structured to present critical HR metrics at the top and provide detailed insights through visualizations and charts.
- Measure Table: I created a separate table for all calculated measures, which helped in aggregating and displaying key insights, such as the total absenteeism rate, average attendance, and employee retention.
- KPIs: Key Performance Indicators (KPIs) such as employee absenteeism rate, average attendance, and employee count were displayed using card charts to provide a quick overview.
- Slicers: Added Month slicers and Department filters to enable HR teams to view data based on specific time periods or employee departments.

Visualizations:
The following visualizations were used to provide a detailed view of employee attendance and key metrics:
- Card Charts: Displayed important KPIs, such as Total Attendance and Absenteeism Rate.
- Pie Charts: Used to show the distribution of absenteeism by department or employee gender.
- Line Charts: Used to visualize attendance trends over time.
- Table Charts: Displayed detailed employee attendance data, including individual attendance records.
- Matrix Chart: Showed attendance by department and gender, giving HR more granular insights.
- Area Chart: Tracked overall employee absenteeism trends over multiple months.

### 4. Interactivity and Filters
The dashboard includes various interactive features that allow HR to explore the data in greater depth:
- Filters: Used to segment data by department, attendance rate, or job role. This helps HR teams perform more detailed analysis.
- Dynamic Visualizations: Hovering over any chart will display tooltips with additional details, such as the exact number of absent days for a specific employee or department.

## Key Insights from the Dashboard
- Overall Attendance Trends: HR can quickly track how employee attendance has changed over time, identifying periods of increased absenteeism.
- Departmental Absenteeism: Visualize absenteeism patterns across different departments, helping HR to identify departments with consistently high absenteeism rates.
- Employee Retention: By tracking employee tenure and absenteeism, HR can gain insights into whether employees with high absenteeism are more likely to leave the organization.
- Targeted Action Plans: The dashboard can be used to identify employees or departments that require targeted HR interventions, such as wellness programs or additional support.

## Conclusion
This project demonstrates the power of using Power BI, Power Query, and DAX Queries to analyze employee attendance data and create an insightful HR dashboard. By cleaning, transforming, and modeling the data, HR teams can gain a deeper understanding of attendance patterns, employee behavior, and areas that may require attention. The interactive dashboard empowers HR to make data-driven decisions to improve employee retention, engagement, and overall workforce management.
