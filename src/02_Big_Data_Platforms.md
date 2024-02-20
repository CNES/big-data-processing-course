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

[Answer link](https://toreply.univ-lille.fr/reponse_5859) _Key: cf_

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

[Answer link](https://toreply.univ-lille.fr/reponse_906) _Key: wl_

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

![Answer](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAAEsCAIAAAD2HxkiAAAG3klEQVR42u3d0ZLqKBQF0MmU///LzkNXWY4mkQTOAZK1nm71VYPELQQkLM/n8x+gn39VAfT1+PmIZVle/9ZsQnPLd7r+Uvf3l61/HzvG2Seufhdc74ugSf30Kuf3H9+/tX19H2gJl2UZvJqez+fq2RWzzLdQ8kepO39NuPMFtizLBT5GI3+/DF6xRxNI42vCc5+Pnd5j84vMj09D4Wu+l/D1FbPVuXr9Zavw35/I9z78z+5ceUV9FPVoHZ74Mv0+4tYbvM8VREhL+LNCz/W+vs/c+381OeL7C5a/5k4JC5/1fqCPMnxcQr8+gqst3tYHdL+i/i4fjtbhR4FDO9LnSnj37mjQ9c9Oq9LkDJ3oy+2U8Oiztgpf2cP8eaxzdVj5lg+dkbZn+S7d0b82IaGy2h4i+exuXTl/V92YfbDTg9sfTZzkRF0T5oxANjyFhePjCYX/vtK7wIf152xE2x6s7mjjM7d6+bE6VtEwNod6ZSUlLCz8oXdR8uCta84mVZTzPRVR+Ktafl65Vebhe8ixcjBzp+lbHd6sKWF54bdGR/fLv/+s/dHRE+erclx6vypKCs96xaqgW31ba5dGvybk8sRPSwjED8wAQghCCAghCCEghCCEgBCCEAJCCEIICCEIISCEIISAEIIQAkIII0m6x8yAN2Auv69HROHT7ipSXviICulbybOcIy0h6I6CEAJCCEIICCHcU8/b4A84TF9ZzrRx9q1tEmveUflrlj/9Jp8QLSHojgJCCEIICCEIIXDCcDv1pk0nVBapfOy+8jXL32b5a1YePaJIU39CtISgOwoIIQghIIQghMAJD1XQUN+FCJUzHJVvM+JAWkJACEEIASEEIQSEEC7MFMX/RNzwZ+olC+VHR0sIQggIIQghIIQghMAhw01R9B3+Lh/67zvxUD6V0nfFQ1otaQkBIQQhBIQQhBAQQphOzymKvnsUlxep8qZMEVtEzPLI631CtIQghIAQghACQghCCLSSNEUx9S/f0wbKp759U8QG4FpCQAhBCAEhBCEEhBAubBltaDjixkRp21CnHSiiktMmSCpPcdqcjZYQdEcBIQQhBIQQhBAIlTRFkXa7oVWVTy9/zYgKKX96ROH7HiiinANOe2gJQXcUhBAQQhBCQAjhnnquophlp4G+EySzLK3oW3VpkxlaQtAdBYQQhBAQQhBCoJWkvSgihpVnubfPgAsmIvaNmHrCSUsIuqOAEIIQAkIIQgjkW6YY6E/73f3Uj6yUtmSh70duwCJpCUF3FIQQEEIQQkAI4Z6GW0VR+ci+2zv3NfWW0ZUfm6lPnJYQhBCEEBBCEEJACOGehltFkTasHLEUYMBNGiJqKW1pxdSbYGsJQXcUEEIQQkAIQQiBfRNPUQw41pw2Jh6xQUXf0zHgjh1aQtAdBYQQhBAQQhBCINRwN3oa8DY+EUsWIjasnuXoleWsPEcDrrfQEoLuKAghIIQghIAQwj31XEXR95fvA654SNszI+0+UX1F3DxKSwi6o4AQghACQghCCLQyxxRFxG/ky6XNWwz4A/9Zpj1mmY3QEoLuKCCEIISAEIIQAi89b/QU8fSILQ1mmU6IqM+0TbAj6nOWxSJaQhBCEEJACEEIASGEe3qMVqCIoeq0mYO0eYuIOYbKwg84H2AvCkAIQQgBIQQhBIQQRtZziiJif+aIsea0p0fcumrALTciyjnL+hUtIQghIIQghIAQghACL0lTFGlbW6ctBZhl84MBZ3f63rZLSwgIIQghIIQghIAQwiBusV125dHLixTxNivrs++Ns/qu4ZhlvxAtIeiOghACQghCCAgh3FPP7bLLR5D73gWo8lf/EbW0apb7GkUsbkib3dESgu4oIIQghIAQghACrSyzjGsnVceNd0SYpUKmvu+WlhB0RwEhBCEEhBCEEHjpuYqir6l/d19ZydfbLjvtvGsJQXcUEEIQQkAIQQiBVh4dj502WJy26UXEgfrW54Dbelee4vKnu9ET6I4CQghCCAghCCEQ6jFagQYcpi8vZ8TEQ99KjnhHfSvEdtmAEIIQAkIIQggIIQzioQrepe3kfL31FhFHT9vKwioK0B0FhBCEEBBCEEIgnymKcGn3IIrYiyJiLiStnKtPtxcFIIQghIAQghACQgiDGG6KYuof+Je/Zt/tMSoXDVQeKK2WyllFAbqjgBCCEAJCCEII5Os5RTHgJg0DvqOI6YS0wvfdwXuWpRVaQtAdBSEEhBCEEBBCuKdlwPvegJYQEEIQQkAIQQgBIQQhBIQQhBAQQhBCQAhBCAEhBCEEhBCEEBBCEEJACEEIASEEIQSEEIQQEEIQQkAIQQgBIQQhBIQQhBAQQpjGf3gjpmiCEIGTAAAAAElFTkSuQmCC)

[Answer link](https://toreply.univ-lille.fr/reponse_415) _Key: ec_

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

[Answer link](https://toreply.univ-lille.fr/reponse_123) _Key: bp_

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

[Answer link](https://toreply.univ-lille.fr/reponse_23) _Key: zl_

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

[Answer link](https://toreply.univ-lille.fr/reponse_2208) _Key: mz_
