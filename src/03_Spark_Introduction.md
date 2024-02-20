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

[Answer link](https://toreply.univ-lille.fr/reponse_102) _Key: rv_

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

[Answer link](https://toreply.univ-lille.fr/reponse_697) _Key: df_

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
