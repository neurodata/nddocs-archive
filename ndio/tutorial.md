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
