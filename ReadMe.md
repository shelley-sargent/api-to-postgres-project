<div align="center">
  <!-- Optional: replace with your repo link + add a real image later -->
  <!--
  <a href="https://github.com/shelley-sargent/api-to-postgres-project">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>
  -->

<h3 align="center">Automated API → PostgreSQL Data Pipeline</h3>

  <p align="center">
    A Python ingestion pipeline that pulls event and individual statistical records from a REST API and upserts results into PostgreSQL (Supabase). Designed to run automatically on Raspberry Pi via cron.
    <br />
    <a href="https://github.com/shelley-sargent/api-to-postgres-project/"><strong>Explore the docs »</strong></a>
    <br />
  </p>
</div>

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

## About The Project

This project implements a repeatable data pipeline:

- Pulls structured event records from a REST API
- Normalizes and cleans fields (IDs, timestamps, numeric types)
- Loads event data into a Pandas DataFrame for transformation
- Retrieves participant-level statistics using rate-limited API calls
- Cleans and merges statistical data with event records using explicit column namespacing
- Upserts into PostgreSQL (Supabase)
- Uses null-safe updates (`COALESCE`) to support partial enrichment runs
- Designed to run automatically on a Raspberry Pi using cron

### Project Goal

This pipeline was originally designed as the data foundation for a predictive modeling system.

As more data is aggregated, an unsupervised learning model (K-means clustering) will be applied to participant statistical profiles and historical outcomes to identify performance-based groupings and patterns.data

The goal is to use these cluseters as inputs for a predictive model capable of estimating conflict outcomes.

### Architecture
REST API
↓
get_data.py (extract / transform / enrich)
↓
db_connect.py (bulk upsert via psycopg2.execute_values)
↓
PostgreSQL (Supabase)
↑
cron + run_upload.sh (every 6 hours)

> Data source note: This repo is designed for the Torn City REST API.

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

### Prerequisites

- Python 3.10+ recommended
- A PostgreSQL database (e.g., Supabase)
- API key for your data source
- (Optional) Raspberry Pi / Linux host for scheduled execution

### Installation

More instructions in progress

<p align="right">(<a href="#readme-top">back to top</a>)</p>
