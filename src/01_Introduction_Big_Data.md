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

![Evolution of the global datasphere size (IDC)](https://supaerodatascience.github.io/OBD/slides/static/img/datasphere.png)

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

![Answer](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAAEsCAIAAAD2HxkiAAAG1ElEQVR42u3d3Y6bMBAG0FLl/V95e7FSlCaEOJiZseGcq6rKjzF8sbEXe/n5+fkD1PmrCqDW7eMrlmW5/1uzCYdbXtP1m7rf/3n37+++Y+8bV38LzvdDcEj9RBdvu/IHP4Q5uqOPFT2mqU/wsizj1/B2uh5/iDdSStc94WpV3qveT13o78uYFft00ldzKIEZ94T7ro+N3uPhN5lP10HjZz6W8H61vf7WPP3Pu8K/Xouvl+zqD9m3FfVU1G/r8Ksf099vWZbl3f3Ia2HY3xJudDY6+zCrP5zb3Zvd39X+mRsl3NE3eyrD0yX72JK8Xv0f77LetT876vCpwO13AatdIZ2j47ujoX2Y9u5NQl9uo4SdfbOjepgfv2tfHX57yC2/OyJ0ZHf03vfIudMY89P2fd1q1Y15gfb0XZ96p+/aZ6HquifM6dwfeJ7e9ZHyC/96p3fuK3L1zlYCR+mOrvZbNsYqDozNV72ylhI2Fv6ro2h5cVzf76ui6oImda8+3rl15uF1yLFzMHOj6Vsd3uwpYXvh342Obpd/+13bo6M7zte+cWmT9eEhVHGXuoakZfR7Qk5P/LSEwDOPMoEQghACQghCCAghCCEghCCEgBCCEAJCCEIICCEIISCEIISAEMK5Ja0xM+BeBfuWG8v/otW3d76ys/DfLpp4+itESwi6o4AQghACQghCCOxQuQx+2hBw2hxDRIVEjN1HTDyklXPAK0RLCLqjgBCCEAJCCEII7DDcTr0DTie0P7IQ8Znt8wFpj1a013xa1dVeIVpC0B0FhBCEEBBCEEJgh5sqOFDEgwjtQ+qdr2wv/ICLMmkJASEEIQSEEIQQEEKYjimK/0z9F/oRW1m0H2bEAxNaQkAIQQgBIQQhBIQQTmy4KYraQe20VZXa13QasJy1J+580x5aQhBCEEJACEEIASGEa6qcohhwvaDa7RwiphNmKecsV4iWEIQQEEIQQkAIQQiBoyyW4vmvOrL2kY4oUsQURdpnagkBIQQhBIQQhBAQQria4aYoOkfkOz9zli+qPR0DTrpMPe2hJQQhBCEEhBCEEBBCuKakKYraFXvO9yhA2lJLnWezc3YnYnJowGkPLSHojoIQAkIIQggIIVxT0l4UtRsqnO9RgIjR87RppNqzOeD+FlpCEEIQQkAIQQgBIYRrSpqiqP2r/84irWovfMSIfO3pmNqAS0JpCUEIQQgBIQQhBIQQrmnivShWRUx7DLiIUMQcQ9rbZ1kjS0sIuqOAEIIQAkIIQgiEGu4pirQvShu7T6uliC0iIt4+YIVoCUF3FBBCEEJACEEIgXzLgOverJRyvN22a8uZtrdH2lMpF3mGQ0sIuqOAEIIQAkIIQgjc3eYtetp+12m7VqSN8tdOusxSTi0h6I4CQghCCAghCCEQauLtsgfctaLz29NEVF1tOTuvkNrnLbSEoDsKQggIIQghIIRwTUkLPdWugNRepPP92X7aRhrnO3ZTFKA7CgghCCEghCCEQKjKKYqpFyZKq5CIt0dUXe1cyCyzEVpC0B0FhBCEEBBCEELgLmmhp9p1eDqH/tPmVyKOfcDPTKvPWZ4g0RKCEIIQAkIIQggIIVxT5V4UqyKGlWt3Gmg/zM5Xth9mxDMHA84H1M4taQlBdxQQQhBCQAhBCIFttylKOcvW1lM/3BDxpEvasQ84C6UlBN1RQAhBCAEhBCEEtlUu9NQubfi7dmGiiGOvHeWvXeBrll3BtYQghCCEgBCCEAJCCNdU+RRFxG7GndMJtcc+y67gaVuDRBzRgM9baAlBdxSEEBBCEEJACOGalpzB2YiZgwHf3n7s7SJO0PmeTogovL0oQHcUEEIQQkAIQQiBUMss6/UnVcfMOyIM+HxA7e4aA85GaAlBdxQQQhBCQAhBCIG7pIWezvd39+1bWXTW0oALKEWczQE3P9cSgu4oIIQghIAQghACoSr3ohhwSH3A3SBqHwVIm1uaZUN1LSHojgJCCEIICCEIIXCU22gFuvLODWlPJ0TUZ+1hpp1NLSHojgJCCEIICCEIIXCUmyp41LnPQfvqTxHTHgMOvq+q3dtjwKrTEoLuKAghIIQghIAQwjWZovgsbRGhzjWdZnkII23drYj9QrSEoDsKCCEIISCEIITAUZacEdvav1KPeGShdqS79ojOtw+HpyhAdxQQQhBCQAhBCIF8lVMUtWo3l46YD5h61iTiM2dZ+UpLCEIIQggIIQghIIRwTcuAI7agJQSEEIQQEEIQQkAIQQgBIQQhBIQQhBAQQhBCQAhBCAEhBCEEhBCEEBBCEEJACEEIASEEIQSEEIQQEEIQQkAIQQgBIQQhBIQQpvEPn/eOlgdOpxsAAAAASUVORK5CYII=)

[Answer link](https://toreply.univ-lille.fr/reponse_84) _Key: yi_

## Quizz

Cite some V's of Big Data (multiple choices):

- Answer A: Validation
- Answer B: Volume
- Answer C: Velocity
- Answer D: Voldemort
- Answer E: Variety

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_730) _Key: rf_

# Legacy “Big Data” ecosystem

## Blowing ecosystem{background-image=https://external-preview.redd.it/P6JcS17ECpmFF2si8KVnuoKpiabc5-pWTmgRt_YxTx4.png?auto=webp&s=3cbdbbe95112b6d6f5fb0bb59f6421b8e8be999e}

## Hadoop & Map Reduce

![Hadoop ecosystem](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/10/HADOOP-ECOSYSTEM-Edureka.png)

## NoSQL (Not only SQL)

:::::::::::::: {.columns}
::: {.column width="50%"}

![SQL vs NoSQL databases model (altitudetvm)](https://altitudetvm.com/images/komputer/apa-itu-nosql-berikut-ini-pengertian-nosql-beserta-kelebihannya_2.png){width=50%}

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

![Machine Learning tools (Azure)](images/ml_azure.png)

## Quizz

Which technology is the most representative of the Big Data world?

- Answer A: Spark
- Answer B: Elasticsearch
- Answer C: Hadoop
- Answer D: Tensorflow
- Answer E: MPI (Message Passing Interface)

![Answer](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAAEsCAIAAAD2HxkiAAAG+UlEQVR42u3d3ZKiOhQG0GGq3/+VnYuushxFBML+Qda6mjqnbWLkMyHpJNPtdvsD1PmrCqDWz8efmKbp/m/NJhxuek3Xb+p+/8u7f2+7xt4Xzn4XfN8XwSH1E1ewJ0/l/Fj4tu+uXUs4TVPzarrdbrP3hJgl1PymlG76Af57Jlz42pumyfdZ6F1+xoqVwLxnwn33x0Lv8fCHzKcPe+XvfCzh/Svm9bvm6b+8K/zrDffYh19oD7dW1FNRt9bhvi/T2Wu9vsHZC4ni2pZwuUJ3975eP4PH/3XIFR9/4frfuVDCla96vNBTGZ4eoe837myL9y4PyxX1+/iwtQ6fCrz+VVuvpd+0szsa9Pyz0KocksMdfbmFEm591bvCD/YwP15rXx1ufcuP3ynrryWB+7ujv21CQufh2Esk93bePTm/Vl3PuzCtVLNNt7x9fibM6cEf+GG8e4TLL/zrk94X3Hb72rStcxj8DbpNZx8/ZscqDozNpl7ZmhKuLPymd7Hmh989cx5SReuLGlcM/vtQPj65DebhdchxcDBzoembHd4cKeH6wr8bHV0u//KrlkdHd3xe+8altw4Ie0TcHBa1c6kbRSS6PxPy9cRPSwjED8wAQghCCAghCCEghCCEgBCCEAJCCEIICCEIISCEIISAEIIQAkIInSTtMdPwQIKFrcGqrl5b8/v2X8v/nbV3iJYQdEcBIQQhBIQQhBA4SuU2+A2H6WsL37Cc785jzHn5qe8QLSHojgJCCEIICCEIIbCs3Um9g4PFEYPa69dbDP5kxMKOwUmCwd/ZcCKn4am4WkIQQhBCQAhBCAEhhGv6UQWPImYj1qsdfB98mxFzIVpCQAhBCAEhBCEEhBC+mCmKzwY3Jho8uSFt2iNiesa8hZYQhBAQQhBCQAhBCIF32k1R1I5fpw2pR+yVFDGdUFtLDe8QLSHojgJCCEIICCEIIXCUyimK2jOKIwofsd7iLD8ZUUunvkO0hCCEgBCCEAJCCEIILEuaorjI3j4RQ+oRcwy17+jKd4iWEIQQEEIQQkAIQQiBu6nb0HDEkdFp512vL1JEhdTOWzSsz9rjx7WEoDsKCCEIISCEIITAsqQpitrthiJeXvyxZQ2+114oopxpEzlaQtAdBYQQhBAQQhBCYFm7sygGx4UbzkZEDL6nLVmorfnajbO0hKA7CgghCCEghCCEQKjKsyhqzzmIOPM5bQlIrbMsajnLadtaQhBCEEJACEEIASGEa6pcRZE2+D74h/MRsxG1syYXWb/ScK2JlhB0RwEhBCEEhBCEELibGv6R/kwps0a6a5dBNDxc+vte3nD9ipYQdEdBCAEhBCEEhBCuKWkVRdrg+1k2UGp4SMP6cs4WaXAFScQajrSXawlBdxQQQhBCQAhBCIEdzrGKIuSdB2x2lHYU8+AURcTCjtqqS6sQLSHojgJCCEIICCEIIXCUdlMUEWPNacPfaSseai8UUUsRd8hZpt+0hCCEIISAEIIQAkII11S50dPggdXr1Q5VR4zIn2WfqIjDJCJOBU9b/qIlBN1RQAhBCAEhBCEE7n6+7P3UriQYLGfDOZvauZCIq9fORmgJQXcUEEIQQkAIQQiBuxOfRdFwrHl9OderPY/hLEdEnGVqSksIuqOAEIIQAkIIQgjcVU5RnPpw6cFNhNZfKO0dNfzgIq7e8CgLLSHojoIQAkIIQggIIVxT5VkUaRqOX9ceETH4wdUe1j04Y9Sw5rWEoDsKQggIIQghIIRwTZVnUdTuLJT2N/KDJ0xc+WTss1xdSwi6o4AQghACQghCCOxwjuOyB/9GPq1IsyKKdJZFGGmVPFh1WkLQHQWEEIQQEEIQQiBf0lkUDU9uiHj5RYbUaysk4maorXktIeiOghACQghCCAghXNPUcAS8sjoCdgFKm56JeHnDof/aWtISgu4oIIQghIAQghACR7nEcdmzIs5Srt1mqnZZSe07SjvKQksIuqOAEIIQAkIIQggcpd1x2RHS9l8avNBZNo9Ke+8RH3HEChItIeiOAkIIQggIIQghsEO747IbjnTX/oV+xHxA7d5TtZMuDRf0aAlBCEEIASEEIQSEEK7pRxUcKO2Mh9qNiQbfZto2Uw2P9dYSgu4oIIQghIAQghACd6YoPos4iyLtOIfBctYWfvC8kLSjLLSEoDsKCCEIISCEIITADu2mKM6yPmBW2lkUEfsvNfw4Biu54QIULSHojgJCCEIICCEIIXBXOUXR8FSA9Wr3dKrdwugsJ3gPVrKWEHRHASEEIQSEEIQQCDU1/KNy0BICQghCCAghCCEghCCEgBCCEAJCCEIICCEIISCEIISAEIIQAkIIQggIIQghIIQghIAQghACQghCCAghCCEghCCEgBCCEAJCCKfxD7kznWido3SlAAAAAElFTkSuQmCC)

[Answer link](https://toreply.univ-lille.fr/reponse_514) _Key: dy_

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

[Answer link](https://toreply.univ-lille.fr/reponse_563) _Key: ri_

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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_933) _Key: fj_

