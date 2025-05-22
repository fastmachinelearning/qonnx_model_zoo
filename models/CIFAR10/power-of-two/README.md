# Model

A ResNet-8 model with power-of-two restricted scales achieving 91.83 % tested with qonnx-evaluation.  
Input and final layer quantization at 8 bits, activations per-tensor at 2 bits, weights per-tensor at 2 bits narrow range.  
Batchnormalizations are converted to a Mul and Add node with pow-of-two parameters(of 32 bit width).

# Train

Trained with Brevitas by [Charalampos Bezaitis](https://github.com/cbezaitis) 
