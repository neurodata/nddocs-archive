---
title: Tutorials
layout: default
---

# Tutorials

## Access

### How do I look at images?

We have developed our own lightweight Web-visualization tool called [NeuroDataViz](http://docs.neurodata.io/NeuroDataViz/).  It has been designed specifically to enable:  volumetric annotations, multi-spectral data, and time-series data.  Here are a few different examples:

* [kharris15apical](http://brainviz1.cs.jhu.edu/ndv/kharris15apical/em,ramon_test/3/507/469/90/) demonstrates annotation overlays and metadata capabilities
  * Image metadata is available via the *Project Info* button in the menubar. 
  * From the menubar, select *Query*, then *kharris15apical / ramon_test*.
  * The blue cell in the center of the image has a corresponding ramon object. Clicking on the blue cell will bring up RAMON metadata. No other cells/objects have ramon objects.

* [aratome15c](http://brainviz1.cs.jhu.edu/ndv/project/Aratome15c_S17_W10/1/5818/527/0/) demonstrates multi-spectral color blending capabilities
  * play with opacity, brightness, and contrast
  * change the blend mode to enable different color blends

* [freeman14](http://openconnecto.me/ocp/viz/freeman14/) demonstrates 3D time-series capabilities.

To see other data in NeuroDataViz, browse to our [projects](http://neurodata.io/projects) page, and select a dataset of interest.  Many of those datasets automatically link to NeuroDataViz.  Of note, they are not yet all currently centered, so you might have to move around a bit to find the data. 

There are many other viewers out there, with complementary features.  The ones that we support are listed below in the 3rd party apps section.


### How do I look at Graphs?

We have developed [Graph Explorer](http://128.220.176.8/ge/), a [shiny app](https://www.shinyapps.io/) that allows you to upload any graph to both visualize and analyze it.  Other 3rd party graph visualization/analysis tools can also be used with any of our graphs.

## Download some data to play with on my computer?

### Images

- The easiest way to download data is via our [Download Web-form](http://neurodata.io/exchange/download). It presents two options: 
  - "Ready-to-go" downloads provide frequently requested cubes as a PNG stack
  - If you know the token, resolution, and bounding box for some data of interest, and you want less than 2 GB, you can type it in directly. 
- [ndio](http://docs.neurodata.io/ndio/) is our Python library that lets you get and put data into NeuroData.  As long as you are transfering < 1 TB of data, this should work fine.
- [CAJAL](http://docs.neurodata.io/CAJAL/) is our MATLAB toolbox for NeuroData. It has all the functionality of ndio, and more.  It can also be used for transfering data up to about 1 TB.
- [Data API](http://docs.neurodata.io/open-connectome/api/data_api.html): you can also download arbitrarily large data via using the RESTful calls directly.  Examples are provided at the above link.

### Graphs

Downloading graphs is easy, simply go to our [graph download](http://openconnecto.me/graph-services/download/) Web-page.  From there, you can select the format (eg, MATLAB, graphml, etc.), and even scale for the human MR derived graphs.  Many other graph services are available from there as well. 


## Show some image data to labmates/colleagues?

### Images

- web-form < 200 GB
- CAJAL < 1 TB
- ndio < 1 TB
- auto-ingest < 2 TB https://github.com/openconnectome/open-connectome/blob/master/ingest/autoingest/verifyjson.py
- (s)ftp/(s)http/open-s3: abritrary size https://github.com/openconnectome/open-connectome/tree/master/ingest/

### Graphs

## Computer Vision


### Stitch and align into volume?

### Color correct a volume?

- 2D
- 3D


### Manually annotate some data?

- CATMAID
- knossos
- VAST
- Reconstruct
- ITK-SNAP
….

### Share annotations (RAMONify)?

csv ingest script (with spec)

### Proofread and error correct metadata?

- ocpviz: edit metadata
- parity

### Train my machine vision algorithm on some data?

Training paradigms are different for each use-case.  We provide examples for a random forest training example and a paradigm using ilastik.  Training is typically conducted using standalone functions (v. a distributed LONI approach)

- vesicle RF example
- ilastik example

### Assess the performance of algorithms?

example (in matlab), of making ROC curves on held out data from a separate volume
example in loni sweeping over a set of hyperparameters

### Run my machine vision algorithm at scale?

- LONI stuff


## Analysis

## m2g

### How do I generate multiscale graphs from MRI data?

#### Code


#### Instructions

### How do I know that the graphs I made are reliable?

### How long does it take to generate graphs?



### Query the scene?

- CAJAL
- ndio

### Estimate statistical properties?

## Other stuff

### Computing Resources

### Third Party Tools Integration Status

- ITK Snap:  Works in manno for annotation purposes.  No one has written a tutorial about actually visualizing things otherwise, but should be possible
- bigdataviewer:  Broke when we switched to channel interface.  Stephan is fixing.
catmaid:  [ask alex]
- vaa3d:  Nathan and Dean did this.  Code broke when we switched to channel interface.
- knossos:  Kunal wrote a backend so that they could pull data.  Status unknown.  No import capability.
- viking:   Kunal wrote a backend so that they could pull data.  Status unknown.  No import capability.
- neutube:  none yet
- janelia-workstation:  ??
- reconstruct:  Alex has some scripts.
- VAST:  can pull data from neurodata
- [Gephi](http://gephi.github.io/): can load any graph downloaded from [here](http://openconnecto.me/graph-services/download/)
