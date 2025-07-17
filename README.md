## 🌿 Plant Co. Performance Report : Power BI Dashboard

### Project Overview
This Power BI project showcases a dynamic, interactive dashboard built to analyze and track key performance metrics — Sales, Gross Profit, and Quantity — for Plant Co.. The report is designed with SWITCH logic, dynamic visuals, and time intelligence measures to provide business stakeholders with an intuitive performance overview and actionable insights.


![PowerBI - Plant Co  Performance Report](https://github.com/user-attachments/assets/280b3b63-8650-446b-9ce7-a40a0fcf3535)



📁 Project Structure
1. Data Preparation (Power Query)

- Loaded and renamed tables (dim_ for dimensions, fact_ for facts).
- Cleaned the data: removed duplicates, renamed columns, corrected datatypes.
- Created a custom date table using:
  ```dax
  Dim_Date = CALENDAR(DATE(2022,01,01), DATE(2024,12,31))
  ```


- Added an Inpast column to identify previous year’s dates for PYTD calculations.

2. Data Modeling

- Created a Slc_Values table with toggle options: Sales, Gross Profit, Quantity.
- Developed a _Measures table with folders:
- Base Measures: Sales, Quantity, COGS, Gross Profit
- YTD / PYTD Measures: Using TOTALYTD, SAMEPERIODLASTYEAR
- SWITCH Logic for dynamic visual toggling:
```dax
S_PYTD = 
VAR selected_value = SELECTEDVALUE(Slc_Values[Values])
RETURN SWITCH(selected_value,
    "Sales", [PYTD_Sales],
    "Quantity", [PYTD_Quantity],
    "Gross Profit", [PYTD_GrossProfit]
)
```


- Built relationships between fact and dimension tables.

  3. Visuals & Layout
     
- Visuals: Cards, Tree Map, Waterfall Chart, Combo Chart, Scatter Plot (with Zoom Slider).
- Added dynamic chart titles using measures, e.g.:


```dax
_Waterfall Title = SELECTEDVALUE(Slc_Values[Values]) & " YTD vs PYTD | Month - Country - Product"
```



- Added Gross Profit %:

```dax
GP% = DIVIDE([Gross Profit], [Sales])
```

4. Review & Enhancements
   
- Measures organized in folders for better structure.
- Final polish: formatting, axis titles, conditional formatting.
- Created a dynamic report title:


```dax
_Report Title = "Plant Co. " & SELECTEDVALUE(Slc_Values[Values]) & " Performance " & SELECTEDVALUE(Dim_Date[Date].[Year])
```


5. Tools & Techniques

- Power BI (Data Modeling, DAX, Visualization)
- Power Query (Data Cleaning)
- Time Intelligence (YTD, PYTD, SAMEPERIODLASTYEAR)
- Dynamic Titles & Conditional Formatting
- SWITCH logic for custom measure selection

✅ Key Features & Outcomes

- Interactive metric selection using slicers and SWITCH logic.
- YTD vs PYTD analysis across time, geography, and product.
- Dynamic titles and visuals adjust automatically based on user input.
- Profitability insights via scatter plot segmentation and GP%.
- Stakeholder Benefits

✅ This dashboard helps Plant Co. decision-makers:

- Monitor and compare current vs past year performance.
- Identify growth areas and operational inefficiencies.
- Make faster, data-driven decisions from a concise, visually engaging report.

#### Project files are attached for reference.
