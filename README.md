# Hands-On: Contract & Operations Analysis

## 🎯 Hands-On Objectives

This hands-on session is designed to demonstrate to executives the power of **Microsoft Fabric Data Agents**. You will discover how AI can transform complex operational data analysis into natural conversations, enabling decision-makers to quickly gain insights without technical skills.

### Estimated Duration: 45 minutes
- Scenario 1: 20 minutes
- Scenario 2: 25 minutes

---

## 📋 Prerequisites

- Access to Microsoft Fabric with enabled capacity
- OneLake Explorer installed on Windows Desktop. Download Onelake Explorer ([here](https://www.microsoft.com/en-us/download/details.aspx?id=105222)).
- Dedicated workspace and lakehouse already created
- Provided `financial_dataset_usdate_10k.csv` file (see Data section)

---

### 🎭 Scenario 1: From Windows Desktop to Data Agents 


### Business Context
*You are an operations director who wants to quickly analyze contract and operational data stored locally. Instead of waiting for the IT team or an analyst, you want to access insights directly through AI.*

#### Detailed Steps
## Load data via OneLake Explorer (optionnal)
## If you don't do use Onelake Explorer, go directly to step [Load data via Onelake](https://github.com/EtienneSIG/WorkshopDataAgent/tree/main?tab=readme-ov-file#load-date-via-onelake)
##### 1. Connection via OneLake Explorer
1. **Launch OneLake Explorer**
   - Right-click on the OneLake icon in the taskbar
   - Select "Open OneLake Explorer"
   
2. **Authentication**
   - Sign in with your Microsoft 365 credentials
   - Select the appropriate Fabric workspace

##### 2. Starting from Windows Desktop
1. **Open Windows Explorer**
   - Download the 'fabric_logs_sample.csv' file [here](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/data/fabric_logs_sample.csv)
   - Navigate to the folder containing your data files
   - Locate the `fabric_logs_sample.csv` file
     
##### 3. Data Loading
1. **Drag and Drop the File**
   - Drag `fabric_logs_sample.csv` from Windows Explorer
   - Drop into your OneLake workspace
 
 ![Onelake Explorer](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/Onelake%20Explorer.png)   

2. **Loading Validation**
   - Click right on the csv file, then ![Onelake](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/onelakeWE.png) and ![Sync Onelake](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/SyncOnelake.png)
   - Verify that the file appears in OneLake online
   - Note the automatic data preview


##### 4. Data Agent Activation
1. **Access Fabric Online**
   - Click right on the file "View item online" from OneLake Explorer
   - Navigate to the "Files" section to see your csv file
   - Click right on csv file, then ![Load to tables](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/load%20to%20table.png) and !["New table"](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/New%20table.png)
   
   ![Load to tables](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/Load%20csv%20into%20table.png)
## Load data via Onelake
1. **Access Fabric Online**
   - Go on powerbi.com and log in. Go to your workspace "Workshop_User01" 
   - then go to the lakehouse "workshop_lakehouse"
   - Navigate to the "Files" click on "...>Upload>Upload files"section to ipload your csv file
   - Click right on csv file, then ![Load to tables](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/load%20to%20table.png) and !["New table"](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/New%20table.png)
   
   ![Load to tables](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/Load%20csv%20into%20table.png)

3. **Create the Data Agent**
   - Locate the newly created `fabric_logs_sample` table
   - Click the **"Add Data Agent"** button
   - Configure the Data Agent name: "Operations Assistant"
   - Just talk to your data

#### 5. First Conversational Test
**Questions to ask the Data Agent:**
- Question 1 : "Can you describe the data?"
- Answer 1 :   image to upload
- Question 2 - a:  "What are the main zones and their distribution?"
- Answer 2 - a :
- Question 2 - b:  "When I said zone, it means site"
- Answer 2 - b :
- Question 2 - c:  "When I said zone, it means site"
- Answer 2 - c : 
- Question 3 - a : "Show me the avg(amoutineur) by site per year"
- Answer 3 - a :
- Question 3 - b : "yes" or "I Would like forecasted values based on these trends for 2026, or any specific site/year details?"
- Answer 3 - b : 

   ![Talk to your data](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/Talk%20to%20your%20data.png)

### 💡 Key Points for Executives
- **Simplicity**: From your desktop to AI in 5 clicks
- **Autonomy**: No need to wait for technical teams
- **Immediacy**: Instant insights in natural language

---

## 🏗️ Scenario 2: Building a Data Agent Based on a Semantic Model

### Business Context
*As a COO, you want to create a permanent AI assistant that understands your company's operational structure and can answer complex questions across multiple data sources.*

### Solution Architecture
```
📊 Data Sources
    ↓
🔄 Fabric Semantic Model
    ↓
🤖 Intelligent Data Agent
    ↓
💬 Conversational Interface
```

### Construction Steps

#### 1. Semantic Model Construction
1. **Create New Semantic Model**
   - In Fabric, select "New" > "Semantic Model"
   - Name: "Corporate Operations Model"
   - Click on "Editing" on right top

   ![EditingSemanticModel](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/EditingSemanticModel.png)

2. **Define DAX Measures**

   Click on ![NewMeasure](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/NewMeasure.png) for each measure to create
   ```dax
   Total Forecast 24 = SUM('fabric_logs_sample'[Fcst 24 tx 24])
   Total Forecast 25 = SUM('fabric_logs_sample'[Fcst 25 tx 25])
   Total Forecast 26 = SUM('fabric_logs_sample'[fcst 26x forecast taux 25])
   Forecast Growth = [Total Forecast 25] - [Total Forecast 24]
   Forecast Growth % = DIVIDE([Forecast Growth], [Total Forecast 24], 0)
   Contract Count = COUNTROWS('fabric_logs_sample')
   ```

4. **Configure Hierarchies**
   - Create geographical hierarchy: Zone > Company > Domain
   - Create contract hierarchy: Domain > Generic Contracts > Reference Name
   
   For this, in Data > Tables section (on the right), click right on the field who will be the high level the hierarchy.
   ![CreateHierarchy](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/CreateHierarchy.png)

   And drag and drop the other field you would like to add to your hierarchy


#### 2. Advanced Data Agent Creation
1. **Access Data Agents**
   - Come back to workspace level, click "New Items" and search for "Data Agents"
   - Select "Create Data Agent"

2. **Data Agent Configuration**
   - **Name**: "Executive Operations Assistant"
   - **Description**: "AI assistant for executive operations and contract analysis"
   - **Data Source**: Select "Corporate Operations Model"

3. **Agent Customization**
   - Define business context in instructions
   - Configure standard responses for frequent questions
   - Enable automatic visualizations

#### 3. Testing and Optimization
**Sophisticated test scenarios:**

1. **Performance Analysis**
   - "How are our different zones performing in terms of forecast growth?"
   - "Identify concerning trends across companies and domains"
   - "Which contracts have the highest variance between forecast years?"

2. **Predictions and Recommendations**
   - "Based on current trends, what will be our forecast for 2026?"
   - "Which zones should we focus on for growth opportunities?"
   - "Compare forecast performance across different currency zones"

3. **Comparative Analysis**
   - "Compare EMEA vs APAC vs AMERICAS performance"
   - "Show me the most significant contract variations by domain"
   - "Analyze the distribution of contracts by company and zone"

#### 4. Power BI Copilot Integration

Building on the semantic model created above, you can now leverage **Copilot for Power BI** to create sophisticated visualizations and dashboards through natural language.

1. **Create Power BI Report**
   - In your Fabric workspace, select "New" > "Power BI Report"
   - Connect to your "Corporate Operations Model" semantic model
   - The report canvas opens with access to your data and DAX measures

2. **Activate Copilot for Power BI**
   - Look for the **Copilot** button in the Power BI ribbon
   - Ensure Copilot is enabled in your tenant settings
   - Click on the Copilot pane to open the conversational interface

3. **Natural Language Report Creation**
   **Example prompts to try:**
   - "Create a chart showing forecast trends by zone"
   - "Show me a map visualization of contracts distribution across zones"
   - "Build a table with the top 10 contracts by forecast value"
   - "Generate a waterfall chart showing forecast growth from 2024 to 2026"
   - "Create a matrix showing forecast values by company and domain"

4. **Advanced Copilot Features**
   - **Narrative Insights**: Ask Copilot to "Explain the forecast performance trends across zones"
   - **Smart Recommendations**: Copilot suggests relevant visualizations based on your data
   - **Auto-formatting**: Automatically applies best practices for chart formatting
   - **Data Storytelling**: Generate executive summaries with key insights

5. **Executive Dashboard Creation**
   - Use Copilot to create a comprehensive executive dashboard
   - Example: "Create an executive summary page with KPI cards for total forecast 24, 25, 26, and growth percentage"
   - Add slicers for interactive filtering by zone, company, and domain
   - Configure drill-through capabilities for detailed contract analysis

6. **Collaborative Features**
   - **Q&A Visual**: Add a Q&A visual that allows users to ask questions in natural language
   - **Comments and Annotations**: Use Copilot to generate insights comments on visuals
   - **Report Narration**: Generate automated narrative explanations of trends and anomalies

### 💡 Power BI Copilot Benefits for Executives
- **Speed**: Create complex reports in minutes instead of hours
- **Accessibility**: No need to learn Power BI interface complexities
- **Intelligence**: AI suggests the most appropriate visualizations for your data
- **Consistency**: Maintains corporate branding and best practices automatically



### 🚀 Advanced Features to Demonstrate

#### Contextual Intelligence
- Understanding company-specific operational terminology
- Recognition of critical performance KPIs
- Proactive analysis suggestions based on contract trends

#### Dynamic Visualizations
- Automatic generation of relevant charts for multi-zone analysis
- Adaptive dashboards based on questions
- Direct export to PowerPoint/Excel

#### Executive Collaboration
- Insight sharing with leadership team
- Question and answer history
- Critical metrics alerts

---

## 📊 Datasets Available

### 1. `fabric_logs_sample.csv` - Original Sample Data

#### Structure

| Column | Type | Description | Example |
|---------|------|-------------|---------|
| Rgpt New Report | Text | Report status | OK, NA |
| Detail | Text | Detail level | BS, XX, NA |
| Supplier | Numeric | Supplier code | 0-5 |
| Rgpt 2 | Numeric | Report metric 2 | 0-5 |
| Rgpt EURSI | Numeric | European SI metric | 0-5 |
| Zone | Text | Geographic zone | EMEA, APAC, AMERICAS |
| Fcst 24 tx 24 | Numeric | Forecast 2024 rate | Various rates |
| Fcst 25 tx 25 | Numeric | Forecast 2025 rate | Various rates |
| fcst 26x forecast taux 25 | Numeric | Forecast 2026 rate | Various rates |
| company | Text | Company identifier | 414 - SML, 415 - ABC, 416 - XYZ |
| Domain | Text | Business domain | ASSI, FIN, OPS, BS |
| DOMAIN | Text | Domain code | BS |
| SL | Text | Service level | (Optional) |
| Sourcing DB currency | Text | Source currency | USD, EUR, BRL |
| Company currency | Text | Company currency | USD, EUR, BRL |
| Dashboard currency Use | Text | Dashboard currency | USD, EUR |
| Generic Contracts | Text | Generic contract ID | BSS-Train, BSS-Taxes, etc. |
| Reference Name | Text | Full contract name | 415 - ABC BSS-Train |
| Domain (duplicate) | Text | Domain repeated | BS |

#### Dataset Characteristics
*The CSV file contains 1000+ lines of operational data representing contracts across multiple zones, companies, and domains with multi-year forecast data in different currencies.*

---

### 2. `generated_dataset_500k.csv` - Large-Scale Financial Data (500,000 rows)

A comprehensive financial transactions dataset generated for testing Data Agents at scale with realistic enterprise data patterns.

#### Structure (30 columns)

| Column | Type | Description | Example Values |
|---------|------|-------------|----------------|
| SupplierName | Text | Supplier company name | UUYWS OTJ INC, ODENK MSP INC, etc. (250+ unique values) |
| Dept | Text | Department | BSS, DIR, IN, MQ |
| Service | Text | Service type | DIR, EUX, DAP, NET, RD, etc. (26 services) |
| NatAnal | Text | Nature of analysis | External Resources, Training, Travels, etc. |
| ModuleName | Text | Module identifier | AP, GL, INV, PA, PO |
| Company | Text | Company name | TechnoGlobal Industries, Meridian Solutions Corp, etc. (5 companies) |
| Account | Text | Account code | 6115000, 6183000, 6250000, etc. (200+ accounts) |
| Site | Text | Site location | RIO, MAN, MTC, MXA, PP1, etc. |
| Section | Text | Section code | 14700A, 14320G, 14360B, etc. (33 sections) |
| Structure | Text | Structure code | 7956, 7950 |
| Intercompany | Text | Intercompany code | 0, 589, 511, 409, etc. |
| Nature | Text | Transaction nature | N22_FE_F, N23_FE_TRAVEL_F, etc. |
| Major | Text | Major category | MAJ09_General_Overhead_F, MAJ05_Maintenance_V, etc. |
| Minor | Text | Minor category | MIN0918, MIN0940, MIN0935, etc. (56 categories) |
| GroupSectionAndDescription | Text | Group section details | ISIT BSS IS Region managers, etc. |
| LedgerName | Text | Ledger identifier | BR_414_PL_BRL, US_415_PL_USD, etc. |
| Source | Text | Transaction source | Payables, Spreadsheet, Manual, etc. |
| Category | Text | Transaction category | Purchase Invoices, GL_Adjustment, etc. (35 categories) |
| Supplier Number | Numeric | Supplier ID | 1-50 |
| SupplierName_Fake | Text | Fake supplier name | Global Tech Solutions, Premier Manufacturing Co, etc. (50 suppliers) |
| DocumentCurrency | Text | Document currency | BRL, USD, EUR, MXN, CAD, GBP |
| Ledgercurrency | Text | Ledger currency | BRL, USD, MXN, CAD |
| AmoutinEUR | Numeric | Amount in EUR | -10,000 to 1,000,000 |
| DebitEnteredAmount | Numeric | Debit amount | 0 to 1,000 |
| CreditEnteredAmount | Numeric | Credit amount | 0 or 100-1,000 (when Debit = 0) |
| DebitAccountedAmount | Numeric | Accounted debit | 0 to 1,000 |
| CreditAccountedAmount | Numeric | Accounted credit | 0 or 100-1,000 (when Debit = 0) |
| DateCreated | Date | Creation date | 2023/01/01 - 2025/11/01 |
| POOrderedDate | Date | PO order date | >= DateCreated |
| DueDate | Date | Due date | >= POOrderedDate |

#### Dataset Characteristics
- **500,000 rows** of realistic financial transaction data
- **30 columns** covering accounting, procurement, and operational dimensions
- **Date range**: January 1, 2023 - November 1, 2025
- **Multi-currency**: EUR, USD, BRL, MXN, CAD, GBP
- **Business rules enforced**:
  - Debit/Credit mutual exclusivity
  - Date chronological constraints (DateCreated < POOrderedDate < DueDate)
  - Realistic amount distributions

#### Use Cases
- **Performance Testing**: Test Data Agents with large-scale enterprise data
- **Advanced Analytics**: Complex multi-dimensional analysis (by dept, service, company, supplier, etc.)
- **Financial Analysis**: Budget analysis, variance tracking, multi-currency reconciliation
- **Trend Analysis**: Time-series analysis over 2+ years of data
- **Supplier Performance**: Analyze 250+ suppliers across multiple dimensions

---

### 3. `generated_dataset_10k.csv` - Medium-Scale Financial Data (10,000 rows)

A smaller version of the 500k dataset, ideal for quick testing and demonstrations.

#### Structure
Identical structure to `generated_dataset_500k.csv` (same 30 columns)

#### Dataset Characteristics
- **10,000 rows** - manageable size for rapid testing
- Same data quality and business rules as the 500k version
- Perfect for:
  - Quick Data Agent prototyping
  - Demonstration scenarios
  - Development and testing
  - Workshop sessions

---

### 📂 Data Generation

All large datasets are generated using the `generate_large_dataset.py` script which:
- Ensures data consistency and business rule compliance
- Generates realistic fake company and supplier names
- Maintains referential integrity across dimensions
- Applies proper date sequencing constraints
- Enforces debit/credit accounting rules

To regenerate or create custom datasets, modify the script configuration:
```python
OUTPUT_FILE = "data/your_custom_file.csv"
NUM_ROWS = 100000  # Your desired row count
```

### Dataset Characteristics (Combined)

### Key Analysis Scenarios
- **Geographic Performance**: Compare EMEA, APAC, and AMERICAS zones
- **Forecast Evolution**: Track forecast trends from 2024 to 2026
- **Currency Analysis**: Analyze multi-currency operations
- **Contract Performance**: Monitor contract-level metrics
- **Company Comparison**: Compare performance across companies (SML, ABC, XYZ)
- **Domain Analysis**: Analyze operations by business domain (ASSI, FIN, OPS)

---

## ✅ Success Criteria

### For Scenario 1
- [ ] Successful data loading via OneLake Explorer
- [ ] Data Agent creation in less than 5 minutes
- [ ] Obtaining 3 relevant insights through conversation

### For Scenario 2
- [ ] Functional semantic model with DAX measures
- [ ] Data Agent responding to complex questions
- [ ] Automatic generation of adapted visualizations

---

## 🎓 Key Messages for Executives

### Immediate ROI
- **Time-to-Insight Reduction**: From days to minutes
- **Decision Autonomy**: No more technical dependencies
- **Data Democratization**: Accessible at all levels

### Digital Transformation
- **Conversational AI**: Natural interface with data
- **Self-Service Analytics**: Team empowerment
- **Intelligent Governance**: Security and control maintained

### Competitive Advantage
- **Faster Decisions**: Increased responsiveness
- **Deeper Insights**: AI detects hidden patterns
- **Continuous Innovation**: Evolving Microsoft platform

---

## 📞 Support and Resources

- **Official Documentation**: [Microsoft Fabric Data Agents](https://learn.microsoft.com)
- **Additional Training**: Microsoft Learn paths
- **Technical Support**: Your IT team or Microsoft partner

---


*This hands-on was designed to demonstrate the transformative power of Microsoft Fabric Data Agents in an executive context. The goal is to show how AI can become a true decision-making assistant for leaders.*

































