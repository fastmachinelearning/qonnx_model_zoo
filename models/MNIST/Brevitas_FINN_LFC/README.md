# Brevitas QONNX Examples

This repo contains pretrained models in the Quantized ONNX format (QONNX). Originally used in the [BNN-PYNQ](https://github.com/Xilinx/BNN-PYNQ) repo
using [Brevitas](https://github.com/Xilinx/brevitas).

These pretrained models and training scripts (located in the [Brevitas Repo](https://github.com/Xilinx/brevitas/tree/master/src/brevitas_examples/bnn_pynq) are courtesy of 
[Alessandro Pappalardo](https://github.com/volcacius) and [Ussama Zahid](https://github.com/ussamazahid96).

## Models

"LFC" models are "large" fully connected networks, similar to "TFC"/"SFC" models, with three hidden layers, each with 64 neurons. 
More details about these models can be found in the [FINN: A Framework for Fast, Scalable Binarized Neural Network Inference](https://arxiv.org/abs/1612.07119) paper. 

NOTE: Accuracy numbers listed here are taken from the Brevitas repo, and are not verified running through QONNX at this time. 

| Name     | Input quantization           | Weight quantization | Activation quantization | Dataset       | Top1 accuracy |
|----------|------------------------------|---------------------|-------------------------|---------------|---------------|
| LFC_1W1A | 1 bit                        | 1 bit               | 1 bit                   |  MNIST        |    98.88%     |
| LFC_1W2A | 2 bit                        | 1 bit               | 2 bit                   |  MNIST        |    98.99%     |

## Train

The training scripts for these models are located in the [Brevitas Repo](https://github.com/Xilinx/brevitas/tree/master/src/brevitas_examples/bnn_pynq).
