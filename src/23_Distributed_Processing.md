---
title: Python for Distributed Processing 
author: Guillaume Eynard-Bontemps and Emmanuelle Sarrazin, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2025-02
---

# Parallel algorithm concepts

## Why parallelize an algorithm ?

- To speed-up the execution (execute several fragments of code at the same time/ reduce latcency) and/or to distribute the requested ressources or tasks on several cpu/machines
- You have to analyze our algorithm in order to know how parallelizable it is.
- Given problem, there may be different algorithms, which may be more or less parallelizable. 

## Why parallelize an algorithm ?

3 kinds of bottlenecks in an algorithm:  


- **CPU bound**: the time for executing a task is determined principally by the speed of the CPU
- **I/O bound**: the time for executing a task is determined principally by the period spent waiting for input/output operations to be completed
- **memory bound**: the time for executing a task is determined principally by the data access in memory 

## Several kind of problems

- **Embarrassingly parallel problems**: easy to divide up into pieces
- **Inherently serial problems**: problems that cannot be split up into parallel portions, as they require the results from a preceding step to effectively carry on with the next step 
- the rest of the problems fall in between...

## Additional challenge of parallelization

In addition to paying attention to the resources consumed in terms of memory and computing time, it is also necessary to take into account:  

- Latency / Communication between different processors: shared memory, message passing
- Load balance

## Granularity

**Granularity** of a task measures the amount of work (or computation) which is performed by that task

## Granularity 

 - **Fine-grained parallelism**: program is broken down to a large number of small tasks.
 - **Coarse-grained parallelism**: program is split into large tasks. 
 - **Medium-grained parallelism**: compromise between fine-grained and coarse-grained parallelism

## Granularity 

|     | Fine-grained | Coarse-grained |
|-----|-------|-----|
| Pros | Possibility to use a lot of ressources  | Low communication and synchronization overhead |
| Cons | Increases the communication and synchronization overhead | Risks of load imbalance |

## Scalability

A system is scalable if adding a resource reduces the computation time. 
You want to be able to reduce the runtime by a factor *N* when using *N* nodes.

## Data parallelism vs Task parallelism

- **Data parallelism**: focuses on distributing the data and process part of the data in parallel. 
Example process an array or a matrices by working on each element in parallel. 
- **Task parallelism**: focuses on distributing different tasks. Example process user requests on a database.

## Data parallelism

- Split data
- Distribute workload over the available CPU
- Coordinate workers
- Synchronize access to share resources
- Merge results

# How to parallelize ?

## On a single computer

- Use several CPU cores
- Solutions:
  - Multi-threading
  - Multi-processing

## Processes vs Threads

:::::::::::::: {.columns}
::: {.column width="50%"}

### Processes

- A process is an executing instance of a program
- A process has a self-contained execution environment. 
- A process generally has a complete, private set of basic run-time resources; in particular, each process has its own memory space.

:::
::: {.column width="50%"}

### Threads

- A thread is a subset of the process.
- A thread exists within a process — every process has at least one. 
- Threads share the process's resources, including memory and open files. This makes for efficient, but potentially problematic, communication.

:::
::::::::::::::

## Processes vs Threads

|     | Processes | Threads |
|-----|-------|-----|
| Pros | Little coordination or synchronization | Lighter, cheaper |
| Cons | High cost creation | Race condition, data corruption because of shared memory access |

## On several machines

Distributed computing  
  
- Cluster computing
- Cloud computing
- Grid computing

## On several machines

- Each processor has its own private memory (distributed memory). 
- Information is exchanged by passing messages between the processors.

# Distributed and parallel computing in Python

## Parallel computing with Python

 - Python packages including parallelization in their processings/methods
 - Python package dedicated to parallelization

## A word on Python Global Interpreter Lock

- The GIL can be seen as a mutex (or a lock) that allows only one thread to hold at a time the control of the Python interpreter.
- This means that only one thread can be in a state of execution at any point in time. 
- The GIL can be a performance bottleneck in CPU-bound and multi-threaded code.
- The GIL turns a multi-threaded program to a single threaded one

## Built-in threading

- Python core package
- To be avoided in CPython implementation due to Global Interpreter Lock 
- To be used only for dealing with I/O bound tasks

## Built-in mutliprocessing

- Python core package
- Spawning processes using an API similar to the threading module
- Effectively side-steps the **Global Interpreter Lock** by using subprocesses instead of threads

```python
from multiprocessing import Pool

def f(x):
    return x*x

with Pool(5) as p:
    print(p.map(f, [1, 2, 3]))
```


## Built-in multiprocessing

Exchanging objects between processes: Data serialization 
  
- Performed with pickle module: 
- Called by default to handle data transfer, when multiprocessing spawns a process
- Implied a time overhead which might offset the benefits of the parallelization
- Limited to types handled by pickle module 

## Built-in multiprocessing

Exchanging objects between processes:  

- Shared-memory: implies to deal with race condition and data corruption

```python
with SharedMemoryManager() as smm:
    sl = smm.ShareableList(range(2000))
    # Divide the work among two processes, storing partial results in sl
    p1 = Process(target=do_work, args=(sl, 0, 1000))
    p2 = Process(target=do_work, args=(sl, 1000, 2000))
    p1.start()
    p2.start()  # A multiprocessing.Pool might be more efficient
    p1.join()
    p2.join()   # Wait for all work to complete in both processes
    total_result = sum(sl)  # Consolidate the partial results now in sl
```

## Built-in multiprocessing

Synchronization between processes using Lock

```python
from multiprocessing import Process, Lock
def f(l, i):
    l.acquire()
    try:
        print('hello world', i)
    finally:
        l.release()

if __name__ == '__main__':
    lock = Lock()

    for num in range(10):
        Process(target=f, args=(lock, num)).start()
```

## Built-in concurrent.futures

:::::::::::::: {.columns}
::: {.column width="40%"}

- High-level interface for running concurrent tasks
- Abstraction for managing pool of threads or processes
- More limited interface than using directly multiprocessing module

:::
::: {.column width="60%"}

```python
from concurrent.futures import ProcessPoolExecutor as PoolExecutor
from functools import partial

def do_work(sleep_secs: float, i: int) -> str:
    time.sleep(sleep_secs)
    return f"foo-{i}"

if __name__ == "__main__":
    start_time = time.time()
    with PoolExecutor() as executor:
        results_gen = executor.map(partial(do_work, 3.0), range(1, 10))
```
:::
:::::::::::::: 


## Numpy threading

- To use threads in Python, you must use GIL immune library like numpy
- Numpy delegates thread execution to outside libraries like BLAS or Lapack
- NumPy functions run in parallel and use multiple threads, by default.
 
## Numba

:::::::::::::: {.columns}
::: {.column width="50%"}

![](https://numba.pydata.org/_static/numba-blue-horizontal-rgb.svg){height=100px}

> Numba makes Python code fast

- Translates Python functions to optimized machine code at runtime (Just In Time compilation)
- Use LLVM compiler library
- Python can approach the speeds of compiled languages like C or FORTRAN
- Just apply one of the Numba decorators

:::
::: {.column width="50%"}

```python
from numba import jit
import random

@jit(nopython=True)
def monte_carlo_pi(nsamples):
    acc = 0
    for i in range(nsamples):
        x = random.random()
        y = random.random()
        if (x ** 2 + y ** 2) < 1.0:
            acc += 1
    return 4.0 * acc / nsamples
```

:::
:::::::::::::: 

## Numba

:::::::::::::: {.columns}
::: {.column width="40%"}

- Just-in-time compilation implies that the code is compiled during the first call of the function
- JIT compilation takes time
- Numba caches the machine code version of the function for the particular types of arguments presented
- Useful if the function is called several times

:::
::: {.column width="60%"}


```python
from numba import jit
import numpy as np
import time

x = np.arange(100).reshape(10, 10)

@jit(nopython=True)
def go_fast(a): # Function is compiled and runs in machine code
    trace = 0.0
    for i in range(a.shape[0]):
        trace += np.tanh(a[i, i])
    return a + trace

> Elapsed (with compilation) = 0.33030009269714355s
> Elapsed (after compilation) = 6.67572021484375e-06s

```

:::
:::::::::::::: 

## Numba 

- Most use decorators: 
  - **@jit**
  - **@njit**:this is an alias for @jit(nopython=True) as it is so commonly used!
  - **@vectorize**: produces NumPy universal functions (which operates on scalar)
  - **@guvectorize**: produces NumPy generalized universal functions (which operates on on higher dimensional arrays and scalars)

- Extra options available in some decorators:
  - `parallel = True`: enable the automatic parallelization of the function.
  - `fastmath = True`: enable fast-math behaviour for the function.

## Joblib

:::::::::::::: {.columns}
::: {.column width="65%"}

![](images/joblib_logo.svg){height=100px}

- Set of tools to provide lightweight pipelining in Python
  - transparent disk-caching of functions and lazy re-evaluation (memoize pattern)
  - easy simple parallel computing
- Optimized to be fast and robust on large data 

:::
::: {.column width="35%"}

```python
from math import sqrt

from joblib import Parallel, delayed

Parallel(n_jobs=2)(delayed(sqrt)(i ** 2) for i in range(10))
[0.0, 1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0]
```

:::
::::::::::::::

## Dask

:::::::::::::: {.columns}
::: {.column width="65%"}

![](images/Dask-Logo-lockup-primary.png){height=100px}

- Provides advanced parallelism for analytics
- First designed as allowing to process datasets bigger than memory
- Now from local computer to clusters, to HPC or Cloud computing
- Scales Numpy and Pandas with same interfaces
- More low level APIs for distributing any algorithm
- More tomorrow

:::
::: {.column width="35%"}

![](https://docs.dask.org/en/latest/_images/dask-dataframe.svg){width=80%}

```python
import dask.dataframe as dd
df = dd.read_csv('2014-*.csv')
df.describe().compute()
```

:::
::::::::::::::

## PySpark

![](https://databricks.com/wp-content/uploads/2018/12/PySpark-1024x164.png){height=100px}

- Spark is Scala (JVM based), but for data scientists, provides Python and R interface
- This means some complexity and translation between languages

![](images/PySpark.jpg)


## Others

:::::::::::::: {.columns}
::: {.column width="50%"}

### [Ray](https://www.ray.io)

![](images/ray_header_logo.png){height=100px}

- Scale general Python apps
- And a lot of high-level libs oriented towards Machine and Deep Learning

:::
::: {.column width="50%"}

### [Vaex](https://vaex.io/docs/index.html)

![](https://user-images.githubusercontent.com/18574951/90343540-a1181f80-e011-11ea-8ff5-bb21e5fdc71c.png){height=100px}

- Lazy out-of-core Dataframes (similar to Pandas)
- Performance oriented on tabular datasets
- Vizualisation

:::
::::::::::::::

# Parallel and distributed machine learning

## How to use parallelization for machine learning tasks ?

- Distributed hyper-parameter optimization
- Distributed training of ensemble models
- Data-parallel training of deep learning models

## Parallelization with Scikit-learn

:::::::::::::: {.columns}
::: {.column width="50%"}

- Higher-level parallelism with joblib or Dask for hyper-parameter optimization
- Lower-level parallelism with OpenMP or NumPy and SciPy routines

:::
::: {.column width="50%"}

```python
from joblib import parallel_backend

with parallel_backend('threading', n_jobs=2):
    # Your scikit-learn code here
```

:::
::::::::::::::


## Parallelization with deep learning framework

- Data parallel training performed via processing multiple data batches across multiple devices simultaneously to achieve better performance. 
- Functionality available in PyTorch or TensorFlow: ensures each device gets a non-overlapping input batch, calculates gradients and simultaneously synchronizes with the others

## Parallelization with deep learning framework

:::::::::::::: {.columns}
::: {.column width="50%"}

- Parallelization for hyper-parameter optimization with Ray Tune

:::
::: {.column width="60%"}
![](images/raytune.png)

Population based training of neural networks (Deepmind)

:::
::::::::::::::

# Tutorials

## Let's try

[Parallel tutorials](https://github.com/esarrazin/parallel-cookbook)

