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

    You can also install from the raw source using the [GitHub repository](https://github.com/neurodata/ndio).

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

## Getting started with ndio


   - This tutorial includes information about [getting started with ndio](https://github.com/neurodata/ndiodemos/blob/master/Getting%20Started.ipynb)

   - Additional examples (still in development) are available [here](https://github.com/neurodata/ndpaper/blob/gh-pages/neurocartography/claims).