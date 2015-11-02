---
title: Data Map
layout: default
---

# Datamap

This page provides links and examples of public tokens.  

## Kasthuri2015 AC3 and AC4 Data

This data is related to the recently published <a href="http://cell.com/cell/abstract/S0092-8674(15)00824-7">Cell Paper</a> entitled a *Saturated Reconstruction of a Volume of Neocortex*.  AC3 and AC4 are small reference datasets containing a variety of manually annotated “gold standard”
annotations and corresponding machine vision results.  These data are found on
the server openconnecto.me.  Clicking on the channel name will lead to an example slice in your browser.

 

| Token  | Channel             | Description                              | X Extent   | Y Extent   | Z Extent   | Resolution |
|--------|---------------------|------------------------------------------|------------|------------|------------|------------|
| ac3ac4 | <a href="http://openconnecto.me/ocp/overlay/0.6/openconnecto.me/kasthuri11cc/image/openconnecto.me/ac3ac4/ac3_neuron_truth/xy/1/5472,6496/8712,9736/1205/">ac3\_neuron\_truth</a>  | raw neuron label gold standard data      | 5472, 6496  | 8712, 9736  | 1000, 1256 | 1        |                                                                                              
| ac3ac4 | <a href="http://openconnecto.me/ocp/overlay/0.6/openconnecto.me/kasthuri11cc/image/openconnecto.me/ac3ac4/ac3_synapse_truth/xy/1/5472,6496/8712,9736/1205/">ac3\_synapse\_truth </a>| raw synapse label gold standard data     | 5472, 6496  | 8712, 9736  | 1000, 1256 | 1        |
| ac3ac4 | <a href="http://openconnecto.me/ocp/overlay/0.6/openconnecto.me/kasthuri11cc/image/openconnecto.me/ac3ac4/ac3membraneIDSIA/xy/1/5472,6496/8712,9736/1205/">ac3membraneIDSIA</a>  | computer vision membranes from isbi 2013 | 5472, 6496  | 8712, 9736  | 1156, 1256 | 1        |
| ac3ac4 | <a href="http://openconnecto.me/ocp/overlay/0.6/openconnecto.me/kasthuri11cc/image/openconnecto.me/ac3ac4/ac4_neuron_truth/xy/1/4400,5424/5440,6464/1120/">ac4\_neuron\_truth</a> | raw neuron label gold standard data      | 4400, 5424 | 5440, 6464 | 1100, 1200 | 1          |
| ac3ac4 | <a href="http://openconnecto.me/ocp/overlay/0.6/openconnecto.me/kasthuri11cc/image/openconnecto.me/ac3ac4/ac4_synapse_truth/xy/1/4400,5424/5440,6464/1120/">ac4\_synapse\_truth</a> | raw synapse label gold standard data     | 4400, 5424 | 5440, 6464 | 1100, 1200 | 1          |
| ac3ac4 | <a href="http://openconnecto.me/ocp/overlay/0.6/openconnecto.me/kasthuri11cc/image/openconnecto.me/ac3ac4/ac4membraneIDSIA/xy/1/4400,5424/5440,6464/1120/">ac4membraneIDSIA</a>   | computer vision membranes from isbi 2013 | 4400, 5424 | 5440, 6464 | 1100, 1200 | 1       |

## Kasthuri2015 Computer Vision results

These annotations were produced with a variety of machine vision algorithms (documented elsewhere).  These may be used as inputs to algorithms or for comparison purposes (citations to follow).

| Token  | Channel             | Description                              | X Extent   | Y Extent   | Z Extent   | Resolution |
|--------|---------------------|------------------------------------------|------------|------------|------------|------------|
| cv_kasthuri11_membrane_2014 | <a href="http://openconnecto.me/ocp/overlay/0.3/openconnecto.me/kasthuri11cc/image/openconnecto.me/cv_kasthuri11_membrane_2014/image/xy/1/4400,5424/5440,6464/920/">image </a>  | computer vision membrane detection reference for kasthuri volume | 2300, 8300  | 4300, 9300  | 1, 1850 | 1 |
| cv_kasthuri11_vesicle_2014 | <a href="http://openconnecto.me/ocp/overlay/0.3/openconnecto.me/kasthuri11cc/image/openconnecto.me/cv_kasthuri11_vesicle_2014/annotation/xy/1/4400,5424/5440,6464/920/">annotation</a>  | computer vision vesicle detection reference for kasthuri volume | 4400, 5424  | 5440, 6464  | 1100, 1200 | 1 |
| cv_ac3_membrane_2014 | <a href="http://openconnecto.me/ocp/overlay/0.3/openconnecto.me/kasthuri11cc/image/openconnecto.me/cv_ac3_membrane_2014/image/xy/1/5500,6500/8500,9500/1000/"> image </a> | computer vision membrane detection reference for ac3 created for i2g paper   | 5200, 6700  | 8500, 10000  | 975, 1275 | 1  |
| cv_ac3_vesicle_2014 | <a href="http://openconnecto.me/ocp/overlay/0.3/openconnecto.me/kasthuri11cc/image/openconnecto.me/cv_ac3_vesicle_2014/annotation/xy/1/5500,6500/8500,9500/1000/">annotation </a>  | computer vision vesicle detection for i2g paper  | 5200, 6700  | 8500, 10000    | 975, 1275 | 1  |                                                                                          
