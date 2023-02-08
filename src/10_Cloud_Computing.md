---
title: Introduction to Cloud Computing
author: Guillaume Eynard-Bontemps, CNES (Centre National d'Etudes Spatiales - French Space Agency)
date: 2020-11-16
---

# Credits and thanks

## Didn't do this

Thanks to [Florient Chouteau](mailto:florient.f.chouteau@airbus.com) and [Dennis Wilson](mailto:Dennis.WILSON@isae-supaero.fr)

for their work on this subject.

I took most of the content from theirs: 

- [https://supaerodatascience.github.io/OBD/1_1_overview.html](https://supaerodatascience.github.io/OBD/1_1_overview.html)
- [https://supaerodatascience.github.io/OBD/slides/1_1_cloud_computing.html](https://supaerodatascience.github.io/OBD/slides/1_1_cloud_computing.html)
- [https://supaerodatascience.github.io/OBD/slides/1_2_cloud_usage.html](https://supaerodatascience.github.io/OBD/slides/1_2_cloud_usage.html)
- [https://supaerodatascience.github.io/OBD/slides/1_3_gcp.html](https://supaerodatascience.github.io/OBD/slides/1_3_gcp.html)

# What is the Cloud?

## 

![](https://nerds.net/wp-content/uploads/2018/02/cloud-computer-reality-750x646.jpg)

## But it's a bit bigger... 

:::::::::::::: {.columns}
::: {.column width="30%"}

![](https://supaerodatascience.github.io/OBD/slides/static/img/fb_datacenter.jpg)

:::
::: {.column width="70%"}

![](https://www.datacenterknowledge.com/sites/datacenterknowledge.com/files/wp-content/uploads/2013/06/lulea-rows.jpg){width="35%"}
![](https://www.datacenterknowledge.com/sites/datacenterknowledge.com/files/wp-content/uploads/2013/06/fb-lulea-external-fans.jpg){width="35%"}

(Facebook's data center & server racks)

:::
::::::::::::::

## Google Cloud Data Center locations

![Data Centers](https://cloud.google.com/images/locations/regions.png)

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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_418) _Key: zq_

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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_702) _Ket: un_

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

![Answer](data:image/png;base64,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)

[Answer link](https://toreply.univ-lille.fr/reponse_743) _Key: gk_

# Cloud Engines

## Public

![Cloud Vendors](https://yogeek.github.io/enseignement/Introduction_Virtualisation_CloudComputing/img/cloud_vendors.jpg)

## Public (European)

![](https://www.comptoir-hardware.com/images/stories/_logos/ovhcloud.png){width=20%}
![](https://cloud.orange.com/ui/app/static/assets/brand/logo_header_login.png){width=20%}
![](images/open_telekom_cloud.png){width=20%}

Academic, public founded:

![gaiax](https://www.data-infrastructure.eu/GAIAX/Redaktion/EN/Bilder/gaia-x.jpg?__blob=normal&v=1&size=834w){width=20%}
![EOSC](https://eosc-portal.eu/sites/all/themes/theme1/logo.png){width=20%}

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

:::::::::::::: {.columns}
::: {.column width="50%"}

![](https://blog.octo.com/wp-content/uploads/2016/12/image01-e1482225268205-1024x827.png){width=50%}

:::
::: {.column width="50%"}

![](https://blog.octo.com/wp-content/uploads/2019/07/pet_vs-cattle-1024x636.png){width=50%}

:::
::::::::::::::

## Quizz

Why Cloud computing is a usage revolution (multiple choices)?

- Answer A: Infinite resources (CPU, memory, storage)
- Answer B: It's cheaper
- Answer C: Infrastructure managed as Code
- Answer D: Pay per use
- Answer E: It gives all our data to Google and Amazon

![Answer](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAAEsCAIAAAD2HxkiAAAG90lEQVR42u3d0ZKbIBQG4NrJ+7/y9mJnMqlRQ4RzAP2+q852jUj8BWWR5efn5w/Qz19VAH09Pv7GsizPf2s2obnlPV2/qfv9yd6/v9vH2Q03rwXXuxA0qZ/o4q0q//WHm9do1+6vu6ObdTqUqb/IZVnGr+HjC8Trhfj1S3lVuBW794QH17bnOeSSFnR9GbNiV196YaLObeWesH0TdNB7bN5Reb88f1vC53nzfq1Z/WSv8O8n2fvJt3kh+7aiVkX9tg6bX0wvfJuQ3RK2vVy99kZWn9m8o/L6geWfeVDCE32zVRlWt9CvbcL7mbp37h5X1LIsJ+pwVeDC6+/BVpvF+LgVu93R0D5MXEflRF/uoIStelmVPcyP+zpXh98e8up+5HWr1X3gXg5XW/GhO/rbJiRct9ruIvlCu3fn/F51Y558J0p17kBk7+Q94Vd9s8zzoPwOJ7r8e4V/v9O7RiOwdxTH95YawM7d0YNbgs1nFQ1jU3+rc67wXx1FyS/v3XM2qaJvK3yzGB9LGFH4q1o+3rlV5uH9kWPlw8w/h4PC5YUvKWF54feejh6X/3ir46ejJ76vc8+lD7Y691+sa1gF3epqrV0a/Z6QyxM/LSEQ/2AGEEIQQkAIQQgBIQQhBIQQhBAQQhBCQAhBCAEhBCEEhBCEEBBCGEnSO2YGfBf6wes0T28eceyV5az8zLS3n8xyhmgJQXcUEEIQQkAIQQiBVnq+Bn/Ax98RRUobzKjce8SxVw573GSAREsIuqMghIAQghACQgj3NNxKvRHzAyr3XjnnoPw3IyZMVA4SVI7upA17pJ0hWkLQHQWEEIQQEEIQQqCVhyp4lTbCUVmkiB1Vjkb0fU+UlhAQQhBCQAhBCAEhhOkYovhP3xkP5SqnQcwyh0NLCAghCCEghCCEgBDChQ03RNH3+XXfNzWlvVFq6gkT1xvh0BKCEIIQAkIIQggIIdxTzyGKvmsUlxcp4jF939GItCkgaSthaAkBIQQhBIQQhBAQQphO0hDF1H/53vdBefne08ZXIr73O7/9SUsIQghCCAghCCEghHBPV1uLovIVRpXTC9KmVkRsnvZ1zDKDJG3UREsIuqMghIAQghACQgj3tOQ8h4144U/fp9J9X2HUdzAj7Sl/xPjKgNM1tIQghCCEgBCCEAJCCPc03FoUlZMbImYSTD2YUW7AYY++Z52WEHRHASEEIQSEEIQQCNVzLYrKFyil7b3vbI/Kw+z7xVV+5oCTMLSEoDsKCCEIISCEIIRAK8OtRTHL0gsDrmI9y3SNiEkt5WdIRNVpCUF3FBBCEEJACEEIgROWAV/NX1r0rMfKEZMGBixS37Uo0vY+4LuntISgOwpCCAghCCEghHBPSbMo0tY9jngAnba+RWU5IzaP+DrKlxtJO0xrUYDuKCCEIISAEIIQAvnMovj8mZX6ziSo3Lzv6dF3MQmzKEB3FBBCEEJACEEIgVATr0UR8Zlpj/5Vcq+vQ0sICCEIISCEIISAEMIghptFMcsD6L5zDvqOmsyyFkVa4bWEoDsKCCEIISCEIITACcOtRZG2uPSAOxpwvkVahcwyAUVLCEIICCEIISCEIIRAK3OsRVH+pDttgYq+Aw9pcyMivrgBjz2tQrSEoDsKCCEIISCEIITAU9IQxSxLW29Ke69RWoVUHtGAL7lKe6OUlhB0RwEhBCEEhBCEEGil5xBFmr6P/iOqru860neeF6IlBN1RQAhBCAEhBCEEWnl03Hfa7IS0+QER0wsiZjyUF768SOVusjCJlhB0RwEhBCEEhBCEEDj2uNjxzLKgQsTeK39zlqq73tQKLSEIIQghIIQghIAQwj0N96KntMWQ+xpwIsLU64VEVLKWEHRHASEEIQSEEIQQCLXM8hg3qTqyHtOnvWZqU8RSFrO8J8py2YAQghACQghCCAghDCLpRU8DToPYfACd9lQ6YjGJiL2nfZuVRYpY8ENLCLqjgBCCEAJCCEIIhBpuuewIaUtGR2w+4CyKAU+GAedGaAlBdxQQQhBCQAhBCIFjwy2X3Xcx5PJn933HA9LGQiJ2FDEWkjaQoyUE3VFACEEIASEEIQRaeaiCcyKWoR7w6XnaYaYN5Aw4g0RLCLqjIISAEIIQAkII92SIoqWIKSBp0zUqdxSxbkTfCtESgu4oIIQghIAQghACoZacv8evXGVhwL1P/baivm/TmnrRCy0h6I4CQghCCAghCCHQSs9ZFAP+PXt5OdPWu06bc5D2meU7iqilvqNlWkLQHQWEEIQQEEIQQuBpGfCPykFLCAghCCEghCCEgBCCEAJCCEIICCEIISCEIISAEIIQAkIIQggIIQghIIQghIAQghACQghCCAghCCEghCCEgBCCEAJCCEIICCFM4x8bwcdsaacMhgAAAABJRU5ErkJggg==)

[Answer link](https://toreply.univ-lille.fr/reponse_959) _Key: sm_

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
