# maize_price_forecasting_in_kenya
This project builds a multi-horizon time-series forecasting model to predict weekly wholesale prices of dry maize in Kenya's counties of Nairobi, Kirinyaga, and Uasin Gishu.

Using historical transaction data, the model forecasts prices for the next two consecutive weeks.

Data:
The first dataset, collected by agriBORA (2023-2025), is the transaction data between businesses showing the wholesale price of white maize for a given week. Contains the target variable to be forecasted.
The second dataset is from KAMIS(https://kamis.kilimo.go.ke/). It consists of historical wholesale and retail prices for three types of maize (white, yellow, and mixed-traditional) in different markets in Kenya from 2021-2025. Useful for EDA and to get market insights.

Feature Engineering:

The model uses autoregressive time-series features derived from historical prices:

Lag Features

lag_1: price during previoud week

lag_2: price two weeks prior

lag_4: price four weeks prior

Rolling Statistics

rolling_mean_4: 4-week moving average to show trends in prices

rolling_std_4: 4-week standard deviation to show volatility

These features capture short-term momentum, local trends, and market stability.

Two prediction horizons are modelled:

t+1 (1-week ahead) → Week 52

t+2 (2-weeks ahead) → Week 1 (following year)

Model:

Chose Random Forest Regressor because it:
Handles nonlinear relationships well

Performs well on small tabular datasets

Requires minimal hyperparameter tuning

Handles interactions between features

Evaluation:

A time-based split is used to avoid data leakage:

Used a time-based split:

Train: historical data before 2025

Test: data from 2025 onward


Performance is evaluated using:

Mean Absolute Error (MAE)

Root Mean Squared Error (RMSE)

Final output:

Predicted wholesale price of dry white maize in Nairobi, Uasin Gishu and Kirinyaga counties in week 52, 2025 and week 1, 2026
