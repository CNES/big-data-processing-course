---
title: Big Data Platforms, Hadoop and beyond
author: Guillaume Eynard-Bontemps, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2020-11-15
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

![Answer]()

[Answer link](https://toreply.univ-lille.fr/reponse_187) _Key: gf_

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

![Answer]()

[Answer link](https://toreply.univ-lille.fr/reponse_49) _Key: td_

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

![Answer]()

[Answer link](https://toreply.univ-lille.fr/reponse_378) _Key: ep_

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

![Answer]()

[Answer link](https://toreply.univ-lille.fr/reponse_816) _Key: nv_

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

![Answer]()

[Answer link](https://toreply.univ-lille.fr/reponse_50) _Key: ex_

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

![Answer]()

[Answer link](https://toreply.univ-lille.fr/reponse_561) _Key: pc_
