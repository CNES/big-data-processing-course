---
title: Object Storage and Cloud Optimized Datasets
author: Guillaume Eynard-Bontemps, Hugues Larat, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2025
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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_7223) _Key: sl_

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

![Answer](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAAFACAIAAACJKdYDAAAG+klEQVR42u3d27LaOBAFUDzx///xlOeBqhQD+ALtllpmradUcjjIsrclSFd7WpblBvQz3263aZqud2DBm8v2nFS+c0XOZuqkBd/6klfp/cD/cR+CvoQQhBCEEBBCEEJACEEIASGE3zPv/kTZ6pBgCUVqBUbHspXIy4Nzsv3WqRM+9FVqJQTbURBCQAhBCAEhBCEEhBCEEGhsDr5+3DKISHlHamVJcMIjxxUseSnbBqb4VWolBNtREEJACEEIASEEIQSEEIQQaGz+2SMf9BFCqVVEwWdRjfsoKyshCCEghCCEgBCCEAJCCEIICCEIIdDO75atle22NO5RYyUEIQSEEIQQEEIQQkAIQQgBIYQhRCtmxu3e07ErUcd6mshRj3uui4/cSghCCEIICCEIISCEIISAEIIQAo3tV8zoLHK6SNlKx/Y2qW8dLGoZ+iq1EoIQghACQghCCAghCCEghCCEQGPTuI1DBp70QHnH7vnq2Dun41tbCQEhBCEEhBCEEBBCEEJACEEIASGEYcy3wk1yOj5CLHXkZY86WHeWOvK8LlLdG1hZCcF2FIQQEEIQQkAIQQgBIQQhBBqblmXJ68/TsRah8nO8cs9oZhepvLcOKlusc+SXWwnBdhSEEBBCEEJACEEIASEEIQQam2/DPrOqclFLx7KVvAMPFiGVndLUehorIdiOAkIIQggIIQghIIQghIAQghACz+bdnxj0wWmpx9Wx0KlyA6vUYr2yz8nT6AlsRwEhBCEEhBCEEBBCEEJACGE4+49Gi9gtgyhbjpN6XGU7a131gXAdq22OTJqVEGxHQQgBIQQhBIQQhBAQQhBCoLE5+PrUKorUXiwRqY1eUpWd0lQdK4GOXCpWQrAdBSEEhBCEEBBCEEJACEEIgcaiFTOVaxG2deyY0rGeJvXBSamu2o7ISgi2oyCEpgCEEIQQEEIQQkAIQQgBIYSfM/V9elleJVRqUVvHRk+Vn8p21UsltTuWRk9gOwpCaApACEEIASEEIQSEEIQQaG9O/e3BKoeOXYnKPr0sOLCOU9q3T1RkYNlFSFZCsB0FIQSEEIQQEEIQQkAIQQiBxqZlWSIFAR1buXSswEjtStLzaujXJGbQJ5+dMi1WQrAdBSEEhBCEEBBCEEJACEEIgcaiPWbGradJLccp2x0n8ssrt+0ZtETJSghCCAghCCEIISCEIISAEIIQAkIIvyhattax+Cu1UqlsTVxqj6lgEWLZmrjU44qfaysh2I6CEAJCCEIICCEIISCEIIRAY9FHo+389n7Pu+pbrFO21qfslI4rfjathGA7CkIICCEIISCEIISAEIIQAo3Nt8wCjsoPrCrbleTCc95r2Kn1T8HXLstiJQTbURBCQAhBCAEhBCEEhBCEEBBC+C37jZ4GlVqLNGinplvXerrU85V6XNmVgFZCsB0FIQSEEIQQEEIQQkAIQQiBxubdnyjbOCi1DCK1dqRjsU7qM9sGbWDV/Qq3EoLtKAghIIQghIAQghACQghCCDQ2B18/7lO+sp93lXTUHUt5dg8qMvLKjY6yK5yshGA7CkIICCEIISCEIISAEIIQAo3NpuALwVKevHqaVME6oas2K4pPmpUQbEdBCAEhBCEEhBCEEBBCEEJACOG3KFtLUfbhZ5G33h1Y5WZNvY5LoyewHQWEEIQQEEIQQkAIQQgBIYSCohUzZbv3pB5XsDQkMmnBbksdH2UXfO5a3si7T6mVEGxHQQgBIQQhBIQQhBAQQhBCoLH9iplBG4dcVeUSpUhNTOVKoGCtj5UQbEcBIQQhBIQQhBAQQhBCQAhBCIH/ma7aqQmshIAQghACQghCCAghCCGw6kh7iz9//7ws/5oyONd0Xwwf03VP3f1v1v782Xt8+8K394Lr3QhOmZ/s4b2d/O0bdPHjKrcdfZzNmoY+l9P0p/4Mb98gHm/Eu/80xBVV8TPh21n7O7/uaqn3l5oT+3TS17ZLT3slCTz/M+F318fG7vH0D5lPp/zg73wc4d9L6vVe8/Q3a4N/vew2lo7IRD0N9dM5DN5M3wZy494tYB+shOfO2uNG5e0uZW0PE3yv479zY4Rf7M2exvD0Efrxwn29dteu5t3N3hdz+PVKdd8KbbzKRumc7Wj3PUyzvdzGCD991drggzvM3ff6bg4/PeSDgZfA07aj9zWhwRbi3LdovOdZ++T8OnU1L8ovRvUY3fthbtxYiX4m/Ghv1vI6OL4Lyh7/2uBfP+k9XayXJIFFt6MbX5S9/a7ixNh8tCs7MsKDg//oKI788NpnzlOm6PhQt4chgaddt9v/WR/Pw+tXjsEvMzeWvrdfb0ZGeHzwa9+Obo9/+1Xb345+cb6++1764Mi3P6PK6tYMa2/xUzd1y1f1z4RcnvgV9B8NeOCjymp7zgAAAABJRU5ErkJggg==)

[Answer link](https://toreply.univ-lille.fr/reponse_621) _Key: kj_
