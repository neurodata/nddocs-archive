# Mouse Brain Cell Detection Pipeline Deliverable

**January 15, 2016**

*JHU/Applied Physics Laboratory Technical Report and Readme*

To enable the detection of cell clusters at scale, we have developed a generalizable, open source framework.  This framework leverages community tools and custom-built code to efficiently and effectively provide scientific tools.

Due to the limited ground truth available at this time, the focus of this handoff is on providing capability, rather than performance, although we have provided post-processing tools and assessment methodology that can be expanded as truthing data mature.

![](./images/overlay_cellCluster_v1b.png)


There are two main ways to interact with this pipeline: 

In the standalone mode, users specify a directory location where their images reside, and use the included scripts to save files in a format compatible with downstream processing.  The results are saved in a specified output directory for future analysis.  Users can then choose an image processing or machine vision tool (deep learning with pyCaffe, ilastik, or a MATLAB pre-screening tool), and save the probabilities to disk.  To convert these images to cell clusters, one can threshold and run a connected components analsyis on the probability maps.  An optional step to compute statistics on each cluster is provided.

![](./images/od_standalone.png)

As an alternative, the input/output modules can be changed to get/put data to the NeuroData spatial databases.  The workflow is as described above, except that all data endpoints are at the spatial database, rather than stored locally.

Currently, the deep learning methods have not been explicitly integrated into the neuroData backend.
 
![](./images/od_nd.png)

## Data Input/Output

### Standalone 

In standalone mode, the data is first converted to a common format.  All three processing methods are flexible regarding input data format, but the interfaces vary slightly, and are described below. 

We provide an example script in ./pipeline/io that downsamples and converts a directory of data to tif stacks for convenience.  This can be easily extended based on user needs.

For output, users will specify an output directory 

### NeuroData

For NeuroData, users are advised to use one of the NeuroData APIs, which are documented extensively at the following locations:

- ndio (python):  documentation is available at http://docs.neurodata.io/nddocs/ndio/
- CAJAL (MATLAB):  documentation is available at http://docs.neurodata.io/CAJAL/
- RESTful endpoints:  documentation is available at http://docs.neurodata.io/open-connectome/ 

## Manual Annotation for Open Science

Prior to training a classifier, dense ground truth is needed.  We provide a tool called manno [http://docs.neurodata.io/manno/] to annotate ground truth.  This interfaces with ITK-Snap and a well-defined protocol that has been used for many neuroimaging tasks.

Interfaces are provided for both standalone and neurodata workflows.

## Machine Annotation for Open Science (Pixel Classification)

For the core processing task of cell cluster detection, we provide three options:

### Basic Thresholding

This is a method that takes in a tif file and outputs both a probability and thresholded mask containing cell cluster detections.  Because this is only image processing (not machine learning), it is recommended to be used as a pre-processing or data reduction step.  Because the deep learning methods are much more computationally expensive, users might wish to use this step to remove background and other pixels that are very unlikely to contain target from a classifier testing paradigm.

The code for this approach has only been tested in standalone mode.

### Ilastik

### Deep Learning

Please see the Deep Learning Repo.

## Post Processing (Object Detection)

- Cell clusters
- Centroids and Size Metrics
 
### Assessment

- Accuracy
- Precision-Recall

## End-to-End Framework Prototype

The processing steps described above can be run sequentially or integrated into a larger framework to automate some of the interfaces.  As each users' integration environment 
Users have at least three choices when running the computational blocks presented here:

- LONI
- Scriptable Format
- Cluster integration (outside scope)

We provide examples of each mode, which can be adapted to user needs.

## Outlook

Finding cell clusters in nissl-stained images can be complex at scale, but the tools provided give three distinct options for processing:

- An intensity based method, perhaps most suitable for 

Future work is needed to generate expert dense ground truth labels for training, evaluation and test.  Additionally, work is needed to estimate cell counts in each cell cluster.  This may be accomplished through a regression problem, superpixelization, or simply counting based on estimated cell sizes.
