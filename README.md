# NSW Data-Centre Electricity Demand and Price Impact Analysis

## Project Overview
This project analyses how future data-centre demand growth could affect NSW wholesale electricity prices and procurement risk. It combines demand-growth scenario modelling, machine-learning-based price-impact modelling, data-centre load profiling, and electricity procurement strategy comparison.

## Business Problem
NSW is expected to experience rapid data-centre growth. Since data centres operate as large, near-continuous electricity loads, this growth may increase wholesale electricity prices and create procurement risk for operators, retailers, and large electricity users.

## Objectives
- Estimate NSW data-centre electricity demand under Slower Growth, Step Change, and Accelerated Transition scenarios.
- Convert annual demand projections into additional continuous MW load.
- Model the price impact of additional data-centre demand on NSW wholesale prices.
- Build a realistic demand profile for a 50 MW data centre.
- Compare procurement strategies including spot exposure, futures hedging, battery storage, and solar plus battery.

## Data
The analysis uses historical NSW electricity market data from July 2021 to June 2024, including:
- NSW wholesale price
- NSW demand
- Solar dispatch
- Wind dispatch
- Hydro dispatch
- Time and seasonal variables
- System-stress indicators

## Methodology

### Task 1: Demand Growth Scenarios
Annual data-centre electricity demand was projected under three scenarios and converted into additional MW using:

Average MW = Annual GWh × 1,000 / 8,760

### Task 2: Price Impact Modelling
An XGBoost regression model was used to estimate NSW wholesale electricity prices. Additional data-centre MW was injected into historical demand, and price impact was calculated as:

Price Impact = Scenario Predicted Price - Baseline Predicted Price

The selected model used a p99 capped price target to reduce distortion from rare extreme price spikes.

### Task 3: Data-Centre Load Profile
A representative 50 MW data-centre profile was constructed using PUE, load factor, daily operating pattern, weekly profile, and seasonal adjustments.

### Task 4: Procurement Strategy
Four electricity procurement strategies were compared:
- Wholesale spot exposure
- Futures hedge
- Battery storage
- Solar plus battery

Strategies were assessed using cost, volatility, CFaR, NPV, payback, emissions, and practicality.

## Key Findings

* NSW data-centre demand is projected to become a material source of continuous electricity load. By FY2030, additional demand reaches approximately **263 MW under Slower Growth**, **639 MW under Step Change**, and **1,221 MW under Accelerated Transition**, creating a sustained increase in NSW grid demand rather than a short-term peak-only effect.

* This additional baseload demand increases NSW wholesale price pressure. Under the central Step Change FY2030 case, the model estimates a mean price impact of around **$19/MWh**, while the Upper-tail price impact (P95) impact reaches about **$49/MWh**. This shows that the risk is not only the average price increase, but also the much larger exposure during high-impact intervals.

* Price impacts are uneven across market conditions. Winter produces the highest seasonal impacts, while 10:00–14:00 shows the largest marginal price impact even though evening remains the highest baseline-price period. Low-renewable output becomes most important when it overlaps with high demand and system stress.

* The 50 MW data-centre profile converts these market impacts into a practical procurement problem. Because the facility operates as a large, near-continuous load, even moderate wholesale price increases translate into material cost exposure across the year.

* Procurement exposure rises sharply with demand-growth intensity. By FY2030, estimated additional wholesale cost reaches around **$323 million under Step Change** and **over $1.1 billion under Accelerated Transition**, showing that higher data-centre load and upper-tail price impacts can materially affect electricity purchasing risk.

* Strategy comparison shows that futures hedging is the strongest default cost-and-risk management option. In the central case, hedging reduces the mean five-year cost from about **$290 million under spot exposure** to about **$193 million**, while also reducing volatility and extreme-price exposure.

* Battery storage and solar-plus-battery provide useful flexibility, especially for reducing grid purchases during expensive or high-risk periods. However, standalone battery does not outperform hedging on cost, while solar-plus-battery is most attractive where emissions reduction and long-term decarbonisation are priorities.

* Overall, the analysis shows that data-centre electricity growth creates both **broad baseload procurement exposure** and **sharp upper-tail price risk**. The recommended response is a layered strategy: use futures hedging for core cost protection, while considering battery or solar-plus-battery where operational flexibility, emissions reduction, or long-term resilience are priorities.


## Tools and Technologies
- Python
- Pandas
- Nemosis
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- Seaborn
- Excel
