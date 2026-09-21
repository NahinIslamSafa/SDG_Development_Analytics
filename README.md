# SDG Development Analytics

A data analytics project built around selected United Nations Sustainable Development Goal (SDG) indicators, combining Python-based data preparation and quality analysis with an interactive Power BI dashboard.

The project explores SDG indicator coverage, geographic reach, trends, performance changes, indicator-level details, and important data-quality characteristics within the selected dataset.

---

## Project Overview

Monitoring progress toward the Sustainable Development Goals requires more than simply visualizing indicator values. SDG datasets can contain different observation types, geographic and demographic disaggregations, missing observations, and threshold-reported values that require careful interpretation before analysis.

This project was developed to create a structured analytical view of selected SDG indicators and provide an interactive dashboard for exploring:

- Indicator coverage across SDG Goals
- Observation volume and geographic coverage
- Changes in indicator values over time
- Indicator performance status
- Country-level comparisons
- Individual indicator trends
- Indicator metadata and information
- Non-numeric threshold observations
- Data coverage and quality considerations

---

## Objectives

The main objectives of the project are to:

1. Explore the structure and coverage of selected SDG data.
2. Prepare the data for analytical use while preserving meaningful non-numeric observations.
3. Investigate missing values and distinguish them from threshold-reported observations.
4. Examine how SDG dimensions and disaggregations affect the structure of observations.
5. Analyze indicator trends over time.
6. Provide a Power BI dashboard for interactive development monitoring and exploration.
7. Present data-quality considerations alongside analytical results.

---

## Dataset

The project uses data from the United Nations Sustainable Development Goal indicator framework.

The dataset used for this project contains selected SDG Goals and their associated indicators, series, geographic areas, time periods, observations, and metadata fields.

The analysis covers:

- **36 indicators**
- **239 geographic areas**
- **~101K observations**
- **2015–2024**
- **10 selected SDG Goals:** 1, 2, 3, 4, 5, 7, 8, 9, 10, and 13

The project uses fields such as:

- Goal
- Target
- Indicator
- SeriesCode
- SeriesDescription
- GeoAreaName
- TimePeriod
- Value
- Units
- Nature
- Reporting Type
- Observation Status
- and relevant SDG disaggregation dimensions

Official UN SDG indicator metadata:
https://unstats.un.org/sdgs/metadata/

---

## Data Preparation & Quality Analysis

The accompanying Jupyter Notebook documents the exploratory data preparation and quality-analysis process.

### Combining SDG Goal Data

Individual Goal-level datasets were loaded and combined into a single analytical dataset.

### Preserving Original Values

A key data-quality issue identified during preparation was the presence of non-numeric threshold observations such as:

- `<2.5`
- `<0.1`

These values should not automatically be treated as ordinary missing values.

Converting the original `Value` field directly to a numeric datatype using coercion can turn threshold observations into `NaN`. Therefore, the original `Value` field was preserved while a separate numeric representation was used where numerical calculations were required.

### Missing vs Threshold-Reported Observations

The analysis distinguishes between:

- genuinely missing observations
- numeric observations
- non-numeric threshold observations

The dashboard identifies **737 threshold-reported observations** in the selected dataset, including:

| SeriesCode | Value | Observations |
|---|---:|---:|
| SN_ITK_DEFC | `<2.5` | 578 |
| SN_ITK_DEFCN | `<0.1` | 159 |

These observations are retained as meaningful information rather than being silently treated as missing data.

### SDG Disaggregation

The dataset contains multiple dimensions that can produce multiple observations for the same country, year, and series.

Examples include dimensions such as:

- Age
- Location
- Sex
- Education level
- Type of skill
- Disability status
- Quantile
- and other reporting dimensions

Therefore, multiple observations for a country-year are not automatically considered duplicate records.

The analysis examines these dimensions before interpreting repeated country-year observations.

### Duplicate Analysis

The notebook also investigates potential duplicate observations while considering the relevant SDG dimensions.

---

## Power BI Dashboard

The final dashboard is organized into four analytical pages.

### 1. SDG Overview

Provides a high-level view of the dataset and its coverage.

Key elements include:

- Total indicators
- Total geographic areas
- Total observations
- Earliest and latest years
- Number of indicators by SDG Goal
- Observation volume by Goal
- Observation coverage over time
- Geographic coverage by Goal

This page establishes the overall scope and structure of the dataset.

---

### 2. Country Performance & Comparison

Examines indicator performance and country-level comparisons.

The page includes:

- Country, Goal, and SeriesCode filters
- Indicator coverage by SDG Goal
- Indicator performance status by Goal
- Overall performance status
- Performance trend over time
- Country comparison by indicator

Performance status is categorized using the project's analytical framework, including:

- Improving
- Deteriorating
- Stable
- No Recent Comparison
- Threshold-reported

The page is intended to support exploration rather than provide a single overall ranking of countries.

---

### 3. Indicator Explorer

Provides a detailed view of an individual indicator for a selected country.

Users can filter by:

- Country
- Goal
- Target
- SeriesCode

The page presents:

- Start Value
- Latest Value
- Long-Term Change
- Performance Status
- Indicator trend over time
- Start vs Latest Value
- Indicator information and metadata

This page allows the user to move from the broader SDG-level view to a specific indicator and examine its historical behavior.

---

### 4. Data Quality & Coverage

Focuses on the structure and usability of the underlying SDG data.

The page includes:

- Observation volume over time
- Geographic reach over time
- Observation distribution by SDG Goal
- Observation volume vs geographic coverage
- Non-numeric threshold observations

This page is particularly important because it makes data-quality characteristics visible instead of treating the dataset as a perfectly uniform collection of numeric observations.

---

## Analytical Approach

The analysis combines Python-based data preparation and quality assessment with Power BI-based exploratory and comparative analysis. The workflow focuses on consolidating selected SDG datasets, examining missing and threshold-reported observations, assessing disaggregation and duplicate records, and preparing the data for dashboard analysis. Power BI measures and visualizations are then used to examine indicator coverage, geographic reach, performance changes, and data quality.
