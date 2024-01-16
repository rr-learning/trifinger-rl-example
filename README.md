TriFinger RL Example Package
============================

This is an example package that provides expert reinforcement learning policies that can be run on the [TriFinger robot cluster](https://webdav.tuebingen.mpg.de/trifinger/).
You can use it as base for your own package when submitting to the robot cluster. The [documentation](https://webdav.tuebingen.mpg.de/trifinger-rl/docs/) for the 
TriFinger RL Datasets provides more information on how to get an account for and submit to the robot cluster.

## Installation

To install the package run with python 3.8 in the root directory of the repository (we recommend doing this in a virtual environment):

```bash
pip install --upgrade pip  # make sure the most recent version of pip is installed
pip install .
```

Example Policies
----------------

The package contains two expert policies that were used to record the expert datasets for the Push and Lift tasks in the TriFinger RL datasets.

For the push task:

    $ python3 -m trifinger_rl_datasets.evaluate_sim push trifinger_rl_example.example.TorchPushPolicy --n-episodes=3 -v

For the lift task:

    $ python3 -m trifinger_rl_datasets.evaluate_sim lift trifinger_rl_example.example.TorchLiftPolicy --n-episodes=3 -v

The policy classes are implemented in `trifinger_rl_example/example.py`.  The corresponding torch
models are in `trifinger_rl_example/policies` and are installed as package_data so they can be loaded
at runtime (see `setup.cfg`).

All training checkpoints of the expert policies are available [here](https://edmond.mpdl.mpg.de/dataset.xhtml?persistentId=doi:10.17617/3.JA8ZW4). They can be
used with this repository by swapping them with the files in the `policies` subdirectory.

Documentation
-------------

For more information, please see the [software
documentation for the TriFinger RL datasets](https://webdav.tuebingen.mpg.de/trifinger-rl/docs/).

## How to cite

The expert policies were introduced in the paper ["Benchmarking Offline Reinforcement Learning on Real-Robot Hardware"](https://openreview.net/pdf?id=3k5CUGDLNdd):

```
@inproceedings{
guertler2023benchmarking,
title={Benchmarking Offline Reinforcement Learning on Real-Robot Hardware},
author={Nico G{\"u}rtler and Sebastian Blaes and Pavel Kolev and Felix Widmaier and Manuel Wuthrich and Stefan Bauer and Bernhard Sch{\"o}lkopf and Georg Martius},
booktitle={The Eleventh International Conference on Learning Representations },
year={2023},
url={https://openreview.net/forum?id=3k5CUGDLNdd}
}
```

The training pipeline for the expert policies was based on the code of the paper ["Transferring dexterous manipulation from GPU simulation to a remote real-world trifinger" by Allshire et al.](https://ieeexplore.ieee.org/abstract/document/9981458).
