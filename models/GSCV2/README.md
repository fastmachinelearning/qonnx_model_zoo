# Keyword Spotting

This repo contains a QONNX model which can classify spoken commands from the [Google Speech Commands dataset](https://arxiv.org/abs/1804.03209). 
The model is part of [finn-examples](https://github.com/Xilinx/finn-examples) and was contributed by Hendrik Borras. 

## Model

The model `kwsmlp_w3a3.onnx` is a 4-layer quantized MLP trained on the Google SpeechCommandsV2 dataset, you can find more information about the model in the [finn-examples kws notebook](https://github.com/Xilinx/finn-examples/blob/main/finn_examples/notebooks/4_keyword_spotting.ipynb). 


| Name        | Input quantization           | Weight quantization | Activation quantization | Dataset       | Top1 accuracy |
|-------------|------------------------------|---------------------|-------------------------|---------------|---------------|
| kwsmlp_w3a3 | 8 bit                        | 3 bit               | 3 bit                   |  GSCV2        |    87.89%     |
