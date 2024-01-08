---
title: CNES Big Data Processing & Distribution Course
author: Guillaume Eynard-Bontemps, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2022-04-08
---

# Welcome

## Course Overview

- Big Data Processing & Distribution

Harnessing the complexity of large amounts of data is a challenge in itself. 

But Big Data processing is more than that: originally characterized by the 3 Vs of Volume, Velocity and Variety, 
the concepts popularized by Hadoop and Google require dedicated computing and storage solutions (both software and infrastructure), 
which will be explored in this module.

## Objectives

By the end of this module, participants will be able to:

- Understand the differences and usage between main distributed computing architectures (HPC, Big Data, Cloud, CPU vs GPGPU)
- Implement the distribution of simple operations via the Map/Reduce principle in PySpark
- Understand the principle of Kubernetes and object storage
- Deploy a Big Data Processing Platform (Pangeo) on the Cloud
- Either implement the distribution of data wrangling/cleaning and training machine learning algorithms using Dask
- Or implement a NDVI processing at scale using Pangeo platform.

## About myself{background-image="images/HPC-blue.jpg" style="color:white"}

- Guillaume Eynard-Bontemps
- CNES (Centre National d'Etudes Spatiales - French Space Agency)
- Since 2016: 
  - 6 years in CNES Computing Center team
  - Technical lead of the team
  - 3 years of using Dask/Python on HPC and in the Cloud
  - A bit of Kubernetes and Google Cloud
- Before that: 5 years on Hadoop and Spark
- Originally: Software developer (a lot of Java)

## First quizz

I'll try to propose some quizz to be sure you're following!

Let's try it.

What is this course module main subject?

- Answer A: Cloud computing
- Answer B: Data Distribution & Processing
- Answer C: Machine Learning

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_575) _Key: nf_

# Program

## Big Data & Distributed Computing (3.5h)

- [Introduction to Big Data and its ecosystem (45min)](01_Introduction_Big_Data.html)
  - What is Big Data?
  - Legacy “Big Data” ecosystem
  - Big Data use cases
  - Big Data to Machine Learning
- [Big Data platforms, Hadoop, HPC & Beyond (1h45min)](02_Big_Data_Platforms.html)
  - Hadoop, HDFS and MapReduce
  - Datalakes, Data Pipelines
  - HPC Platforms Architecture
  - From HPC to Big Data to Cloud and High Performance Data Analytics 
  - BI vs Big Data
  - Hadoop legacy: Spark, Dask, Object Storage ...
- [Spark](03_Spark_Introduction.html)
  - Spark Introduction (30min)
  - Exercise: Play with MapReduce through Spark (30min)

## Cloud, Kubernetes & Object stores (3.5h)

- [The Cloud in 30 minutes (30min)](10_Cloud_Computing.html)
  - What's the Cloud, Virtualization
  - Cloud history, layers, Engines
  - Usage revolution and new Data processing standard
- [Containers Orchestration (1h)](12_OrchestrationKubernetes.html)
  - Container orchestration and Kubernetes
  - Processing Platform over Kubernetes (Databricks, Coiled)
- [Object storage (30min)](14_ObjectStorage.html)
  - Object storage concepts: POSIX vs Object
  - Object storage architecture
  - Processing tools interfaces, Cloud Optimized files
- [Deploy a Data processing platform on the Cloud based on Kubernetes and Dask (1.5h)](13_Dask_On_Cloud.html)
  - Exercise: DaskHub or Dask Kubernetes or Pangeo

## Python ecosystem for data processing and Dask at scale (3.5h)

- [The rise of the Python ecosystem for Data Processing (1h)](21_Python_Data_Processing.html)
  - Data Science programming languages
  - Pydata stack (Pandas, Numpy, Matlplotlib, Jupyter)
  - Distributed and sctientific processing (Dask, PySpark)
  - Data vizualisation (Seaborn, Plotly, Pyviz)
  - Machine and Deep Learning (Sickit Learn, TensorFlow, Pytorch)
  - Jupyter notebooks, Binder, Google Colab
- [Dask Presentation (30min)](22_Dask_Pangeo.html)
- Dask/Pangeo practice:
  - Either play with Pangeo notebooks ([in the cloud](https://gallery.pangeo.io/) or [on HAL cluster](https://gitlab.cnes.fr/inno/pangeo-jupyter-demo)
  - [Or try to answer Supaero evaluation notebook!](30_Evaluation.html)

## Quizz

What will we do today (multiple choices)?

- Answer A: Explain what's Big Data
- Answer B: See what's Hadoop
- Answer C: Dig into Cloud computing
- Answer D: Take a nap
- Answer E: Some Spark

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_55) _Key: dy_

