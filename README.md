# NSW Data Centre Demand & Electricity Price Impact Analysis

## Project Overview

This project analyses how future growth in **NSW data-centre electricity demand** could affect wholesale electricity prices and market risk.

The analysis combines **5-minute NSW electricity-market data** from July 2021 to June 2024 with solar, wind and hydro dispatch data. After integrating and validating multiple data sources, the dataset was enriched with temporal, renewable-output and system-stress features to examine the conditions associated with elevated electricity prices.

Future data-centre demand scenarios were then converted into additional continuous MW load and injected into NSW demand. An **XGBoost regression model** was used to compare baseline and scenario prices and estimate the marginal price impact of additional data-centre load.

The analysis evaluates how these impacts vary across:

* demand-growth scenarios;
* seasons;
* hours of day;
* renewable-output conditions;
* system-stress periods;
* upper-tail / high-risk price intervals.

The resulting insights provide a basis for understanding **electricity-market exposure, procurement risk and potential risk-management strategies** for large data-centre loads.

---

## Business Problem

Data centres are large, energy-intensive facilities that operate close to continuously. Unlike many commercial loads, their electricity demand remains relatively stable throughout the day, meaning rapid data-centre expansion can increase the underlying **baseload demand** placed on the electricity system.

For NSW, this raises an important market question:

> **How much additional wholesale electricity-price pressure could future data-centre growth create, and under which market conditions is that impact greatest?**

The challenge is not only to estimate an average price increase. Wholesale electricity prices are highly variable and depend on the interaction between:

* system demand;
* renewable-generation availability;
* time of day;
* seasonal conditions;
* periods of system stress.

A meaningful analysis therefore needs to identify both the **typical price impact** of additional data-centre demand and the **higher-risk intervals** where the market is more sensitive to additional load.

This project addresses that problem by combining market data, renewable-generation data, scenario modelling and predictive analytics to quantify how additional data-centre demand may affect NSW wholesale prices and translate those results into practical market-risk insights.


### Baseline vs Scenario Comparison

The model does **not** compare future prices against FY2025 prices directly.

Instead, it compares two predictions generated from the same historical 5-minute market conditions:

```text
Baseline Predicted Price
= Modelled price using the original historical NSW demand profile

Scenario Predicted Price
= Modelled price after adding future data-centre demand to NSW demand
```

The estimated price impact is then calculated as:

```text
Price Impact
= Scenario Predicted Price − Baseline Predicted Price
```

For example, if a particular historical interval has:

```text
Baseline predicted price = $120/MWh
Scenario predicted price = $138/MWh
```

then:

```text
Price impact = $18/MWh
```

FY2025 is used only as the **reference point for calculating additional data-centre demand**. It is not the baseline price year.

This approach isolates the marginal effect of additional data-centre load by holding the underlying historical market conditions constant and changing only the demand-related scenario inputs.
