# MotoGP Race Results Analysis in Excel

## Project Summary
This project analyzes historical MotoGP race results from **1949 to 2021** in Excel.

The goal was to turn a large raw dataset into an interactive analysis dashboard that supports data-based decision-making. The dashboard allows users to compare riders, teams, and tracks by filtering the data by **year** and **category**.

The final analytical focus is based on three dimensions:
- **Performance**
- **Consistency**
- **Risk**

## Dataset and Tools
**Dataset**
- Source: Kaggle MotoGP race results dataset
- Time period: 1949–2021
- Size: 56,000+ rows
- Granularity: rider-level race results

**Tools Used**
- Microsoft Excel
- Power Query
- PivotTables
- PivotCharts
- Slicers
- Dynamic Excel formulas

## Workflow
1. Import raw MotoGP data into Excel
2. Clean and transform the data in Power Query
3. Create helper columns for analysis
4. Build a structured `Results` table
5. Create PivotTables and PivotCharts
6. Add slicers and interactive selection logic
7. Generate KPI-based insights and recommendations

## Data Preparation
The raw data was prepared in **Power Query** before the analysis was built in Excel.

Main transformation steps:
- corrected data types
- standardized text fields
- created finish / DNF logic
- created helper columns such as `Is_finished`, `Is_not_finished`, `Is_Winner`, and `Is_Podium`
- converted race times and gap values into numeric seconds
- cleaned rider and team naming where needed

The final cleaned table used for analysis is called **`Results`**.

## KPI Framework
The dashboard evaluates riders and teams using three KPI groups.

### 1. Performance
- total points
- wins
- podiums

### 2. Consistency
- finish rate
- average finishing position
- number of race starts

### 3. Risk
- DNF rate
- average gap to the winner
- median gap to the winner

This framework allows a more balanced evaluation than points alone.

## Interactive Dashboard Features
The Excel solution includes:
- filtering by **year** and **category**
- rider rankings and top 10 comparisons
- KPI summary views
- performance and risk charts
- track-based insights
- fun facts and special views
- a data-based recommendation for a potential season favorite

## Key Insight
A strong favorite is not defined by performance alone.

The strongest rider profile combines:
**high performance + strong consistency - low risk**

This means that points, wins, and podiums should always be interpreted together with reliability measures such as finish rate and DNF count.

## What I Learned
This project helped me improve my skills in:
- data cleaning with Power Query
- KPI design in Excel
- dashboard building
- pivot-based reporting
- dynamic filtering logic
- transforming raw data into decision-ready insights

## Repository Contents
Recommended repository structure:

```text
excel-motogp-analysis/
├── README.md
├── assets/
├── data/
├── docs/
│   ├── motogp-handout.md
│   ├── motogp-analysis-presentation.pdf
│   └── screenshots/
└── workbook/
```

## Data Source
This project is based on the **MotoGP Race Results** dataset from Kaggle.
