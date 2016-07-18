---
title: ndmg web services
layout: default
---

## Web Services

There are two web services associated with the **ndmg** pipeline which allow you to build and access graphs: *c4* and *mr-grutedb*.

### [c4](http://openconnecto.me/graph-services/c4/)
The *c4* (Community Connectomics via Cloud Computing) web service enables users to upload data and build their own connectome from unprocessed data. The webservice accepts as input the following files: DTI image (nifti format), MPRAGE/T1 image (nifti format), B-value file (ASCII text), and the B-vector file (ASCII text). The tool also asks which space you would like your graph aligned to (with the default being MNI152), and the scale of the derived graph.

Once uploaded and submitted, your job will be placed on the stack of our internal queue and being processing. Once the pipeline comlpetes (which takes < 1hr once the job has reached the top of the queue), you will be emailed with a public link to your graph and derivatives. This service is, of course, currently completely free of charge to our users.

It is **very important** to note that we **do not accept non-deidentified data**. Our server is public facing and we have gone through exactly no hoops to be HIPPA compliant, so require that all data uploaded to us is completely deidentified prior to transfer.

### [mr-grutedb](http://openconnecto.me/graph-services/download/)
The *mr-grutedb* (MRI with rich Graph AttribUTE DataBase) web service enables users to inspect and download graphs derived from various modalities and access them in a variety of common formats for interfacing with different processing engines.

Several species exist, though in largest abbundance we distribute human connectomes here. The naming convention for the graphs in the *human* table is as follows: `{dataset}_{subjectid}_{scanid}_{scale}`. The dataset pertains to the study which collected the data; the subject id is the particular identifier of the person who was scanned/mapped; the scan id is the identifier of the scan number which was taken on this subject in this study; the scale indicates the parcellation/atlas on which the graph was mapped (i.e. the set of nodes in the graph).

As with our other web service, all data is freely accessible and de-identified/publicly available.
