# 🏭 Supply Chain Data Model & Analytics Platform
### Spark-Wars 4.0 | Problem Statement 1 | By Shubham Dangi

---

## 🚀 Project Overview

This project implements a **end-to-end Supply Chain Analytics Platform** built on **Databricks**, using a **3-Layer Medallion Architecture** — transforming raw SAP & IBP data into powerful business insights visualized through **Power BI**.

---

## 🏗️ Architecture

```
RAW DATA (SAP + IBP)
       ↓
  🥉 BRONZE LAYER   →  Raw Delta Tables (43 tables)
       ↓
  🥈 SILVER LAYER   →  Cleaned & Transformed Data
       ↓
  🥇 GOLD LAYER     →  Star Schema (Fact + Dimension Tables)
       ↓
  📊 POWER BI       →  Interactive Dashboards & KPIs
```

---

## 📂 Repository Structure

```
├── 01_bronze_layer.ipynb       # Raw data ingestion from SAP & IBP
├── 02_silver_layer.ipynb       # Data cleaning & transformation
├── 03_gold_layer.ipynb         # Star schema & business logic
└── Supply_Chain_Report.pbix    # Power BI Dashboard
```

---

## 🥉 Bronze Layer
- Ingested **37 SAP tables** + **6 IBP tables** from CSV
- Stored as **Delta format** in `wsshubhamcontest.bronze`
- Total: **43 raw tables** loaded

## 🥈 Silver Layer
- **Duplicate removal** across all tables
- **String trimming** & **null row elimination**
- Clean data stored in `wsshubhamcontest.silver`

## 🥇 Gold Layer — Star Schema

### Fact Tables:
| Table | Description |
|-------|-------------|
| `fact_purchase_order` | PO data from EKPO + EKET |
| `fact_inventory` | Current stock from MARD + MCHB + MBEW |
| `fact_inventory_month_end_stock` | Historical batch-level stock |
| `fact_inventory_monthly_snapshot` | Monthly stock snapshots |
| `fact_demand_actual` | Actual demand & revenue |
| `fact_demand_forecast` | IBP consensus forecasts |
| `fact_batch_release_extern` | External supplier inspection lots |
| `fact_batch_release_internal` | Internal QA inspection records |

### Dimension Tables:
| Table | Description |
|-------|-------------|
| `dim_supplier` | Vendor master (LFA1 + LFM1) |
| `dim_product` | Material master (MARA + MAKT) |
| `dim_customer` | Customer master (IBP) |
| `dim_location` | Plant & location master |
| `dim_storage` | Storage location master |
| `dim_currency` | Currency exchange rates |
| `dim_date` | Date dimension |
| `dim_batch` | Batch master data |
| `dim_uom` | Unit of measure |
| `dim_customer_product` | Customer-product mapping |
| `dim_location_product` | Location-product mapping |

---

## 📊 Power BI Report

### Page 1 — Demand Analysis
- **FCA Cons Forecast** — Sales History / IBP Consensus Forecast
- **FCA IBP Forecast** — Sales History / IBP Forecast
- **Budget Attainment** — Sales History / Budget Volumes
- **FCA Lag 3 & Lag 6** — Forecast accuracy snapshots
- Trend analysis by market & period

### Page 2 — Inventory
- **40.48M** Total unrestricted stock
- Stock by plant visualization
- Material-level inventory table

### Page 3 — Purchase Orders
- **34.42bn** Total net value
- **7.59M** Total quantity
- Plant-wise PO analysis

---

## 🛠️ Tech Stack

- **Databricks** — Data Engineering & Medallion Architecture
- **Apache Spark** — Distributed data processing
- **Delta Lake** — ACID transactions & time travel
- **Power BI Desktop** — Business intelligence & visualization
- **DAX** — KPI measures & calculations
- **SAP Data** — EKKO, EKPO, MARA, LFA1, QALS and 30+ more tables
- **SAP IBP Data** — Demand actuals & forecasts

---

## 🤖 AI Assistance

> *"Behind every great data engineer is a great debugging session — and sometimes, a brilliant AI co-pilot."*

- 🔍 **Debugging** complex Spark SQL join issues
- 🏗️ **Architecting** the Gold layer data model
- 🔧 **Fixing** schema mismatches and null value problems
- 💡 **Suggesting** the right SAP column names (KTWRT, MENGE, etc.)
- 📊 **Guiding** Power BI relationship setup and DAX measures
- 🚀 **Keeping calm** when things broke at 3 AM 😄

Working with Claude felt like having a **senior data engineer** sitting right next to me — one who never gets tired, never judges, and always has an answer (even when the answer is "let's check the actual column names first!").


---

## 👨‍💻 Author

**Shubham Dangi**
- 📧 shubham19dangi@gmail.com
- 🏆 Spark-Wars 4.0 Participant

---

*Built with ❤️, ☕, and a lot of debugging at 3 AM*
