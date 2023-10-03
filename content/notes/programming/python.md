---
title: Python
date: 2019-05-05
type: book
---
# TL;DR
- Use python packages in editable mode with `setup.py` and `pip install -e .`
- Reusable (general) code goes inside the main package
- Use `./examples` to show how to use your code
- Use `./experiments` for advanced experiment configuration/tracking etc 
    - e.g. with [hydra](https://hydra.cc/) and [Weights & Biases](https://wandb.ai/site)
    - makes your package agnostic to configuration/tracking tools
- Use [direnv](https://direnv.net/) to manage python virtual environments
    - automatically activates/deactivates envs depending on current directory

## Python versions (pyenv)
I use [pyenv](https://github.com/pyenv/pyenv) for managing python versions.
- Install using Homebrew
    ``` shell
    brew install pyenv
    ```
- [Follow these instructions](https://github.com/pyenv/pyenv) to set up pyenv and install different python versions

I then set my global python version to be 3.9.13.

## Virtual environments (direnv)
I use [direnv](https://direnv.net/) to automatically activate/deactivate python virtual environments when I enter/leave a 
project's directory.
- On Mac OSX [direnv](https://direnv.net/) can be installed using Homebrew
    ``` shell
    brew install direnv
    ```
- Create the `.envrc` file in the root of the project's directory and enter "layout python" with
    ``` shell
    cd /path/to/python/project
    echo "layout python" >> .envrc
    ```
- Give direnv access to the directory with
    ``` shell
    direnv allow
    ```
    This enables direnv to activate/deactivate the projects virtual environment when entering/leaving the directory.
    
I specify each project's dependencies using `setup.py` or `pyproject.toml`.
More details on this later.

## Directory structure
I tend to put my machine learning projects into python packages with the following directory structure
```sh
package-name/
└── LICENCE
└── README  # detail how to install package and refer to examples/experiments
└── requirements.txt  # pin dependencies for reproducibility
└── setup.py  # package 
├── examples/
│   └── train_my_alg_on_example.ipynb  # detail how to use package via some example
├── experiments/
│   └── README  # detail how to run experiments / reproduce results
│   └── configs/  # directory containing yaml config files for hydra
│   └── train.py  # script for running experiments (with logging/monitoring/checkpointing etc)
├── package-name/  # reusable code in the main package
│   └── model.py
│   └── algorithm.py
├── tests/  # because I always write tests 🫣
```
The general idea is to keep the reusable code (models, algorithms) inside the main package 
(`package-name/package-name`) and to put problem specific training/plotting scripts in separate directories.
I like to use an `./examples` directory to show how the pacakge can be used; often in the form of a notebook.
I then like to have an `./experiments` directory which contains training/plotting scripts for generating results for a paper.
I use [hydra](https://hydra.cc/) to configure all of my experiments and [Weights & Biases](https://wandb.ai/site) to track them.
[hydra](https://hydra.cc/) and [Weights & Biases](https://wandb.ai/site) are powerful tools for configuring/tracking experiments
but as not everybody uses them, it can make the `./experiments` directory  they can m



## Dependencies

### setup.py
```python
import pathlib
import setuptools

_here = pathlib.Path(__file__).resolve().parent

name = "INSERT PACKAGENAME"
author = "Aidan Scannell"
author_email = "scannell.aidan@gmail.com"
description = "INSERT DESCRIPTION"

with open(_here / "README.md", "r") as f:
    readme = f.read()

url = "https://github.com/aidanscannell/" + name

license = "Apache-2.0"

classifiers = [
    "Development Status :: 3 - Alpha",
    "Intended Audience :: Science/Research",
    "Intended Audience :: Developers",
    "Intended Audience :: Information Technology",
    "License :: OSI Approved :: Apache Software License",
    "Natural Language :: English",
    "Programming Language :: Python :: 3",
    "Topic :: Scientific/Engineering :: Artificial Intelligence",
    "Topic :: Scientific/Engineering :: Mathematics",
]
keywords = ["keyword-one", "keyworkd-two"]

python_requires = "~=3.7"

install_requires = ["jax==0.3.14", "jaxlib==0.3.10", "numpy"]
extras_require = {
    "dev": ["black", "pyright", "isort", "pyflakes", "pytest"],
    "examples": ["hydra-core", "wandb", "matplotlib", "seaborn", "bsuite"],
}

setuptools.setup(
    name=name,
    version="0.1.0",
    author=author,
    author_email=author_email,
    maintainer=author,
    maintainer_email=author_email,
    description=description,
    keywords=keywords,
    long_description=readme,
    long_description_content_type="text/markdown",
    url=url,
    license=license,
    classifiers=classifiers,
    zip_safe=False,
    python_requires=python_requires,
    install_requires=install_requires,
    extras_require=extras_require,
    packages=setuptools.find_namespace_packages(),
)
```

The pacakge can be installed in editable mode using
```sh
pip install -e .
```
If we also wish to install the "dev" and "examples" dependencies we can use
```sh
pip install -e ".[examples,dev]"
```

### Developer packages
These packages will make any python developer's life easier:
- [black](https://github.com/psf/black) code formatter
- [pyright](https://github.com/microsoft/pyright) type checker
- [isort](https://pycqa.github.io/isort/) import sorter
- [pyflakes](https://github.com/PyCQA/pyflakes) checks python files for errors
- [pytest](https://docs.pytest.org/en/7.2.x/) framwork for making tests

[pre-commit](https://pre-commit.com/) is another super handy tool for executing pre-commit hooks, e.g. formatting code, sorting imports, formatting notebooks, etc.
My `.pre-commit-config.yaml` setup usually looks something like this
```yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.3.0
    hooks:
      - id: check-yaml
      - id: requirements-txt-fixer
      - id: trailing-whitespace
  - repo: https://github.com/psf/black
    rev: 22.10.0
    hooks:
      - id: black
  - repo: https://github.com/nbQA-dev/nbQA
    rev: 1.5.2
    hooks:
      - id: nbqa-black
      - id: nbqa-isort
      # - id: nbqa-flake8
  - repo: https://github.com/PyCQA/isort
    rev: 5.10.1
    hooks:
      - id: isort
  - repo: https://github.com/pycqa/flake8
    rev: 4.0.1
    hooks:
      - id: flake8
```

### Pinning dependencies
For reproducibility I usually freeze and commit dependencies in a `requirements.txt` file before running experiments
```sh
pip freeze > requirements.txt
```
