# ☕ Starbucks Insights Dashboard (Power BI)

An interactive Power BI dashboard analyzing Starbucks' beverage nutrition
and global store footprint.

## Business Questions
- Which beverages and categories have the highest caffeine?
- How do calories and sugar vary across beverage categories?
- Where are Starbucks stores located, and how are they distributed by country?

## Datasets
| File | Description | Size |
|---|---|---|
| `starbucks.csv` | Beverage nutrition by size and prep (calories, sugar, caffeine, etc.) | 242 rows, 33 beverages, 9 categories |
| `directory.csv` | Global store locations (brand, ownership type, country, lat/long) | ~25,600 stores, 73 countries |

## Tools
Power BI Desktop, Power Query (M), DAX

## Data Cleaning (Power Query)
- Trimmed stray spaces from column headers
- Converted `Caffeine (mg)` from text to number; replaced "Varies" with null
- Removed error rows, keeping zero-caffeine drinks (valid data)
- Documented a bug I fixed: a filter that kept only rows where caffeine = 0

## Data Model and DAX
- Example measure: `Avg Caffeine - Coffee = CALCULATE(AVERAGE(starbucks[Caffeine (mg)]), starbucks[Beverage_category] = "Coffee")`
- KPI measures: Total Beverages, Avg Calories, Avg Sugar, Avg Caffeine
- Used **Average** instead of Sum, because the table has one row per size/prep and a sum would inflate drinks with many variations

## Key Insights
- Brewed Coffee has the highest average caffeine (about 294 mg), followed by Caffè Americano (about 188 mg)
- Coffee is the highest-caffeine category (293.75 mg average), well ahead of Classic Espresso (122.07 mg)

## Dashboard Features
- KPI cards, category and beverage-level caffeine charts, donut chart, global presence visual
- Slicers for protein range and beverage prep
- Custom green theme and image-based Top 5 cards
