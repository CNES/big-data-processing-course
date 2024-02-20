---
title: Big Data Processing Course Introduction
author: Guillaume Eynard-Bontemps, Emmanuelle Sarrazin, Hugues Larat, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2024-02-24
---

# Welcome

## Course Overview

- Big Data Processing

Harnessing the complexity of large amounts of data is a challenge in itself. 

But Big Data processing is more than that: originally characterized by the 3 Vs of Volume, Velocity and Variety, 
the concepts popularized by Hadoop and Google requires dedicated computing solutions (both software and infrastructure), 
which will be explored in this module.

## Objectives

By the end of this module, participants will be able to:

- Understand the differences and usage between main distributed computing architectures (HPC, Big Data, Cloud, CPU vs GPGPU)
- Implement the distribution of simple operations via the Map/Reduce principle in PySpark
- Connect on a cloud computing engine (e.g. Google Cloud Platform) and  use it
- Understand the principle of containers (through Docker) and Kubernetes
- Deploy a Big Data Processing Platform on the Cloud
- Implement the distribution of data wrangling/cleaning and training machine learning algorithms using PyData stack, Jupyter notebooks and Dask

## Typical daily schedule

| Time slot | Content |
|-----------|---------|
| 9:00-10:30 | Slides, tutorial or exercises |
| 10:30-10:45 | Coffee Break |
| 10:45-12:15 | Slides, tutorial or exercises |
| 12:15-13:30 | Lunch (I know it's a bit short) |
| 13:30-15:15 | Slides, tutorial or exercises (not nap) |
| 15:15-15:30 | Coffee Break (we may also make two breaks) |
| 15:30-17:15 | Slides, tutorial or exercises (last session, at last) |

I'll try to propose some quizz to be sure you're following!

## About myself{background-image="images/HPC-blue.jpg" style="color:white"}

- Guillaume
- CNES (Centre National d'Etudes Spatiales - French Space Agency)
- Since 2016: 
  - 6 years in CNES Computing Center team
  - 1 year of holydays
  - 1 year in developping image processing tools
  - 6 years of using Dask/Python on HPC and in the Cloud
  - A bit of Kubernetes and Google Cloud
- Before that: 5 years on Hadoop and Spark
- Originally: Software developer (a lot of Java)

## About others

:::::::::::::: {.columns}
::: {.column width="50%"}

- Hugues
- CNES (Centre National d'Etudes Spatiales - French Space Agency)
- Since 2020: 
  - Cloud specialist
  - Ground Segment Engineer
- Before that:
  - System Architect
  - 8 years as Software Enginner and Tech Lead (a lot of Java)
  - 5 years as System & Network Technician

:::
::: {.column width="50%"}

- Emmanuelle
- CNES (Centre National d'Etudes Spatiales - French Space Agency)
- Since 2013: 
  - 6 years, HPC Expert
  - 5 years Image processing, 3D 

:::
::::::::::::::


## About yourselves

What are the previous courses you've followed in this master?

What are you familiar with in the big data, cloud, Python and machine learning subjects?

## First quizz

Let's try the Quizz mechanism.

What is this course module main subject?

- Answer A: Cloud computing
- Answer B: Big Data Processing
- Answer C: Machine Learning

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_916) _Key: ah_

# Program

## Day 1: Big Data, Distributed Computing and Spark

- [Introduction to Big Data and its ecosystem (1h)](01_Introduction_Big_Data.html)
  - What is Big Data?
  - Legacy “Big Data” ecosystem
  - Big Data use cases
  - Big Data to Machine Learning
- [Big Data platforms, Hadoop & Beyond (2h)](02_Big_Data_Platforms.html)
  - Hadoop, HDFS and MapReduce,
  - Datalakes, Data Pipelines
  - From HPC to Big Data to Cloud and High Performance Data Analytics 
  - BI vs Big Data
  - Hadoop legacy: Spark, Dask, Object Storage ...
- [Spark Introduction (1h)](03_Spark_Introduction.html)
- Play with MapReduce through Spark (Notebook on small datasets) (2h)

## Day 2: Cloud Computing and Kubernetes

- [Introduction to Cloud Computing (2h)](10_Cloud_Computing.html)
  - What's the Cloud, Virtualization
  - Cloud history, layers, Engines
  - Usage revolution and new Data processing standard
  - Google Cloud Engine
- First interaction with Google Cloud, how to get a server? (1h)
  - Exercise through Google console or cloud CLI
- Container & Kubernetes (2h) 
  - [Containers and Docker](11_ContainersAndDocker)
  - Play with Docker
  - [Containers Orchestration, Kubernetes](12_OrchestrationKubernetes.html)
    - Kubernetes & CaaS & PaaS (Databricks, Coiled)
  - [Object Storage and Cloud Optimized datasets](14_ObjectStorage.html)
  - Play with Kubernetes (if we have time)

## Day 3 (morning): Deploy your own processing platform on Kubernetes

- Deploy a Jupyterhub on Kubernetes
  - Exercise: Zero to Jupyterhub: deploy a Jupyterhub on Kubernetes
- Deploy a Data processing platform on the Cloud based on Kubernetes and Dask (3h)
  - Exercise: [Deploy Data processing platform on the Cloud](13_Dask_On_Cloud.html)

## Day 3 (afternoon): Python ecosystem for data processing

- [The rise of the Python ecosystem for Data Processing (1,5h)](21_Python_Data_Processing.html)
  - Data Science programming languages
  - Pydata stack (Pandas, Numpy, Matlplotlib, Jupyter)
  - Distributed and sctientific processing (Dask, PySpark)
  - Data vizualisation (Seaborn, Plotly, Pyviz)
  - Machine and Deep Learning (Sickit Learn, TensorFlow, Pytorch)
  - Jupyter notebooks, Binder, Google Colab
- Includes [Pandas library tutorial](https://github.com/esarrazin/pandas-cookbook), [Scikit-learn mooc](https://github.com/INRIA/scikit-learn-mooc/)
- [Distributed processing](23_Distributed_Processing.html)

## Day 4: Python for distributed processing

- [Manage large datasets](24_Large_Datasets.html)
- [Dask processing framework](25_Dask.html)
- Includes [Dask tutorial](https://github.com/dask/dask-tutorial).

## Day 4: Evaluation

- [Final Evaluation](30_Evaluation.html)
  - Prerequisite: Pangeo platform deployed before (on day 2 and 3)
  - Clean big amounts of data using Dask in the cloud (3h)
  - Train machine learning models in parallel (hyper parameter search) (3h)
  - Notebook with cell codes to fill or answers to give

## Quizz

What will we do today (multiple choices)?

- Answer A: Explain what's Big Data
- Answer B: See what's Hadoop
- Answer C: Dig into Cloud computing
- Answer D: Take a nap
- Answer E: Some Spark

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_252) _Key: mv_

