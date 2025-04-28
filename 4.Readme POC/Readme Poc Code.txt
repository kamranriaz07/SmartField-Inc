This repository contains a proof-of-concept (PoC) implementation for predictive maintenance using PySpark, Delta Lake, and FastAPI. The notebook is designed to run on Google Colab, which provides an open-source environment for PySpark development.

Prerequisites

A Google account to access Google Colab.

The sample dataset predictive_maintenance.csv uploaded to Colab or accessible via a public URL.

Running on Google Colab

Open the Notebook

Navigate to the Colab link or upload the notebook file (.ipynb).

Upload Dataset

In the left sidebar, go to the Files tab.

Click Upload and select predictive_maintenance.csv.

Execute Cells Sequentially

Cell 1: Installs Java, PySpark, Delta Lake, FastAPI, and Uvicorn.

Cell 2: Configures Spark session with Delta Lake support.

Cell 3: Reads and previews the CSV dataset.

Cell 4: Writes raw data to the Bronze layer and prints row count.

Cell 5: Transforms data into the Silver layer with cleaning, type-casting, partitioning, and schema evolution.

Cell 6: Runs comprehensive data quality checks (row counts, nulls, duplicates, value ranges, percentiles).

Cell 7: Performs feature engineering (time-series and categorical features) and writes features to Delta.

Cell 8: Converts Spark features to a Pandas DataFrame for API serving.

Cell 9: Generates app.py, a FastAPI application with Swagger documentation.

Cell 10: (Optional) Installs and configures ngrok, starts Uvicorn in the background, and prints a public URL for the API.

Access the API

After Cell 10 runs, note the console output for the public URL (e.g., https://abcd1234.ngrok.io).

Open your browser to https://<public_url>/docs to view and interact with the Swagger UI.

Running Locally

If you prefer running on your local machine instead of Colab:

Install Java (OpenJDK 8 or higher).

Clone the Repository:

git clone <repo-url>
cd <repo-directory>

Install Python Dependencies:

pip install pyspark delta-spark fastapi uvicorn

Ensure Dataset Availability:

Place predictive_maintenance.csv in the project root or adjust the path in the notebook.

Run the Colab Notebook Locally:

Convert the notebook to a Python script or run cells manually in an interactive environment.

Start the API:

uvicorn app:app --reload --host 0.0.0.0 --port 8000

Open Swagger UI:

Navigate to http://localhost:8000/docs in your browser.

Notes

Delta Lake format provides ACID transactions and schema enforcement, ideal for Bronze/Silver/Gold medallion architecture.

Feature engineering includes rolling averages (time-series) and categorical extraction (month/day).

FastAPI offers automatic OpenAPI (Swagger) documentation.