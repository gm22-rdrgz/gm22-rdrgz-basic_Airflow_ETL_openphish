## Project Title
**Basic ETL with Airflow on OpenPhish**

Created: 09/17/2025

## Description
This project demonstrates a basic ETL pipeline using Apache Airflow on the 
OpenPhish free dataset of malicious sites that may contain bugs and malware.

The pipeline extracts raw phishing domain feeds from OpenPhish into a text file, and 
transforms the data into a csv using pandas.

## Features
- Built with Airflow DAGs
- Uses Python and pandas for data processing
- Extracts raw data from OpenPhish and converts it into a structured csv format
- Runs on a daily schedule with Airflow

## Libraries
- `airflow import DAG`
- `airflow.operators.python import PythonOperator`
- `datetime import datetime`
- `requests`
- `pandas as pd`

## Notes
This project was relatively simple, but setting up dependencies was a bit confusing. 
I originally planned to use `Docker`, but for this basic project I decided to run Airflow locally.

**CAUTION**
This project requires a WSL (Windows Subsystem for Linux) environment if you are running on Windows:
- Airflow may not work properly on a native Windows Command Prompt or PowerShell.
- Ensure that WSL is installed and properly configured before running Airflow.
- Make sure your IDE or terminal is set to the WSL environment when working with the project.

## To run Airflow:
Below are the steps to run the project:

**Create and activate a virtual environment (To be safe)**

`python3 -m venv venv`

`source venv/bin/activate    # Mac/Linux`

`venv\Scripts\activate       # Windows`

**Install Airflow and dependencies**
(replace version with one that supports your Python version)

`pip install "apache-airflow==2.6.3" --constraint \
https://raw.githubusercontent.com/apache/airflow/constraints-2.6.3/constraints-3.8.txt`

`pip install requests pandas`

**Initialize Airflow database**

`airflow db init`

**Create an Airflow user (username, email, password)**

Create an admin user so you can log into the web UI. Replace the sample values (username, email, password) 
with your own values:

Example: 


airflow users create \

  --username myadmin \
  
  --firstname Admin \
  
  --lastname User \
  
  --role Admin \
  
  --email admin@example.com \
  
  --password password

**Start Airflow services**

In one terminal:

`airflow webserver --port 8080`

In another terminal:

`airflow scheduler`

**Access the Airflow UI**

Open `http://localhost:8080` in your browser.

In the Airflow UI:
- Log in your credentials
- enable and trigger the DAG.

## Sources
[Airflow DAG: Coding your first DAG for Beginners](https://www.youtube.com/watch?v=IH1-0hwFZRQ)

[Airflow: Quick Start](https://airflow.apache.org/docs/apache-airflow/stable/start.html)

[Running Airflow locally](https://airflow.apache.org/docs/apache-airflow/2.3.0/start/local.html)
