# Powerbi-sales-performance-dashboard
Power BI Dashboard analyzing sales and performance metrics -includes PBIX file, screenshot previews, data schema, and documentation.
# 📊 Power BI -Beverage Brand Sales Dashboard

This repository contains an interactive *Power BI Dashboard* analyzing the sales performance of a beverage brand.  
It highlights *monthly revenue trends, **state-wise performance, and **key business metrics* using clean visuals and optimized DAX calculations.

---

## 🖼 Dashboard Preview

Below is a preview of the dashboard included in this project:

![Dashboard Preview](assets/dashboard-screenshot.png)

---

## 🔗 Download Report (.pbix)

Click below to download the report:

➡ *[Download PBIX File](https://github.com/monowarhossain-dot/Powerbi-sales-performance-dashboard/blob/main/SALES%20DASHBOARD%20POWER%20BI.pbix )*

---

## 📝 Project Overview

This dashboard is designed to help business leaders and recruiters quickly understand:

- 📅 *Sum of Revenue by Month Name*  
- 🗺 *Sum of Revenue by State*  
- 📈 *Overall performance trends*  
- 🏷 *Top categories and SKUs*  
- 🎯 *KPI comparison vs targets*  
- 🧠 *Insightful design using DAX + Power Query*



---

## 🧮 Key DAX Measures Used

```DAX
Total Revenue = SUM( Sales[Revenue] )

Total Units = SUM( Sales[UnitsSold] )

Revenue By State = 
CALCULATE(
    [Total Revenue],
    ALLEXCEPT( Sales, Sales[State] )
)

Revenue (Month) = 
CALCULATE(
    [Total Revenue],
    VALUES('Date'[MonthName])
)

MoM Growth % = 
VAR PrevMonthRevenue =
    CALCULATE( [Total Revenue], DATEADD('Date'[Date], -1, MONTH) )
RETURN
IF( ISBLANK(PrevMonthRevenue), BLANK(),
    DIVIDE( [Total Revenue] - PrevMonthRevenue, PrevMonthRevenue )
)
Fact Table:
- Sales

Dimension Tables:
- Date
- Product
- Category
- Region (State)

Relationships:
Date[Date] → Sales[Date]
Product[ProductID] → Sales[ProductID]
Region[State] → Sales[State]

## Author
*Md. Monowar Hossain*
Aspiring Data Analyst | Research Enthusiast | MBA in Marketing
Specializing in Data Analytics, Tableau, Power BI & Digital Marketing

- Email: monowar.bba@gmail.com  
- LinkedIn: https://www.linkedin.com/in/monowar-hossain-278460225
