---
title: Manage large datasets
author: Guillaume Eynard-Bontemps and Emmanuelle Sarrazin, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2025-02
---

# Introduction

## More and more data

Process ever larger and more numerous datasets

![](images/big_data_2.png){width=50%}  

<sub><sup>https://towardsdatascience.com/machine-learning-with-big-data-86bcb39f2f0b</sup></sub>

## More and more data

- More than 16 million text messages are sent every minute
- More than 100 million spam emails are sent every minute
- Every minute, there are more than a million tinder swipes
- Every day, more than a billion photos are uploaded to Google Photos

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
- Launched in 2023
- Data volume: 170 PB (6 years) i.e. 80 TB / day

:::
::::::::::::::

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
- Relies on schemas

## Zarr

![](images/zarr_logo.png)

- Free and open-source
- Array oriented file format
- File storage format for chunked, compressed, N-dimensional arrays
- Same performances than HDF5
- More flexible because chunking can be done along any dimension
- Cloud optimized


## Comparison 

|     | CSV | HDF5 | Parquet | Feather | Avro | Zarr |
|-----|-----|------|---------|---------|------|------|
| Format | Row | Array  | Column | Column | Row | Array |
| Writing | - - - | - - | + | +++ | ++ | + |
| File size | - - | - - - |  ++ | + | ++ | ++ | 
| Compression | no | no | +++ | + | + | +++ | 
| Reading | - - | - - - | ++ | +++ | +  | ++ |

## Dedicated format

- Best performances
- Optimized for one specific application or purpose
- For instance: 
  - TFRecord format
  - Cloud Optimized GeoTIFF: Optimize satellite images in cloud storage



## Choice of the file format

The optimum format depends on:  
  
- the type of data stored: same types or not
- the type of access: partial access or global access
- the usage: compatibility with the library or the application used


# Where to store large datasets ?

## Distributed data storage

- HDFS
- Object storage:
  - Amazon S3
  - Azure storage
  - Google Cloud Storage

# Pandas and large datasets

## Good pratices: Load less data

:::::::::::::: {.columns}
::: {.column width="50%"}

- Load only required columns for our processing

:::
::: {.column width="50%"}

```python
pd.read_parquet("timeseries_wide.parquet", columns=required_columns)
```

:::
::::::::::::::

## Good pratices: Use efficient datatypes

:::::::::::::: {.columns}
::: {.column width="50%"}

- Objective: Reduce memory foot-print
- Text data column is not memory efficient
- Use pandas.Categorical for categorical data
- Use pandas.numeric() to downcast the numeric columns to their smallest types 
- Use PyArrow data structure (available in Pandas 2)

:::
::: {.column width="50%"}

```python
ts2["name"] = ts2["name"].astype("category")
ts2["id"] = pd.to_numeric(ts2["id"], downcast="unsigned")
```

:::
::::::::::::::

## Good pratices: Use chunking

:::::::::::::: {.columns}
::: {.column width="50%"}

- Split a large problem into a bunch of small problems. 
- Each chunk must fits in memory

:::
::: {.column width="50%"}

```python
from more_itertools import sliced
CHUNK_SIZE = 5

index_slices = sliced(range(len(df)), CHUNK_SIZE)

for index_slice in index_slices:
    chunk = df.iloc[index_slice] # your dataframe chunk ready for use
```

:::
::::::::::::::

## Good pratices: Dask

- Use it only if needed, Pandas is often the best for dataset that fits in memory
- Dask includes dask.dataframe, a pandas-like API for working with larger than memory datasets in parallel. 
- Dask can use multiple threads or processes on a single machine, or a cluster of machines to process data in parallel.
- More information in the next course


# Xarray and large datasets

## Parallel commputing with Dask

- Xarray integrates with Dask to support parallel computations and streaming computation on datasets that don’t fit into memory
- Almost all of xarray’s built-in operations work on Dask arrays.
- If you want to use a function that isn’t wrapped by xarray, and have it applied in parallel on each block of your xarray object
- More information in the next course

# Large datasets and machine learning

## Good practices

- Stream data or use progressive loading: Read dataset in chunks with Pandas
- Optimize the datatype constraints
- Use parallelization for preprocessing the data : Vectorization or Multiprocessing
- Use incremental learning
- Use warm start
- Use distributed libraries
- Be careful with data shuffling: required random access, so comes at the expense of performance


# Tutorials

## Let's try

[Tutorial](https://github.com/esarrazin/large-dataset-cookbook)





