# 📦 Vendor Performance Analysis

> **An end-to-end data analytics project** that ingests raw vendor & sales data into a SQLite database, performs exploratory data analysis in Python, automates KPI generation, and delivers an interactive Power BI dashboard — all wrapped up in a professional PDF report.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Tech Stack](#tech-stack)
- [Dataset](#dataset)
- [Workflow](#workflow)
- [Key Features](#key-features)
- [How to Run](#how-to-run)
- [Outputs](#outputs)
- [Contact](#contact)

---

## 🔍 Overview

This project analyses vendor performance using transactional sales and purchasing data. The pipeline covers:

1. **Data Ingestion** – CSV files are loaded into a SQLite database automatically.
2. **Vendor Summary Generation** – SQL queries merge purchases, sales, and invoice tables; new KPI columns (Gross Profit, Profit Margin, Stock Turnover, Sales-to-Purchase Ratio) are engineered.
3. **Exploratory Data Analysis (EDA)** – Trends, outliers, and patterns across vendors are uncovered using Pandas, Matplotlib, and Seaborn.
4. **Dashboard** – An interactive Power BI report provides drill-down visibility into vendor KPIs.
5. **Report** – Insights are compiled into a professional PDF for stakeholder presentation.

---

## 📂 Project Structure

```
Vendor-Performance-Analysis/
│
├── data/
│   └── vendor_sales_summary.csv          # Processed vendor KPI dataset
│
├── notebooks/
│   ├── Exploratory Data Analysis.ipynb   # EDA notebook – trends, distributions, correlations
│   └── Vendor Performance Analysis.ipynb # Deep-dive vendor analysis & visualizations
│
├── scripts/
│   ├── ingestion_db.py                   # Ingests CSV files into SQLite (inventory.db)
│   └── get_vendor_summary.py             # SQL + Pandas pipeline to build vendor_sales_summary
│
├── dashboard/
│   └── vendor_performance.pbix           # Power BI interactive dashboard
│
├── reports/
│   └── Vendor Performance Report.pdf     # Final insights & recommendations report
│
├── logs/                                 # Auto-generated runtime logs (git-tracked as empty)
│   └── .gitkeep
│
├── .gitignore
└── README.md
```

---

## 🛠️ Tech Stack

| Category       | Tools / Libraries                              |
|----------------|------------------------------------------------|
| Language       | Python 3.x                                     |
| Data Wrangling | Pandas, NumPy                                  |
| Visualisation  | Matplotlib, Seaborn                            |
| Database       | SQLite3, SQLAlchemy                            |
| Notebooks      | Jupyter Notebook                               |
| BI Dashboard   | Microsoft Power BI Desktop                     |
| Reporting      | PDF (manual export)                            |

---

## 📊 Dataset

[![Kaggle](https://img.shields.io/badge/Data%20Source-Kaggle-20BEFF?style=flat&logo=kaggle&logoColor=white)](https://www.kaggle.com/datasets/shouryagupta01/vendor-performance-analysis)

> 📥 **Source:** [Vendor Performance Analysis — Kaggle Dataset](https://www.kaggle.com/datasets/shouryagupta01/vendor-performance-analysis)

The raw data consists of four related tables ingested into `inventory.db`:

| Table            | Description                                      |
|------------------|--------------------------------------------------|
| `purchases`      | Purchase orders per vendor and brand             |
| `purchase_prices`| Reference prices and volumes per brand           |
| `sales`          | Sales transactions per vendor and brand          |
| `vendor_invoice` | Freight and invoice costs per vendor             |

The `get_vendor_summary.py` script merges these into a consolidated `vendor_sales_summary` table with the following engineered KPIs:

| KPI Column              | Formula                                              |
|-------------------------|------------------------------------------------------|
| `GrossProfit`           | `TotalSalesDollars − TotalPurchaseDollars`           |
| `ProfitMargin (%)`      | `(GrossProfit / TotalSalesDollars) × 100`            |
| `StockTurnover`         | `TotalSalesQuantity / TotalPurchaseQuantity`         |
| `SalesToPurchaseRatio`  | `TotalSalesDollars / TotalPurchaseDollars`           |

---

## 🔄 Workflow

```
Raw CSVs (data/)
      │
      ▼
ingestion_db.py  ──────────────►  inventory.db  (SQLite)
                                        │
                                        ▼
                               get_vendor_summary.py
                               (SQL CTEs + Pandas cleaning)
                                        │
                                        ▼
                               vendor_sales_summary.csv
                                        │
                          ┌─────────────┴──────────────┐
                          ▼                             ▼
              Jupyter Notebooks (EDA)        Power BI Dashboard
                          │                             │
                          └──────────┬─────────────────┘
                                     ▼
                             Vendor Performance Report.pdf
```

---

## 💡 Key Features

- ✅ **Automated data ingestion** — any CSV dropped into `data/` is picked up and loaded into SQLite
- ✅ **Complex SQL CTEs** — efficient multi-table joins to build a unified vendor view
- ✅ **KPI engineering** — Profit Margin, Stock Turnover, Sales-to-Purchase Ratio computed automatically
- ✅ **Comprehensive EDA** — distributions, outliers, correlation heatmaps, vendor ranking charts
- ✅ **Interactive Power BI dashboard** — sliceable by vendor, brand, and time period
- ✅ **Structured logging** — every pipeline run is logged to `logs/` for auditability

---

## 🚀 How to Run

### Prerequisites

```bash
pip install pandas sqlalchemy matplotlib seaborn jupyter
```

### Step 1 – Ingest raw CSV data into SQLite

```bash
python scripts/ingestion_db.py
```

> Reads all `.csv` files from `data/` and loads them as tables into `inventory.db`.  
> Logs are written to `logs/ingestion_db.log`.

### Step 2 – Generate the vendor summary

```bash
python scripts/get_vendor_summary.py
```

> Runs SQL CTEs, cleans the data, engineers KPI columns, and saves the result back to `inventory.db` as the `vendor_sales_summary` table.  
> Logs are written to `logs/get_vendor_summary.log`.

### Step 3 – Exploratory Data Analysis

Open and run the notebooks in order:

```bash
jupyter notebook
```

1. `notebooks/Exploratory Data Analysis.ipynb`
2. `notebooks/Vendor Performance Analysis.ipynb`

### Step 4 – Power BI Dashboard

Open `dashboard/vendor_performance.pbix` in **Microsoft Power BI Desktop**.

### Step 5 – Final Report

See `reports/Vendor Performance Report.pdf` for the complete findings and recommendations.

---

## 📈 Outputs

| Output                          | Location                          |
|---------------------------------|-----------------------------------|
| SQLite database                 | `inventory.db` (auto-generated)   |
| Vendor KPI summary (CSV)        | `data/vendor_sales_summary.csv`   |
| EDA visualisations              | Inside Jupyter notebooks          |
| Interactive BI dashboard        | `dashboard/vendor_performance.pbix` |
| Final insights PDF              | `reports/Vendor Performance Report.pdf` |

---

## 📬 Contact

**Ashok Aryal**  
Feel free to connect or collaborate:

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/ashok-aryal/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=flat&logo=github)](https://github.com/)

---

> *If you find this project useful, please ⭐ star the repository — it helps others discover the work!*
