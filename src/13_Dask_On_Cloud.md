---
title: Deploy Data processing platform on the Cloud
author: Guillaume Eynard-Bontemps, Hugues Larat, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2024-01-08
---

# Zero to Jupyterhub

## Jupyterhub

![Jupyterhub for Kubernetes](https://zero-to-jupyterhub.readthedocs.io/en/latest/_static/logo.png)

> JupyterHub brings the power of notebooks to groups of users. It gives users access to computational environments and resources without burdening the users with installation and maintenance tasks. Users - including students, researchers, and data scientists - can get their work done in their own workspaces on shared resources which can be managed efficiently by system administrators.

> JupyterHub allows users to interact with a computing environment through a webpage. As most devices have access to a web browser, JupyterHub makes it is easy to provide and standardize the computing environment of a group of people (e.g., for a class of students or an analytics team).

## Hands on

Open your Google console, and let's deploy a Jupyterhub!

- [Zero to Jupyterhub documentation](https://zero-to-jupyterhub.readthedocs.io/en/latest/)
- [Google Kubernetes Engine Instruction](https://zero-to-jupyterhub.readthedocs.io/en/latest/google/step-zero-gcp.html) 

# Dask Hub

## Dask

- #1 Distributed processing tool in Python
- Distributed Dataframe and Arrays
- We'll see more of it in another class

## Pangeo

- Community of (geo)scientists and developers
- Tackling big data problems: analysing simulations or sensor data
- Providing recipes to build a Pangeo platform:
  - Jupyterhub
  - Dask
  - Xarray
  - on Kubernetes or HPC

## Hands on

We will focus on getting a data processing platform on the Cloud:

- Dask cluster running in Kubernetes, 
- With Pangeo libraries available,
- Which we will then use in the final evaluation.

[Documentation notebook](https://github.com/guillaumeeb/OBD/blob/master/notebooks/Kubernetes_Daskhub.ipynb)

This is the first part of you evaluation!
