# MotoGP Race Results Analysis in Excel

## Project Overview
This project analyzes historical MotoGP race results from **1949 to 2021** in Excel.

The goal was to transform a large raw dataset into an interactive dashboard that helps evaluate riders, teams, and tracks based on three dimensions:

- **Performance**
- **Consistency**
- **Risk**

The final output is a decision-support dashboard built with **Power Query**, **PivotTables**, **PivotCharts**, **Slicers**, and Excel formulas.

---

## Project Goal
The purpose of this project was to create a management-style analysis tool that makes it easy to answer questions such as:

- Which riders collected the most points?
- Who was the most dominant or most consistent?
- Which riders had the highest risk of failure?
- Which tracks were the most chaotic?
- Who would be the best data-based favorite for the next season?

---

## Tools Used
- **Microsoft Excel**
- **Power Query**
- **PivotTables**
- **PivotCharts**
- **Slicers**
- **Dynamic formulas**
- **Conditional KPI logic**

---

## Dataset
- **Source:** Kaggle MotoGP race results dataset
- **Time period:** 1949–2021
- **Size:** 56,000+ rows
- **Granularity:** Rider-level race results

The dataset includes fields such as:
- year
- category
- rider
- team
- bike
- points
- finishing position
- race time
- gap to winner
- status / DNF information

---

## Data Preparation
The raw dataset was imported and transformed in **Power Query**.

Main preparation steps:
- corrected data types
- cleaned and standardized text fields
- created a finish / DNF status logic
- created KPI helper fields such as:
  - `Is_finished`
  - `Is_not_finished`
  - `Is_Winner`
  - `Is_Podium`
- converted race times into seconds
- converted gap values into numeric seconds
- standardized rider and team naming where necessary

The cleaned output table serves as the main analytical table: **`Results`**.

---

## KPI Framework
The analysis is based on three KPI groups:

### 1. Performance
- Total points
- Wins
- Podiums

### 2. Consistency
- Finish rate
- Average finishing position
- Number of race starts

### 3. Risk
- DNF rate
- Average gap to the winner
- Median gap to the winner

This KPI structure makes it possible to compare riders and teams in a more balanced way than using points alone.

---

## Dashboard Features
The Excel dashboard includes:

- interactive filtering by **year** and **category**
- rider rankings
- top 10 comparisons
- charts for performance and trends
- KPI summary cards
- DNF / risk analysis
- track-based insights
- fun facts and special views
- a final **data-based recommendation**

The slicers allow fast switching between seasons and categories, so the analysis updates dynamically.

---

## Example Insight
One of the main findings of the project is:

> A strong favorite is not defined by performance alone.  
> The best profile combines **high performance + strong consistency - low risk**.

For example, in one selected MotoGP view, the dashboard recommends a rider based on the combination of:
- highest points
- strong win and podium count
- low DNF count
- excellent average finishing position

---

## Repository Structure
```text
excel-motogp-analysis/
├── README.md
├── assets/
├── data/
├── docs/
└── workbook/
```
