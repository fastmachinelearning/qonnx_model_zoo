# Jet Tagging

The jet tagging dataset is an open dataset of simulated jets from collisions at the Large Hadron Collider. It's described in more detail in the [first hls4ml paper](https://iopscience.iop.org/article/10.1088/1748-0221/13/07/P07027), and available online at [Zenodo](https://zenodo.org/record/3602254#.YiePu_XMLUI), and [OpenML](https://www.openml.org/d/42468).

To access the dataset quickly:
```
from sklearn.datasets import fetch_openml
data = fetch_openml('hls4ml_lhc_jets_hlf')
```

## Models

The model `qkeras_jettagging.onnx` is trained in part 4 of the [hls4ml tutorial](https://github.com/fastmachinelearning/hls4ml-tutorial) - including some recommended dataset preprocessing.
It's an MLP with 3 hidden layers, with ReLU activations and a Softmax layer at the output.

The models here were trained originally using `QKeras`, then translated to `QONNX` using the in-development converter `qonnx.converters.from_keras`.
The original `QKeras` model is also available from the `hls4ml` [example models](https://github.com/fastmachinelearning/example-models/tree/0d4cc7277eac9bb9020e3d73a992dc15dbdcce4e/keras) (`qkeras_3layer` model).

| weight bits | bias bits | activation bits | accuracy |
| --- | --- | --- | --- |
| 6 | 6 | 6 | 76.2 % |