---
title: Introduction to Big Data and its Ecosystem
author: Guillaume Eynard-Bontemps, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2020-11-15
---

# What is Big Data?

## Data evolution

1 ZB  
1,000,000 PB  
1,000,000,000,000 GB  
1,000,000,000,000,000,000,000 B  

![Evolution of the global datasphere size (IDC)](https://supaerodatascience.github.io/DE/slides/static/img/datasphere.png)

## Some figures

![Volume of data produced in a day in 2019 (source www.visualcapitalist.com)](https://www.visualcapitalist.com/wp-content/uploads/2019/04/a-day-in-data.jpg){width="50%"}

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

[Answer link](https://toreply.univ-lille.fr/reponse_176) _Key: yk_

## Quizz

Cite some V's of Big Data (multiple choices):

- Answer A: Validation
- Answer B: Volume
- Answer C: Velocity
- Answer D: Voldemort
- Answer E: Variety

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_169) _Key: zq_

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

![Answer](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAAEsCAIAAAD2HxkiAAAG2klEQVR42u3d3ZIaIRAG0EzK93/lzUWqLEtHZOzpBnbOuUpFV5mfTxAEtp+fnz/AOH+dAhjr9vEZ27bd/63ahNNtr+n6n7r///Pu38fe49s/3P0s+H0fBKecn+zi7Z787x5ivzn6eMrmtPSF3LZt/jPc/oB4/CCOPETrO+HumbqfxMk/rZd2v1knr6IfE/XdQ7Sao6/n68TW49MLft1QeVewpwvc+Zq7JXx9i87Cv95k726+d8229nE9FeBe1LPOYc/zd0/F0YdofSds3IiRT9CneyVyeXaf37j8X5SwHcL+b8uHSvXxuDrPZ+Tbne+EUzRHU9swH5s3lW25Rgm/a5ud3sL8+F7fncOjh+w7YY3b4xWq6T849y2KL/C7b86vp27Oj/9I2/V+mK9Nhs6H5O1DCJ++aUxyHxxtoGaX/13hXxtjbjuGNUefWiCvjaindsuJsTnUKuspYWfhDx1Fz5N3i3FKpA8VtVGM7x7iQ8fM1x1o7Ty0e0fjnQpP/99f+J4S9he+vxe0/6/avaNfXC8dM5OG0Am61Ke1emn274T8euKnJgTyO2YAIQQhBIQQhBAQQhBCQAhBCAEhBCEEhBCEEBBCEEJACEEIASGEmRStMTPhGsy763qUlbNsVZGjCxzO/5pj7xA1IWiOAkIIQggIIQghcJaRy+BP2E0/tvATlvPdfow1f770HaImBM1RQAhBCAEhBCEE2qbbqTfYWZzRqd0/3yL4zIyJHcFBguBrTjiQM+GuuGpCEEIQQkAIQQgBIYRrujkFj8pGI3aN7XwPHmbGWIiaEBBCEEJACEEIASGEX8wQxWfBhYky5hz0D2YE940wbqEmBCEEhBCEEBBCEEIgyXRDFGP7rzO61MtmZpSNBwSLtPQdoiYEzVFACEEIASEEIQTOMnKIYuwexRmFn3A0ouyZ7hA1IQghIIQghIAQghAChxQNUVxkbZ+yvamD7z7haMSVV39SE4IQghACQghCCAghXNM2W9dwxpbRZT3yZasqZRx72TUKWmX7cTUhaI4CQghCCAghCCHQVjSLIthRnrE/8yr912MnN2QUPuMOyRjIUROC5igghCCEgBCCEAKpptuLomxv6v4/DxY+o/N97ISJpUcOyjYVVxOC5igghCCEgBCCEAJtI/eiGLvPQXCPh/5nZgy6TKhsNKJsoSc1IWiOAkIIQggIIQghkGrkLIqyvuayH86v0vm+9PyVsiKpCUFzFBBCEEJACEEIgVTbKj/S3yn6IusaTbg39dgFqcb++dhREzUhaI4CQghCCAghCCFwVzREMbafPfiawSPK6CgfOzNj7JhNxq1oLwrQHAWEEIQQEEIQQqDedLMoxv7IfcJZFMGzFDx1ZZejbF/usntJTQiao4AQghACQghCCLQtPESxa8IpC6vMIOl/o+CFK1v5apVFzNSEIIQghIAQghACQgjXVLRddvA38qtsKpDx7ruHOeGoSfDY+++Q/iMKblBhLwrQHAWEEIQQEEIQQiDVGrMoxu44PXZFqbG950uPhawyiKUmBM1REEJACEEIASGEaxo5i2LXhCsLlR37KvsxlJ3PsmM3iwI0RwEhBCEEhBCEEKi3rbJef+ggq/a3GPtb/lW2ts64mkuPbKkJQXMUhBAQQhBCQAjhmoqGKMo6tTP6rydcVSko44RMuFn3KtddTQiaoyCEgBCCEAJCCNd0m61AZXtRlA2Q7ApuBB3sfM84IWNnkKwyGqEmBM1RQAhBCAEhBCEE7m5LlLK/W3mV5YYy3v33GTszQ00ImqOAEIIQAkIIQgikul3hIIMjHGN3sd41dsPqjCMq2+vbXhSAEIIQAkIIQggIIUyiaIiiv7c3o1947HBCmWDne8ZATsYlLlu6Sk0ImqOAEIIQAkIIQgikKhqimLDrP9j5HuwTD/byB3exnnBeSMb5DN4MakLQHAWEEIQQEEIQQiDVyIWeVtm54fdNwhi7M3ZGkcpmkKgJQXMUEEIQQkAIQQiBs0y3F8WEPd1l6xqVbahQdpj9cziClh5GUhOCEIIQAkIIQggIIVzTzSk40djxgKUPM2OMIePMqwlBcxQQQhBCQAhBCIGzGKL4rGzrhbLXLFtVKfiawf1Cxm7SriYEzVFACEEIASEEIQTaphuiWGV+wK6MVaqCayUtPV0jeJLH7jChJgTNUUAIQQgBIQQhBNpGDlGssrn0rrIljMoWjxp74TJ28A6eZDUhaI4CQghCCAghCCGQapvwR+WgJgSEEIQQEEIQQkAIQQgBIQQhBIQQhBAQQhBCQAhBCAEhBCEEhBCEEBBCEEJACEEIASEEIQSEEIQQEEIQQkAIQQgBIQQhBIQQlvEPgBHcjMV8DIIAAAAASUVORK5CYII=)

[Answer link](https://toreply.univ-lille.fr/reponse_888) _Key: an_

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

[Answer link](https://toreply.univ-lille.fr/reponse_283) _Key: tk_

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

Is Big Data and Machine Learning the same?

![Answer]()

[Answer link](https://toreply.univ-lille.fr/reponse_623) _Key: go_

