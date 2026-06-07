---
layout: Article
title: "Notes on IoT/Edge Deep Learning Frameworks/Tools- Introduction"
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

    Dataset → Tensor → Neural Network → Prediction → Loss Function → Backpropagation → Optimizer → Update Weight 

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

