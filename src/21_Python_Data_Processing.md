---
title: The rise of the Python ecosystem for Data Processing 
author: Guillaume Eynard-Bontemps and Emmanuelle Sarrazin, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2022-03
---

# Data Science programming languages

## R

:::::::::::::: {.columns}
::: {.column width="50%"}

- Programming language and free software environment
- Open source
- Interactive
- Ecosystem
  - Statistical computing
  - Graphics, vizualisation
  - Data analysis

:::
::: {.column width="50%"}

![R Studio](https://www.rstudio.com/images/screenshots/rstudio-windows.png){width=80%}

:::
::::::::::::::

## Julia

:::::::::::::: {.columns}
::: {.column width="50%"}

![](https://julialang.org/assets/infra/lorenz.gif)

:::
::: {.column width="50%"}

- Fast: designed for high performance
- Open source
- Dynamically typed, interactive use
- Ecosystem
  - Scientific and parallel computing
  - Visualisation and plotting
  - Data science and machine learning


:::
::::::::::::::

## C/C++

- Static languages
- Not much visualization
- For under layers of use libraries
- Easy to interface with Python (Cython, pybind11)


## Java

- Static languages
- Not much visualization
- Not completely compatible with IEEE Standard 754 Floating Points Numbers

## Matlab and others

:::::::::::::: {.columns}
::: {.column width="50%"}

![](https://fr.mathworks.com/help/matlab/learn_matlab/desktop.png)

:::
::: {.column width="50%"}

Matlab (and equivalent Scilab)

- Interactive
- With IDE and plotting
- Closed, not reproducible
- For some researchers

:::
::::::::::::::

## Python

:::::::::::::: {.columns}
::: {.column width="50%"}

- Interpreted and so interactive language
- Really simple syntax (Code readability)
- General-purpose programming language
- Many, many (many) libraries
  - A lot of scientific ones!
- Ecosystem
  - Scientific and parallel computing
  - Visualisation and plotting
  - Machine Learning, Deep Learning
  - Web developement

:::
::: {.column width="50%"}

![](images/Python.png)

:::
::::::::::::::

## Python the most used language?

[comment]: # (https://insights.stackoverflow.com/trends)
![](images/stackoverflow_trends.svg){width=90%}

## Kaggle Languages Popularity

![](images/kaggle_survey_2022_languages.png)

## Kaggle IDE Popularity

![](images/kaggle_survey_2022_ide.png)

## Quizz

What is the most used language (in Data Science)?

- Answer A: R
- Answer B: Go
- Answer C: Python
- Answer D: Matlab

# Python scientific ecosystem{background-image=https://jupytearth.org/_images/python-stack.png}

# Core (Numpy, SciPy, Pandas ...)

## Numpy

:::::::::::::: {.columns}
::: {.column width="60%"}

- Manipulate N-dimensionnal arrays
- Numerical computing tools :
    - math functions
    - linear algebra
    - Fourier transform
    - random number capabilities
    - etc
- Performant: core is well-optimized C/C++ and Fortran code
- Easy and de facto standard syntax

> [Nearly every scientist working in Python draws on the power of NumPy](https://medium.com/@RRamya02/nearly-every-scientist-working-in-python-draws-on-the-power-of-numpy-6bdb2ce45c15)

:::
::: {.column width="40%"}

![](images/numpylogo.svg){height=100px}

```Python
# The standard way to import NumPy:
import numpy as np

# Create a 2-D array, set every second element in
# some rows and find max per row:

x = np.arange(15, dtype=np.int64).reshape(3, 5)
x[1:, ::2] = -99
x
array([[  0,   1,   2,   3,   4],
       [-99,   6, -99,   8, -99],
       [-99,  11, -99,  13, -99]])
x.max(axis=1)
array([ 4,  8, 13])

# Generate normally distributed random numbers:
rng = np.random.default_rng()
samples = rng.normal(size=2500)
```

:::
::::::::::::::

## Scipy

:::::::::::::: {.columns}
::: {.column width="40%"}

![](https://docs.scipy.org/doc/scipy/_static/logo.svg){height=100px}

- Use Numpy arrays as basic data structure
- Offer scientific functions :
  - Optimization
  - Interpolation
  - Signal processing
  - Linear algebra
  - Statistics
  - Image processing

:::
::: {.column width="60%"}

```python
import numpy as np
from scipy import linalg
import matplotlib.pyplot as plt
rng = np.random.default_rng()
xi = 0.1*np.arange(1,11)
yi = 5.0*np.exp(-xi) + 2.0*xi
zi = yi + 0.05 * np.max(yi) * rng.standard_normal(len(yi))
A = np.concatenate((np.exp(-xi)[:, np.newaxis], xi[:, np.newaxis]),axis=1)
c, resid, rank, sigma = linalg.lstsq(A, zi)
xi2 = np.arange(0.1,1.01,0.01)
yi2 = c[0]*np.exp(-xi2) + c[1]*xi2
```

![](images/scipy_curve.png)

:::
::::::::::::::

## Pandas

:::::::::::::: {.columns}
::: {.column width="50%"}

- Deal with Dataseries and Dataframes (e.g. tables)
- Data manipulation and analysis
   - Selection
   - Grouping
   - Merge
   - Statistics
   - Transformation
- Numerical tables and time series
- Extension to geospatial data with geopandas

:::
::: {.column width="50%"}

![](https://pandas.pydata.org/static/img/pandas.svg){height=100px}

![](images/pandas_io.svg)

```python
import pandas as pd
pd.read_csv('Myfile.csv')
pd.describe()
```

:::
::::::::::::::
 
## Xarray

:::::::::::::: {.columns}
::: {.column width="40%"}

![](http://xarray.pydata.org/en/stable/_static/dataset-diagram-logo.png){height=100px}

- Manipulate N-dimensionnal **labelled** arrays and **datasets**
- Introduce dimensions, coordinates and attributes on top of Numpy
- Borrows heavily from Pandas

:::
::: {.column width="60%"}

![](https://gdfa.ugr.es/python/climate_data/img/xarray2.png)

:::
::::::::::::::

## Sympy

:::::::::::::: {.columns}
::: {.column width="50%"}

![](https://www.sympy.org/static/images/logo.png){height=100px}

- Library for symbolic mathematics
- Simplification, Calculus, Solvers

```python
from sympy import symbols
x, y = symbols('x y')
expr = x + 2*y
```

:::
::: {.column width="50%"}

![](images/sympy.png){height=500px}

:::
::::::::::::::

## Matplotlib

:::::::::::::: {.columns}
::: {.column width="50%"}

- Base/Reference plotting library
- For Python and Numpy
- Static, animated, and interactive visualizations
- Designed to be as usable as MATLAB

```python
fig, ax = plt.subplots(subplot_kw={"projection": "3d"})

# Plot the surface.
surf = ax.plot_surface(X, Y, Z, cmap=cm.coolwarm,
                       linewidth=0, antialiased=False)

# Customize the z axis.
ax.set_zlim(-1.01, 1.01)
ax.zaxis.set_major_locator(LinearLocator(10))
# A StrMethodFormatter is used automatically
ax.zaxis.set_major_formatter('{x:.02f}')

# Add a color bar which maps values to colors.
fig.colorbar(surf, shrink=0.5, aspect=5)

plt.show()

```

:::
::: {.column width="50%"}

![](https://matplotlib.org/stable/_static/logo2_compressed.svg){height=100px}

![](https://matplotlib.org/stable/_images/sphx_glr_surface3d_001.png)

:::
::::::::::::::

## Jupyter (Lab and Notebook)

:::::::::::::: {.columns}
::: {.column width="50%"}

![](https://jupyter.org/assets/share.png){height=100px}

![](https://jupyterlab.readthedocs.io/en/1.2.x/_images/jupyterlab.png)

:::
::: {.column width="50%"}

- Open source web application
- Create and share documents that contain live code
- Equations, visualizations and narrative text
- Interactive programming and visualizing
- Usage: 
  - data cleaning and transformation, 
  - numerical simulation, 
  - statistical modeling, 
  - data visualization, 
  - machine learning
- Used by Google Colab or Kaggle

:::
::::::::::::::

## Quizz

Which tools allows manipulating tabular data?

- Answer A: Numpy
- Answer B: Xarray
- Answer C: Pandas
- Answer D: Jupyter

# Distributed and scientific computing

## Parallel computing

 - Thead vs processus
 - Race conditions, mutual exclusion, synchronization, and parallel slowdown
 - Fine-grained, coarse-grained, and embarrassing parallelism

## Classes of parallel computers

 - Multi-core computing
 - Symmetric multiprocessing
 - Distributed computing
    * Cluster computing
    * Cloud computing
    * Grid computing
 - Specialized parallel computers
    * General-purpose computing on graphics processing units (GPGPU)
    * Reconfigurable computing with field-programmable gate arrays (FPGA)
    * Application-specific integrated circuits
    * Vector processors

## Parallel computing with Python

 - Python packages including parallelization in their processings/methods
 - Python package dedicated to parallelization

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

## Dask

:::::::::::::: {.columns}
::: {.column width="65%"}

![](images/Dask-Logo-lockup-primary.png){height=100px}

- Provides advanced parallelism for analytics
- First designed as allowing to process datasets bigger than memory
- Now from local computer to clusters, to HPC or Cloud computing
- Scales Numpy and Pandas with same interfaces
- More low level APIs for distributing any algorithm
- More this afternoon

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

## Quizz

What Dask does better than Spark (multiple choices)?

- Answer A: Dataframes manipulation
- Answer B: N-dimensionnal Arrays manipulation
- Answer C: Low level parallelization
- Answer D: Scaling to Petabytes dataset
- Answer E: Reliability


# Vizualisation (other than Matplotlib)

## Landscape

![Adaptation of Jake VanderPlas graphic about the Python visualization landscape, by Nicolas P. Rougier](images/Python-viz-landscape-colors.png){width=80%}

## Seaborn

![](https://seaborn.pydata.org/_images/logo-wide-lightbg.svg){height=100px}

- Based on Matplotlib
- Integrates closely with Pandas
- Dataset oriented to produce informative plots

![](https://seaborn.pydata.org/_images/faceted_lineplot.png)

## Plotly

:::::::::::::: {.columns}
::: {.column width="35%"}

![](images/Plotly-logo-01-square.png){height=100px}

- Interactive, publication-quality graphs
- Make dashboard with Dash

:::
::: {.column width="65%"}

![](https://raw.githubusercontent.com/cldougl/plot_images/add_r_img/anim.gif)

:::
::::::::::::::

## Bokeh

:::::::::::::: {.columns}
::: {.column width="35%"}

![](http://static.bokeh.org/og/logotype-on-hex.png){height=80px}

- Interactive, publication-quality graphs
- Make dashboard with Dash

:::
::: {.column width="65%"}

![](images/bokeh_plot.png){width=60%}

:::
::::::::::::::

## Pyviz

![](https://pyviz.org/_static/logo.png){height=100px}

- **HoloViews**: Declarative objects for instantly visualizable data, building Bokeh plots from convenient high-level specifications
- **GeoViews**: Visualizable geographic data that that can be mixed and matched with HoloViews objects
- **Panel**: Assembling objects from many different libraries into a layout or app, whether in a Jupyter notebook or in a standalone serveable dashboard
- **Datashader**: Rasterizing huge datasets quickly as fixed-size images
- **hvPlot**: Quickly return interactive HoloViews or GeoViews objects from your Pandas, Xarray, or other data structures
- **Param**: Declaring user-relevant parameters, making it simple to work with widgets inside and outside of a notebook context

## Quizz

Matlplotlib is the only vizualisation library for Python.


# Machine and Deep Learning

## Kaggle stats

![Machine Learning Frameworks usage](images/KaggleFrameworkUsage.png)

## Sickit Learn

![](https://scikit-learn.org/stable/_images/scikit-learn-logo-notext.png){height=100px}

- Simple and efficient tools for predictive data analysis
- Built on NumPy, SciPy, and matplotlib
- Every classical ML Algorithms
- Standard interface with Pipelines, estimators, transformers
- No GPU support (so not good for Deep Learning)

```python
from sklearn.ensemble import RandomForestClassifier
clf = RandomForestClassifier(random_state=0)
X = [[ 1,  2,  3],  # 2 samples, 3 features
     [11, 12, 13]]
y = [0, 1]  # classes of each sample
clf.fit(X, y)
```

## Sickit Learn

![](https://scikit-learn.org/stable/_static/ml_map.png){width=70%}

## TensorFlow, Keras

:::::::::::::: {.columns}
::: {.column width="50%"}

![](https://camo.githubusercontent.com/906e661107a3bc03104ca5d88336d1f4b0e80fdcac65efaf7904041d371c747f/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6b657261732e696f2f696d672f6b657261732d6c6f676f2d323031382d6c617267652d313230302e706e67){height=100px}
![](https://camo.githubusercontent.com/aeb4f612bd9b40d81c62fcbebd6db44a5d4344b8b962be0138817e18c9c06963/68747470733a2f2f7777772e74656e736f72666c6f772e6f72672f696d616765732f74665f6c6f676f5f686f72697a6f6e74616c2e706e67){height=100px}

- Deep Learning on GPU with no previous knowledge
- Keras on top of Tensorflow
- Tensorflow complete platform, with TensorBoard and other tools

:::
::: {.column width="50%"}

![](https://www.tensorflow.org/tensorboard/images/tensorboard.gif){width=60%}

:::
::::::::::::::

## Pytorch

![](images/Pytorch_logo.png){height=100px}

- Deep Learning on GPU with no previous knowledge
- Always trolls about Keras/TF vs PyTorch
- Additional librairies:
    * pytorch-lightning
    * pytorch3d

## Gradient boosting algorithms

:::::::::::::: {.columns}
::: {.column width="50%"}

### [XGBoost](https://xgboost.readthedocs.io/en/latest/)

- Distributed gradient boosting library
- Efficient, flexible and portable
- XGBoost provides a parallel tree boosting
- Runs on major distributed environment (Hadoop, SGE, MPI, Spark)
- Solve problems beyond billions of examples

![](https://raw.githubusercontent.com/dmlc/dmlc.github.io/master/img/logo-m/xgboost.png){height=100px}

:::
::: {.column width="50%"}

### [LighGBM](https://lightgbm.readthedocs.io/en/latest/)

- Distributed gradient boosting framework
- Efficient, Faster, lower memory usage, better accuracy
- Support of parallel, distributed, and GPU learning
- Capable of handling large-scale data

![](https://lightgbm.readthedocs.io/en/latest/_images/LightGBM_logo_black_text.svg){height=100px}

:::
::::::::::::::

## Data Version Control

:::::::::::::: {.columns}
::: {.column width="50%"}

![](images/dvclogo.png){height=100px}

:::
::: {.column width="50%"}

![](images/dvcgraphic.png){width=80%}

:::
::::::::::::::

 - Version your data and models: Store them in your cloud storage but keep their version info in your Git repo.
 - Track experiments in your local Git repo (no servers needed).
 - Share experiments and automatically reproduce anyone's experiment.

## MLFlow

![](images/MLflow-logo-final-black.png){height=100px}

- Tracking experiments to record and compare parameters and results (MLflow Tracking).
- Packaging ML code in a reusable, reproducible form in order to share with other data scientists or transfer to production (MLflow Projects).
- Managing and deploying models from a variety of ML libraries to a variety of model serving and inference platforms (MLflow Models).
- Providing a central model store to collaboratively manage the full lifecycle of an MLflow Model, including model versioning, stage transitions, and annotations (MLflow Model Registry).

## MLFlow

![](images/mlflow_tracking.jpeg)

## Quizz

Which is the best Deep Learning library in Python?

- Answer A: Sickit-Learn
- Answer B: Keras
- Answer C: TensorFlow
- Answer D: PyTorch
- Answer E: XGBoost


# Others

## Packaging: Pip / Conda

![](images/pypilogo.svg){height=100px}
![](images/conda_logo.svg){height=100px}

- Package libraries
- Make them available on repositories
- Build environments automatically

## Packaging: Pip / Conda

![](images/pypilogo.svg){height=100px}
![](images/conda_logo.svg){height=100px}

Difference between Conda and Pip according to Anaconda.

|     | conda | pip |
|-----|-------|-----|
| manages | binaries | wheel or source |
| can require compilers | no | yes |
| package types | any | Python-only |
| create environment | yes, built-in | no, requires virtualenv or venv |
| dependency checks | yes | no |

## Numba

:::::::::::::: {.columns}
::: {.column width="50%"}

![](https://numba.pydata.org/_static/numba-blue-horizontal-rgb.svg){height=100px}

> Numba makes Python code fast

- Translates Python functions to optimized machine code at runtime
- Use LLVM compiler library
- Python can approach the speeds of C or FORTRAN
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

## Binder

![](https://mybinder.org/static/logo.svg?v=fe52c40adc69454ba7536393f76ebd715e5fb75f5feafe16a27c47483eabf3311c14ed9fda905c49915d6dbf369ae68fb855a40dd05489a7b9542a9ee532e92b)

> Turn a Git repo into a collection of interactive notebooks

![](https://binderhub.readthedocs.io/en/latest/_images/architecture.png)

# Exercise

## Pandas tutorial

[Let's try Pandas in Binder](https://github.com/jvns/pandas-cookbook)

Follow this first tutorial at least till chapter 6. Use the binder button!

[Pandas & Scikit-learn](https://github.com/INRIA/scikit-learn-mooc/)

If you have time, go through part "The predictive modeling pipeline". Notebook 01 to 03. With Binder too.
