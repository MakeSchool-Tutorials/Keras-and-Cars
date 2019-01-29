---
title: "Keras CNN Implementation"
slug: keras-cnn-implementation
---

Now that we've learned all the parts of a CNN, let's implement it in our notebook!

>[action]
> Add the following to your notebook:
>
```python
model = Sequential()
model.add(Conv2D(32, kernel_size=(3, 3), padding='same',input_shape=x_train.shape[1:]))
model.add(Activation('relu'))
model.add(Conv2D(32,kernel_size=(3, 3)))
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))
model.add(Dropout(0.25))
>
model.add(Conv2D(64, kernel_size=(3, 3), padding='same'))
model.add(Activation('relu'))
model.add(Conv2D(64, kernel_size=(3, 3)))
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))
model.add(Dropout(0.25))
>
model.add(Flatten())
model.add(Dense(512))
model.add(Activation('relu'))
model.add(Dropout(0.5))
model.add(Dense(num_classes))
model.add(Activation(tf.nn.softmax))
```

# Compiling, running and analyzing our models

The internal parameters of a model play a very important role in efficiently and effectively training a model and produce accurate results. This is why we use various optimization strategies and algorithms to update and calculate appropriate and optimum values of a model’s parameters which influence our model’s learning process and the output of a model.

Compiling the model takes three parameters: **optimizer, loss and metrics.**

We do this by using the built in `compile` function: `model.compile()`

Let's break this down into its components before we compile it:

## Optimization algorithms

**Optimization algorithms** help us to minimize our model's errors. It is usually based off either the [Stochastic Gradient Descent](https://en.wikipedia.org/wiki/Stochastic_gradient_descent), which is what we will be using today, or the [Adam optimizer](https://machinelearningmastery.com/adam-optimization-algorithm-for-deep-learning/). This tutorial won't cover all of it's parameters, but this will be covered in your course in depth.

Of note is the **learning rate** which controls how quickly your model forgets old information as new information is fed into it. A slow learning rate means that your model will train slower but will be less prone to outliers and smaller changes in the data. A larger learning rate will respond quickly to new changes but will be affected greatly by this new data. Chose your learning rate based on what your model needs to accomplish.

## Loss

A **loss function** is simple: it’s a method of evaluating how well your CNN models your data. If your predictions are extremely off, your loss function will output a higher number. If they’re pretty good, it will output a lower number. As you change pieces of your algorithm to try and improve your model, your loss function will tell you if you’re getting anywhere.

##Metrics

The **metrics** will output exactly what it says, the metrics for this model that you want to be measured, have a look at the [documentation](https://keras.io/metrics/)


# Model Summary

Running `summary()` will give you a summary of your model in it's current form.

Let's look at this!

>[action]
> Add the following to your notebook:
>
```python
sgd = SGD(lr=0.01, decay=1e-6, momentum=0.9, nesterov=True)
model.compile(loss='categorical_crossentropy', optimizer=sgd, metrics=['accuracy'])
model.summary()
```
>
> Your output should match the following:
>
```
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
conv2d_1 (Conv2D)            (None, 32, 32, 32)        896       
_________________________________________________________________
activation_1 (Activation)    (None, 32, 32, 32)        0         
_________________________________________________________________
conv2d_2 (Conv2D)            (None, 32, 30, 30)        9248      
_________________________________________________________________
activation_2 (Activation)    (None, 32, 30, 30)        0         
_________________________________________________________________
max_pooling2d_1 (MaxPooling2 (None, 32, 15, 15)        0         
_________________________________________________________________
dropout_1 (Dropout)          (None, 32, 15, 15)        0         
_________________________________________________________________
conv2d_3 (Conv2D)            (None, 64, 15, 15)        18496     
_________________________________________________________________
activation_3 (Activation)    (None, 64, 15, 15)        0         
_________________________________________________________________
conv2d_4 (Conv2D)            (None, 64, 13, 13)        36928     
_________________________________________________________________
activation_4 (Activation)    (None, 64, 13, 13)        0         
_________________________________________________________________
max_pooling2d_2 (MaxPooling2 (None, 64, 6, 6)          0         
_________________________________________________________________
dropout_2 (Dropout)          (None, 64, 6, 6)          0         
_________________________________________________________________
flatten_1 (Flatten)          (None, 2304)              0         
_________________________________________________________________
dense_1 (Dense)              (None, 512)               1180160   
_________________________________________________________________
activation_5 (Activation)    (None, 512)               0         
_________________________________________________________________
dropout_3 (Dropout)          (None, 512)               0         
_________________________________________________________________
dense_2 (Dense)              (None, 10)                5130      
_________________________________________________________________
activation_6 (Activation)    (None, 10)                0         
=================================================================
Total params: 1,250,858
Trainable params: 1,250,858
Non-trainable params: 0
_________________________________________________________________
```

Congrats, you just **analyzed a Keras implementation of a Convolutional Neural Network!** Now we'll learn how to train and validate our model!
