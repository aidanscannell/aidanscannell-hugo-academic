---
title: Conda environments
date: 2019-05-05
type: book
summary: Conda handles installing PyTorch with CUDA
---
## TL;DR
- [Conda](https://docs.conda.io/en/latest/) handles installing PyTorch with CUDA

## environment.yaml
This is a minimal conda environment config `environment.yaml` which will install PyTorch with CUDA 11.8
```yaml
name: ENV_NAME
channels:
  - nvidia
  - pytorch
  - conda-forge
dependencies:
  - pytorch=2.0
  - pytorch-cuda=11.8
  - torchvision=0.15
  - wandb=0.15
  - hydra-core=1.3
  - hydra-submitit-launcher=1.2
```
## Create environment
On a cluster we usually need to load a module for minoconda with
```sh
module load miniconda
```
It varies from cluster to cluster.
As conda is actually quite slow I prefer to use mamba.
We can create an environment from this environment config `environment.yaml` with
```sh
mamba env create -f environment.yaml
```
If we add to `environment.yaml` we can easily update it with
```sh
mamba env update -f environment.yaml
```
