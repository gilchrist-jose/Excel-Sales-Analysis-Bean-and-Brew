# Coffee Shop Sales Dashboard | Automated Refresh Pipeline

**Analyst:** Gilchrist Jose  
**Tools:** Excel | Power Query  
**Approach:** Automated data pipeline with folder-based connections  

---

## Overview

Sales dashboard for a coffee shop with automated monthly refresh capability. Uses Power Query folder connections to eliminate manual data consolidation and enable one-click updates when new monthly data arrives.

<img width="1858" height="654" alt="Screenshot 2026-03-03 221228" src="https://github.com/user-attachments/assets/915a1631-29e6-462d-8f4c-38c99e382241" />

## Business Requirements

Monthly sales monitoring dashboard with the following criteria:

- Update automatically when new monthly data exports arrive
- Accumulate historical data (append, not replace)
- Enable filtering by month, product, payment method, and day of week
- Operate without analyst intervention after initial setup
- Handle indefinite data growth

---

## Technical Implementation

### Data Pipeline Architecture

```
Monthly CSV Files (Folder) → Power Query ETL → Data Model → Dashboard
```

**Folder-based connection** monitors a designated directory and automatically combines all CSV files on refresh. New monthly files dropped into the folder are detected and appended to existing data without manual intervention.

### ETL Process (Power Query)

**Transformations applied:**
- Remove duplicate transactions
- Handle null values in Payment_Method field
- Extract Hour from transaction time
- Derive Month_Name from date
- Validate data types

**All steps execute automatically on refresh.**

### Data Model

Loaded to Excel's internal data model rather than visible worksheets for:
- Cleaner workbook structure
- Better performance with growing datasets
- Reduced file size

---

## Dashboard Components

### KPIs
- Total Revenue (AED)
- Total Sales
- Average Order Value

### Visualizations
- **Daily Revenue Trend:** Line chart showing sales over time
- **Product Performance:** Column chart of revenue by product
- **Peak Hours Analysis:** Column chart of transaction volume by hour

### Interactive Filters
- Month (compare specific months)
- Product (individual item analysis)
- Day of Week (weekday vs weekend patterns)
- Payment Method

All filters synchronized across visualizations.

---

## Refresh Workflow

**When new monthly data arrives:**

1. Export CSV from POS system
2. Save to designated folder
3. Open dashboard
4. Click Refresh All
5. Done (20-30 seconds)

Power Query automatically detects the new file, appends it to historical data, applies all transformations, and updates all visualizations.

**No manual data manipulation. No chart rebuilding.**

---

## Dataset Structure

**Monthly files contain:**
- Transaction_ID
- Date, Time, Day_of_Week
- Product, Quantity
- Unit_Price_AED, Total_Amount_AED
- Payment_Method

**Current scope:** 3 months (Jan-Mar 2025), ~500 transactions, ~AED 12,500 revenue

**Scales to:** Years of historical data without performance degradation

---

## Files

```
/
├── Bean_and_Brew_Dashboard.xlsx          # Dashboard workbook
├── Dashboard_Screenshot.png              # Visual preview
└── Sample_Data/
    ├── Bean_and_Brew_Sales_Jan2025.csv
    ├── Bean_and_Brew_Sales_Feb2025.csv
    └── Bean_and_Brew_Sales_Mar2025.csv
```

---

## Setup

**Requirements:** Excel 2016+ (Power Query support)

**Configuration:**

1. Create the designated folder
2. Place CSV files in folder
3. Open dashboard workbook
4. Refresh All

**Adding new months:** Drop CSV file in folder, click Refresh All

---

## Approach

Standard folder-based connection pattern for recurring monthly data feeds. Eliminates manual consolidation work and ensures consistency in data processing. Dashboard structure remains static while data layer updates dynamically.

This architecture is reusable for any scenario requiring monthly/periodic data appends: sales reports, financial close data, operational metrics, etc.

---

## Related Work

- [Financial Variance Analysis](https://github.com/gilchrist-jose/CloudSync-Financial-Variance-Analysis-2025) - Budget vs actual reporting with Power Query
- [Sales Performance Dashboard](https://github.com/gilchrist-jose/TechGear-Sales-Analysis-2025) - Retail analytics dashboard

---

## Contact

**Gilchrist Jose**  
📁 [GitHub](https://github.com/gilchrist-jose) | 💼 [LinkedIn](https://www.linkedin.com/in/gilchrist-jose-a96658322/) | ✉️ gill.christ11@gmail.com

---

`Excel` `Power-Query` `ETL` `Automated-Refresh` `Data-Pipeline` `Business-Intelligence`
