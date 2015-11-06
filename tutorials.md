---
title: Tutorials
layout: default
---

# Tutorials

## Access = Visualize, Download & Upload

### How do I look at images?

We have developed our own lightweight Web-visualization tool called [NeuroDataViz](http://docs.neurodata.io/NeuroDataViz/).  It has been designed specifically to enable:  volumetric annotations, multi-spectral data, and time-series data.  An example URL:

* Visit http://brainviz1.cs.jhu.edu/ndv/kharris15apical/em,ramon_test/3/507/469/90/
* Image metadata is available via the *Project Info* button in the menubar. 
* From the menubar, select *Query*, then *kharris15apical / ramon_test*.
* The blue cell in the center of the image has a corresponding ramon object. Clicking on the blue cell will bring up RAMON metadata. No other cells/objects have ramon objects.

To see other data in NeuroDataViz, browse to our [projects](http://neurodata.io/projects) page, and select a dataset of interest.  Many of those datasets automatically link to NeuroDataViz.  Of note, they are not yet all currently centered, so you might have to move around a bit to find the data. 

There are many other viewers out there, with complementary features.  The ones that we support are listed below in the 3rd party apps section.


### How do I look at Graphs?

#### web viewer: graph explorer

#### local client viewers: gephi

### Download some data to play with on my computer?

### Images

- web-form < 2 GB
- CAJAL < 1 TB
- ndio < 1 TB
- get: arbitrary size

### Graphs




## Show some image data to labmates/colleagues?

- web-form < 200 GB
- CAJAL < 1 TB
- ndio < 1 TB
- auto-ingest < 2 TB https://github.com/openconnectome/open-connectome/blob/master/ingest/autoingest/verifyjson.py
- (s)ftp/(s)http/open-s3: abritrary size https://github.com/openconnectome/open-connectome/tree/master/ingest/


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
