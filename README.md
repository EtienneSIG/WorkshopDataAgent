# Microsoft Fabric Data Agents Workshop

## 🎯 Workshop Overview

Welcome to this hands-on workshop demonstrating the transformative power of **Microsoft Fabric Data Agents**. This comprehensive training showcases how AI can revolutionize data analysis across different business domains, enabling executives and managers to gain instant insights through natural language conversations with their data.

### 🌟 Workshop Goals

- **Demonstrate AI-Powered Analytics**: Experience how Data Agents make complex data analysis accessible to non-technical users
- **Enable Self-Service Insights**: Empower business leaders to answer their own questions without waiting for IT or analytics teams
- **Showcase Real-World Scenarios**: Learn through practical use cases from Finance and HR domains
- **Accelerate Decision-Making**: Transform data-to-insight time from days to minutes

### ⏱️ Total Duration: 150 minutes
- Introduction: 15 minutes
- Scenario 1 (Financial Data): 45 minutes
- Scenario 2 (HR Data): 45 minutes
- Scenario 3 (Real-Time Intelligence): 60 minutes
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
- 🚴 Real-time bicycle telemetry data (via Fabric sample data)
- 📖 Complete documentation for all datasets

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

## 🚴 Scenario 3: Real-Time Intelligence - Bike Fleet Monitoring

### 📊 Business Context
**Role**: Operations Manager for Bike-Sharing Company  
**Challenge**: Monitor and analyze real-time bicycle usage data across a city network to optimize fleet management  
**Goal**: Gain instant insights from streaming data, detect anomalies, and respond proactively to operational needs

### 🗂️ Dataset Overview
- **Source**: Microsoft Fabric Sample Data - Bicycles
- **Data Type**: Real-time streaming telemetry
- **Update Frequency**: Real-time (simulated 100-500 events/sec)
- **Coverage**: 200-800 bike stations across city
- **Dimensions**: 10 columns including:
  - Station identifiers and locations
  - GPS coordinates (Latitude/Longitude)
  - Real-time availability (bikes, empty docks)
  - Timestamps and neighborhood data
  - Calculated metrics (availability ratio, status)

### 🎯 Key Learning Objectives
1. **Eventstream Creation**: Set up real-time data ingestion pipelines
2. **Data Transformation**: Apply in-flight transformations to streaming data
3. **KQL Queries**: Learn Kusto Query Language for real-time analytics
4. **Real-Time Dashboards**: Build auto-refreshing operational dashboards
5. **Alerting**: Configure proactive alerts for critical conditions
6. **Power BI Integration**: Create reports from streaming data

### 💡 Example Scenarios You'll Build
- **Availability Monitoring**: "Show all stations with less than 3 bikes available"
- **Geospatial Analysis**: "Map current bike distribution across the city"
- **Trend Analysis**: "Track availability patterns over the last hour"
- **Station Status**: "Identify stations that are empty or full"
- **Peak Detection**: "What are the busiest stations right now?"
- **Predictive Insights**: "Which stations will need restocking soon?"
- **Conversational Analytics**: Ask questions in natural language via Data Agent

### 📈 Expected Outcomes
- Build complete real-time data pipeline
- Create Data Agent for streaming data queries
- Create operational dashboards with auto-refresh
- Set up proactive alerts for low availability
- Understand KQL for streaming analytics
- Integrate real-time data with Power BI
- Demonstrate business value of Real-Time Intelligence

### 🔧 Technologies Used
- **Eventstream**: Real-time data ingestion and transformation
- **KQL Database**: High-performance time-series storage
- **KQL (Kusto Query Language)**: Query language for big data
- **Data Agent**: Natural language interface for real-time data
- **Real-Time Dashboard**: Operational monitoring interface
- **Power BI**: Advanced reporting and analytics
- **Alerts**: Automated notifications (Email, Teams)

### 📂 Location
[`scenario 3 - Real-Time Intelligence/`](./scenario%203%20-%20Real-Time%20Intelligence/)
- 📄 [README.md](./scenario%203%20-%20Real-Time%20Intelligence/README.md) - Complete step-by-step guide
- 📁 [01_data/](./scenario%203%20-%20Real-Time%20Intelligence/01_data/)
  - 📖 `RealTime_Dataset_Description.md` - Detailed documentation

---

## 🚀 Workshop Journey

### Phase 1: Introduction (15 min)
- Overview of Microsoft Fabric Data Agents and Real-Time Intelligence
- Workshop objectives and three scenarios
- Technical setup verification

### Phase 2: Scenario 1 - Financial Data (45 min)

#### Part A: Quick Start (20 min)
1. **Upload Data** (5 min)
   - Use OneLake Explorer OR upload directly
   - Load CSV into Fabric lakehouse
   
2. **Create Data Agent** (5 min)
   - One-click Data Agent creation
   - Configure "Operations Assistant"

3. **Conversational Analysis** (10 min)
   - Ask financial questions in natural language
   - Explore spending patterns
   - Identify supplier insights

#### Part B: Semantic Model & Advanced Features (25 min)
1. **Build Semantic Model** (10 min)
   - Create "Corporate Operations Model"
   - Define DAX measures (Total Spending, Transaction Count)

2. **Advanced Data Agent** (10 min)
   - Create "Executive Operations Assistant"
   - Test complex multi-dimensional queries

3. **Power BI Copilot** (5 min)
   - Generate visualizations with natural language
   - Create executive dashboard

### Phase 3: Scenario 2 - HR Data (45 min)

#### Part A: Data Setup (15 min)
1. **Upload Workforce Data** (5 min)
   - Load `workforce_dataset_400.csv`

2. **Quick Data Agent** (5 min)
   - Create "HR Workforce Assistant"
   - Test capacity queries

3. **Initial Insights** (5 min)
   - Identify overutilized employees
   - Find underutilized resources

#### Part B: HR Analytics Platform (30 min)
1. **Workforce Semantic Model** (15 min)
   - Create "Workforce Capacity Model"
   - Build HR-specific DAX measures:
     - Total Employees
     - Average Workload
     - Overutilized/Underutilized counts
     - Internal vs External ratios

2. **HR Intelligence Agent** (10 min)
   - Create "HR Workforce Intelligence Assistant"
   - Test complex workforce scenarios
   - Identify burnout risks and hiring needs

3. **Executive HR Dashboard** (5 min)
   - Use Power BI Copilot to create HR KPIs
   - Generate capacity planning visualizations

### Phase 4: Scenario 3 - Real-Time Intelligence (60 min)

#### Part A: Real-Time Data Pipeline (25 min)
1. **Create Eventhouse** (5 min)
   - Set up Real-Time Intelligence workspace
   - Create KQL database

2. **Configure Eventstream** (10 min)
   - Connect to Bicycle sample data source
   - Set up real-time data ingestion
   - Apply data transformations

3. **KQL Queries** (10 min)
   - Learn basic KQL syntax
   - Query streaming data
   - Perform time-series analysis
   - Execute geospatial queries

#### Part B: Data Agent for Real-Time Data (15 min)
1. **Create Data Agent** (7 min)
   - Create "Bike Fleet Intelligence Agent"
   - Connect to KQL database
   - Configure for real-time queries

2. **Conversational Analytics** (8 min)
   - Ask operational questions in natural language
   - Identify stations needing attention
   - Explore geographic patterns
   - Generate insights from streaming data

#### Part C: Real-Time Dashboards & Alerts (20 min)
1. **Build Real-Time Dashboard** (10 min)
   - Create operational monitoring tiles
   - Configure auto-refresh (30 sec)
   - Add KPIs: Total Bikes, Station Status
   - Build visualizations: Maps, Time Charts, Bar Charts

2. **Power BI Real-Time Report** (5 min)
   - Generate report from KQL queries
   - Create executive analytics views
   - Publish to workspace

3. **Configure Alerts** (5 min)
   - Set up low availability alerts
   - Configure email notifications
   - Test alert conditions

### Phase 5: Wrap-up (15 min)
- Key takeaways and benefits
- Best practices discussion
- Q&A session
- Next steps

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
- ✅ **Real-Time Pipelines**: Design and implement streaming data solutions
- ✅ **KQL Expertise**: Master query language for big data and time-series

### For Executives
- ✅ **ROI**: Accelerate decision-making across organization
- ✅ **Digital Transformation**: Enable AI-powered analytics at scale
- ✅ **Democratization**: Empower all levels with data access
- ✅ **Competitive Advantage**: Faster insights = better decisions
- ✅ **Proactive Operations**: Real-time monitoring and alerting

---

## 📊 Comparison: All Three Scenarios

| Aspect | Scenario 1: Financial | Scenario 2: HR | Scenario 3: Real-Time |
|--------|----------------------|----------------|-----------------------|
| **Domain** | Finance & Operations | Human Resources | Operations & IoT |
| **Data Type** | Historical Transactions | Employee Records | Streaming Telemetry |
| **Dataset Size** | 10,000 records | 400 employees | Continuous stream |
| **Time Period** | 2023-2025 (3 years) | 2025 (12 months) | Real-time |
| **Complexity** | Medium | Medium-Advanced | Advanced |
| **Key Metrics** | Spending, Suppliers | Workload, Capacity | Availability, Location |
| **Primary Users** | Finance Directors | HR Directors | Operations Managers |
| **Technology** | Data Agents, Semantic Models | Data Agents, DAX | Eventstream, KQL, Alerts |
| **Query Language** | Natural Language, DAX | Natural Language, DAX | KQL |
| **Visualizations** | Financial charts | Capacity heatmaps | Real-Time dashboards, Maps |
| **Unique Feature** | Multi-currency analysis | Burnout detection | Proactive alerting |
| **Business Value** | Cost optimization | Resource planning | Fleet optimization |
| **Update Frequency** | Static/Scheduled | Static/Scheduled | Real-time (seconds) |

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
- **IoT & Smart Cities**: Traffic monitoring, energy consumption, environmental sensors
- **Retail**: Real-time inventory, customer foot traffic, point-of-sale analytics

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

### Real-Time Intelligence
- ⚡ **Eventstreams**: Ingest and transform streaming data
- 🔍 **KQL Queries**: Powerful query language for time-series and big data
- 📊 **Real-Time Dashboards**: Auto-refreshing operational views
- 🔔 **Proactive Alerts**: Automated notifications for critical conditions
- 🗺️ **Geospatial Analysis**: Location-based insights with maps

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

### Scenario 3 (Real-Time Intelligence)
- [ ] Create Eventhouse and KQL database
- [ ] Configure Eventstream with bicycle sample data
- [ ] Write 5+ KQL queries for real-time analysis
- [ ] Create "Bike Fleet Intelligence Agent" Data Agent
- [ ] Ask 5+ natural language questions to Data Agent
- [ ] Build Real-Time Dashboard with auto-refresh
- [ ] Set up low availability alert
- [ ] Create Power BI report from KQL data

### Overall
- [ ] Understand when to use Data Agents vs Real-Time Intelligence vs traditional BI
- [ ] Explain the value of semantic models
- [ ] Demonstrate self-service analytics to stakeholders
- [ ] Apply learned concepts to your own business data
- [ ] Identify streaming data opportunities in your organization

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

### For Real-Time Intelligence
1. **Plan Data Flow**: Map out source → transform → destination pipeline
2. **Start Simple**: Test with basic queries before adding complexity
3. **Monitor Performance**: Watch ingestion rates and query latency
4. **Set Smart Alerts**: Balance sensitivity vs alert fatigue
5. **Document KQL**: Comment complex queries for team collaboration

---

## 📚 Additional Resources

### Microsoft Documentation
- [Microsoft Fabric Data Agents](https://learn.microsoft.com/fabric/data-science/data-agent)
- [Power BI Copilot](https://learn.microsoft.com/power-bi/create-reports/copilot-introduction)
- [Real-Time Intelligence in Fabric](https://learn.microsoft.com/fabric/real-time-intelligence/)
- [KQL Quick Reference](https://learn.microsoft.com/azure/data-explorer/kusto/query/)
- [Eventstreams Documentation](https://learn.microsoft.com/fabric/real-time-intelligence/event-streams/)
- [DAX Guide](https://dax.guide/)
- [Semantic Models in Fabric](https://learn.microsoft.com/power-bi/connect-data/service-datasets-understand)

### Learning Paths
- Microsoft Learn: Fabric Fundamentals
- Microsoft Learn: Power BI Data Analyst
- Microsoft Learn: Real-Time Intelligence with Fabric
- Microsoft Learn: DAX in Power BI
- Microsoft Applied Skills: Implement Real-Time Intelligence

### Tutorials & Samples
- [AI Tour: Get Started with Fabric](https://github.com/microsoft/aitour-get-started-with-fabric)
- [Real-Time Intelligence Tutorial](https://learn.microsoft.com/fabric/real-time-intelligence/tutorial-introduction)
- [KQL Query Samples](https://learn.microsoft.com/azure/data-explorer/kusto/query/samples)

### Community
- Microsoft Fabric Community
- Power BI Community Forums
- DAX Patterns Library

---

## 🆘 Support & Troubleshooting

### Common Issues

**Data Agent not responding:**
- Verify Fabric capacity is running
- Check data permissions in lakehouse
- Refresh the Data Agent page

**DAX measure errors:**
- Verify column names match exactly
- Check data types are correct
- Test with simpler measure first

**Eventstream not ingesting data:**
- Verify data source connection
- Check transformation logic
- Monitor event flow in diagram view

**KQL query errors:**
- Check table and column names (case-sensitive)
- Verify data types in operations
- Test with smaller time ranges first

**Real-Time Dashboard not refreshing:**
- Verify auto-refresh is enabled
- Check data ingestion is active
- Refresh browser cache

**OneLake Explorer not syncing:**
- Check internet connection
- Re-authenticate with Microsoft 365
- Verify workspace permissions

### Getting Help
- Workshop instructor (during session)
- Your IT team or Microsoft partner
- Microsoft Fabric documentation
- Community forums

---

## 🎉 Next Steps After the Workshop

### Immediate Actions
1. **Apply to Your Data**: Try Data Agents with your own business data
2. **Share Insights**: Demonstrate to colleagues and stakeholders
3. **Build Models**: Create semantic models for frequent analyses
4. **Explore More**: Try Data Agents with different data sources
5. **Identify Streaming Opportunities**: Look for real-time data use cases in your organization

### Medium-Term Goals
1. **Governance**: Establish data quality standards
2. **Training**: Expand Data Agent adoption across teams
3. **Integration**: Connect multiple data sources in semantic models
4. **Automation**: Schedule data refreshes and automated reports
5. **Real-Time Expansion**: Implement streaming for IoT, sensors, or transactional systems

### Long-Term Vision
1. **Center of Excellence**: Build Fabric expertise internally
2. **Self-Service Culture**: Enable organization-wide analytics
3. **AI-First Approach**: Make AI assistants standard for decision-making
4. **Continuous Innovation**: Stay updated with Fabric new features

---

## 📞 Contact & Feedback

- **Workshop Feedback**: [Provide feedback link]
- **Technical Support**: Your IT team or Microsoft partner
- **Questions**: [Contact information]

---

## 📄 License & Attribution

This workshop material is provided for educational purposes. Datasets are synthetic and generated for demonstration only.

---

**🌟 Ready to transform your data analysis with AI and Real-Time Intelligence?**  
**Let's get started with [Scenario 1: Financial Data Analysis](./scenario%201%20-%20Financial%20data/README.md)!**

---

*Last Updated: November 25, 2025*  
*Workshop Version: 2.0*  
*Duration: 150 minutes*
