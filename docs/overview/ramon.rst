RAMON Data Standard
*********************

Overview
--------

RAMON An acknowledged challenge in the connectomics field is annotation representation and
its impact on software and institution-level interoperability.

As the field grows and data volumes increase, the sharing of data through remote and programmatic
interfaces and the application of community developed algorithms and software will become common.
Answering this challenge requires scene parsing, rather than simply segmentation; the rich semantic
annotations are critical to inferring graph structure and understanding the function and structure of
neuronal circuits. We developed a standard for annotation metadata, which
we call the Reusable Annotation Markup for Open Neuroscience (RAMON).

RAMON defines a minimum set of annotation types and associated metadata that capture important
biological information and build the relationships between annotations that are critical for connectome
generation and neuroscience exploration. Annotation metadata is trivially extensible through custom, user defined key-value pairs.
Thisis not a formal ontology; rather it facilitates the development of software and tools by providing a flexible,
yet reliable, standard for representing annotation data. For example, our synapse annotation type has fields
such as weight, type, confidence, associated neural segments, and is extensible with arbitrary, searchable
key-value pairs.

RAMON types
-----------

There are currently 9 RAMON types:

RAMONBase
===============
* Superclass to all RAMON data types
* Contains information common to all annotations
* Is not used directly by the OCP backend infrastructure - used for building more complicated objects

Properties
~~~~~~~~~~
* id (uint32): **Primary Key** Assigned by the OCP database on upload, or set manually
* confidence (float): Indicates estimated confidence in an annotation [0,1]
* dynamicMetadata (string): a flexible key-value pair store
* status (int): used to indicate processing status
* author (string): indicating who created the annotation

RAMONNeuron
===============
Container for assembling SEGMENTs.  Useful for building up complete neurons; each SEGMENT has its own voxel data and properties.

Properties
~~~~~~~~~~
* segments (int[]): A collection of segments associated with this neuron.
* RAMONBase fields

RAMONVolume
===============
Used to store pixel label information; inherited by many other types.  This object type is often used to post
raw label data, which may be linked later with metadata.

* Inherits from RAMONBase
* Superclass to all RAMON data types that contain voxel data

Voxel data can be represented as:

* Cutout – 3D array with unlabeled voxels set to 0 and labeled voxels set to the object’s ID
* Voxel List – an Nx3 array representing the x,y,z coordinates of all labeled voxels

Properties
~~~~~~~~~~

* xyzOffset (int[3]):  x,y,z coordinates of the minimum corner of the cube (if data is a cutout), otherwise empty
* resolution (int): level in the database resolution hierarchy - defaults to project resolution
* cutout (int32):  dense matrix of data; left empty when using voxel lists
* voxels (int32[][3]): list of voxels making up annotation
* RAMONBase fields

RAMONGeneric
===============
Extensible, used to specify arbitrary, user-defined information for a voxel set.  Used to create RAMON objects
without an assigned type or special fields

Properties
~~~~~~~~~~

* RAMONBase, RAMONVolume fields

RAMONSynapse
===============
Junction between two NEURONs is used to connect SEGMENTs when building a GRAPH

Properties
~~~~~~~~~~

* synapsetype (int):  Used to specify a synapse type (e.g., excitatory)
* weight (float):  Synaptic weight, as defined by the user
* segments (int[][2]): Segments associated with this synapse, and their direction
* RAMONBase, RAMONVolume fields

RAMONSegment
===============
A labeled region of a neuron (e.g., a neurite); typically a contiguous voxel set.

Properties
~~~~~~~~~~

* class (int):  Specifies the type of segment (e.g., axon, dendrite, soma)
* neuron (int):  Neuron parent associated with this segment.  No more than one id permitted
* synapses (int[]):  Synapses associated with this segment.
* organelles (int[]): Organelle IDs associated with this segment.  This is a unidirectional linkage
* RAMONBase, RAMONVolume fields

RAMONOrganelle
===============
Represents internal cell structures (e.g., mitochondria, vesicles).

Properties
~~~~~~~~~~

* organelleclass (int): Used to specify the organelle type (e.g., mitochondria)
* RAMONBase, RAMONVolume fields

RAMONROI (proposed)
===================
An attributed region of interest, often used for atlases and other collections of labels.  In combination with key-value specified metadata, this can be used to define any object type,
although query support may be more limited than if the more defined data standard is used.

Properties
~~~~~~~~~~

* parent (int): ids of parent objects
* child (int): ids of children objects
* RAMONBase, RAMONVolume fields

RAMONNode
===============
Sparse annotation format for tracing processes or objects.

Properties
~~~~~~~~~~

* nodetype: TBD
* parentid: TBD
* skeletonid: TBD
* radius: TBD
* children: TBD
* location: TBD
* RAMONBase: TBD

RAMONSkeleton
===============
An (organized) collection of NODEs, often used to represent a NEURON or arbor.

Properties
~~~~~~~~~~

* skeletontype: TBD
* rootnode: TBD

**Note that the following data types have been deprecated and should not be used:  RAMONSeed, RAMONAttributedRegion, and RAMONNonNeuron**

RAMON Inheritance Diagram
=========================

A visual depiction of the inheritance between the different RAMON types can be seen in the picture below.

.. image:: ../images/ramon_inheritance.png

RAMON Queries
-------------

RAMON Enumerations
------------------
