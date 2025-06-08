# 🚗⚡ Electric Vehicle Market Analysis: Germany
### Comprehensive Data Analysis of EV Sales & Charging Infrastructure (2011-2023)

![Electric Vehicle](https://img.shields.io/badge/Electric%20Vehicle-Analysis-brightgreen)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-blue)
![Power BI](https://img.shields.io/badge/Power%20BI-Visualization-orange)
![Data Analysis](https://img.shields.io/badge/Data-Analysis-red)

---

## 🎯 Project Overview

This project presents a comprehensive analysis of Germany's electric vehicle market transformation from 2011-2023, examining both **Battery Electric Vehicles (BEVs)** and **Plug-in Hybrid Electric Vehicles (PHEVs)** alongside the supporting charging infrastructure across all German states.

**Key Achievement**: Analyzed Germany's journey from 5,000 annual EV sales in 2011 to over 830,000 units in 2022, supported by 65,249 charging stations nationwide.

---

## 📊 Key Findings

### Market Growth Highlights
- **2011-2018**: Foundation period with <50k annual sales
- **2019-2022**: Explosive growth phase reaching 830k+ units
- **2023**: Market maturation with strategic recalibration
- **Infrastructure**: 65,249 charging stations (77% standard, 23% fast chargers)

### Regional Leaders
1. **Bayern**: 17,213 charging stations
2. **Baden-Württemberg**: 14,332 charging stations  
3. **Nordrhein-Westfalen**: 9,279 charging stations

---

## 🛠️ Technical Stack

| Tool | Purpose | Usage |
|------|---------|--------|
| **PostgreSQL** | Database Management | Complex queries, data aggregation, geospatial analysis |
| **Power BI** | Data Visualization | Interactive dashboards, trend analysis, KPI tracking |
| **SQL** | Data Analysis | Statistical calculations, data transformation |

---

## 🔍 Data Sources

### Primary Sources
1. **[IEA Global EV Data Explorer](https://www.iea.org/data-and-statistics/data-tools/global-ev-data-explorer)**
   - Electric vehicle sales statistics
   - Market share data by vehicle type
   - Annual sales trends (2011-2023)

2. **[Bundesnetzagentur - German Federal Network Agency](https://www.bundesnetzagentur.de/DE/Fachthemen/ElektrizitaetundGas/E-Mobilitaet/Ladesaeulenkarte/start.html)**
   - Charging station locations and specifications
   - Infrastructure development timeline
   - Regional distribution data

---

## 🗄️ Database Schema

### Main Tables
```sql
-- Charging Infrastructure Data  
CREATE TABLE evcharging_germany (
    id_device INTEGER,
    company_name VARCHAR(115),
    type_device VARCHAR(20),    
    number_charger INTEGER,
    power_device_kw NUMERIC,
    plug_types VARCHAR(15),
    commissioning_date DATE,
    street_name VARCHAR(55),
    street_number VARCHAR(15),
    postal_code INTEGER,
    place VARCHAR(45),
    states VARCHAR(25)
);
```

![SQL table creation](https://github.com/user-attachments/assets/fb8bd6af-37a1-45d7-874d-b5bbb2e005ac)

---

## 📈 Key SQL Analyses

### 1. Fast Charger Distribution by State
```sql
SELECT states, COUNT(type_device) FROM evcharging_germany
WHERE type_device='Fast charger' AND power_device_kw>100
GROUP BY states, type_device
ORDER BY states;
```

![SQL fast charger more 100kw per states](https://github.com/user-attachments/assets/1b10b616-8cbc-44aa-8a81-4eaccbcf7677)

### 2. Total EV Infrastructure Count
```sql
SELECT COUNT(*) FROM evcharging_germany
WHERE type_device = 'Fast charger';
-- Result: 14,807 fast chargers
```

![SQL numbers of fast charger](https://github.com/user-attachments/assets/061ccb48-2bc1-4eef-a048-a3d871ab18df)

### 3. Regional Infrastructure Analysis
```sql
SELECT states, COUNT(type_device) FROM evcharging_germany
WHERE type_device='Standard charger'
GROUP BY states, type_device
ORDER BY states;
```

![SQL standard charger per states](https://github.com/user-attachments/assets/755af443-89cd-4919-b629-f9fa4a85452a)

---

## 📊 Visualizations & Insights

### Power BI Dashboard Components
- **Time Series Analysis**: EV sales trends (2011-2023)
- **Geographic Distribution**: Charging stations by German states
- **Market Composition**: BEV vs PHEV market share evolution
- **Infrastructure Density**: Fast vs Standard charger distribution
- **Growth Correlation**: Sales vs Infrastructure development

![power BI phev and bev germany](https://github.com/user-attachments/assets/59efec21-fd29-451c-a7b1-c8651ffa9cd4)


### Key Performance Indicators (KPIs)
- Total EV Sales: 3.2M+ vehicles (2011-2023)
- Infrastructure Coverage: 65,249 charging points
- Fast Charging Ratio: 23% of total infrastructure
- Peak Sales Year: 2022 (830,000+ units)

---

## 📋 Analysis Results Summary

### Market Transformation (2011-2023)
- **Growth Rate**: 16,500% increase in annual EV sales
- **Market Leadership**: PHEVs overtook BEVs by 2021
- **Infrastructure Scaling**: 65k+ charging stations deployed

### Regional Insights
- **Top 3 States**: Bayern, Baden-Württemberg, NRW control 62% of infrastructure
- **Emerging Markets**: Brandenburg, Bremen show growth potential
- **Urban vs Rural**: 77% standard chargers serve local communities

### Business Intelligence
- **Market Size**: €15+ billion annual opportunity
- **Investment Areas**: Fast charging, rural expansion, grid integration
- **Risk Factors**: Policy dependency, technology evolution

---

## 🙏 Acknowledgments

- **International Energy Agency (IEA)** for comprehensive EV market data
- **Bundesnetzagentur** for detailed charging infrastructure datasets
- German Federal Government for transparent data accessibility

---
