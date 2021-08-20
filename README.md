# Sparkify-Cassandra

ETL (Extract, Transform &amp; Load) Pipeline to extract event data from csv files and ingestion into NoSQL Database (Apache Cassandra). This Project is part of the [Udacity Data Engineering nanodegree](https://www.udacity.com/course/data-engineer-nanodegree--nd027).
For convenience I have created a microservice infrastructure (powered by docker) to improve reproducibility.

- [About](#about)
- [Solution Strategy](#solution-strategy)
- [ETL Pipeline and Database Design](#etl-pipeline-and-database-design)
- [Tech/Framework used](#tech/framework-used)
- [Files](#files)
- [Credits and Acknowledgments](#credits-and-acknowledgments)

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
- Docker

## Deployment

Please install docker.
[Docker](https://www.docker.com/)

## Getting Started

### Build the containers

```cmd

docker-compose build

```

### Start the containers

```cmd

$ docker-compose up

...
...
 or http://127.0.0.1:8888/?token=xxxxxxxxxxxxxxxxxxxxx

```

Docker compose will spin up two containers:

- cassandradb (the nosql database)
- cassandra_jupyter_notebook (jupyter notebook container)

Check the cassandra_jupyter_notebook logs:

```bash

docker logs cassandra_jupyter_notebook

```

Jupyter displays multiple links to start working in the browser. Use the last one with "http://127.0.0.1:8888/?token=xxxxx

## Files

- The raw data of the Project can be found in **workspace/event_data** folder.
- **README.md** documentation of the project.
- **docker-compose.yml** docker-compose file defining the services.
- **compose/jupyter-notebook/Dockerfile** Dockerfile for cassandra_jupyter_notebook.
- **compose/cassandra/Dockerfile** Dockerfile for cassandradb.
- **requirements.txt** requirements for the cassandra_jupyter_notebook.
- **workspace/Sparkify-Apache-Cassandra.ipynb** contains the complete solution.
- **.gitignore** Python gitignore provided by GitHub

## Credits and Acknowledgments

This project is part of the [Udacity Data Engineering Nanodegree](https://www.udacity.com/course/data-engineer-nanodegree--nd027)

Helpfull documentation and resources:

- [Docker Documentation](https://docs.docker.com/)
- [Jupyter Docker Stacks](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/recipes.html)
- [Markdown Guide](https://www.markdownguide.org/basic-syntax/)
- [Apache Cassandra](https://cassandra.apache.org/_/index.html)
- [Netflix osstracker](https://github.com/Netflix/osstracker/blob/master/docker-compose.yml)
