---
title: Containers Orchestration, Kubernetes
author: Guillaume Eynard-Bontemps, Hugues Larat, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2026
---

# Credits and thanks

## Didn't do this

Thanks to [Florient Chouteau](mailto:florient.f.chouteau@airbus.com) and [Dennis Wilson](mailto:Dennis.WILSON@isae-supaero.fr)

for their work on this subject.

I took most of the content from theirs:

- [https://supaerodatascience.github.io/DE/slides/1_5_orchestration.html](https://supaerodatascience.github.io/DE/2_2_orchestration.html)
- [https://supaerodatascience.github.io/DE/slides/2_3_kubernetes.html#/](https://supaerodatascience.github.io/DE/2_2_orchestration.html)

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

![https://strawpoll.com/NPgxepmBrZ2](https://cdn.strawpoll.com/images/polls/qr/NPgxepmBrZ2.png)


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

![https://strawpoll.com/B2ZB9KPJpgJ](https://cdn.strawpoll.com/images/polls/qr/B2ZB9KPJpgJ.png)

# Kubernetes tutorial

## Try some

[https://training.play-with-kubernetes.com/kubernetes-workshop/](https://training.play-with-kubernetes.com/kubernetes-workshop/)

[https://labs.play-with-k8s.com/](https://labs.play-with-k8s.com/) with [Voting App](https://training.play-with-docker.com/swarm-stack-intro/)
