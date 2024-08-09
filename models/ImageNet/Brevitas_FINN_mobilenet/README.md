# Brevitas QONNX Examples

This repo contains pretrained models in the Quantized ONNX format (QONNX), which were trained and exported using [Brevitas](https://github.com/Xilinx/brevitas).

These pretrained models and training scripts (located in the [Brevitas Repo](https://github.com/Xilinx/brevitas/tree/master/src/brevitas_examples/imagenet_classification) are courtesy of 
[Alessandro Pappalardo](https://github.com/volcacius).

## Models

The mobilenet model is based on the MobilnNets V1 architecture, published in the [MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications](https://arxiv.org/abs/1704.04861) paper.

NOTE: Accuracy numbers listed here are taken from the Brevitas repo, and are not verified running through QONNX at this time. 

| Name           | Input quantization | Weight quantization | Activation quantization | Dataset  | Top1 accuracy | Top5 accuracy |
|----------------|--------------------|---------------------|-------------------------|----------|---------------|---------------|
| mobilenet_4W4A | 8 bit              | 4 bit               | 4 bit                   | ImageNet | 71.14%        | 90.10%        |

## Train

The training scripts for these models are located in the [Brevitas Repo](https://github.com/Xilinx/brevitas).

## License

Models are licensed under LICENSE.txt within this directory.
