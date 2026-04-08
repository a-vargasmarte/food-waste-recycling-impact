# Cary Food Waste Diversion: Interactive Data Story
**Project Brief - Draft v1.0**

---

## Project Overview

This project is an interactive data visualization platform that communicates the environmental impact of the Town of Cary's "Cary Composts - Food Waste Recycling" service. The service began on February 7, 2022 following a successful pilot program and a 2019 waste characterization study that found nearly 30% of single-family household waste in Cary was food waste ([Wake County Waste Characterization Study, 2019](https://s3.us-west-2.amazonaws.com/wakegov.com.if-us-west-2/prod/documents/2020-10/2019%20Wake%20WCS%20Final%20Report_Final.pdf)).

Using publicly available data from Cary's open data portal, this web application will track food waste diversion trends, visualize program impact, and forecast future diversion through 2026 and 2030.

---

## Problem Statement

While the Town of Cary collects and publishes food waste recycling data in a timely fashion, the interpretation of the impact of the town's food waste recycling efforts lacks relatable context for most residents and stakeholders. Community members cannot readily understand:

- Future food waste collection projections based on current trends.
- Variation in food waste collection efforts by collection site.
- Seasonality in food waste collection efforts
- Deeper understanding of the environmental implications based on historical efforts.

Without clear visualization and analysis, the value and impact of Cary's composting efforts remain stunted, limiting community engagement and informed policy decisions.

---

## Research Questions

This project addresses three primary questions:

1. **How much food waste is projected to be diverted by the Town of Cary by the end of 2026?**
2. **How much food waste is projected to be diverted by the Town of Cary by the end of 2030?**
3. **How does food waste diversion vary by drop-off location?** (Currently three sites in Cary)

Secondary questions include:
- What seasonal and weekly trends exist in food waste collection?
- What is the greenhouse gas emission reduction impact compared to landfilling?

---

## Target Audience

**Primary Audiences:**
- **Cary Residents**: General public interested in understanding their community's environmental impact
- **Policymakers**: Town of Cary officials evaluating program effectiveness and planning future initiatives
- **Waste Industry Professionals**: Practitioners interested in municipal composting program outcomes

**Secondary Audiences:**
- Environmental advocates and sustainability organizations
- Other municipalities considering similar programs
- Researchers studying food waste diversion strategies and communication tools

---

## Project Goals

**1. Data Transparency & Accessibility**
- Transform raw municipal data into intuitive, interactive visualizations
- Make food waste diversion metrics accessible to non-technical audiences

**2. Impact Communication**
- Quantify environmental benefits (greenhouse gas emissions avoided, landfill diversion)
- Highlight community contribution to sustainability goals

**3. Predictive Insights**
- Forecast future food waste diversion using statistical modeling
- Provide data-driven projections to inform program planning

**4. Automated Updates**
- Build system to automatically ingest new monthly data from Cary's portal
- Ensure projections and visualizations remain current without manual intervention

---

## Environmental Context

According to the Proceedings of the National Conference on Undergraduate Research (NCUR) at UNC Asheville, composting one ton of food waste produces less than 10% of the greenhouse gas emissions compared to landfilling the same amount.

**Current Impact (as of latest data):**
- Approximately **597,749 pounds** of food waste collected through Cary Composts service
- Significant reduction in methane emissions from landfill diversion
- Compost production supporting local soil health and circular economy, including a portion return to the earth at [Good Hope Farm](https://www.carync.gov/recreation-enjoyment/parks-greenways-environment/community-gardens-urban-agriculture/good-hope-farm).

---

## Technical Approach

### Data Sources
- **Primary**: Town of Cary [Food Waste Recycling Impact API](https://data.townofcary.org/explore/dataset/food-waste-pilot/api/?sort=date_collection_datetime&disjunctive.stop_name)
  - Drop-off location (stop name)
  - Collection date
  - Food waste collected (lbs)
  - Estimated compost produced (lbs)

### Technology Stack

**Data Pipeline & Analysis:**
- Python (pandas, scikit-learn, statsmodels) for data analysis and forecasting models
- PostgreSQL for data storage and management
- Automated monthly data ingestion from Cary API

**Web Application:**
- **Frontend**: React.js framework for interactive user interface
- **Visualization**: D3.js for custom, publication-quality data visualizations
- **Backend**: Node.js and Express.js for API routing and server-side logic
- **Deployment**: Google Firebase for hosting and continuous deployment
- **Version Control**: GitHub for code management and documentation

### Analytical Methods
- Time-series forecasting for 2026 and 2030 projections
- Seasonal decomposition to identify weekly and seasonal trends
- Location-based aggregation and comparison analysis
- Environmental impact calculations (CO2 equivalent, landfill space saved)

---

## Key Features

**Interactive Visualizations:**
- Time-series trend of food waste collection since program inception
- Seasonal and weekly pattern analysis
- Drop-off location comparison and performance metrics
- Forecasts through 2026 and 2030 with confidence intervals
- Environmental impact dashboard (GHG emissions avoided, compost produced)

**Automated Data Updates:**
- Monthly refresh as new data published by Town of Cary
- Real-time recalculation of forecasts and statistics

**User Experience:**
- Scroll-driven narrative data story
- Mobile-responsive design
- Accessible visualizations with clear annotations

---

## Deliverables

1. **Public-facing website** with interactive data visualizations and forecasts
2. **GitHub repository** with complete project code and documentation
3. **Technical documentation** explaining methodology, data sources, and limitations
4. **Blog post / case study** summarizing findings and community impact

---

## Timeline & Iteration

This project follows an iterative development approach. Specific implementation details will evolve as technical challenges are encountered and stakeholder feedback is incorporated. For the most current project status, methodology, and technical specifications, refer to the [project repository](https://github.com/[your-username]/cary-food-waste-analysis) (link to be added). The estimated timeline below is subject to change as time goes on.

**Estimated Timeline:**
- Weeks 1-2: Data exploration, pipeline development, project scoping
- Weeks 3-6: Exploratory analysis, forecasting model development
- Weeks 6-8: Web application development and D3.js visualizations
- Weeks 9-10: Testing, refinement, stakeholder feedback, deployment

---

## Project Context

This project is being developed as part of the **Technologists for the Public Good** civic tech [mentorship program](https://www.publicgood.tech/programs/mentorship). It serves as a demonstration of how publicly available municipal data can be transformed into actionable insights for residents, policymakers, and sustainability professionals.

---

## Contact & Collaboration

For questions, feedback, or collaboration opportunities, please visit the project repository or contact Alberto Vargas at alberto@cacicon.com.

**Note:** This is a living document and will be updated as the project evolves.

---

*Last Updated: 2-16-26*