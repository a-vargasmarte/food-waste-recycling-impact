# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Cary Food Waste Diversion Interactive Data Story - a civic tech project for the Technologists for the Public Good mentorship program. This web application visualizes the environmental impact of the Town of Cary's "Cary Composts - Food Waste Recycling" service and forecasts future diversion through 2026 and 2030.

## Development Commands

```bash
# Activate virtual environment
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run Jupyter notebook
jupyter lab

# Open specific notebook
jupyter lab notebook/DataExploration.ipynb
```

## Data Source

**Town of Cary Food Waste Recycling Impact API**
- Base URL: `https://data.townofcary.org/api/explore/v2.1/catalog/datasets/food-waste-pilot`
- Endpoints: `/records` (100 record limit), `/exports/json` (full dataset)
- Update frequency: Monthly
- No authentication required

**Data fields:**
- `stop_name`: Drop-off location (Citizen's Convenience Center, Mills Park)
- `date_collection_datetime`: Collection date
- `lbs_collected`: Pounds of food waste collected
- `compost_created_lbs`: Estimated compost produced (~10:1 ratio)
- Derived metrics: `Food Waste Tons Collected`, `Food Waste Tons Difference`

**Local Government Annual Reports (LGAR)**
- Source: NC DEQ annual solid waste reports for Town of Cary
- Location: `data/raw/pdfs/CARY LGAR FY XX-XX.pdf`
- Extracted via GreenPT API using PyPDF2
- Programs: Municipal Solid Waste, Recycling, Yard Waste
- Key fields: `Year`, `Program`, `Tons Collected`, `Collection Cost`, `Disposal Cost`, `Total Cost`, `Households/Customers Served`
- Derived metrics: `Collection Cost per Ton`, `Disposal Cost per Ton`, `Collection Cost per Ton Difference`, `Disposal Cost per Ton Difference`

## Architecture

**Current Phase (Data Analysis):**
- Python with pandas, scikit-learn, statsmodels for analysis and forecasting
- Plotly and seaborn for visualization prototyping
- Jupyter notebooks for exploration

**Planned Production Stack:**
- Frontend: React.js + D3.js for scroll-driven data story
- Backend: Node.js/Express.js
- Database: PostgreSQL
- Deployment: Google Firebase

## Key Data Considerations

- Data spans February 2022 to present
- Mills Park collection site added in 2024 (any Mills Park records before 2024 are erroneous)
- Multiple collections can occur on the same day across different sites
- For time-series analysis, aggregate to daily totals using `groupby('date_collection_datetime').sum()`
- The `df_cleaner` pattern in notebooks removes known bad records
- Cary Food Waste Recycling Impact API will be supplemented with Local Government Annual Solid Waste and Materials Management Report data

## Research Questions

1. How much food waste will be diverted by end of 2026?
2. How much food waste will be diverted by end of 2030?
3. How does diversion vary by drop-off location?

## Visualization Approach

The final product uses a "martini glass" narrative structure:
- **Stem**: Author-driven scrollytelling with sticky chart that transitions between views
- **Glass**: Reader-driven exploration with filters for date range, location, and metrics

## Exploratory Charts (DataExploration.ipynb)

**Distribution & Comparison:**
- Histograms: lbs_collected distribution (overall, by year, fiscal year, season)
- Box plots: lbs_collected by year and stop_name, outlier detection with IQR bounds
- Bar plots: lbs_collected by year, tons by fiscal year

**Time Series (Food Waste API):**
- Line plots: daily lbs_collected (overall and by stop_name)
- Monthly tons collected and month-over-month difference
- Daily and yearly tons difference

**LGAR Program Analysis:**
- Grouped bar/line plots by program: Tons Collected, Collection Cost, Disposal Cost
- Cost per ton metrics: Collection Cost per Ton, Disposal Cost per Ton
- Year-over-year difference: Cost per Ton Difference by program

**Combined Analysis:**
- Tons Collected vs Food Waste Tons Collected (dual y-axis)
- Food Waste Tons Difference over fiscal years

## Development Best Practices
- Use comments sparingly. Only comment complex code.