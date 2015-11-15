---
title: Importing ndio
layout: default
---

# ndio: Importing
ndio consists of many submodules that import different, non-standard libraries depending on their function. For instance, `ndio.convert.hdf5` imports the `h5py` package to handle importing and exporting HDF5 files.

However, not all Python distributions or computers have all of these packages -- for instance, it is unlikely a new installation of Python has the `h5py` library installed -- and so rather than requiring all of these libraries to be installed prior to using ndio, ndio allows you to selectively import its submodules.

Below is a list of each submodule, as well as its requirements.

## Submodules

All modules require `numpy`.

| Submodule | Description | Requirements |
|-------------|-------------|--------------|
| `convert.hdf5` | Conversion of data to and from the HDF5 data standard | `h5py` |
| `convert.png` | Conversion of data to and from the PNG image format | `PIL` |
| `convert.tiff` | Conversion of data to and from the TIFF image format | `PIL` |
| `ramon` | Storage of datatypes in the RAMON data standard | None |
| `remote` | Handles uploads and downloads of data from a non-local server | `requests` |
| `utils` | Some extraneous functions to assist in performing actions on data | None |

## Installing Requirements
If you installed ndio with `pip`, then you should already have all the requisite python libraries. However, if you downloaded the code and are using a development copy, then you can download required libraries with the command

~~~
pip install -r requirements.txt
~~~

from the root ndio directory.
