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

[Answer link](https://toreply.univ-lille.fr/reponse_935) _Key: ch_

## Quizz

Cite some V's of Big Data (multiple choices):

- Answer A: Validation
- Answer B: Volume
- Answer C: Velocity
- Answer D: Voldemort
- Answer E: Variety

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_701) _Key: wn_

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

[Answer link](https://toreply.univ-lille.fr/reponse_194) _Key: rv_

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

[Answer link](https://toreply.univ-lille.fr/reponse_903) _Key: pe_

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

![Answer](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAAEsCAIAAAD2HxkiAAAG+UlEQVR42u3d0XKzKhQG0OOZvv8r97/oTCaTKFFxbzZxratO2ySE+AlChOX39/c/YJz/VQGM9fPxP5Zlefys2YTLLe/p+kvd32+2fj72GmcfuHou+L4TwSX1E1281cpf/dPzL52+D3RHVyuulKk/xWVZ6tdw+wTxfCL++KfH7x8kbdc1YeME9jiG1GbQ+aVmxb586FvdpZe+EtdfE547Phq9x8svMt/PwUdL+Dik3s81L7/ZKvz78ddoOnoq6qWoR+uw82T6nLq/U3PjUuWLryBCWsJrz2TPHZWX52z3YTpfa/9zNkp4om/2UoaX4/L5wH0/HLcO0HZF/R39R+vwpcBHu9OrJ7utXtK5Et69OzppH+ZEX65RwqOP2ip8Zw/z42udq8Ojb7kdp63TxMt1oBwe6I4+Ohg5Vxo1n+3cy61WXc0+2IlSrXZB308Tz71Tzl8THuqbZR4H+69wosu/Vfj3zthtj0hjeOO7o6vXS42xigtjc6hXtqeEOwt/6F3s+eeta85Lqmh/URvFOPcn1j+Uj1dunXl477p0DmY2mr7V4c2eEu4v/NboaLv87Ue1R0dPfF7nxqWPTtb3vNZNQ6iCbnW21i5Vvybk64mflhCIH5gBhBCEEBBCEEJACEEIASEEIQSEEIQQEEIQQkAIQQgBIQQhBIQQKklaY6bgAsyr63qklTNtVZGjCxzWf86xR4iWEHRHASEEIQSEEIQQuMrIZfALDtOPLXzBcm7tx5jz8KmPEC0h6I4CQghCCAghCCHQVm6n3s7B4ohB7f33W3T+Z8SNHZ2TBJ3PWXAip+CuuFpCEEIQQkAIQQgBIYR7+lEFz9JmI1ZFLKC0X+fbjJgL0RICQghCCAghCCEghPDFTFF8lrYwUcR8QMQ9HOYttIQghIAQghACQghCCPQrN0Uxdvw6bUg9YpOGtHs4Ouctpj5CtISgOwoIIQghIIQghMBVRk5RjN2jOKLwaetEpa09lTbx8H1HiJYQhBAQQhBCQAhBCIG2pCmKO6/tk7Y39dSzEXc+QrSEIIQghIAQghACQgj3tFQbGu4cE4+456BTxBRF53vvLOfYmxvSypkWDS0h6I6CEAJCCEIICCHcU9JdFGlf8I+YjRi7F0XEVErBUf60jTTG3iyiJQTdUUAIQQgBIQQhBB7K7UXROR8QMRsRMXqeNmuSditAWs0XPOq0hKA7CgghCCEghCCEwAkj96IYu89B2gpIBddfSrsvpODHoSUEhBCEEBBCEEJACKGIkXdRpH11PWLH6alnIyLW3YooZ8QBVnDeQksIQghCCAghCCEghHBPP9UKNHb1p4jtMQp+63/selbf93AtIeiOAkIIQggIIQghcMKSMw4bMfg+dtuJsesazbJOVMGNH+xFAQghCCEghCCEgBBCEcvYwdm9pQwYVp56RL5zyqfgSk1jb0AxRQG6o4AQghACQghCCOSbeIpi1dR3POw39oUiPqO0g0FLCAghCCEghCCEgBBCERPvRTHLUHXEiHzBWZPO977/c9//jiI2P9cSgu4oIIQghIAQghACVxm5F8UsO06nrdRUcPR86rmQWSaxtISgOwpCCAghCCEghHBPyyyL4ex9P5Psz7zf2P0YZtkiYpapKS0h6I4CQghCCAghCCHwMPIuilURSwPNMnY/y2xEwRs7Cu6ZoSUE3VFACEEIASEEIQTafuYt+v4R5LTx64gNFQreAjJ2s+60mtcSgu4oIIQghIAQghACoUZOUYxdWShi6L/gvEXaZhJjd4NIu39FSwi6o4AQghACQghCCFxljrsoOkf504pUsJYKfkb7yzn1DhNaQtAdBYQQhBAQQhBCoG3kXhRp37v/vn0jBh80Q1d/ijgYxta8lhB0R0EIASEEIQSEEO5pKTgCPrI6AlYBmmV6ZpYltmZZe0pLCLqjgBCCEAJCCEIItCUt9FRwWaSxu1h3zhx01ufY+0IiipS2lYWWEHRHASEEIQSEEIQQuEq57bIjpA2pd773tOeMGNAfu55VxK0V7qIA3VFACEEIASEEIQRCldsu+yYj3REvFLGmU1o5O429BURLCLqjgBCCEAJCCEIInPCjCj7qXG4oYk2nsSPyEW8z4h0V3NZbSwi6o4AQghACQghCCDyYovgsbRfrguUcW/i0/ULsRQG6o4AQghACQghCCOQrN0UxdrC48yv2aZtJRKy/VPDj6KzksTtMaAlBdxQQQhBCQAhBCIG2kVMUBXcF2C9tCaO0zSTGfnARO3h3VrKWEHRHASEEIQSEEIQQCLUU/FI5aAkBIQQhBIQQhBAQQhBCQAhBCAEhBCEEhBCEEBBCEEJACEEIASEEIQSEEIQQEEIQQkAIQQgBIQQhBIQQhBAQQhBCQAhBCAEhhGn8A0SxFWDnfveWAAAAAElFTkSuQmCC)

[Answer link](https://toreply.univ-lille.fr/reponse_685) _Key: tf_

