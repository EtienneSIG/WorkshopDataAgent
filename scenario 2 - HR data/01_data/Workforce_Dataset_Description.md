# Workforce Dataset Description

## 📋 Overview

**File Name:** `workforce_dataset_400.csv`  
**Total Records:** 400 employees  
**Format:** CSV (Comma-Separated Values)  
**Year:** 2025  
**Primary Use:** HR workforce capacity planning, workload analysis, and employee productivity tracking

---

## 📊 Dataset Structure

### Record Count
- **Total Employees:** 400
- **Header Row:** 1
- **Data Rows:** 400

---

## 🗂️ Column Definitions

| # | Column Name | Data Type | Description | Example Values |
|---|------------|-----------|-------------|----------------|
| 1 | **Entity** | Text | Business entity classification | BS, AMN |
| 2 | **Type** | Text | Employee type | EXT (External), INT (Internal) |
| 3 | **Company number** | Integer | Company identifier code | 415, 508, 407, 589 |
| 4 | **MASA status** | Text | Management level/status | EVP, NEVP, Groupe EVP, (blank for external) |
| 5 | **FirstName** | Text | Employee first name | Timothy, Charles, Pamela |
| 6 | **LastName** | Text | Employee last name | Snyder, Woods, Simpson |
| 7 | **Year** | Integer | Data year | 2025 |
| 8 | **Domain Solutions** | Text | Domain/department assignment | ES, DIR, EC, SC, OPN, RDMF |
| 9 | **% of work January** | Decimal | Workload percentage in January | 0.92, 1.14, 0.86 |
| 10 | **% work February** | Decimal | Workload percentage in February | 1.14, 0.95, 1.16 |
| 11 | **% work March** | Decimal | Workload percentage in March | 0.86, 1.0, 0.98 |
| 12 | **% work April** | Decimal | Workload percentage in April | 1.03, 1.08, 1.0 |
| 13 | **% work May** | Decimal | Workload percentage in May | 1.12, 1.19, 0.91 |
| 14 | **% work June** | Decimal | Workload percentage in June | 0.86, 1.13, 0.84 |
| 15 | **% work July** | Decimal | Workload percentage in July | 1.01, 1.09, 0.85 |
| 16 | **% work August** | Decimal | Workload percentage in August | 0.94, 1.16, 1.17 |
| 17 | **% work September** | Decimal | Workload percentage in September | 0.92, 1.06, 0.81 |
| 18 | **% work October** | Decimal | Workload percentage in October | 0.95, 0.94, 1.13 |
| 19 | **% work November** | Decimal | Workload percentage in November | 1.13, 1.02, 0.84 |
| 20 | **% work December** | Decimal | Workload percentage in December | 1.06, 0.9, 0.83 |

---

## 🏢 Key Dimensions

### Entities
- **BS** - Business Services
- **AMN** - Americas Network

### Employee Types
- **EXT** - External (contractors, consultants)
- **INT** - Internal (full-time employees)

### MASA Status (Management Levels)
- **EVP** - Executive Vice President
- **NEVP** - Non-Executive Vice President
- **Groupe EVP** - Group Executive Vice President
- **(Blank)** - Not applicable (typically for external employees)

### Company Numbers
- **415**
- **407**
- **508**
- **589**

### Domain Solutions (Departments)
| Code | Description |
|------|-------------|
| **ES** | Enterprise Services |
| **DIR** | Direction/Management |
| **EC** | Enterprise Computing |
| **SC** | Supply Chain |
| **OPN** | Operations |
| **RDMF** | Research, Development & Manufacturing |

---

## 📈 Workload Metrics

### Monthly Workload Percentages
- **Normal Capacity**: 1.0 (100%)
- **Underutilized**: < 1.0 (e.g., 0.82 = 82% capacity)
- **Overutilized**: > 1.0 (e.g., 1.20 = 120% capacity)

### Workload Range in Dataset
- **Minimum**: ~0.80 (80% capacity)
- **Maximum**: ~1.20 (120% capacity)
- **Typical Range**: 0.81 - 1.20

### Monthly Coverage
All 12 months of 2025 are covered:
- January through December
- Each employee has workload percentages for every month

---

## 🔍 Data Characteristics

### Data Quality Notes
- **Complete Records**: All 400 employees have complete monthly data
- **Workload Values**: All values are decimal numbers representing capacity percentage
- **MASA Status**: Only applies to internal employees (INT)
- **Year Consistency**: All records are for 2025

### Unique Identifiers
- Employee name combination (FirstName + LastName)
- No explicit employee ID field

### Distribution Summary
- **Internal vs External**: Mixed workforce
- **Multiple Companies**: 4 different company numbers (415, 407, 508, 589)
- **Domain Diversity**: 6 different domain solutions
- **Management Levels**: 3 distinct MASA status levels for internal employees

---

## 📊 Use Cases

### Primary Analytics Applications

1. **Capacity Planning**
   - Identify underutilized employees
   - Spot overutilized employees at risk of burnout
   - Balance workload across teams

2. **Resource Allocation**
   - Analyze capacity by domain/department
   - Compare internal vs external workforce utilization
   - Optimize staffing levels

3. **Workforce Trends**
   - Seasonal workload patterns
   - Month-over-month capacity changes
   - Department-specific workload trends

4. **Management Insights**
   - Compare workload across management levels
   - Entity performance analysis (BS vs AMN)
   - Company-specific workforce analysis

5. **HR Planning**
   - Identify hiring needs (consistent overutilization)
   - Detect potential redundancies (consistent underutilization)
   - Succession planning for management roles

6. **Operational Efficiency**
   - Domain-specific productivity analysis
   - Peak and low demand periods identification
   - Cross-company workload comparison

---

## 🎯 Key Performance Indicators (KPIs)

### Recommended Metrics

#### Individual Level
- Average Workload per Employee
- Monthly Workload Variance
- Over/Underutilization Count
- Peak Workload Month

#### Department Level
- Average Workload by Domain
- Domain Utilization Rate
- Headcount by Domain
- Internal vs External Ratio by Domain

#### Company Level
- Average Workload by Company Number
- Company-wide Utilization Trends
- Employee Distribution by Company

#### Management Level
- Average Workload by MASA Status
- Management Capacity Analysis
- Leadership Utilization Patterns

#### Time-Based
- Monthly Average Workload (across all employees)
- Seasonal Trends (Q1, Q2, Q3, Q4)
- Month-over-Month Changes
- Year-to-Date Utilization

---

## 💡 Business Questions to Explore

### 1. **Capacity Analysis**
- "Which employees are consistently overutilized (>110%) across multiple months?"
- "Identify underutilized resources (<90%) that could take on additional work"
- "What's the average workload by Domain Solutions?"
- "Compare capacity utilization between internal and external employees"
- "Which company number has the highest/lowest average utilization?"

### 2. **Seasonal Patterns**
- "Are there specific months with higher workload across all employees?"
- "Identify seasonal trends by Domain Solutions"
- "Which quarter has the peak workload?"
- "Compare summer vs winter workload patterns"

### 3. **Workforce Distribution**
- "How many employees are in each Domain Solutions?"
- "What's the ratio of internal to external employees by company?"
- "Distribution of employees across MASA status levels"
- "Which entity (BS vs AMN) has more employees?"

### 4. **Risk Identification**
- "List employees with workload >115% for 3+ consecutive months (burnout risk)"
- "Find employees with <85% workload for 6+ months (potential redundancy)"
- "Identify departments with consistently high utilization (hiring needs)"

### 5. **Comparative Analysis**
- "Compare workload patterns between EVP, NEVP, and Groupe EVP"
- "Average workload: BS vs AMN entities"
- "Which Domain Solutions has the most balanced workload distribution?"
- "Compare workload volatility across different employee types"

---

## 📐 Data Modeling Recommendations

### Recommended Dimension Tables

1. **DimEmployee**
   - EmployeeKey (auto-generated)
   - FirstName
   - LastName
   - FullName (concatenated)
   - Entity
   - Type
   - CompanyNumber
   - MASAStatus
   - DomainSolutions

2. **DimDate** (Month-level granularity)
   - DateKey
   - Year
   - Month
   - MonthName
   - Quarter
   - Semester

3. **DimDomain**
   - DomainKey
   - DomainCode (ES, DIR, EC, SC, OPN, RDMF)
   - DomainName (full description)
   - DomainCategory

4. **DimCompany**
   - CompanyKey
   - CompanyNumber
   - CompanyName

### Fact Table

**FactWorkload** (Unpivoted structure recommended)
- EmployeeKey (FK)
- DateKey (FK)
- Year
- Month
- WorkloadPercentage
- IsOverutilized (calculated: >1.0)
- IsUnderutilized (calculated: <1.0)
- UtilizationCategory (calculated: Low/Normal/High)

### Recommended Transformation

Transform the wide format (12 month columns) into a long format:
```
Original: Employee | Jan | Feb | Mar | ...
Transformed: Employee | Month | Workload%
```

---

## 🔧 Power BI/Fabric Setup

### Import Settings
- **First Row as Headers**: Yes
- **Data Types**:
  - Text: Entity, Type, MASA status, FirstName, LastName, Domain Solutions
  - Integer: Company number, Year
  - Decimal: All monthly workload columns
- **Handle Missing Values**: MASA status blanks are intentional for external employees

### DAX Measures Examples

```dax
// Average Workload
Average Workload = AVERAGE(FactWorkload[WorkloadPercentage])

// Overutilized Employees Count
Overutilized Count = 
CALCULATE(
    DISTINCTCOUNT(FactWorkload[EmployeeKey]),
    FactWorkload[WorkloadPercentage] > 1.1
)

// Underutilized Employees Count
Underutilized Count = 
CALCULATE(
    DISTINCTCOUNT(FactWorkload[EmployeeKey]),
    FactWorkload[WorkloadPercentage] < 0.9
)

// Monthly Workload Trend
Monthly Avg Workload = 
CALCULATE(
    AVERAGE(FactWorkload[WorkloadPercentage]),
    ALLEXCEPT(FactWorkload, DimDate[Month])
)

// Utilization Rate
Utilization Rate = 
DIVIDE(
    COUNTROWS(
        FILTER(FactWorkload, FactWorkload[WorkloadPercentage] >= 0.9 
            && FactWorkload[WorkloadPercentage] <= 1.1)
    ),
    COUNTROWS(FactWorkload),
    0
)

// Employee Count
Total Employees = DISTINCTCOUNT(DimEmployee[EmployeeKey])

// Peak Month
Peak Workload Month = 
CALCULATE(
    MAX(DimDate[MonthName]),
    TOPN(1, ALL(DimDate[MonthName]), [Average Workload], DESC)
)
```

---

## 🎨 Visualization Recommendations

### Executive Dashboard

1. **KPI Cards**
   - Total Employees
   - Average Workload (across all months)
   - % Overutilized
   - % Underutilized

2. **Charts**
   - **Line Chart**: Monthly workload trend (all employees average)
   - **Bar Chart**: Average workload by Domain Solutions
   - **Clustered Bar**: Internal vs External workload comparison
   - **Heatmap**: Employee workload by month (color-coded)
   - **Donut Chart**: Employee distribution by Entity
   - **Column Chart**: Workload by MASA Status

3. **Tables**
   - Top 10 Overutilized Employees
   - Top 10 Underutilized Employees
   - Employee details with YTD average workload

4. **Filters/Slicers**
   - Entity (BS, AMN)
   - Type (INT, EXT)
   - Company Number
   - Domain Solutions
   - MASA Status
   - Month

---

## 🔐 Data Privacy & Security

- **Real Names**: This dataset contains employee names - ensure proper access controls
- **Confidential Information**: Workload data is sensitive HR information
- **Usage Restrictions**: Should be used only for legitimate business analysis
- **Compliance**: Ensure GDPR/privacy law compliance when using employee data

---

## 📝 Technical Specifications

### File Properties
- **Encoding**: UTF-8
- **Delimiter**: Comma (,)
- **Header**: Row 1
- **Data Rows**: 400
- **File Size**: ~60 KB (approximate)

### Column Count
- **Total Columns**: 20
- **Identifier Columns**: 7 (Entity through Domain Solutions)
- **Metric Columns**: 12 (monthly workload percentages)
- **Metadata Column**: 1 (Year)

---

## 📚 Related Documentation

- Power BI Workforce Analytics Best Practices
- HR Capacity Planning Guide
- Workload Optimization Strategies

---

**Last Updated:** October 29, 2025  
**Dataset Version:** 1.0  
**Record Count:** 400 employees  
**Year Coverage:** 2025
