
# Customer Segmentation & Sales Intelligence Dashboard

An end-to-end Customer Segmentation and Business Intelligence project developed as part of the **ApexPlanet 60-Day Data Analytics Internship – Task 3**.

This project uses **RFM (Recency, Frequency, Monetary) Analysis** to segment customers based on purchasing behavior and identify opportunities to improve customer engagement, repeat purchases, and revenue.

## Project Overview

Businesses need to understand not only how much revenue they generate but also which customers contribute to it.

This project analyzes customer transaction data, calculates RFM metrics, assigns customer segments, and presents actionable business insights through an interactive Power BI dashboard.

## Objectives

- Define and calculate key business KPIs.
- Perform customer-level RFM analysis.
- Segment customers based on purchasing behavior.
- Analyze revenue contribution across customer segments.
- Build an interactive Power BI dashboard.
- Derive actionable business recommendations.

## Tech Stack

| Technology | Purpose |
|---|---|
| Python | Data processing and RFM analysis |
| Pandas | Data manipulation and aggregation |
| Matplotlib | Data visualization |
| MySQL | Business data analysis |
| Power BI | Interactive dashboard development |
| GitHub | Project documentation and version control |

## Dataset Overview

The cleaned sales dataset contains:

- **1,000** transaction records
- **12** columns
- **947** unique customers
- Transaction dates from January 1, 2025, to January 1, 2026
- No missing values after cleaning

### Key Attributes

`Customer_ID`, `Order_Date`, `Age`, `Gender`, `City`, `Product`, `Category`, `Quantity`, `Unit_Price`, and `Total_Sales`.

## Business KPIs

Five core KPIs were calculated:

| KPI | Result |
|---|---:|
| Total Customers | 947 |
| Repeat Customer Rate | 5.49% |
| Average Purchase Frequency | 1.06 |
| Average Customer Spend | ₹1,47,201.10 |
| Average Recency | 178.78 days |

## RFM Analysis

RFM stands for:

- **Recency:** Number of days since the customer's last purchase.
- **Frequency:** Number of transaction records associated with the customer.
- **Monetary:** Total amount spent by the customer.

Each customer receives an RFM score and is assigned to a segment using rule-based classification.

### Customer Segmentation Results

| Customer Segment | Customers | Revenue Contribution |
|---|---:|---:|
| At Risk / Inactive | 379 | 38.19% |
| Recent One-time Customers | 341 | 34.05% |
| Needs Attention | 181 | 18.01% |
| Champions | 30 | 7.24% |
| Loyal Customers | 16 | 2.51% |
| **Total** | **947** | **100%** |

## Key Business Insights

1. **At Risk / Inactive:** This segment contains 379 customers and contributes 38.19% of total revenue. Targeted re-engagement campaigns could encourage future purchases.

2. **Recent One-time Customers:** 341 customers belong to this segment. Follow-up offers and personalized recommendations may encourage repeat purchases.

3. **Champions:** 30 customers have strong RFM scores. Loyalty rewards and personalized experiences could help retain them.

4. **Needs Attention:** 181 customers fall into this segment and may benefit from targeted engagement strategies.

5. **Loyal Customers:** Only 16 customers belong to this segment, highlighting an opportunity to strengthen repeat-purchase behavior.

## Power BI Dashboard

The interactive dashboard includes:

- Customer distribution by RFM segment
- Revenue contribution by customer segment
- Average recency analysis
- Average purchase frequency analysis
- Customer-level RFM details
- Segment and purchase-date slicers
- KPI overview

### Dashboard Screenshots

Add your dashboard screenshots inside the `images/` folder and display them here.

![Customer Segmentation Dashboard](images/dashboard_screenshot.png)

## Project Structure

```text
ApexPlanet-Task3-Customer-Segmentation/
│
├── data/
│   ├── cleaned_sales_dataset.csv
│   └── customer_rfm_segments.csv
│
├── notebooks/
│   └── customer_segmentation.ipynb
│
├── powerbi/
│   └── Customer_Segmentation_Sales_Intelligence.pbix
│
├── reports/
│   └── customer_segmentation_report.md
│
├── images/
│   └── dashboard_screenshot.png
│
└── README.md
```

## Methodology

1. Dataset loading and validation.
2. Customer-level aggregation.
3. Calculation of Recency, Frequency, and Monetary values.
4. RFM scoring and rule-based segmentation.
5. Segment-level customer and revenue analysis.
6. Interactive Power BI dashboard development.
7. Business insight generation.

## Dataset Limitations

- Only 52 customers have more than one transaction record.
- Frequency is calculated using transaction row counts because repeated Order_ID values make distinct Order_ID counts unreliable for customer-level frequency.
- The dataset contains a repeated Order_ID anomaly that was documented rather than silently corrected.
- The reference date for recency calculation is January 2, 2026.
- Segment labels are based on selected business rules and do not represent a predictive churn model.
- Customer retention and long-term loyalty cannot be conclusively established from this limited repeat-purchase history.

## Conclusion

This project demonstrates how customer transaction data can be transformed into meaningful business intelligence using Python, RFM analysis, and Power BI.

The analysis identifies customer segments, evaluates their revenue contribution, and highlights opportunities for customer engagement and repeat-purchase improvement.

## Internship

**ApexPlanet Software Pvt. Ltd.**  
