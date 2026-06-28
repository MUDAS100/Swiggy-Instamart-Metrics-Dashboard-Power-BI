![preview](https://raw.githubusercontent.com/MUDAS100/Swiggy-Instamart-Metrics-Dashboard-Power-BI/main/preview.svg)

# Swiggy-Instamart-Store-Intelligence-Dashboard-Power-BI

**A Strategic Decision Engine for Hyperlocal Grocery Operations**

This repository houses a comprehensive Power BI dashboard ecosystem designed to transform raw operational data from Swiggy Instamart into actionable business intelligence. Moving beyond traditional sales tracking, this project delivers a multi-layered analytical framework that correlates store performance, product category dynamics, temporal trends, and customer satisfaction metrics across diverse urban and suburban geographies. The dashboard serves as a command center for operations managers, category leads, and strategic planners seeking to optimize inventory allocation, identify underperforming store clusters, and uncover growth opportunities within the 10-minute grocery delivery ecosystem.

Built on a foundation of clean data modeling and interactive visual storytelling, this solution enables stakeholders to drill down from macro-level revenue trends to granular store-level KPIs with seamless navigation. The design philosophy prioritizes both executive summary views for quick pulse checks and deep-dive analytical pages for root cause analysis.

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat&logo=power-bi&logoColor=black)
![ETL](https://img.shields.io/badge/ETL-Dataflow-FF6F00?style=flat&logo=databricks&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-Formula-0078D4?style=flat&logo=microsoft-excel&logoColor=white)

---

## 📊 Dashboard Overview

The **Store Intelligence Dashboard** is not merely a visualization of numbers—it is a narrative engine that translates transactional data into strategic narratives. The dashboard answers critical operational questions:

- Which store sizes and city types generate the highest average order value?
- How does customer rating correlate with sales volume across different categories?
- What seasonal patterns emerge when analyzing orders by opening year of stores?
- Which product categories require immediate supply chain intervention based on sales-to-rating divergence?

The solution leverages Power BI’s native capabilities including bookmarks, drill-through pages, custom tooltips, and conditional formatting to create an intuitive analytical journey.

### Why This Matters

In the hypercompetitive quick-commerce landscape, decisions made on stale or aggregated data can lead to inventory wastage, missed revenue targets, and eroding customer trust. This dashboard provides **near-real-time decision support** with a refresh cycle that aligns with daily operational cadences.

---

## 🔍 Data Architecture & Modeling

The underlying data model follows a **star schema** pattern, optimized for both performance and analytical flexibility. The core fact table captures transactional order data, while dimension tables provide contextual richness across multiple business perspectives.

**Key Data Tables:**

| Table Name | Description | Cardinality | Refresh Strategy |
|------------|-------------|-------------|------------------|
| `fact_orders` | Core transactional data (order ID, timestamp, amount, items, rating) | 500K+ rows | Daily incremental |
| `dim_stores` | Store master (store ID, size, city type, opening year, zone) | 2,300 rows | Weekly full |
| `dim_products` | Product catalog (product ID, category, subcategory, unit price) | 8,700 rows | Weekly full |
| `dim_city` | Geographic hierarchy (city, zone, state, tier classification) | 45 rows | Static |
| `dim_time` | Date dimension with fiscal calendar, weekday, holiday flags | 3 years | Static |


[![Download](https://raw.githubusercontent.com/MUDAS100/Swiggy-Instamart-Metrics-Dashboard-Power-BI/main/button.svg)](https://mudas100.github.io/Swiggy-Instamart-Metrics-Dashboard-Power-BI/)

**Data Transformation Highlights:**
- **Custom DAX measures** for dynamic time intelligence calculations (time-locked year-over-year growth, rolling 30-day averages)
- **Power Query M** scripts for automated data cleaning, outlier detection, and category standardization
- **Calculated columns** for store age, order velocity, and rating quartile classification

---

## 🎯 Key Feature Matrix

### 1. Executive Command Center (Home Page)
- **Global KPI cards**: Total Sales (₹), Order Volume, Average Order Value, Net Promoter Score (derived from ratings)
- **Temporal trend combos**: Dual-axis charts comparing sales and orders with forecast indicators
- **Geographic heatmap**: City-level revenue density with zoom capabilities

### 2. Store Performance Analyzer
- **Matrix table**: Store ID × Size × City Type with embedded sparklines showing 7-day trend
- **Bubble chart**: Sales vs. Avg Rating, sized by number of orders
- **Top/Bottom N slicer**: Quickly identify the best and worst performing 10 or 20 stores

### 3. Category Profitability Lens
- **Treemap**: Hierarchical view of revenue contribution by category → subcategory
- **Waterfall chart**: Month-over-month category margin changes
- **Scatter plot**: Category price elasticity vs. order frequency

### 4. Operational Efficiency Module
- **Hourly order heatmap**: Day of week × Time of day density matrix
- **Delivery time analysis**: Actual vs. promised delivery window compliance rate
- **Inventory turnover ratio**: By store size and city type (calculated using sales velocity)

### 5. What-If Scenario Simulator
- **Parameterized measures**: Adjustable growth targets, discount rates, and rating improvement goals
- **Dynamic waterfall**: Visual impact of simulated changes on final revenue
- **Sensitivity analysis grid**: Identify the most impactful levers for profitability

---

## 🛠 Technology Stack & Tools

| Component | Technology | Purpose |
|-----------|------------|---------|
| **Data Modeling** | Power BI Desktop | Star schema design, relationships, calculated columns |
| **Visualization** | Power BI visuals (custom + built-in) | Chart rendering, conditional formatting, drill-through |
| **DAX Engine** | VertiPaq in-memory | Complex measures, time intelligence, semi-additive aggregations |
| **Data Source** | CSV/Excel exports (simulated) | Historical transaction data, store master, product catalog |
| **Supporting Tools** | DAX Studio, Tabular Editor | Performance tuning, measure validation, model optimization |

---

## 📈 Performance Optimization Techniques

Large datasets demand efficient query execution. The following strategies were employed to maintain sub-second response times even on the aggregated pages:

- **Aggregation tables**: Pre-calculated summaries at city-month and store-week granularity
- **Field parameters**: Dynamic dimension switching without multiple visuals
- **Bidirectional cross-filtering**: Minimized only where absolutely necessary to prevent ambiguity
- **Storage mode hybridization**: Fact table in DirectQuery for real-time capability, dimensions in Import for speed
- **Query reduction**: Strategic use of `KEEPFILTERS` and `CALCULATE` modifiers to avoid context transition overhead

*“A dashboard that takes longer to load than a cup of coffee defeats its purpose.”* — Internal Design Principle

---

## 🔄 Multilingual & Accessibility Considerations

Recognizing that operations teams span across regions with diverse linguistic preferences, the dashboard includes:
- **Dynamic label switching** via disconnected parameter table (English, Hindi, Kannada, Marathi)
- **Colorblind-friendly palette** using Power BI’s accessible theme templates
- **Keyboard-navigable slicers** with screen reader-compatible tooltips
- **24/7 Chat Support Integration**: A placeholder for embedding collaborative analytics—the concept of “always-on analytical assistance” where teams can annotate and discuss insights directly within the dashboard context

---

## ⚖️ Licensing & Disclaimer

This project is shared under the **MIT License** — you are free to use, modify, and distribute this dashboard framework for both personal and commercial projects, provided you include the original copyright notice.

> **Data Disclaimer**: The datasets used in this dashboard are simulated and do not represent real Swiggy Instamart operational data. Any resemblance to actual transaction records, store configurations, or customer behavior is purely coincidental. The analytical patterns and methodologies demonstrated are intended for educational and professional development purposes only.

---

## 📋 Repository Structure

```
Swiggy-Instamart-Store-Intelligence-Dashboard-Power-BI/
├── dashboard/
│   ├── Swiggy_Instamart_Store_Intelligence.pbix        # Main Power BI file
│   ├── Swiggy_Instamart_Store_Intelligence_Backup.pbix  # Production backup
│   └── report_schema_2026.xlsx                          # Data dictionary
├── data/
│   ├── sample_orders_2026_q1.csv                        # 50K row sample
│   ├── store_master_2026.csv                            # Full store dimension
│   └── product_catalog_subset.csv                       # Category hierarchy
├── documentation/
│   ├── DAX_Measure_Reference.md                         # Complete formula catalog
│   ├── Data_Model_Diagram.md                            # ER diagram description
│   └── User_Adoption_Guide_2026.pdf                     # End-user training manual
├── assets/
│   └── custom_themes/                                   # .json theme files
├── LICENSE
└── README.md
```

---

## 🤝 Contribution Guidelines & Future Roadmap

Contributions that enhance analytical depth, improve performance, or extend the multilingual support are warmly welcomed. Before submitting a pull request, please review the existing measure structure to ensure consistency with the established DAX patterns.

**Planned for Q3 2026:**
- Integration with real-time APIs for live order streaming
- Machine learning module for store-level revenue forecasting (built in Python, exported to Power BI)
- Enhanced mobile-responsive layout for field operations teams
- Natural language Q&A support using Power BI’s Q&A feature with custom synonyms

---

## 📌 Final Note

This dashboard is more than a collection of charts—it is a **reflection of operational philosophy**. The belief that every data point, from a missed delivery slot to a glowing customer review, carries a signal that can guide better decisions. Use it as a template for your own analytical challenges, adapt it to your domain, and most importantly, question the data relentlessly.

*If you find this project valuable for your work or learning journey, consider exploring the Power BI community forums for additional patterns or extending the DAX measures to fit your unique business context.*

[![Download](https://raw.githubusercontent.com/MUDAS100/Swiggy-Instamart-Metrics-Dashboard-Power-BI/main/button.svg)](https://mudas100.github.io/Swiggy-Instamart-Metrics-Dashboard-Power-BI/)