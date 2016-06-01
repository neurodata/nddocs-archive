---
title: ND Paper 2016 - Explore
layout: default
---

## Images

### *NeuroDataViz*

We have curated a collection of image datasets and setup pre-configured *NeuroDataViz* projects for them. This data is available by visiting [viz.neurodata.io](http://viz.neurodata.io) and clicking on "Data".

The data in Figure 2(a) was collected by Bobby Kasthuri in 2011 and published in 2015. The global dataset is available at [viz.neurodata.io/project/kasthuri11cc](http://viz.neurodata.io/project/kasthuri11cc). The data used to generate the figure was taken from the following subregion: [viz.neurodata.io/project/kasthuri11cc/xy/2/2439/4281/1100/](http://viz.neurodata.io/project/kasthuri11cc/xy/2/2439/4281/1100/). In *NDStore* parlance, the data is identified as follows:

| Key | Value |
| ------ | ------------ |
| Token | kasthuri11cc |
| Channel | image |
| Resolution | 2 |
| x-coordinate | 2439 |
| y-coordinate | 4281 |
| z-coordinate | 1100 |

This data can be downloaded using raw *NDStore* APIs, *CAJAL*, or *ndio*.

In addition to the data exhibited in Figure 2, we wish to highlight the following published 8-bit EM Datasets:

|Dataset | URL |
|--------|-----|
| Mouse S1 (Kasthuri et al., 2015) | [http://viz.neurodata.io/dataview/mouseS1](http://viz.neurodata.io/dataview/mouseS1) |
| Mouse V1 (Bock et al., 2011) | [http://viz.neurodata.io/dataview/bock11](http://viz.neurodata.io/dataview/bock11) |
| Rat Hippocampal CA1 neuropil (Harris et al., 2015) | [http://viz.neurodata.io/dataview/kharris15](http://viz.neurodata.io/dataview/kharris15) |
| Cardona et al. | [http://viz.neurodata.io/dataview/acardona](http://viz.neurodata.io/dataview/acardona) |
| C. elegans hermaphrodite pharynx (Bhatla et al., 2015) | [http://viz.neurodata.io/dataview/bhatla15](http://viz.neurodata.io/dataview/bhatla15) |
| Fly Medulla	(Takemura et al., 2013) | [http://viz.neurodata.io/dataview/takemura13](http://viz.neurodata.io/dataview/takemura13) |

### *Histogram Explorer*

The *Histogram Explorer* is available at [hx.neurodata.io](http://hx.neurodata.io). An *NDStore* dataset **Token** and **Channel** are required to load histograms and associated statistics. Public tokens and channels are available in Table 1, Table 2, and supplementary material.

#### 8-bit Datasets

Figure 2(b) was generated using Histogram Explorer. To setup the view shown in the figure, first visit [hx.neurodata.io](http://hx.neurodata.io). Enter **kharris15apical** in the Token box, and **em** in the Channel box. Press "Load Histogram" to load the histogram and relevant statistics.

#### 16-bit Datasets

The *Histogram Explorer* can also be used to determine an appropriate "image window" for 16-bit datasets. The image window sets a low bound and high bound for resampling a 16-bit dataset into an 8-bit image. Often, the low bound is set at around the 15% and 25% of the dataset intensity value, and the high bound is set at between 80% and 99%.

To use the tool to resample a dataset, first load a 16-bit token and channel into the Histogram Explorer. A good example token / channel combination is **Ex10R55** and **DAPI_1**. The *Ex10R55* dataset was collected by Weiler et al and published in Nature Scientific Data in 2014 [(Weiler et al., 2014)](http://www.nature.com/articles/sdata201446).

**AB TODO:** Finish this section when histogram for DAPI_1 is generated.


## Annotations

### *NeuroDataViz*

Several of the above mentioned image datasets include paint. However, only a small number of paint datasets include RAMON metadata. The data used in Figure2(c) is a paint dataset that includes RAMON metadata, and is available at [viz.neurodata.io/project/kasthuri2015_ramon_v4](http://viz.neurodata.io/project/kasthuri2015_ramon_v4). The EM layer (**kasthuri11cc**, from *Images*) is used as a base.

The specific data used in Figure 2(c) is available at [viz.neurodata.io/project/kasthuri2015_ramon_v4/xy/2/2439/4281/1100/](http://viz.neurodata.io/project/kasthuri2015_ramon_v4/xy/2/2439/4281/1100/). To bring up object metadata shown in the figure, first mouse over the query tool (the magnifying glass) and select *Synapses* in the dropdown query box. Next, click on the relevant synapse (synapse #37, located between the pink and brown neurons, to the right of the large purple neuron). If you are having trouble identifying the Synapse, the following URL will place a marker at the synapse location (though the overall screen center will be slightly different than the center used in the figure):: [viz.neurodata.io/project/kasthuri2015_ramon_v4/xy/2/2433/4295/1100/marker/](http://viz.neurodata.io/project/kasthuri2015_ramon_v4/xy/2/2433/4295/1100/marker/).

The following projects from the Images table also include annotation data:

|Dataset | URL |
|--------|-----|
| Mouse S1 (Kasthuri et al., 2015) | [http://viz.neurodata.io/dataview/mouseS1](http://viz.neurodata.io/dataview/mouseS1) |
| Rat Hippocampal CA1 neuropil (Harris et al., 2015) | [http://viz.neurodata.io/dataview/kharris15](http://viz.neurodata.io/dataview/kharris15) |
| C. elegans hermaphrodite pharynx (Bhatla et al., 2015) | [http://viz.neurodata.io/dataview/bhatla15](http://viz.neurodata.io/dataview/bhatla15) |
| Fly Medulla	(Takemura et al., 2013) | [http://viz.neurodata.io/dataview/takemura13](http://viz.neurodata.io/dataview/takemura13) |


## Matrices

## Graphs

## Reproducibility

## Links
