---
title: SDD DE Data Distribution Course
author: Guillaume Eynard-Bontemps, Hugues Larat, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2026-01
---

# Welcome

## Course Overview

- [Data Distribution & Big Data Processing](https://supaerodatascience.github.io/DE/2_1_overview.html)

Harnessing the complexity of large amounts of data is a challenge in itself. 

But Big Data processing is more than that: originally characterized by the 3 Vs of Volume, Velocity and Variety, 
the concepts popularized by Hadoop and Google require dedicated computing solutions (both software and infrastructure), 
which will be explored in this module. We'll also take a dive in new programming and infrastructure technologies
that emerged from these concepts.

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
  - 3 year in developping image processing tools
  - 8 years of using Dask/Python on HPC and in the Cloud
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

![Answer](https://cdn.strawpoll.com/images/polls/qr/poy9kxpQAgJ.png)

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

## Evaluation: DaskHub, Dask preprocess, ML training (3h + self paced)

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

![Answer](https://cdn.strawpoll.com/images/polls/qr/xVg71DedQyr.png)

[Answer link](https://strawpoll.com/xVg71DedQyr)

