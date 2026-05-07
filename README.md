# Car Sales Dashboard Project

## Overview

The Car Sales Dashboard is an interactive business intelligence solution created using Power BI. It offers a detailed analysis of dealership sales performance, helping users monitor important KPIs, discover sales trends, and support data-driven business decisions. 

---

## Main Features

* **KPI Monitoring in Real Time**: Tracks important metrics such as Year-to-Date (YTD), Month-to-Date (MTD), and Year-over-Year (YOY) sales performance, average vehicle prices, and total cars sold.
* **Interactive Visual Reports**:

  * Line charts displaying weekly YTD sales trends.
  * Pie charts analyzing sales by car body style and color.
  * Map visualizations showing sales distribution by region.
  * Detailed data grids presenting company-wise sales insights and trends.
* **User-Friendly Filters and Navigation**: Allows filtering by body style, dealer region, engine type, and transmission, along with smooth page navigation for enhanced analysis. 

---

## Important DAX Calculations

### Sales Metrics

* **YTD Total Sales**

```DAX
TOTALYTD(SUM(car_data[Price ($)]), 'Calendar Table'[Date])
```

* **Previous Year YTD Sales**

```DAX
CALCULATE(SUM(car_data[Price ($)]), SAMEPERIODLASTYEAR('Calendar Table'[Date]))
```

* **Year-over-Year Growth**

```DAX
([YTD Total Sale] - [PYTD]) / [PYTD]
```

### Average Price Metrics

* **YTD Average Price**

```DAX
TOTALYTD([Avg Price], 'Calendar Table'[Date])
```

* **Average Price**

```DAX
SUM(car_data[Price ($)]) / COUNT(car_data[Car_id])
```

### Cars Sold Analysis

* **YTD Cars Sold**

```DAX
TOTALYTD(COUNT(car_data[Car_id]), 'Calendar Table'[Date])
```

### Weekly Sales Trend Highlight

* **Maximum Point Detection**

```DAX
IF(MAXX(ALLSELECTED('Calendar Table'[Week]), [Total Sale]) = [Total Sale], MAXX(ALLSELECTED('Calendar Table'[Week]), [Total Sale]), BLANK())
```
---

## Data Modeling

* Built relationships between the `Date Table` and `Calendar Table` to enable accurate time-based reporting.
* Applied DAX time intelligence functions such as `TOTALYTD`, `TOTALMTD`, and `SAMEPERIODLASTYEAR` for trend and performance analysis. 

---

## Usage Instructions

1. Open the `Car_Sales_Dashboard.pbix` file in Power BI Desktop.
2. Use available filters like dealer region or body style to customize the dashboard view.
3. Navigate through different report pages to explore detailed insights and performance summaries. 
