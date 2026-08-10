# Airline Revenue Management using Machine Learning and Mathematical Optimization

## Overview

This project presents an end-to-end airline revenue management system that combines machine learning and mathematical optimization to determine optimal ticket prices for different fare classes across multiple booking stages.

The workflow starts by forecasting passenger demand using supervised machine learning models trained separately for Economy, Premium, and Business cabins. The predicted demand is then used to estimate price elasticity by evaluating demand over a range of ticket prices. Finally, a mathematical optimization model built with Pyomo and solved using Gurobi selects the optimal prices that maximize expected revenue while satisfying aircraft seat capacity constraints.

The project demonstrates how predictive analytics and operations research can be integrated into a practical pricing decision support system similar to those used in the airline industry.

---

## Business Problem

Airlines continuously adjust ticket prices as the departure date approaches. Setting prices too low may fill seats quickly but reduce revenue, while setting prices too high may leave seats unsold.

The objective of this project is to develop a decision support system capable of:

- Forecasting passenger demand
- Estimating price elasticity
- Optimizing ticket prices
- Maximizing expected revenue
- Respecting aircraft capacity constraints

---

## Project Workflow

```
Historical Flight Data
          │
          ▼
Demand Forecasting Models
(Economy / Premium / Business)
          │
          ▼
Demand Prediction
for Candidate Prices
          │
          ▼
Price Elasticity Analysis
          │
          ▼
Revenue Optimization
(Pyomo + Gurobi)
          │
          ▼
Optimal Ticket Prices
```

---

## Repository Structure

```
.
├── data/
│   ├── table1_historical.csv
│   ├── table2_current.csv
│   ├── Expected_Revenue_Economy.csv
│   ├── Expected_Revenue_Premium.csv
│   └── Expected_Revenue_Business.csv
│
├── models/
│   ├── economy_model.joblib
│   ├── premium_model.joblib
│   └── business_model.joblib
│
├── notebooks/
│   ├── 1_Demand_Forecasting_Economy.ipynb
│   ├── 1_Demand_Forecasting_Premium.ipynb
│   ├── 1_Demand_Forecasting_Business.ipynb
│   ├── 2_Price_Elasticity_Economy.ipynb
│   ├── 2_Price_Elasticity_Premium.ipynb
│   ├── 2_Price_Elasticity_Business.ipynb
│   └── 3_Optimization.ipynb
│
└── README.md
```

---

## Dataset

The historical dataset contains synthetic airline booking records representing three fare classes and three booking stages.

### Main Features

- Flight information
- Route characteristics
- Fare class
- Booking stage
- Seasonal variables
- Fuel price
- Competitor price
- Weather score
- Ticket price
- Passenger demand (target variable)

---

## Machine Learning

Three independent demand forecasting models were developed:

| Model | Target |
|--------|---------|
| Economy | Economy Demand |
| Premium | Premium Demand |
| Business | Business Demand |

The models predict expected passenger demand based on:

- Ticket price
- Competitor price
- Booking stage
- Route popularity
- Seasonality
- Fuel price
- Weather
- Economic conditions

The trained models are saved as Joblib files and later used during price optimization.

---

## Price Elasticity Analysis

For each fare class:

1. Candidate ticket prices are generated.
2. The trained demand model predicts demand for each price.
3. Expected revenue is calculated.

Expected Revenue = Price × Predicted Demand

The resulting demand and revenue curves represent the estimated price elasticity for each fare class and booking stage.

---

## Revenue Optimization

The optimization model is formulated using **Pyomo** and solved with **Gurobi**.

### Decision Variables

- Ticket price for each fare class
- Ticket price for each booking stage

### Objective

Maximize total expected revenue.

### Constraints

- Economy cabin capacity
- Premium cabin capacity
- Business cabin capacity
- One pricing decision per fare class and booking stage

---

## Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- CatBoost
- Joblib
- Matplotlib
- Pyomo
- Gurobi

---

## Results

The optimization model produces:

- Optimal ticket prices
- Expected passenger demand
- Expected revenue
- Cabin load factors

while satisfying all seat capacity constraints.

---

