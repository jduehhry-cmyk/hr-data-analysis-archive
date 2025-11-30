# Data Transformation Documentation

## Overview
This document details all data transformations applied to the raw IBM HR Analytics dataset to prepare it for analysis of Sales Department attrition patterns.

## Transformation Steps

### 1. Table Creation and Column Selection
**Purpose**: Create a focused analysis table containing only relevant columns for attrition analysis.

**Transformation**:
```sql
CREATE TABLE employee_sales AS
SELECT Attrition, Department, JobSatisfaction, MonthlyIncome
FROM employee;
```

**Rationale**:
- Reduced the dataset to only the columns needed for Sales Department attrition analysis
- Selected columns: Attrition, Department, JobSatisfaction, and MonthlyIncome

---

### 2. Income Rounding
**Purpose**: Normalize monthly income data by rounding to the nearest thousand dollars for easier analysis and grouping.

**Transformation**:
```sql
SELECT Attrition, Department, JobSatisfaction,
       ROUND(MonthlyIncome, -3) AS MonthlyIncomeRounded
FROM employee_sales;
```

**Rationale**:
- Rounds MonthlyIncome to the nearest $1000 (e.g., $5,432 becomes $5,000)
- Reduces granularity for better pattern recognition
- Makes income brackets more manageable for analysis

---

### 3. Department Filtering
**Purpose**: Focus analysis exclusively on the Sales Department.

**Transformation**:
```sql
SELECT Attrition, Department, JobSatisfaction,
       ROUND(MonthlyIncome, -3) AS MonthlyIncomeRounded
FROM employee_sales
WHERE Department = 'Sales';
```

**Rationale**:
- Filtered dataset to include only Sales Department employees
- Enables focused analysis on sales-specific attrition patterns

---

### 4. Data Ordering
**Purpose**: Sort data by job satisfaction levels to facilitate trend analysis.

**Transformation**:
```sql
SELECT Attrition, Department, JobSatisfaction,
       ROUND(MonthlyIncome, -3) AS MonthlyIncomeRounded
FROM employee_sales
WHERE Department = 'Sales'
ORDER BY JobSatisfaction DESC;
```

**Rationale**:
- Ordered data from highest to lowest job satisfaction
- Allows for easy identification of satisfaction-to-attrition correlations
- Facilitates visual analysis of patterns

---

## Summary of Transformations

| Step | Transformation Type | Impact |
|------|-------------------|---------|
| 1 | Column Selection | Reduced from full dataset to 4 key columns |
| 2 | Data Normalization | Rounded MonthlyIncome to nearest $1000 |
| 3 | Filtering | Isolated Sales Department records only |
| 4 | Sorting | Ordered by JobSatisfaction (descending) |

## Final Dataset Characteristics
- **Scope**: Sales Department employees only
- **Key Variables**: Attrition status, Job Satisfaction, Rounded Monthly Income
- **Sorting**: Organized by Job Satisfaction (highest to lowest)
- **Purpose**: Ready for aggregation and attrition pattern analysis
