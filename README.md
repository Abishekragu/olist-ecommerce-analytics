# Olist E-Commerce Sales & Customer Analytics Dashboard

A Power BI business intelligence project analyzing the Brazilian Olist e-commerce marketplace to understand sales performance, customer behavior, product and seller performance, and delivery operations.

## Project Overview

This project was developed as a practical data analytics portfolio project using the Brazilian E-Commerce Public Dataset by Olist.

The objective was to transform raw e-commerce data into an interactive Power BI dashboard that provides a structured view of commercial performance, customer behavior, and delivery operations.

The analysis is organized into three dashboard pages:

1. Executive Overview
2. Sales & Customer Analysis
3. Operations & Delivery Analysis

The project covers the complete analytical workflow from data preparation and transformation through data modeling, measure creation, visualization, and business interpretation.

---

## Business Objective

The purpose of the analysis is to provide a consolidated view of Olist's marketplace performance and identify areas that may require business attention.

The dashboard focuses on questions such as:

- How are overall sales and order volumes performing?
- How do sales and orders change over time?
- Which payment methods are most frequently used?
- What proportion of customers are repeat customers?
- Which states generate the highest sales and order volumes?
- Which states have higher average order values?
- Which product categories receive lower review scores?
- How does seller sales performance relate to late delivery rates?
- Which states experience higher late-delivery rates?
- How severe are late-order delays?
- How does delivery performance change over time?
- Which states have higher average delivery delays?
- Is there a relationship between order volume and delivery delays?

---

## Dataset

The project uses the **Brazilian E-Commerce Public Dataset by Olist**, obtained from Kaggle.

**Source:** Kaggle — Brazilian E-Commerce Public Dataset by Olist

The dataset contains multiple related tables covering:

- Customers
- Orders
- Order Items
- Payments
- Reviews
- Products
- Sellers
- Product Category Translations
- Geolocation

The raw data was prepared and transformed for analytical use before being modeled in Power BI.

---

## Data Preparation & Transformation

The project involved preparing the source data for analysis by:

- Reviewing the structure and contents of the source tables
- Cleaning and organizing the datasets
- Preparing fields required for analysis
- Handling data types and analytical fields
- Creating relationships between relevant datasets
- Preparing calculated measures for business metrics
- Structuring the data model for Power BI reporting

The cleaned data was then used as the foundation for the dashboard analysis.

---

## Data Model

The analysis combines multiple Olist datasets to connect different aspects of the e-commerce business, including:

- Customer information
- Order information
- Product information
- Seller information
- Payment information
- Review information
- Delivery information
- Product category information

This structure enables analysis across sales, customers, products, sellers, payments, reviews, and delivery performance.

---

# Dashboard

## 1. Executive Overview

The Executive Overview provides a high-level summary of marketplace performance.

### Key Performance Indicators

- Total Sales
- Total Orders
- Average Order Value
- Total Payment Value
- Total Customers
- Repeat Customer Rate
- Average Delivery Days
- Late Delivery Rate

### Visual Analysis

- Sales & Orders Over Time
- Order Delivery Status

This page is designed to provide a quick understanding of the overall business position before moving into detailed analysis.

---

## 2. Sales & Customer Analysis

This page focuses on commercial performance and customer behavior.

### Analysis Included

- Lowest-Rated Product Categories
- Order Distribution by Payment Type
- Top States by Average Order Value
- Sales & Orders by State
- Repeat vs One-Time Customers
- Average Review Score by Delivery Status
- Top 10 Sellers: Sales vs Late Delivery Rate

The page helps identify differences in customer behavior, state-level sales performance, product satisfaction, payment preferences, and seller performance.

---

## 3. Operations & Delivery Analysis

This page focuses on logistics and delivery performance.

### Analysis Included

- Top 10 States by Late Delivery Rate
- Late Order Delay Severity
- Average Delivery Days Over Time
- Top 10 States by Late Orders
- Top 10 States by Average Days Late
- Order Volume vs Average Delay by State

The analysis helps identify geographic areas with higher delivery issues and examines the relationship between order volume and delivery performance.

---

# Key Metrics

The dashboard includes business metrics such as:

| Metric | Purpose |
|---|---|
| Total Sales | Measures overall sales value |
| Total Orders | Measures order volume |
| Average Order Value | Measures average value per order |
| Total Customers | Measures customer base size |
| Repeat Customer Rate | Measures customer retention behavior |
| Average Delivery Days | Measures delivery duration |
| Late Delivery Rate | Measures the proportion of late deliveries |
| Average Review Score | Measures customer satisfaction through reviews |

---

# Tools & Technologies

- **Power BI** — Data modeling, DAX measures, dashboard development and visualization
- **Microsoft Excel** — Data preparation and supporting analysis
- **GitHub** — Version control and portfolio presentation
- **DAX** — Business calculations and analytical measures

---

# Project Workflow

The project followed a structured analytics workflow:

```text
Raw Olist Dataset
       ↓
Data Preparation
       ↓
Data Cleaning & Transformation
       ↓
Data Modeling
       ↓
Calculated Measures
       ↓
Business Analysis
       ↓
Power BI Visualizations
       ↓
Dashboard Review & Validation
       ↓
Portfolio Documentation