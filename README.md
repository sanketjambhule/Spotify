# Spotify

Spotify Advanced EDA using SQL (BigQuery)

📊 Dataset: [Spotify Dataset (Kaggle)](https://www.kaggle.com/datasets/sanjanchaudhari/spotify-dataset)


Overview

This project focuses on performing Exploratory Data Analysis (EDA) on a Spotify dataset using Google BigQuery and SQL.
The dataset contains various attributes related to tracks, albums, artists, and audio features.

The project demonstrates real-world analytical SQL skills, including:

Data exploration

Aggregations

Window functions

Common Table Expressions (CTEs)

Performance-aware querying in BigQuery

The primary goal is to derive meaningful insights from music data while practicing advanced SQL concepts in a cloud data warehouse environment.

Dataset Description

The dataset includes the following attributes:

artist – Name of the artist

track – Track name

album – Album name

album_type – Single or album

danceability, energy, loudness, tempo – Audio features

views, likes, comments – Engagement metrics

licensed, official_video – Boolean indicators

stream – Streaming count

most_played_on – Platform information

BigQuery Table Schema

The dataset was loaded into Google BigQuery using the following schema:

CREATE OR REPLACE TABLE `project_id.dataset_id.spotify` (
  artist STRING,
  track STRING,
  album STRING,
  album_type STRING,
  danceability FLOAT64,
  energy FLOAT64,
  loudness FLOAT64,
  speechiness FLOAT64,
  acousticness FLOAT64,
  instrumentalness FLOAT64,
  liveness FLOAT64,
  valence FLOAT64,
  tempo FLOAT64,
  duration_min FLOAT64,
  title STRING,
  channel STRING,
  views FLOAT64,
  likes INT64,
  comments INT64,
  licensed BOOL,
  official_video BOOL,
  stream INT64,
  energy_liveness FLOAT64,
  most_played_on STRING
);

Project Workflow
1. Data Exploration

Initial exploration was carried out to understand:

Data distribution

Missing or inconsistent values

Audio feature ranges

Popularity and engagement metrics

2. Querying the Data

SQL queries were written and categorized into Easy, Medium, and Advanced levels to progressively analyze the dataset.

Easy Queries

Basic filtering and selection

Simple aggregations using COUNT, SUM, AVG

Medium Queries

Group-wise analysis

Ranking tracks based on popularity

Album-level and artist-level aggregations

Advanced Queries

Window functions (RANK, ROW_NUMBER, LAG)

Common Table Expressions (WITH)

Analytical comparisons and trend analysis

Practice Questions
Easy Level

Retrieve tracks with more than 1 billion streams

List albums along with their respective artists

Total comments for tracks where licensed = TRUE

Tracks belonging to album type single

Count total tracks by each artist

Medium Level

Average danceability per album

Top 5 tracks with highest energy

Tracks with official videos along with views and likes

Total views per album

Tracks streamed more on Spotify than YouTube

Advanced Level
Example: Energy Difference Using CTE
WITH energy_stats AS (
  SELECT
    album,
    MAX(energy) AS highest_energy,
    MIN(energy) AS lowest_energy
  FROM `project_id.dataset_id.spotify`
  GROUP BY album
)
SELECT
  album,
  highest_energy - lowest_energy AS energy_diff
FROM energy_stats
ORDER BY energy_diff DESC;


Other advanced analyses include:

Top 3 most-viewed tracks per artist

Tracks with above-average liveness

Energy-to-liveness ratio analysis

Cumulative likes using window functions

Query Performance Considerations in BigQuery

Unlike traditional databases, BigQuery is a serverless, columnar data warehouse.
Instead of indexing, performance optimization focuses on:

Selecting only required columns

Avoiding SELECT *

Using partitioned and clustered tables (where applicable)

Filtering data early using WHERE clauses

Leveraging BigQuery’s distributed execution engine

BigQuery automatically optimizes query execution, making it suitable for large-scale analytical workloads.

Technology Stack

Data Warehouse: Google BigQuery

Query Language: SQL

Concepts Used:

Aggregations

Window Functions

CTEs (WITH clause)

Data Cleaning with CAST & SAFE_CAST

Platform: Google Cloud Platform (GCP)

How to Run the Project

Upload the Spotify dataset to Google BigQuery

Create a table using the provided schema

Execute SQL queries from the queries/ folder

Analyze results using BigQuery’s query output

Key Skills Demonstrated

Exploratory Data Analysis (EDA)

Advanced SQL querying

BigQuery analytics

Data interpretation

Performance-aware querying

Next Steps

Build dashboards using Tableau / Power BI / Looker Studio

Perform time-series trend analysis

Apply clustering or partitioning for optimization

Extend analysis to recommendation insights

Author

Sanket D. Jambhule

License

This project is licensed under the MIT License
