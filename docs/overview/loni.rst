LONI Pipeline
*************

The `LONI Pipeline`_ tool sits on top of the system scheduler (Son of Grid Engine, for instance), and allows the user to easily string together modules (i.e. single commandline executable calls) to form workflows. This environment is our choice tool for creating pipelines, as it allows us to easily pipe outputs from one module to the input of another.

An `example LONI Module`_ from one of our projects, `m2g`_, can be used as a reference when creating your own modules.

If you are looking for more guidance when creating modules, checkout LONI's `tutorial videos`_.


.. _LONI Pipeline: http://pipeline.loni.usc.edu
.. _example LONI Module: https://github.com/openconnectome/m2g/blob/master/library/modules/extract_b0.pipe
.. _m2g: http://m2g.io
.. _tutorial videos: http://pipeline.loni.usc.edu/learn/basic-videos/
