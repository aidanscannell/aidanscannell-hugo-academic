---
title: Hydra submitit launcher
date: 2019-05-05
type: book
summary: Hydra is extremely powerful for submitting HPC (SLURM) jobs
---

## TL;DR
- [Hydra](https://hydra.cc/)'s [Submitit Launcher plugin](https://hydra.cc/docs/plugins/submitit_launcher/) makes it easy to  submit SLURM jobs
- Easily sweep over multiple random seeds
- Easily sweep over different combinations of hyperparameters

## Hydra submitit launcher
[Hydra](https://hydra.cc/)'s [Submitit Launcher plugin](https://hydra.cc/docs/plugins/submitit_launcher/)
provides a [SLURM](https://slurm.schedmd.com/documentation.html) launcher based on 
[Submitit](https://github.com/facebookincubator/submitit).
It is extremely powerful as you can submit slurm jobs without writing sbatch scripts.

The main idea is to put the info we'd pass to `srun` (e.g. `--gpus-per-task=1`) inside a hydra config.
Then, instead of writing `sbatch` scripts with array jobs (e.g. submit 5 jobs with different seeds), 
we can easily submit many jobs from the command line.
Let me show with an example.

### Example
Consider a simple example with the following directory structure
```sh
awesome-ml-project/
└── train.py  # training script
├── cfgs/
│   └── train.yaml  # main config
│   └── hydra/
│       └── launchers/
│           └── MY_CLUSTER_2HRS.yaml
```
The main training script `train.py` looks something like
```python
import hydra

@hydra.main(version_base="1.3", config_path="./cfgs", config_name="train")
def train(cfg):
    print(cfg.batch_size)
    print(cfg.learning_rate)
    print(cfg.seed)

if __name__ == "__main__":
    train()
```
where the `learning_rate`, `batch_size` and `seed` are configured in the config file in `cfgs/train.yaml`
```yaml
defaults:
  - override hydra/launcher: MY_CLUSTER_2HRS
  - _self_

batch_size: 128
learning_rate: 1e-4
seed: 42
```
We now add a configuration file `cfgs/hydra/launcher/MY_CLUSTER_2HRS.yaml` 
to configure the parameters we'd usually set in the `sbatch` script.
Note that the file must be inside `cfgs/hydra/launcher/` as we're overriding hydra's default launcher.
Here's a simple example requesting 1 GPU for 2 hours.
```yaml
defaults:
  - submitit_slurm

_target_: hydra_plugins.hydra_submitit_launcher.submitit_launcher.SlurmLauncher
timeout_min: 120 # 2 hours
tasks_per_node: 1
nodes: 1
name: ${hydra.job.name}
comment: null
exclude: null
signal_delay_s: 600
max_num_timeout: 20
additional_parameters: {}
array_parallelism: 256
setup: []
constraint: "volta"
mem_gb: 50
gres: gpu:1
```

#### Submit a single SLURM job
We can now submit SLURM jobs straight from the command line with
``` shell
python train.py -m ++learning_rate=1e-3 ++batch_size=64
```
The `-m`/`--multirun` tells hydra to use multirun which will now submit a slurm job with the settings we specified in 
`cfgs/hydra/launcher/MY_CLUSTER_2HRS.yaml`.

#### Sweep over hyperparameters
We can easily perform sweeps over hyperparameters.
The following command will submit four jobs running `train.py` with each combination of `learning_rate` and `batch_size`
``` shell
python train.py -m ++learning_rate=1e-3,1e-4 ++batch_size=64,128
```
This massively speeds up hyperparameter search and makes configuring experiments a lot easier.

#### Sweep over multiple random seeds
We can also easily submit jobs with multiple random seeds.
For example,
``` shell
python train.py ++seed=42,100,696,23492,15
```
