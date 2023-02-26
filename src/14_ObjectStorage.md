---
title: Object Storage and Cloud Optimized Datasets
author: Guillaume Eynard-Bontemps, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2022-04-26
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

![](images/posix_vs_storage.png)

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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_716) _Key: hl_

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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_35) _Key: rv_
