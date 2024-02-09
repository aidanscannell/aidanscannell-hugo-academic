---
title: Running Jupyter Notebooks on GPU Clusters
date: 2019-05-05
type: book
summary: Run your notebooks fast using GPU.
---
## TL;DR
- Run your notebooks fast using GPU.

## Configure SSH
Run the notebook on the cluster and set the port using 
```sh
jupyter notebook --no-browser --port=8886
```
Now we can set up local SSH port forwarding to connect to the cluster
```sh
ssh -N -L localhost:8887:localhost:8886 USERNAME@HOSTNAME.NODE_ID
```
Now we can access the notebook at [localhost:8887](localhost:8887).
