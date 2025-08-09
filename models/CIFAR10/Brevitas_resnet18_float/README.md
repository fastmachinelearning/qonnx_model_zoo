# Brevitas QONNX Examples – Extended

This repository extends the [Brevitas](https://github.com/Xilinx/brevitas/tree/master/src/brevitas_examples/bnn_pynq) examples with additional trained models in the Quantized ONNX (QONNX) format.  
These models are trained using [Brevitas](https://github.com/Xilinx/brevitas) and exported to QONNX for downstream deployment.  

The original trained models and training scripts for the BNN-PYNQ examples are courtesy of  
[Alessandro Pappalardo](https://github.com/volcacius) and [Ussama Zahid](https://github.com/ussamazahid96).  
This repository builds upon that work and introduces additional quantization configurations and some customizations to the training script.  

## Models  

This release includes a ResNet18 architecture with **8-bit weight and activation quantization**, trained **from scratch** using newly introduced configurations that set **floating-point quantizers** to preserve accuracy.  

| Name                 | Input quantization | Weight quantization | Activation quantization | Dataset  | Top-1 accuracy (test) | Top-5 accuracy (test) | Top-1 accuracy (QONNX) |
|----------------------|--------------------|---------------------|-------------------------|----------|-----------------------|-----------------------|------------------------|
| resnet18_8w8a_float  | 8 bit              | 8 bit               | 8 bit                   | CIFAR10  | 93.09%                | 99.59%                | 93.09%                 |

## Notes  

- Baseline FP32 accuracy: **Prec@1 92.82**, **Prec@5 99.41**  
- Model trained for **200 epochs** on CIFAR-10  

## Train  

Training scripts for the extended models are based on the Brevitas examples and are located in the  
[extended Brevitas repo](https://github.com/nghielme/brevitas/tree/float_quant_exp/src/brevitas_examples/bnn_pynq).  

## License  

Models are licensed under `LICENSE.txt` within this directory.  
