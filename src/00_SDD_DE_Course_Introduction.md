---
title: SDD DE Data Distribution Course
author: Guillaume Eynard-Bontemps, Hugues Larat, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2025-01
---

# Welcome

## Course Overview

- [Data Distribution & Big Data Processing](https://supaerodatascience.github.io/DE/2_1_overview.html)

Harnessing the complexity of large amounts of data is a challenge in itself. 

But Big Data processing is more than that: originally characterized by the 3 Vs of Volume, Velocity and Variety, 
the concepts popularized by Hadoop and Google require dedicated computing solutions (both software and infrastructure), 
which will be explored in this module.

## Objectives

By the end of this module, participants will be able to:

- Understand the differences and usage between main distributed computing architectures (HPC, Big Data, Cloud, CPU vs GPGPU)
- Implement the distribution of simple operations via the Map/Reduce principle in PySpark and Dask
- Understand the principle of Kubernetes
- Deploy a Big Data Processing Platform on the Cloud
- Implement the distribution of data wrangling/cleaning and training machine learning algorithms using PyData stack, Jupyter notebooks and Dask

## About us{background-image="images/HPC-blue.jpg" style="color:white"}

:::::::::::::: {.columns}
::: {.column width="50%"}

- Guillaume
- CNES (Centre National d'Etudes Spatiales - French Space Agency)
- Since 2016: 
  - 6 years in CNES Computing Center team
  - 1 year of holydays
  - 2 year in developping image processing tools
  - 7 years of using Dask/Python on HPC and in the Cloud
  - A bit of Kubernetes and Google Cloud
- Before that: 5 years on Hadoop and Spark
- Originally: Software developer (a lot of Java)

:::
::: {.column width="50%"}

- Hugues
- CNES (Centre National d'Etudes Spatiales - French Space Agency)
- Since 2020: 
  - Cloud specialist
  - Ground Segment Engineer
- Before that:
  - System Architect
  - 8 years as Software Enginner and Tech Lead (a lot of Java)
  - 6 years as System & Network Technician

:::
::::::::::::::

## First quizz

I'll try to propose some quizz to be sure you're following!

Let's try it.

What is this course module main subject?

- Answer A: Cloud computing
- Answer B: Data Distribution
- Answer C: Machine Learning

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_520) _Key: od_

# Program

## Big Data & Distributed Computing (3h)

- [Introduction to Big Data and its ecosystem (1h)](01_Introduction_Big_Data.html)
  - What is Big Data?
  - Legacy “Big Data” ecosystem
  - Big Data use cases
  - Big Data to Machine Learning
- [Big Data platforms, Hadoop & Beyond (1h30)](02_Big_Data_Platforms.html)
  - Hadoop, HDFS and MapReduce,
  - Datalakes, Data Pipelines
  - From HPC to Big Data to Cloud and High Performance Data Analytics 
  - BI vs Big Data
  - Hadoop legacy: Spark, Dask, Object Storage ...
- [Object Storage (30m)](14_ObjectStorage.html)

## Deployment & Intro to Kubernetes (3h)

- MLOps: deploying your model as a Web App 
- [Introduction to Orchestration](https://supaerodatascience.github.io/DE/slides/2_2b_orchestration.html)
- [Introduction to Kubernetes](12_OrchestrationKubernetes.html)

## Kubernetes hands on (3h)

- Zero to Jupyterhub: deploy a Jupyterhub on Kubernetes
- Deploy a Daskhub: a Dask enables Jupyterhub (for later use)

[Slides](13_Dask_On_Cloud.html)

## Python Dataprocessing and Spark hands on (3h)

- [The rise of the Python ecosystem for Data Processing (1h)](21_Python_Data_Processing.html)
  - Data Science programming languages
  - Pydata stack (Pandas, Numpy, Matlplotlib, Jupyter)
  - Distributed and sctientific processing (Dask, PySpark)
  - Data vizualisation (Seaborn, Plotly, Pyviz)
  - Machine and Deep Learning (Sickit Learn, TensorFlow, Pytorch)
  - Jupyter notebooks, Binder, Google Colab
- [Spark Introduction (30m)](03_Spark_Introduction.html)
- Play with MapReduce through Spark (Notebook on small datasets) (1.5h)

## Distributed Processing and Dask hands on (3h)

- [Manage large datasets(30m)](24_Large_Datasets.html)
- [Dask Introduction (30m)](22_Dask_Pangeo.html)
- Includes [Dask tutorial(2h)](https://github.com/dask/dask-tutorial).

## Evaluation: DaskHub, Dask preprocess, ML training (6h)

- [Evaluation introduction (1h)](30_Evaluation.html)
  - Subject presentation
  - Everyone should have a Daskhub cloud platform setup or Dask on local computer
  - Get the data
- Notebook with cell codes to fill or answers to give
  - Clean big amounts of data using Dask in the cloud or on a big computer
  - Train machine learning models in parallel (hyper parameter search)
  - Complete with yor own efforts!

## Quizz

What will we do today?

- Answer A: Explain what's Big Data
- Answer B: Dig into Cloud computing
- Answer C: Take a nap
- Answer D: Play with Kubernetes
- Answer E: Some Spark

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_4463) _Key: si_

