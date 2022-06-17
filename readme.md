# Forecast Application: [[WebApp link]](https://share.streamlit.io/luke-chugh/forecasting-webapp/main/app.py)

![](https://img.shields.io/badge/python-3.10.4-blueviolet)
![](https://img.shields.io/badge/prophet-1.0.1-orangered)
![](https://img.shields.io/badge/plotly-5.8.0-greenyellow)
![](https://img.shields.io/badge/streamlit-1.9.1-brightgreen)

This WebApp can forecast any kind of time series data using facebook's [prophet](https://facebook.github.io/prophet/) library.

### 1. Load the time series:

Upload a .csv file in form of a timeseries. Even though Prophet requires the date column o be labeled **ds** and the value column as **y** , it is not necessary to pre-proces the file to comply with this rule, since it is taken care of during the upload in the app. 
The dataset can as well contain multiple columns, of which only the chosen one in the selector will be used for the prediction.
After loading data a checkbox will show up to visualize the dataframe, include a statistical description and create a plot of the timeseries. 

![Capture](https://github.com/luke-chugh/Forecasting-WebApp/blob/main/screenshots/loading%20the%20time%20series.png)

### 2. Configure the model settings:

Once the data is loaded, the user can tweak and configure the following parameters:
- **Horizon**: the time in future to forecast. It is expressed in days.
- **Seasonality**: choose beetwen Additive seasonality or Multiplicative seasonality. 
- **Trend Components**: declare which trends you want to discover and propagate:
    * Daily should be selected if loading a dataset with hourly data.

    * Weekly: Prophet will search for trend during days of the week (Monday to Sunday).

    * Monthly: Prophet will search for trends during days of the month (1st to 31st).

    * Yearly: will evaluate trends within months of the year (January to December)

- **Growth model**: choose beetwen linear growth or logistic growth, to specify carrying capacity, for example if there is a maximum acheivable point. The app then allows the user to specify cap and floor of the logistic model.
- **Holidays**: add holidays to the model. Available countries at the moment: Italy, Spain, France, United States, India, Germany and Ukraine.
- **Hyperparameters**: Change the scale of the changepoints or holidays. It impacts the flexibility of the model. 

![Capture](https://github.com/luke-chugh/Forecasting-WebApp/blob/main/screenshots/configure%20the%20model%20settings.png)

### 3. Fit the model and predict future:
- Initialize the model with the settings configured above  (Fit)
- Generate forecast (Predict): will plot forecast with standard Prophet charts
- Show components: shows finding about time components selected in point 2.

![Capture](https://github.com/luke-chugh/Forecasting-WebApp/blob/main/screenshots/fit%20and%20predict.png)

### 4. Evaluate and validate prediction:

- Set the k-fold configuration: specify the initial timeframe to keep as training data, the horizon to predict and recurrency of the prediction as period.
- Calculate the metrics related to the cross-validatio. A dataframe will be generated and a plot of the selected metric will be created.

![Capture](https://github.com/luke-chugh/Forecasting-WebApp/blob/main/screenshots/evaluate%20and%20validate.png)

### 5. Hyperparameter tuning:
Runs the model with all the combinations possible within the matrix of coefficients of scaling. It return the best combination of changepoint ans seasonality prior scale, which can be used to go back above at point 2 and embed in the model and create an optimized forecast.

![Capture](https://github.com/luke-chugh/Forecasting-WebApp/blob/main/screenshots/hyperparameter%20tuning.png)

# Installation:
This project can only be run in Anaconda. To install the required packages and libraries, run the following commands in Anaconda Prompt:
```bash
conda install -c conda-forge prophet
```
```bash
pip install streamlit
```
After this step, open a Anaconda Prompt in the directory containing the files [cloned](https://www.howtogeek.com/451360/how-to-clone-a-github-repository/) from this repository and run the following command:
```bash
streamlit run app.py
```

# Author:
[Luke Chugh](https://www.linkedin.com/in/luke-chugh-2b2043181/)

