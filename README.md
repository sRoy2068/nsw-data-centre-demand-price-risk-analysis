# NSW Data Centre Demand & Electricity Price Impact Analysis

> **Scenario-based electricity market analytics project examining how future data-centre demand could affect NSW wholesale electricity prices and market risk.**

This project combines **NSW electricity-market data, renewable-generation data, feature engineering and predictive modelling** to investigate how additional data-centre electricity demand may affect wholesale electricity prices.

Historical 5-minute NSW market data was integrated with solar, wind and hydro dispatch data, engineered into market and system-stress features, and modelled using **XGBoost**. Future data-centre demand scenarios were then injected into NSW electricity demand to estimate price impacts across scenarios, seasons, hours of day and stressed market conditions.

---

## Business Problem

Data centres operate as large, near-continuous electricity loads. As the sector expands in NSW, this additional baseload demand could increase wholesale electricity-price pressure and create greater exposure for electricity users, retailers and data-centre operators.

The analysis therefore focuses on four questions:

* How much additional continuous electricity demand could future data-centre growth add to NSW?
* How could this additional demand affect NSW wholesale electricity prices?
* During which seasons, hours and market conditions are price impacts greatest?
* What do these findings imply for electricity procurement and market-risk management?

---

## Analytical Workflow

**Scenario Demand → Feature Engineering → Price Modelling → Market Risk Analysis → Procurement Strategy**

### 1. Scenario Demand

Annual data-centre electricity projections were converted into continuous MW load and expressed as additional demand above the FY2025 baseline.

### 2. Feature Engineering

Historical market data was enriched with renewable-dispatch, temporal and system-stress variables.

### 3. Price Modelling

An XGBoost regression model was trained to estimate NSW wholesale electricity prices under baseline and additional-demand conditions.

### 4. Market Risk Analysis

Price impacts were analysed across scenarios, seasons, hours of day, renewable conditions and system-stress periods.

### 5. Procurement Strategy

The resulting price-risk profiles provide evidence for electricity procurement, hedging and flexible-demand decisions.

---

## Data

The core analytical dataset contains **5-minute NSW electricity-market observations from July 2021 to June 2024**.

### Main variables

| Variable                 | Description                                  |
| ------------------------ | -------------------------------------------- |
| `NSW1_Price`             | NSW wholesale electricity price ($/MWh)      |
| `NSW1_Demand`            | NSW electricity demand (MW)                  |
| `solar_dispatch`         | Aggregated solar dispatch (MW)               |
| `wind_dispatch`          | Aggregated wind dispatch (MW)                |
| `hydro_dispatch`         | Aggregated hydro dispatch (MW)               |
| `Net_Demand`             | Demand remaining after solar and wind output |
| `DemandStressFlag`       | Identifies high-demand intervals             |
| `CoreSystemStressFlag`   | High demand + low solar + evening peak       |
| `SevereSystemStressFlag` | Core stress occurring during autumn/winter   |

### Data Integration

Separate renewable-generation datasets were integrated with NSW demand and price data at a common 5-minute temporal grain.

Key preparation steps included:

* timestamp alignment across multiple datasets;
* validation of interval completeness;
* missing-value and consistency checks;
* integration of solar, wind and hydro dispatch;
* creation of time-of-day, day-type and seasonal variables;
* calculation of net demand;
* construction of market-stress indicators.

<!-- ADD SCREENSHOT / DATA-PREPARATION VISUAL HERE -->

<!--
![Data preparation workflow](outputs/your_image_name.png)
-->

---

## Scenario Demand Modelling

Annual data-centre electricity projections were con
