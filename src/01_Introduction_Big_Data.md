---
title: Introduction to Big Data and its Ecosystem
author: Guillaume Eynard-Bontemps, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2025
---

# What is Big Data?

## Data evolution

1 ZB  
1,000,000 PB  
1,000,000,000,000 GB  
1,000,000,000,000,000,000,000 B  

![Evolution of the global datasphere size (IDC)](https://supaerodatascience.github.io/DE/slides/static/img/datasphere.png)

## Some figures

![Volume of data produced in a day in 2019 (source www.visualcapitalist.com)](images/a-day-in-data.jpg){width="50%"}

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

Store, Compute, Analyse: Calculators, Cloud, Hadoop, Spark, Dask

Visualize, Use: Applications, Web interfaces

:::
::: {.column width="50%"}

### Definition (Wikipedia)

> Big data is a field that treats ways to analyze, systematically extract information from, or otherwise deal with data sets that are too large or complex to be dealt with by traditional data-processing application software.

> Big data is where parallel computing tools are needed to handle data.

Not a technology.

:::
::::::::::::::

## Quizz

What is the estimated size of the global data sphere?

- Answer A: 175 Petabytes
- Answer B: 175 Exabytes
- Answer C: 175 Zetabytes

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_616) _Key: bh_

## Quizz

Cite some V's of Big Data (multiple choices):

- Answer A: Validation
- Answer B: Volume
- Answer C: Velocity
- Answer D: Voldemort
- Answer E: Variety

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_8114) _Key: zv_

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

Which technology is the most representative of the Big Data world?

- Answer A: Spark
- Answer B: Elasticsearch
- Answer C: Hadoop
- Answer D: Tensorflow
- Answer E: MPI (Message Passing Interface)

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_411) _Key: ge_

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

![Airplane Digital Twin](https://www.prolim.com/wp-content/uploads/2019/08/digital-twin.jpg)

:::
::::::::::::::

## Quizz

What is the typical volumes of scientific Datasets (multiple choices)?

- Answer A: MBs
- Answer B: GBs
- Answer C: TBs
- Answer D: PBs
- Answer E: EBs

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_718) _Key: fr_

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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_799) _Key: dq_

