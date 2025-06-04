---
title: Building models
published: true
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
  

---

Now that you had a glimpse on how CNNs work...
…it’s time to dive into how you can create your own model or adapt an existing one to your task. We'll assume you've already collected a decent amount of image data.

## How to train your ~~dragon~~ model

### 1. Definition of classes

The first major step is thinking about what you want your model to actually detect and/or classify — and yes, this is where things can already get tricky.
Some models can do both steps — detect where something is and classify what it is — all in one go (e.g. YOLO).
However, if your goal is to save storage space by cropping out insects from full-frame images, a misdetection might mean you lose important data entirely.

Alternatively, you could do a two-step approach:

Step 1: Use a 1 class detection model to locate insects in an image (e.g., draw bounding boxes around them).

Step 2: Use a classification model to analyze the cropped region and decide what kind of insect it is — either on-device (edge processing) or later on your PC after collecting the data.

In any way, you'll need to define clear classes for your classification model.

#### What are classes?
A class is a category your model learns to recognize. In your case, this could be:

* Different insect species (e.g., *Apis mellifera*, *Vespula germanica*)
* Morphotypes
* Broader taxonomical groups (e.g., beetles, flies, bees)
* Behavioral states (e.g., flying, feeding, mating) — if you go fancy

The key is to make the classes meaningful, distinguishable, and consistently labeled. Also, keep in mind that the more classes you have, the more examples of each you'll need to train a good model.

> Let's collect potential pitfalls


### 2. Annotation

Once you’ve pinned down your classes, it’s time to annotate your data — that means telling the model what it's looking at.

But before jumping into annotation, take a step back. If you have more than one class, chances are they won’t be equally represented. You’ll likely end up with lots of examples of one kind of insect (e.g., honeybees) and very few of another (e.g., beetles). This is called an imbalanced dataset.

If you train a model on this as-is, you’ll get a classifier that’s great at identifying the common class and terrible at everything else.

Before you start labeling your full dataset, screen your images. You might only need to annotate a smaller, balanced subset to get started. This subset should have:

* A reasonable number of examples per class (as equal as possible)

* A good variety of lighting, positions, angles, and insect counts

>Let's have a look at last years data!


Two more strategies might help if balancing is not enough:

1. **Data augmentation** 
This means synthetically modifying your images to create more variety — especially for underrepresented classes. 

2. **Class weighting**
When training your model, you can tell the loss function to give more importance to rare classes. This encourages the model not to just "default" to the common class.

### Annotation types
There are different options on how to annotate your object of interest

|   Annotation Type   |  	Description	                        |   Pros    |	Cons |
| --------------------|---------------------------------------|-----------|------|
| Bounding Boxes	    |Draw a rectangle around each object	  | Simple; good for object detection	|Can include b ackground noise    |
| Polygons	|Outline the shape of the object	| More precise, supports segmentation	| More time-consuming | 
| Image Labels	| Label the whole image (e.g., "contains bee")|	Fast to annotate; used in classification	| Not usable for detection|


### Annotation tools

By now, there are many annotation tools available. These tools provide the user interface to quickly annotate images and marking regions of interest with your chosen classes. The output is usually a set of structured files that contain the coordinates of the annotated areas along with their class names. These files are used during training so the model can learn what to detect or classify. Many have options to export the data in various machine learning formats:

This is how such a format might look like:
```
[
  {
    "bbox": [100, 150, 60, 80],
    "class": "bee",
    "confidence": 0.87
  },
  {
    "bbox": [300, 120, 45, 45],
    "class": "ant",
    "confidence": 0.72
  }
]
```

See [the page by Maximilian Sittinger](https://maxsitt.github.io/insect-detect-docs/modeltraining/annotation/) for some suggestions on useful annotation tools.

## 2. Splitting the data

The next step is to split your data into training, validation and test data. 
If you train and test your model on the same data, you’ll never know if it has really learned to generalize — or if it’s just memorizing the answers. A good model needs to perform well not just on familiar data, but also on new, unseen examples.

**Training data (generally ~70%)** is used to teach the model — it sees this data repeatedly and adjusts its internal parameters based on it.
**Validation data (~20%)** is used during training to check how the model is doing on unseen data. This helps you fine-tune things like the learning rate, architecture, or when to stop training to avoid overfitting. Be careful:  if you are changing your model based on the validation results each time — your decisions are no longer independent of that data. You're gradually tailoring the model to do well on the validation set itself. 
**Test data (~10%)**  is kept completely separate and is used only at the very end to evaluate the final performance of your model. It gives you an honest picture of how your model will do “in the wild.”

## 3: Construct and train your CNN

Now that your data is annotated and structured, the next step is to design and train a Convolutional Neural Network (CNN).

### Reminder - Key Components of a CNN
**Convolutional layers** are the core of a CNN. They apply a series of small filters (also called kernels) across the image. These filters are designed to detect local patterns — such as edges, shapes, or textures — without the model having to "see" the whole image at once. The network learns the best filters during training.
**Pooling layers** usually follow convolutional layers. Their role is to reduce the spatial size of the feature maps, which makes the network more efficient and robust to small translations or distortions.
**Fully connected (dense) layers** appear at the end of the network. These layers interpret the features detected in earlier layers and make the final classification decision.
**Dropout layers and batch normalization** are often added to improve performance and generalization. Dropout randomly deactivates some neurons during training, which helps prevent overfitting. Batch normalization normalizes the output of a layer so that the network trains faster and is more stable.

### Settings
When the model has seen the entire training dataset once, it has run for one **epoch**. In most training setups, you’ll run for multiple epochs to allow the model to gradually improve. However, too many epochs can lead to overfitting (see below), where the model learns the training data too well and fails to generalize.

Rather than feeding the entire dataset to the model at once, data is divided into **batches**. Each batch is processed independently and updates the model weights based on the error for that subset. This is more efficient and allows for better use of memory.

To determine how the model processes the output of each layer, you have to define **activation functions**.

When training a model, you might run into **overfitting**. In short, overfitting means that your model learns the training data too well. It doesn’t just learn the general patterns that distinguish, say, bees from flies — it also memorizes irrelevant details: a bit of background blur, a specific angle, or lighting condition. As a result, it performs very well on the training set but poorly on new, unseen data. This defeats the purpose of machine learning, which is to generalize.

To reduce overfitting, you can:

* Use data augmentation to introduce variety (e.g., rotate, zoom, flip images)
* Add dropout layers to force the model to be less reliant on specific neurons
* Use regularization (L1/L2) to penalize overly complex model
* Limit the number of epochs, or use early stopping to halt training when validation performance stops improving
* Train with more data, if possible — the most effective solution, though not always available

Keeping an eye on validation accuracy (see below) during training is one of the simplest ways to spot overfitting early.

## How Learning Works in a CNN
Training a CNN means adjusting the internal weights of the network so it can make better predictions. At the start, these weights are just random numbers, so the model's guesses are basically noise.

Here’s how the learning process works — step by step:

1) The input image is passed through the network layer by layer. Each layer transforms the input, extracts features, and produces an output — ending in a prediction (e.g., class probabilities).

2) The model’s prediction is compared to the true label to measure how wrong the prediction is. For classification tasks, a common choice is categorical cross-entropy.

3) Backward pass (backpropagation): the model calculates how each weight contributed to the error. 

4) Weight update: The model updates its weights slightly.

This process is repeated over and over for each batch of images, across multiple epochs. Over time, the network “learns” which features are useful for solving the task and becomes better at making predictions.

## Understanding Model Performance
During training, you’ll see output that looks something like this:

```
Epoch 3/10
loss: 0.42 - accuracy: 0.85 - val_loss: 0.60 - val_accuracy: 0.78
```

Here’s what those values mean:

**Loss**: This is the value of the loss function — how wrong the model's predictions are on average. Lower is better. 

**Accuracy**: This is the percentage of correctly classified images. It’s intuitive, but not always enough on its own — especially for imbalanced datasets.


You’ll usually see:
Decrease in loss of training and validation -> Model is learning and generalizing well
Decrease in Training loss, increase in validation loss ->	Model is overfitting 
Both losses flat or erratic	-> Learning rate might be too high or too low

[Let's see it in action!](https://playground.tensorflow.org)

## Frameworks: TensorFlow vs PyTorch
There are several frameworks available to build CNNs, with TensorFlow and PyTorch being the most widely used. Both are open-source and work in Python.

TensorFlow was developed by Google. It’s widely used in industry

PyTorch was developed by Meta (formerly Facebook). It’s a bit more flexible in model building, especially for experimentation.

You can find a detailed explanation how to code a model in these two frameworks [here](https://www.analyticsvidhya.com/blog/2020/07/how-to-train-an-image-classification-model-in-pytorch-and-tensorflow/)


# get pretrainded models / prefitted architectures
Instead of doing everything from scratch, you might want to build upon prefitted detection architecture (a design of a deep neural network), such as YOLO. YOLO is a neural network architecture for object detection. There are pretrained YOLO models available for common tasks.



<!--more-->