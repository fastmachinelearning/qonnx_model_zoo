# CIFAR10 ResNet-18 models with Accumulator-Aware Quantization

QONNX models trained with accumulator-aware quantization (A2Q) as proposed "[A2Q: Accumulator-Aware Quantization with Guaranteed Overflow Avoidance](https://arxiv.org/abs/2308.13504)" and "[A2Q+: Improving Accumulator-Aware Weight Quantization](https://arxiv.org/abs/2401.10432)".

These pretrained models, originally located in the [Brevitas Repo](https://github.com/Xilinx/brevitas/master/src/brevitas_examples/imagenet_classification/a2q), are courtesy of 
[Ian Colbert](https://github.com/i-colbert).

## Models

All models are trained on the CIFAR10 dataset.
Input images are normalized to have unit mean and variance.
All residual connections are quantized to the specified activation bit width.


| Model Name | Weight Quantization | Activation Quantization | Target Accumulator | Top-1 Accuracy (%) |
|-----------------------------|----------------|---------------------|-------------------------|----------------------------|
| [quant_resnet18_w4a4_a2q_16b](https://github.com/fastmachinelearning/qonnx_model_zoo/releases/download/a2q-20240905/quant_resnet18_w4a4_a2q_16b-d4bfa990.onnx) | int4 | uint4 | int16 | 94.2 |
| [quant_resnet18_w4a4_a2q_15b](https://github.com/fastmachinelearning/qonnx_model_zoo/releases/download/a2q-20240905/quant_resnet18_w4a4_a2q_15b-eeca8ac2.onnx) | int4 | uint4 | int15 | 94.2 |
| [quant_resnet18_w4a4_a2q_14b](https://github.com/fastmachinelearning/qonnx_model_zoo/releases/tag/a2q-20240905#:~:text=quant_resnet18_w4a4_a2q_14b%2D563cf426.onnx) | int4 | uint4 | int14 | 92.6 |
| [quant_resnet18_w4a4_a2q_13b](https://github.com/fastmachinelearning/qonnx_model_zoo/releases/download/a2q-20240905/quant_resnet18_w4a4_a2q_13b-d3cae293.onnx) | int4 | uint4 | int13 | 89.8 |
| [quant_resnet18_w4a4_a2q_12b](https://github.com/fastmachinelearning/qonnx_model_zoo/releases/download/a2q-20240905/quant_resnet18_w4a4_a2q_12b-fb3a0f8a.onnx) | int4 | uint4 | int12 | 83.9 |
||
| [quant_resnet18_w4a4_a2q_plus_16b](https://github.com/fastmachinelearning/qonnx_model_zoo/releases/download/a2q-20240905/quant_resnet18_w4a4_a2q_plus_16b-09e47feb.onnx) | int4 | uint4 | int16 | 94.2 |
| [quant_resnet18_w4a4_a2q_plus_15b](https://github.com/fastmachinelearning/qonnx_model_zoo/releases/tag/a2q-20240905#:~:text=quant_resnet18_w4a4_a2q_plus_15b%2D10e7bc83.onnx) | int4 | uint4 | int15 | 94.1 |
| [quant_resnet18_w4a4_a2q_plus_14b](https://github.com/fastmachinelearning/qonnx_model_zoo/releases/download/a2q-20240905/quant_resnet18_w4a4_a2q_plus_14b-8db8c78c.onnx) | int4 | uint4 | int14 | 94.1 |
| [quant_resnet18_w4a4_a2q_plus_13b](https://github.com/fastmachinelearning/qonnx_model_zoo/releases/download/a2q-20240905/quant_resnet18_w4a4_a2q_plus_13b-f57b05ce.onnx) | int4 | uint4 | int13 | 92.8 |
| [quant_resnet18_w4a4_a2q_plus_12b](https://github.com/fastmachinelearning/qonnx_model_zoo/releases/download/a2q-20240905/quant_resnet18_w4a4_a2q_plus_12b-1e2aca29.onnx) | int4 | uint4 | int12 | 90.6 |