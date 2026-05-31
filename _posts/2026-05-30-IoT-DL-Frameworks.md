---
layout: Article
title: "Notes on IoT/Edge Deep Learning Framework- Introduction"
date: 2026-05-30
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






# Notes on IoT/Edge Deep Learning Framework- Introduction!
By Dr. Saira Latif,
Published: 2026-05-30
  <div style="text-align:center; margin-bottom:50px;">
  <img src="{{ site.baseurl }}/assets/images/IoT_Edge_DLFrameworks.jpeg" width="40%">
  
  <div style="margin-top:10px; font-size:0.9em;">
     IoT/Edge DL Frameworks Overview
  </div>
</div>

<p>

</p>


It is simply fascinating how integrating technology in day to day processes is crucial for our collective future and sustainability of infrastructures. Deep learning methods as a general concept are considered computation intensive or somewhat scary when it comes to low level applications but not an impossibility. `Recently I have been exploring from the plethora of ML & DL techniques and new research to extract a few commonly used techniques that are being deployed and utilized for various maintenance and monitoring applications. So if you are interested to be aware of some core DL methodologies for IoT or edge computing devices for various applications such as AI based monitering and predictive maintaince. Each ML framework is specialized application categories as tabulated in the table below: You ll find this introduction useful for holistic view; 

<!--

  | Model  | Best For    |    
  |-------|--------------|
  | Autoencoder | Anomaly detection | 
  | LSTM  | Sequential/time-series prediction | 
  | CNN   | Signal/Image feature extraction  | 
  | Transformers |Long-range temporal relationships|

-->

<div style="text-align: center;">

<table border="1" style="margin-left:auto; margin-right:auto;">
    <tr>
      <th>Model</th>
      <th>Best Use Cases</th>
    </tr>
    <tr>
      <td>Autoencoder</td>
      <td>Anomaly Detection</td>
    </tr>
    <tr>
      <td>LSTM</td>
      <td>Sequential/time-series prediction</td>
    </tr>
    <tr>
      <td>CNN</td>
      <td>Signal/Image feature extraction </td>
    </tr>
    <tr>
      <td>Transformers</td>
      <td>Long-range temporal relationships</td>
    </tr>
</table>

</div>        

The choice of model depends on:

      - Sensor type,
      - Compute power,
      - Latency requirements,
      - and whether inference runs on:
                                    - Microcontrollers,
                                    - Edge gateways,
                                    - or Cloud Servers.

 <div style="text-align:center; margin-bottom:50px;">
  <img src="{{ site.baseurl }}/assets/images/IoT_Arciteture.jpg" width="40%">
  
  <div style="margin-top:10px; font-size:0.9em;">
     Architecture for DL based IoT/Edge Use Cases
  </div>
</div>

<p>

</p>

___
<br><br>
# 1.   AUTOENCODES

An Autoencoder is an unsupervised learning model most frequently used as an anomaly detector. 

For decades and so, Autoencoders have been a buzz word in AI and Robotics. All of Us who have been in conferences and seminars and other interactions with domain experts, Autoencoders are one of those few words that come up in discussion over and over again and a fantastic concept and technique mainly used for anomaly detection,compression, unsupervised learning.
Unlike supervised learning, autoencoders do not require labeling or classification. The model learns underlying patterns, structure and correlation. It  extracts main features as a first step known as compression and generates latent representation/vector and then reconstructs it back as close to original data(decoder) . 

  |  Input → Encoder → Latent Space → Decoder → Reconstructed Output |
 

## 1.1 Core Idea
“Anything reconstructed poorly is likely an anomaly! “

The autoencoder is trained to learn normal system behavior by reconstructing input data. During inference, new data is passed through the model, and it produces a reconstructed output.
The difference between input and output is measured using reconstruction error:
$$
L = \| x - \hat{x} \|^2
$$
If “L” : the reconstruction error is  higher than statistically defined threshold , it indicates that the input deviates from learned normal patterns, suggesting a possible anomaly or machine fault. Otherwise, the system is considered operating normally.
Most common Industrial use cases are:
- Bearing Fault Detection i-e normal vibration vs abnormal vibrations
- Thermal Anomaly Detection - Machine Fault


---
<br><br>
# 2. LSTM (Long Short-Term Memory)

LSTM as we know is best known as an ML technique applied for time series data or sequential data to examine trends and has been widely used across racing applications to forecasting. Unlike traditional Neural Networks which typically don't remember previous inputs, LSTM have memory and don't forget previous inputs. Therefore contains "memory cells“, “gates”  and “hidden states”  which enable it possible to predict or estimate  compound behaviour over time.

## 2.1  Core idea

LSTM works on time-dependent sequences and  identifies temporal patterns. It uses primarily : Memory cells,  gates, and hidden states. There are three types of gates utilized namely Forget gate, Input Gate, and output gate.

## 2.2 LSTM Components:

<table border="1" style="border-collapse: collapse; margin:auto;">
  <tr>
    <th>Concept</th>
    <th>Correct form</th>
  </tr>
  <tr>
    <td>Candidate memory</td>
    <td>$\tilde{C}_t$</td>
  </tr>
  <tr>
    <td>Forget gate</td>
    <td>$f_t$</td>
  </tr>
  <tr>
    <td>Input gate</td>
    <td>$i_t$</td>
  </tr>
  <tr>
    <td>Memory update</td>
    <td>$C_t = f_t C_{t-1} + i_t \tilde{C}_t$</td>
  </tr>
</table>

 <div style="text-align:center; margin-bottom:50px;">
  <img src="{{ site.baseurl }}/assets/images/LASTM.jpg" width="40%">
  
  <div style="margin-top:10px; font-size:0.9em;">
     Architecture for DL based IoT/Edge Use Cases
  </div>
</div>

<p>

</p>


### 2.2.1 LSTM's Gates

LSTM controls information flow using gates namely Forget Gate, Input gate and Output gates. Each gate is a small neural network with a Sigmoid activation function. Sigmoid Activation Function output: 
$$
\sigma(x) = \frac{1}{1 + e^{-x}} 
$$


This function outputs values between 0 and 1 i-e 0 0< σ(x) < 1. It blocks information if close to 0 and allows information if close to 1 and partially passes information if in between.


#### 2.2.1.1  Forget Gate
It is to decide which old memory should be removed and is defined by sigmoid function equation:

$$
f_t = \sigma\left(W_f [h_{t-1}, x_t] + b_f\right)
$$

where :

            - $x_t$ = current input  
            - $h_{t-1}$ = previous hidden state  
            - $W_f$ = weights  
            - $b_f$ = bias  

If “ $f_t$ “ close to 0 forget and if “ $f_t$  " close to 1 , keep it.

#### 2.2.1.2    Input Gate
It is to decide what new information to be stored and also defined by sigmoid function equation:

$$
i_t = \sigma\left(W_i [h_{t-1}, x_t] + b_i\right)
$$

where :
            
            - $i_t$ = input gate activation  
            - $x_t$ = current input  
            - $h_{t-1}$ = previous hidden state  
            - $W_i$ = input gate weight matrix  
            - $b_i$ = bias term

#### 2.2.1.3  Output Gate
It decides on output and also defined by sigmoid function equation:

$$
o_t = \sigma\left(W_o [h_{t-1}, x_t] + b_o\right)
$$

where:

            - $o_t$ = output gate activation  
            - $x_t$ = current input  
            - $h_{t-1}$ = previous hidden state  
            - $W_o$ = output gate weights  
            - $b_o$ = bias term



### 2.2.2  Memory Cells


#### 2.2.2.1    Candidate Memory
The candidate memory represents potential new information:

$$
\tilde{C}_t = \tanh\left(W_c [h_{t-1}, x_t] + b_c\right)
$$

#### 2.2.2.2  Updated Memory State
This is the core of LSTM and combines old memory with new information:

$$
C_t = f_t \cdot C_{t-1} + i_t \cdot \tilde{C}_t
$$

Input gate multiplies candidate memory, not old memory.


### 2.2.3  Hidden states

It is where final output is delivered by LSTM defined by equation:

$$
h_t = o_t \cdot \tanh(C_t)
$$

There are several variants of LSTMs with different architecture designs based on the same principles as discussed. One such commonly used variant is GRU base LSTM. For an intuitive and simple understanding of LSTM in detail, Colah's blog on "Understanding LSTM” is a good reference.
