---
title: Object Storage and Cloud Optimized Datasets
author: Guillaume Eynard-Bontemps, Hugues Larat, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2024-08-01
---

# Object Storage

## Object Storage concepts

> Object storage is a computer data storage that manages data as objects, as opposed to other storage architectures like file systems which manages data as a file hierarchy, and block storage which manages data as blocks within sectors and tracks. 
> Each object typically includes the data itself, a variable amount of metadata, and a globally unique identifier. (Wikipedia)

But Why?

- Scalability. Scale-out, infinitly. 
- Security/Reliability/Availability. Erasure Coding.
- Cost. Commodity hardware.
- Performance (bandwith). Just need good network, and scale.

## POSIX vs Object Storage

![](images/posix_vs_object.png)

## Object store Architecture

![](https://www.glennklockwood.com/data-intensive/storage/object-store-schematic.png)

## Ceph @CNES

![](images/Ceph-CNES.png)

## Quizz

What makes object storage efficient? (multiple choices)

- Answer A: The use of high-end and complex harware for storage solutions
- Answer B: The multiplication of standard servers with JBOD storage
- Answer C: High performance network
- Answer D: POSIX API
- Answer E: Dedicated API developed for simple transactions

![Answer]()

[Answer link](https://toreply.univ-lille.fr/reponse_214) _Key: mz_

# Processing and Cloud Optimized datasets

## Object storage interface and libraries

- Just HTTP Rest Calls: GET, PUT
- With authentification and authorizations: Access key and secret access key.
- Easier with AWS CLI or alike:

```bash
# Needs a keys file in your $HOME dir, or to dynamically obtain a key
aws s3 cp /tmp/foo/ s3://bucket/ --recursive --exclude "*" --include "*.jpg"
```

Interfaces and libraries for major programming languages:

- [Boto3 for Python](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html): not just S3, all AWS services
- Higher level for Python: [s3fs: Pythonic file interface for S3](https://s3fs.readthedocs.io/en/latest/)
- Other languages:
  - [Java SDK](https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/com/amazonaws/services/s3/AmazonS3.html)
  - [C++ SDK](https://aws.amazon.com/fr/sdk-for-cpp/)
- Other Object storage interfaces:
  - [Google Cloud Storage](https://cloud.google.com/storage/docs/reference/libraries)
  - [Azure Blob Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-directory-file-acl-python)

## Processing framework and Object store

All Major Data processing framework are compatible with S3 like interfaces.

- [Pandas dataframes](https://pandas.pydata.org/docs/user_guide/io.html)
- [Spark](https://spark.apache.org/docs/latest/cloud-integration.html)
- [Dask](https://docs.dask.org/en/stable/how-to/connect-to-remote-data.html)

Just replace */* or *file://* by *s3://*.

```python
import dask.dataframe as dd
df = dd.read_csv('s3://bucket/path/to/data-*.csv')
df = dd.read_parquet('gcs://bucket/path/to/data-*.parq')
```

More on the next part of the course.

## ARCO Data

**A**nalysis **R**eady **C**loud **O**ptimized Data.

Thanks to Ryan Abernathey.

:::::::::::::: {.columns}
::: {.column width="50%"}

What is Analysis Ready?

- Think in Datasets, not data files
- No need for tedious homogenizing, cleaning steps
- Curated and cataloged

:::
::: {.column width="50%"}

![How do data scientists spend their time (Crowdflower Data Science Report, 2016)](images/What-data-scientists-spend-the-most-time-doing-7.ppm.png)

:::
::::::::::::::

## ARCO Data (2)

**A**nalysis **R**eady **C**loud **O**ptimized Data.

Thanks to Ryan Abernathey.

:::::::::::::: {.columns}
::: {.column width="50%"}

What is Cloud Optimized?

- Compatible with object storage (access via HTTP)
- Support lazy access and intelligent subsetting
- Integrates with high-level analysis libraries and distributed frameworks

:::
::: {.column width="50%"}

![](images/ARCOData.png){width=60%}

:::
::::::::::::::

## Cloud Optimized Geotiff

:::::::::::::: {.columns}
::: {.column width="50%"}

- Metadata at the start of the file only
- Tiling instead of stripes (chunks)
- Compression
- Overviews (zoom out)
- HTTP range requests, and so object storage!

:::
::: {.column width="50%"}

![](https://staging.dev.element84.com/wp-content/uploads/2019/04/smiley_tiled.png)

:::
::::::::::::::

## Zarr

:::::::::::::: {.columns}
::: {.column width="30%"}

![](images/Zarr.png)

:::
::: {.column width="70%"}

- Python library for storage of chunked, compressed NDarrays
- Developed by Alistair Miles (Imperial) for genomics research (@alimanfoo)
- Arrays are split into user-defined chunks; each chunk is optional compressed (zlib, zstd, etc.)
- Can store arrays in memory, directories, zip files, or any python mutable mapping interface (dictionary)
- External libraries (s3fs, gcsf) provide a way to store directly into cloud object storage

:::
::::::::::::::

## Parquet

- Chunked binary file
- Compressed
- Metadata easily accessible

![](images/Parquet.png){width=60%}

## See more

<iframe width="560" height="315" src="https://www.youtube.com/embed/hprPIr9Vt4M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Quizz

Object storage is always performant for scientific data processing.

![Answer]()

[Answer link](https://toreply.univ-lille.fr/reponse_546) _Key: qp_
