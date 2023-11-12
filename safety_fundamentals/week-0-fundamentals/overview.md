- [Overview](#overview)
  - [](#)
  - [](#-1)
  - [Machine learning tasks](#machine-learning-tasks)
    - [Supervised learning](#supervised-learning)
    - [Unsupervised learning](#unsupervised-learning)
    - [Self-supervised learning](#self-supervised-learning)
    - [Reinforcement Learning](#reinforcement-learning)

# Overview
##

* Pretty much each list in this first section is non-exhaustive.

The term artificial intelligence is split into two different pieces, "tasks" and "techniques".

Under the category of "tasks" we find:
- Answering questions
- Recognizing images
- generalizing content
- following instructions
- controlling robots

Under the category of "AI techniques" we find:
- Symbolic AI
    - Logic
    - Search
- Learning

Under the label "Learning" (aka machine learning), we again find "tasks" and "techniques".

Included in "tasks" are:
- supervised learning
- self-supervised learning
- reinforcement learning

Included in "techniques" are:
- Statistical modeling
- Graphical Modeling
- Deep Learning

Deep Learning is split into two parts:
- Optimization techniques
- Neural Network architectures

"Optimization techniques" include:
- gradient descent
- backpropagation
- momentum

"Neural Network architectures" include:
- Convolutional networks
- Recurrent networks
- Transformers


We can visualize the above like so:
Artificial intelligence
  - Tasks
    - Answering questions
    - Recognizing images
    - generating content
    - following instructions
    - controlling robots
  - Techniques
    - Symbolic AI
      - Logic
      - Search
    - Learning (ML)
      - ML Tasks
        - Supervised learning
        - Self-supervised learning
        - Reinforcement learning
      - ML Techniques
        - Convolutional networks
        - Recurrent networks
        - Transformers

##

The first major paradigm in AI was Symbolic ai, which operated deontologically, using rules from language, human or code.

Since the 90s the major paradigm in AI is machine learning, which uses free parameters that start off as random and are slowly trained based upon the data they are given.

_Learning_ is also known as training or _optimization process_.

Deep learning
- uses billions of parameters.
- the process involves training a neural network with many layers
  - this is done through an optimization technique such as
    - gradient descent
    - backpropagation


Neural networks
- known as deep neural networks if there is more than one layer between input and output

Activation - a neuron receives signals from all of the neurons in the preceding layer and turns it into a single value, which is called its activation. It then passed the activation to all of the neurons in the next layer

a Weight - the strength of a connection between neurons

Objective function (aka loss function) - the function by which we measure how optimized a model is.

Gradient descent - a way to optimize a model where the weights begin as random, and are slowly updated in the direction of their gradient with respect to the objective function.

Backpropagation = The gradients of the wights can be calculated layer by layer. Going from the last layer and moving backwards is called *backpropagation*.

There are several architectures for neural networks:
  - fully-connected networks: where every neuron in a layer is connected to every neuron in the layers next to it
  - convulational networks
  - recurrent networks
  - transformers

## Machine learning tasks

### Supervised learning
requires a data set where each data point has a label and are used to predict labels that correspond with values
  - tasks
    - classification problem - requiring prediction on different categories
    - regression problem - requiring prediction on a continuum of values
    - reward modeling
  - techniques
    - most neural networks
    - support vector machines
    - Gaussian processes

### Unsupervised learning
implementing supervised learning without the labels
### Self-supervised learning
self-supervised learning - implementing supervised learning by finding automatic ways to convert an unlabeled dataset into a labeled dataset

examples of self-supervised learning:
  - next-word prediction such as:
  - GPT-2 and 3
  - Dall-E

- tasks
  - image generation
  - language modeling
  - behavioral cloning
- techniques
  - autoregression
  - generative adversarial networks
  - diffusion modeling

### Reinforcement Learning
There is no fixed dataset, but an environment where actions are taken and rewards are given.
- tasks
  - exploration
  - temporal credit assignment
  - multi-agent credit assignment
- techniques
  - q-learning
  - policy gradients
  - self-play
  - intrinsic motivation

Credit assignment - the problem of knowing which actions are responsible for which rewards
