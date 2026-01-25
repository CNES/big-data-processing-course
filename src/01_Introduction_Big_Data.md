---
title: Introduction to Big Data and its Ecosystem
author: Guillaume Eynard-Bontemps, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2026
---

# What is Big Data?

## Data evolution

1 ZB  
1,000,000 PB  
1,000,000,000,000 GB  
1,000,000,000,000,000,000,000 B  

![Evolution of the global datasphere size (IDC)](https://supaerodatascience.github.io/DE/slides/static/img/datasphere.png)

## Some figures

:::::::::::::: {.columns}
::: {.column width="50%"}

![](images/a-day-in-data.jpg)

:::
::: {.column width="50%"}

![](https://www.digitalsilk.com/wp-content/uploads/2024/12/how-much-data-is-generated-per-day-hero-image.jpg)

:::
::::::::::::::

## Some figures in sciences

:::::::::::::: {.columns}
::: {.column width="50%"}

### Earth Observation Data

![Volume of data per year (source The Australian Geoscience Data Cube — Foundations and lessons learned, A. Lewis)](images/The-estimated-volumes-EOS-data-produced-by-the-Landsat-8-Sentinel-1-2-3-and.jpg){width="60%"}

:::
::: {.column width="50%"}

### CERN

- The LHC experiments produce about 90 petabytes of data per year
- an additional 25 petabytes of data are produced per year for data from other (non-LHC) experiments at CERN

![CERN current data volumes](images/CERNVolumes.png)

[You can have a look](https://monit-grafana-open.cern.ch/d/000000884/it-overview?orgId=16)

:::
::::::::::::::

## 3V, 4V, 5V{background-image="https://www.lebigdata.fr/wp-content/uploads/2016/05/les-4-V-du-big-data-ibm.jpg"}

## What is Behind Big Data

:::::::::::::: {.columns}
::: {.column width="50%"}

### Data

Volume, variety, multiple sources, internal, external...

### Tools and technology

Store: Cloud storage, Hadoop, Specialized Hardware

Compute, Analyse: Calculators, Cloud, Hadoop, Spark, Dask, Jupyter

Visualize, Use: Applications, Web interfaces, Dashboards

:::
::: {.column width="50%"}

### Definition (Wikipedia)

> Big data is a field that treats ways to analyze, systematically extract information from, or otherwise deal with data sets that are too large or complex to be dealt with by traditional data-processing application software.

> Big data is where parallel computing tools are needed to handle data.

Not a technology.

:::
::::::::::::::

## Quizz

What is the estimated size of the global data sphere in 2025?

- Answer A: 175 Petabytes
- Answer B: 175 Exabytes
- Answer C: 175 Zetabytes

![Answer](https://cdn.strawpoll.com/images/polls/qr/YVyPv9qP4gN.png)

[Answer link](https://strawpoll.com/YVyPv9qP4gN)

## Quizz

Cite some V's of Big Data (multiple choices):

- Answer A: Validation
- Answer B: Volume
- Answer C: Velocity
- Answer D: Voldemort
- Answer E: Variety

![Answer](https://cdn.strawpoll.com/images/polls/qr/6QnMQkd1Pne.png)

[Answer link](https://strawpoll.com/6QnMQkd1Pne)

# Legacy “Big Data” ecosystem

## Blowing ecosystem{background-image=https://external-preview.redd.it/P6JcS17ECpmFF2si8KVnuoKpiabc5-pWTmgRt_YxTx4.png?auto=webp&s=3cbdbbe95112b6d6f5fb0bb59f6421b8e8be999e}

## Hadoop & Map Reduce

![Hadoop ecosystem](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/10/HADOOP-ECOSYSTEM-Edureka.png)

## NoSQL (Not only SQL)

:::::::::::::: {.columns}
::: {.column width="50%"}

![SQL vs NoSQL databases model (altitudetvm)](images/sql-vs-nosql.png){width=50%}

:::
::: {.column width="50%"}

![Popular NoSQL Databases](https://miro.medium.com/max/800/1*Sz73n23vbZ_Gtsx2FU3Otg.jpeg)

:::
::::::::::::::

## Logs, ETL, Time series

:::::::::::::: {.columns}
::: {.column width="50%"}

![Elastic stack](https://www.elastic.co/static-res/images/elk/elk-stack-elkb-diagram.svg){width=60%}

:::
::: {.column width="50%"}

![Grafana/Prometheus/InfluxDB](https://www.sqlpac.com/en/documents/images/influxdb-v2-getting-started-setup-preparing-migration-from-version-1.7-02.png)

![Dahboards](https://grafana.com/static/img/screenshots/Modal_dashboards.png){width=60%}

:::
::::::::::::::

## Dataviz

:::::::::::::: {.columns}
::: {.column width="50%"}

### BI (softwares)

![Classical BI tools](https://information4all.com/wp-content/uploads/2018/08/bi-logos.jpg){width=50%}

:::
::: {.column width="50%"}

### Python (libraries)

![Python data vizualisation landscape](https://rougier.github.io/python-visualization-landscape/landscape-colors.png){width=60%}

:::
::::::::::::::

## Data Science and Machine Learning

![Machine Learning tools (Azure)](images/mlops_azure.png)

## Quizz

Which technology is (was?) the most representative of the Big Data world?

- Answer A: Spark
- Answer B: Elasticsearch
- Answer C: Hadoop
- Answer D: Tensorflow
- Answer E: MPI (Message Passing Interface)

![Answer](https://cdn.strawpoll.com/images/polls/qr/61gD9MxPOZw.png)

[Answer link](https://strawpoll.com/61gD9MxPOZw)

# Big Data use cases

## Typical Dataset (originally)

Huge amount of small objects:

- Billions of records
- KB to MB range

Think of:

- Web pages, and words into it
- Tweets
- Text files, where each line is a record
- IoT and everyday life sensors: a record per second, minute or hour.

## Cost effective storage and processing

- Commodity hardware (standard servers, disks and network)
- Horizontal scalability
- Proximity of Storage and Compute
- Secure storage (redundancy or Erasure Coding)

Use cases:

- Archiving
- Massive volume handling
- ETL (Extract Transform Load)

## Data mining, data value, data cross processing

Extract new knowledge and value from the data:

- Statistics,
- Find new Key Performance Indicators,
- Explain your data with no prior knowledge (Data Mining)

Cross analysis of internal and external data, correlations:

- Trends with news or social network stream and correlation to sales
- Near real time updates with Stream processing

## Scientific data processing

Data production or scientific exploration:

- Stream processing, or near real time processing from sensor data
- Distributed processing of massive volume of incomming data on computing farm
- Data exploration and analysis
- Data Science

![Gaia: 150TB input, 6PB generated](images/GaiaPlatform.png){width=40%}
![Iota2: 20-40TB of input data](images/Iota2.png)

## Other main use cases

:::::::::::::: {.columns}
::: {.column width="50%"}

- Digital twins
- Predictive maintenance
- Smart City
- Real time processing

:::
::: {.column width="50%"}

![Airplane Digital Twin](images/airplane-dt.png)

:::
::::::::::::::

## Quizz

What are the typical volumes of scientific Datasets (multiple choices)?

- Answer A: MBs
- Answer B: GBs
- Answer C: TBs
- Answer D: PBs
- Answer E: EBs

![Answer](https://cdn.strawpoll.com/images/polls/qr/BJnXVEWkXZv.png)

[Answer link](https://strawpoll.com/BJnXVEWkXZv)

# Big Data to Machine Learning

## Big Data ecosystem allows (part of) machine learning to be effective

- More data = more precise models
- Deep Learning difficult without large (possibly generated) input datasets
- Tools to collect, store, filter, index, structure data
- Tools to analyse and visualize data
- Real time model learning

[https://blog.dataiku.com/when-and-when-not-to-use-deep-learning](https://blog.dataiku.com/when-and-when-not-to-use-deep-learning)

## Pre processing before machine learning

- Data wrangling and exploration
- Feature engineering: unstructured data to input features
- Cross mutliple data sources
- Get insights on the data before processing it (statistics, vizualisation)

## Distribute datasets and algorithms

- For preprocessing as seen above
- Means to load and learn on large volumes by distributing storage
- Distributed learning with data locality on big datasets
- Distributed hyper parameter search

![Lambda Architecture (Azure)](https://docs.microsoft.com/fr-fr/azure/architecture/data-guide/big-data/images/big-data-pipeline.png){width=60%}

## Quizz

Are Big Data and Machine Learning the same?

![Answer](https://cdn.strawpoll.com/images/polls/qr/GPgVYMaJzna.png)

[Answer link](https://strawpoll.com/GPgVYMaJzna)

