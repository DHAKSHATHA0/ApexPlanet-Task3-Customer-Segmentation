# Customer Segmentation & Sales Intelligence Report

**Internship:** ApexPlanet 60-Day Data Analytics Internship\
**Task:** Task 3 -- Deep-Dive Analysis & Interactive Dashboarding\
**Tools:** Python, Pandas, Matplotlib, MySQL, Power BI

## 1. Executive Summary

This project analyzes customer transaction data using RFM (Recency,
Frequency, Monetary) analysis. Customers are grouped according to their
purchase recency, transaction-row frequency, and total spending. The
analysis classifies 947 customers into five rule-based segments and
compares customer counts and revenue contribution.

## 2. Business Problem

The objective is to understand customer purchasing behavior, identify
customer groups that may need re-engagement, compare revenue
contribution across segments, and present findings in an interactive
Power BI dashboard.

## 3. Dataset Overview

  Attribute                              Value
  ------------------------------- ------------
  Transaction records                    1,000
  Columns                                   12
  Unique customers                         947
  Distinct Order_ID values                 992
  Missing values after cleaning              0
  Exact duplicate rows                       0
  Earliest order date               2025-01-01
  Latest order date                 2026-01-01

Fields used include `Customer_ID`, `Order_ID`, `Order_Date`, and
`Total_Sales`.

**Data-quality note:** `ORD100050` occurs nine times across different
customers and dates. Therefore, distinct `Order_ID` counts are not
reliable for calculating customer purchase frequency. This anomaly was
documented rather than silently corrected.

## 4. Data Preparation and Validation

The cleaned dataset was loaded using Pandas. Validation included
checking dimensions, missing values, exact duplicate rows, date types,
repeated order IDs, and the relationship
`Total_Sales = Quantity × Unit_Price`. The cleaned dataset contained no
missing values or exact duplicate rows.

## 5. Core Business KPIs

  ------------------------------------------------------------------------
  KPI                   Definition                                  Result
  --------------------- --------------------- ----------------------------
  Total Customers       Distinct count of                              947
                        Customer_ID           

  Repeat Customer Rate  Customers with more                          5.49%
                        than one transaction  
                        row / total customers 
                        × 100                 

  Average Purchase      Transaction rows /                            1.06
  Frequency             total customers       

  Average Customer      Average                               ₹1,47,201.10
  Spend                 customer-level        
                        monetary total        

  Average Recency       Average days since                     178.78 days
                        last purchase         
  ------------------------------------------------------------------------

The recency reference date is **2026-01-02**, one day after the latest
transaction date. Frequency is based on transaction-row counts, not
distinct Order_ID counts.

## 6. RFM Methodology

-   **Recency:** Days between the reference date and the customer's most
    recent purchase.
-   **Frequency:** Number of transaction rows associated with the
    customer.
-   **Monetary:** Sum of `Total_Sales` for the customer.

Recency and Monetary scores were assigned using quintile-based ranking.
Frequency scores used a custom rule adapted to the dataset: 1
transaction row = 1, 2 rows = 3, and 3 or more rows = 5.

The combined score is:

`RFM_Score = R_Score + F_Score + M_Score`

### Rule-based segments

-   **At Risk / Inactive:** R score ≤ 2.
-   **Recent One-time Customers:** R score ≥ 4 and F score = 1.
-   **Loyal Customers:** R score ≥ 3 and F score ≥ 3.
-   **Champions:** R score ≥ 4, F score ≥ 3, and M score ≥ 4.
-   **Needs Attention:** Customers not assigned to the preceding
    categories.

These are project-specific descriptive rules, not universal RFM
definitions or a predictive churn model.

## 7. Customer Segmentation Results

  Customer Segment              Customers          Total Revenue   Revenue Share
  --------------------------- ----------- ---------------------- ---------------
  At Risk / Inactive                  379        ₹5,32,38,182.48          38.19%
  Recent One-time Customers           341        ₹4,74,69,097.81          34.05%
  Needs Attention                     181        ₹2,51,06,970.09          18.01%
  Champions                            30        ₹1,00,87,602.81           7.24%
  Loyal Customers                      16          ₹34,97,586.46           2.51%
  **Total**                       **947**   **₹13,93,99,439.65**     **100.00%**

Percentages may differ slightly from 100% due to rounding.

## 8. Key Findings and Business Interpretation

### At Risk / Inactive

This is the largest segment, with 379 customers, and contributes 38.19%
of revenue. Its average recency is approximately 289.55 days. A targeted
re-engagement campaign could be tested with this group.

### Recent One-time Customers

This segment contains 341 customers and contributes 34.05% of revenue.
Its average recency is approximately 68.17 days, and its average
frequency is one transaction row. Follow-up offers or complementary
product recommendations could be tested to encourage a second purchase.

### Needs Attention

This segment contains 181 customers and contributes 18.01% of revenue.
Its average recency is approximately 179.59 days. Further analysis of
product and customer characteristics may help identify relevant
engagement actions.

### Champions

This segment contains 30 customers and contributes 7.24% of revenue. Its
average frequency is approximately 2.03 transaction rows and average
recency is approximately 57.30 days. Loyalty benefits and personalized
recommendations could be considered.

### Loyal Customers

This segment contains 16 customers and contributes 2.51% of revenue. Its
average frequency is 2.00 transaction rows. The small segment size means
conclusions should be treated cautiously.

## 9. Power BI Dashboard

The report is designed with two pages:

### KPI Overview

-   Total Customers
-   Repeat Customer Rate
-   Average Purchase Frequency
-   Average Customer Spend
-   Average Recency

### Customer Segmentation

-   Customer distribution by RFM segment
-   Revenue contribution by customer segment
-   Average recency by segment
-   Average purchase frequency by segment
-   Customer-level RFM details
-   Segment slicer
-   Last-purchase date slicer

Add the final dashboard screenshot to `images/dashboard_screenshot.png`
and the Power BI file to the `powerbi/` folder. Add a live report link
only if the report has been published and the link is accessible.

## 10. Recommendations

1.  Test re-engagement campaigns for customers with high recency values.
2.  Encourage second purchases among recent one-time customers.
3.  Consider loyalty benefits for Champions.
4.  Investigate product and location patterns within the Needs Attention
    segment.
5.  Track repeat purchases over a longer period before making strong
    retention or churn claims.
6.  Evaluate campaign outcomes using repeat-purchase rate, revenue per
    customer, and recency.

These are recommendations for testing, not measured campaign outcomes.

## 11. Limitations

-   Only 52 customers have more than one transaction row; most customers
    have only one recorded transaction.
-   Frequency uses transaction-row count because of the repeated
    Order_ID anomaly.
-   The dataset covers January 1, 2025, to January 1, 2026.
-   Recency values use January 2, 2026 as the reference date and are
    tied to that date.
-   Segment labels are based on selected business rules.
-   "At Risk / Inactive" is a recency-based classification; it does not
    prove that a customer has churned.
-   The analysis does not prove that recommended campaigns will improve
    revenue or retention.

## 12. Conclusion

This project demonstrates a customer segmentation workflow using Python,
Pandas, RFM analysis, and Power BI. It classifies 947 customers into
five segments and compares their customer counts, recency, frequency,
and revenue contribution. The findings highlight opportunities to
investigate customer re-engagement and encourage repeat purchases.

------------------------------------------------------------------------

**Internship Organization:** ApexPlanet Software Pvt. Ltd.\
**Internship:** 60-Day Data Analytics Internship\
**Task:** Task 3 -- Deep-Dive Analysis & Interactive Dashboarding\
**Project:** Customer Segmentation & Sales Intelligence Dashboard
