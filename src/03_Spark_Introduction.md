---
title: Spark Introduction
author: Guillaume Eynard-Bontemps, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2020-11-15
---

# Spark Introduction

## Spark History

- Research project at the [UC Berkeley AMPLab](https://amplab.cs.berkeley.edu/), started in 2009
- Open sourced in early 2010:
  - 2013: Moved to Apache Software Foundation
  - 2014: 1.0 release, top level Apache project
  - 2016: 2.0 release
  - 2020: 3.0 release
- Now with 100s of developers

## Spark goal and key features

From [Spark Research homepage](https://spark.apache.org/research.html):

> Our goal was to design a programming model that supports a **much wider class** of applications than MapReduce, while maintaining its automatic **fault tolerance**. 
> In particular, MapReduce is **inefficient for multi-pass applications** (...). 

- Iterative algorithms (many machine learning algorithms)
- Interactive data mining
- Streaming applications that maintain aggregate state over time

## Spark vs Map Reduce

![Difference between MapReduce and Spark (Knoldus)](https://i0.wp.com/blog.knoldus.com/wp-content/uploads/2018/10/Difference-between-MapReduce-and-Spark_A.jpg?w=700&ssl=1)

- MapReduce alternative which provides in memory processing (100x faster)
- A lot of other things, tools, higher level API

## Tools and ecosystem

:::::::::::::: {.columns}
::: {.column width="70%"}

![Spark stack (Databricks)](https://databricks.com/wp-content/uploads/2016/02/Spark-Stack-1024x474.png){width=60%}

![Spark sources (Databrick)](https://databricks.com/wp-content/uploads/2015/02/Introducing-DataFrames-in-Spark-for-Large-Scale-Data-Science1.png){width=60%}

:::
::: {.column width="30%"}

![](https://www.python.org/static/community_logos/python-logo-master-v3-TM.png){width=40%}

![](https://www.r-project.org/logo/Rlogo.png){width=30%}

![](https://www.scala-lang.org/files/archive/spec/2.11/public/images/scala-logo-red-spiral-dark.png){width=40%}

![](https://www.oracle.com/a/ocom/img/cb71-java-logo.png){width=40%}

:::
::::::::::::::

## Quizz

What are the main differences between Spark and Hadoop Map Reduce?

- Answer A: Spark uses another algorithm at the heart of its computing model
- Answer B: Spark can work on memory and is much faster
- Answer C: Spark has a better name
- Answer D: Spark provides many more APIs

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_530) _Key: hg_

## APIs

![](https://databricks.com/wp-content/uploads/2018/05/rdd.png)

## Resilient Distributed Dataset (RDD)

- Was primary user-facing API in Spark
- An RDD is an 
  - **immutable** 
  - **distributed** 
  - **collection** of elements of your data
- partitioned across nodes in your cluster
- operated in parallel with a low-level API
- Offers **transformations** and **actions**
- Unstructured datasets
- Functional programming constructs
- In memory, **fault tolerant**
- No schema, less optimization

## Dataframes and Datasets

:::::::::::::: {.columns}
::: {.column width="50%"}

- Also an immutable distributed collection of data
- Built on top of RDDs
- Structured data, organized in named columns
- Impose a structure, gives higher-level abstraction
- SQL like operations
- Dataset: strongly typed objects
- Catalyst optimizer, better performances

:::
::: {.column width="50%"}

![](https://databricks.com/wp-content/uploads/2016/06/Unified-Apache-Spark-2.0-API-1.png)

:::
::::::::::::::

## Transformations and Actions

:::::::::::::: {.columns}
::: {.column width="60%"}

### [Transformations](https://databricks.com/glossary/what-are-transformations)

- Create a new (immutable) dataset from an existing one
- Instruct Spark how you would like to modify the Data
- Narrow Dependencies: 1 to 1 input to output
- Wide Dependencies (shuffles, so MapReduce): 1 to N
- transformations in Spark are **lazy**
  - No computations
  - Just remember the transformations from input dataset

:::
::: {.column width="40%"}


### Actions

- Return a value to the driver program 
- After running a computation on the dataset

:::
::::::::::::::

## Transformations and Actions examples

:::::::::::::: {.columns}
::: {.column width="50%"}

### [Transformations](https://databricks.com/glossary/what-are-transformations)

| Transformations |
|---------|
| map* |
| filter |
| groupByKey |

:::
::: {.column width="50%"}

### Actions

| Actions |
|---------|
| reduce |
| collect |
| count |
| first |
| take |
| saveAs... |

:::
::::::::::::::


## Some code

```python
lines = sc.textFile("data.txt")
lineLengths = lines.map(lambda s: len(s))
totalLength = lineLengths.reduce(lambda a, b: a + b)
```

## Execution Plan and DAGS

:::::::::::::: {.columns}
::: {.column width="60%"}

```python
rdd1.map(splitlines).filter("ERROR")
rdd2.map(splitlines).groupBy(key)
rdd2.join(rdd1, key).take(10)
```

![](https://databricks.com/wp-content/uploads/2014/03/spark-devs1.png)

:::
::: {.column width="40%"}

- Job: each action triggers a job
- Stages:
  - Group of Narrow transformation
  - Can be processed in one go
  - **Shuffling** (Wide transformations) split stages
- Task: unitary transformation on a data chunk

:::
::::::::::::::

## Streaming

![](https://spark.apache.org/docs/latest/img/streaming-arch.png)

![](https://spark.apache.org/docs/latest/img/streaming-flow.png)

## MLLib

- Uses Dataframe API as inputs
- Pipeline made of
  - Transformers (analogy to transformation)
  - Estimator (can be actions)

![](https://spark.apache.org/docs/latest/img/ml-Pipeline.png){width=50%}

![](https://spark.apache.org/docs/latest/img/ml-PipelineModel.png){width=50%}

## Spark Application and execution

![](https://spark.apache.org/docs/latest/img/cluster-overview.png)
![](https://databricks.com/wp-content/uploads/2018/05/Spark-Applications.png)

## Dashboard

![Spark DAG](https://spark.apache.org/docs/3.0.0-preview/img/JobPageDetail2.png){width=20%}
![Spark stages details](https://spark.apache.org/docs/3.0.0-preview/img/AllStagesPageDetail3.png){width=70%}

## Dashboard 2

![Spark tasks](https://spark.apache.org/docs/3.0.0-preview/img/AllStagesPageDetail6.png){width=60%}

## Quizz

What's the main API of Spark?

- Answer A: MLLib
- Answer B: RDDs (Resilitent Distributed Datasets)
- Answer C: Datasets
- Answer D: Transformations

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_37) _Key: op_

# Play with Map Reduce through Spark 

## Context

- Interactive notebook (developed some years ago...)
- Pre-configured
- Warm up on [Py computation](https://www.geeksforgeeks.org/estimating-value-pi-using-monte-carlo/)

![](https://github.com/SupaeroDataScience/DE/blob/main/notebooks/Pi_30K.gif?raw=true){width=20%}

- RDDs
- Dataframes

## Notebook

[Notebook is here](https://github.com/CNES/big-data-processing-course/blob/main/notebooks/IntroductionToSpark.ipynb)

Easiest:

[Run it on Binder](https://mybinder.org/v2/gh/CNES/big-data-processing-course/main?urlpath=lab)
