---
title: "Keras and Neural Networks"
slug: keras-and-neural-networks
---

[Keras](https://keras.io/) is a high level deep learning API that helps quickly build neural networks via a modular approach. Keras is built on top of [Tensorflow](https://www.tensorflow.org/), which provides support for training on CPU or GPU. With Keras, users can design and iterate on machine learning ideas, moving from experiments to production very quickly.

In this tutorial, we're going to build, train, and evaluate some deep learning classifiers in the context of Computer Vision with the [CIFAR-10 dataset](https://www.cs.toronto.edu/~kriz/cifar.html), a collection of images that can be classified into different categories based on type.

The `CIFAR-10` data set is one of the more well known classification problems in machine learning, similar to doing descriptive statistics with the titanic dataset. `CIFAR-10` contains 60000 32 × 32 pixel color images in 10 separate classes, with 6000 images per class. For training and testing, the set contains 50000 training images and 10000 in the test/validation image set.

>[info]
> If you can read more about `CIFAR-10`, [you can do so here](https://www.cs.toronto.edu/~kriz/cifar.html)
>
> Luckily, Keras has this dataset built in, but in case you run into issues, or would like to import it yourself. [Click here to download the set!](https://www.cs.toronto.edu/~kriz/cifar-10-python.tar.gz)

# Prerequisites

Before beginning this tutorial, you should have completed the following tutorials from DS 1.1 and DS 2.1:

- [App Store Dataset](https://www.makeschool.com/academy/track/app-store-dataset-tutorial)
- [Classification](https://www.makeschool.com/academy/track/ds-2-1-classification-tutorial)

# Learning Outcomes

By the end of this tutorial, you should be able to...

1. Implement a method to classify images
1. Explain what a Convolutional Neural Network is, and how it can be applied in the world of Data Science
1. Describe the layers of a Keras Sequential Model
1. Analyze a Keras implementation of a Convolutional Neural Network
1. Analyze the results of training and validating your model to then test it on data
1. Test your model for accuracy
1. Apply the concepts learned here in your own projects

>[action]
> Take a moment to write down these learning outcomes and reflect on them. Make sure that as you progress through the tutorial that you're furthering your understanding, and that by the end, you have completed all of the outcomes.
