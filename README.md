# Smartphone Logistics Performance Dashboard (End-to-End BI Project)

Single-page executive dashboard for SMART Service (Airbus context) to monitor smartphone logistics performance and rollout progress through weekly-refreshed KPIs.  
This project covers the full BI lifecycle end-to-end: **requirements → data modeling → Talend ETL → Oracle data mart → Power BI dashboard**. :contentReference[oaicite:1]{index=1}

![Dashboard Preview](kpi-overview.png)

---

## 1. Project Background
SMART Service supports Airbus employees with smartphone provisioning and operations (eligibility → selection → reception/configuration → appointment → delivery).  
The business requested an automated KPI dashboard to monitor team activity and performance, with governance and security constraints. :contentReference[oaicite:2]{index=2}

**Key requirements**
- **One-pager**: all KPIs on a single page (executive view). :contentReference[oaicite:3]{index=3}  
- **Weekly refresh** and historical tracking. :contentReference[oaicite:4]{index=4}  
- **Security / roles** separation (admin vs users) + SSO recommended. :contentReference[oaicite:5]{index=5}  
- **Data quality log** during integration (error visibility). :contentReference[oaicite:6]{index=6}  
- **Retention**: keep data for 2 years. :contentReference[oaicite:7]{index=7}  
- Filters: time range, country, and business unit. :contentReference[oaicite:8]{index=8}  

---

## 2. What I Built (Deliverables)
### A) Power BI Dashboard (KPI-Performance)
A single-page dashboard designed as an executive cockpit:
- **KPI 1 – Weekly logistics follow-up**: contacted, ordered, received, prepared, informed, delivered  
- **KPI 2 – SMART rollout follow-up**: actual vs forecast (manual/auto), deviation alert  
- **KPI 3 – Inventory / backlog**: stock in/out, net effect, cumulative backlog (K units)  
- **KPI 4 – Popular smartphone**: distribution by country + most popular model  
- **Interactive slicers**: Year / Month / Week + Business Unit + Country  
- **Run with Week / Run with Month**: playback controls that animate the timeline so **all visuals update dynamically** for demos and storytelling

### B) Data Mart in Oracle (Mag_SMART)
A centralized analytical store built to serve all KPI needs with consistent definitions:
- Dimensions: **Time**, **Business Unit**, **Country**
- Facts/measures aligned with KPI measurement dictionary (counts/sums for operational steps, stock movements, backlog, etc.) :contentReference[oaicite:9]{index=9}

### C) Automated ETL in Talend
A production-style pipeline to ingest, standardize, validate, and load weekly extracts from multiple repositories.

> **Important:** All components above (Talend jobs + Oracle data mart + Power BI model & dashboard) were designed and implemented by me end-to-end.

---

## 3. Data Sources
Operational data originates from three non-integrated repositories (weekly extracts): :contentReference[oaicite:10]{index=10}
- **BES**
- **SMART Portal**
- **Fleet** (shared directory exports)

---

## 4. Architecture Overview
**Data Flow**
1. Source files (BES / Portal / Fleet)  
2. **Talend ETL pipeline** (staging → standardization → cleansing → validation)  
3. **Oracle DW / Data Mart (Mag_SMART)**  
4. **Power BI** semantic model + measures + dashboard :contentReference[oaicite:11]{index=11}

---

## 5. ETL Pipeline (Talend) – Technical Highlights
### 5.1 Staging & Standardization
- Load delimited flat files into a staging area to preserve raw snapshots (auditability)
- Normalize formats (e.g., dates to consistent patterns; token parsing when fields contain extra characters)

### 5.2 Data Quality, Validation, and Reuse
- Handle common issues: nulls, inconsistent values, manual spelling errors
- Implement reusable **Java routines** inside Talend and call them in **tMap** for consistent rule enforcement
- Apply business rules required by reporting (e.g., week number derivation when missing) :contentReference[oaicite:12]{index=12}

### 5.3 Traceability & Lineage
- Track metadata: source system, file name, load timestamp, row counts
- Reconciliation checks between staging and curated layers to support lineage and audit

### 5.4 Error Logging & Exception Handling
- Row-level rejects (quarantine) with reason codes
- Job-level exception handling for schema mismatch/corrupted files/connection failures
- Integration requirement: **data quality log available during file integration** :contentReference[oaicite:13]{index=13}

### 5.5 Scheduling
- Weekly load cadence to meet refresh requirements (e.g., Monday morning schedule) :contentReference[oaicite:14]{index=14}

---

## 6. Data Modeling (Oracle Data Mart)
Designed as a star schema to support flexible slicing and consistent KPIs: :contentReference[oaicite:15]{index=15}
- **Dim_Time**: Date, Week, Month, Quarter, Year
- **Dim_BU**: Business Unit
- **Dim_Country**: Country
- Fact tables aligned with operational steps and performance indicators

This structure enables:
- Time-range selection (week/month/quarter/year)
- BU and Country filtering
- KPI aggregation at different granularities without redefining business rules

---

## 7. Power BI Model & Reporting Layer
- Connect Power BI to the curated **Mag_SMART** data mart
- Build measures for KPIs (including K-unit scaling) and ensure consistent definitions
- Apply unified look & feel (single-page cockpit) and interactive filtering
- Provide dynamic playback with **Run with Week / Run with Month** for presentation-mode analytics

---

## 8. Files in This Repository
- `images/kpi-overview.png` — dashboard screenshot preview  
- `exports/smartphone-logistics-dashboard.pdf` — PDF export for quick viewing (recommended)  
- `report/smartphone-logistics-dashboard.pbix` — Power BI source file (optional)  
- `docs/Concept dossier...docx` — functional & technical design document (project specification) :contentReference[oaicite:16]{index=16}

---

## 9. Notes (Refresh & Credentials)
The original academic/enterprise setup referenced an Oracle environment and controlled credentials.  
If you open the PBIX, **refresh may fail or prompt for login; please refer to the PDF instead.**

---

## 10. Role Fit
This project demonstrates end-to-end capability across:
- **Data Analyst**: KPI design, business rules, dashboard storytelling, stakeholder needs translation  
- **Pipeline / BI Engineer**: ETL automation, data quality, logging/traceability, dimensional modeling, data mart delivery

---
