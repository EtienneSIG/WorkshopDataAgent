# Microsoft Fabric Data Agents Workshop

## 🎯 Workshop Overview

Welcome to this hands-on workshop demonstrating the transformative power of **Microsoft Fabric Data Agents**. This comprehensive training showcases how AI can revolutionize data analysis across different business domains, enabling executives and managers to gain instant insights through natural language conversations with their data.

### 🌟 Workshop Goals

- **Demonstrate AI-Powered Analytics**: Experience how Data Agents make complex data analysis accessible to non-technical users
- **Enable Self-Service Insights**: Empower business leaders to answer their own questions without waiting for IT or analytics teams
- **Showcase Real-World Scenarios**: Learn through practical use cases from Finance and HR domains
- **Accelerate Decision-Making**: Transform data-to-insight time from days to minutes

### ⏱️ Total Duration: 90 minutes
- Introduction: 15 minutes
- Scenario 1 (Financial Data): 45 minutes
- Scenario 2 (HR Data): 45 minutes
- Q&A and Wrap-up: 15 minutes

---

## 📋 Prerequisites

### Technical Requirements
- ✅ Access to Microsoft Fabric with enabled capacity
- ✅ Power BI Pro or Premium Per User license
- ✅ OneLake Explorer installed on Windows Desktop ([Download here](https://www.microsoft.com/en-us/download/details.aspx?id=105222))
- ✅ Dedicated Fabric workspace created
- ✅ Lakehouse created in your workspace

### Provided Assets
- 📊 `financial_dataset_usdate_10k.csv` - 10,000 financial transactions
- 👥 `workforce_dataset_400.csv` - 400 employee workload records
- 📖 Complete documentation for both datasets

### Skills Required
- No coding skills needed
- Basic understanding of business operations
- Familiarity with Excel/data tables

---

## 🎭 Scenario 1: Financial Data Analysis

### 📊 Business Context
**Role**: Operations/Finance Director  
**Challenge**: Analyze 10,000 financial transactions to identify spending patterns, supplier performance, and payment trends  
**Goal**: Gain instant insights without waiting for finance analysts or IT teams

### 🗂️ Dataset Overview
- **File**: `financial_dataset_usdate_10k.csv`
- **Records**: 10,000 financial transactions
- **Period**: 2023-2025
- **Dimensions**: 30 columns including:
  - Suppliers, Departments, Companies, Sites
  - Multi-currency transactions (EUR, USD, GBP, BRL, CAD, MXN)
  - Debit/Credit amounts
  - Dates: Created, PO Ordered, Due Date
  - Account classifications and ledger information

### 🎯 Key Learning Objectives
1. **Quick Data Loading**: Upload CSV from desktop to Fabric in minutes
2. **Instant Data Agent Creation**: Create AI assistant with one click
3. **Natural Language Queries**: Ask business questions in plain English
4. **Financial Insights**: Discover spending patterns, supplier risks, overdue payments

### 💡 Example Questions You'll Ask
- "What are the top 10 suppliers by spending?"
- "Show me spending trends by department over time"
- "Which sites have overdue payments?"
- "Compare spending across different companies"
- "Identify suppliers with negative transactions"
- "What's the average payment cycle by department?"

### 📈 Expected Outcomes
- Identify cost optimization opportunities
- Detect payment delays and risks
- Understand supplier concentration
- Analyze multi-currency exposure
- Discover seasonal spending patterns

### 📂 Location
[`scenario 1 - Financial data/`](./scenario%201%20-%20Financial%20data/)
- 📄 [README.md](./scenario%201%20-%20Financial%20data/README.md) - Complete step-by-step guide
- 📁 [01_data/](./scenario%201%20-%20Financial%20data/01_data/)
  - 📊 `financial_dataset_usdate_10k.csv` - Dataset
  - 📖 `Dataset_Description.md` - Detailed documentation

---

## 👥 Scenario 2: HR Workforce Analysis

### 📊 Business Context
**Role**: HR Director / CHRO  
**Challenge**: Analyze 400 employees' monthly workload data to optimize capacity planning and identify burnout risks  
**Goal**: Make data-driven decisions about resource allocation, hiring needs, and workload balancing

### 🗂️ Dataset Overview
- **File**: `workforce_dataset_400.csv`
- **Records**: 400 employees
- **Period**: Full year 2025 (12 months)
- **Dimensions**: 20 columns including:
  - Employee details (Name, Type, Entity)
  - Management levels (EVP, NEVP, Groupe EVP)
  - Company numbers and domain assignments
  - Monthly workload percentages (Jan-Dec)
  - Internal vs External workforce classification

### 🎯 Key Learning Objectives
1. **HR Analytics at Scale**: Analyze capacity across entire workforce
2. **Semantic Model Creation**: Build reusable HR data model with DAX measures
3. **Advanced Data Agent**: Create sophisticated AI assistant for HR insights
4. **Power BI Copilot Integration**: Generate executive dashboards through conversation

### 💡 Example Questions You'll Ask
- "Which employees are overutilized (>110% workload) consistently?"
- "Show me underutilized resources who can take on more work"
- "What are the seasonal workload patterns by department?"
- "Compare capacity utilization between internal and external employees"
- "Which domains need additional hiring based on sustained high workload?"
- "Identify burnout risks (>115% for 3+ months)"
- "Compare workload across management levels"

### 📈 Expected Outcomes
- Identify hiring needs by department
- Detect burnout risks early
- Optimize resource allocation
- Balance workload distribution
- Plan for seasonal capacity changes
- Compare internal vs external workforce efficiency

### 🔧 Advanced Features Demonstrated
- **Semantic Model**: Build reusable data model with custom DAX measures
- **Power BI Copilot**: Generate visualizations through natural language
- **Executive Dashboards**: Create KPI cards, charts, and reports automatically
- **Drill-Through Analysis**: Navigate from summaries to detailed employee data

### 📂 Location
[`scenario 2 - HR data/`](./scenario%202%20-%20HR%20data/)
- 📄 [README.md](./scenario%202%20-%20HR%20data/README.md) - Complete step-by-step guide
- 📁 [01_data/](./scenario%202%20-%20HR%20data/01_data/)
  - 👥 `workforce_dataset_400.csv` - Dataset
  - 📖 `Workforce_Dataset_Description.md` - Detailed documentation

---

## 🎓 Key Learning Outcomes

### For Business Users
- ✅ **Self-Service Analytics**: Answer your own questions without IT dependency
- ✅ **Natural Language Interface**: No SQL, DAX, or coding required
- ✅ **Instant Insights**: Transform exploration time from days to minutes
- ✅ **Multi-Domain Application**: Same approach works for Finance, HR, Sales, Operations

### For Data Professionals
- ✅ **Semantic Models**: Build reusable data models with governance
- ✅ **DAX Measures**: Create enterprise-grade calculations
- ✅ **Data Agent Configuration**: Customize AI assistants for specific domains
- ✅ **Integration**: Combine Data Agents with Power BI Copilot

### For Executives
- ✅ **ROI**: Accelerate decision-making across organization
- ✅ **Digital Transformation**: Enable AI-powered analytics at scale
- ✅ **Democratization**: Empower all levels with data access
- ✅ **Competitive Advantage**: Faster insights = better decisions

---

## 📊 Comparison: Scenario 1 vs Scenario 2

| Aspect | Scenario 1: Financial | Scenario 2: HR |
|--------|----------------------|----------------|
| **Domain** | Finance & Operations | Human Resources |
| **Dataset Size** | 10,000 transactions | 400 employees |
| **Time Period** | 2023-2025 (3 years) | 2025 (12 months) |
| **Complexity** | Medium | Medium-Advanced |
| **Key Metrics** | Spending, Suppliers, Payments | Workload, Capacity, Utilization |
| **Primary Users** | Finance Directors, COOs | HR Directors, CHROs |
| **Data Agent Type** | Basic + Advanced | Advanced with Semantic Model |
| **Visualizations** | Financial charts, tables | Capacity heatmaps, trend lines |
| **Business Value** | Cost optimization, risk detection | Resource planning, burnout prevention |
| **Advanced Features** | Semantic model, DAX | Semantic model, DAX, Complex KPIs |

---

## 💡 Real-World Applications

### Financial Domain
- **Budget Monitoring**: Track spending vs budget in real-time
- **Supplier Risk Management**: Identify concentration and payment risks
- **Cash Flow Forecasting**: Predict future cash needs based on payment patterns
- **Audit Trail**: Quick access to transaction details for compliance
- **Multi-Currency Analysis**: Consolidate global financial data

### HR Domain
- **Capacity Planning**: Right-size teams based on actual workload
- **Burnout Prevention**: Identify and address overwork early
- **Resource Optimization**: Balance workload across departments
- **Hiring Forecasting**: Data-driven headcount planning
- **Performance Management**: Workload context for performance reviews

### Other Potential Domains
- **Sales**: Pipeline analysis, forecast accuracy, territory performance
- **Supply Chain**: Inventory optimization, supplier lead times, demand forecasting
- **Customer Service**: Ticket analysis, response times, satisfaction trends
- **Manufacturing**: Production efficiency, quality metrics, downtime analysis

---

## 🔑 Key Features Demonstrated

### Data Agents Core Capabilities
- ✨ **Natural Language Understanding**: Ask questions as you would to a colleague
- 🔍 **Intelligent Data Exploration**: AI suggests relevant insights
- 📊 **Automatic Visualizations**: Charts generated based on question context
- 🎯 **Contextual Awareness**: Remembers conversation history
- 🔒 **Security & Governance**: Respects Fabric data permissions

### Power BI Copilot Integration
- 🎨 **Dashboard Generation**: Create entire dashboards through conversation
- 📈 **Smart Recommendations**: AI suggests appropriate chart types
- 🎭 **Narrative Insights**: Automatic written summaries of data patterns
- ⚡ **Rapid Prototyping**: Test different visualizations quickly

### Semantic Models
- 🏗️ **Reusable Data Models**: Build once, use everywhere
- 📐 **DAX Measures**: Enterprise-grade calculations
- 🔗 **Relationships**: Connect multiple data sources
- 🎯 **Business Logic**: Embed domain knowledge in the model

---

## ✅ Success Criteria

By the end of this workshop, you should be able to:

### Scenario 1 (Financial)
- [ ] Upload financial data to Fabric lakehouse
- [ ] Create a Data Agent in under 5 minutes
- [ ] Ask 5+ financial questions and get meaningful answers
- [ ] Identify top suppliers and spending patterns
- [ ] Build a basic semantic model with DAX measures

### Scenario 2 (HR)
- [ ] Load workforce data and create HR Data Agent
- [ ] Identify overutilized and underutilized employees
- [ ] Build "Workforce Capacity Model" with 6+ DAX measures
- [ ] Create advanced "HR Intelligence Assistant"
- [ ] Generate executive HR dashboard with Power BI Copilot

### Overall
- [ ] Understand when to use Data Agents vs traditional BI tools
- [ ] Explain the value of semantic models
- [ ] Demonstrate self-service analytics to stakeholders
- [ ] Apply learned concepts to your own business data

---

## 🎯 Best Practices

### For Effective Data Agent Conversations
1. **Start Broad**: Begin with "describe the data" to understand what's available
2. **Be Specific**: Use exact column names when you know them
3. **Iterate**: Refine questions based on initial answers
4. **Use Context**: Reference previous answers in follow-up questions
5. **Validate**: Cross-check AI insights with domain knowledge

### For Semantic Model Design
1. **Plan Ahead**: Identify key metrics before building
2. **Use Clear Names**: Make DAX measures self-explanatory
3. **Document**: Add descriptions to measures
4. **Test**: Validate calculations with known data points
5. **Iterate**: Start simple, add complexity gradually

### For Power BI Copilot
1. **Be Descriptive**: Clearly state what you want to visualize
2. **Specify Details**: Mention chart types, colors, filters if important
3. **Review & Refine**: Check generated visuals and adjust prompts
4. **Save Favorites**: Keep track of effective prompts
5. **Combine Tools**: Use Copilot with manual editing for best results

---

## 📚 Additional Resources

### Microsoft Documentation
- [Microsoft Fabric Data Agents](https://learn.microsoft.com/fabric/data-science/data-agent)
- [Power BI Copilot](https://learn.microsoft.com/power-bi/create-reports/copilot-introduction)
- [DAX Guide](https://dax.guide/)
- [Semantic Models in Fabric](https://learn.microsoft.com/power-bi/connect-data/service-datasets-understand)

### Learning Paths
- Microsoft Learn: Fabric Fundamentals
- Microsoft Learn: Power BI Data Analyst
- Microsoft Learn: DAX in Power BI

### Community
- Microsoft Fabric Community
- Power BI Community Forums
- DAX Patterns Library

*Last Updated: October 29, 2025*  
*Workshop Version: 1.0*  
*Duration: 90 minutes*

