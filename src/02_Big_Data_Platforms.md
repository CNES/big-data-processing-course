---
title: Big Data Platforms, Hadoop and beyond
author: Guillaume Eynard-Bontemps, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2025
---

# Hadoop

## Introduction

What is Hadoop?

Open source framework supported by Apache foundation:

- Store and process massive amount of data
- In a distributed way
- On "commodity" hardware (i.e. not expensive)
- Fault tolerant

## A complex ecosystem

:::::::::::::: {.columns}
::: {.column width="50%"}

![Hadoop ecosystem](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2016/10/HADOOP-ECOSYSTEM-Edureka.png){width=80%}

:::
::: {.column width="50%"}

Numerous Apache Software Foundation projects:

- Each covering a specific functionnality
- With their own developer community
- And their own development cycle

Hadoop distributions!

- Cloudera/Horthonworks (2018 fusion)
- MapR
- Others smaller

:::
::::::::::::::

## HDFS and MapReduce principles

### Two main components of Hadoop

- Distributed Software Defined Storage: HDFS (Hadoop Distributed File System)
![](https://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-hdfs/images/hdfs-logo.jpg){height=50px}
- Distributed Data Processing: MapReduce
![](https://www.pikpng.com/pngl/m/533-5331939_hadoop-apache-org-hadoop-map-reduce-logo-png.png){height=50px}

### Principles

- Split and store data on a cluster of servers (with local storage)
- Process data localy (on the server which owns it)
- Horizontal scalability: add or remove machines, on the fly, for compute or storage
- Fault tolerant

## Hadoop cluster components{background-image=https://pbs.twimg.com/media/EKzU0wMWsAAkKLc.jpg data-background-opacity=0.2}

- CLuster of "commodity" servers
- **Shared Nothing** architecture: only shared component is _standard_ network
- Each machine is a node which own both storage and compute

Each cluster is composed of:

- Master nodes: handle metadata and knowledge of the whole infrastructure
- Worker nodes: 
  - Host distributed pieces of data
  - Execute data processing algorithm parts

## Hadoop story, from google to Spark

![Hadoop history](images/Hadoop_Final.jpg){height=40%}

Spark first version in 2014.

## Quizz

What are the **two** building blocks of Hadoop ecosystem (multiple choices)?

- Answer A: Oozie
- Answer B: HDFS
- Answer C: Map Reduce
- Answer D: Servers

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_139) _Key: uw_

## Map Reduce exercise

[Learning Python](https://www.learnpython.org/en/Map%2C_Filter%2C_Reduce)

# HDFS 

## HDFS Basics

:::::::::::::: {.columns}
::: {.column width="50%"}

### Distributed File System

- Written in **Java**
- Allowing to **store** massive amounts of data, 
  - structured or not, 
  - on a cluster of machines
- Extensible and portable
- One of the first **Software Defined Storage** 
  - (OK, Google was here first)
- In HDFS, data are of **writen-once** type (no inline modifications)

:::
::: {.column width="50%"}

### Data blocks

- Data is **splitted** and **distributed**
  -  among the Hadoop cluster
- Splitted into 128MB (default) **blocks**
- With a **replication** factor for preventing data loss 
  - (3 replicas default)
- Hadoop 3: **Erasure coding**
  - similar or better durability as replication 3, 
  - but **only 50%** volume increase (can be less or more)
  - instead of 200%

:::
::::::::::::::

## HDFS blocks repartition

![](images/HDFSBlocks.png)

## HDFS Daemons

:::::::::::::: {.columns}
::: {.column width="60%"}

### Namenode

- Accountable for data locality and file system global namespace
- Daemon on a dedicated server
- Hosts metadata, create, remove, move files and folders
- Knows nodes wich own the parts of a file
- Needs to be replicated and secured (loss of metadata = loss of all data)

:::
::: {.column width="40%"}

### Datanode

- Stores and loads data blocks
- Daemon on every worker nodes
- Reading and writing of data
- Creation and Deletion of blocks

:::
::::::::::::::

## HDFS Architecture

![](https://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-hdfs/images/hdfsarchitecture.png)

## Quizz

What means HDFS?

- Answer A: Hadoop Distributed Functional Services
- Answer B: Hadoop Delayed File System
- Answer C: Hadoop Distributed File System
- Answer D: Hadoop Delayed Functional Services

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_539) _Key: vn_

# Map Reduce

## Map Reduce Basics

- **Functional** language concept
- Heavily used by Google for **WWW indexing**
- **Colocate** data and processing (with Hadoop and alikes)
- Automatic process **distribution** on pieces of data (eager distribution)
- Optimized for fast processing of **huge datasets**
- **Fault tolerant**: 
  - Data is replicated, 
  - Individual tasks can be restarted anywhere

## Wordcount (1. storage)

![](images/Wordcount1.png){style="background:white"}

## Wordcount (2. split)

![](images/Wordcount2.png){style="background:white"}

## Wordcount (3. map)

![](images/Wordcount3.png){style="background:white"}

## Wordcount (4. shuffle)

![](images/Wordcount4.png){style="background:white"}

## Wordcount (5. reduce)

![](images/Wordcount5.png){style="background:white"}

## Wordcount (6. result)

![](images/Wordcount6.png){style="background:white"}

## YaRN

- Yet Another Resource Negociator...
- Introduced in Hadoop v2
- Separation between
  - Resources scheduling and cluster state
  - Job execution and distribution

![](images/YARN.png){width=40%}
![](https://hadoop.apache.org/docs/stable/hadoop-yarn/hadoop-yarn-site/yarn_architecture.gif){width=40%}

## Quizz

What is the magical hidden step of distributed Map Reduce?

- Answer A: Map
- Answer B: Reduce
- Answer C: Shuffle
- Answer D: Split

![Answer](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAAFACAIAAACJKdYDAAAGyUlEQVR42u3d0a7aOhBAUdKT///jKn1AOqJAQmAy9jis9VT1FgiGTQzXcqZlWS5AP/Plcpmm6XxPLPjhsj0mlT+5Iq9m6qAFH/qU79LrE//jcwj6EiGIEEQIiBBECIgQRAiIEL7P/PJflF0dElxCkboCo+OylcjNg2Oy/dCpAz70u9SZEExHQYSACEGEgAhBhIAIQYRAY3Pw9uMug4gs70hdWRIc8MjzCi55KbsNTPF3qTMhmI6CCAERgggBEYIIARGCCIHG5q995oNeQih1FVHwWlTjXsrKmRBECIgQRAiIEEQIiBBECIgQRAi0873L1srutjTus8aZEEQIiBBECIgQRAiIEEQIiBCGEF0xM+7uPR13Jeq4nibyrMd9rYsfuTMhiBBECIgQRAiIEEQIiBBECDT2esWMnUUOF1m20nF7m9SHDi5qGfpd6kwIIgQRAiIEEQIiBBECIgQRAo1N424cMvCgB5Z3vHy9Ou6d0/GhnQkBEYIIARGCCAERgggBEYIIARHCMOZL4U1yOl5CLPXIyz7r4Lqz1CPP20Wq+wZWzoRgOgoiBEQIIgRECCIERAgiBBqbOu78E2TPosPHfNzrk5VdrLPnzp0JwXQURAiIEEQIiBBECIgQRAg0dto9ZoKXEAvquGwlbzVPcC+WskOaup7GmRBMRwERgggBEYIIARGCCAERggiBe9OyLB0XBGVfdOrzcam6RVXHIa28bVfHY7PRE5iOAiIEEQIiBBECIgQRAiKE4UypKxU67rZU+XmVvbLaWS8IV3wlkDMhmI6CCAERgggBEYIIARGCCIHGptTFH0Pv/BG5847DMuiBddR3syJ7zIDpKIjQEIAIQYSACEGEgAhBhEB7nfeYidz5ttTtbca9IFRE3z1mym5H5EwIpqOACEGEgAhBhIAIQYSACEGEwHvmS9cFXGWvxVV2YVrlq7J1v8ZY0mFHHtpGT2A6CogQRAiIEEQIiBBECIgQCpqDtw+uz8hbi9DxoYN3nnr1so6ro7rvp/TxgWUvQnImBNNRECEgQhAhIEIQISBCECHQ2LQsy6AXCat83bVR3w39Nokpe0G4bPaYAdNREKEhABGCCAERgggBEYIIgfZe7zFTdi+W1D1mxt3KJW/pSdkDuwy+hsmZEEQIIgRECCIERAgiBEQIIgRECN8l99JowZt3XDGXugyq4/OKDHjHC8KlvpE6DqkzIZiOAiIEEYIIARGCCAERggiBLubKB+fqZR88r8igpV6LLu+ws+88e1icCcF0FEQIiBBECIgQRAiIEEQINDaddWXJ62d+0tUhZV/QsgMeXIQU38DGmRBMR0GEgAhBhIAIQYSACEGEgAjhu8yX5FVUvVRejhdc6LTtlK/mpfBV9OK3dSYE01EQISBCECEgQhAhIEIQIdDY60ujDbpxUOrzCq6xSL3kmw2s6tyzMyGYjgIiBBECIgQRAiIEEQIihJrm4O3HvcpX2b1Yyu5A8/LliBx55a1xUgfNmRBMR0GEhgBECCIERAgiBEQIIgTamw3BU6nLVrKv8pMkuLPOWTcrig+aMyGYjoIIARGCCAERgggBEYIIARHCd7Fs7bngBcaytwbq8tCpz7qj7q+mMyGYjoIIARGCCAERgggBEYIIgcaiK2bK7t6T+rw6bvQU3G2p46XsOi5CKj6kzoRgOgoiBEQIIgRECCIERAgiBBp7vWJm0I1DUnVc3lF5iVJkTUzllUDBtT7OhGA6CogQRAiIEEQIiBBECIgQRAj8ZzrrTk3gTAiIEEQIiBBECIgQRAis2rO9xc/vn5flryGDY03Xk+FtXdfqrn+z9uf3HuPTGz79LDjfB8Eh49P4CG8/mm+tvZF4fSacpp/ig7Usf9deeJk1OPiN2J7+s3FfrJ7fCTfGepp+fKqlfr6UHdjPWlLgwd8JP3t/bMweD/+SefeS77zP2yP8/YhZm3f9/s3awT++7W7n8Bvnw3cH6u5Q3x3Ddz9MH5/FnrvdeSv+OxMeO2q/L8njHPL2Px3yiLd3uP8+N45w561uH+juGO6+Qt++NR/f/Ws9bA/U9evDu2N4d8Am2+Wmo0kvycZZ5ZAOP5jLbRzhUR/2wRnmy8f6bAzffcoKbD0dvZ4TGkwhMj6Gu/9K8Th0Nd+Xxx6VAo//TtjmF8jUj+Hs4187+MdvevV/cFbgaaejT78vbfxWcWA2b83K9hzhzoN/61ns+cdr3zkPGaJDBlyBR36cbf/P+ngPjz85Bn/M3Dj1Pf15M3KE+w9+7dfR7ePfvtX2r6MfvF4f/C69/avv9q9K9SfnVSK0vcVXfa47g1X/Tsjpya+gf5iWvK0BQduFAAAAAElFTkSuQmCC)

[Answer link](https://toreply.univ-lille.fr/reponse_171) _Key: nm_

# Datalakes

## Toward a new data management model

:::::::::::::: {.columns}
::: {.column width="50%"}

### Process centric

- Structured Data
- Internal sources
- Important data only
- Multiple copies

![](images/ProcessCentric.png){height=25%}

:::
::: {.column width="50%"}

### Data centric

- Multiple types (structured, semi-structured, unstructured)
- Multiple sources (internal, external)
- Everything
- One copy

![](images/DataCentric.png){height=25%}

:::
::::::::::::::

## Host and process different kind of data

![](images/Datalake1.png){width=60%}

## Typical Architecture

![Enterprise data lake reference architecture](images/AzureDatalake.png){width=80%}

## CNES Datalake infrastructure example

![](images/CNESDatalake.png){width=50%}

## Quizz

What is the goal of a Datalake?

- Answer A: Host structured and filtered Data
- Answer B: Host any kind of Data, at any stages of processing
- Answer C: Standardizing Data structure

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_2596) _Key: gj_

# Data pipelines and associated tools

## Data manipulation is complex

You won't usually achieve what you want with a single MapReduce or Spark job.

Let's say you want to train a ML model every time a text file is updated on a website and evaluate it next.

You'll need to:

::: incremental

- Periodically poll the website for new data
- Launch your model training when new text file is availaible
- Evaluate your new model on a reference dataset
- Push the evaluation result somewhere you can see it

:::

## Processing pipelines

This is called a Pipeline or a workflow.

It mainly means chaining tasks or jobs together to automatically produce a result from an input.

Tasks are typically either:

- Triggered based on a date, periodicity (like Linux crontab for those who knows).
- Triggered by an external event: data availability.
- Triggered by the end of the previous task or tasks.

It is usually represented by Direct Acyclic Graphs (DAGs).

## Example in Satellite ground segment

![Iota2 Pipeline](images/Iota2Pipeline.png)

## Some tools

![Airflow](images/demo_graph_view.png)

Plenty others from Apache or in Python ecosystem.

# HPC Platforms

## Overview and Use cases

:::::::::::::: {.columns}
::: {.column width="40%"}

> HPC = High Performance Computing

- HPC were built to solve compute bound problems
- Some early fields of research:
  - Weather forecasting
  - Atmospheric and climate research
  - Rockets and Aeronautics design
  - Computational Fluid Dynamics in general
- High performance infrastructure: compute, CPU, storage, Network

:::
::: {.column width="60%"}

<iframe src="https://player.vimeo.com/video/300943265?h=ef84e12ec0" width="640" height="362" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>
<p><a href="https://vimeo.com/300943265">Current speed in eNATL60 simulation with explicit tidal motion.</a> from <a href="https://vimeo.com/oceannumerique">Oc&eacute;an Num&eacute;rique</a> on <a href="https://vimeo.com">Vimeo</a>.</p>

- number of processors in parallel required: 18000
- Model time step: 40s
- Model integration speed: 45 minutes for 1 model day
- 40 million cpu-hour allocation

:::
::::::::::::::

## CNES typical use cases (1)

:::::::::::::: {.columns}
::: {.column width="50%"}

### R&D, Studies, upstream research

- Launchers (combustion, structure)
- Flight dynamics, orbitography
- Sensor data simulation
- Satellite structure and materials
- Technical domain: MPI, HTC, Big Data, AI

:::
::: {.column width="50%"}

![HPC Upstream](images/HPCUpstream.png)

:::
::::::::::::::

## CNES typical use cases (2)

:::::::::::::: {.columns}
::: {.column width="50%"}

![HPC production](images/HPCProduction.png)

:::
::: {.column width="50%"}

### Data production and diffusion

- Continuous data production (L0 --> L2)
- Data portals, catalogs
- Processing or reprocessing campains
- Technical Domain: HTC
- CNES Projects: SWOT, THEIA, SWH, SSALTO, PEPS

:::
::::::::::::::

## CNES typical use cases (3)

:::::::::::::: {.columns}
::: {.column width="50%"}

### Data analysis, dowstream research

- Scientific studies on data prodcuts
- Multi temporal or cross domain analysis
- EO or astronomical Data
- Technical Domain: HTC, Big Data, AI
- CNES labs or projects : CESBIO, LEGOS, AI4Geo, EOLab 

:::
::: {.column width="50%"}

![HPC downstream](images/HPCDownstream.png)

:::
::::::::::::::

## Architecture, big picture

![HPC Architecture](https://www.marquette.edu/high-performance-computing/images/architecture.png){width=50%}

Several things: Login nodes, Admin/Scheduler nodes, Compute resources, Parallel FS, RMDA Network

## Job scheduler

:::::::::::::: {.columns}
::: {.column width="50%"}

- Job Queuing System
- Job = Resources, Walltime, Queue, Account, etc.
- Resources management and scheduling
- Priority, fairshare partition, QoS
- SLURM, PBS, SGE, LSF, etc.

![HPC Scheduler](images/HPCScheduler.png)

:::
::: {.column width="50%"}

```bash
#!/bin/bash
#SBATCH --job-name=serial_job_test    # Job name
#SBATCH --ntasks=1                    # Run on a single CPU
#SBATCH --mem=1gb                     # Job memory request
#SBATCH --time=00:05:00               # Time limit hrs:min:sec
#SBATCH --output=serial_test_%j.log   # Standard output and error log

module load python

python /data/training/SLURM/plot_template.py
```

:::
::::::::::::::

## High Performance Storage

:::::::::::::: {.columns}
::: {.column width="50%"}

- POSIX file system
- Usually based on powerfull SAN storage infrastructure
- High performance and capacity: millions IO/s, hundreds GB/s, hundreds PB capacity.
- Spectrum Scale (GPFS) and Lustre
- Other players: WekaIO, BeeGFS

:::
::: {.column width="50%"}

![HAL GPFS](images/GPFSHALArchitecture.png){height=50%}

:::
::::::::::::::

## Software technologies

:::::::::::::: {.columns}
::: {.column width="60%"}

- Classical HPC: C and Fortran
  - Compiled languages, hardware optimized
  - MPI & OpenMP
  - CUDA, OpenACC
- More and More: Python, Julia
  - Interpreted Languages, easyer to use
  - Lots of performant libraries to reuse (e.g. Numpy, Scipy, Pandas, etc.)
  - Parallel and distributed computations:
    - Multiprocessing
    - MPI4Py : Python over MPI
    - Dask, Ray, etc.

:::
::: {.column width="40%"}

![MPI Code](images/mpimultistampede70pct.png)

:::
::::::::::::::

# From HPC to Big Data to Cloud and High Performance Data Analytics

## HPC platform, story and use case

:::::::::::::: {.columns}
::: {.column width="50%"}

> HPC = High Performance Computing

- Firsts HPC platforms built in the 1960s
- Mainly compute bounds algorithms
- At first for Weather forcasting and Aerodynamic research
- Structure modeling and fluid mecanics by discretization
- Needs (needed?) high performance hardware (network, CPUs, storage)
- Compute and storage are separated
- Uses a resource scheduler

:::
::: {.column width="50%"}

![Jean-Zay supercomputer](http://www.idris.fr/media/images/jean-zay-annonce-01.jpg?id=web%3Aeng%3Ajean-zay%3Acpu%3Ajean-zay-cpu-hw-eng)

:::
::::::::::::::

## TOP500

| Rank | System | Cores | Rmax (TFlop/s) | Rpeak (PFlop/s) | Power (kW) |
|------| -------|-------|----------------|-----------------|------------|
| 1 | Frontier - United States  | 8,699,904 | 1,194.00 | 1,679.82 | 22,703 |
| 2 | Aurora - United States | 4,742,808 	 | 585.34 | 1,059.33 | 24,687 |
| 4 | Supercomputer Fugaku - Japan | 7,630,848 | 442.01 | 537.21 | 29,899 |
| 5 | LUMI - Finland | 2,752,704 | 2379.70 | 531.51 | 7,107 |
| 17 | Adastra - France | 319,072 | 46.10 | 61.61 | 921 |
| 167 | Jean Zay - France | 93,960 | 4.48 | 7.35 | |

[Top 500 (november 2023)](https://top500.org/lists/top500/2023/11/)

## Big Data and Hadoop

- First platforms in the 2000's
- Mainly data bound algorithms
- Limitation in standard ethernet network performances = data locality
- At first for web indexing, or large amount of textual or tabular data analysis
- Web giant problem, then banking or IT stuf
- Use commodity hardware
- Compute and storage colocated

## HPDA convergence

![](images/HPDA.png){width=50%}

- Hadoop world step towards HPC: YaRN, equivalent to HPC resources scheduler
- HPC step towards Big Data: hardware not so specialized
- Hadoop big limitation: non standard File System and compute and storage colocation
- HPC big limitation: storage can be difficult to scale

## Cloud computing basics

Hence the cloud computing model...

- Compute resources separated from storage (but proximity is key)
- Can host anything, at first not compute oriented
- Object store model: Software Defined Storage as HDFS, specific interface (S3)
- Horizontal scalability of compute AND storage
- Resources on demand, mutualized between millions of users
- Infinite resources like for user

## Distributed programming: Hadoop vs HPC vs Cloud

:::::::::::::: {.columns}
::: {.column width="33%"}

### Hadoop

- Data bound algorithms
- Statistics
- Big volumes in input
- Often small outputs
- Can be used for computing problems, but not physical simulation

:::
::: {.column width="33%"}

### HPC (MPI)

- Compute bound algorithms
- Small or medium amount of inputs, 
- Medium or big outputs (big simulations)
- Can be used for data processing too (Dask)

:::
::: {.column width="33%"}

### Cloud

- Anything: services, storage bound, compute bound
- Object store limitations for some HPC workflow
- Or not anymore: HPC as a Service
- Big Data as a Service too...

:::
::::::::::::::

## Machine Learning Computations

### Machine learning

- Either lots of data in inputs
- Or lots of models to train (hyperparameter search)
- And of course data preprocessing
- Big Data or HPC or Cloud

### GPGPU

- Specific hardware (expensive)
- Really efficient for Deep Learning algorithms
- Image processing, Language processing

## Quizz

How Big Data processing differs from classical HPC (multiple choices)?

- Answer A: It is compute bound
- Answer B: It is data bound
- Answer C: It uses specialized hardware
- Answer D: It uses commodity hardware
- Answer E: It is fault tolerant

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_4356) _Key: fw_

# BI vs Big Data

## Business Intelligence

> Business intelligence (BI) comprises the strategies and technologies used by enterprises for the data analysis of business information.
>
> BI technologies provide historical, current, and predictive views of business operations. 

_Wikipedia_

Business Intelligence _can_ use Big Data ecosystems, but is more commonly considered something different.

[https://medium.com/doctolib/data-engineers-are-no-longer-data-folks-d10d44712580](https://medium.com/doctolib/data-engineers-are-no-longer-data-folks-d10d44712580)
[https://alphalyr.fr/blog/difference-bi-business-intelligence-big-data/](https://alphalyr.fr/blog/difference-bi-business-intelligence-big-data/)

## Classical BI key points

- Build data systems from Business questions
- KPI and business decisions oriented
- Data warehouse, mainframe = Big server with closed technology
- Use structured data, like SQL databases, 
- Oriented towards Data Value

## Big Data key points

- Find insights from the data systems, 
- KPI and business of course, but many more use cases
- Distributed architecture, lot of Open Source
- Different toolset (Hadoop, Python), 
- Every data flavor, keep anything!
- Data Volume, Variety, Velocity

# Hadoop and Big Data legacy

## Is Hadoop dead?

Not quite yet. Still **used in many places**

. . .

It grew up with **web giants**, producing a really rich and **open source** ecosystem

. . .

But clearly the two main components (HDFS and MapReduce) are now **deprecated**

. . .

And have paved the way to better alternatives

## Future of Big Data

Infrastructure: Private or public cloud, and HPC(DA) in some cases.

. . .

HDFS? Object Storage!

. . .

MapReduce? Spark, Dask.

. . .

Chunked file format (SequenceFile)? Parquet, Zarr, Cloud optimized Geotiff.

. . .

YaRN? HPC job scheduler, or Kubernetes

. . . 

### Cloud Computing

## Quizz

What technologies are replacing Hadoop ecosystem (multiple choices)?

- Answer A: Map Reduce
- Answer B: MPI (Message Passing Interface)
- Answer C: Spark
- Answer D: Cloud computing and object storage

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_748) _Key: qt_
