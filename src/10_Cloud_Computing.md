---
title: Introduction to Cloud Computing
author: Guillaume Eynard-Bontemps, Hugues Larat, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2026
---

# Credits and thanks

## Didn't do this

Thanks to [Florient Chouteau](mailto:florient.f.chouteau@airbus.com) and [Dennis Wilson](mailto:Dennis.WILSON@isae-supaero.fr)

for their work on this subject.

I took most of the content from theirs: 

- [https://supaerodatascience.github.io/DE/1_1_overview.html](https://supaerodatascience.github.io/DE/1_1_overview.html)
- [https://supaerodatascience.github.io/DE/slides/1_1_cloud_computing.html](https://supaerodatascience.github.io/DE/slides/1_1_cloud_computing.html)
- [https://supaerodatascience.github.io/DE/slides/1_2_cloud_usage.html](https://supaerodatascience.github.io/DE/slides/1_2_cloud_usage.html)
- [https://supaerodatascience.github.io/DE/slides/1_3_gcp.html](https://supaerodatascience.github.io/DE/slides/1_3_gcp.html)

# What is the Cloud?

## 

![](https://nerds.net/wp-content/uploads/2018/02/cloud-computer-reality-750x646.jpg)

## But it's a bit bigger... 

:::::::::::::: {.columns}
::: {.column width="30%"}

![](https://supaerodatascience.github.io/DE/slides/static/img/fb_datacenter.jpg)

:::
::: {.column width="70%"}

![](https://www.akita.co.uk/wp-content/uploads/2023/09/cloud-storage-facilities-1.jpg)

(Facebook's data center & server racks)

:::
::::::::::::::

## Google Cloud Data Center locations

![Data Centers](images/google-dc-map.png)

## Cloud Definition

> The cloud is a real physical place - accessed over the internet - where a service is performed for you or where your stuff is stored. Your stuff is stored in the cloud, not on your device because the cloud is not on any device; the cloud lives in datacenters. A program running on your device accesses the cloud over the internet. The cloud is infinite, accessible from anywhere, at any time

Todd Hoff in "Explain the Cloud like I'm 10"

## Cloud Computing

Using cloud resources for any purpose, web server, storage, computations.

- The cloud is a set of **cloud providers**
- Renting cloud **services**
- Increasingly **abstracted** from the physical hardware

. . .

Examples:

- "Renting a server" ... (this is pure "cloud computing")
- "Replicated & Secure storage space"
- "Autoscaling deployment of a microservice"

## A portion of AWS services{background-image=https://www.matthewb.id.au/cloud/images/AWS-Services.png data-background-size=contains}

## Quizz

What's the Cloud?

- Answer A: Still don't know...
- Answer B: A magic place where my photos and alikes are
- Answer C: Someone else computer
- Answer D: Several big Data centers around the world that host data and service

![https://strawpoll.com/e7ZJar1eLg3](https://cdn.strawpoll.com/images/polls/qr/e7ZJar1eLg3.png)

## How?

# Virtualization

## Definition

> In computing, virtualization refers to the act of creating a virtual (rather than actual) version of something, including virtual computer hardware platforms, storage devices, and computer network resources.

Wikipedia

> Basically we are running software on "abstract hardware" which is a "portion" of a real computer ("bare metal")

## Desktop virtualization

![](images/virtualization.png){width=75%}

## Server virtualization

![](images/illustration-of-the-concept-of-Virtualization-7.png)

## Virtualization evolution

![](https://miro.medium.com/max/10698/1*wE7TrQmFyRTDwh6VpbkbMQ.png){width=90%}

## Definitions

- **Hypervisor** (VMWare, Virtualbox, KVM): A hypervisor is a program for creating and running virtual machines
- **Virtual Machine**: A virtual machine is the emulated equivalent of a computer system that runs on top of another system
- **Containers**: Isolated environments that share the same underlying OS (more this afternoon) & resources

## Opens up new possibilities

:::::::::::::: {.columns}
::: {.column width="50%"}

### Hardware abstraction

- Hardware Abstraction ("download more RAM")
- Fine-grained resource allocation / sharing
- Decouple maintenance of hardware from maintenance of software

:::
::: {.column width="50%"}

### Reliability, security...

![balancing](https://yogeek.github.io/enseignement/Introduction_Virtualisation_CloudComputing/img/vm_charge_repartition.gif)

:::
::::::::::::::

## Quizz

Virtualization allows... (multiple choices)

- Answer A: Hardware abstraction, download a machine with more ram
- Answer B: Resources sharing optimization
- Answer C: Building immersive video games
- Answer D: Reliability
- Answer E: Reproducibility

![https://strawpoll.com/7rnzV4aRDnO](https://cdn.strawpoll.com/images/polls/qr/7rnzV4aRDnO.png)

# Cloud history

## AWS

Once upon a time...

Amazon (the e-commerce store) has "scaling" issues

![](https://cdn.chiefmartec.com/wp-content/uploads/2016/11/jeff_bezos_big_mandate.jpg)

## Idea

2002-2003; The idea

> Building an infrastructure that is completely standardized, completely automated, and relied extensively on web services for things like storage 

[http://blog.b3k.us/2009/01/25/ec2-origins.html](http://blog.b3k.us/2009/01/25/ec2-origins.html)

## So ...

Basically Amazon became very good at *running* scalable infrastructure as *services*

- For themselves...
- ... but also for other partners (target)

And that infrastructure is often there to answer peak load...

## Let's sell it !

![](https://fchouteau.github.io/isae-practical-gcp/static/img/ec2.png)

# The many layers of Cloud Computing

## Public, hybrid, private

![](images/blog-cloud-comparison.jpg){width=80%}

## Different layers of abstractions

![](images/modeles-de-services-cloud.png)

## Abstraction examples

- Using data storage service like google cloud storage without managing the infrastructure ?aaS
- Using google drive ?aaS
- Renting a server with hard drive and storing data ?aaS


. . . 


- Using data storage service like google cloud storage without managing the infrastructure **PaaS**
- Using google drive **SaaS**
- Renting a server with hard drive and storing data **IaaS**

## Quizz

What means IaaS?

- Answer A: I am a Sociopath
- Answer B: Information as a System
- Answer C: Information as a Service
- Answer D: Infrastructure as a Service

![https://strawpoll.com/w4nWWO2xlnA](https://cdn.strawpoll.com/images/polls/qr/w4nWWO2xlnA.png)

# Cloud Engines

## Public

![Cloud Vendors](https://yogeek.github.io/enseignement/Introduction_Virtualisation_CloudComputing/img/cloud_vendors.jpg)

## Public (European)

![](https://www.comptoir-hardware.com/images/stories/_logos/ovhcloud.png){width=20%}
![](https://www.orange-business.com/sites/default/files/illustration-obs---cloud---infrastructures.png){width=20%}
![](images/open_telekom_cloud.png){width=20%}

Academic, public founded:

![gaiax](https://gaia-x.eu/wp-content/uploads/2022/12/Gaia-X_Logo_Inverted_White_Transparent_210401-3-1000x687.png){width=20%}
![EOSC](https://eosc.eu/wp-content/uploads/2023/08/EOSCA_logo.svg){width=20%}

## Private/on premise

![](http://1.bp.blogspot.com/-1BuI8MUh498/Uc4BOPBpChI/AAAAAAAAGjk/XWA0iYO5drA/s1028/Screen+Shot+2013-06-28+at+12.03.11+PM.png)

## Leaders

![](https://cdn.statcdn.com/Infographic/images/normal/18819.jpeg){width=45%}

# Cloud computing: usage revolution

## A technical evolution

- More Virtualization
- More API
- More Managed Services

## Access and operating computing power

- Outsourcing infra, maintenance, security, development of new services
  - Less (?) operation cost (or at least less burden)
- Pay-per-use, pay as you go, change of economical model
- "Infinitely scalable" for common folks
- "No need to plan out" infrastructure
  - Enabling innovation
  - Power in the hands of developpers/builders

## Technical benefits

- Infrastructure as Code
- Continuous Deployment
- Infinite resources
- On demand scalability and resources

## Changing the way we interact with hardware

We interact with cloud providers using APIs...

```bash
gcloud compute --project=deeplearningsps instances create ${INSTANCE_NAME} \
    --zone=${ZONE} \
    --machine-type=n1-standard-8 \
    --scopes=default,storage-rw,compute-rw \
    --maintenance-policy=TERMINATE \
    --image-family=ubuntu-1804-lts \
    --image-project=ubuntu-os-cloud \
    --boot-disk-size=200GB \
    --boot-disk-type=pd-standard \
    --accelerator=type=nvidia-tesla-p100,count=1 \
    --metadata-from-file startup-script=startup_script.sh
```

## Infrastructure as Code

- Infrastructure is now managed via text files
- Data is securely stored on storage
- So we store code + urls on git... and everything is reproducible ! (not _that_ simple)
- We use automated deployment tools (terraform, gcp deployment manager...)

## Pet vs Cattle

![](images/petcattle.png){width=50%}

## Quizz

Why Cloud computing is a usage revolution (multiple choices)?

- Answer A: Infinite resources (CPU, memory, storage)
- Answer B: It's cheaper
- Answer C: Infrastructure managed as Code
- Answer D: Pay per use
- Answer E: It gives all our data to Google and Amazon

![https://strawpoll.com/Q0Zp7zDPGgM](https://cdn.strawpoll.com/images/polls/qr/Q0Zp7zDPGgM.png)

# New Data Processing standard

## Object store

High througput storage system with horizontal scalability

![](images/FileStorage.png)
![](images/ObjectStorage.png)

## Compute as a service

- Start and stop compute resources when needed
  - IaC tools like Terraform, Ansible
  - Mesos/Nomad and other tools.
- Kubernetes as a Service
  - With autoscaling features: add VMs if needed
  - Dask, Spark and other processing tools plugged in
- Function as a Service
  - Just put a bit of code, everything else is handled.
- HPC as a Service
  - With POSIX filesystem (sometimes over Object store)
  - And high performance network.

## HPC as a Service

AWS ParallelCluster

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2019/11/06/parallelcluster-1.gif)

# Discussions and Troll

## Is using cloud computing less expensive?

- ![+1](images/thumbsup.svg){height=20px} Depend on your {normal / peak} utilization
- ![+1](images/thumbsup.svg){height=20px} Access to latest hardware without investment
- ![-1](images/thumbsdown.svg){height=20px} Fully utilized hardware is more expensive on the cloud
- ![-1](images/thumbsdown.svg){height=20px} CLOUD HYGIENE !
  - Watch for unused services / storage
  - Shutdown machines when not used
  - Services stack up...

## Is using cloud computing more secure / safer.

- ![+1](images/thumbsup.svg){height=20px} The best engineers in the world working on it
- ![+1](images/thumbsup.svg){height=20px} Secure regions / private cloud...
- ![-1](images/thumbsdown.svg){height=20px} Your data somewhere in some datacenter...
- ![-1](images/thumbsdown.svg){height=20px} "Dependency" towards your cloud provider...
- ![-1](images/thumbsdown.svg){height=20px} Still need to handle security inside you resources

![OVHCloud burning](https://cdn.searchenginejournal.com/wp-content/uploads/2021/03/fire-ovh-data-center-60488d3b150d6-760x400.jpg)

# Google Cloud Platform

## Presentation

- One of the main cloud provider
- Behind AWS in SaaS (serverless...)
- More "readable" product line (for a Cloud Provider...)
- Very good "virtual machine" management  
  * per second billing
  * fine-grained resource allocation

## Services

![](https://static.packt-cdn.com/products/9781788837675/graphics/ee72c164-888d-4cec-b3f9-efd3b8e8e4cb.png)

## {background-image=https://raw.githubusercontent.com/gregsramblings/google-cloud-4-words/master/Poster-medres.png}

## Concepts: Zones and regions

![](https://cloud.google.com/docs/images/overview/regions-zones.svg)

## Concepts: Projects

![](https://cloud.google.com/docs/images/overview/console-ids.png)

- Access (Enabling API/Services)
- Ressources (Quota by project)
- Networking
- Billing

## Concepts: Identity and Access Management (IAM)

![IAM](https://miro.medium.com/max/638/0*kGyUfNWZCk78hmPU.)

## Interacting with GCP: The Console

![https://console.cloud.google.com](https://cloud.google.com/docs/images/overview/console.png){width=60%}

## Interacting with GCP: SDK & Cloud Shell

- Using the gcloud CLI: [https://cloud.google.com/sdk/install](https://cloud.google.com/sdk/install)
- Using Google Cloud Shell: A small VM instance you can connect to with your browser

# First interaction with Google Cloud (Exercise)

## Objectives

Everyone has its credits/coupons?

- Create your GCP account, configure your credentials, ensure everything is working
- With the coupons you got, you should see $50 of credits (in the billing tab)
- Interact with Google cloud console: check all the services
- Start a first VM instance through the console, watch prices and all the options
- Create a Google Storage bucket and upload content
- Connect to google cloud shell and interact with it
- Follow [this Google codelabs](https://codelabs.developers.google.com/codelabs/cloud-compute-engine#2) to deploy a Website!

We'll do more this afternoon!
