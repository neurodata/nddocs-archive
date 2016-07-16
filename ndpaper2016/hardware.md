---
title: ND Paper 2016 - Hardware
layout: default
---


## Hardware

We have three data nodes, each with 64 cores, 64GB of memory and 20x2TB hard-drives; and a single web-server node with 24 cores, 48GB of memory and 10x2TB hard-drives. 

In addition to our data cluster, we maintain a small 3-node compute cluster for development and testing of workflows. The head node is a Dell R630 server with an Intel Xeon E5-2630 v3 CPU at 2.40GHz, 64GB of RAM and a 256GB SSD. The two worker nodes are both Dell R730 servers with dual Intel Xeon E5-2670 v3 CPUs running at 2.30 GHz, 256GB of RAM, and a 256GB root drive. A 2TB and a 40TB shared filesystem are both available on each server. 

We also maintain a visualization server, which hosts a development NeuroDataViz instance as well as the Window Explorer. The visualization server is a Dell R730 rack server with dual Intel Xeon E5-2660 CPUs running at 2.60GHz, 256GB of RAM, 256GB of SSD storage, and 20TB of data storage in various redundancy configurations. 

We maintain a Docker server which hosts a variety of web services inside containers, including Graph Explorer and Matrix Explorer. The Docker server is a Dell R630 with an Intel Xeon E5-2650 v3 CPU running at 2.30 GHz, 128GB of RAM, and a 512GB SSD volume. 

Finally, we maintain a data analysis server where we deploy FlashX for large-scale
data analytics. The server is a Dell R920 and has four Intel Xeon E7-4860 v2 CPUs running at 2.60GHz, 1TB of RAM and 24 SSDs with 400GB each.

Supplementary Table 1: Functions supported in our databases.  (A) NeuroImages. (B) NeuroAnnotations. (C) NeuroGraphs. (D) NeuroMatrices

Supplementary Figure 1: Infrastructure supporting all components of the OCP data analysis pipeline.  (A) The OCP Data Cluster. (B) Software running on the backend. (C) Software running on the frontend.




