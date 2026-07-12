# Global Weather Trend Forecasting

## What this is
I picked up the Global Weather Repository dataset from Kaggle and used it to dig into
recent weather trends and build a basic forecasting model for temperature. This covers
cleaning up the raw data, exploring it visually, and then forecasting where temperatures
are headed using time series methods.

## Dataset
Grabbed from Kaggle here: https://www.kaggle.com/datasets/henryshan/globalweatherrepository

It's not included in this repo (it's a bit large and Kaggle asks you to download it
directly), so you'll need to pull it yourself and drop it into `data/GlobalWeatherRepository.csv`.

## Running it yourself

```bash
git clone https://github.com/<your-username>/weather-trend-forecasting.git
cd weather-trend-forecasting

python -m venv venv
source venv/bin/activate      # venv\Scripts\activate on Windows

pip install -r requirements.txt
```

Then download the dataset from the Kaggle link above and save it as
`data/GlobalWeatherRepository.csv`, and open up `notebooks/analysis.ipynb` in Jupyter
or VS Code and run it top to bottom.

## How I approached it

**Cleaning the data** — checked for missing values and filled them in (median for
numeric columns, most common value for categorical ones), then went through the key
weather columns and capped extreme outliers using the IQR method so a handful of bad
readings wouldn't throw off the analysis. Also converted the `last_updated` column
into an actual datetime so I could work with it as a time series.

**Exploring the data** — looked at how temperature, precipitation, humidity, and a
few other variables are distributed, checked which features correlate with each
other, and plotted how temperature and precipitation move over time. Also compared
average temperatures across countries.

**Forecasting** — resampled the data into a daily average temperature series, split
it into train/test, and fit an ARIMA model. Evaluated it using MAE, RMSE, and MAPE
so I had a concrete sense of how far off the forecasts were, not just a chart that
looks reasonable.

## What I found
<img width="1006" height="718" alt="image" src="https://github.com/user-attachments/assets/d5d20bec-0151-4460-afc4-a5770278c812" />
<img width="759" height="609" alt="image" src="https://github.com/user-attachments/assets/7a79137a-756e-42e0-9413-af01cc70e341" />
<img width="836" height="397" alt="image" src="https://github.com/user-attachments/assets/a8162440-9d73-439f-aecf-963e8c040071" />
<img width="847" height="394" alt="image" src="https://github.com/user-attachments/assets/971956b8-ee9f-44a9-9df9-95a7494d2632" />
<img width="800" height="401" alt="image" src="https://github.com/user-attachments/assets/99665d60-7300-433d-b71b-ae85e65ad84c" />
<img width="827" height="437" alt="image" src="https://github.com/user-attachments/assets/1df31a9a-23cb-45e1-baef-1444c45c4c10" />
<img width="828" height="439" alt="image" src="https://github.com/user-attachments/assets/cd93be7d-542b-4bd6-b6e2-1c15b9924c6f" />

