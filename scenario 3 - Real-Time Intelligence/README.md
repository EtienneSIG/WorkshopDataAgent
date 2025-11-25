# Scenario 3: Real-Time Intelligence with Microsoft Fabric

## 🎯 Scenario Objectives

This hands-on scenario demonstrates the power of **Microsoft Fabric Real-Time Intelligence** for analyzing streaming data. Learn how to ingest, transform, query, and visualize real-time data streams using Eventstreams, KQL, and Real-Time Dashboards.

### Estimated Duration: 60 minutes

---

## 📋 Prerequisites

- Access to Microsoft Fabric with enabled capacity
- Microsoft Fabric trial activated (if needed)
- Real-Time Intelligence capabilities enabled in your workspace
- Basic understanding of data streaming concepts

---

## 🎭 Business Context

*You are a data analyst for a bike-sharing company that needs to monitor and analyze real-time bicycle usage data. Your goal is to track bike locations, detect anomalies, and provide real-time insights to operations teams for better fleet management and customer service.*

### Key Business Questions:
- Where are bikes currently located in real-time?
- Which bikes need maintenance based on usage patterns?
- What are the peak usage times and locations?
- How can we proactively respond to unusual patterns?
- Which stations consistently run empty or full?
- What are the availability trends by neighborhood?

---

## 🏗️ Solution Architecture

```
📡 Real-Time Data Source (Bicycle Telemetry)
    ↓
🔄 Eventstream (Ingest & Transform)
    ↓
📊 KQL Database (Store & Query)
    ↓
🤖 Data Agent (Natural Language Interface)
    ↓
📈 Real-Time Dashboard (Visualize)
    ↓
⚡ Power BI Report (Advanced Analytics)
    ↓
🔔 Alerts (Proactive Monitoring)
```

---

## 🚀 Step-by-Step Guide

### Part 1: Create Resources in Microsoft Fabric

#### 1.1 Create an Eventhouse

An **Eventhouse** is a workspace for real-time data that includes a KQL database.

1. **Navigate to Fabric Portal**
   - Go to [Microsoft Fabric](https://app.fabric.microsoft.com)
   - Select your workspace or create a new one

2. **Create Eventhouse**
   - Click **+ New Item**
   - Select **Eventhouse** (under Real-Time Intelligence)
   - Name: `BikeMonitoring`
   - Click **Create**

3. **Verify KQL Database**
   - The eventhouse automatically creates a KQL database
   - Note the database name (e.g., `BikeMonitoring`)

---

### Part 2: Get Data in the Real-Time Hub

#### 2.1 Access Real-Time Hub

The **Real-Time Hub** is the central location for discovering and managing streaming data sources.

1. **Open Real-Time Hub**
   - In your Fabric workspace, click **Real-Time** on the left navigation
   - Select **Real-Time Hub**

2. **Connect to Sample Data Source**
   - Click **+ Get data**
   - Select **Sample data** tab
   - Choose **Bicycles** sample dataset
   - Click **Connect**

#### 2.2 Create Eventstream

1. **Configure Eventstream**
   - Name: `BikeTelemetryStream`
   - Description: "Real-time bicycle location and status data"
   - Click **Next**

2. **Configure Source Settings**
   - Source type: Sample data - Bicycles
   - Review the data schema:
     - `BikepointID`: Unique bike identifier
     - `Street`: Location street name
     - `Neighbourhood`: Area/neighborhood
     - `Latitude` / `Longitude`: GPS coordinates
     - `No_Bikes`: Number of bikes available
     - `No_Empty_Docks`: Empty docking stations
     - `Timestamp`: Event timestamp

3. **Create the Eventstream**
   - Click **Create**
   - Wait for the eventstream to be provisioned

---

### Part 3: Transform Events and Send to KQL Database

#### 3.1 Add Transformation

1. **Open Eventstream Editor**
   - Navigate to your `BikeTelemetryStream`
   - Click **Edit** to enter design mode

2. **Add Data Transformation**
   - In the canvas, click **+ Add destination**
   - Select **Transform events**
   - Choose **Manage fields** operation

3. **Configure Field Transformations**
   - Add calculated field: `AvailabilityRatio`
     ```
     No_Bikes / (No_Bikes + No_Empty_Docks)
     ```
   - Add field: `Status`
     ```
     CASE 
       WHEN No_Bikes = 0 THEN 'Empty'
       WHEN No_Empty_Docks = 0 THEN 'Full'
       ELSE 'Available'
     END
     ```
   - Click **Save**

#### 3.2 Send to KQL Database

1. **Add KQL Database Destination**
   - Click **+ Add destination** after the transformation
   - Select **KQL Database**
   - Choose your `BikeMonitoring` database

2. **Configure Ingestion**
   - Table name: `BikeData`
   - Ingestion mode: **Direct ingestion**
   - Click **Save**

3. **Publish the Eventstream**
   - Click **Publish** to activate the stream
   - Monitor the data flow in real-time

---

### Part 4: Query Streaming Data Using KQL

#### 4.1 Create a KQL Queryset

1. **Open KQL Queryset**
   - In your workspace, click **+ New Item**
   - Select **KQL Queryset**
   - Name: `BikeAnalytics`
   - Connect to: `BikeMonitoring` database

2. **Basic Queries**

**View Recent Bike Data:**
```kql
BikeData
| take 100
| order by Timestamp desc
```

**Count Bikes by Status:**
```kql
BikeData
| summarize Count = count() by Status
| render piechart
```

**Bikes with Low Availability:**
```kql
BikeData
| where No_Bikes < 3
| project BikepointID, Street, Neighbourhood, No_Bikes, Timestamp
| order by Timestamp desc
```

#### 4.2 Advanced Analytics Queries

**Availability Trends Over Time:**
```kql
BikeData
| summarize AvgBikes = avg(No_Bikes) by bin(Timestamp, 5m), Neighbourhood
| render timechart
```

**Identify Full or Empty Stations:**
```kql
BikeData
| where Status in ('Empty', 'Full')
| summarize Count = count() by BikepointID, Street, Status
| order by Count desc
| take 20
```

**Geospatial Analysis - Map View:**
```kql
BikeData
| summarize AvgBikes = avg(No_Bikes) by BikepointID, Latitude, Longitude, Street
| project Latitude, Longitude, Street, AvgBikes
```

---

### Part 5: Create a Real-Time Dashboard

#### 5.1 Build the Dashboard

1. **Create Real-Time Dashboard**
   - In workspace, click **+ New Item**
   - Select **Real-Time Dashboard**
   - Name: `Bike Fleet Monitor`

2. **Add Tiles to Dashboard**

**Tile 1: Total Bikes Available**
```kql
BikeData
| summarize TotalBikes = sum(No_Bikes)
| project TotalBikes
```
- Visualization: **Card**
- Title: "Total Bikes Available"

**Tile 2: Bikes by Status**
```kql
BikeData
| summarize Count = count() by Status
| render piechart
```
- Visualization: **Pie Chart**
- Title: "Station Status Distribution"

**Tile 3: Availability Trend**
```kql
BikeData
| summarize AvgBikes = avg(No_Bikes) by bin(Timestamp, 10m)
| render timechart
```
- Visualization: **Time Chart**
- Title: "Average Bike Availability (10-min intervals)"

**Tile 4: Top 10 Busy Locations**
```kql
BikeData
| summarize TotalActivity = count() by Street, Neighbourhood
| top 10 by TotalActivity
| render barchart
```
- Visualization: **Bar Chart**
- Title: "Most Active Bike Stations"

**Tile 5: Geographic Distribution**
```kql
BikeData
| summarize AvgBikes = avg(No_Bikes) by Latitude, Longitude, Street
| project Latitude, Longitude, Street, AvgBikes
```
- Visualization: **Map**
- Title: "Bike Availability by Location"

3. **Configure Auto-Refresh**
   - Set refresh interval: **30 seconds**
   - Enable auto-refresh for real-time monitoring

---

### Part 6: Create a Power BI Report

#### 6.1 Build Power BI Report from KQL

1. **Create Report**
   - From your KQL Queryset, select a query
   - Click **Build Power BI report**
   - This creates a new Power BI report connected to your KQL database

2. **Report Visualizations**

**Page 1: Executive Overview**
- KPI Cards:
  - Total Bikes Available
  - Total Stations Monitored
  - Average Availability %
- Line Chart: Availability trend over last 24 hours
- Map: Geographic distribution of bikes

**Page 2: Operational Insights**
- Table: Stations needing attention (empty or full)
- Bar Chart: Top 20 stations by activity
- Scatter Plot: Bikes vs. Empty Docks by location

**Page 3: Neighborhood Analysis**
- Matrix: Availability by Neighbourhood and Status
- Clustered Column Chart: Bikes by Neighbourhood over time
- Filters: Time range, Status, Neighbourhood

3. **Publish to Workspace**
   - Click **Save**
   - Name: `Bike Fleet Analytics`
   - Publish to your Fabric workspace

---

### Part 7: Create Data Agent for Real-Time Intelligence

#### 7.1 Enable Conversational Analytics on Real-Time Data

Now that you have streaming data in your KQL database, you can create a **Data Agent** to enable natural language queries on your real-time data.

1. **Navigate to KQL Database**
   - Go to your workspace
   - Open your `BikeMonitoring` KQL database
   - You should see the `BikeData` table with streaming data

2. **Create Data Agent**
   - In the KQL database view, look for **"Add Data Agent"** button
   - Click to create a new Data Agent
   - Name: `Bike Fleet Intelligence Agent`
   - Description: "AI assistant for real-time bike fleet monitoring and analysis"

3. **Configure Data Agent**
   - **Data Source**: Automatically connected to `BikeMonitoring` database
   - **Tables**: Ensure `BikeData` is selected
   - **Context Instructions** (optional): Add business context:
     ```
     You are analyzing real-time bicycle sharing data. 
     Focus on availability, station status, and geographic distribution.
     Help identify operational issues like empty or full stations.
     ```

#### 7.2 Test Data Agent with Natural Language Queries

**Basic Exploration:**
- "How many bike stations are being monitored?"
- "Show me the current status of all stations"
- "What is the average number of bikes available per station?"

**Real-Time Monitoring:**
- "Which stations have less than 3 bikes available right now?"
- "Show me all empty stations"
- "Which stations are completely full?"
- "What's the most recent data timestamp?"

**Geospatial Analysis:**
- "Which neighborhoods have the most bike stations?"
- "Show me bike availability by neighborhood"
- "List stations in Westminster"

**Trend Analysis:**
- "What are the availability trends over the last hour?"
- "Show me the busiest stations by activity"
- "Which stations have the most fluctuation in bike availability?"

**Operational Insights:**
- "Identify stations that need immediate restocking"
- "Which areas have consistent low availability?"
- "Compare bike availability between morning and afternoon"

#### 7.3 Advanced Data Agent Features

1. **Custom Queries**
   - Ask complex questions combining multiple dimensions
   - Example: "Show me stations in Camden with less than 5 bikes that have been low for more than 30 minutes"

2. **Visual Responses**
   - The Data Agent can suggest or generate visualizations
   - Ask: "Create a chart showing availability by neighborhood"

3. **Follow-up Questions**
   - The agent maintains context from previous questions
   - Example conversation:
     - "Show me stations with low availability"
     - "Now filter those to only Westminster"
     - "What's the average for those stations?"

#### 7.4 Integrate Data Agent with Dashboards

1. **Create Semantic Model (Optional)**
   - For more advanced scenarios, create a semantic model on top of KQL data
   - Define DAX measures:
     ```dax
     Total Stations = DISTINCTCOUNT(BikeData[BikepointID])
     Average Bikes = AVERAGE(BikeData[No_Bikes])
     Empty Stations = CALCULATE(COUNT(BikeData[BikepointID]), BikeData[No_Bikes] = 0)
     Full Stations = CALCULATE(COUNT(BikeData[BikepointID]), BikeData[No_Empty_Docks] = 0)
     Utilization Rate = DIVIDE([Average Bikes], [Average Bikes] + AVERAGE(BikeData[No_Empty_Docks]))
     ```

2. **Enhanced Data Agent**
   - Create a new Data Agent connected to the semantic model
   - This enables more sophisticated business logic queries
   - Example: "What's our overall fleet utilization rate?"

---

### Part 8: Set Alerts on Event Stream

#### 8.1 Configure Real-Time Alerts

1. **Create Alert Rule**
   - Go to your `BikeTelemetryStream`
   - Click **Set alert**

2. **Define Alert Condition**
   - Alert name: `Low Bike Availability Alert`
   - Condition: `No_Bikes < 2`
   - Evaluation frequency: **1 minute**

3. **Configure Actions**
   - Action type: **Email**
   - Recipients: Your email address
   - Message template:
     ```
     ⚠️ Low Bike Availability Alert
     
     Station: {Street}
     Location: {Neighbourhood}
     Available Bikes: {No_Bikes}
     Timestamp: {Timestamp}
     
     Action Required: Restock bikes at this location.
     ```

4. **Activate Alert**
   - Review configuration
   - Click **Create**
   - Test the alert with sample data

#### 8.2 Additional Alert Scenarios

**Station Full Alert:**
- Condition: `No_Empty_Docks < 2`
- Purpose: Prevent customers from being unable to return bikes

**High Utilization Alert:**
- Condition: `AvailabilityRatio > 0.9`
- Purpose: Identify stations approaching capacity

**Anomaly Alert:**
- Condition: Sudden drop in availability (>50% in 5 minutes)
- Purpose: Detect potential system issues or unusual events

---

## 💡 Key Concepts Demonstrated

### Real-Time Intelligence Features

1. **Eventstreams**
   - Ingest streaming data from multiple sources
   - Transform data in-flight
   - Route to multiple destinations

2. **KQL (Kusto Query Language)**
   - Fast, scalable query language for big data
   - Time-series analysis
   - Geospatial queries

3. **Real-Time Dashboards**
   - Auto-refreshing visualizations
   - Low-latency data display
   - Interactive filtering

4. **Integration with Power BI**
   - Advanced analytics and reporting
   - Scheduled refresh or DirectQuery
   - Enterprise-grade sharing

5. **Alerting**
   - Proactive monitoring
   - Condition-based notifications
   - Multi-channel alerts (Email, Teams, etc.)

---

## 📊 Sample Data Schema

### BikeData Table

| Column | Type | Description |
|--------|------|-------------|
| BikepointID | string | Unique identifier for bike station |
| Street | string | Street address of station |
| Neighbourhood | string | Neighborhood/area name |
| Latitude | decimal | GPS latitude coordinate |
| Longitude | decimal | GPS longitude coordinate |
| No_Bikes | int | Number of bikes available |
| No_Empty_Docks | int | Number of empty docking spots |
| Timestamp | datetime | Event timestamp (UTC) |
| AvailabilityRatio | decimal | Calculated: No_Bikes / Total_Capacity |
| Status | string | Derived: 'Empty', 'Full', or 'Available' |

---

## ✅ Success Criteria

### For This Scenario
- [ ] Eventhouse and KQL database created
- [ ] Eventstream ingesting bicycle data
- [ ] Data transformations applied successfully
- [ ] KQL queries returning insights
- [ ] Real-Time Dashboard with auto-refresh enabled
- [ ] Power BI report published
- [ ] Alert configured and tested

---

## 🎓 Learning Outcomes

After completing this scenario, you will understand:

### Technical Skills
- How to create and configure Eventstreams
- KQL query language fundamentals
- Building Real-Time Dashboards
- Integrating Fabric with Power BI
- Setting up automated alerts

### Business Value
- **Proactive Operations**: Alerts enable teams to respond before issues escalate
- **Real-Time Visibility**: Instant insights into fleet status
- **Data-Driven Decisions**: Analytics inform resource allocation
- **Cost Optimization**: Reduce downtime and improve asset utilization
- **Customer Satisfaction**: Ensure bike availability at popular locations

---

## 🔄 Extension Ideas

1. **Predictive Maintenance**
   - Use historical patterns to predict which stations will need restocking
   - Apply machine learning models for demand forecasting

2. **Advanced Geospatial Analysis**
   - Create heat maps for peak usage zones
   - Route optimization for bike redistribution trucks

3. **Multi-Source Integration**
   - Combine bike data with weather data
   - Integrate with event calendars for demand prediction

4. **Custom Metrics**
   - Calculate station utilization efficiency
   - Track time-to-restock SLAs

5. **Mobile Dashboard**
   - Create mobile-optimized views for field teams
   - Enable on-the-go decision making

---

## 📞 Additional Resources

- **Tutorial Source**: [Microsoft AI Tour - Get Started with Fabric](https://github.com/microsoft/aitour-get-started-with-fabric)
- **Microsoft Learn**: [Real-Time Intelligence Tutorial](https://learn.microsoft.com/fabric/real-time-intelligence/tutorial-introduction)
- **KQL Documentation**: [Kusto Query Language](https://learn.microsoft.com/azure/data-explorer/kusto/query/)
- **Fabric Trial**: [Activate Fabric Trial](https://learn.microsoft.com/fabric/get-started/fabric-trial)
- **Community**: [Fabric Community](https://community.fabric.microsoft.com/)

---

## 🏆 Next Steps

1. **Explore More Scenarios**: Try different data sources (IoT sensors, social media, financial tickers)
2. **Advanced KQL**: Learn window functions, joins, and aggregations
3. **Certification Path**: Consider [DP-600: Implementing Analytics Solutions Using Microsoft Fabric](https://learn.microsoft.com/credentials/certifications/fabric-analytics-engineer-associate/)
4. **Applied Skills**: [Implement a Real-Time Intelligence with Microsoft Fabric](https://learn.microsoft.com/credentials/applied-skills/implement-a-real-time-intelligence-solution-with-microsoft-fabric/)

---

*This scenario is based on the Microsoft AI Tour workshop "Get Started with Fabric" and demonstrates real-world applications of Microsoft Fabric Real-Time Intelligence capabilities.*
