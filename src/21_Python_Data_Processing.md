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
![](images/stackoverflow_trends.svg){width=120%}

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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_549) _Key: pc_

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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_446) _Key: fp_

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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_558) _Key: dt_

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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_881) _Key: jf_

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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_491) _Key: hy_

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
