# Hands-On: Workforce & HR Data Analysis

## 🎯 Hands-On Objectives

This hands-on session is designed to demonstrate to HR executives and managers the power of **Microsoft Fabric Data Agents**. You will discover how AI can transform complex workforce data analysis into natural conversations, enabling HR decision-makers to quickly gain insights about employee capacity, workload distribution, and resource planning without technical skills.

### Estimated Duration: 45 minutes
- Scenario 1: 20 minutes
- Scenario 2: 25 minutes

---

## 📋 Prerequisites

- Access to Microsoft Fabric with enabled capacity
- OneLake Explorer installed on Windows Desktop. Download Onelake Explorer ([here](https://www.microsoft.com/en-us/download/details.aspx?id=105222)).
- Dedicated workspace and lakehouse already created
- Provided `workforce_dataset_400.csv` file (see Data section)

---

### 🎭 Scenario 1: From Windows Desktop to Data Agents 


### Business Context
*You are an HR director who wants to quickly analyze employee workload and capacity data stored locally. Instead of waiting for the IT team or an HR analyst, you want to access workforce insights directly through AI.*

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
   - Navigate to the folder containing your HR data files
   - Locate the `workforce_dataset_400.csv` file in the `01_data` folder
     
##### 3. Data Loading
1. **Drag and Drop the File**
   - Drag `workforce_dataset_400.csv` from Windows Explorer
   - Drop into your OneLake workspace
 
 ![Onelake Explorer](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/Onelake%20Explorer.png)   

2. **Loading Validation**
   - Click right on the csv file, then ![Onelake](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/onelakeWE.png) and ![Sync Onelake](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/SyncOnelake.png)
   - Verify that the file appears in OneLake online
   - Note the automatic data preview showing employee workload data


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
   - Navigate to the "Files" click on "...>Upload>Upload files"section to upload the `workforce_dataset_400.csv` csv file that you found in the `01_data` folder.
   ![UploadFiles](https://github.com/EtienneSIG/WorkshopDataAgent/blob/main/img/Uploadfiles.png) 
   - Click right on csv file, then ![Load to tables](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/load%20to%20table.png) and !["New table"](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/New%20table.png)
   
   ![Load to tables](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/Load%20csv%20into%20table.png)

3. **Create the Data Agent**
   - Locate the newly created `workforce_dataset_400` table
   - Click the **"Add Data Agent"** button
   - Configure the Data Agent name: "HR Workforce Assistant"
   - Just talk to your HR data

#### 5. First Conversational Test
**Questions to ask the Data Agent:**
- Question 1 : "Can you describe the workforce data?"
- Question 2 : "How many employees do we have in total, and how are they distributed between internal and external?"
- Question 3 : "What's the average workload across all employees?"
- Question 4 : "Show me employees who are consistently overutilized (workload > 110%) for multiple months"
- Question 5 : "Which Domain Solutions has the highest average workload?"
- Question 6 : "Are there any seasonal patterns in workload? Which months are busiest?"
- Question 7 : "Compare workload between BS and AMN entities"
- Question 8 : "Identify underutilized employees (< 90% workload) who could take on more work"


### 💡 Key Points for HR Executives
- **Simplicity**: From your desktop to AI-powered HR insights in 5 clicks
- **Autonomy**: No need to wait for IT teams or HR analytics specialists
- **Immediacy**: Instant workforce insights in natural language
- **Employee Privacy**: Secure analysis within your Fabric environment

---

## 🏗️ Scenario 2: Building a Data Agent Based on a Semantic Model

### Business Context
*As a CHRO (Chief Human Resources Officer), you want to create a permanent AI assistant that understands your company's workforce structure and can answer complex questions about employee capacity, workload distribution, and resource planning.*

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
   - Name: "Workforce Capacity Model"
   - Click on "Editing" on right top

   ![EditingSemanticModel](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/EditingSemanticModel.png)

2. **Define DAX Measures**

   Click on ![NewMeasure](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/NewMeasure.png) for each measure to create
   ```dax
   // Total Employees
   Total Employees = COUNTROWS('workforce_dataset_400')

   // Average Workload
   Average Workload = 
   AVERAGE(
       'workforce_dataset_400'[% of work January] + 
       'workforce_dataset_400'[% work February] + 
       'workforce_dataset_400'[% work March] + 
       'workforce_dataset_400'[% work April] + 
       'workforce_dataset_400'[% work May] + 
       'workforce_dataset_400'[% work June] + 
       'workforce_dataset_400'[% work July] + 
       'workforce_dataset_400'[% work August] + 
       'workforce_dataset_400'[% work September] + 
       'workforce_dataset_400'[% work October] + 
       'workforce_dataset_400'[% work November] + 
       'workforce_dataset_400'[% work December]
   ) / 12

   // Overutilized Employees
   Overutilized Employees = 
   CALCULATE(
       COUNTROWS('workforce_dataset_400'),
       [Average Workload] > 1.1
   )

   // Underutilized Employees
   Underutilized Employees = 
   CALCULATE(
       COUNTROWS('workforce_dataset_400'),
       [Average Workload] < 0.9
   )

   // Internal Employees
   Internal Employees = 
   CALCULATE(
       COUNTROWS('workforce_dataset_400'),
       'workforce_dataset_400'[Type] = "INT"
   )

   // External Employees
   External Employees = 
   CALCULATE(
       COUNTROWS('workforce_dataset_400'),
       'workforce_dataset_400'[Type] = "EXT"
   )
   ```
#### 2. Advanced Data Agent Creation
1. **Access Data Agents**
   - Come back to workspace level, click "New Items" and search for "Data Agents"
   - Select "Create Data Agent"

2. **Data Agent Configuration**
   - **Name**: "HR Workforce Intelligence Assistant"
   - **Description**: "AI assistant for workforce capacity planning, workload analysis, and employee resource management"
   - **Data Source**: Select "Workforce Capacity Model"

3. **Agent Customization**
   - Define HR business context in instructions
   - Configure standard responses for frequent workforce questions
   - Enable automatic visualizations for capacity analysis

#### 3. Example of testing and optimization
**Sophisticated test scenarios:**

1. **Capacity Analysis**
   - "Which employees are consistently overutilized (>110%) across multiple months?"
   - "Identify underutilized resources (<90%) that could take on additional work"
   - "What's the average workload by Domain Solutions?"
   - "Compare capacity utilization between internal and external employees"
   - "Which company number has the highest/lowest average utilization?"

2. **Seasonal Patterns**
   - "Are there specific months with higher workload across all employees?"
   - "Identify seasonal trends by Domain Solutions"
   - "Which quarter has the peak workload?"
   - "Compare summer vs winter workload patterns"

3. **Workforce Distribution**
   - "How many employees are in each Domain Solutions?"
   - "What's the ratio of internal to external employees by company?"
   - "Distribution of employees across MASA status levels"
   - "Which entity (BS vs AMN) has more employees?"

4. **Risk Identification**
   - "List employees with workload >115% for 3+ consecutive months (burnout risk)"
   - "Find employees with <85% workload for 6+ months (potential redundancy)"
   - "Identify departments with consistently high utilization (hiring needs)"

5. **Comparative Analysis**
   - "Compare workload patterns between EVP, NEVP, and Groupe EVP"
   - "Average workload: BS vs AMN entities"
   - "Which Domain Solutions has the most balanced workload distribution?"
   - "Compare workload volatility across different employee types"

#### 4. Power BI Copilot Integration

Building on the semantic model created above, you can now leverage **Copilot for Power BI** to create sophisticated visualizations and dashboards for workforce analysis through natural language.

1. **Create Power BI Report**
   - In your Fabric workspace, select "New" > "Power BI Report"
   - Connect to your "Workforce Capacity Model" semantic model
   - The report canvas opens with access to your HR data and DAX measures

2. **Activate Copilot for Power BI**
   - Look for the **Copilot** button in the Power BI ribbon
   - Ensure Copilot is enabled in your tenant settings
   - Click on the Copilot pane to open the conversational interface

3. **Natural Language Report Creation**
   **Example prompts to try:**
   - "Create a chart showing average workload trends by Domain Solutions over the year"
   - "Build a table with employees who have workload >110% in any month"
   - "Generate a heatmap showing employee workload by month"
   - "Create a matrix showing average workload by Entity and Type"
   - "Show me a line chart of monthly workload trends across all employees"
   - "Build a clustered column chart comparing internal vs external employee workload"

4. **Advanced Copilot Features**
   - **Narrative Insights**: Ask Copilot to "Explain the workload patterns and identify departments at risk"
   - **Smart Recommendations**: Copilot suggests relevant visualizations based on your workforce data
   - **Auto-formatting**: Automatically applies best practices for HR dashboard formatting
   - **Data Storytelling**: Generate executive summaries like "Summarize workforce capacity issues and hiring needs"

5. **HR Executive Dashboard Creation**
   - Use Copilot to create a comprehensive workforce executive dashboard
   - Example: "Create an executive summary page with KPI cards for Total Employees, Average Workload, Overutilized Employees, and Underutilized Employees"
   - Add slicers for interactive filtering by Entity, Type, Company Number, Domain Solutions, and MASA Status
   - Configure drill-through capabilities for detailed employee workload analysis
   - "Add a KPI card showing the percentage of overutilized employees"
   - "Create a decomposition tree for workload by Entity → Type → Domain Solutions"
   - "Build a Q&A visual that answers 'Which employees need workload rebalancing?'"


### 💡 Power BI Copilot Benefits for HR Executives
- **Speed**: Create complex workforce reports in minutes instead of hours
- **Accessibility**: No need to learn Power BI interface complexities
- **Intelligence**: AI suggests the most appropriate visualizations for your HR data
- **Consistency**: Maintains corporate HR branding and best practices automatically



### 🚀 Advanced Features to Demonstrate

#### Contextual Intelligence
- Understanding HR-specific workforce terminology
- Recognition of critical capacity and workload KPIs
- Proactive analysis suggestions based on utilization trends

#### Dynamic Visualizations
- Automatic generation of relevant charts for workforce analysis
- Adaptive dashboards based on capacity questions
- Direct export to PowerPoint/Excel for HR presentations

#### HR Leadership Collaboration
- Insight sharing with executive team
- Question and answer history for workforce planning
- Critical capacity alerts for overutilized teams

---

## 📊 Dataset Available

### `workforce_dataset_400.csv` - Employee Workload & Capacity Data

#### Structure

| Column | Type | Description | Example |
|---------|------|-------------|---------|
| Entity | Text | Business entity | BS, AMN |
| Type | Text | Employee type | INT (Internal), EXT (External) |
| Company number | Integer | Company identifier | 415, 508, 407, 589 |
| MASA status | Text | Management level | EVP, NEVP, Groupe EVP |
| FirstName | Text | Employee first name | Timothy, Charles, Pamela |
| LastName | Text | Employee last name | Snyder, Woods, Simpson |
| Year | Integer | Data year | 2025 |
| Domain Solutions | Text | Department/Domain | ES, DIR, EC, SC, OPN, RDMF |
| % of work January - December | Decimal | Monthly workload % | 0.80 - 1.20 (80% - 120% capacity) |

#### Dataset Characteristics
- **400 employees** with complete 2025 workload data
- **12 months** of capacity metrics per employee
- **20 columns** total (8 employee attributes + 12 monthly workload percentages)
- **Workload range**: 0.80 (80% capacity) to 1.20 (120% capacity)
- **Normal capacity**: 1.0 = 100% utilization

#### Domains (Departments)
- **ES** - Enterprise Services
- **DIR** - Direction/Management
- **EC** - Enterprise Computing
- **SC** - Supply Chain
- **OPN** - Operations
- **RDMF** - Research, Development & Manufacturing

#### Management Levels (MASA Status)
- **EVP** - Executive Vice President
- **NEVP** - Non-Executive Vice President
- **Groupe EVP** - Group Executive Vice President
- **(Blank)** - External employees (no MASA status)

#### Key Analysis Scenarios
- **Capacity Planning**: Identify over/underutilized employees
- **Resource Allocation**: Balance workload across teams
- **Workforce Trends**: Seasonal patterns and monthly variations
- **Management Insights**: Compare utilization by management level
- **Department Analysis**: Workload patterns by Domain Solutions
- **Internal vs External**: Compare workforce type utilization
- **Risk Identification**: Detect burnout risks and redundancies
- **Hiring Needs**: Identify departments requiring additional staff

#### For detailed dataset documentation, see:
📄 [Workforce_Dataset_Description.md](./01_data/Workforce_Dataset_Description.md)

---

## ✅ Success Criteria

### For Scenario 1
- [ ] Successful data loading via OneLake Explorer
- [ ] Data Agent creation in less than 5 minutes
- [ ] Obtaining 3 relevant HR workforce insights through conversation
- [ ] Successfully identifying overutilized/underutilized employees

### For Scenario 2
- [ ] Functional semantic model with HR-specific DAX measures
- [ ] Data Agent responding to complex workforce capacity questions
- [ ] Automatic generation of adapted HR visualizations
- [ ] Clear identification of capacity planning opportunities

---

## 🎓 Key Messages for HR Executives

### Immediate ROI
- **Time-to-Insight Reduction**: From days to minutes for workforce analysis
- **Decision Autonomy**: No more waiting for HR analytics teams
- **Data Democratization**: Workforce insights accessible to all HR managers

### Digital HR Transformation
- **Conversational AI**: Natural interface with workforce data
- **Self-Service HR Analytics**: Empower HR team with instant insights
- **Intelligent Governance**: Security and employee privacy maintained

### Strategic Workforce Management
- **Faster Decisions**: Increased responsiveness to capacity issues
- **Deeper Insights**: AI detects hidden workforce patterns
- **Proactive Planning**: Identify burnout risks and hiring needs early
- **Resource Optimization**: Better workload distribution across teams

---

## 📞 Support and Resources

- **Official Documentation**: [Microsoft Fabric Data Agents](https://learn.microsoft.com)
- **Additional Training**: Microsoft Learn paths
- **Technical Support**: Your IT team or Microsoft partner
- **HR Analytics Best Practices**: Microsoft HR Analytics resources

---


*This hands-on was designed to demonstrate the transformative power of Microsoft Fabric Data Agents for HR workforce management. The goal is to show how AI can become a true decision-making assistant for HR leaders in capacity planning, workload optimization, and employee resource management.*




































