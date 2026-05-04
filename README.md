# Schedule Health & Resource Optimization Analysis

## Overview
This project analyzes a Primavera P6 schedule export using SQL to identify schedule health issues, resource inefficiencies, and areas of risk.

## Tools Used
- SQLite
- SQL
- Excel / Primavera P6

---

## Problem
The schedule showed:
- Imbalanced activity statuses
- Resource duplication
- Limited visibility into in-progress work
- Potential delays in specific work areas

---

## Data Preparation
- Imported schedule data into SQLite
- Removed invalid header rows
- Standardized date formats (YYYY-MM-DD)
- Validated activity status values

---

## Key Analysis

### Activity Status Distribution
```sql
SELECT status_code, COUNT(*) 
FROM activities
GROUP BY status_code;

- Completed: 62.1% (433 activities)  
- Not Started: 36.3% (253 activities)  
- In Progress: 1.6% (11 activities)

### Key Insight

Only 1.6% of activities are marked as "In Progress," indicating that progress updates are likely being recorded only at completion rather than incrementally. This reduces visibility into ongoing work and may impact forecasting accuracy.

### Localized Schedule Risk

Two late not-started activities were identified in the same work package:

- CON-BLW-1350 – Blower System I&C  
- CON-BLW-1360 – Air Compressor I&C  

Both activities share the same location and discipline, indicating a likely common dependency or constraint impacting the Blower Building scope.

## Business Impact

- Reduced visibility into active work due to low in-progress tracking  
- Potential delays in downstream activities due to localized slippage  
- Risk concentrated in specific work packages rather than distributed across the schedule

## Example Output

![Activity Status Distribution](Activity Status Distribution.png)
