---
title: Tutorials
layout: default
---

Tutorials

# Infrastructure

## Look at some data?

### Images

# web viewers
ocpviz:
- http://brainviz1.cs.jhu.edu/ocp/viz/project/kharris15apical/
- http://openconnecto.me/ocp/viz/project/kasthuri15ramon/
- catmaid

# local client viewers:
- ITK-SNAP
- bigdataviewer
- vaa3d
- knossos
- viking
- neutube
- janelia-workstation
- reconstruct

### Graphs

- web viewer: graph explorer
- local client viewers: gephi


## Download some data to play with on my computer?

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

## Stitch and align into volume?

## Color correct a volume?

- 2D
- 3D

# Computer Vision

## Manually annotate some data?

- CATMAID
- knossos
- VAST
- Reconstruct
- ITK-SNAP
….

## Share annotations (RAMONify)?

csv ingest script (with spec)

## Proofread and error correct metadata?

- ocpviz: edit metadata
- parity

## Train my machine vision algorithm on some data?

Training paradigms are different for each use-case.  We provide examples for a random forest training example and a paradigm using ilastik.  Training is typically conducted using standalone functions (v. a distributed LONI approach)

- vesicle RF example
- ilastik example

## Assess the performance of algorithms?

example (in matlab), of making ROC curves on held out data from a separate volume
example in loni sweeping over a set of hyperparameters

## Run my machine vision algorithm at scale?
LONI stuff

# Analysis

## Query the scene?

- CAJAL
- ndio

## Estimate statistical properties?
