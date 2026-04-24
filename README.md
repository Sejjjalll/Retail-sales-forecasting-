# Retail sales forecasting (hierarchical + reconciliation)
<div align="center">
<img src="https://raw.githubusercontent.com/Nixtla/neuralforecast/main/nbs/imgs_indx/logo_mid.png"/>
<h1 align="center">Statistical ⚡️ Forecast</h1>
<h3 align="center">Lightning fast forecasting with statistical and econometric models</h3>

[![CI](https://github.com/Nixtla/statsforecast/actions/workflows/ci.yaml/badge.svg?branch=main)](https://github.com/Nixtla/statsforecast/actions/workflows/ci.yaml)
[![Python](https://img.shields.io/pypi/pyversions/statsforecast)](https://pypi.org/project/statsforecast/)
[![PyPi](https://img.shields.io/pypi/v/statsforecast?color=blue)](https://pypi.org/project/statsforecast/)
[![conda-nixtla](https://img.shields.io/conda/vn/conda-forge/statsforecast?color=seagreen&label=conda)](https://anaconda.org/conda-forge/statsforecast)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://github.com/Nixtla/statsforecast/blob/main/LICENSE)
[![docs](https://github.com/Nixtla/statsforecast/actions/workflows/build-docs.yaml/badge.svg)](https://github.com/Nixtla/statsforecast/actions/workflows/build-docs.yaml)
[![Downloads](https://pepy.tech/badge/statsforecast)](https://pepy.tech/project/statsforecast)

**StatsForecast** offers a collection of widely used univariate time series forecasting models, including automatic `ARIMA`, `ETS`, `CES`, and `Theta` modeling optimized for high performance. It also includes a large battery of benchmarking models.
</div>

## Installation

You can install `StatsForecast` with:

```python
pip install statsforecast
```

or

```python
conda install -c conda-forge statsforecast
```

Vist our [Installation Guide](https://nixtlaverse.nixtla.io/statsforecast/docs/getting-started/installation.html) for further instructions.

## Quick Start

**Minimal Example**

```python
from statsforecast import StatsForecast
from statsforecast.models import AutoARIMA
from statsforecast.utils import AirPassengersDF

df = AirPassengersDF
sf = StatsForecast(
    models=[AutoARIMA(season_length=12)],
    freq='ME',
)
sf.fit(df)
sf.predict(h=12, level=[95])
```

**Get Started [quick guide](https://nixtlaverse.nixtla.io/statsforecast/docs/getting-started/getting_started_short.html)**

**Follow this [end-to-end walkthrough](https://nixtlaverse.nixtla.io/statsforecast/docs/getting-started/getting_started_complete.html) for best practices.**

## Why?

Current Python alternatives for statistical models are slow, inaccurate and don't scale well. So we created a library that can be used to forecast in production environments or as benchmarks.  `StatsForecast` includes an extensive battery of models that can efficiently fit millions of time series.

## Features

* Fastest and most accurate implementations of `AutoARIMA`, `AutoETS`, `AutoCES`, `MSTL` and `Theta` in Python.
* Out-of-the-box compatibility with Spark, Dask, and Ray.
* Probabilistic Forecasting and Confidence Intervals.
* Support for exogenous Variables and static covariates.
* Anomaly Detection.
* Familiar sklearn syntax: `.fit` and `.predict`.

## Highlights

* Inclusion of `exogenous variables` and `prediction intervals` for ARIMA.
* 20x [faster](https://github.com/Nixtla/statsforecast/tree/main/experiments/arima) than `pmdarima`.
* 1.5x faster than `R`.
* 500x faster than `Prophet`.
* 4x [faster](https://github.com/Nixtla/statsforecast/tree/main/experiments/ets) than `statsmodels`.
* 1,000,000 series in [30 min](https://github.com/Nixtla/statsforecast/tree/main/experiments/ray) with [ray](https://github.com/ray-project/ray).
* Replace FB-Prophet in two lines of code and gain speed and accuracy. Check the experiments [here](https://github.com/Nixtla/statsforecast/tree/main/experiments/arima_prophet_adapter).
* Fit 10 benchmark models on **1,000,000** series in [under **5 min**](https://github.com/Nixtla/statsforecast/tree/main/experiments/benchmarks_at_scale/).

Missing something? Please open an issue or write us in [![Slack](https://img.shields.io/badge/Slack-4A154B?&logo=slack&logoColor=white)](https://join.slack.com/t/nixtlaworkspace/shared_invite/zt-135dssye9-fWTzMpv2WBthq8NK0Yvu6A)

## Examples and Guides

📚 [End to End Walkthrough](https://nixtlaverse.nixtla.io/statsforecast/docs/getting-started/getting_started_complete.html): Model training, evaluation and selection for multiple time series

🔎 [Anomaly Detection](https://nixtlaverse.nixtla.io/statsforecast/docs/tutorials/anomalydetection.html): detect anomalies for time series using in-sample prediction intervals.

👩‍🔬 [Cross Validation](https://nixtlaverse.nixtla.io/statsforecast/docs/tutorials/crossvalidation.html): robust model’s performance evaluation.

❄️ [Multiple Seasonalities](https://nixtlaverse.nixtla.io/statsforecast/docs/tutorials/multipleseasonalities.html): how to forecast data with multiple seasonalities using an MSTL.

🔌 [Predict Demand Peaks](https://nixtlaverse.nixtla.io/statsforecast/docs/tutorials/electricitypeakforecasting.html): electricity load forecasting for detecting daily peaks and reducing electric bills.

📈 [Intermittent Demand](https://nixtlaverse.nixtla.io/statsforecast/docs/tutorials/intermittentdata.html): forecast series with very few non-zero observations.

🌡️ [Exogenous Regressors](https://nixtlaverse.nixtla.io/statsforecast/docs/how-to-guides/exogenous.html): like weather or prices

## Models

### Automatic Forecasting

Automatic forecasting tools search for the best parameters and select the best possible model for a group of time series. These tools are useful for large collections of univariate time series.

|Model | Point Forecast | Probabilistic Forecast | Insample fitted values | Probabilistic fitted values |Exogenous features|
|:------|:-------------:|:----------------------:|:---------------------:|:----------------------------:|:----------------:|
|[AutoARIMA](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#autoarima)|✅|✅|✅|✅|✅|
|[AutoETS](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#autoets)|✅|✅|✅|✅||
|[AutoCES](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#autoces)|✅|✅|✅|✅||
|[AutoTheta](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#autotheta)|✅|✅|✅|✅||
|[AutoMFLES](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#automfles)|✅|✅|✅|✅|✅|
|[AutoTBATS](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#autotbats)|✅|✅|✅|✅||

### ARIMA Family

These models exploit the existing autocorrelations in the time series.

|Model | Point Forecast | Probabilistic Forecast | Insample fitted values | Probabilistic fitted values |Exogenous features|
|:------|:-------------:|:----------------------:|:---------------------:|:----------------------------:|:----------------:|
|[ARIMA](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#arima)|✅|✅|✅|✅|✅|
|[AutoRegressive](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#autoregressive)|✅|✅|✅|✅|✅|

### Theta Family

Fit two theta lines to a deseasonalized time series, using different techniques to obtain and combine the two theta lines to produce the final forecasts.

|Model | Point Forecast | Probabilistic Forecast | Insample fitted values | Probabilistic fitted values |Exogenous features|
|:------|:-------------:|:----------------------:|:---------------------:|:----------------------------:|:----------------:|
|[Theta](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#theta)|✅|✅|✅|✅|✅|
|[OptimizedTheta](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#optimizedtheta)|✅|✅|✅|✅||
|[DynamicTheta](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#dynamictheta)|✅|✅|✅|✅||
|[DynamicOptimizedTheta](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#dynamicoptimizedtheta)|✅|✅|✅|✅||

### Multiple Seasonalities

Suited for signals with more than one clear seasonality. Useful for low-frequency data like electricity and logs.

|Model | Point Forecast | Probabilistic Forecast | Insample fitted values | Probabilistic fitted values |Exogenous features|
|:------|:-------------:|:----------------------:|:---------------------:|:----------------------------:|:----------------:|
|[MSTL](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#mstl)|✅|✅|✅|✅|If trend forecaster supports|
|[MFLES](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#mfles)|✅|✅|✅|✅|✅|
|[TBATS](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#tbats)|✅|✅|✅|✅||

### GARCH and ARCH Models

Suited for modeling time series that exhibit non-constant volatility over time. The ARCH model is a particular case of GARCH.

|Model | Point Forecast | Probabilistic Forecast | Insample fitted values | Probabilistic fitted values |Exogenous features|
|:------|:-------------:|:----------------------:|:---------------------:|:----------------------------:|:----------------:|
|[GARCH](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#garch)|✅|✅|✅|✅||
|[ARCH](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#arch)|✅|✅|✅|✅||

### Baseline Models

Classical models for establishing baseline.

|Model | Point Forecast | Probabilistic Forecast | Insample fitted values | Probabilistic fitted values |Exogenous features|
|:------|:-------------:|:----------------------:|:---------------------:|:----------------------------:|:----------------:|
|[HistoricAverage](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#historicaverage)|✅|✅|✅|✅||
|[Naive](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#naive)|✅|✅|✅|✅||
|[RandomWalkWithDrift](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#randomwalkwithdrift)|✅|✅|✅|✅||
|[SeasonalNaive](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#seasonalnaive)|✅|✅|✅|✅||
|[WindowAverage](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#windowaverage)|✅|||||
|[SeasonalWindowAverage](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#seasonalwindowaverage)|✅|||||

### Exponential Smoothing

Uses a weighted average of all past observations where the weights decrease exponentially into the past. Suitable for data with clear trend and/or seasonality. Use the `SimpleExponential` family for data with no clear trend or seasonality.

|Model | Point Forecast | Probabilistic Forecast | Insample fitted values | Probabilistic fitted values |Exogenous features|
|:------|:-------------:|:----------------------:|:---------------------:|:----------------------------:|:----------------:|
|[SimpleExponentialSmoothing](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#simpleexponentialsmoothing)|✅||✅|||
|[SimpleExponentialSmoothingOptimized](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#simpleexponentialsmoothingoptimized)|✅||✅|||
|[SeasonalExponentialSmoothing](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#seasonalexponentialsmoothing)|✅||✅|||
|[SeasonalExponentialSmoothingOptimized](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#seasonalexponentialsmoothingoptimized)|✅||✅|||
|[Holt](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#holt)|✅|✅|✅|✅||
|[HoltWinters](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#holtwinters)|✅|✅|✅|✅||

### Sparse or Inttermitent

Suited for series with very few non-zero observations

|Model | Point Forecast | Probabilistic Forecast | Insample fitted values | Probabilistic fitted values |Exogenous features|
|:------|:-------------:|:----------------------:|:---------------------:|:----------------------------:|:----------------:|
|[ADIDA](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#adida)|✅||✅|✅||
|[CrostonClassic](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#crostonclassic)|✅||✅|✅||
|[CrostonOptimized](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#crostonoptimized)|✅||✅|✅||
|[CrostonSBA](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#crostonsba)|✅||✅|✅||
|[IMAPA](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#imapa)|✅||✅|✅||                                                                                
|[TSB](https://nixtlaverse.nixtla.io/statsforecast/src/core/models.html#tsb)|✅||✅|✅||

