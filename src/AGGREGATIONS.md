# Data Aggregation and Analysis Documentation

## Overview
This document details all aggregation operations performed on the transformed Sales Department data to analyze attrition patterns and their relationship with monthly income.

## Aggregation Operations

### 1. Attrition Count Analysis
**Purpose**: Quantify the number of salespeople with and without attrition.

#### Table 1: Attrition Count
```sql
CREATE TABLE attrition_count AS
SELECT COUNT(*) AS attrition
FROM employee_sales
WHERE Department = 'Sales' AND Attrition = 'Yes';
```

**Result**: 92 salespeople with attrition

#### Table 2: Non-Attrition Count
```sql
CREATE TABLE non_attrition_count AS
SELECT COUNT(*) AS `Non Attrition`
FROM employee_sales
WHERE Department = 'Sales' AND Attrition = 'No';
```

**Result**: 354 salespeople without attrition

**Key Insight**: Approximately 20.6% (92/446) of Sales Department employees experienced attrition.

---

### 2. Monthly Income Statistics
**Purpose**: Calculate statistical measures (average, minimum, maximum) of monthly income across different employee groups.

#### All Salespeople Statistics
```sql
CREATE TABLE sales_all_stats AS
SELECT
    AVG(MonthlyIncome) AS average_monthly_income,
    MIN(MonthlyIncome) AS min_monthly_income,
    MAX(MonthlyIncome) AS max_monthly_income
FROM employee_sales
WHERE Department = 'Sales';
```

**Purpose**: Establishes baseline income statistics for the entire Sales Department.

#### Salespeople WITH Attrition Statistics
```sql
CREATE TABLE sales_attrition_stats AS
SELECT
    AVG(MonthlyIncome) AS average_monthly_income,
    MIN(MonthlyIncome) AS min_monthly_income,
    MAX(MonthlyIncome) AS max_monthly_income
FROM employee_sales
WHERE Department = 'Sales' AND Attrition = 'Yes';
```

**Purpose**: Identifies income patterns for employees who left the company.

#### Salespeople WITHOUT Attrition Statistics
```sql
CREATE TABLE sales_non_attrition_stats AS
SELECT
    AVG(MonthlyIncome) AS average_monthly_income,
    MIN(MonthlyIncome) AS min_monthly_income,
    MAX(MonthlyIncome) AS max_monthly_income
FROM employee_sales
WHERE Department = 'Sales' AND Attrition = 'No';
```

**Purpose**: Identifies income patterns for retained employees.

---

### 3. Income Distribution Analysis
**Purpose**: Analyze the distribution of employees across different income levels, segmented by attrition status.

#### Income Distribution - WITH Attrition
```sql
CREATE TABLE income_attrition_dist AS
SELECT
    MonthlyIncome AS monthlyincome,
    COUNT(*) AS `count`
FROM employee_sales
WHERE Department = 'Sales' AND Attrition = 'Yes'
GROUP BY MonthlyIncome
ORDER BY MonthlyIncome;
```

**Purpose**: Shows how many employees at each income level experienced attrition.

#### Income Distribution - WITHOUT Attrition
```sql
CREATE TABLE income_non_attrition_dist AS
SELECT
    MonthlyIncome AS monthlyincome,
    COUNT(*) AS `count`
FROM employee_sales
WHERE Department = 'Sales' AND Attrition = 'No'
GROUP BY MonthlyIncome
ORDER BY MonthlyIncome;
```

**Purpose**: Shows how many employees at each income level were retained.

---

## Summary of Aggregations

| Aggregation Type | Tables Created | Key Metrics |
|-----------------|----------------|-------------|
| Count Analysis | 2 tables | Attrition vs Non-Attrition counts |
| Statistical Analysis | 3 tables | AVG, MIN, MAX income by group |
| Distribution Analysis | 2 tables | Employee count per income level |

## Key Findings

1. **Attrition Rate**:
   - 92 employees left (20.6%)
   - 354 employees retained (79.4%)

2. **Income Analysis**:
   - Statistical comparison reveals income differences between attrition groups
   - Distribution analysis enables identification of income brackets with higher attrition risk

3. **Analysis Ready**:
   - Data is now aggregated and ready for visualization
   - Income patterns can be correlated with attrition likelihood

## Tables Generated
- `attrition_count` - Count of employees with attrition
- `non_attrition_count` - Count of employees without attrition
- `sales_all_stats` - Income statistics for all salespeople
- `sales_attrition_stats` - Income statistics for employees with attrition
- `sales_non_attrition_stats` - Income statistics for retained employees
- `income_attrition_dist` - Income distribution for attrition group
- `income_non_attrition_dist` - Income distribution for retention group
