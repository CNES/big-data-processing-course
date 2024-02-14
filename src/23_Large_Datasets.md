---
title: Manage large datasets
author: Guillaume Eynard-Bontemps and Emmanuelle Sarrazin, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2024-01
---

# Introduction

## More and more data

Process ever larger and more numerous datasets

![](images/big_data.png){width=70%}


## Larger science catalogues

:::::::::::::: {.columns}
::: {.column width="50%"}

### GAIA

- Mission: create a 3D map of astronomical objects throughout the milky way 
- Data volume: 60TB (5 years) 
- Launched in 2013
- Number of objects in Gaia catalogues:
  - Version 1: 1,142,679,769
  - Version 2: 1,692,919,135
  - Version 3: 1,811,709,771

:::
::: {.column width="50%"}

### EUCLID

- Mission: Explore the composition and evolution of the dark Universe
- Launch in 2023
- Data volume: 170 PB (6 years) i.e. 80 TB / day

:::
::::::::::::::

## Larger datasets

- Training large deep neural networks required large datasets


# How to store the large datasets ?

## File formats

- Column oriented formats
- Record oriented formats
- Array oriented formats

## Advantages of column oriented format

- Stores values of each column in contiguous memory locations
- Facilitates efficient data analytics since queries can be made on subsets of columns without needing to load entire data records
- Improves compression because it is performed column by column, which enables different encoding schemes to be used for text and integer data. 

## Historical file format

- CSV: 
  - easy to use
  - human readable
  - plain text
- HDF5: 
  - designed to store and organize large amounts of data.
  - composed of groups of datasets, which are typed multidimensional arrays

## Apache parquet

![](images/parquet_logo.png)

- Free and open-source column-oriented data storage format
- Provides efficient data compression and encoding schemes
- Designed for long-term storage
- Can be use on distributed data storage
- Supported by an extensive software ecosystem with multiple frameworks and tools

## Feather

![](images/feather_logo.png)

- Free and open-source column-oriented data storage format
- More intended for short term or ephemeral storage 
- Support two fast compression libraries, LZ4 and ZSTD
- Can be use on distributed data storage
- Less popular than parquet so the number of supporting frameworks is much more limited

## AVRO

![](images/avro_logo.png)

- Free and open-source raw-oriented data storage format
- Not supported natively by pandas

## Zarr

![](images/zarr_logo.png)

- Free and open-source
- Array oriented file format
- File storage format for chunked, compressed, N-dimensional arrays
- Same performances than HDF5
- More flexible because chunking can be done along any dimension


## Comparison 

|     | CSV | HDF5 | Parquet | Feather | Avro | Zarr |
|-----|-----|------|---------|---------|------|------|
| Format | Row | Array  | Column | Column | Row | Array |
| Writing | --- | -- | + | +++ | ++ | + |
| File size | -- | --- |  ++ | + | | | 
| Compression | no | no | +++ | + | + | +++ | 
| Reading | -- | --- | ++ | +++ | +  | ++ |

## Dedicated format

- Best performances
- Optimized for one specific application or purpose
- For instance: 
  - TFRecord format
  - Cloud Optimized GeoTIFF: Optimze satellite images in cloud storage


## Choice of the file format

The optimum format depends on:  
  
- the type of data stored: same types or not
- the type of access: partial access or global access
- the usage: compatibility with the library or the application used


# Where to store large datasets ?

## Distributed data storage

- HDFS
- Amazon S3

# Pandas and large datasets

## Good pratices

- Limit to useful column
- Use efficient datatypes
- Chunking
- Use Dask


# Xarray and large datasets

# Large datasets and machine learning

## Good practices

- Data shuffling: required random access, so comes at the expense of performance
