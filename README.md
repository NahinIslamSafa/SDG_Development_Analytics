# SDG Development Analytics

An end-to-end data analytics project using selected United Nations Sustainable Development Goal (SDG) indicators to explore development trends, geographic coverage, indicator performance, and data quality.

The project combines **Python-based data preparation and exploratory analysis** with an interactive **Power BI dashboard** designed for SDG monitoring and development-oriented analysis.

---

## Project Overview

The United Nations Sustainable Development Goals provide a global framework for monitoring progress across economic, social, and environmental development.

This project analyzes a selected subset of SDG indicators from the UN Global SDG Indicators Database. The analysis focuses on:

- Indicator and observation coverage
- Geographic reach of SDG data
- Trends across available years
- Country-level comparisons
- Indicator-level performance changes
- Missing and threshold-reported observations
- Data disaggregation and observation structure
- Data quality and coverage considerations

The final results are presented through a four-page Power BI dashboard.

---

## Objectives

The project was developed to:

- Consolidate selected SDG datasets from multiple Goal-level files.
- Examine the structure and coverage of the available SDG observations.
- Identify and distinguish missing observations from threshold-reported values.
- Investigate disaggregated observations across different demographic and contextual dimensions.
- Analyze indicator-level changes across the available time period.
- Compare indicator coverage and performance across geographic areas.
- Build an interactive Power BI dashboard for development monitoring.
- Demonstrate a practical data analytics workflow using Python and Power BI.

---

## Dataset

The project uses selected data from the **United Nations Global SDG Indicators Database**.

### Scope of the analysis

| Metric | Coverage |
|---|---:|
| SDG Goals analyzed | 10 |
| Indicators | 36 |
| Geographic areas | 239 |
| Observations | ~101K |
| Earliest year | 2015 |
| Latest year | 2024 |

### SDG Goals included

The analysis covers the following selected SDG Goals:

- Goal 1 — No Poverty
- Goal 2 — Zero Hunger
- Goal 3 — Good Health and Well-being
- Goal 4 — Quality Education
- Goal 5 — Gender Equality
- Goal 7 — Affordable and Clean Energy
- Goal 8 — Decent Work and Economic Growth
- Goal 9 — Industry, Innovation and Infrastructure
- Goal 10 — Reduced Inequalities
- Goal 13 — Climate Action

The project does not attempt to represent the complete SDG indicator framework. It focuses on the selected Goal-level datasets included in the analysis.

---

## Data Preparation & Quality Analysis

Python was used to inspect, combine, and analyze the selected SDG datasets before visualization in Power BI.

### Data Consolidation

The individual Goal-level datasets were loaded and combined into a consolidated analytical dataset.

Initial inspection included:

- Dataset dimensions
- Column structures
- Indicator and SeriesCode coverage
- Goal-level observation counts
- Data types
- Missing values
- Geographic coverage
- Time coverage

### Preserving Original Values

The original `Value` field was retained because SDG observations are not necessarily represented only as conventional numeric values.

Some observations contain threshold-reported values such as:

- `<2.5`
- `<0.1`

Converting the original field directly to numeric values would turn these observations into missing values. Therefore, numeric transformations were handled separately so that threshold-reported observations could remain identifiable during data quality analysis.

### Missing vs Threshold-Reported Observations

A distinction was made between genuinely missing observations and observations reported using threshold notation.

The analysis identified **737 threshold-reported observations** in the selected dataset:

- `<2.5` — 578 observations
- `<0.1` — 159 observations

These observations were retained as meaningful reported information rather than being treated as ordinary missing values.

### Disaggregation Analysis

The dataset contains observations reported across different dimensions. Depending on the indicator, these may include dimensions such as:

- Age
- Sex
- Location
- Education level
- Disability status
- Quantile
- Population group
- Other indicator-specific classifications

These dimensions were considered when examining the structure of observations and potential duplicate records.

### Duplicate Analysis

Duplicate checks were performed with consideration for the dataset's disaggregation structure.

Multiple observations for the same indicator, geographic area, and year are not automatically duplicates because they may represent different valid disaggregated categories.

---

## Power BI Dashboard

The processed data was used to create a four-page Power BI dashboard.

### 1. SDG Overview

Provides a high-level view of the dataset and its overall coverage.

Key elements include:

- Total indicators
- Total geographic areas
- Total observations
- Earliest available year
- Latest available year
- Number of indicators by SDG Goal
- Number of observations by SDG Goal
- Observation coverage over time
- Geographic coverage by SDG Goal

### 2. Country Performance & Comparison

Examines indicator-level performance and enables comparisons across geographic areas.

Key elements include:

- Country filtering
- SDG Goal filtering
- SeriesCode filtering
- Indicator coverage by Goal
- Overall indicator performance status
- Performance status by SDG Goal
- Performance trends
- Country comparison by indicator

Performance categories used in the dashboard include:

- Improving
- Deteriorating
- Stable
- No Recent Comparison
- Threshold-reported

### 3. Indicator Explorer

Provides a focused view of an individual indicator and its available observations.

Users can explore:

- Country
- SDG Goal
- Target
- SeriesCode

The page provides:

- Start Value
- Latest Value
- Long-Term Change
- Performance Status
- Indicator trend over time
- Start vs Latest Value
- Indicator metadata and information

### 4. Data Quality & Coverage

Focuses on the completeness, geographic reach, and reporting characteristics of the underlying dataset.

Key elements include:

- Coverage volume and geographic reach
- Observation distribution by SDG Goal
- Observation volume versus geographic coverage
- Non-numeric threshold observations

The threshold observation analysis highlights reported values such as `<2.5` and `<0.1` that should not be treated as ordinary missing values.

---

## Analytical Approach

The project combines exploratory data analysis, data quality assessment, and interactive visualization.

Python was primarily used for dataset inspection, consolidation, data quality analysis, and examination of the structure of SDG observations. Power BI was then used to develop interactive views of indicator coverage, geographic reach, performance changes, trends, and data quality.

Performance analysis in the dashboard compares available observations over the selected period. Because SDG indicators differ in measurement units, definitions, reporting frequency, and desirable direction of change, performance interpretation is handled at the indicator level rather than treating all indicators as directly comparable.

---

## Key Data Insights

The analysis provides several observations about the structure of the selected SDG data:

- The dataset contains approximately 101K observations across 239 geographic areas.
- Coverage varies substantially across SDG Goals and indicators.
- Observation availability differs across countries and years.
- SDG indicators may contain multiple observations for the same country and year because of valid disaggregation categories.
- Threshold-reported observations occur in the selected dataset and represent reported information rather than conventional missing values.
- Indicator performance cannot always be compared directly because indicators use different units, measurement approaches, and reporting structures.
- Data availability and geographic coverage are important considerations when interpreting SDG trends.

These findings are intended to support data-informed exploration rather than provide a comprehensive assessment of global SDG progress.

---

## Tools & Technologies

- **Python**
  - Pandas
  - NumPy
  - Jupyter Notebook
- **Power BI**
  - Power Query
  - DAX
  - Interactive data visualization
- **GitHub**
  - Project documentation
  - Versioned project files

---

## Limitations

- This project analyzes a selected subset of SDG Goals and indicators rather than the complete SDG framework.
- Data availability varies across indicators, countries, and years.
- Indicators use different units, definitions, and reporting methodologies, so their raw values are not directly comparable.
- Performance classifications in the dashboard are analytical interpretations and are not official UN SDG ratings.

---

## Data Source & Official Documentation

The data used in this project originates from the United Nations Global SDG Indicators Database.

Official UN resources:

- [UN SDG Indicators](https://unstats.un.org/sdgs/indicators/en/)
- [UN SDG Metadata Repository](https://unstats.un.org/sdgs/metadata/)
- [Official List of Global SDG Indicators](https://unstats.un.org/sdgs/metadata/)
- [UN SDG Database Archive](https://unstats.un.org/sdgs/indicators/database/archive)

The UN metadata repository provides reference metadata for the global SDG
indicator framework, including indicator definitions and methodological
information. The repository is periodically updated by the UN system and
relevant international organizations.

For indicator-specific definitions and methodological interpretation,
refer to the corresponding official UN metadata.
