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


<table border="1" style="border-collapse: collapse; margin:auto;">
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
    <th>Form</th>
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

<br><br>

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

<br><br>

### 2.2.3  Hidden states

It is where final output is delivered by LSTM defined by equation:

$$
h_t = o_t \cdot \tanh(C_t)
$$


There are several variants of LSTMs with different architecture designs based on the same principles as discussed. One such commonly used variant is GRU base LSTM. For an intuitive and simple understanding of LSTM in detail, Colah's blog on "Understanding LSTM” is a good reference.

<br><br>
---

# 3.   CNN- Convolutional Neural Networks
Convolutional Neural Networks are specialized deep learning neural networks specially widely used for Images, spatial patterns, visual recognition, feature extraction and also being utilized extensively for sensor maps, vibration analysis, spectrogram etc.

## 3.1   CORE IDEA:
CCN works on images and identifies edges, shapes and spatial patterns. 


## 3.2  COMPONENTS:
 
    | Input Image→ Convolution  → Activation → Pooling →Feature Maps →  Fully Connected Layer → Output/Classification |

### 3.2.1 cINPUT IMAGES
Input images provided for CNN could be 64x64 grayscale or 64x54x3RGB
For training/testing/evulation purposes use mINSt dataset.

### 3.2.2  CONVOLUTION LAYER
A convolutional layer is like a small filter/kernel of suitable size that slides through the whole image and computer features like edges, textures or other patterns in each window slide and repeat. 
Example for filter  or kernel could be:

                             [1 0 -1;1 0  -1; 1  0  -1 ]
Mathematically :

$$
(I * K)(x, y) = \sum_{m} \sum_{n} I(x + m, y + n)\, K(m, n)
$$

Where:
- \(I(x,y)\) = input image
- \(K(m,n)\) = kernel / filter
- \(*\) = convolution operation


### 3.2.3  FEATURE MAPS
As a result of convolution, important feature like edge, circles, cracks, or other features of intent get highlighted.


### 3.2.4   ACTIVATION LAYER

CNN utilizes ReLU function defined as 
	
$$
f(x) = \max(0, x)
$$

to remove negative values , and introduces nonlinearity to help CNN learn. There are other activation functions that are being used as well.

| Concept | Python code:(add convolution filter, activation function , and input image to model)|
|--------|----------------|
| Conv2D Layer | `model.add(layers.Conv2D(32, (3,3), activation='relu', input_shape=(64,64,1)))` |

### 3.2.5 POOLING LAYER
This layer compresses information. One example could be MaxPooling which takes the largest value in the region. It could vary depending on application. The pooling layer reduces computation, removes noise and improves robustness.

| Concept | Python code:(add maxPooling to model)|
|--------|----------------|
|POOLING LAYER | `model.add(layers.MaxPooling2D((2,2)))` |


### 3.2.5  FULLY CONNECTED LAYER
This layer finally outputs binary classification from features whether the input image is cat or dog, faulty or healthy  and so on.

| Concept | Python code:(add maxPooling to model)|
|--------|----------------|
|                     |`model.add(layers.Dense(64, activation='relu'))` |
|FULLY CONNECTED LAYER| `model.add(layers.Dense(2, activation='softmax'))`|
|                      |`model.summary() `|


---
<br><br>

# 4. TRANSFORMERS

A Transformer is a deep learning architecture designed to handle long-range sequences (like text, time-series, sensor data) using a mechanism called attention.tOther DL frameworks such as CNN, LSTM , RNN  struggle with long-range dependencies. Since Transformers are attention-based model , key differentiating idea is look at the entire sequence at once and decide what is important.This is done using Attention; 

The attention mechanism is defined as:

$$
\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V
$$

Where:
- \(Q\) = Query matrix  
- \(K\) = Key matrix  
- \(V\) = Value matrix  
- \(d_k\) = dimension of key vectors


|Symbol|Meaning|
|------|------|
|Q (Query)|what I am looking for|
|K (Key)|what each input offers|
|V (Value)|actual information|


It is the foundation of modern AI models like ChatGPT.


## 4.1    Transformer Architecture- Building Blocks

    |Input Sequence  → Embedding →Positional encoding → Self/Multi-head -Attention Layer/s → Add & Normalize  → Feed Forward Network →       Add & Normalize → Output|

## 4.2   Embeddings

An embedding is a way of converting data (words, sensor states, products, images, etc.) into a vector of numbers that a neural network can understand.A learned numerical representation that captures meaning and relationships. 
“Embedding matrix exists inside model”

      |Text/Data → Tokenization(words→tokenids) → Vocabulary Look Ups → Assign Token Ids →find  Embeddings|


The embedding matrix is not probability-based.It is learned by optimization (gradient descent) on a loss function, not by sampling probabilities.Where do embedding values come from?They start as random numbers,then training updates them.
During training:

        - Model makes prediction
        - Loss is computed
        - Gradients flow back
        - Embedding rows get update
  
The model has an embedded table:

$$
E = \mathbb{R}^{V \times d}
$$

Where:
V = vocabulary size (e.g., 50,000)
d = embedding size (e.g., 768)

Neural networks cannot directly process words.Each word is assigned a token and is converted into a vector(embeddings). token s are assigned from vocabulary.
Vocabulary is the dictionary that converts words into numbers (IDs), so neural networks can process them. A vocabulary for NN uses is created by collecting large amount of data(e.g text ,etc), converts each element into token, then calculating frequency to identify most common tokens and assign IDs(numbers).Token ID is just a number assigned to each token in the vocabulary. In essence a vocabulary is fixed mapping from token to numbers It is created before training starts and usually does NOT change during training.A vocabulary is a fixed list of all tokens a model knows.


## 4.3   Positional Encoding

A Transformer does not naturally know order. We add position information to embeddings. It  tells it: “This token is first, this is second, this is third…”

    | embedding(token) + positional_encoding(position)|
    
There are two types of positional encoding

    - Learned Positional Encoding: Model learns a table just like embeddings
    - Sinusoidal positional encoding (as in original Transformer paper):Each position becomes a unique wave pattern.


## 4.4 Self-Attention

This is the heart of the transformer.
Every token asks: Which other tokens should I pay attention to? Which then transformed into Query (Q), Key (K), Value (V) using learned matrices.

|Symbol|Meaning|
|------|------|
|Q (Query)|what I am looking for|
|K (Key)|what each input offers|
|V (Value)|actual information|


Attention Score as calculated through following equations 

$$
\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V
$$

determines similarity between query and key. If there is a large value, then there is strong relevance. If small value then there is weak relevance. Transformer scales the score because large vector dimensions can produce huge numbers that destabilize.Softmax convert scores into probabilities.

## 4.5  Multi-Head Attention

Instead of one attention calculation:

Attention Head 1,
Attention Head 2,
Attention Head 3,
Attention Head 4...
Each head learns different relationships and the each output gets concatenated

### 4.5.2  Concatenation

In Concatenation, Outputs from all heads are joined i-2 “Combine different perspectives”.
Each attention head produces its own output:
Head 1 → h1, 
Head 2 → h2, 
Head 3 → h3, 
Head 4 → h4,....
Then,  we combine all heads into one big vector.

### 4.5.2  Residual Connection
“Don’t forget the original information”
Deep networks suffer from:

              - vanishing gradients
              - training instability
              - forgetting earlier information
  
We add input back to output , So the model learns only the “change”, not everything from scratch.

                |Input + Layer Output|

### 4.5.3 Layer Normalization

“Keep values stable and balanced”
Neural network activations can become:

                  - too large
                  - too small
                  - unstable during training
                  
This slows or breaks learning. Normalize activations:mean ≈ 0, variance ≈ 1

### Reference: 
Attention Is All You Need :
https://arxiv.org/abs/1706.03762?utm_source=chatgpt.com

 
