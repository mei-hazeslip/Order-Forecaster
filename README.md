# Retail Order Forecasting for Online Grocery Delivery
> **Check out the [interactive project page](https://mei-hazeslip.github.io/order-forecaster.html) for a detailed breakdown and live demo.**

## Project Overview

This project predicts the number of daily customer orders for an online grocery delivery business using historical warehouse-level order data. Accurate order forecasting can help reduce overstock, avoid stockouts, improve delivery planning, and lower operational costs.

The project was inspired by the Rohlik Orders Forecasting Challenge and focuses on building an interpretable machine learning workflow for demand forecasting across multiple warehouses.

## Team

This was a team project completed by:

- Mei (Chien) Hazeslip
- Xuelian Liu
- Tianzhu Qin
- Wenbo Ma
- Terry Lou

## My Role

I served as the team lead and contributed across project planning, feature engineering, modeling, and presentation.

My responsibilities included:

- Led team coordination by scheduling meetings, communicating project goals, dividing workloads, and consolidating individual contributions into a cohesive final project.
- Created the project introduction and helped define the business problem of forecasting online grocery orders.
- Conducted exploratory data analysis on categorical variables, including holiday, warehouse, and calendar-related features.
- Built reusable feature-engineering classes to apply newly created features consistently across the training and testing datasets.
- Applied machine learning models to both the full dataset and clustered warehouse groups, including general models and cluster-specific models.
- Prepared project slides and presented progress during weekly team presentations.

## Business Problem

Online grocery delivery companies need to prepare enough inventory and delivery capacity to meet customer demand. Poor forecasting can lead to:

- Overstock and food waste
- Stockouts and missed sales
- Inefficient staffing and delivery planning
- Higher operational costs
- Lower customer satisfaction

The goal of this project is to predict future order volume as accurately as possible and estimate the potential business value of improved forecasting.

## Dataset

The dataset contains historical order records for multiple warehouses, including:

- Warehouse name
- Date
- Number of orders
- Holiday indicators
- School holiday indicators
- Shop closure indicators
- Other calendar-related information

Only features available at prediction time were used for modeling to avoid data leakage.

## Methods

The workflow includes:

1. Exploratory Data Analysis  
   - Analyzed order trends by year, month, weekday, holiday, and warehouse.
   - Identified seasonal patterns and warehouse-level differences.
   - Examined missing values and feature availability.

2. Feature Engineering  
   - Created calendar-based features such as year, month, weekday, quarter, season, and weekend indicators.
   - Added holiday-related features such as days before/after holidays and school holiday indicators.
   - Applied categorical encoding for warehouse and holiday features.
   - Used cyclic encoding for time-related variables.

3. Warehouse Clustering  
   - Used Dynamic Time Warping similarity to compare order patterns across warehouses.
   - Applied hierarchical clustering to group warehouses with similar demand behavior.
   - Built separate models for different warehouse clusters.

4. Model Development  
   Models tested include:

   - Linear Regression
   - Random Forest
   - XGBoost
   - Gradient Boosting
   - CatBoost
   - LightGBM

5. Model Evaluation  
   Models were evaluated using:

   - RMSE
   - MAPE
   - R² score

## Key Results

The best-performing model was a LightGBM regressor trained on engineered time, holiday, and warehouse-level features.

For one warehouse cluster, the LightGBM model reduced RMSE from 668 orders to 383 orders compared with the Linear Regression benchmark.

This represents:

- 285 fewer order errors by RMSE
- 43% RMSE reduction compared with the benchmark
- Estimated daily cost savings of $14,250
- Estimated annual cost savings of approximately $5 million

The business value estimate assumes an average cost impact of $50 per order error.

## Key Takeaways

- Demand patterns vary significantly across warehouses.
- Time-based and holiday-related features are important for order forecasting.
- Warehouse clustering can help capture different demand behaviors across regions.
- Gradient boosting models, especially LightGBM, performed better than simpler benchmark models.
- Translating RMSE reduction into business cost provides a clearer explanation of model value.

## Tools and Libraries

- Python
- pandas
- NumPy
- Matplotlib
- seaborn
- scikit-learn
- LightGBM
- XGBoost
- CatBoost
- fastdtw
- Jupyter Notebook

## Repository Structure

```text
.
├── order_forecast_MC.ipynb     # Main analysis and modeling notebook
├── README.md                   # Project summary

