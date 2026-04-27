# MotoGP Excel Project – Technical Notes

## Purpose of This Document
This file documents the technical logic behind the Excel project. It explains the data model, Power Query transformations, Excel-based KPI calculations, and the logic used for interactive filtering and analysis.

## 1. Data Model Overview
The project is built around a central table called **`Results`**.

This table contains the cleaned race-level data and is the main source for:
- PivotTables
- PivotCharts
- KPI calculations
- helper lists and dropdowns
- dashboard outputs

The project structure follows this logic:
- **Power Query** for data import and transformation
- **Results table** as the analytical base
- **PivotTables** for rankings and aggregations
- **Dropdown logic and formulas** for interactive KPI views

## 2. Core Transformation Logic in Power Query
### Finish and Status Logic
- `position -> Finished_position`
  - keep positive finishing positions
  - convert invalid or non-finish values to null

- `Finished_position -> Is_finished`
  - `1` if the rider finished the race
  - `0` if not finished

- `Finished_position -> Is_not_finished`
  - `1` if the rider did not finish
  - `0` if finished

### Performance Flags
- `Finished_position -> Is_Winner`
  - `1` if finishing position = 1
  - otherwise `0`

- `Finished_position -> Is_Podium`
  - `1` if finishing position is between 1 and 3
  - otherwise `0`

### Time Classification
The original `time` field is classified into a new field called **`TimeType`**.

Rules:
- starts with `+` -> `Gap`
- contains `Lap` -> `LapsDown`
- empty / null -> blank
- otherwise -> `RaceTime`

This allows a clean separation between:
- actual race time
- gap to the winner
- lap-down information

### Gap Conversion
For gap analysis, the original text values are transformed into numeric seconds.

Process:
1. keep original gap text in `Gap_text`
2. remove symbols such as `+`
3. normalize separators
4. split into hours / minutes / seconds
5. calculate final numeric field `Gap_seconds`

Additional helper flag:
- `Gap_flag`
  - `1` if the row contains a valid gap entry
  - `0` otherwise

### LapsDown Conversion
If a value in the `time` field contains lap-based information, it is transformed into:
- `LapsDown_count`

This allows the number of laps behind the leader to be analyzed numerically.

## 3. Recommended Final Output Columns
The final analytical table should keep these core fields:
- `Finished_position`
- `Is_finished`
- `Is_not_finished`
- `Is_Winner`
- `Is_Podium`
- `TimeType`
- `LapsDown_count`
- `Gap_text` (optional)
- `Gap_seconds`
- `Gap_flag`

Temporary helper columns created only for conversions should be removed after validation.

## 4. Excel-Based KPI Logic
The Excel dashboard uses the cleaned `Results` table to calculate KPIs.

### Main KPI Categories
#### Performance
- points
- wins
- podiums

#### Consistency
- number of races
- finish rate
- average finishing position

#### Risk
- DNF count
- DNF rate
- average gap to the winner
- median gap to the winner

### Typical Excel Logic
Examples of function types used in the project:
- `SUMIFS` / `SUMMEWENNS`
- `COUNTIFS` / `ZÄHLENWENNS`
- `AVERAGEIFS` / `MITTELWERTWENNS`
- `MAXIFS` / `MAXWENNS`
- `MINIFS` / `MINWENNS`
- `XLOOKUP` / `XVERWEIS`
- `FILTER`
- `UNIQUE` / `EINDEUTIG`
- `SORT`
- `IFERROR` / `WENNFEHLER`

## 5. Dynamic Dropdown Logic
An additional worksheet is used to generate dynamic lists for user selections.

### Selection Fields
Typical input cells:
- Year
- Category
- Rider

### Logic Behind the Lists
The dropdown lists are generated dynamically from the `Results` table using:
- `FILTER`
- `UNIQUE`
- `SORT`
- `IFERROR`

Examples:
- all available years
- categories filtered by year
- riders filtered by year + category
- teams, bikes, and tracks based on the current selection

This creates a cascading selection system and ensures that only valid combinations can be selected.

## 6. Pivot and Dashboard Logic
The project uses PivotTables for rankings and comparative analysis.

Typical outputs:
- Top 10 riders by points
- winners ranking
- podium ranking
- DNF analysis
- team and bike comparisons
- track-related risk insights

Slicers are connected to multiple PivotTables so that one filter selection updates several outputs at the same time.

## 7. Fun Facts and Additional Insights
The project also includes formula-based insight views outside classical PivotTables.

Examples:
- closest race finish
- most dominant victory
- speed king
- most chaotic track
- finish-rate-based consistency insight

These views combine KPI logic with interactive selections and help make the dashboard easier to interpret.

## 8. Power Query vs Excel – Role Split
### Done in Power Query
- data import
- type correction
- cleaning text fields
- status logic
- helper flag creation
- gap and race time conversion
- structure normalization

### Done in Excel
- KPI calculations
- rankings
- dashboard layout
- charts
- dropdown logic
- fun facts
- final recommendation logic

## 9. Notes for Repository Use
For a public GitHub repository, this technical document should support the project documentation without replacing the main README.

Recommended use:
- `README.md` -> project overview for first-time viewers
- `docs/motogp-handout.md` -> short portfolio-style project summary
- `docs/motogp-technical-notes.md` -> detailed technical explanation

## 10. Suggested Screenshots for the Repo
Recommended screenshot set:
- dashboard overview
- driver ranking with slicers
- DNF / risk analysis
- recommendation view
- optional Power Query applied steps
