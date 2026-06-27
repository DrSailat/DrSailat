---
layout: Article
title: "2026-06-07: Notes on IoT/Edge Deep Learning Frameworks/Tools- Introduction"
date(yy-mm-dd): 2026-06-07
---
<script>
  window.MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']]
    }
  };
</script>

<script async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>






# Notes on IoT/Edge Deep Learning Frameworks/Tools- Introduction!
By Dr. Saira Latif,
Published: 2026-06-07

---


Deep Learning pipeline as generally can be summarized as: 

**Dataset** → **Tensor** → **Neural Network** → **Prediction** → **Loss Function** → **Backpropagation** → **Optimizer** → **Update Weight**

 is implemented by DL frameworks 

Frameworks are a set of tools to implement models or architectures primarily in python. In deep learning applications these frameworks support curating datasets(handling), compute related operations, import and implement neural network models, functions for training, testing of these models for several applications conveniently without  need for grassroot coding. Some commonly used frameworks/libraries include 

                    - Pythorch
                    - Tensor Flow/Keras
                    - TensorFlow Lite/ONNX runtime

## Connection hierarchy  

                              PyTorch
                             
                              └── Complete framework
                          
                              TensorFlow
                          
                              └── Complete framework
                          
                                └── Keras (high-level interface)

TensorFlow and PyTorch can often be used as alternatives to each other, because both are full-featured deep learning frameworks capable of training and deploying neural networks but slightly different in programming style.PyTorch is generally considered more Pythonic and intuitive.TensorFlow offers a larger deployment ecosystem:

                      - TensorFlow Lite for mobile and edge devices
                      - TensorFlow Serving for production serving
                      - TensorFlow Extended (TFX) for MLOps pipelines

PyTorch  is currently the dominant framework in  AI research, robotics, autonomous systems, and modern LLMs. TensorFlow has a strong ecosystem for  industrial deployment and embedded AI production systems and edge devices.For beginners Keras: provides easy user end interface for  For beginners for easiest way to start building neural networks.

A practical rule is:
                      
                      - Use PyTorch → when to learn deep learning concepts and build models.
                      - Use TensorFlow/Keras → useful when deploying to mobile or embedded devices.
                      - TensorFlow Lite / ONNX Runtime → deploy trained models on edge devices such as Raspberry Pi, Jetson, and microcontroller-adjacent systems.

## TensorFlow vs Keras vs TensorFlow Lite

            TensorFlow ---> Keras builds models ----> TensorFlow trains models ---> TensorFlow Lite deploys models

---

# 1. PyTorch - Introduction

PyTorch is a deep learning framework based on tensors + automatic differentiation + GPU acceleration.
Official: PyTorch = 
<a href="https://docs.pytorch.org/docs/2.12/index.html" target="_blank" rel="noopener">
https://docs.pytorch.org/docs/2.12/index.html
</a>

 
## PyTorch Fundamentals: From Tensors to Optimization

Pytorch is a mathematical library for deep learning . In pytorch everything is built around: 

**Tensor → Computation Graph → Gradients → Optimization**

A neural network can be represented mathematically as:

                            y=f(x,W)

where:
                  
                        * (x) is the input data,
                        * (W) represents the model parameters (weights),
                        * (y) is the predicted output.

To measure prediction error, a loss function is defined. A common example is the Mean Squared Error (MSE):

  L=(\hat{y}-y)^2

PyTorch uses **automatic differentiation (Autograd)** to compute gradients of the loss with respect to model parameters:

   \frac{\partial L}{\partial W}

These gradients indicate how the parameters should be adjusted to minimize the loss.

PyTorch also provides a rich set of built-in optimization algorithms through the `torch.optim` module. These optimizers automatically update the model parameters during training based on the computed gradients.

Below is a short summary of the most commonly used optimizers.

## Common PyTorch Optimizers


<table border="1" cellspacing="0" cellpadding="8">
  <thead>
    <tr>
      <th>Optimizer</th>
      <th>Description</th>
      <th>Advantages</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>SGD</td>
      <td>Stochastic Gradient Descent updates parameters using the gradient of the loss.</td>
      <td>Simple and memory-efficient.</td>
    </tr>
    <tr>
      <td>Momentum SGD</td>
      <td>Extends SGD by accumulating previous gradients.</td>
      <td>Faster convergence and reduced oscillations.</td>
    </tr>
    <tr>
      <td>Adagrad</td>
      <td>Adapts the learning rate for each parameter individually.</td>
      <td>Useful for sparse data.</td>
    </tr>
    <tr>
      <td>RMSprop</td>
      <td>Uses a moving average of squared gradients.</td>
      <td>Handles non-stationary objectives well.</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Combines Momentum and RMSprop.</td>
      <td>Most widely used; generally works well out of the box.</td>
    </tr>
    <tr>
      <td>AdamW</td>
      <td>Adam with decoupled weight decay.</td>
      <td>Better regularization and generalization.</td>
    </tr>
    <tr>
      <td>LBFGS</td>
      <td>Second-order optimization method.</td>
      <td>Effective for some small-scale optimization problems.</td>
    </tr>
  </tbody>
</table>




PyTorch training follows the workflow:

```text
            Tensor → Computation Graph → Gradients → Optimization
```
            
            1. Create tensors.
            2. Build a neural network.
            3. Perform a forward pass.
            4. Compute the loss.
            5. Use Autograd to calculate gradients.
            6. Update parameters with an optimizer.
            7. Repeat until the model converges.

```
```

## Tensors (Fundamental Unit)

A tensor is a multi-dimensional array used to store data in PyTorch.

<table border="1" cellspacing="0" cellpadding="8">
  <thead>
    <tr>
      <th>Type</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Scalar</td>
      <td><code>5</code></td>
    </tr>
    <tr>
      <td>Vector</td>
      <td><code>[1, 2, 3]</code></td>
    </tr>
    <tr>
      <td>Matrix</td>
      <td><code>[[1, 2], [3, 4]]</code></td>
    </tr>
    <tr>
      <td>3D Tensor</td>
      <td>Image <code>(H × W × C)</code></td>
    </tr>
  </tbody>
</table>


### Creating Tensors

```python
import torch

x = torch.tensor([1.0, 2.0, 3.0])
print(x)
```


### Tensor with Gradient Tracking

```python
x = torch.tensor([2.0], requires_grad=True)
```

This enables **automatic differentiation (Autograd)**.


## Basic Tensor Operations

### Tensor Addition

Mathematically:

`c = a + b`

```python
a = torch.tensor([2.0])
b = torch.tensor([3.0])

c = a + b
print(c)
```

### Tensor Multiplication

Mathematically:

`C = AB`

```python
A = torch.randn(2, 3)
B = torch.randn(3, 4)

C = torch.matmul(A, B)
```


## Pytorch Autograd (Most Important Concept)

Autograd automatically computes gradients.

### Example

```python
x = torch.tensor(2.0, requires_grad=True)

y = x**2 + 3*x + 1

y.backward()

print(x.grad)
```

For Example :PyTorch computes following automatically.

`y = x² + 3x + 1`

Derivative:

`dy/dx = 2x + 3`

At `x = 2`:

`dy/dx = 7`

PyTorch computes this automatically.


## Pytorch Neural Network Module (`torch.nn`)

PyTorch provides neural network functionality through:

```python
import torch.nn as nn
```

### Pytorch Simple Neural Network Example

```python
model = nn.Sequential(
    nn.Linear(3, 8),
    nn.ReLU(),
    nn.Linear(8, 1)
)
```

### Pytorch Forward Pass

Mathematically:

`y = W₂(W₁x + b₁) + b₂`

```python
x = torch.randn(1, 3)

y_pred = model(x)
```


### Pytorch Loss Functions

Loss functions measure prediction error.

#### Mean Squared Error (MSE)

`L = (1/n) Σ (ŷ - y)²`

```python
criterion = nn.MSELoss()
```


### Pytorch Optimization

Optimizers update model weights based on gradients.

```python
import torch.optim as optim

optimizer = optim.Adam(
    model.parameters(),
    lr=0.001
)
```

Gradient-descent update rule:

`W ← W − η∇L`

### Common Pytorch Optimizers

<table border="1" cellspacing="0" cellpadding="8">
  <thead>
    <tr>
      <th>Optimizer</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>SGD</td>
      <td>Basic stochastic gradient descent</td>
    </tr>
    <tr>
      <td>Momentum SGD</td>
      <td>Uses previous gradients to accelerate learning</td>
    </tr>
    <tr>
      <td>Adagrad</td>
      <td>Adaptive learning rate for each parameter</td>
    </tr>
    <tr>
      <td>RMSprop</td>
      <td>Maintains moving average of squared gradients</td>
    </tr>
    <tr>
      <td>Adam</td>
      <td>Combines Momentum and RMSprop</td>
    </tr>
    <tr>
      <td>AdamW</td>
      <td>Adam with decoupled weight decay</td>
    </tr>
  </tbody>
</table>



### Pytorch Training Loop (Most Important)

```python
for epoch in range(100):

    # forward pass
    y_pred = model(X)

    # compute loss
    loss = criterion(y_pred, Y)

    # reset gradients
    optimizer.zero_grad()

    # backward pass
    loss.backward()

    # update weights
    optimizer.step()

    print(loss.item())
```

### Training Flow

```text
Data → Model → Loss → Backpropagation → Update Weights → Repeat
```


## PyTorch Backpropagation

PyTorch computes:

                  `∂L/∂W`

using the chain rule:

                      `∂L/∂W = (∂L/∂y) × (∂y/∂W)`

This allows gradients to flow backward through the network and update parameters efficiently.


### PyTorch GPU Acceleration

Move models and tensors to the GPU:

```python
device = torch.device("cuda")

model = model.to(device)
X = X.to(device)
Y = Y.to(device)
```

This significantly speeds up training for large models.


### PyTorch Dataset Handling

PyTorch provides:

* `torch.utils.data.Dataset`
* `torch.utils.data.DataLoader`

### Example

```python
from torch.utils.data import DataLoader, TensorDataset

dataset = TensorDataset(X, Y)

loader = DataLoader(
    dataset,
    batch_size=32,
    shuffle=True
)
```

The `DataLoader` automatically creates mini-batches and efficiently feeds data to the model during training.



## Summary

PyTorch training follows the workflow:

```text
Tensor → Computation Graph → Gradients → Optimization
```
          
          1. Create tensors.
          2. Build a neural network.
          3. Perform a forward pass.
          4. Compute the loss.
          5. Use Autograd to calculate gradients.
          6. Update parameters with an optimizer.
          7. Repeat until the model converges.

```
```
--- 

# 2. TensorFlow/Keras/TensorLite

    TensorFlow

      │
      ├── Keras (easy model-building API)
      │
      └── TensorFlow Lite (deployment on edge devices)

---

## 2.1  What is TensorFlow?

Official Link:
<a href="https://www.tensorflow.org" target="_blank" rel="noopener">
https://www.tensorflow.org
</a>

TensorFlow is a deep learning framework developed by Google AI.
Official site:TensorFlow

It helps you:

              - Build neural networks
              - Train models
              - Evaluate models
              - Deploy models
      
TensorFlow Workflow

  Data → Model → Training → Loss Calculation → Backpropagation → Weight Update → Trained Model

TensorFlow performs:

                    - Forward Pass: y= f(x)
                    - Compute Loss: Example MSE: L= 1n(y-y)2
                    - Backpropagation: Compute gradients: LW
                    - Update Weights: W=W−ηLW



## 2.3 What is Keras?

Official Link:
<a href="https://keras.io" target="_blank" rel="noopener">
https://keras.io
</a>


Keras is a high-level API that runs on top of TensorFlow.

Think of it like:

          - TensorFlow = Engine
          - Keras = Steering Wheel
          - TensorFlow does the heavy lifting.Keras makes it easy to use.

## With/Without Keras

You would manually build layers, losses, gradients, and optimizers and ended up in Lots of code. 
You can create a neural network in a few lines using keras:

```python
from tensorflow import keras

model = keras.Sequential([
    keras.layers.Dense(8, activation='relu'),
    keras.layers.Dense(1)
])
```

Complete Example:
Suppose: y=2x

Training data:

```python
import tensorflow as tf

X = [1,2,3,4]
Y = [2,4,6,8]
```
Build Model:
```python
model = tf.keras.Sequential([
tf.keras.layers.Dense(1)]) or tf.keras.layers.Dense(64)

A dense layer  tf.keras.layers.Dense(64)  performs:y= Wx+b
Means 64 neurons
```

Compile Model:

```python
model.compile(optimizer='adam', loss='mse')
```
Train Model:
```python
model.fit(X, Y, epochs=100)
```
Predict:
```python
model.predict([5])

```
---

# Edge AI Deployment: TensorFlow Lite, ONNX Runtime, Jetson, and Edge Impulse

## What is TensorFlow Lite?

Official Link:
<a href="https://developers.google.com/edge/litert" target="_blank" rel="noopener">
https://developers.google.com/edge/litert
</a>

TensorFlow Lite (TFLite), now part of Google's LiteRT ecosystem, is a framework for deploying machine learning and generative AI models on edge devices. It provides efficient model conversion, optimization, and runtime execution for resource-constrained hardware.

### Supported Platforms

TensorFlow Lite is designed for deployment on:
                
                      - Mobile devices (Android and iOS)
                      - Raspberry Pi
                      - Edge AI systems
                      - Embedded systems
                      - Microcontrollers (via TensorFlow Lite Micro)

### Why TensorFlow Lite?

Standard TensorFlow models can be large and computationally expensive.

For example:

<table border="1" cellspacing="0" cellpadding="8">
  <thead>
    <tr>
      <th>Model Type</th>
      <th>Size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>TensorFlow Model</td>
      <td>100 MB</td>
    </tr>
    <tr>
      <td>Optimized TFLite Model</td>
      <td>10 MB or smaller</td>
    </tr>
  </tbody>
</table>


Benefits include:

                      * Reduced model size
                      * Faster inference
                      * Lower memory consumption
                      * Lower power consumption


## Converting a TensorFlow Model to TFLite

### Example

```python
import tensorflow as tf

converter = tf.lite.TFLiteConverter.from_keras_model(model)

tflite_model = converter.convert()

# Save model
with open("model.tflite", "wb") as f:
    f.write(tflite_model)
```


## TensorFlow Lite on Raspberry Pi

A common deployment pipeline is:

```text
Sensor
   ↓
Raspberry Pi
   ↓
TFLite Model
   ↓
Prediction
```

Typical applications include:

    - Predictive maintenance
    - Anomaly detection
    - Smart agriculture
    - Industrial monitoring
    - Computer vision


## TensorFlow Lite Micro (TinyML)

Google link: 
<a href="https://developers.google.com/edge/litert/microcontrollers/overview" target="_blank" rel="noopener">
https://developers.google.com/edge/litert/microcontrollers/overview
</a>


TensorFlow Lite Micro enables machine learning inference directly on microcontrollers.

### Supported Hardware

      - ESP32
      - STM32
      - Arduino
      - ARM Cortex-M devices

### Workflow

```text
Train in TensorFlow
        ↓
Convert to TFLite
        ↓
Generate C/C++ Model
        ↓
Deploy on Microcontroller
```

This approach allows AI models to run with only a few kilobytes of memory.
---

## Example:  Industrial IoT and Predictive Maintenance Pipeline 

For predictive maintenance applications, a practical learning and deployment progression is:
  
  ```text
  TensorFlow + Keras
      ↓
  Autoencoders
      ↓
  LSTM Networks
      ↓
  CNN for Vibration Signals
      ↓
  TensorFlow Lite
      ↓
  Raspberry Pi / Edge Gateway
      ↓
  ESP32 + MQTT Data Acquisition
  ```

### Typical Architecture

```text
Sensors
   ↓
ESP32
   ↓
MQTT
   ↓
Raspberry Pi
   ↓
TensorFlow Lite Model
   ↓
Fault Prediction
```

---

# ONNX Runtime

ONNX Runtime is an open-source, cross-platform engine developed by Microsoft for executing machine learning models efficiently.

It supports models from:

    * PyTorch
    * TensorFlow
    * Scikit-learn
    * XGBoost
    * Other ONNX-compatible frameworks

### Key Benefits

A single model can run on:

                        - Windows
                        - Linux
                        - Raspberry Pi
                        - NVIDIA Jetson
                        - Cloud platforms

### Deployment Workflow

```text
PyTorch
    ↓
Export to ONNX
    ↓
ONNX Runtime
    ↓
Deployment
```

### Advantages

<table border="1" cellspacing="0" cellpadding="8">
  <thead>
    <tr>
      <th>Feature</th>
      <th>Benefit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Cross-platform</td>
      <td>Run anywhere</td>
    </tr>
    <tr>
      <td>Hardware acceleration</td>
      <td>CPU, GPU, NPU support</td>
    </tr>
    <tr>
      <td>Fast inference</td>
      <td>Production-ready</td>
    </tr>
    <tr>
      <td>Framework agnostic</td>
      <td>One runtime for many frameworks</td>
    </tr>
  </tbody>
</table>


---

# NVIDIA Jetson Ecosystem

For high-performance edge AI, NVIDIA Jetson devices are among the most powerful solutions available.

### Recommended Platform

* NVIDIA Jetson Orin Nano

### Supported Models

* CNNs
* LSTMs
* Vision Transformers (ViTs)
* YOLO Object Detection
* Large Language Models (LLMs)

### Typical Workflow

  ```text
  PyTorch
      ↓
  TensorRT Optimization
      ↓
  Jetson Deployment
      ↓
  Real-Time Inference
  ```

### Applications

    * Robotics
    * Autonomous systems
    * Smart cameras
    * Industrial inspection
    * Edge computer vision

---

# Edge Impulse

Official link: 
<a href="https://www.edgeimpulse.com" target="_blank" rel="noopener">
https://www.edgeimpulse.com
</a>

Edge Impulse is a beginner-friendly platform for building and deploying TinyML applications.


### Supported Hardware

* ESP32
* Arduino
* STM32
* Nordic nRF series

### Workflow
            
```text
Collect Sensor Data
          ↓
Train Model in Edge Impulse
          ↓
Generate Firmware
          ↓
Deploy to Device
```

### Advantages

<table border="1" cellspacing="0" cellpadding="8">
  <thead>
    <tr>
      <th>Feature</th>
      <th>Benefit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>No-code interface</td>
      <td>Easy to learn</td>
    </tr>
    <tr>
      <td>TinyML support</td>
      <td>Optimized for microcontrollers</td>
    </tr>
    <tr>
      <td>Data collection tools</td>
      <td>Integrated workflow</td>
    </tr>
    <tr>
      <td>Deployment tools</td>
      <td>One-click export</td>
    </tr>
  </tbody>
</table>



---

# Choosing the Right Platform

<table border="1" cellspacing="0" cellpadding="8">
  <thead>
    <tr>
      <th>Platform</th>
      <th>Best For</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>TensorFlow Lite</td>
      <td>Mobile and Raspberry Pi deployment</td>
    </tr>
    <tr>
      <td>TensorFlow Lite Micro</td>
      <td>TinyML and microcontrollers</td>
    </tr>
    <tr>
      <td>ONNX Runtime</td>
      <td>Cross-platform deployment</td>
    </tr>
    <tr>
      <td>NVIDIA Jetson</td>
      <td>High-performance edge AI</td>
    </tr>
    <tr>
      <td>Edge Impulse</td>
      <td>Rapid prototyping and education</td>
    </tr>
  </tbody>
</table>




# Conclusion

Modern Edge AI systems typically follow one of the following deployment paths:
  
  ```text
  TensorFlow
      ↓
  TensorFlow Lite
      ↓
  Raspberry Pi / Mobile Device
  ```

**OR**

  ```text
  PyTorch
      ↓
  ONNX
      ↓
  ONNX Runtime
      ↓
  Cross-Platform Deployment
  ```

**OR**

  ```text
  PyTorch
      ↓
  TensorRT
      ↓
  NVIDIA Jetson
      ↓
  High-Performance Edge AI
  ```

The choice depends on the available hardware, computational requirements, power constraints, and deployment environment.

Note: *The branding has shifted from "TensorFlow Lite" toward LiteRT, but many developers still use the term "TensorFlow Lite (TFLite)" because of its widespread adoption and existing tooling.*


---
---

# PRACTICE WHAT YOU LEARN

## Tools:

 Anaconda: https://www.anaconda.com/download

## Try CNN in Anaconda!

 Install Anaconda lite version - Create Environment with ML/DL libraries etc
You can create a fresh environment directly from Terminal(Mac/Win) or Anaconda Prompt 

- To run test CNN in notebook, First ,install tensorflow as it doesn't come preinstalled. You can use    the system terminal(Mac/Windows) to create an environment and install tensoreflow and tensorboard to    visualize CNN training , testing accuracy graphs etc. 

- You can also create an environment inside anaconda , using environment and the create environment      and to install tensorflow and tensorboard etc. Following is stepwise instruction to create a DL        environment in anaconda.




## Install TensorFlow in Anaconda + Jupyter Notebook

### Step 1 — Open Anaconda Navigator

Open: Anaconda

You will see:

    Environments -> Jupyter Notebook, Spyder, VSCode etc.

## Step 2 — Create New Environment (Recommended)

Go to:

- Environments → Create
- Name:
  
      cnn_env
- Choose:
  
      Python 3.10
  
Then click:

          Create

## Step 3 — Open Terminal in Environment
- Inside Anaconda, Click on:
  
        cnn_env → Open Terminal

## Step 4 — Install TensorFlow

Run:

    pip install tensorflow
    
Also install useful packages:

      pip install matplotlib numpy pandas jupyter

## Step 5 — Launch Jupyter Notebook

Still inside terminal, click on:

            jupyter notebook
            
  Browser opens automatically.

## Step 6 — Test TensorFlow
- Create notebook cell:
- import tensorflow as tf
- print(tf.__version__)
  
If installed correctly:

      2.x.x  Appears.


## Step 7 — Test CNN
After this you can run CNNcode in notebook




