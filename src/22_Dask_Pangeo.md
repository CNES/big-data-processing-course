---
title: Dask presentation and tutorials
author: Guillaume Eynard-Bontemps, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2024-01
---

# Dask Presentation

![](images/Dask-Logo-lockup-primary.png){height=100px}

[Just use the Dask slidedeck](https://docs.google.com/presentation/d/e/2PACX-1vSTH2kAR0DCR0nw8pFBe5kuYbOk3inZ9cQfZbzOIRjyzQoVaOoMfI2JONGBz-qsvG_P6g050ddHxSXT/pub?start=false&loop=false&delayms=60000#slide=id.p)

# Quizz

What produces all dask API in the end?

- Answer A: Processes
- Answer B: Tasks
- Answer C: Tasks and associated graphs

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_797) _Key: eg_

# Dask Tutorial

[Just use the Dask tutorial in Binder](https://mybinder.org/v2/gh/dask/dask-tutorial/main?urlpath=lab)

Try to follow by order of importance:

- Dask Dataframes
- Distributed
- Parallel and Distributed Machine Learning
- Next, if you have more time
  - Array
  - Bag (this should remind RDDs of Spark)

# Pangeo tutorial or finish deploying your computing platform

[Just try some use cases here](https://gallery.pangeo.io/)

or

[Finish yesterday deployment](https://github.com/SupaeroDataScience/OBD/blob/master/notebooks/Kubernetes_Daskhub.ipynb) 
(needed for tomorrow).
