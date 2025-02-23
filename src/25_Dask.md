---
title: Dask presentation and tutorials
author: Guillaume Eynard-Bontemps and Emmanuelle Sarrazin, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2025-02
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
