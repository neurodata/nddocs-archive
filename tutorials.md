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

* [freeman14](http://viz.neurodata.io/freeman14/) demonstrates 3D time-series capabilities.

To see other data in NeuroDataViz, browse to our [projects](http://neurodata.io/projects) page, and select a dataset of interest.  Many of those datasets automatically link to NeuroDataViz.  Of note, they are not yet all currently centered, so you might have to move around a bit to find the data.

There are many other viewers out there, with complementary features.  The ones that we support are listed below in the 3rd party apps section.


### How do I look at Graphs?

We have developed [Graph Explorer]128.220.176.8/Graph-Explorer/shiny/), a [shiny app](https://www.shinyapps.io/) that allows you to upload any graph to both visualize and analyze it.  Other 3rd party graph visualization/analysis tools can also be used with any of our graphs.

### Download some data to play with on my computer?

#### Images

- The easiest way to download data is via our [Download Web-form](http://neurodata.io/exchange/download). It presents two options:
  - "Ready-to-go" downloads provide frequently requested cubes as a PNG stack
  - If you know the token, channel, resolution, and bounding box for some data of interest, and you want less than 2 GB, you can type it in directly.  Information about each dataset can be found in the project info pages 
(e.g., `openconnecto.me/ocp/ca/bock11/info/`)
- [ndio](http://docs.neurodata.io/ndio/) is our Python library that lets you get and put data into NeuroData.  As long as you are transfering < 1 TB of data, this should work fine.  An example ipython notebook can be found [here](https://github.com/openconnectome/ndio-demos/blob/master/Getting%20Started/Downloading%20a%20Volume.ipynb).  An example call is:

~~~
bock11_subvol = oo.get_cutout('bock11', 'image', 11000, 11100, 11000, 11100, 4000, 4010, resolution=3)
~~~

- [CAJAL](http://docs.neurodata.io/CAJAL/) is our MATLAB toolbox for NeuroData. It has all the functionality of ndio, and more.  It can also be used for transferring data up to about 1 TB.  A code snippet to download data can be found below.

~~~
%% Create OCP Interface and set tokens
oo = OCP();
oo.setServerLocation('http://openconnecto.me/');
oo.setImageToken('kasthuri11cc');
oo.setDefaultResolution(1);

xstart = 5500;
ystart = 6000;
zstart = 400;

% Build query to cutout IMAGE data.
q = OCPQuery(eOCPQueryType.imageDense);
q.setCutoutArgs([xstart xstart+500],...
                [ystart ystart+500],...
                [zstart zstart+5], 1);

% Download the data into a RAMONVolume.
cutout = oo.query(q);
~~~

- [Data API](http://docs.neurodata.io/open-connectome/api/data_api.html#get): you can also download data < 2 GB via using the RESTful calls directly.  An example call follows:

~~~
http://openconnecto.me/ocp/ca/kasthuri11cc/image/hdf5/1/5472,6496/8712,9736/1000,1100/
~~~

#### Graphs

Downloading graphs is easy, simply go to our [graph download](http://openconnecto.me/graph-services/download/) Web-page.  From there, you can select the format (eg, MATLAB, graphml, etc.), and even scale for the human MR derived graphs.  Many other graph services are available from there as well.


### Show some image data to labmates/colleagues?

#### Images

- web-form < 200 GB
- CAJAL < 1 TB
- ndio < 1 TB
- auto-ingest < 2 TB https://github.com/openconnectome/open-connectome/blob/master/ingest/autoingest/verifyjson.py
- (s)ftp/(s)http/open-s3: arbitrary size https://github.com/openconnectome/open-connectome/tree/master/ingest/

#### Graphs

-----

## Computer Vision

#### Stitch and align into volume?

#### Color correct a volume?

- 2D
- 3D


#### Manually annotate some data?

- CATMAID
- knossos
- VAST
- Reconstruct
- ITK-SNAP
….

#### Share annotations (RAMONify)?

csv ingest script (with spec)

#### Proofread and error correct metadata?

- ocpviz: edit metadata
- parity

#### Train my machine vision algorithm on some data?

Training paradigms are different for each use-case.  We provide examples for a random forest training example and a paradigm using ilastik.  Training is typically conducted using standalone functions (v. a distributed LONI approach)

- vesicle RF example
- ilastik example

#### Assess the performance of algorithms?

example (in matlab), of making ROC curves on held out data from a separate volume
example in loni sweeping over a set of hyperparameters

#### Run my machine vision algorithm at scale?

- LONI stuff

-----

## Analysis

### FlashGraph

[FlashGraph](http://www.flashgraph.net/) is an extremely fast, parallelized and highly scalable graph processing engine. It can operate in *Semi-External Memory* mode, meaning the RAM requirements are vastly reduced; this allows users to process graphs with billions of vertices even on personal computers.

FlashGraph is written in `C++` for speed, but has an `R` interface, [FlashGraphR](https://github.com/icoming/FlashGraph/wiki/FlashGraphR-Quick-Start-Guide). Documentaion on how to install and use FlashGraph can be found [here](https://github.com/icoming/FlashGraph/wiki).

### m2g

#### How do I generate multiscale graphs from MRI data?

We have developed a one-click multi-modal MRI processing pipeline called [m2g](http://m2g.io) which estimates structural graphs from diffusion MRI. The pipeline and its sourcecode can be found on [github](https://github.com/openconnectome/m2g), and full documentation exists on our [m2g webpage](http://m2g.io).  

We offer several ways to interact with m2g:

- Our [Webservice](http://openconnecto.me/graph-services/c4/) allows users to upload a brain image and have a connectome emailed to them after it has been generated.
- A [Standalone Cluster](http://m2g.io/sphinx/services.html#using-m2g-on-captive-cluster) exists on which we process large volumes of data with collaborators.
- An [Amazon EC2](http://m2g.io/sphinx/services.html#using-m2g-in-an-ami) machine image with the NeuroData stack and the m2g pipeline installed is publicly available for use.
- Our [graph service engine](http://mrbrain.cs.jhu.edu/graph-services/welcome/) hosts graph data of a variety of species and scales, as well as enables downsampling and type conversion of graphs.
- Pipeline derivatives and graphs may also be found in our public s3 bucket. Contact [support](mailto:support@neurodata.io) to gain access.

#### How do I know that the graphs I made are reliable?

We assess the quality of our graphs using a metric called reliability. Several test-retest (TRT) datasets have been chosen as benchmarks for performance, and a detailed explanation of how they were evaluated and their performance can be found on our [validation page](http://m2g.io/tutorials/validation.html).

#### Where can I find public data so that I may get started?

We have processed and share several publicly available datasets on our s3 bucket. Look at our [available data](http://m2g.io/tutorials/available_data.html) page for information about reading and accessing this data.

#### How long does it take to run the pipeline?

In addition to recording reliability performance on our benchmark datasets (see above), we record [timing](http://m2g.io/tutorials/validation.html) as well. Currently, on our cluster, the pipeline takes approximately 6 hours/subject/core when running at saturation to produce small graphs.

### Query the scene?

- CAJAL
- ndio

### Estimate statistical properties?

-----

## Other stuff

### Computing Resources

### Third Party Tools Integration Status

#### ITK Snap

Works in manno for annotation purposes (see http://docs.neurodata.io/manno).

#### VAST

VAST was developed by Daniel Berger at MIT and Harvard and can pull image data from OpenConnectome project for annotating EM volumes.  Details are available here:  https://software.rc.fas.harvard.edu/lichtman/vast/  (please also see details in the linked manual).

#### Others
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
