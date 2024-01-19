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

[Answer link](https://toreply.univ-lille.fr/reponse_541) _Key: bl_

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

```python
text_file = spark.sparkContext.textFile("some_words.txt")

counts = (
    text_file.flatMap(lambda line: line.split(" "))
    .map(lambda word: (word, 1))
    .reduceByKey(lambda a, b: a + b)
)

counts.collect()
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

[Answer link](https://toreply.univ-lille.fr/reponse_406) _Key: ns_

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
