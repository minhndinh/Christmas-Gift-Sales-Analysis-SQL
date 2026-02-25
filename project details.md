# 🎄 Christmas Gift Sales Analysis

## Details

### 🔄 Workflow

```
Xmas_Dataset.xlsx  →  Azure SQL Database  →  Data Exploration  →  Data Analysis
```

1. **Excel Dataset** — raw sales data stored in `Xmas_Dataset.xlsx`, uploaded directly to the repo
2. **Azure SQL Database** — file imported into Azure to enable SQL querying across 3 tables (`xmas_sales`, `country`, `purchase_type`)
3. **Data Dictionary** — created to document all tables, columns, and field descriptions for reference
4. **Data Exploration** (`data_exploration.sql`) — understand data structure, value ranges, and distributions; build a time-enriched view as the foundation for analysis
5. **Data Analysis** (`data_analysis.sql`) — run business queries on top of the view to extract insights

---

## Goals

### 📁 `data_exploration.sql`
Explores the structure and value distribution across all analysis dimensions:
- **Time** — year range (2018–2022), months (Nov/Dec/Jan), Christmas season labels, day of week, hour of day
- **Geography** — 10 countries, 36 cities
- **Customer** — 3 age groups, gender
- **Product** — 13 categories, 18 products
- **Others** — 3 purchase types (In-store, Online, Xmas Market), 5 payment methods, 3 budget segments (Low/Medium/High)

Also creates a **time-enriched view** `dbo.v_xmas_sales` that adds `xmas_year`, `xmas_season`, `weekday`, `weekday_name`, and `hour` to every transaction row — used as the base for all analysis queries. Note: incomplete season 2017–2018 is excluded from the view.

### 📊 `data_analysis.sql`
9 analysis queries built on top of `v_xmas_sales`:

| # | Question |
|---|---|
| 1 | Revenue, quantity, cost, and profit by Christmas season |
| 2 | YoY revenue growth rate across seasons |
| 3 | Revenue and contribution % by purchase channel per season |
| 4 | Revenue by country and city |
| 5 | Country ranking by revenue and revenue growth in each season |
| 6 | Revenue proportion by age group, gender, and purchase type |
| 7 | Purchase channel and payment method preference by age group |
| 8 | Revenue, profit, and margin by product category and product |
| 9 | Shopping day preference by gender; time-of-day distribution |
