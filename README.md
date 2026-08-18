# Olist Brazilian E-Commerce Analytics

**Power BI · DAX · Excel · Business Analytics**

An end-to-end business analytics project using the **Brazilian E-Commerce Public Dataset by Olist**, developed to evaluate marketplace performance across sales, customers, products, sellers, delivery operations, customer reviews, and repeat purchasing.

The project follows a structured analytics workflow from **data auditing and transformation through data modeling, DAX measure development, dashboard design, validation, and portfolio documentation**.

---

## Project Overview

The objective was to turn a multi-table e-commerce dataset into a controlled analytical model and business-focused Power BI dashboard.

Rather than beginning with visualizations, the project first established:

* Data quality and table-grain integrity
* Business questions and metric definitions
* Data cleaning and transformation rules
* Analytical table design
* Power BI relationships and model validation
* DAX measures and KPI validation
* Dashboard structure and visual QA

The final dashboard was designed around **12 approved business questions** and organized into three analytical pages.

---

## Business Questions

The analysis was structured around the following approved questions.

### Sales & Marketplace Performance

**Q1.** How are order volume and sales value changing over time?

**Q2.** Which product categories contribute the most sales value and unique orders?

**Q3.** Which customer states contribute the most sales value and unique orders?

**Q4.** Which sellers have high sales contribution, and how does their delivery/customer experience compare?

### Delivery & Operational Performance

**Q5.** What is the typical customer delivery time, and how does it vary?

**Q6.** What percentage of delivered orders miss the estimated delivery date, and by how much?

**Q7.** Which factors are associated with higher late-delivery rates?

### Customer Experience

**Q8.** Is late delivery associated with lower customer review scores?

**Q9.** Which product categories are associated with lower customer review scores?

**Q11.** What proportion of customers made repeat purchases during the observed period?

### Supporting & Synthesis Analysis

**Q10.** How do customers use different payment methods and installment options?

**Q12.** Which high-sales sellers or categories show weaker delivery or customer-experience performance?

Q10 was classified as **low priority**, while the core analytical focus was placed on sales, delivery, late delivery, customer experience, repeat purchasing, and high-sales/weak-performance areas.

---

## Dataset

**Source:** Brazilian E-Commerce Public Dataset by Olist

The dataset contains multiple related tables covering customers, orders, order items, payments, reviews, products, sellers, geolocation, and category translation.

**Source:** [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

The original raw source files were retained separately during the project. The cleaned analytical workbook and raw CSV files are **not hosted in this repository**; the repository focuses on the analytical output and portfolio documentation.

---

## Data Audit & Quality

Before transformation, all **9 source tables** were audited for:

* Row counts and table grain
* Keys and cardinality
* Missing values
* Exact duplicates
* Data types
* Date validity
* Cross-table integrity
* Major data-quality issues

Several issues were documented and carried forward deliberately rather than being blindly deleted or filled.

Examples included:

* Duplicate geolocation records
* Mixed ZIP/CEP data types
* Missing order lifecycle timestamps
* Missing product attributes
* Payment anomalies
* Multiple review records for some orders
* Untranslated product categories

The audit confirmed that the core transaction relationships contained **zero unmatched/orphan records** across the major relationships tested.

---

## Data Preparation & Transformation

The cleaned data was maintained as **separate tables rather than flattened into a single dataset**, preserving the natural grain of each source table.

Key transformations included:

* Standardizing identifiers and data types
* Treating ZIP/CEP values as text identifiers
* Preserving legitimate missing values
* Creating an order-level review table
* Creating delivery-performance fields
* Creating customer order-count analysis
* Creating repeat-customer analysis
* Preserving source anomalies where analytical justification for deletion did not exist

### Derived Analytical Fields

The `Orders_Analysis` table contains:

* `delivery_days`
* `delivery_eligible_flag`
* `late_delivery_flag`
* `days_late`

A separate customer analysis layer was also created to evaluate order frequency and repeat purchasing using `customer_unique_id`.

The transformation stage passed QA checks for row counts, key integrity, data types, null handling, delivery logic, repeat-customer logic, and row multiplication.

---

## Power BI Data Model

The final Power BI model was deliberately built rather than relying on automatically detected relationships.

The model contains **10 intentional active relationships**, including:

* Customers → Orders
* Orders → Order Items
* Products → Order Items
* Sellers → Order Items
* Orders → Payments
* Orders → Reviews
* Category Translation → Products
* Customers → Customer Repeat Analysis
* Orders ↔ Orders Analysis
* Orders ↔ Reviews Order Level

The model was validated for cardinality, filter behavior, key association, and unintended many-to-many relationships before DAX development.

### Data Model

![Power BI Data Model](Images/Data_Model_Relationships.png)

### Relationship Details

![Power BI Relationship Details](Images/Relationship_Details.png)

---

## DAX & KPI Layer

The DAX layer was developed after the analytical model was validated.

**16 measures** were created and validated with no DAX errors or evidence of unintended double-counting.

### Validated KPIs

| KPI                   |          Result |
| --------------------- | --------------: |
| Total Orders          |          99,441 |
| Total Customers       |          96,096 |
| Total Products        |          32,951 |
| Total Sellers         |           3,095 |
| Total Sales Value     | R$13,591,643.70 |
| Total Freight         |  R$2,251,909.54 |
| Total Payment Value   | R$16,008,872.12 |
| Average Order Value   |        R$136.68 |
| Average Delivery Days |           12.56 |
| Late Orders           |           6,534 |
| Late Delivery Rate    |            6.8% |
| Average Days Late     |           10.62 |
| Repeat Customers      |           2,997 |
| Repeat Customer Rate  |            3.1% |
| Average Review Score  |        4.09 / 5 |
| Reviewed Orders       |          98,673 |

**Important:** Sales Value is based on `Order Items[price]` and is treated as **Sales Value/GMV**, not accounting revenue.

---

# Dashboard

The final Power BI dashboard contains **three analytical pages**, following an executive → sales/customer → operations/delivery flow. Stage 6 was completed and approved after dashboard, visual, usability, and business-question QA.

---

## 1. Executive Overview

A high-level view of marketplace performance covering:

* Total Sales
* Total Orders
* Average Order Value
* Total Payment Value
* Total Customers
* Repeat Customer Rate
* Average Delivery Days
* Late Delivery Rate
* Sales & Orders Over Time
* Overall Order Delivery Status

![Executive Overview](Images/Executive_Overview.png)

---

## 2. Sales & Customer Analysis

This page focuses on commercial performance and customer experience.

Key analyses include:

* Lowest-Rated Product Categories
* Order Distribution by Payment Type
* Top States by Average Order Value
* Sales & Orders by State
* Repeat vs One-Time Customers
* Average Review Score by Delivery Status
* Top 10 Sellers: Sales vs Late Delivery Rate

![Sales & Customer Analysis](Images/Sales_Customer_Analysis.png)

---

## 3. Operations & Delivery Analysis

This page focuses on delivery performance and operational problem areas.

Key analyses include:

* Top 10 States by Late Delivery Rate
* Late Orders by Delay Severity
* Average Delivery Days Over Time
* Top 10 States by Late Orders
* Top 10 States by Average Days Late
* Order Volume vs Average Delay by State

Late orders are grouped into:

* 1–3 days
* 4–7 days
* 8–14 days
* 15+ days

![Operations & Delivery Analysis](Images/Operations_Delivery_Analysis.png)

---

## Analytical Workflow

```text
Brazilian E-Commerce Dataset
            ↓
       Data Audit
            ↓
   Business Questions
            ↓
Data Cleaning & Transformation
            ↓
    Analytical Tables
            ↓
  Power BI Data Modeling
            ↓
       DAX Measures
            ↓
      KPI Validation
            ↓
   Dashboard Development
            ↓
 Dashboard QA & Review
            ↓
    Portfolio Packaging
```

The workflow was intentionally designed so that **business questions and metric definitions were established before dashboard construction**.

---

## Key Analytical Principles

Several decisions were made to keep the analysis defensible:

* Missing values were not automatically treated as zero.
* Source anomalies were not deleted simply because they looked unusual.
* Delivery metrics use eligible delivered orders with valid delivery timestamps.
* Late delivery findings are interpreted as **associations, not causal claims**.
* Orders without reviews are not treated as zero-star reviews.
* Repeat purchasing uses `customer_unique_id`.
* Seller and category performance is evaluated through separate sales, order, delivery, and review metrics rather than an arbitrary composite score.
* Multiple review records per order were handled through an order-level average review score.

---

## Tools & Technologies

* **Power BI** — Dashboard development, data modeling and visualization
* **DAX** — KPI and analytical measure development
* **Microsoft Excel** — Data preparation and transformation
* **GitHub** — Version control and portfolio documentation

---

## Repository Structure

```text
olist-brazilian-ecommerce-analytics/
│
├── Dashboard/
│   ├── Olist_Analytics_Dashboard_Portfolio.pbix
│   └── Olist_Analytics_Dashboard_Portfolio.pdf
│
├── Images/
│   ├── Data_Model_Relationships.png
│   ├── Relationship_Details.png
│   ├── Executive_Overview.png
│   ├── Sales_Customer_Analysis.png
│   └── Operations_Delivery_Analysis.png
│
├── .gitattributes
└── README.md
```

The repository contains the final Power BI dashboard files and visual documentation required to review the project without requiring access to the original source dataset.

---

## Project Status

**Completed & Approved**

The project progressed through data auditing, business-question definition, transformation, modeling, DAX validation, dashboard design, visual QA, and GitHub portfolio packaging.

The final dashboard was reviewed against the **12 approved business questions** and finalized as a three-page Power BI analytical product.

---

## Author

**Abishek Ragu**

Data Analyst | Business Analyst

[GitHub Profile](https://github.com/Abishekragu) · [LinkedIn](https://www.linkedin.com/in/rabishekragu23/)

Chennai, Tamil Nadu, India
