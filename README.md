# Hierarchical Deep Models

## Models
* RBM (Bernoulli, Multinomial, Gaussian)
* Easy to add new type of RBM (implement new type of stochastic units or create new RBM from existing types of units)
* DBM with arbitrary number of layers of any types

## Features
#### General
* Serialization (tf saver + python class hyperparams + RNG state)
* Reproducible (random seeds)
* All models support both `float32` and `float64` precision

### RBM and DBM features
* momentum
* L2 weight decay
* maxnorm weight decay
* ***TODO***: rest
* ***TODO***: sparsity targets
* ***TODO***: dropout

### Visualization
* Learning curves in TensorBoard (reconstruction RMSE, pseudo log-likelihood, free energy gap)
* Distribution of weights and weights updates in TensorBoard
* Routines to display images and learned filters

## How to install
By default, the following commands install (among others) **tensorflow-gpu~=1.3.0**. If you want to install tensorflow without GPU support, replace corresponding line in [requirements.txt](requirements.txt). If you have already tensorflow installed, comment that line but note that for [edward](http://edwardlib.org/) to work correctly, you must have tf>=1.2.0rc installed.
```bash
git clone https://github.com/monsta-hd/hd-models
cd hd-models/
pip install -r requirements.txt
```
See [here](docs/virtualenv.md) how to run in a ***virtual environment***.
</br>
See [here](docs/docker.md) how to run in a GPU-supported ***docker container***.

After installation, tests can be run with:
```bash
make test
```
All the necessary data can be downloaded with:
```bash
make data
```
## Common installation issues
**ImportError: libcudnn.so.6: cannot open shared object file: No such file or directory**.<br/>
TensorFlow 1.3.0 assumes cuDNN v6.0 by default. If you have different one installed, you can create symlink to `libcudnn.so.6` in `/usr/local/cuda/lib64` or `/usr/local/cuda-8.0/lib64`. More details [here](https://stackoverflow.com/questions/42013316/after-building-tensorflow-from-source-seeing-libcudart-so-and-libcudnn-errors).
