# Brevitas GTSRB example

This is the binarized CNV topology from the paper [FINN: A Framework for Fast, Scalable Binarized Neural Network Inference](https://arxiv.org/abs/1612.07119) which is trained
on the [German Traffic Sign Recognition Benchmark (GTSRB)](https://benchmark.ini.rub.de/gtsrb_news.html) dataset and exported in QONNX format.

## Models

NOTE: Accuracy numbers listed here are provided by the trainer, and are not verified running through QONNX at this time. 

| Name     | Input quantization           | Weight quantization | Activation quantization | Dataset       | Top1 accuracy |
|----------|------------------------------|---------------------|-------------------------|---------------|---------------|
| CNV_1W1A | 8 bit                        | 1 bit               | 1 bit                   |  GTSRB      |    96.93%     |


## Train

The training scripts for the CNV topology are located in [Brevitas Repo](https://github.com/Xilinx/brevitas/tree/master/src/brevitas_examples/bnn_pynq).
The original setup uses the CIFAR-10 dataset, which was subsequently modified by [Nicholas Fraser](https://github.com/nickfraser) for GTSRB for this example.

## License

Models are licensed under LICENSE.txt within this directory.