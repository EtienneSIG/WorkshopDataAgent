# Real-Time Intelligence Dataset Description

## Overview

This scenario uses **sample bicycle telemetry data** provided by Microsoft Fabric's Real-Time Intelligence capabilities. The data simulates real-time streaming from a bike-sharing system, tracking bike availability and location across a city network.

---

## Data Source

**Source Type**: Microsoft Fabric Sample Data - Bicycles  
**Update Frequency**: Real-time streaming (simulated)  
**Data Format**: JSON events via Eventstream  
**Geographic Coverage**: City-wide bike-sharing network  

---

## Schema Details

### BikeData Table (After Ingestion)

| Column Name | Data Type | Description | Example Values |
|-------------|-----------|-------------|----------------|
| **BikepointID** | string | Unique identifier for the bike docking station | "BikePoints_1", "BikePoints_142" |
| **Street** | string | Street address or location name of the station | "Park Lane", "Oxford Street" |
| **Neighbourhood** | string | Neighborhood or district where station is located | "Westminster", "Camden", "Kensington" |
| **Latitude** | decimal | GPS latitude coordinate (WGS84) | 51.5074 |
| **Longitude** | decimal | GPS longitude coordinate (WGS84) | -0.1278 |
| **No_Bikes** | int | Current number of bikes available at the station | 0-40 |
| **No_Empty_Docks** | int | Number of empty docking spots available | 0-40 |
| **Timestamp** | datetime | UTC timestamp when the event was generated | 2025-11-25T14:30:00Z |

### Calculated/Derived Fields (Added via Transformation)

| Column Name | Data Type | Calculation | Description |
|-------------|-----------|-------------|-------------|
| **AvailabilityRatio** | decimal | `No_Bikes / (No_Bikes + No_Empty_Docks)` | Percentage of station capacity filled with bikes (0.0 to 1.0) |
| **Status** | string | Conditional logic | Station status: "Empty" (0 bikes), "Full" (0 docks), or "Available" |

---

## Data Characteristics

### Volume
- **Event Rate**: ~100-500 events per second (simulated)
- **Stations**: ~200-800 bike stations
- **Daily Events**: Millions of telemetry events

### Temporal Patterns
- **Peak Hours**: Morning (7-9 AM) and Evening (5-7 PM) commute times
- **Weekend Patterns**: Leisure-focused usage, peaks around midday
- **Seasonal Variation**: Higher usage in spring/summer months

### Spatial Distribution
- **Urban Density**: Higher concentration in city centers and transit hubs
- **Suburban**: Lower density, larger spacing between stations
- **Points of Interest**: Clusters around parks, universities, shopping areas

---

## Sample Data Records

```json
{
  "BikepointID": "BikePoints_1",
  "Street": "River Street, Clerkenwell",
  "Neighbourhood": "Islington",
  "Latitude": 51.529163,
  "Longitude": -0.10997,
  "No_Bikes": 12,
  "No_Empty_Docks": 7,
  "Timestamp": "2025-11-25T10:15:30.000Z"
}

{
  "BikepointID": "BikePoints_142",
  "Street": "Hyde Park Corner, Hyde Park",
  "Neighbourhood": "Westminster",
  "Latitude": 51.502904,
  "Longitude": -0.152641,
  "No_Bikes": 0,
  "No_Empty_Docks": 23,
  "Timestamp": "2025-11-25T10:15:32.000Z"
}

{
  "BikepointID": "BikePoints_267",
  "Street": "Tooley Street, Bermondsey",
  "Neighbourhood": "Southwark",
  "Latitude": 51.504324,
  "Longitude": -0.077406,
  "No_Bikes": 18,
  "No_Empty_Docks": 0,
  "Timestamp": "2025-11-25T10:15:35.000Z"
}
```

---

## Use Cases & Analytics

### Operational Monitoring
- **Real-Time Availability**: Track bikes available across all stations
- **Station Status**: Identify empty or full stations needing attention
- **Fleet Utilization**: Calculate overall system usage and efficiency

### Predictive Analytics
- **Demand Forecasting**: Predict bike demand by location and time
- **Rebalancing Optimization**: Determine optimal bike redistribution routes
- **Capacity Planning**: Identify locations needing additional docking stations

### Business Intelligence
- **Usage Patterns**: Analyze peak times, popular routes, and seasonal trends
- **Customer Behavior**: Understand commuter vs. leisure usage
- **Service Level**: Measure availability SLAs and customer satisfaction metrics

### Alert Scenarios
- **Low Availability**: Alert when bikes < threshold at high-demand stations
- **Station Full**: Notify when docks are full (prevents new rentals)
- **Maintenance Needs**: Detect stations with prolonged zero availability
- **Anomaly Detection**: Flag unusual patterns (e.g., sudden drop in availability)

---

## KQL Query Examples

### Basic Exploration
```kql
// View latest 100 events
BikeData
| take 100
| order by Timestamp desc

// Count total stations
BikeData
| summarize Stations = dcount(BikepointID)

// Average bikes per station
BikeData
| summarize AvgBikes = avg(No_Bikes)
```

### Time-Series Analysis
```kql
// Hourly availability trend
BikeData
| summarize AvgBikes = avg(No_Bikes) by bin(Timestamp, 1h)
| render timechart

// Peak usage detection
BikeData
| summarize TotalActivity = count() by bin(Timestamp, 15m)
| order by TotalActivity desc
| take 10
```

### Geospatial Queries
```kql
// Map of current availability
BikeData
| summarize CurrentBikes = arg_max(Timestamp, No_Bikes) by BikepointID, Latitude, Longitude, Street
| project Latitude, Longitude, Street, CurrentBikes

// Stations in specific neighborhood
BikeData
| where Neighbourhood == "Westminster"
| summarize AvgBikes = avg(No_Bikes) by Street
| order by AvgBikes desc
```

### Alerts & Monitoring
```kql
// Stations with critical low availability
BikeData
| where No_Bikes <= 2
| summarize LastSeen = max(Timestamp) by BikepointID, Street, Neighbourhood
| where LastSeen > ago(5m)
| order by LastSeen desc

// Full stations (no empty docks)
BikeData
| where No_Empty_Docks == 0
| summarize Count = count() by BikepointID, Street
| order by Count desc
```

---

## Data Quality Considerations

### Completeness
- All fields are populated for each event
- No missing timestamps or location data
- Continuous stream with minimal gaps

### Accuracy
- GPS coordinates are precise to 6 decimal places (~10cm accuracy)
- Bike counts are validated against station capacity
- Timestamps are synchronized to UTC

### Consistency
- Station identifiers are stable over time
- Neighborhood names follow standardized taxonomy
- Status derivations follow business rules

---

## Integration Points

### Data Sources
- **Primary**: Fabric Sample Data (Bicycles)
- **Future Extensions**: 
  - Weather API (temperature, precipitation)
  - Calendar/Events API (concerts, sports, holidays)
  - Public Transit data (bus/subway schedules)

### Destinations
- **KQL Database**: Primary storage and query engine
- **Power BI**: Advanced reporting and dashboards
- **Real-Time Dashboard**: Operational monitoring
- **Alerts**: Email, Teams, Azure Monitor

---

## Performance Metrics

### Ingestion
- **Latency**: < 1 second from event generation to KQL database
- **Throughput**: Handles 10,000+ events/second
- **Retention**: Configurable (default 365 days)

### Query Performance
- **Simple Aggregations**: < 100ms
- **Time-Series Scans**: < 500ms for 7 days of data
- **Geospatial Queries**: < 1 second for full dataset

---

## Security & Compliance

### Access Control
- Workspace-level permissions in Microsoft Fabric
- Row-level security available for multi-tenant scenarios
- Audit logging of all data access

### Data Privacy
- Sample data contains no personal information
- Real deployments should anonymize user data
- Comply with GDPR, CCPA, and local regulations

### Data Retention
- Configurable retention policies (30 days to 10 years)
- Automatic archival to Azure Data Lake for long-term storage
- Soft-delete for data recovery

---

## References

- **Microsoft Learn**: [Real-Time Intelligence in Fabric](https://learn.microsoft.com/fabric/real-time-intelligence/)
- **Sample Data Source**: Built-in Fabric sample datasets
- **KQL Reference**: [Kusto Query Language](https://learn.microsoft.com/azure/data-explorer/kusto/query/)
- **Real-Time Hub**: [Get Data in Real-Time Hub](https://learn.microsoft.com/fabric/real-time-intelligence/event-streams/get-data-real-time-hub)

---

*This dataset description supports Scenario 3: Real-Time Intelligence with Microsoft Fabric*
