---
title: Containers and Docker
author: Guillaume Eynard-Bontemps, Hugues Larat, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2024-01-08
---

# Credits and thanks

## Didn't do this

Thanks to [Florient Chouteau](mailto:florient.f.chouteau@airbus.com) and [Dennis Wilson](mailto:Dennis.WILSON@isae-supaero.fr)

for their work on this subject.

I took most of the content from theirs:

- [https://supaerodatascience.github.io/DE/slides/1_4_containers.html](https://supaerodatascience.github.io/DE/slides/1_4_containers.html)
- [https://supaerodatascience.github.io/DE/slides/1_5_orchestration.html](https://supaerodatascience.github.io/DE/slides/1_5_orchestration.html)
- [https://supaerodatascience.github.io/DE/slides/2_3_kubernetes.html#/](https://supaerodatascience.github.io/DE/slides/2_3_kubernetes.html#/)

# Containers

## Why containers?

- How to get software to run reliably when moved from one computing environment to another
  - from a developer's laptop to a test environment
  - from staging to prod
  - from a Cloud provider to another
- Packaging application + runtime as a single package
- Abstract differences in OS and underlying hardware
- Build once, run anywhere
- Pet vs Cattle, at another level

## Container vs VM

![](https://images.contentstack.io/v3/assets/blt300387d93dabf50e/bltb6200bc085503718/5e1f209a63d1b6503160c6d5/containers-vs-virtual-machines.jpg){width=50%}

## Container vs VM: similarities and drawbacks

:::::::::::::: {.columns}
::: {.column width="30%"}

### Similarities

* Isolated environments for applications
* Movable between hosts

:::
::: {.column width="35%"}

### VM Drawbacks

* VM Contains full OS at each install => Install + Resource overhead
* VM needs pre-allocation of resource for each VM (=> Waste if not used)
* Communication between VM <=> Communication between computers

:::
::: {.column width="35%"}

### Containers Drawbacks

* Containers are Linux based (but still works on Windows)
* Isolation is not perfect since containers share underlying kernels 
  * (security and stability)

:::
::::::::::::::

## Applications concept

![Build, Ship, Run](https://www.nebulaworks.com/insights/posts/containers-the-new-guy-on-the-block-so-why-all-the-noise/assets/images/build-ship-run.77855d42ceb65e4f433e274a3105b95d.gif)

## Containers for Data science

:::::::::::::: {.columns}
::: {.column width="50%"}

Data Science is about **reproducibility**

* Experimental science
* Communicating results
* Hands-out to other teams
* Deployment and versioning of models

:::
::: {.column width="50%"}

So... containers ?

* ... for deployment
* ... for standardized development environments
* ... dependency management
* ... for complex / large scale workflows

:::
::::::::::::::

## Quizz

What's a container?

- Answer A: Docker
- Answer B: A virtual Machine, kind of
- Answer C: A software package that contains everything the software needs to run (system, apps, dependencies)

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_827)

# Docker

## Docker

Docker is **a** solution that **standardizes** packaging and execution of software in isolated
 environments
 (**containers**) that share resources and can communicate between themselves

> Build, Share, and Run Any App, Anywhere

![](https://www.docker.com/wp-content/uploads/2022/03/vertical-logo-monochromatic.png){width=30%}

## History

[Docker](https://www.docker.com/)

* Created in 2013
* Open Source (some parts)
* Not a new idea but set a new standard
* Docker is a company built around its main product (Docker Engine)
* In charge of dev of everything docker (Docker hub...) + additional paid services 

## Under the hood

Docker is some fancy tech over linux kernel capabilities (containers)

![](images/DockerLinux.png)

[more info](https://medium.com/@goyalsaurabh66/docker-basics-cb006b9be243)

## Using Docker in practice

![](https://supaerodatascience.github.io/DE/slides/static/img/docker-jworkflow.jpg)

## Vocabulary of Docker

* **Layer**: Set of read-only files to provision the system
* **Image**: Read-Only layer "snapshot" (or blueprint) of an environment. Can inherit from another **Image**. Image have a *name* and a *tag*
* **Container**: Read-Write instance of an **Image**
* **DockerFile**: Description of the process used to build an Image
* **Container Registry**: Repository of Docker Images
* **Dockerhub**: The main container registry of docker.com

## Workflow

![workflow](images/basics-of-docker-system.png)

## Layers, Container, Image

![layers](images/servlet.ImageServer.jpg){width=45%}

## Layer / Image Analogy

Docker:
```Dockerfile
FROM python:3.6
RUN pip install torch
CMD ipython
```

```bash
docker build -f Dockerfile -t my-image:1.0 .
docker run my-image
```

Python:
```python
class BaseImage:
    def __init__(self, a):
       self.a = a

class NewImage(BaseImage):
    def __init__(self, a, b):
       super(NewImage, self).__init__(a=a)
       self.b = b

container = NewImage(a=0,b=1)
```

## Dockerfile

* Used to build Images

```Dockerfile
FROM python:3.7
ENV MYVAR="HELLO"
RUN pip install torch
COPY my-conf.txt /app/my-conf.txt
ADD my-file.txt /app/my-file.txt
EXPOSE 9000
WORKDIR "/WORKDIR"
USER MYUSER
ENTRYPOINT ["/BIN/BASH"]
CMD ["ECHO” , "${MYVAR}"]
```

```bash
docker build -f Dockerfile -t my-image:1.0 .
docker run my-image
```

* Reproducible (if you include static data)
* Can be put under version control (simple text file)

## Architecture

![](images/DockerArchi.png)

## Registry

* Local registry: All images/containers in your machine
* https://hub.docker.com/
* GCP Container Registry
* Social Dimension (share docker images to speed up development/deployment)

## Alternatives: Singularity

![](https://sylabs.io/guides/3.0/user-guide/_static/logo.png){height=200px}

"Docker for HPC"

- No root daemon process
- Better (?) security
  - Rootless build and run
- Better isolation between users, "just" a process
- Bridge between Dockerimage and Singularity images
- OCI compliant

## Alternatives: Podman

![](https://raw.githubusercontent.com/containers/podman/main/logo/podman-logo.png){height=200px}

"Rootless Docker for Redhat"

- Not root daemon
- Not need to be root
- Fully compliant with Docker images (and OCI)
- Better security and isolation


## Quizz

What's Docker typical workflow?

- Answer A: Pull Build Run
- Answer B: Pull Run
- Answer C: Build Ship Run
- answer D: Build Ship Push Run Pull

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_887)

# Hands on Docker

## Play with Docker

* You need to have a docker hub account : [https://hub.docker.com/](https://hub.docker.com/)
* Then we'll use the service provided at [https://labs.play-with-docker.com/](https://labs.play-with-docker.com/)
* Free, interactive, cluster of vms to experiment docker with
* [https://training.play-with-docker.com/](https://training.play-with-docker.com/) lots of resoures !
* We'll begin with [https://training.play-with-docker.com/beginner-linux/](https://training.play-with-docker.com/beginner-linux/)
* And try to make it to the [Voting App](https://training.play-with-docker.com/swarm-stack-intro/)
