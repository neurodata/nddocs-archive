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

### *Histogram Explorer*

The *Histogram Explorer* is available at [hx.neurodata.io](http://hx.neurodata.io). An *NDStore* dataset **Token** and **Channel** are required to load histograms and associated statistics.

#### 8-bit Datasets

Figure 2(b) was generated using Histogram Explorer. To setup the view shown in the figure, first visit [hx.neurodata.io](http://hx.neurodata.io). Enter **kharris15apical** in the Token box, and **em** in the Channel box. Press "Load Histogram" to load the histogram and relevant statistics.

## Annotations

### *NeuroDataViz*

Several of the above mentioned image datasets include paint. The data used in Figure2(c) is a paint dataset that includes RAMON metadata, and is available at [viz.neurodata.io/project/kasthuri2015_ramon_v4](http://viz.neurodata.io/project/kasthuri2015_ramon_v4). The EM layer (**kasthuri11cc**, from *Images*) is used as a base.

The specific data used in Figure 2(c) is available at [viz.neurodata.io/project/kasthuri2015_ramon_v4/xy/2/2439/4281/1100/](http://viz.neurodata.io/project/kasthuri2015_ramon_v4/xy/2/2439/4281/1100/). To bring up object metadata shown in the figure, first mouse over the query tool (the magnifying glass) and select *Synapses* in the dropdown query box. Next, click on the relevant synapse (synapse #37, located between the pink and brown neurons, to the right of the large purple neuron). If you are having trouble identifying the Synapse, the following URL will place a marker at the synapse location (though the overall screen center will be slightly different than the center used in the figure):: [viz.neurodata.io/project/kasthuri2015_ramon_v4/xy/2/2433/4295/1100/marker/](http://viz.neurodata.io/project/kasthuri2015_ramon_v4/xy/2/2433/4295/1100/marker/).
