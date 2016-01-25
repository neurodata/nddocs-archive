---
title: home
---


# NeuroData Docs

This site contains a collection of pages explaining how to access data, analyze data, and visualize both raw and derived data products.

All of our code is open source and available via our github repository. Individual packages and repositories can be found by navigating the packages below. For mesoscale problems or proof-of-concept testing, we have integrated our analytics stack into an AMI, which can also be found below.

Finally, as our services mature, we migrate our raw code to web-services, to facilitate one-click analysis and discovery.

{% include image.html url="images/ocp_example.png" width="700px" %}

## Tutorials

If you are new to NeuroData, we recommend that you start with our [tutorials](tutorials.html), which cover a quick, easy-to-understand overview of our services, taught by example.

The rest of this page includes a detailed description of our standards and links to each of our code repositories and associated documentation, and is more suitable as a reference.

## Overview

-   [AMI](ami.html)
-   [Datamap](datamap.html)
-   [Python Library: ndio](ndio/)
-   [RAMON Spec](ramon.html)
-   [RAMON + NeuroData](ramonnd.html)

## code

### neuroimages

#### image processing

These tools help users to preprocess and convert raw neuroscience data for
manual or machine annotation.

-   [2D Color Correction](https://github.com/openconnectome/dmg)
-   [Volume Reconstruct](https://github.com/openconnectome/AT-reconstruction-service)

#### manual annotation

These tools exist to help users manually annotate their neuroimaging data for
downstream analysis.

-   [manno](https://openconnectome.github.io/manno)
-   [vast](https://software.rc.fas.harvard.edu/lichtman/vast/) (3rd party)
-   [catmaid](http://fly.mpi-cbg.de/~saalfeld/catmaid/) (3rd party)
-   [parity](http://www.openconnecto.me/stem) (not live)

#### machine annotation

These tools exist to help users automatically annotate their neuroimaging data
for downstream analysis.

-   [deep learning](https://github.com/iscoe/coca)

#### time-varying images

-   [oopsi for calcium imaging](https://github.com/jovo/oopsi)
-   [mr. sid for fmri](https://github.com/shachen/PLDS/)

#### electrophysiology

-   [spike-sorting](https://github.com/jovo/spike-sorting)
-   [online-spike-sorting](https://github.com/decarlson/opass)

#### infrastructure

-   [open-connectome](http://openconnectome.github.io/open-connectome)
-   [tilecache](http://openconnectome.github.io/ocptilecache)

#### graph inference

-   [i2g](http://i2g.io)
-   [m2g](http://m2g.io)

#### access

-   [CAJAL](http://openconnectome.github.io/CAJAL)
-   [ndio](ndio/)

### neurographs

-   [FlashR](https://github.com/openconnectome/FlashR)
-   [FlashGraph](http://www.flashgraph.net/)
-   [Fast Approximate QAP](https://github.com/jovo/FastApproximateQAP)
-   [Signal Subgraph Classifier](https://github.com/jovo/signal-subgraph-classifier)

### machine learning

-   [LOL](https://github.com/jovo/LOL)
-   [Randomer Forest](https://github.com/ttomita/RandomerForest)
-   [Iterative Denoising Trees](https://github.com/youngser/behaviotypes)
-   [Multiscale Dictionary Learning for Estimating Conditional Distributions](https://github.com/jovo/conditional-density-estimation)

#### analytics framework

-   [AMI](ami.html)
-   [LONI](#)
-   [distributed computing](./overview/distributed_computing.html)

## Parse <a name="parse"></a>

**ndparse** is the NeuroData Parse parent repository

This repo contains the code needed to train, evaluate, and deploy code for parsing volumes of NeuroData images.  The source code can be downloaded [here](https://github.com/openconnectome/ndparse).

![ndod example](images/ndod/ndod_example.png)

It contains the legacy code for manno and macho.  The current version of ndparse is divided into the three major components required to parse neuroscience data at scale:

- [**mana**](mana.html):  manual annotation 
- [**maca**](maca.html): big-data research algorithms to inform neuroscience
- [**maxa**](maxa.html): deployment resources for annotation generation and open neuroscience 

Documentation for each component can be found using the above links.  Additionally, users may find the following pages helpful:

- installation instructions and getting started
- [function reference](http://docs.neurodata.io/ndod)
- [tutorial for mouse brain cell detection using ilastik](mbcd.html)
- [tutorial for mouse brain cell detection using deep learning](nddl.html)
- tutorial using NeuroData and Ilastik for generalizable object detection
- [vesicle](http://docs.neurodata.io/vesicle/)

Web-services
------------

### neuroimages

-   [open-connectome](http://openconnectome.github.io/open-connectome)
-   [tilecache](http://openconnectome.github.io/ocptilecache)
-   [AMI](http://aws.amazon.com) (AMI name: neurodata)
-   [2D Color Correction](https://github.com/openconnectome/dmg)

### neurographs

-   [m2g](http://m2g.io)
-   [c4](http://openconnecto.me/graph-services/c4/)
