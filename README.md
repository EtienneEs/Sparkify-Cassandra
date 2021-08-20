# Sparkify-Cassandra

ETL (Extract, Transform &amp; Load) Pipeline to extract event data from csv files and ingestion into NoSQL Database (Apache Cassandra). This Project is part of the [Udacity Data Engineering nanodegree](https://www.udacity.com/course/data-engineer-nanodegree--nd027).

- [About](#about)
- [Solution Strategy](#solution-strategy)
- [ETL Pipeline and Database Design](#etl-pipeline-and-database-design)


## About

This project was created for Sparkify, a music streaming provider. The Analytics team requires a high availability database with low latency capable of handling large amounts of data whilst providing fast reads for the following types of queries:

1. artist, song title and song length for sessionId 338 and itemInSession 4
2. artist, song title, first name and last name of user with the id 10 in session 182
3. every user first name and last name who listend to 'All Hands Against His Own'


## Solution Strategy

- Pre-processing the .csv files (into a single file)
- Connecting to the cluster, creating and setting the keyspace
- For every Query:
  - Design NoSQL data model & create table
  - Ingest Data
  - Verify Data by running example queries

## ETL Pipeline and Database Design

### The Raw Data

The raw data consists of one data set *event_data*.  The directory contains csv files named with a timestamp.

### Pre-processing

In order to speed up and facilitate the ETL process the .csv files are pre-processed into a single *.csv* file, named *event_datafile_new.csv*.

### Data Modeling

For each query a (denormalized) data model is created to optimize the read queries.

### ETL Design

The ETL process contains the following steps:

1. Pre-processing
2. For each query:
    1. Create Table
    2. ETL of the data
    3. Select Query to verify the data
3. Drop tables
4. Disconnect

## Tech/Framework used

- Apache Cassandra
- Jupyter Notebook

## Files

- The raw data of the Project can be found in **event_data** folder.
- **Sparkify-Apache-Cassandra.ipynb** contains the complete solution.
- **.gitignore** Python gitignore provided by GitHub

## Credits and Acknowledgments

This project is part of the [Udacity Data Engineering Nanodegree](https://www.udacity.com/course/data-engineer-nanodegree--nd027)
