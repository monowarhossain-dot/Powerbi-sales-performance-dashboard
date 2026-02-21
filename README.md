# 📊 Power BI: Strategic Sales & System Performance Dashboard

> **Data as a lens for strategic decision-making and understanding market ecosystems.**

This repository contains an interactive **Power BI Dashboard** that translates complex sales and operational data for a beverage brand into clear, actionable insights. Designed with a focus on usability and strategic alignment, it empowers stakeholders to visualize performance trends, identify market friction, and make informed, data-driven decisions.

---

## 🎯 The Strategic Value 

In service design and business strategy, data visualization is about reducing cognitive load for decision-makers. This dashboard goes beyond raw numbers to help leaders quickly understand the overarching business system:

- 📅 **Behavioral & Revenue Trends:** Visualizing monthly growth and seasonal shifts.
- 🗺️ **Geographic Ecosystems:** State-wise performance mapping to identify regional friction or opportunities.
- 🎯 **Strategic Alignment:** KPI comparison vs. targets to ensure the system is operating optimally.
- 🧠 **Information Architecture:** Clean visual hierarchy powered by optimized DAX and Power Query.

---

## 🖼️ Dashboard Preview

Below is a preview of the dashboard's user interface, focusing on clarity and insight generation:

![Dashboard Preview 1](https://github.com/monowarhossain-dot/Powerbi-sales-performance-dashboard/blob/main/Screenshot%20(361).png)
![Dashboard Preview 2](https://github.com/monowarhossain-dot/Powerbi-sales-performance-dashboard/blob/main/Screenshot%20(362).png)

---

## 🔗 Interactive Report (.pbix)

Experience the full interactive dashboard and underlying data model:

➡ **[Download the Strategic PBIX File](https://github.com/monowarhossain-dot/Powerbi-sales-performance-dashboard/blob/main/SALES%20DASHBOARD%20POWER%20BI.pbix)**
*(Alternate link: [Report File](https://github.com/monowarhossain-dot/Powerbi-sales-performance-dashboard/blob/main/power%20bi%20report.pbix%20().pbix))*

---

## 🧮 System Architecture & Data Modeling

Robust service solutions require a solid backend. Below is the structural logic and DAX syntax driving the dashboard's intelligence.

### Key Analytical Measures (DAX)
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
