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
