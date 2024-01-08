---
title: Containers Orchestration, Kubernetes
author: Guillaume Eynard-Bontemps, Hugues Larat, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2024-01-08
---

# Credits and thanks

## Didn't do this

Thanks to [Florient Chouteau](mailto:florient.f.chouteau@airbus.com) and [Dennis Wilson](mailto:Dennis.WILSON@isae-supaero.fr)

for their work on this subject.

I took most of the content from theirs:

- [https://supaerodatascience.github.io/DE/slides/1_5_orchestration.html](https://supaerodatascience.github.io/DE/slides/1_5_orchestration.html)
- [https://supaerodatascience.github.io/DE/slides/2_3_kubernetes.html#/](https://supaerodatascience.github.io/DE/slides/2_3_kubernetes.html#/)

# Kubernetes

## Why orchestration?

Suppose I have a large pool of machines available

* How do I **deploy my container**?
* How do I **put the right containers at the right spot**?
* How do I **scale (up and down) to demand**?
* How do I **expose the http endpoints**?
* How do I **manage failure of containers**?
* How do I **update my model without downtime**?

## Tools example

:::::::::::::: {.columns}
::: {.column width="40%"}

Examples...

- Docker Swarm
- CoreOS Fleet
- [Apache Mesos](https://mesos.apache.org/) / [Marathon](https://github.com/mesosphere/marathon)

... and so many more !

:::
::: {.column width="60%"}

![ecosystem](https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F996C7D4B5AF43B6C27)

:::
::::::::::::::

## Short Kubernetes history

Kubernetes (or k8s) comes from Google's internal systems [Borg](https://github.com/SupaeroDataScience/OBD/blob/master/readings/borg.pdf)

It is open source now <https://github.com/kubernetes> and used... everywhere ?

## Thanks to Dennis for the next part

[Slides](https://supaerodatascience.github.io/DE/slides/2_3_kubernetes.html#/)

## Quizz

What allows container orchestration (multiple choices)?

- Answer A: Auto scaling of services
- Answer B: Making coffee
- Answer C: Ensuring container states and availability
- Answer D: Submitting finite jobs

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_672) _Key: vp_


# Processing platform on Kubernetes

## Kubeflow

[https://www.kubeflow.org/](https://www.kubeflow.org/)

![kubeflow](https://miro.medium.com/max/2446/1*ZQsFV3o1c3Amu26Z-IEd7w.png){width=55%}

## Jupyterhub/Binder

![](https://miro.medium.com/max/1400/1*F_jJ1nDSQgBhrkbsEXB93Q.png){width=70%}

## Databricks: Spark as a Service

![](https://docs.gcp.databricks.com/_images/databricks-architecture-gcp.png){width=40%}

## Coiled: Dask as a Service

![](images/Coiled.png)

## Quizz

How do you deploy containers through Kubernetes (mutliple choices)?

- Answer A: docker run
- Answer B: Helm charts and command
- Answer C: yaml configuration and kubectl
- Answer D: custom bash script

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_761) _Key: gb_

# Kubernetes tutorial

## Try some

[https://training.play-with-kubernetes.com/kubernetes-workshop/](https://training.play-with-kubernetes.com/kubernetes-workshop/)

[https://labs.play-with-k8s.com/](https://labs.play-with-k8s.com/) with [Voting App](https://training.play-with-docker.com/swarm-stack-intro/)
