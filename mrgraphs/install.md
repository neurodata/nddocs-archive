---
title: ndmg install
layout: default
---

## Installing ndmg
Installing **ndmg** is very simple! We have a few dependencies which must be installed, but once that's taken care of you are ready to dive in!

**ndmg** relies on: [FSL](http://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FslInstallation), [DiPy](http://nipy.org/dipy/), [networkx](https://networkx.github.io/), and [nibabel](http://nipy.org/nibabel/), as well as [numpy](http://www.numpy.org/) and [scipy](http://www.scipy.org/). You should install FSL through the instructions on their website. Then, you can install **ndmg** with the following command and it'll handle the rest:

    pip install ndmg

On some systems, python-igraph requires a separate pip install, and may require the separate compilation of the igraph C core.  Please see the igraph website for additional details.

