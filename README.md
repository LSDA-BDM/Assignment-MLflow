# Forecasting Wind Power Production in Orkney

The Orkney archipelago in the UK generates more than its net electricity needs from renewable energy, primarily wind power. However, wind power production is inherently variable and difficult to predict. Accurate forecasting is critical for grid stability, planning, and efficient energy distribution.

In this assignment, you will design, implement, and serve a **reproducible machine learning pipeline** that predicts wind power generation in Orkney using real-world historical power data and weather forecasts. The emphasis is not on achieving the best possible accuracy, but on demonstrating sound **data engineering, modeling, reproducibility, and deployment practices** across the full machine learning lifecycle.

---

## Workflow

1. In the assignment repository you will find a Jupyter Notebook `exploration.ipynb` with some helper code to get you started. Go through the steps in this notebook to get familiar with the datasets, pipelines, and working with MLflow.
1. Start the development process using the `modelling.py` script. First, make sure that you can run this template script. Then, modify it to run your experiments, solving the tasks below.

---

## Data description

You will work with three datasets:

### Power generation data (`power.csv`)

* **Source:** Scottish and Southern Electricity Networks (SSEN)
* **Granularity:** 1-minute sampling
* **Target variable:** Total renewable power generation (MW)

Key fields:

* `time`: Timestamp of measurement
* `Total`: Renewable power generation (MW)

### Weather forecast data (`weather.csv`)

* **Source:** UK Met Office
* **Granularity:** 3-hour intervals
* Forecasts include a *source time* (forecast creation) and a *target time* (forecasted timestamp)

Key fields:

* `time`: Target time of the forecast
* `Speed`: Wind speed (m/s)
* `Direction`: Wind direction (categorical string, e.g. "NW")
* `Source_time`: Forecast generation time
* `Lead_hours`: Forecast horizon

### Future forecasts (`future.csv`)

* Weather forecasts to be used for generating future power predictions using your model

---


## Task description

You will build a **training and deployment pipeline** that transforms raw data into a forecasting service.
  
  - [ ] Data alignment

  * Load power generation and weather forecast data
  * Align the two data sources temporally (e.g. resampling, joins, or interpolation)
  * Clearly justify your alignment strategy and discuss its implications

  - [ ] Data preprocessing with pipelines

   * Apply a suitable data-splitting strategy for train and test
   * Handle missing values
   * Transform wind direction into a numeric representation (e.g. encoding, radians, vector form)
   * Scale numerical features where appropriate


  - [ ] Model training and evaluation

  * Train at least 2 regression models of your choice
  * Use evaluation metrics appropriate for regression
  * Use the `future.csv` file to generate future predictions (to check that your model works on new data)

  - [ ] Experiment tracking with MLflow
  
  * Log parameters, metrics, and artifacts using MLflow Tracking
  * Organize experiments and runs clearly
  * Use MLflow to compare model variants and select a best model that you will register and serve
  
  - [ ] Model serving
  
  * Save the selected model using the MLflow Model format
  * Serve the model
  * Expose a prediction endpoint that accepts weather inputs and returns power forecasts
    
  - [ ] Reproducibility with MLflow Projects
  
  * Package your training code as an MLProject
  * Specify dependencies using a `requirements.txt` or environment file
  * Ensure the project can be executed from scratch on another machine
  
  - [ ] Reflection
  
  * Mention limitations of your approach and potential improvements
  * Discussion of data window size (e.g. 90 days): trade-offs and impact on accuracy

---

## Deliverables

### Report (PDF)

In the report you briefly describe how you solved the tasks above. For each task:

- explain how you solved it and why you chose a particular approach
- show snippets of your code

Include your results with screen captures from the MLflow UI.

**Maximum length:** 5 pages (excluding figures)

**File name:** `<itu_username>-A1-report.pdf`

**Submission:** on LearnIt

### Code repository

* A Git repository containing all code needed to run the pipeline
* Code must run without errors
* Code must be packaged as MLProject; it should be possible to run it with `mlflow run`
* Include instructions for running training and deployment
* Repository URL must be included in the report

---

## Assessment criteria

Your submission will be evaluated based on:

* Pipeline design and correctness
* Quality of preprocessing, feature engineering, modeling, and evaluation decisions
* Appropriate use of MLflow for tracking and reproducibility
* Clarity and depth of reflection in the report

Model accuracy alone is *not* a grading criterion.
