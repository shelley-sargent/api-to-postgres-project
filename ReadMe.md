<div align="center">
  <!-- Optional: replace with your repo link + add a real image later -->
  <!--
  <a href="https://github.com/shelley-sargent/api-to-postgres-project">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>
  -->

<h3 align="center">Torn Fight Predictor</h3>

  <p align="center">
    A Python ingestion pipeline that pulls attack and player statistics from Torn City's REST API and upserts results into PostgreSQL (Supabase). Designed to run automatically on Raspberry Pi via cron.
    <br />
    <a href="https://github.com/shelley-sargent/api-to-postgres-project/"><strong>Explore the docs »</strong></a>
    <br />
  </p>
</div>

## About The Project

This project implements a repeatable data pipeline using Torn City's REST API:

- Pulls individual attacking records every 6 hours in batches of up to 1,000
- Analyzes the records to find individual attackers and defenders
- Uses rate-limited API calls to pull individual statistics on each participating attacker and defender
- Cleans and normalizes the data (IDs, timestamps, numeric types)
- Loads event data into a Pandas DataFrame for transformation
- Cleans and merges player data with attacking records using explicit column namespacing
- Upserts into PostgreSQL (Supabase)
- Designed to run automatically on a Raspberry Pi using cron

### Project Goal

This pipeline was originally designed as the data foundation for a predictive modeling system.

As more data is aggregated, an unsupervised learning model (K-means clustering) will be applied to the accrued information in an attempt to predict fight outcomes. Early models showed 63% accuracy, more data is currently being collected and chosen statistics being tweaked to try to get this above 70%.

### Architecture
api.py (function providing easy access to various calls within Torn City's Swagger v2.0 REST API)<br />
⬇️ <br />
get_data.py (data extraction and transformation) <br />
⬇️ <br />
db_connect.py (bulk upsert via psycopg2.execute_values) <br />
⬇️ <br />
PostgreSQL (Supabase) <br />
⬆️ <br /> 
cron + run_upload.sh (every 6 hours)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Installation

### Prerequisites

- Python 3.10+ recommended
- A PostgreSQL database (e.g., Supabase)
- API key for your data source
- (Optional) Raspberry Pi / Linux host for scheduled execution

### Installation Steps


<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Built With

* [Python](https://www.python.org/)
* [pandas](https://pandas.pydata.org/)
* [PostgreSQL](https://www.postgresql.org/)
* [psycopg2](https://www.psycopg.org/)
* [Supabase](https://supabase.com/)
* Linux cron

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Getting Started



### Installation

## Road Map
[] Finish writing ReadMe

<p align="right">(<a href="#readme-top">back to top</a>)</p>
