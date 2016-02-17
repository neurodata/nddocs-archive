---
title: ndmg data requirements
layout: default
---

## Readying your data
Once **ndmg** is installed, the next thing you need to do is track down your data. If you don't have data readily available, you can [borrow some of ours](http://openconnecto.me/mrdata/share/demo_data.zip). The data you'll need are the following:

- 1 MPRAGE image
- 1 DTI image
- 1 DTI b-values file
- 1 DTI b-vectors file

In the interest of comparing results, **ndmg** performs operations in a predefined *atlas* space. In order for this to work you'll need, who would've guessed, an atlas! We recommend the MNI152 atlas and the Desikan parcellation, and you can [download them here](http://openconnecto.me/mrdata/share/atlas.zip) (if you've downloaded the demo data you're good to go - we thought ahead).

**ndmg** expects the DTI and MPRAGE images in a nifti format, and the b-values and b-vectors files to be ASCII text files with the extensions `.bval` and `.bvec`, respectively. If you are unsure if you data is formatted correctly, please feel free to [download our demo data](http://openconnecto.me/mrdata/share/demo_data.zip) and check for yourself!

