---
title: Debugging on a cluster
date: 2019-05-05
type: book
summary: Tips for debugging Python ML code on a GPU cluster
---
## TL;DR
- Use the [python debugger](https://docs.python.org/3/library/pdb.html) inside interactive jobs (on GPU)
- Check you have GPU PyTorch/JAX/TensorFlow

## Debugging on a cluster
1. Start a short (5 minute) interactive job (on GPU)
    ```sh
    srun --mem=32gb --gres=gpu:1 -p gpu --time=0:05:00 --pty zsh
    ```
2. Run code on GPU with python debugger
    ```sh
    python -m pdb train.py
    ```
    - Press `c` to continue
    - Press `u` to go up. This is handy when you the code stops at an error and you want to move from low-level package code up to your code.
    - Press `d` to go down. 
3. Read error messages
4. Make fixes locally
5. Push to GitHub
    ```sh
    git push
    ```
6. Pull fixes onto cluster
    ```sh
    git pull
    ```
7. Run code again 
    ```sh
    python train.py
    ```

## Check you have GPU
Check you have installed PyTorch with GPU
```sh
import torch
torch.cuda.is_available()
```
## Monitor GPU use
On NVIDIA GPUs you can run the [NVIDIA System Management Interface](https://developer.nvidia.com/nvidia-system-management-interface)
to monitor your GPU usage. You can run it with
```sh
nvidia-smi
```
This is especially useful when combined with [tmux](https://github.com/tmux/tmux/wiki)
```sh
tmux
```
