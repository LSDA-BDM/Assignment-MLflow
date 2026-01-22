# Assignment MLflow (WIP)

## Project Overview
Time-series ML project for forecasting wind power production in Orkney using weather data. You will start with Jupyter-based experimentation with MLflow tracking, model registry, and deployment and develop python scripts you can use for deployment.


- **Data sources**: `data/power.csv` (power generation), `data/weather.csv` (weather forecasts), `data/future.csv` (future forecasts)
- **Primary workflow**: notebook [`exploration.ipynb`](exploration.ipynb) contains complete pipeline from EDA → training → MLflow tracking → model registry → prediction
- **MLflow structure**: 
  - Experiments tracked in `mlruns/` (local file-based tracking)
  - Model artifacts stored in `mlartifacts/` 
  - Model registry for production models (accessed via `models:/{name}/{version}`)

  Follow the instructions in the notebook.
