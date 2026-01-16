# AIRBUS-powerbi-sales-dashboard
Smartphone Logistics Performance Dashboard (Power BI)

A single-page executive dashboard built in **Power BI** to monitor **smartphone logistics performance** across time (year/month/week), business unit, and country. It consolidates key KPIs, rollout/forecast trends, inventory & backlog signals, and order distribution into one view for quick weekly/monthly follow-up.

## Preview
![Dashboard Preview](Users/37045/Pictures/kpi-overview.png)

## Key Features
- **Interactive time controls**: Year / Month / Week slicers (range sliders) for flexible period selection (e.g., Jan–Mar vs. full year).
- **Run with Week / Run with Month (Dynamic Demo Controls)**:  
  Built-in playback controls to **auto-animate the dashboard over time** (weekly or monthly). When running, **all visuals update dynamically** to demonstrate trends and changes across the selected timeline—useful for presentations and storytelling.
- **Core KPI cards**: Users contacted, smartphones delivered, ordered, informed, received, and prepared.
- **Rollout & forecast monitoring**: Trend view comparing actual vs. forecast (manual/auto) with deviation alert (e.g., “Danger”).
- **Inventory & backlog view**: Combined chart showing received vs. delivered volumes, net effect, and backlog evolution (**K units**).
- **Country distribution + popular model**: Order share by country with a highlight of the most popular phone model.
- **Business unit & country filters**: Slice performance by BU and geography.

## Data & Privacy
- Uses **mock/synthetic data** (no real personal or company data).
- Original version referenced an **Oracle** data source during development. Credentials are no longer available, so **refresh may fail or prompt for login; please refer to the PDF instead.**

## Files
- `images/kpi-overview.png` — dashboard screenshot preview  
- `exports/smartphone-logistics-dashboard.pdf` — PDF export for easy viewing (recommended)  
- `report/smartphone-logistics-dashboard.pbix` — Power BI source file (optional)

## How to View
### Option A (Recommended): View the PDF
Open: `exports/smartphone-logistics-dashboard.pdf`

### Option B: Open the PBIX (Power BI Desktop required)
1. Download `report/smartphone-logistics-dashboard.pbix`
2. Open with **Power BI Desktop**
3. Note: data refresh may prompt for credentials due to the retired Oracle connection.

## Skills Demonstrated
- Dashboard design for **executive KPI monitoring**
- Data modeling with a **Date dimension** (time intelligence-ready)
- DAX measures (KPI aggregations, unit scaling to **K**)
- Interactive reporting (slicers, cross-filtering, **time playback animation** for demos)

## Project Context
Designed as a **single-page executive dashboard** to support fast, repeatable weekly/monthly monitoring and issue spotting (inventory/backlog build-up, forecast deviation, geographic concentration).

---
