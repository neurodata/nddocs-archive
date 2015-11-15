---
title: ndio Tutorials
layout: default
---

# ndio: Tutorials

-----

## Getting Started

-----

### Downloading and Installing ndio
You can download and install ndio automatically using pip, the python package manager. To install, simply open a new terminal window (OSX/Linux) or a command-line window (Windows) and type,

~~~
pip install ndio
~~~

You can also install from the raw source using the [GitHub repository](https://github.com/openconnectome/ndio).

### Installing Requirements
If you installed ndio with `pip`, then you should already have all the requisite python libraries. However, if you downloaded the code and are using a development copy, then you can download required libraries with the command

~~~
pip install -r requirements.txt
~~~

from the root ndio directory.

-----

### Using ndio in a Python Script
Using ndio is as simple as using any other Python library. Simply add the line,

~~~
import ndio
~~~
{: .language-python}

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
