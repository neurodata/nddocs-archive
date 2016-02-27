---
title: mbcd
layout: default
---

# Mouse Brain Cell Detection Pipeline Deliverable

**January 15, 2016**

*JHU/Applied Physics Laboratory Technical Report and Readme*

To enable the detection of cell clusters at scale, we have developed a generalizable, open source framework.  This framework leverages community tools and custom-built code to efficiently and effectively provide scientific results.

Due to the limited ground truth available (especially dense ground truth) at this time, the focus of this handoff is on providing capability, rather than performance, although we have provided tools and an assessment methodology that can be expanded as truthing data mature.

This tutorial assumes you have access to a nissl stained brain, which may be requested from Cold Spring Harbor Laboratories.  A single slice is shown below. 

![](./images/ndod/PMD2040_slice140_full.png)

This tutorial exists completely standalone from the spatial databases and web backend of neurodata to facilitate computation on large data volumes on disk.  Other tutorials exist for distributed computing using the NeuroData spatial database and tools (including gets/puts of data and annotations).  
 
In the standalone mode, users first specify a directory location where their images reside, and use the included scripts to save files in a format compatible with downstream processing.  The results are saved in a specified output directory for future analysis.  

Users can then choose an image processing or machine vision tool (deep learning with pyCaffe, ilastik, or a MATLAB pre-screening tool), and save the probabilities to disk.  To convert these images to cell clusters, the final step is to threshold and run a connected components analysis on the probability maps.  An optional prototype to compute statistics on each cluster is provided.

![](./images/ndod/ndod_standalone_pipeline.png)

## ndod

The standalone code to process these brains has been integrated into ndparse, the NeuroData Object Detection Package, and is available for use.  Relevant links are provided throughout this document.  

Tutorials for general ndod usage are provided [here](http://docs.neurodata.io/nddocs/index.html#parse).  There are three modules in our strategy of parsing neurodata:  manual annotation (mana), machine annotation (maca), and max annotation, which contains our reference deployment code (maxa).

## Demo

To follow along with the examples in this tutorial, users should first download example classifiers and data [here](http://openconnecto.me/data/public/mbcd/), provided by Cold Spring Harbor Laboratories.

The overall sequence of steps is:

- Matlab:  Format and load data `rename_jp2_mbcd` and `jp2_convert_to_tiff`
- Bash/Python:  Run Ilastik
- Matlab:  Convert and post-process `ilastik_to_tif_mbcd.m` and `cluster_postprocess_mbcd.m`

## Data Input/Output

The data is first converted to a common format.  Reference code is avaiable to take in a directory of JP2 files and output TIF slices for convenience.  This function can be found in ndparse/io (`jp2_convert_to_tiff`), and can be easily adapted to other use cases.  The existing function facilitates the conversion, downsampling and grayscale conversion for downstream processing, as user-modifiable parameters.  

Prior to running this function, an optional file name cleanup function (`rename_jp2`) may be run if desired.  Depending on your local environment, small changes may be required to modify paths.

The functions and examples referenced in this section can be found in the maca repo in [io](https://github.com/openconnectome/ndod/tree/master/maca/packages/mbcd).  

## Manual Annotation

Prior to training a classifier, dense ground truth is needed.  We provide a tool called [mana](http://docs.neurodata.io/nddocs/mana/) to annotate ground truth.  This interfaces with ITK-Snap and a well-defined protocol that has been used for many neuroimaging tasks.

Readers and writers to convert data to nifti format from standalone files are available (`mana_get_local` and `mana_put_local`).  These functions can be found in the maca repo in [mbcd](https://github.com/openconnectome/maca/packages/mbcd/).

## Machine Annotation (Pixel Classification)

For the core processing task of cell cluster detection, we provide two primary options: [ilastik](http://ilastik.org) (a random forest based classifier based on texture and image features), and a deep learning method based on [pyCaffe](http://caffe.berkeleyvision.org/).

### Ilastik

For processing in ilastik, users can most simply train a classifier or use the one provided, and use the ilastik GUI to batch process an entire brain. 

Unfortunately, it is memory-intensive (and prohibitive for smaller workstations) to operate on an entire nissl brain in memory, and so we provide examples of using ilastik in a batch mode in [maca](http://docs.neurodata.io/nddocs/maca/).

In brief, users have two choices: either a command line bash call or a python option.  We recommend processing on a single slice of brain and writing a wrapper to loop through directories of interest in your local computational environment.  More details are explained at the above link.

Ilastik will work with grayscale or RGB images.  A script is provided [here](https://github.com/neurodata/ndod/tree/master/maca/packages/mbcd/) to take ilastik hdf5 probability output and convert to tif as a convenience function.  The example classifier assumes RGB data and a downsampling factor of 0.25 (in XY).

#### Bash

This option should "just work" if you have ilastik on your system.  We have tested using OSX and Linux.  Ilastik 1.1.8 is recommended.

~~~
#<ilastik executable> --headless
#--project <project file>.ilp
#--output_format hdf5
#--output_filename_format <output filename>
#<path and filename for raw data>/<hdf5 dataset>
~~~

#### Python

This option requires additional configuration that is system dependent.  We recommend conda.  Users may also need to install vigra.

~~~
# Install
conda create -n ilastik-devel -c ilastik ilastik-everything-but-tracking

# Run
CONDA_ROOT=$(conda info --root)
${CONDA_ROOT}/envs/ilastik-devel/run_ilastik.sh
~~~

~~~
# Example of running a single tif file 
# through default ilastik classifier.

inputImage = '<full path to image>/PMD2040_0100_rgb_025.tif'
ilpfile = '<full path to classifier>/mbcd_training_new.ilp'

import ilastik, ilastik_main
import os

#Override lazyflow environment settings
os.environ["LAZYFLOW_THREADS"] = "4"
os.environ["LAZYFLOW_TOTAL_RAM_MB"] = "4096"
parsed_args, workflow_cmdline_args = ilastik_main.parser.parse_known_args()


parsed_args.headless = True
parsed_args.project='/Users/graywr1/code/PMD2040/Training_new.ilp'

workflow_cmdline_args = [inputImage]

print workflow_cmdline_args
ilastik_main.main(parsed_args, workflow_cmdline_args)

~~~

An example of thresholded detections from running the provided ilastik classifier are shown below, as an entire slice and zoomed in as a detail view:

![](./images/ndod/PMD2040_slice140_overlay_full.png)

![](./images/ndod/PMD2040_slice140_overlay_zoom.png)

To convert the ilastik HDF5 output to TIF, please use the following convenience function:  `ilastik_to_tif_mbcd.m,` located [here](https://github.com/neurodata/ndod/tree/master/maca/packages/mbcd/).
 
### Deep Learning

Please see the nddl Deep Learning page [here](http://docs.neurodata.io/nddocs/nddl.html).  Note that the current  deep learning classifier was trained and designed to run with the provided point-based ground truth and is grayscale (single channel, downsample factor of 0.25), although the method itself is agnostic to these choices.

## Post Processing (Object Detection)

The primary purpose of this tutorial is to generate clusters of cell detections.  However, we provide a simple function tothreshold, perform connected components, and extract basic statistics from each cluster.  

This function may actually be used in two ways:  

- as an object detection post-processing step
- as an image processing data-reduction step to filter putative cell cluster locations based on intensity.  This offers the possibility of a dramatic reduction in processing time, as far fewer pixels will need to be evaluated.  Because the deep learning methods are especially computationally expensive, users might wish to use this step to remove background and other pixels that are very unlikely to contain target from a classifier testing paradigm.

The prototype code for post-processing can be found [here](https://github.com/neurodata/ndod/tree/master/maca/packages/mbcd/).  `ilastik_to_tif_mbcd.m` saves ilastik outputs as a uint16 tif file, and `cluster_postprocess.m` labels each cluster and extracts basic stats.

## Outlook and Engineering Recommendations

Finding cell clusters in nissl stained images can be challenging, especially at scale, but the tools provided give two distinct solutions for processing.  These tools exist as standalone modules, which can be easily integrated into a processing chain suitable for a local workstation or cluster environment.  

Two possible options for scalable frameworks are the [LONI Pipeline](http://pipeline.loni.usc.edu), which runs in standalone or cluster mode and is used across a variety of NeuroData projects.  A second option would be to create an end to end Python "driver," which has three distinct steps:  data input, pixel classification, and object-detection/post-processing.  The code referenced in this example is python and MATLAB based; a wrapper for calling matlab functions from Python is available [here](https://github.com/openconnectome/CAJAL/blob/master/api/matlab/wrapper/basicWrapper.py).

To improve the results, we recommend two actions for future work:

- the creation of dense ground truth suitable for training and evaluation
- work to separate cell clusters - [SLIC](http://scikit-image.org/docs/dev/api/skimage.segmentation.html#skimage.segmentation.slic) based on putative cell sizes might be an easy first step; also framing the problem as a deep learning regression problem might be fruitful. 

Finally, although this effort was more focused on capability creation rather than performance, the precision-recall code [here](https://github.com/openconnectome/vesicle/blob/master/packages/vesiclerf/tools/pr_evaluate_full.m) or [here](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_recall_fscore_support.html), may be useful in computing metrics once the classifiers are finalized.  This code is generalizable and the version in the vesicle repository attempts to account for some common failure modes like double-counting truth objects.  

