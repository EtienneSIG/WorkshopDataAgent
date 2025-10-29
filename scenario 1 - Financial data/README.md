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
   - Locate the `financial_dataset_usdate_10k.csv` file
     
##### 3. Data Loading
1. **Drag and Drop the File**
   - Drag `financial_dataset_usdate_10k.csv` from Windows Explorer
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
   - Navigate to the "Files" click on "...>Upload>Upload files"section to upload the `financial_dataset_usdate_10k.csv` csv file that you found in the data section.
   ![UploadFiles](https://github.com/EtienneSIG/WorkshopDataAgent/blob/main/img/Uploadfiles.png) 
   - Click right on csv file, then ![Load to tables](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/load%20to%20table.png) and !["New table"](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/New%20table.png)
   
   ![Load to tables](https://github.com/EtienneSIG/-HO-Microsoft-Fabric-DataAgent/blob/main/img/Load%20csv%20into%20table.png)

3. **Create the Data Agent**
   - Locate the newly created `financial_data` table
   - Click the **"Add Data Agent"** button
   - Configure the Data Agent name: "Operations Assistant"
   - Just talk to your data

#### 5. First Conversational Test
**Questions to ask the Data Agent:**
- Question 1 : "Can you describe the data?"
- Answer 1 :
  ![Question1](https://github.com/EtienneSIG/WorkshopDataAgent/blob/main/img/question1.png)
- Question 2 - a:  "What are the main zones and their distribution?"
- Answer 2 - a :
  ![Question2a](https://github.com/EtienneSIG/WorkshopDataAgent/blob/main/img/Question%202a.png)
- Question 2 - b:  "When I said zone, it means site"
- Answer 2 - b :
  ![Question2b](https://github.com/EtienneSIG/WorkshopDataAgent/blob/main/img/Question%202b.png)
- Question 2 - c:  "When I said zone, it means site"
- Answer 2 - c :
  ![Question2c](https://github.com/EtienneSIG/WorkshopDataAgent/blob/main/img/Question%202c.png)
- Question 3 - a : "Show me the avg(amoutineur) by site per year"
- Answer 3 - a :
  ![Question3a](https://github.com/EtienneSIG/WorkshopDataAgent/blob/main/img/question%203%20-%20a.png)
- Question 3 - b : "yes" or "I Would like forecasted values based on these trends for 2026, or any specific site/year details?"
- Answer 3 - b :
  ![Question3b](https://github.com/EtienneSIG/WorkshopDataAgent/blob/main/img/question%203b.png)


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
   // Total Spending
   Total Spending = SUM('FinancialData'[AmoutinEUR])

   // Number of Transactions
   Number of Transactions = COUNTROWS('FinancialData')
   ```
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

#### 3. Example of testing and optimization
**Sophisticated test scenarios:**

1. Performance Analysis
   - "How are our different departments (Dept) performing in terms of average spending?"
   - "Identify concerning average trends across companies and sites"
   - "Which suppliers have the highest average transaction volumes and amounts?"
   - "What's the average spending pattern across different Nature categories (N81_MASA_F, N30_ENERGY_V, etc.)?"
   - "Compare average spending performance across different ledgers (MX_589_PL_MXN, BR_414_PL_BRL, etc.)"
2. Predictions and Recommendations
   - "Based on current trends, what will be our aveerage spending forecast for Q1 2026?"
   - "Which departments should we focus on for cost optimization?"
   - "Predict overdue payments based on historical patterns"
   - "What's the expected spending by Service category for next quarter?"
   - "Identify suppliers with increasing transaction trends"
3. Comparative Analysis
   - "Compare  average spending across BSS vs IN vs DIR vs MQ departments"
   - "Show me the most significant  average spending variations by NatAnal category"
   - "Analyze the  average distribution of transactions by Company and Site"
   - "Compare  average Debit vs  average Credit patterns across different Sources"
   - "What's the difference in spending between document currencies (EUR vs BRL vs GBP vs USD)?"
4. Additional Operational Questions
   - "Which sites have the longest payment cycles (DateCreated to DueDate)?"
   - "What's the average transaction amount by Category (GL_Intercompany_Reversal, Inventory, etc.)?"
   - "Identify suppliers with negative transactions - why are we receiving credits?"
   - "How does average spending vary across different Intercompany codes?"
   - "What's the lead time between PO Order Date and Document Creation?"
   - "Which Major/Minor classification combinations have the highest average spending?"

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
   - "Create a chart showing average spending trends by Department over time"
   - "Build a table with the top 10 suppliers by average transaction amount"
   - "Generate a waterfall chart showing average net amount flow from Debit to Credit"
   - "Create a matrix showing average spending by Company and Service"

4. **Advanced Copilot Features**
   - **Narrative Insights**: Ask Copilot to "Explain the spending performance trends across departments and companies"
   - **Smart Recommendations**: Copilot suggests relevant visualizations based on your financial data
   - **Auto-formatting**: Automatically applies best practices for financial chart formatting
   - **Data Storytelling**: Generate executive summaries with key insights like "Summarize top spending areas and payment trends"

6. **Executive Dashboard Creation**
   - Use Copilot to create a comprehensive financial executive dashboard
   - Example: "Create an executive summary page with KPI cards for Total Spending, Number of Transactions, Overdue Amount, and Average Transaction Value"
   - Add slicers for interactive filtering by Department, Company, Supplier, and DateCreated
   - Configure drill-through capabilities for detailed supplier and transaction analysis
   - "Add a KPI card showing YoY spending growth percentage"
   - "Create a decomposition tree for spending by Dept → Service → NatAnal"
   - "Build a Q&A visual that answers 'What are the top 5 suppliers by spending?'"


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





































