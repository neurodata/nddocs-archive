# mano:  A Lightweight Annotation Protocol for the NeuroData Project using ITK-Snap and CAJAL 

mano provides a protocol for creating NeuroData compatible manual annotations, leveraging [ITK Snap](http://www.itksnap.org/).  This tool allows users to quickly create and upload annotations to the Open Connectome Project for science, machine learning, and other applications.  This protocol uses the NIFTI format as a method to exchange data; other tools such as MRIStudio may also be able to use this protocol (but have not been extensively tested).

![](images/ndod/mano_itk_example.jpg)

## Introduction

mano is a lightweight protocol leveraging the NeuroData Spatial database and the CAJAL toolbox.  This provides an easy method for users to create, upload, and manage manual annotations across a variety of use-cases and datasets.  The figure below outlines a sample workflow.

![](./images/ndod/mano_intro.png)

## Configuration

In order to use this truthing protocol, users should have the following software:

 * [CAJAL Toolbox](http://github.com/openconnectome/cajal)
 * [NIFTI Tools (distributed as part of CAJAL)](http://www.mathworks.com/matlabcentral/fileexchange/8797-tools-for-nifti-and-analyze-image)
 * [ITK-Snap v 3.x](http://www.itksnap.org/)
 * [MATLAB 2014a+](http://www.mathworks.com)
 * [The ndod toolbox](http://github.com/openconnectome/mano)

 Please follow the instructions with each program to download and install, and setup cajal and ndod (as an installed toolbox).
 For the neurodata tools, you can be up and running with the following commands within MATLAB.  Please replace values inside ```< >``` (including the brackets) with the correct paths for your system.

 ~~~
   run('<cajal root directory>/tools/matlab_install/setupEnvironment.m')
   run('<cajal root directory>/cajal.m')
   cajal.installToolbox('<ndod root directory>/setup.m')
~~~
*This tool uses ITK-Snap for annotating, and mano+CAJAL to pull and push data appropriately.  It is not necessary for all annotators to use MATLAB and CAJAL, as long as they have a mechanism (such as a grad student) to help pull and push data.  Annotators only need to be able to load, annotate, and save within ITK Snap.*

## Basic Usage

### Protocol

- Identify a region of interest in OCP, and note the data server, token, channel, resolution, and coordinates
- Create a query, using the instructions for CAJAL
- Run *mano_getImage.m* to generate an image volume suitable for annotation in ITK Snap
- Annotate: Once the data has been formatted for ITK Snap, the user should open the ITK SNAP application and load in the NIFTI data saved during the data acquisition step. Then using the brush tool, annotate the data as desired. Users can choose to use separate colors for each annotation or rely on a connected component post-processing step to identify each object (best for sparse data)
- Save Segmentation Image: (ITK Snap Menu > Segmentation > Save Segmentation Image). Choose a name that you will be able to easily correlate to its appropriate volume image volume.
- Run *mano_putAnno.m*, specifying the server, token, annotation file, and query used to download the underlying image. Users may choose to run a simple connected component post-processing step to break each group of connected pixels (3D) into a separate ID. More complicated post-processing should be done outside of the tool, with the result uploaded using the ocp_upload_dense.m function (see CAJAL documentation).

Usage Notes
-----------

- For more information on painting annotations, please follow the steps outlined [here](http://www.itksnap.org/pmwiki/pmwiki.php?n=Documentation.TutorialSectionManualSegmentation).
- Currently, only single channel 8-bit image data is supported
- ITK-Snap is compatible with a variety of input data formats; the most straightforward is NIFTI, a general purpose neuroimaging format. On laptops or smaller workstations, only a small portion of a slice/volume should be truthed at a time for memory reasons.
- *run_mano_example.m* provides a minimal working example to use as a starting point.

Example
-------

The following code demonstrates the mano protocol.  A few mitochondria have been labeled as an example.  The example script should take approximately 10 seconds to complete.

~~~
  function run_mano_example()
  % mano Example
  % mano starter to demonstrate protocol functionality.  All required inputs
  % are hardcoded for this demo.  Paths are hardcoded for Linux/Mac.
  %
  % This example should be run from the code directory because of the
  % relative paths

  xstart = 5472;
  xstop = xstart + 512;
  ystart = 8712;
  ystop = ystart + 512;
  zstart = 1020;
  zstop = zstart + 16;

  resolution = 1;

  query = OCPQuery;
  query.setType(eOCPQueryType.imageDense);
  query.setCutoutArgs([xstart, xstop],[ystart,ystop],[zstart,zstop],resolution);

  save('../data/queryFileTest.mat','query')
  %% Servers and tokens - alter appropriately
  server = 'openconnecto.me';
  token = 'kasthuri11cc';
  channel = 'image';
  serverUp = 'openconnecto.me';
  tokenUp = 'mano';
  channelUp = 'mito';
  %% Run mano
  mano_getImage(server,token,channel,'../data/queryFileTest','../data/testitk.nii',0)

  % Manual annotation step happens here
  mano_putAnno(serverUp,tokenUp,channelUp,'../data/queryFileTest','../data/mito_seg_example.nii.gz','RAMONOrganelle', 1,0)
~~~

Validation
----------

The result of the example script can be accessed using this [link](http://openconnecto.me/ocp/overlay/0.6/openconnecto.me/kasthuri11cc/image/openconnecto.me/mano/mito/xy/1/5472,5972/8712,9212/1031/).

Note that the server and token pair listed here are public but read-only and other data may be pre-existing.  Please create your own projects for testing and annotating!

![](./images/ndod/mano_example_v2.png)

Notes
-----

Currently, mano only supports 8-bit image data as input, and 32-bit annotation data as output.  If your data is another type (e.g., RGB32), please follow these steps to get your data into a NIFTI file.
Once your data is in a NIFTI format, you can seamlessly use the rest of the protocol (annotation and upload).  We will be making additional enhancements to simplify this process in the coming months.

- Get an HDF5 cutout of your data, following the instructions [here](http://docs.neurodata.io/open-connectome/api/data_api.html#get).
- Open your hdf5 file in matlab.  This can typically be accomplished with the following command:  

~~~
im = h5read(<path to data>, '/default/CUTOUT')
~~~

- If you have difficulty with this step, try viewing the structure of your data using [HDFView](https://www.hdfgroup.org/products/java/hdfview/), a free cross-platform tool.
- Next save your nifti data:

~~~
  nii = make_nii(im);
  save_nii(nii, fileOut);
~~~

- And finally be sure to manually create and save your query using the instructions provided in CAJAL (or the demo script):

~~~
  query = OCPQuery;
  query.setType(eOCPQueryType.imageDense);
  query.setCutoutArgs([xstart, xstop],[ystart,ystop],[zstart,zstop],resolution);
~~~

This initial version of mano is an annotation protocol that depends on ITKSnap.  So any annotations that are possible in ITKSnap are possible in mano.  We do not currently support metadata export, or data downloads other than 8-bit, single channel. 

## Support

If you have questions about ndod, or have data to analyze, let us know:  support@neurodata.io
