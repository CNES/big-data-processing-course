---
title: Dask presentation and tutorials
author: Guillaume Eynard-Bontemps and Emmanuelle Sarrazin, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2024-01
---

# Dask

## What Dask is for ?

- **Problem**: Python is powerful and user friendly but it doesn't scale well
- **Solution**: Dask enables to scale Python natively

## What is Dask ?


![](images/Dask-Logo-lockup-primary.png){height=100px}  
Python library for parallel and distributed computing

1. Scales Numpy, Pandas and Scikit-Learn 
2. General purpose computing/parallelization framework

## Why use Dask ?

- Allow to process data than is larger than available memory for a single machine
- Parallel execution for faster processing
- Distribute computation for large datasets

# How to use Dask ?

## Dask provides several APIs

- Dataframes
- Arrays
- Bags
- Delayed
- Futures

## Dataframes

:::::::::::::: {.columns}
::: {.column width="50%"}

- Extends Pandas library
- Enables to parallelize Pandas Dataframes operations
- Similar to Apache Spark

![](images/dask_dataframe.png)

:::
::: {.column width="50%"}


```python
import pandas as pd

df = pd.read_csv("file.csv")
result = df.groupby(df.name).amount.mean()
```


```python
import dask.dataframe as dd

df = dd.read_csv("file.csv")
result = df.groupby(df.name).amount.mean()

result = result.compute()  # Compute to get pandas result
```

:::
::::::::::::::


## Arrays

:::::::::::::: {.columns}
::: {.column width="50%"}

- Extends Numpy library
- Enables to parallelize Numpy array operations

![](images/dask_array.png)

:::
::: {.column width="50%"}

```python
import numpy as np

x = np.random.random((10000, 10000))
y = (x + x.T) - x.mean(axis=1)
```

```python
import dask.array as da

x = da.random.random((10000, 10000))
y = (x + x.T) - x.mean(axis=1)
```

:::
::::::::::::::


## Bags

:::::::::::::: {.columns}
::: {.column width="50%"}

- Allow to process in parallel Python lists, commonly used to process text or raw Python objects
- Offer map and reduce functionalities
- Similar to Spark RDDs or vanilla Python data structures and iterators

:::
::: {.column width="50%"}

```python
import dask.bag as db

# Read large datasets in parallel
lines = db.read_text("s3://mybucket/data.*.json")
records = (lines
    .map(json.loads)
    .filter(lambda d: d["value"] > 0)
)
df = records.to_dask_dataframe()
```

:::
::::::::::::::


## Delayed

:::::::::::::: {.columns}
::: {.column width="50%"}

- Allow to construct custom pipelines and workflows
- Enables to parallelize arbitrary for-loop style Python code
- Parallelize and distribute tasks 
- Lazy task scheduling
- Similar to Airflow

![](images/dask_task_2.png){width=60%}

:::
::: {.column width="50%"}

```python
from dask.distributed import LocalCluster
client = LocalCluster().get_client()

# Submit work to happen in parallel
results = []
for filename in filenames:
    data = client.submit(load, filename)
    result = client.submit(process, data)
    results.append(result)

# Gather results back to local computer
results = client.gather(results)
```

:::
::::::::::::::

## Futures

:::::::::::::: {.columns}
::: {.column width="50%"}

- Extends Python’s concurrent.futures interface for real-time 
- Allow to scale generic Python workflows across a Dask cluster with minimal code changes
- Immediate task scheduling 

:::
::: {.column width="50%"}

```python
from dask.distributed import LocalCluster
client = LocalCluster().get_client()
futures = client.map(score, x_values)

best = -1
for future in as_completed(futures):
   y = future.result()
   if y > best:
       best = y
```

:::
::::::::::::::


## Two levels of API

:::::::::::::: {.columns}
::: {.column width="50%"}

### High-level

- Parallel version of popular library 
- Scale Numpy, Pandas
- Similar to Spark

:::
::: {.column width="50%"}

### Low-level 

- Distributed real-time scheduling
- Scale custom workflows
- Similar to Airflow

:::
::::::::::::::


# How Dask works ?

## First, produce a task graph

![](images/dask_graph.png){width=70%}

High level collections are used to generate task graphs

## First, produce a task graph

Create an array of ones

```python
import dask.array as da

x = da.ones(15, chunks=(5,))
```
![](images/dask_graph_1.png){height=50%}

## First, produce a task graph

:::::::::::::: {.columns}
::: {.column width="40%"}

Sum that array
```python
import dask.array as da

x = da.ones(15, chunks=(5,))
y = sum()
```

:::
::: {.column width="60%"}

![](images/dask_graph_2.png){width=30%}

:::
::::::::::::::


## First, produce a task graph

Create an 2d-array of ones and sum it

```python
import dask.array as da

x = da.ones((15,15), chunks=(5,5))
y = x.sum()
```
![](images/dask_graph_3.png){width=30%}

## First, produce a task graph

Add array to its transpose

```python
import dask.array as da

x = da.ones((15,15), chunks=(5,5))
y = x +x.T
```
![](images/dask_graph_4.png){width=40%}

## First, produce a task graph

Matrix multiplication

```python
import dask.array as da

x = da.ones((15,15), chunks=(5,5))
y = da.ones((15,15), chunks=(5,5))
r = da.matmul(x,y)
```
![](images/dask_graph_5.png){width=80%}

## Dask graph

:::::::::::::: {.columns}
::: {.column width="40%"}

```python
import dask.array as da

x = da.ones((15,15), chunks=(5,5))
y = da.ones((15,15), chunks=(5,5))
r = da.matmul(x,y)
```

:::
::: {.column width="60%"}

```python
x
```

![](images/dask_graph_6.png)

:::
::::::::::::::

## Dask graph

- Every operations/tasks submit to Dask are turned to a graph
- Dask is lazily evaluated
- The real computation is performed by executing the graph

## Then, compute the calculation

Use `compute()` to execute the graph and get the result

![](images/dask_graph.gif){width=80%}

## Then, compute the calculation

:::::::::::::: {.columns}
::: {.column width="50%"}

### Compute() method

- The method allows to compute the result of a Dask collection or a Future object
- The method blocks until the computation is complete and returns the result.

:::
::: {.column width="50%"}

### Persist() method

- The method allows to persist the computation of a Dask collection or a Future object in the worker's memory. 
- This can be useful for large datasets that are used multiple times in a computation, as it avoids recomputing the same data multiple times. 

:::
::::::::::::::

# How to deploy ?

## Dask execution

- Task graphs can be executed by schedulers on a single machine or a cluster
- Dask offers several backend execution systems, resilience to failures

![](images/dask_scheduler.png){width=70%}


## Dask execution

![](images/dask_scheduler_2.png){width=70%}

## Dask execution


- **Client**: interacts with the Dask cluster, submits task
- **Scheduler**: is in charge of executing the Dask graph, sends task to the workers
- **Workers**: compute tasks as directed by the scheduler, store and serve computed results to other workers or clients

## Local execution

- Deploy Dask cluster on a single machine
- Configure to use threads or multiprocessing

```python
from dask.distributed import LocalCluster

cluster = LocalCluster()
client = cluster.get_client()
```

## Distributed execution

- Deploy Dask cluster on a distributed hardware
- Dask can work with:
  - popular HPC job submission systems like SLURM, PBS, SGE, LSF, Torque, Condor
  - Kubernetes

```python
from dask_kubernetes.operator import KubeCluster
cluster = KubeCluster(
   name="my-dask-cluster",
   image="ghcr.io/dask/dask:latest",
   resources={"requests": {"memory": "2Gi"}, "limits": {"memory": "64Gi"}},
)
cluster.scale(10)
client = cluster.get_client()
```

## Use Dashboard

:::::::::::::: {.columns}
::: {.column width="40%"}

  
   
- Help to understand the state of your workers
- Follow worker memory consumption
- Follow CPU Utilization
- Follow data Transfer between workers

:::
::: {.column width="60%"}

![](images/dashboard_status.png){width=90%}

:::
::::::::::::::

## Quizz

What Dask does better than Spark (multiple choices)?

- Answer A: Dataframes manipulation
- Answer B: N-dimensionnal Arrays manipulation
- Answer C: Low level parallelization
- Answer D: Scaling to Petabytes dataset
- Answer E: Reliability

![Answer](data:image/png;base64,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 jUAAAAAASUVORK5CYII=)

[Answer link](https://toreply.univ-lille.fr/reponse_334) _Key: tw_

# Dask and machine learning

## Scikit-learn/Joblib

:::::::::::::: {.columns}
::: {.column width="40%"}

```python
model = Model(...,n_jobs=n)
model.fit(X,y)
```
- User specify n_jobs
- Scikit-learn and joblib communicate
- Joblib uses threads and processes on a single machine
:::
::: {.column width="60%"}

![](images/scikit_learn_joblib.png)

:::
::::::::::::::

## Scikit-learn/Joblib/Dask

:::::::::::::: {.columns}
::: {.column width="40%"}

```python
from joblib import parallel_backend
model = Model(...,n_jobs=n)
with parallel_backend("dask"):
    model.fit(X,y)
```
- User specify n_jobs
- Scikit-learn and joblib communicate
- Joblib and Dask communicate
- Dask distributes jobs

:::
::: {.column width="60%"}

![](images/scikit_learn_joblib_dask.png)

:::
::::::::::::::

## Dask-ML

- Provides scalable machine learning alongside popular machine learning libraries
- Work with 
  - Scikit-Learn, 
  - XGBoost
  - PyTorch
  - Tensorflow/Keras

# How to install ?

## via pip

```python
python -m pip install "dask[complete]"    # Install everything
```

## Extras package

- Use Dask on queuing systems like PBS, Slurm, MOAB, SGE, LSF, and HTCondor.
```python
pip install dask-jobqueue
```
- Use Dask on Kubernetes
```python
pip install dask-kubernetes
```
- Use Dask with machine learning framework
```python
pip install dask-ml
```

# Try Dask 

## Dask Tutorial

[Dask tutorial](https://github.com/esarrazin/dask-tutorial)

Try to follow by order of importance:

- Dask Dataframes
- Distributed
- Delayed
- Parallel and Distributed Machine Learning
- Next, if you have more time
  - Array
  - Futures

## Pangeo tutorial or finish deploying your computing platform

[Just try some use cases here](https://gallery.pangeo.io/)

or

[Finish yesterday deployment](https://github.com/SupaeroDataScience/DE/blob/main/notebooks/Kubernetes_Daskhub.ipynb) 
(needed for tomorrow).

# References

## Dask presentations

[Just use the Dask slidedeck](https://docs.google.com/presentation/d/e/2PACX-1vSTH2kAR0DCR0nw8pFBe5kuYbOk3inZ9cQfZbzOIRjyzQoVaOoMfI2JONGBz-qsvG_P6g050ddHxSXT/pub?start=false&loop=false&delayms=60000#slide=id.p)
