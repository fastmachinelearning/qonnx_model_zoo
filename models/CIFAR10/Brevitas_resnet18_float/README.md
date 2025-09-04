# Brevitas QONNX Examples – Extended

This repository extends the [Brevitas](https://github.com/Xilinx/brevitas/tree/master/src/brevitas_examples/bnn_pynq) examples with additional trained models in the Quantized ONNX (QONNX) format.  
These models are trained using [Brevitas](https://github.com/Xilinx/brevitas) and exported to QONNX for downstream deployment.  

The original trained models and training scripts for the BNN-PYNQ examples are courtesy of  
[Alessandro Pappalardo](https://github.com/volcacius) and [Ussama Zahid](https://github.com/ussamazahid96).  
This repository builds upon that work and introduces additional quantization configurations and some customizations to the training script.  

## Models  

This release includes **ResNet18** models with **8-bit** and **5-bit** weight and activation floating-point quantization, plus a **baseline FP32** model, all trained **from scratch** using newly introduced configurations that set **floating-point quantizers** to preserve accuracy.  

| Float quant. type    | Input quantization | Weight quantization | Activation quantization | Dataset  | Top-1 accuracy (test) | Top-5 accuracy (test) | Top-1 accuracy (QONNX) |
|----------------------|--------------------|---------------------|-------------------------|----------|-----------------------|-----------------------|------------------------|
| 8w8a_e4m3            | 8 bit              | 8 bit               | 8 bit                   | CIFAR10  | 93.09%                | 99.59%                | 93.09%                 |
| 5w5a_e3m1            | 5 bit              | 5 bit               | 5 bit                   | CIFAR10  | 90.69%                | 99.49%                | 90.69%                 |
| 32w32a_e8m23         | 32 bit             | 32 bit              | 32 bit                  | CIFAR10  | 92.82%                | 99.41%                | 92.82%                 |


## Training Setup

We trained a quantized ResNet-18 model on CIFAR-10 using the Brevitas framework for Quantization-Aware Training (QAT). All experiments used the same training script and hyperparameters: batch size 100, Adam optimizer (learning rate 0.02, momentum 0.9, no weight decay), Square Hinge loss, and 200 epochs training duration. Quantized models (weights and activations) were exported to QONNX format. The accuracy of the models showed on the test-set with Brevitas matches the one produced using QONNX, confirming that the quantization implementation is the same in both frameworks.

For 5w5a_e3m1 run, we used a smaller learning rate (0.001) and Cross Entropy loss, an extended training schedule of up to 10,000 epochs, early stopping (patience 100), and a step LR schedule. The training ended after 236 epochs showing accuracy performance very close to the baseline. The different hyperparameter configuration was needed for the low-precision configuration to converge. Since quantization reduces model size and compute requirements (smaller bitwidth means less memory and fewer cycles), our goal was to identify the lowest-precision floating-point formats that preserve accuracy.

## Notes  

- Baseline FP32 accuracy: **Prec@1 92.82**, **Prec@5 99.41**  
- Notation: `eXmY` denotes a floating-point format with X exponent bits and Y mantissa bits (e.g., `e4m3` → 8-bit, `e3m1` → 5-bit, `e8m23` → FP32).  
- Most models trained for **200 epochs** on CIFAR-10; `5w5a_e3m1` used an extended schedule with early stopping and converged after **236 epochs**.  

## Training and Evaluation

Training scripts for the extended models are based on the Brevitas examples and are located in the  
[extended Brevitas repo](https://github.com/nghielme/brevitas/tree/float_quant_exp/src/brevitas_examples/bnn_pynq).

After pip install Brevitas, you can reproduce the results by running the following scripts:

Training:

```
brevitas_bnn_pynq_train --gpus 0 --num_workers 8 --network RESNET18_5W5A_FLOAT_E3M1 --experiments outputs_RESNET18_5W5A_FLOAT_E3M1_5w5a_e3m1 --epochs 10000 --log_freq 20 --early_stopping --patience 100 --lr 0.001 --loss CrossEntropy --scheduler STEP --export_qonnx
```

Evaluation:

```
brevitas_bnn_pynq_train --gpus 0 --num_workers 8 --evaluate --network RESNET18_5W5A_FLOAT_E3M1 --resume outputs_RESNET18_5W5A_FLOAT_E3M1_5w5a_e3m1/RESNET18_5W5A_FLOAT_E3M1_5W5A_20250817_223330/checkpoints/best.tar
```