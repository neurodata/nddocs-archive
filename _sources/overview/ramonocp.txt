RAMON + OCP
***********

Our RAMON data standard may be used alone, although is designed for seamless
integration with the Open Connectome Project spatial database.

When interacting with OCP, there are three parts to each request.

- **Target:** This contains information about the project database, including the server, token, and channel.  [WHERE the request is executed]
- **Request:** This is a RESTful call, and is the action of the request (create, read, update, delete) [the ACTION being taken]
- **Payload:** This is the data that is being manipulated by the request, such as a RAMON object.  [WHAT is being affected]

Create:  Create a new (RAMON) object in the database, to include labels and metadata.  Create can also be used to upload image or label data alone.
Update:  Used to update an existing RAMON object in the database
Delete:  Used to delete an existing RAMON object in the database

Reading from the database uses an expanded set of queries to promote flexibility and scientific discovery.  The available RESTful queries are shown below.

RAMON Queries
-------------

* RAMONIdList – This returns a list of ids that meet some list of predicates (e.g. type equal to synapse and status equal to unprocessed)
* imageDense – this returns a RAMONVolume containing a image voxel data in cutout format
* annoDense – this returns a RAMONVolume containing a annotation voxel data in cutout format
* RAMONDense – This returns a RAMON data type associated with a provided id with the voxel data in cutout form.  If no voxel data a warning is given.
* RAMONVoxelList - This returns a RAMON data type associated with a provided id with the voxel data in voxel list form.  If no voxel data a warning is given.
* RAMONMetaOnly - This returns a RAMON data type associated with a provided id with only the metadata fields populated
* imageSlice – this returns a single slice in the desired slice plane in a matrix format of image data
* annoSlice – this returns a single slice in the desired slice plane in a matrix format of annotation data
* overlaySlice – this returns a single slice in the desired slice plane in matrix format of annotation data overlaid onto image data
* RAMONBoundingBox – This returns a bounding box around the RAMON object associated with the provided id
* voxelId – This returns the id of a voxel based on provided x,y,z coordinates

Details of how to Get and Put data, including RAMONObjects, is detailed in the Open Connectome Project RESTful calls section of this documentation,
found here:  http://openconnectome.github.io/open-connectome/

A MATLAB API called CAJAL wraps these functions into a toolbox that is easy to use.
A stripped down version of the data standard and RESTful calls is also available in a beta package called OCPy.
