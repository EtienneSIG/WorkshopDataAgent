# Financial Dataset Description

## 📋 Overview

**File Name:** `financial_dataset_usdate_10k.csv`  
**Total Records:** 10,000 transactions  
**Format:** CSV (Comma-Separated Values)  
**Date Range:** 2023 - 2025  
**Primary Use:** Financial transaction tracking and analysis for enterprise accounting

---

## 📊 Dataset Structure

### Record Count
- **Total Transactions:** 10,000
- **Header Row:** 1
- **Data Rows:** 10,000

---

## 🗂️ Column Definitions

| # | Column Name | Data Type | Description | Example Values |
|---|------------|-----------|-------------|----------------|
| 1 | **SupplierName** | Text | Original supplier name identifier | MXAXR WJA INC, DQVKN WPP INC |
| 2 | **Dept** | Text | Department code | IN, BSS, DIR, MQ |
| 3 | **Service** | Text | Service category or type | D1 DAP, MF, GOSM, NET, Security |
| 4 | **NatAnal** | Text | Nature of analysis category | Training, Capitalized production (PRIM), Internal, Other expenses, Salaries, Taxes, Depreciation |
| 5 | **ModuleName** | Text | Module/system name | AP, PA, GL, PO, INV |
| 6 | **Company** | Text | Company entity name | Nexus Enterprise Holdings, Apex Innovations Ltd, TechnoGlobal Industries, Quantum Dynamics Group, Meridian Solutions Corp |
| 7 | **Account** | Text | Account number | 6417204, 6117000, 6076700 |
| 8 | **Site** | Text | Site/location code | GRU, MAN, RIO, RES, LAV, MTC, DDD, CGR, PP1, PPC |
| 9 | **Section** | Text | Section identifier | 14580B, 14400A, 14560B, 14480A |
| 10 | **Structure** | Integer | Structure code | 7956, 7950 |
| 11 | **Intercompany** | Integer | Intercompany transaction code | 567, 796, 511, 200, 409, 589, 407, 415, 723, 0 |
| 12 | **Nature** | Text | Nature classification | N81_MASA_F, N30_ENERGY_V, N23_FE_TRAVEL_F, N70_DEPRECIATION_F, N22_FE_F, N87_FE_F |
| 13 | **Major** | Text | Major classification | MAJ16_Restructuring, MAJ11_Income, MAJ09_General_Overhead_F, MAJ05_Maintenance_F |
| 14 | **Minor** | Text | Minor classification | MIN2005, MIN0918, MIN0210, MIN0520, MIN0925 |
| 15 | **GroupSectionAndDescription** | Text | Group section with description | 9815 Expenses to be reinvoiced or reallocated, 1448 ISIT Infra Transverse operations (GOM) |
| 16 | **LedgerName** | Text | Ledger identifier | MX_589_PL_MXN, MX_839_PL_MXN, BR_414_PL_BRL, CA_407_PL_CAD, US_415_PL_USD |
| 17 | **Source** | Text | Transaction source | Payables, Assets, MICH_EPW_GLJRNLINTF, Cost Management, Receivables, Projects, Spreadsheet, Manual, Recurring, MassAllocation |
| 18 | **Category** | Text | Transaction category | GL_Intercompany_Reversal, Inventory, GL_Tax, Misc Receipts, Purchase Invoices, Receiving, Depreciation, GL_Payroll |
| 19 | **SupplierNumber** | Integer | Supplier identifier number | 49, 39, 14, 23, 15, 29, 8, 47 |
| 20 | **SupplierName_Fake** | Text | Anonymized supplier name | Optimal Distribution Co, Integrated Solutions Ltd, Innovation Industries Corp |
| 21 | **DocumentCurrency** | Text | Original document currency | EUR, GBP, BRL, USD, CAD, MXN |
| 22 | **Ledgercurrency** | Text | Ledger/accounting currency | BRL, CAD, USD, MXN, EUR |
| 23 | **AmoutinEUR** | Decimal | Transaction amount in EUR | 958637.12, 869321.62, 405570.65, -860.31 (can be negative) |
| 24 | **DebitEnteredAmount** | Decimal | Debit amount entered | 854.89, 128.73, 137.24 |
| 25 | **CreditEnteredAmount** | Decimal | Credit amount entered | 0 (mostly), can have values |
| 26 | **DebitAccountedAmount** | Decimal | Debit amount in accounting | 109.48, 556.79, 753.68 |
| 27 | **CreditAccountedAmount** | Decimal | Credit amount in accounting | 0 (mostly), can have values |
| 28 | **DateCreated** | Date | Transaction creation date | MM/DD/YYYY format (e.g., 11/11/2023) |
| 29 | **POOrderedDate** | Date | Purchase order date | MM/DD/YYYY format (e.g., 01/15/2025) |
| 30 | **DueDate** | Date | Payment due date | MM/DD/YYYY format (e.g., 10/21/2025) |

---

## 🏢 Key Dimensions

### Departments (Dept)
- **IN** - Information Technology/Infrastructure
- **BSS** - Business Support Systems
- **DIR** - Direction/Management
- **MQ** - Methods & Quality

### Companies
- Nexus Enterprise Holdings
- Apex Innovations Ltd
- TechnoGlobal Industries
- Quantum Dynamics Group
- Meridian Solutions Corp

### Sites (Geographic Locations)
- GRU, MAN, RIO, RES, LAV, MTC, DDD, CGR, PP1, PPC

### Services
- D1 DAP (Data & Applications Platform)
- MF (Manufacturing)
- GOSM (General Operations & Service Management)
- NET (Network)
- Security
- Communications
- DEV (Development)
- SC (Supply Chain)
- EC (Enterprise Computing)
- EUX (End User Experience)
- And many more...

### Nature Analysis Categories (NatAnal)
- Training
- Capitalized production (PRIM)
- Internal
- Other expenses
- Salaries
- Taxes
- Depreciation
- Telecom Data/Voice
- Maintenance & Rental
- Travels
- Purchases
- Invoices sent
- External Resources

---

## 💰 Financial Metrics

### Currencies Used
| Currency Code | Description |
|--------------|-------------|
| EUR | Euro |
| USD | US Dollar |
| GBP | British Pound |
| BRL | Brazilian Real |
| CAD | Canadian Dollar |
| MXN | Mexican Peso |

### Amount Fields
- **AmoutinEUR**: Main transaction amount (standardized in EUR)
  - Range: Negative values to ~980,000 EUR
  - Can be negative (credit transactions/reversals)
- **DebitEnteredAmount**: Original debit entry
- **CreditEnteredAmount**: Original credit entry
- **DebitAccountedAmount**: Accounted debit
- **CreditAccountedAmount**: Accounted credit

---

## 📅 Date Fields

### Three Key Dates Per Transaction
1. **DateCreated**: When the transaction was created/recorded
2. **POOrderedDate**: When the purchase order was placed
3. **DueDate**: Payment deadline

**Date Range Coverage:**
- Earliest: 2023
- Latest: 2025
- Covers approximately 2-3 years of financial data

---

## 🏷️ Classification Hierarchy

### Multi-Level Classification System
```
Nature (N81_MASA_F, N30_ENERGY_V, etc.)
  └── Major (MAJ16_Restructuring, MAJ11_Income, etc.)
      └── Minor (MIN2005, MIN0918, etc.)
          └── GroupSectionAndDescription (Detailed description)
```

**Example Hierarchy:**
- Nature: N81_MASA_F
- Major: MAJ16_Restructuring
- Minor: MIN2005
- Description: "9815 Expenses to be reinvoiced or reallocated"

---

## 🔍 Data Characteristics

### Data Quality Notes
- **Complete Records**: All 10,000 records have core required fields
- **Optional Fields**: Some records have blank values for Source, Category
- **Negative Values**: AmoutinEUR can be negative (representing credits/refunds)
- **Zero Values**: Debit/Credit amounts can be 0

### Unique Identifiers
- **SupplierNumber**: Ranges from 1-50
- **SupplierName_Fake**: Anonymized supplier names for privacy
- **Account**: Various GL account numbers (6000000-9000000 range)

---

## 📈 Use Cases

### Primary Analytics Applications
1. **Spend Analysis**
   - Department-wise spending
   - Supplier spend concentration
   - Category-based analysis

2. **Cash Flow Management**
   - Payment aging analysis
   - Due date tracking
   - Overdue monitoring

3. **Financial Reporting**
   - Multi-currency transaction tracking
   - Debit/Credit reconciliation
   - Ledger consolidation

4. **Operational Insights**
   - Service line profitability
   - Site-based cost analysis
   - Nature of expense trending

5. **Supplier Management**
   - Vendor performance tracking
   - Payment terms analysis
   - Supplier diversity analysis

6. **Intercompany Tracking**
   - Cross-company transactions
   - Transfer pricing analysis
   - Internal billing reconciliation

---

## 🎯 Key Performance Indicators (KPIs)

### Recommended Metrics
- Total Spending (AmoutinEUR)
- Transaction Count
- Average Transaction Value
- Overdue Payments (DueDate < Today)
- Payment Cycle Time (DateCreated to DueDate)
- Order-to-Invoice Time (POOrderedDate to DateCreated)
- Top 10 Suppliers by Volume
- Department Spending Distribution
- Currency Exposure Analysis
- Debit/Credit Balance
- Month-over-Month Trends
- Year-over-Year Growth

---

## 🔐 Data Privacy & Security

- **Anonymization**: Real supplier names replaced with fake names (SupplierName_Fake)
- **Sample Data**: This is a synthetic/test dataset for demonstration purposes
- **PII Protection**: No personal identifiable information included

---

## 📝 Technical Specifications

### File Properties
- **Encoding**: UTF-8
- **Delimiter**: Comma (,)
- **Header**: Row 1
- **Data Rows**: 10,000
- **File Size**: ~2.5 MB (approximate)

### Import Recommendations
- **Data Types**: 
  - Text fields: String
  - Amount fields: Decimal/Float
  - Date fields: Date (MM/DD/YYYY format)
  - Numeric codes: Integer

### Power BI/Fabric Import Settings
- **First Row as Headers**: Yes
- **Date Format**: MM/DD/YYYY (US format)
- **Currency Detection**: Manual (EUR, USD, GBP, BRL, CAD, MXN)
- **Null Handling**: Blank cells treated as null/empty

---

## 🔄 Relationships for Data Modeling

### Recommended Dimension Tables
1. **DimDepartment** (from Dept)
2. **DimCompany** (from Company)
3. **DimSupplier** (from SupplierName_Fake, SupplierNumber)
4. **DimSite** (from Site)
5. **DimService** (from Service)
6. **DimCurrency** (from DocumentCurrency, Ledgercurrency)
7. **DimNature** (from Nature, Major, Minor)
8. **DimDate** (from DateCreated, POOrderedDate, DueDate)

### Fact Table
- **FactFinancialTransactions** (current dataset)
  - Measures: All amount fields
  - Foreign Keys: Links to dimension tables

---

## 📚 Related Documentation

- [PowerBI_Prompts_And_Examples.md](./PowerBI_Prompts_And_Examples.md) - DAX measures and visualization prompts
- Original Dataset: `financial_dataset_usdate_10k.csv`

---

**Last Updated:** October 29, 2025  
**Dataset Version:** 1.0  
**Record Count:** 10,000 transactions
