---
title: The rise of the Python ecosystem for Data Processing 
author: Guillaume Eynard-Bontemps and Emmanuelle Sarrazin, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2026
---

# Python scientific ecosystem{background-image=https://jupytearth.org/_images/python-stack.png}

# Core (Numpy, SciPy, Pandas ...)

## Numpy

:::::::::::::: {.columns}
::: {.column width="60%"}

- Manipulate N-dimensional arrays
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

![](https://docs.xarray.dev/en/stable/_static/Xarray_Logo_RGB_Final.svg){height=100px}

- Manipulate N-dimensional **labelled** arrays and **datasets**
- Introduce dimensions, coordinates and attributes on top of Numpy
- Borrows heavily from Pandas

:::
::: {.column width="60%"}

![](https://docs.xarray.dev/en/stable/_images/dataset-diagram.png)

:::
::::::::::::::

# Visualization

## Landscape

![Adaptation of Jake VanderPlas graphic about the Python visualization landscape, by Nicolas P. Rougier](images/Python-viz-landscape-colors.png){width=80%}


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

![](https://matplotlib.org/_static/logo_light.svg){height=100px}

![](https://matplotlib.org/stable/_images/sphx_glr_surface3d_001.png)

:::
::::::::::::::


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

- **HoloViews**: Declarative objects for instantly viewable data, building Bokeh plots from convenient high-level specifications
- **GeoViews**: Viewable geographic data that that can be mixed and matched with HoloViews objects
- **Panel**: Assembling objects from many different libraries into a layout or app, whether in a Jupyter notebook or in a standalone serveable dashboard
- **Datashader**: Rasterizing huge datasets quickly as fixed-size images
- **hvPlot**: Quickly return interactive HoloViews or GeoViews objects from your Pandas, Xarray, or other data structures
- **Param**: Declaring user-relevant parameters, making it simple to work with widgets inside and outside of a notebook context

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

![](images/ml_map.svg){width=60%}

## Pytorch

:::::::::::::: {.columns}
::: {.column width="50%"}

![](images/Pytorch_logo.png){height=100px}

- Deep Learning on GPU with no previous knowledge
- Additional libraries:
    * pytorch-lightning
    * pytorch3d
    * tensorboard
    * keras (>=3)

:::
::: {.column width="50%"}

![](https://www.tensorflow.org/tensorboard/images/tensorboard.gif){width=70%}

:::
::::::::::::::

## Pytorch

:::::::::::::: {.columns}
::: {.column width="50%"}

### High-level libraries

- **lightning**: Provides all the necessary features:
    * Fine-grained control of epochs and validation cycles
    * Optimizer and scheduler
    * Checkpointing, Tensorboard interface
    * Gradient clipping
    * Distributed learning
- **keras**: A high-level neural networks API written in Python which simplifies building and training deep learning models.

:::
::: {.column width="50%"}

### Hyperparameter tuning

- **Optima**
- **Raytune**


### Configuration management

- **hydra**: Framework for managing complex configurations in Python applications through YAML files. Can be used for machine learning experiments and scalable applications.


:::
::::::::::::::

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


# Others scientific libraries

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


## Shapely

:::::::::::::: {.columns}
::: {.column width="50%"}

- Library for manipulation and analysis of planar geometric objects

```python
import shapely
import numpy as np

geoms = np.array([Point(0, 0), Point(1, 1), Point(2, 2)])
polygon = shapely.box(0, 0, 2, 2)

shapely.contains(polygon, geoms)
```

:::
::: {.column width="50%"}

![](images/shapely.jpg){height=500px}

:::
::::::::::::::


## Pandas Extension

:::::::::::::: {.columns}
::: {.column width="50%"}

### [GeoPandas](https://geopandas.org/en/stable/index.html)

- For manipulating geospatial data in python easier
- Provide geospatial operations in pandas:
  - Measure areas and distances
  - Compute intersections/unions
  - Make maps and plots

![](images/geopandas.svg){height=300px}

:::
::: {.column width="50%"}

### [Text Extensions for Pandas](https://text-extensions-for-pandas.readthedocs.io/en/latest/)

- Add NLP-specific data types, operations, and library integrations to Pandas
- Make it easier to manipulate and analyze NLP-related data with Pandas

:::
::::::::::::::

## Xarray Extension

Like Pandas, there are xarray extensions like **rioxarray** which extends xarray with geospatial raster capabilities

# Development Tools

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

## VSCode

:::::::::::::: {.columns}
::: {.column width="50%"}

![](images/vscode_logo.png){height=100px}

- Source-code editor developed by Microsoft for Windows, Linux and macOS.
- Features include support for 
  - debugging, 
  - syntax highlighting, 
  - intelligent code completion, 
  - snippets, 
  - code refactoring, 
  - testing and 
  - embedded Git. 
- Lots of extensions that add functionality. 

:::
::: {.column width="50%"}

![](images/vscode_ihm.png)

:::
::::::::::::::

## PyCharm

:::::::::::::: {.columns}
::: {.column width="50%"}

![](images/pycharm_logo.png){height=100px}

- IDE used for programming in Python
- Cross-platform, working on Microsoft Windows, macOS and Linux
- Features include support for 
  - Code analysis, 
  - Graphical debugger, 
  - Integrated unit tester, 
  - Integration with version control systems

:::
::: {.column width="50%"}

![](images/pycharm_ihm.png)

:::
::::::::::::::

# Packaging

## Pip / Conda / Pixi

![](images/pypilogo.svg){height=100px}
![](images/conda_logo.svg){height=100px}
![](images/pixi_logo.png){height=100px}

- Package libraries
- Make them available on repositories
- Build environments automatically

## Packaging: Pip / Conda / Pixi

![](images/pypilogo.svg){height=100px}
![](images/conda_logo.svg){height=100px}
![](images/pixi_logo.png){height=100px}

Difference between Conda and Pip according to Anaconda.

|     | conda / pixi | pip |
|-----|-------|-----|
| manages | binaries | wheel or source |
| can require compilers | no | yes |
| package types | any | Python-only |
| create environment | yes, built-in | no, requires virtualenv or venv |
| dependency checks | yes | no |

# Others

## Code check

Python linters help to ensure that your code complies with coding standards, to identify potential errors, and to improve code readability

- **pylint**
- **ruff**
- **flake8**

## Code format

- **black** 
- **isort**
- **ruff**

## Type checker

### Why 

- to allow developers to optionally specify the types of variables and function signatures.
- to improve code readability and maintainability

### Examples

- **mypy**: static type checking
- **jaxtyping**: static type checking for tensors
- **typeguards**: dynamic type checking during test execution

## Test

### Why write tests

- To verify that the software works as intended
- To avoid non regressions,
- To improve quality of your code

### Test framework

- **pytest**
- **unittest**

# Exercises

## Tutorials

Clone [https://github.com/esarrazin/big-data-processing-course-tutorials](https://github.com/esarrazin/big-data-processing-course-tutorials)

Look at pandas and xarray tutorials

