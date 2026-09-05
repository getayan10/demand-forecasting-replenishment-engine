# Demand Forecasting & Automated Replenishment Engine

## Project Overview
This project provides an automated Python engine designed for e-commerce supply chain operations. It processes raw transactional sales records, analyzes daily demand volatility, calculates dynamic **Safety Stock** and **Reorder Points (ROP)** based on supplier lead times, and outputs optimized **Purchase Order (PO) quantities** to protect margins, maximize in-stock rates, and increase inventory turns.

## Supply Chain & Mathematical Methodology

1. **Daily Demand Volatility & Distribution:**
   Aggregates transaction logs into daily SKU-level demand to establish baseline daily average sales ($\mu$) and standard deviation ($\sigma$):
   $$\mu_{daily} = \frac{\sum Units}{Days}, \quad \sigma_{daily} = \sqrt{\frac{\sum (Units - \mu_{daily})^2}{N - 1}}$$

2. **Dynamic Safety Stock Calculation:**
   Factors in sales variability and supplier lead times ($L$) at a 95% target service level ($Z = 1.65$) to guard against unexpected demand surges and stockouts:
   $$Safety\ Stock = Z \times \sigma_{daily} \times \sqrt{L}$$

3. **Reorder Point (ROP) Thresholds:**
   Establishes the exact inventory level that triggers a replenishment order before stockouts occur:
   $$ROP = (\mu_{daily} \times L) + Safety\ Stock$$

4. **Automated Purchase Order (PO) Quantity:**
   Computes required replenishment orders targeting a standard 45-day inventory cover window:
   $$Suggested\ PO\ Qty = (\mu_{daily} \times Target\ Days\ Cover) - Safety\ Stock$$

   ## Interactive Visualizations
View the live interactive Tableau dashboard.

## Repository Structure
```text
├── demand_forecasting_replenishment_engine.ipynb  # Core Python analytical pipeline
├── kaggle_inventory_replenishment_plan.csv         # Generated PO replenishment plan
└── README.md                                       # Documentation & supply chain model overview
