---
title: Artificial intelligence - the very basics
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---

<!--more--> 

Let's assume we've built the perfect energy-efficient sensor, which runs reliably in its designated location and continuously provides us with high-quality images or audio data, each capturing our target perfectly. All this would be pointless if there wasn't a way to automatically classify these images and potentially even identify species, as manually reviewing the images would be extremely time-consuming and exhausting. We need **Artificial Intelligence (AI)**.

**AI** refers to the development of computer systems that can perform tasks that typically require human intelligence. These tasks include learning from experience, understanding natural language, recognizing patterns, and making decisions.

**Machine Learning (ML)** is a subset of AI focused on developing algorithms and models that enable computers to learn from data and make predictions or decisions. ML models identify patterns in data and improve their performance over time through training and are essential if we want automated image or sound identification.

This sounds complicated, but the basic principle remains the same as in classical data modeling: given a variable \( X \), we try to estimate a target variable \( Y \). In classical data modeling, we would assume that the relationship between \( Y \) and \( X \) can be approximated with a mathematical formula, such as a logarithmic regression. The coefficients and variance would be estimated from the data. Machine learning, on the other hand, does not assume a specific form. Instead, it aims to find a function that best describes the relationship between \( X \) and \( Y \) without any prior assumption.

# Machine Learning

In machine learning, there are three primary types of learning paradigms: **unsupervised learning**, **supervised learning**, and **reinforcement learning**.

- **Unsupervised Learning:** Uses data without explicit labels. This type of learning paradigm aims at finding similarities within the data, which can be used to understand the underlying structure and distribution of data.
- **Supervised Learning:** Involves training a model on a labeled dataset, meaning that each training example is paired with an output label. The main tasks of supervised learning are classification (categorizing inputs) and regression (predicting continuous outputs).
- **Reinforcement Learning (RL):** A type of machine learning where an agent (like a robot or a computer program) learns to make decisions by interacting with its environment. The agent tries different actions and learns from the results of those actions to get the best possible outcome. In contrast to supervised learning, which is about predicting the correct output based on provided examples, the goal of reinforcement learning is to learn a policy for making a sequence of decisions that maximizes cumulative rewards over time.

Because we're primarily interested in identifying critters, we'll focus on **Supervised Learning**.

---

> ### Think About It
> What obstacles can you think of when it comes to labeling data for supervised learning?

<details>
  <summary>Click here to see some common obstacles</summary>
  
  - **Time-Consuming:** Manually labeling large datasets can be very!! time-consuming.  
  - **Costly:** Hiring experts to label data, especially for specialized tasks, can be expensive - if they can be found at all.  
  - **Human Error:** Labels can be inconsistent due to human error or subjective judgment.  
  - **Ambiguity:** Some data points may be difficult to label clearly, leading to ambiguous or incorrect labels.  
  - **Imbalance:** In some cases, there might be an imbalance in the labeled data (e.g., more labels for common critters, nearly none for rare ones), which can affect model performance.

</details>



# Neural networks
One of the most well-known methods in machine learning to find this function is neural networks. Neural networks are computational models inspired by the human brain, consisting of interconnected nodes (neurons) organized into layers. Each neuron receives input signals, processes them by applying a weighted sum followed by an activation function, and passes the output to the next layer. The network typically includes an input layer, one or more hidden layers, and an output layer. Following our example, \( Y \)becomes the output layer, and \( X \) becomes the input layer.

![Hot Mess](https://imgs.xkcd.com/comics/machine_learning.png)
"Machine learning" by xkcd.com. This work is licensed under a Creative Commons Attribution-NonCommercial 2.5 License. 

## How do Neural Networks Work?
During training, the network adjusts the weights of the connections using algorithms like backpropagation, which minimizes the error between predicted and actual outputs by iteratively updating weights based on the gradient of the loss function. This process enables the neural network to learn complex patterns and make accurate predictions or decisions based on input data.

In the input layer, raw data (e.g., pixel values of an image) is fed into the network. This data passes through hidden layers, where it is processed and transformed by neurons. Finally, the transformed signal reaches the output layer, where the final prediction (e.g., the identity of a species) is produced.

This principle is wonderfully explained here:<br/>
[![](https://img.youtube.com/vi/aircAruvnKk/0.jpg)](https://youtu.be/aircAruvnKk?si=HOIBl_Ux_gAv--9E "Neural networks by 3Blue1Brown")


If there are many hidden layers, that is, if the hidden layers are "deep"  it is called deep learning. These deep neural networks can automatically learn hierarchical feature representations. Deep learning models can have hundreds or even thousands of layers, making them capable of learning extremely complex patterns and representations. 

A class of deep neural networks commonly used for analyzing visual data are so called Convolutional Neural Networks (CNNs). These have Convolutional Layers, which applies a set of filters (or kernels) to the input image, sliding them across the image to produce a feature map. Each filter detects a specific feature such as edges, textures, or patterns. They also have pooling layers, which reduce the spatial dimensions (height and width) of the feature maps, retaining the most important information while reducing the computational load and controlling overfitting. After several convolutional and pooling layers, the output is flattened and fed into dense layers. These layers are similar to those in traditional neural networks and consist of neurons connected to all activations in the previous layer.

<!--
https://saturncloud.io/blog/a-comprehensive-guide-to-convolutional-neural-networks-the-eli5-way/
http://neuralnetworksanddeeplearning.com/chap3.html
# TUNING with hyperparameters
backpropagation video
cito package parameters
# Bias- Variance- Trade-off
https://playground.tensorflow.org/#activation=tanh&batchSize=11&dataset=xor&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=5&networkShape=4,2&seed=0.96509&showTestData=false&discretize=false&percTrainData=20&x=true&y=true&xTimesY=true&xSquared=true&ySquared=true&cosX=false&sinX=true&cosY=false&sinY=true&collectStats=false&problem=classification&initZero=false&hideText=false
-->