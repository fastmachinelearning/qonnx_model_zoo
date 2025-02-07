# Keyword Spotting

This repo contains a QONNX model which can classify network packets as malicious or not. The model is trained on the [UNSW-NB15 datset](https://research.unsw.edu.au/projects/unsw-nb15-dataset). 
The model is part of [finn-examples](https://github.com/Xilinx/finn-examples) and the [three-part FINN end2end tutorial](https://github.com/Xilinx/finn/tree/main/notebooks/end2end_example/cybersecurity). 

## Model

The model `unsw_nb15_mlp_w2a2.onnx` is a quantized MLP with three hidden layers with 64 neurons, and a final output layer with a single output, all using 2-bit weights.
2-bit quantized ReLU activation functions are used, and batch normalization is inserted between each fully-connected layer and its activation. 
The input is quantized to 1 bit following the procedure described by [Murovic and Trost](https://ev.fe.uni-lj.si/1-2-2019/Murovic.pdf).


| Name                | Input quantization   | Weight quantization | Activation quantization | Dataset       | Accuracy |
|---------------------|----------------------|---------------------|-------------------------|---------------|----------|
| unsw_nb15_mlp_w2a2  | 1 bit                | 2 bit               | 2 bit                   |  UNSW-NB15    |  91.90%  |
