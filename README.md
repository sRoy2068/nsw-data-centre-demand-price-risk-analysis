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
- Under Step Change FY2030, additional data-centre demand reaches approximately 639 MW.
- Mean price impact reaches around $19/MWh under Step Change FY2030.
- Upper-tail impacts are much larger, with P95 impact around $49/MWh.
- Winter shows the highest seasonal price impact.
- Evening has the highest baseline price, but 10:00–14:00 shows the largest marginal impact.
- Futures hedging provides the strongest cost and risk reduction.
- Solar plus battery is most attractive for emissions reduction but requires high upfront capital.

## Tools and Technologies
- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- Excel
