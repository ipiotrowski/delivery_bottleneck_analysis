# Delivery Process Bottleneck Analysis  
*Built fully in Power BI*

## Project Context
This project analyzes delivery process bottlenecks in an e-commerce environment using the Brazilian E-Commerce dataset by Olist.

Instead of treating delivery delay as a single outcome, the analysis decomposes the order lifecycle into fulfillment stages to understand **where delays are introduced**, **which sellers and products drive them**, and **how stable the process is over time**.

The project is designed as an end-to-end analytics system built entirely in Power BI.

---

## Business Goal
The main objective is to identify operational bottlenecks in the delivery process and distinguish between:
- seller-driven inefficiencies,
- product-related constraints,
- and systemic logistics delays.

Key questions answered:
- Which fulfillment stages contribute most to delivery delays?
- Which sellers represent the highest operational risk?
- Are bottlenecks structural or operational?
- How stable and predictable is delivery performance over time?

---

## Data Source
**Brazilian E-Commerce Public Dataset by Olist (Kaggle)**  
https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

The dataset is publicly available and used strictly for educational and portfolio purposes.

Due to GitHub file size limitations, raw CSV files are not stored directly in this repository.  
The directory structure is preserved to document the data pipeline design.

---

## Architecture & Modeling

### Power Query (ETL)
A layered approach is applied:
- **Raw** – direct ingestion of source CSV files
- **Staging** – typing, deduplication, timestamp validation, sanity checks
- **Final** – fact and dimension tables optimized for analytics

Lead times and fulfillment stages are calculated during ETL to keep business logic outside the reporting layer.

Missing or undefined product categories are explicitly labeled as `Unclassified` to avoid hidden blanks in analysis.

---

### Data Model
The model follows a star-schema-based design with bridge tables where required.

- Order-level fact table
- Dimensions for date, sellers, products, and customers
- Bridge tables used to resolve many-to-many relationships

Bidirectional filtering is applied only where analytically necessary.

---

## Business Logic (DAX)
DAX is used strictly as a semantic and analytical layer.

Key measures include:
- Average and percentile-based delivery lead times
- Lead Time Variability Index (P90 / P50)
- Fulfillment stage contribution
- Bottleneck Severity Index

The **Bottleneck Severity Index** is a composite metric combining delivery duration, variability, and order volume (log-weighted) to highlight sellers and product categories representing the highest operational risk.

Calculated columns are avoided unless technically justified.

---

## Report Structure

### 1. Overview
High-level view of delivery performance:
- core KPIs,
- time-based trends,
- fulfillment stage contribution,
- concise executive narrative.

---

### 2. Bottleneck Drivers
Root cause analysis focusing on:
- seller bottleneck ranking,
- fulfillment stage composition by seller,
- product category impact.

This page identifies **who** and **what** drives delivery bottlenecks and serves as the main entry point for drill-through analysis.

---

### 3. Bottleneck Deep Dive (Drill-through)
A hidden diagnostic page accessible via drill-through only:
- delivery lead time trends,
- fulfillment stage evolution,
- lead time distribution,
- order volume context.

The page is intentionally excluded from navigation to preserve analytical context.

---

## Repository Contents
- Power BI report file (`.pbix`)
- Project documentation
- Report screenshots
- Data pipeline structure (raw / processed layers documented)

---

## Design Principles
- Power BI treated as an analytics platform, not a charting tool
- Clear separation between ETL, modeling, logic, and presentation
- No custom visuals
- Drill-through used instead of overcrowding main pages
- Focus on explainability and decision support

---

## Limitations & Possible Extensions
- Static, historical dataset
- No carrier-level or real-time logistics data

Potential extensions:
- SQL / Fabric-based pipelines
- Incremental refresh
- Operational alerting

---

## Final Note
This project demonstrates how Power BI can be used to build a **structured, end-to-end analytical solution**, emphasizing data modeling quality, business logic clarity, and analytical reasoning.
