---
title: ndio Tutorials
layout: default
---

# ndio: Tutorials

* TOC
{:toc}

-----

## Getting Started

-----

- **Downloading and Installing ndio**
    You can download and install ndio automatically using pip, the python package manager. To install, simply open a new terminal window (OSX/Linux) or a command-line window (Windows) and type,

    ```
    pip install ndio
    ```

    You can also install from the raw source using the [GitHub repository](https://github.com/openconnectome/ndio).

- **Installing Requirements**
    If you installed ndio with `pip`, then you should already have all the requisite python libraries. However, if you downloaded the code and are using a development copy, then you can download required libraries with the command

    ```
    pip install -r requirements.txt
    ```

    from the root ndio directory.

    You may also need to install other requirements, depending on your use case. `h5py` is required, which may require that you install `libhdf5`. On Ubuntu, you can run this line:

    ```
    sudo apt-get install libhdf5-serial-dev
    ```

    You will also need numpy and scipy. `numpy` can be installed with pip, and scipy's installation directions are available [here](http://www.scipy.org/install.html).

    `ndio`'s in-house installation script for Ubuntu machines is available in the [TravisCI build file](https://github.com/openconnectome/ndio/blob/master/.travis.yml) inside the repository on GitHub.

- **Using ndio in a Python Script**
    Using ndio is as simple as using any other Python library. Simply add the line,

    ```
    import ndio
    ```

    You can see what version of ndio you have imported with `ndio.version`.

    > <small>Note: There are parts of ndio that are not imported by this single line, because they are too large or require additional non-standard libraries. To learn more about these, go to the page on [Importing ndio](importing.html).</small>

## Learning About the Project

- **How can I get a list of all available public datasets?**

    This tutorial includes information about how to list all open-source, public tokens.

    [How Big is NeuroData?](https://github.com/openconnectome/ndio-demos/blob/master/Logistics/How%20Big%20is%20NeuroData%3F.ipynb)

- **How can I get metadata for a project?**

    This folder includes tutorials on reading and writing metadata to the NeuroData LIM system.

    [LIMS](https://github.com/openconnectome/ndio-demos/tree/master/LIMS)

## Data Download

- **How do I download a 2D image [to use in a PowerPoint or publication or...]?**

    This tutorial shows you how to download an image, save it to disk, or show it inside Python:

    [Downloading an Image](https://github.com/openconnectome/ndio-demos/blob/master/Getting%20Started/Downloading%20an%20Image.ipynb)

- **How do I download a 3D volume?**

    This tutorial shows you how to download a piece of a 3D dense volume (such as a subvolume of image data).

    [Downloading a Volume](https://github.com/openconnectome/ndio-demos/blob/master/Getting%20Started/Downloading%20a%20Volume.ipynb)

- **How do I know what to put in for `x_start`, `x_stop`, etc..?**

    This information can be found by reading the metadata of a project before downloading from it. The following tutorial explains how to get metadata for a project.

    [Getting Project Metadata](https://github.com/openconnectome/ndio-demos/blob/master/Getting%20Started/Getting%20Project%20Metadata.ipynb)

## Converting Data

- **How do I convert data from TIFF to PNG?**

    [Converting Data](https://github.com/openconnectome/ndio-demos/blob/master/Data%20and%20Conversion/Converting%20Data.ipynb)

## Making Your Own Datasets

- **How do I create my own project?**

    Please reach out to us at support@neurodata.io. We'd love to help you get your data online and in the hands of thousands of neuroscientists around the globe!

- **How do I create my own channels (inside my project)?**

    See this tutorial. Be careful when deleting channels! There is no way to undo this.

    [Creating and Deleting Channels](https://github.com/openconnectome/ndio-demos/blob/master/Logistics/Creating%20and%20Deleting%20Channels.ipynb)


## Uploading Data

- **How can I set metadata for one of my projects?**

    This folder includes tutorials on reading and writing metadata to the NeuroData LIM system.

    [LIMS](https://github.com/openconnectome/ndio-demos/tree/master/LIMS)

- **How do I upload volume data to a project?**

    This tutorial shows you how to upload a volume.

    [Uploading a Volume](https://github.com/openconnectome/ndio-demos/blob/master/Logistics/Uploading%20Volume%20(Cutout)%20Data%20From%20an%20HDF5%20File.ipynb)

    This tutorial includes information about how to download data from one location and upload it back to another location. This is useful if you're running your own copy of the OpenConnectome stack.

    [Transferring Data Between Remotes](https://github.com/openconnectome/ndio-demos/blob/master/Logistics/Transferring%20Data%20Between%20Development%20and%20Production%20Servers.ipynb)


# Claims from *Kasthuri, et al. CELL 2015*

## Analysis

- ***The 64,000 um3 box imaged at high resolution had roughly 13.7 million cell profiles in its 1850 sections.***
- ***Count: Dendrites = 193 (92% Spiny)***
- ***Count: Unmyelinated Axons = 1407***
- ***Count: Excitatory (Axons) Synapses = 93%***
- ***There were 1,700 synapses at a density of one synapse per 1.13 μm<sup>3</sup>.***
- ***Neuronal processes (axons and dendrites) occupy 92% of the cellular volume with glial processes, occupying much of the remaining 8%.***
- ***The non-cellular (extracellular) space accounts for 6% of the total volume, less than half the extracellular space estimates from living brains.***
- ***Each excitatory axon establishes slightly more synapses in the volume than each inhibitory axon (∼1.2 synapses/excitatory axon versus ∼0.9 synapses/inhibitory).***
- ***The excitatory-to-inhibitory-synapse ratio (van Vreeswijk and Sompolinsky, 1996 and Wehr and Zador, 2003) is 20.2 for the dendrites of excitatory neurons (1,494 excitatory synapses versus 74 inhibitory synapses), whereas the ratio is only 9.7 (116 excitatory synapses and 12 inhibitory synapses) for the input to inhibitory dendrites.***
- ***Excitatory axons establish synapses mostly on spines (94%; n = 1,406/1,700), and inhibitory axons establish mostly on shafts (81%, n = 70/86).***
- ***The number of vesicles per synaptic varicosity range from 2 to 1,366 for varicosities with one postsynaptic target (mean = 153 ± 127), with significantly greater numbers of vesicles at multi-synaptic varicosities (mean = 200 ± 173; Wilcoxon rank-sum test; p = 0.0005).***
- ***The number of vesicles is not significantly different in excitatory and inhibitory synapses.***
