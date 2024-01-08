---
title: SDD DE Data Distribution Course
author: Guillaume Eynard-Bontemps, Hugues Larat, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2024-01-08
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
  - 1 year in developping image processing tools
  - 6 years of using Dask/Python on HPC and in the Cloud
  - A bit of Kubernetes and Google Cloud
- Before that: 5 years on Hadoop and Spark
- Originally: Software developer (a lot of Java)

:::
::: {.column width="50%"}

- Hugues
- CNES (Centre National d'Etudes Spatiales - French Space Agency)
- Since 2020: 
  - Cloud specialist
- Before that: Cloud, Kubernetes

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

[Answer link](https://toreply.univ-lille.fr/reponse_185) _Key: aj_

# Program

## Deployment & Intro to Kubernetes (3h)

- MLOps: deploying your model as a Web App 
- Introduction to Orchestration
- Introduction to Kubernetes

## Kubernetes hands on (3h)

- Zero to Jupyterhub: deploy a Jupyterhub on Kubernetes
- Deploy a Daskhub: a Dask enables Jupyterhub (for later use)

## Big Data & Distributed Computing (3h)

- Introduction to Big Data and its ecosystem (1h)
  - What is Big Data?
  - Legacy “Big Data” ecosystem
  - Big Data use cases
  - Big Data to Machine Learning
- Big Data platforms, Hadoop & Beyond (2h)
  - Hadoop, HDFS and MapReduce,
  - Datalakes, Data Pipelines
  - From HPC to Big Data to Cloud and High Performance Data Analytics 
  - BI vs Big Data
  - Hadoop legacy: Spark, Dask, Object Storage ...

## Spark & Dask hands on (4h)

- Spark Introduction (30m)
- Play with MapReduce through Spark (Notebook on small datasets) (1.5h)
- Dask Introduction (30m)
- Dask tutorial (1.5h)

## Evaluation: DaskHub, Dask preprocess, ML training (6h)

- Evaluation introduction (1h)
  - Subject presentation
  - Everyone should have a Daskhub cloud platform setup
- Notebook with cell codes to fill or answers to give
  - Clean big amounts of data using Dask in the cloud
  - Train machine learning models in parallel (hyper parameter search)
  - Complete with yor own efforts!

## Quizz

What will we do today (multiple choices)?

- Answer A: Explain what's Big Data
- Answer C: Dig into Cloud computing
- Answer D: Take a nap
- Answer B: Play with Kubernetes
- Answer E: Some Spark

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_506) _Key: hx_

