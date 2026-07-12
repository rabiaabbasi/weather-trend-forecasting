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

## What's in the repo
weather-trend-forecasting/
├── data/                       # dataset lives here locally (not tracked in git)
├── notebooks/
│   └── analysis.ipynb          # all the actual analysis
├── requirements.txt
└── README.md

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
- [Add your actual findings once you've run the notebook — e.g. which two variables
  turned out to be most correlated, which country/region ran hottest, how accurate
  the forecast ended up being, anything that surprised you]
