# HR Data Analysis Archive

## Project Overview

This repository contains a comprehensive analysis of employee attrition patterns in the Sales Department using the IBM HR Analytics Attrition Dataset. The analysis examines the relationship between employee attrition, job satisfaction, and monthly income to identify key factors contributing to employee turnover.

## Business Problem

**Primary Question**: What factors contribute to employee attrition in the Sales Department, and how do monthly income and job satisfaction correlate with employee retention?

**Context**: Employee attrition is a critical concern for organizations, particularly in revenue-generating departments like Sales. Understanding the patterns and drivers of attrition enables HR and management to:
- Develop targeted retention strategies
- Optimize compensation structures
- Improve employee satisfaction initiatives
- Reduce recruitment and training costs

## Key Insights

### 1. Attrition Rate
- **20.6%** of Sales Department employees experienced attrition (92 out of 446 employees)
- **79.4%** retention rate indicates generally strong employee retention

### 2. Income Analysis
- Statistical comparison reveals distinct income patterns between employees who stayed versus those who left
- Income distribution analysis enables identification of high-risk compensation brackets
- Monthly income appears to be a significant factor in attrition likelihood

### 3. Job Satisfaction Impact
- Job satisfaction levels were analyzed in conjunction with attrition status
- Data ordered by satisfaction levels (highest to lowest) reveals patterns in retention
- Correlation between satisfaction and income provides actionable insights

### 4. Data-Driven Recommendations
- Target retention efforts toward specific income brackets with higher attrition
- Monitor job satisfaction levels as an early warning indicator
- Consider compensation adjustments based on statistical findings

## Project Structure

```
hr-data-analysis-archive/
│
├── README.md                          # This file - project overview and insights
│
├── data/                              # Raw data documentation
│   └── DATA_README.md                 # Dataset source and retrieval instructions
│
├── munge/                             # Data transformation documentation
│   ├── TRANSFORMATIONS.md             # Detailed transformation steps
│   └── Human Resources analysis (module 4).docx
│
├── src/                               # Data aggregation and analysis
│   ├── AGGREGATIONS.md                # Detailed aggregation operations
│   └── Data Aggregation and Analysis of Sales Department Attrition in Human Resources (module 5).docx
│
└── reports/                           # Visualizations and final reports
    ├── VISUALIZATIONS.md              # Dashboard and chart descriptions
    └── Human Resources Data _ Module 6  revised.xlsx
```

## Directory Details

### `/data`
Contains documentation about the raw dataset source and how to retrieve it.
- **Dataset**: IBM HR Analytics Attrition Dataset from Kaggle
- **Access**: Instructions for downloading from Kaggle
- **Note**: Raw data file not included in repository

### `/munge`
Documents all data transformation operations applied to prepare the data for analysis.
- Table creation and column selection
- Income normalization (rounding to nearest $1000)
- Department filtering (Sales only)
- Data ordering by job satisfaction

### `/src`
Contains detailed aggregation and analysis operations.
- Attrition count analysis (92 vs 354)
- Statistical calculations (AVG, MIN, MAX income)
- Income distribution by attrition status
- Seven aggregated tables created for analysis

### `/reports`
Final visualizations and Excel dashboards.
- Interactive Excel workbook with charts
- Attrition comparison visualizations
- Income analysis dashboards
- Job satisfaction correlations

## Analysis Workflow

1. **Data Acquisition** → Retrieved IBM HR Analytics dataset from Kaggle
2. **Data Transformation** → Applied filtering, rounding, and sorting operations
3. **Data Aggregation** → Generated statistical summaries and distributions
4. **Visualization** → Created dashboards and charts for insight communication

## Technologies Used

- **Database**: SQL (for data transformation and aggregation)
- **Analysis**: Statistical aggregation (AVG, MIN, MAX, COUNT)
- **Visualization**: Microsoft Excel (dashboards and charts)
- **Version Control**: Git & GitHub

## Dataset Source

**IBM HR Analytics Attrition Dataset**
Kaggle: https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset/data

## How to Use This Repository

1. **Understand the Data**: Start with `/data/DATA_README.md` to learn about the dataset
2. **Review Transformations**: See `/munge/TRANSFORMATIONS.md` for data preparation steps
3. **Explore Aggregations**: Check `/src/AGGREGATIONS.md` for analysis operations
4. **View Insights**: Open the Excel file in `/reports` to see visualizations
5. **Extend Analysis**: Use the documented methodology to perform additional analyses

## Future Analysis Opportunities

- Expand analysis to other departments (R&D, HR)
- Incorporate additional variables (age, years at company, education)
- Build predictive models for attrition risk
- Analyze temporal patterns and trends
- Compare across different job roles within Sales

## Course Information

This analysis was completed as part of a Data Analytics course, covering:
- Module 4: Data Transformation
- Module 5: Data Aggregation and Analysis
- Module 6: Data Visualization

## License

This project is for educational purposes as part of course requirements.

---

*For questions or to extend this analysis, please refer to the detailed documentation in each folder.*
