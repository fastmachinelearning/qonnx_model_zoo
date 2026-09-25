# CloudSatNet

CloudSatNet is a lightweight convolutional neural network for binary cloud
coverage classification of RGB Landsat-8 image tiles. Tiles are classified
as cloudy if the cloud coverage for the given input patch exceeds 70%.

The model was trained from scratch on the EXSI split of the Landsat-8 biome
dataset. EXSI excludes the Snow/Ice biome from the experiment. The ONNX graph
accepts an input tensor with shape `1x3x512x512` and produces two class logits
for cloudy and not cloudy.
The first and last layer weights use 8-bit quantization, while the internal layer
weights and activations use 4-bit quantization.

## Model

| Name | Input | Weight | Activation | Dataset | Test accuracy |
| --- | --- | --- | --- | --- | --- |
| `cloudsatnet_qat_4bit_exsi` | 4 bit | 8 bit first/last, 4 bit internal | 4 bit | Landsat-8 EXSI | 93.54% |

Model file: [`cloudsatnet_qat_4bit_exsi.onnx`](cloudsatnet_qat_4bit_exsi.onnx)

## Training and evaluation

The model was trained with quantization-aware training from scratch using a
batch size of 64 and learning rate `0.002`. The reported test result contains
8,649 samples:

| Loss | Accuracy | Precision | Recall | F1 | False-positive rate |
| ---: | ---: | ---: | ---: | ---: | ---: |
| 0.16013 | 93.54% | 93.99% | 90.66% | 92.29% | 4.32% |

These metrics are from the test run that produced the QONNX file. A separate
CPU/ONNX Runtime evaluation of the sibling `qcdq_clean` export on the 204-tile
`data/manifests/EXSI/test.json` smoke set achieved 99.02%; that result is not
reported as a direct evaluation of this QONNX graph.

## Credit

The architecture and original CloudSatNet-1 CNN are described in:

[1] Radoslav Pitonak, Jan Mucha, Lukas Dobis, Martin Javorka, and Marek Marusin,
"CloudSatNet-1: FPGA-Based Hardware-Accelerated Quantized CNN for Satellite
On-Board Cloud Coverage Classification," *Remote Sensing*, 14 (2022), 3180.
[DOI: 10.3390/rs14133180](https://doi.org/10.3390/rs14133180).

Dataset preparation as described in the paper and quantization-aware training were
performed by [Yaman Umuroglu](https://www.ntnu.edu/employees/yaman.umuroglu) at
NTNU.

The paper reports 94.84% accuracy and a 2.23% false-positive rate for its
4-bit EXSI result. The metrics above are the independently recorded result for
the model file contributed here.