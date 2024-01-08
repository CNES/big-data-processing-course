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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_256) _Key: jo_

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

[Answer link](https://toreply.univ-lille.fr/reponse_813) _Key: me_

# Map Reduce

## Map Reduce Basics

- **Functional** language concept
- Heavily used by Google for **WWW indexing**
- **Colocate** data and processing (with Hadoop and alikes)
- Automatic process **ditribution** on pieces of data (eager distribution)
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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_387) _Key: rs_

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

[Answer link](https://toreply.univ-lille.fr/reponse_729) _Key: tw_

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

[Answer link](https://toreply.univ-lille.fr/reponse_425) _Key: xf_

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

[Answer link](https://toreply.univ-lille.fr/reponse_722) _Key: ez_
