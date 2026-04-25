# House Price Prediction — Linear Regression

## The Problem

I built this project to answer a simple business question: can an estate agent in Suffolk, East Anglia estimate a house price quickly using house size alone? The goal was to create a fast, explainable baseline model that could support pricing conversations with clients.

## The Dataset

The dataset contains 200 houses from East Anglia, UK, with just 2 columns: house size (sq ft) and house price (GBP). This was a very clean dataset, so the focus was not on heavy cleaning but on understanding the relationship between size and price.

## Approach

I used Linear Regression with one feature: house size. I trained the model to learn how much price changes as size increases, then evaluated it using R², MAE, and RMSE so I could measure both fit and prediction error in real money terms.

I chose linear regression deliberately, an estate agent needs to tell a client "each extra square foot adds roughly £165 to the price." That clear, explainable relationship matters more than squeezing out extra accuracy with a complex model like XGBoost.

### Steps

1. Loaded and explored 200 property records
2. Quick EDA: data types, missing values, duplicates, distributions
3. Deep EDA: histogram, scatter plot, and grouped bar chart to confirm a linear pattern
4. Train/test split (80/20)
5. Trained a Linear Regression model (no scaling — to preserve coefficient interpretability)
6. Evaluated on unseen test data
7. Visualised predictions vs actuals

## Results

| Metric | Value |
|--------|-------|
| R² | 0.96 |
| MAE | £16,864 |
| RMSE | £22,272 |
| Coefficient | £165 per sq ft |
| Intercept | ~£45,000 |

The model performed strongly, house size alone explained 96% of the variation in price. The coefficient means each extra square foot increases the predicted price by roughly £165. The MAE of £16,864 represents about 4.7% of the average house price, giving a practical sense of prediction accuracy.

**The formula:** `Price = £45,000 + £165 × Size (sq ft)`

## Key Insight

A simple model is not an old model, it's the right model for the right problem. For this project, house size alone gave a strong baseline, and linear regression made the result fully explainable. The remaining 4% error shows that other features like location, condition, and number of rooms would likely improve the model further.

In regulated or client-facing contexts (like Deloitte's Risk Advisory or a real estate valuation), interpretability often matters more than raw accuracy. A CFO or estate agent needs "each square foot adds £165" — not a prediction from 500 decision trees they can't explain.

## Tech Stack

- Python 3
- pandas
- scikit-learn
- matplotlib / seaborn

## Project Structure

```
house-price-prediction/
├── house-price-prediction.ipynb   # Full notebook
├── README.md                      # This file
└── house_price_regression_test_plot.png  # Final result plot
```
