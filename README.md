# Octo Experiments

This is a repository for some experiments with the Octo model. 

## Setup

```bash
mamba create -n octo python=3.10
mamba activate octo
python -m pip install tensorflow[and-cuda]==2.14.0
python -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"

mamba install cudnn=8.8 cuda-version=11.8
pip install --upgrade "jax[cuda11_pip]==0.4.20" -f https://storage.googleapis.com/jax-releases/jax_cuda_releases.html
```

Some warnings and even errors from Tensorflow seem to be normal and acceptable, see also [this article](https://medium.com/@dev-charodeyka/tensorflow-conda-nvidia-gpu-on-ubuntu-22-04-3-lts-ad61c1d9ee32). In Octo, Tensorflow is mainly used for dataloading, not for the model themselves. 

Verify GPU support in JAX is working:
```python
from jax.lib import xla_bridge
print(xla_bridge.get_backend().platform)
```

Then, go on to install the other requirements:

```bash
cd octo
pip install -e .
pip install -r requirements.txt
```
