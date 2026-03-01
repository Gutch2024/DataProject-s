# EuroEdu Analytics Center
## Data Warehouse & Business Intelligence — Gender Parity in European Higher Education

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Tool](https://img.shields.io/badge/Tool-Power%20BI-F2C811?logo=powerbi&logoColor=black)
![Data](https://img.shields.io/badge/Data-Eurostat%20%2F%20PORDATA-003399?logo=europeanunion&logoColor=white)
![Period](https://img.shields.io/badge/Period-2013--2023-blue)

> **Analysis period:** 2013–2023 · **Data source:** PORDATA / Eurostat · **Tool:** Power BI Desktop

---

## Overview

This project builds a **Data Warehouse and Business Intelligence solution** to analyse gender parity in European higher education. Using public data from Eurostat/PORDATA, it models ~390 million student records across 10 years, countries, study cycles and fields of education — delivering interactive Power BI dashboards with key gender-parity indicators.

**Key questions answered:**
- Is there gender balance (≈50/50) across European higher education?
- Which countries, study cycles and fields show the strongest imbalances?
- How has gender parity evolved from 2013 to 2023?

---

## Dashboard Preview

> **Screenshots coming soon** — open `report/Relatorio-DW-BI.pbix` in Power BI Desktop to explore the full interactive report.

<!-- Once you have screenshots, replace the lines below:
![Global Overview Dashboard](docs/images/dashboard-overview.png)
![Country Comparison](docs/images/dashboard-countries.png)
![Time Trends](docs/images/dashboard-trends.png)
-->

---

## Repository Structure

```
DataProject-s/
├── data/
│   └── Data-Warehouse-Business-Project.xlsx   # Fact table & base data (ETL source)
├── report/
│   └── Relatorio-DW-BI.pbix                   # Power BI report (requires Power BI Desktop)
├── docs/
│   ├── Report-DW-BI-EN.pdf                    # Full project report (English)
│   ├── Relatorio-DW-BI-PT.pdf                 # Full project report (Portuguese)
│   └── images/                                # Dashboard screenshots
├── .gitignore
├── LICENSE
└── README.md
```

> **Note:** To open the `.pbix` file, download [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free). Refresh the data source pointing to `data/Data-Warehouse-Business-Project.xlsx`.

---

## Data Model — Star Schema

Fact table **`FactEnsinoSuperior`** with granularity at `Year + Country + Gender + Study Cycle + Field of Education`:

| Dimension | Values |
|---|---|
| DimYear | 2013 – 2023 |
| DimCountry | European countries (Eurostat) |
| DimGender | Male / Female |
| DimCycle | Short Cycle, Bachelor, Master, PhD |
| DimField | Eurostat/PORDATA education categories |
| **Measure** | **Number of enrolled students** |

---

## ETL Process

1. **Extract** — CSV from PORDATA/Eurostat (last updated 15-09-2025)
2. **Transform** — Excel: header normalisation, data type correction, whitespace removal → Power Query: null handling via DAX measures, deduplication, category consistency
3. **Load** — Fact table imported into Power BI data model

---

## KPIs & Dashboards

| Dashboard Page | Key Indicators |
|---|---|
| Global Overview | Total students, % Male, % Female, Gender Gap %, GPI |
| By Country | % Male/Female per country, country contribution to EU total |
| By Study Cycle | Gender distribution across Short Cycle / Bachelor / Master / PhD |
| By Field | Gender breakdown per education field (STEM vs. Social/Health) |
| Time Trends | Annual variation in % Female and % Male (2013–2023) |

**GPI (Gender Parity Index)** = Female students / Male students — values >1 indicate female majority.

---

## Key Findings

- **Overall balance:** ~54% female / 46% male across the full 10-year period.
- **By country:** Sweden shows the highest female predominance; Germany and Greece are slightly below parity — all within a narrow range.
- **By field:** Strongest imbalances in ICT and Engineering (male-dominated) vs. Education, Health and Social Sciences (female-dominated).
- **By cycle:** Female majority in Bachelor and Master; near-parity in Short Cycle; slight male majority in PhD.
- **Trend:** Patterns are stable — no abrupt shifts across the decade, with small annual variations.

---

## Technologies

| Tool | Purpose |
|---|---|
| **Power BI Desktop** | Data model, Power Query (ETL), DAX measures, dashboards |
| **Microsoft Excel** | Initial data cleaning, CSV → structured table conversion |
| **PORDATA / Eurostat** | Official European higher education statistics |

---

## How to Run

1. Clone or download this repository.
2. Open `report/Relatorio-DW-BI.pbix` in Power BI Desktop.
3. If prompted, update the data source path to `data/Data-Warehouse-Business-Project.xlsx`.
4. Click **Refresh** to reload data.

---

## License

This project is licensed under the [MIT License](LICENSE).

---

*Project developed for academic purposes — CTESP Data Analysis & Programming, Instituto Piaget.*
