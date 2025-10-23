# 🏫 School Financial Performance Dashboard (Power BI)

### 📊 Overview
This Power BI report provides a **comprehensive financial analysis for an educational institution**, covering revenue, expenses, and profit across different academic years.  
It enables interactive comparison between periods, detailed tracking of student payments, and cost breakdowns by account and payment type.

The project demonstrates strong data modeling, DAX calculations, and clean BI design with a consistent blue-white theme inspired by Greek academic branding.

---

## 🧱 Report Pages

### 🎓 1. Student Payments (Πληρωμή Μαθητών)
![Student Payments](screenshots/Student%20payments.png)
- Displays **revenues per student** and **payment method** (cash, bank, mixed).
- Breakdown by **document type** (receipt, credit note, cancellation).
- Filters available for **academic year (Διδακτικές περίοδοι)** and **date range**.
- KPI cards summarize total **Revenue**, **Registrations**, **Profit**, and **Expenses**.

---

### 💰 2. Other Payments (Άλλες Πληρωμές)
![Other Payments](screenshots/Other%20payments.png)
- Focused on **expenses** such as salaries, invoices, and operational costs.
- Visuals show:
  - Expenses by document type (Τύπος Παραστατικού)
  - Expenses by account (Λογαριασμός)
  - Expenses by payment method (Τρόπος Πληρωμής)
- Includes a detailed table by company, academic period, and payment type.

---

### 📆 3. Comparison with Previous Years (Σύγκριση με Περσι)
![Comparison with Last Years](screenshots/Comparison%20with%20the%20last%20years.png)
- Year-over-year comparison of **Revenues (Έσοδα)** and **Expenses (Έξοδα)**.
- Dual charts for current vs previous academic years (2022-2023 and 2023-2024).
- KPI table summarizing:
  - Revenue % change YoY  
  - Expense % change YoY  
  - Profit margin variance.
- Dynamic slicers for year and date selection.

---

## ⚙️ Key Features
- **Dynamic academic year comparison** (YoY)
- **Greek-language interface** fully localized
- Clean, minimal visual design with clear KPI emphasis
- Use of DAX for previous-year metrics and percent differences
- Filter sync across pages for unified control
- Consistent branding and navigation buttons

---

## 🧮 DAX Highlights
Some of the core calculations include:
```DAX
Sales Value = SUM ( 'Financial Data'[Revenue] )
Sales Cost  = SUM ( 'Financial Data'[Expense] )
Profit      = [Sales Value] - [Sales Cost]

Sales Value LY =
CALCULATE ( [Sales Value], DATEADD ( 'Calendar'[Date], -1, YEAR ) )

Sales vs LY % =
DIVIDE ( [Sales Value] - [Sales Value LY], ABS ( [Sales Value LY] ) )
