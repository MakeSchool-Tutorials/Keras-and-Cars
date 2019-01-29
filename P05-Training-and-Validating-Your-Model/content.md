---
title: "Training and Validating Your Model"
slug: training-and-validating-your-model
---

We're now at the point in which we can now **fit** our model to our data. This step will tell us how well the model we've created will generalize. It's also one of the final steps before we train and test our model! This gives us access to insights for tweaking our model for better performance.

# Parameters

## Epoch

**Epoch** is one forward pass and one backward pass of all the training examples

## Batch_size

The **Batch_size** algorithm will now take the first 100 samples (from 1st to 100th) from the training data and trains the network. Next it takes the second 100 samples (from 101st to 200th) and trains the network again. We can keep doing this procedure until we have propagated through all samples of the network. A problem usually happens with the last set of samples. In our example we've used 50000 which is divisible by 100 without remainder.

There are some advantages of using a batch size smaller than the number of all samples:

1. **It requires less memory.** Since you train the network using fewer samples, the overall training procedure requires less memory. That's especially important if you are not able to fit the whole dataset in your machine's memory.
1. Typically networks train faster with **mini-batches.** That's because we update the weights after each propagation. In our example we've propagated our batches and after each of them we've updated our network's parameters. If we used all samples during propagation we would make only 1 update for the network's parameter.

# Calling Validate()

Lets execute this below and get our scores by using the `model.validate()`

**WARNING: This can take up to ~1.5 hours to run to completion.** Make sure to get this going and then check in on it later.

>[action]
> Add the following to your notebook:
>
```python
model.fit(x_train, y_train, validation_data=(x_test, y_test), epochs=10, batch_size=100)
# Final evaluation of the model
scores = model.evaluate(x_test, y_test, verbose=0)
print("Accuracy: %.2f%%" % (scores[1]*100))
```
>
> Run this, and after completion, check to see if it matches the results below:
>
```
Train on 50000 samples, validate on 10000 samples
Epoch 1/10
50000/50000 [==============================] - 1553s 31ms/step - loss: 1.7090 - acc: 0.3742 - val_loss: 1.2892 - val_acc: 0.5313
Epoch 2/10
50000/50000 [==============================] - 1829s 37ms/step - loss: 1.2888 - acc: 0.5361 - val_loss: 1.1323 - val_acc: 0.5974
Epoch 3/10
50000/50000 [==============================] - 859s 17ms/step - loss: 1.1201 - acc: 0.6006 - val_loss: 0.9846 - val_acc: 0.6510
Epoch 4/10
50000/50000 [==============================] - 1316s 26ms/step - loss: 1.0093 - acc: 0.6423 - val_loss: 0.8895 - val_acc: 0.6872
Epoch 5/10
50000/50000 [==============================] - 5490s 110ms/step - loss: 0.9271 - acc: 0.6736 - val_loss: 0.8358 - val_acc: 0.7075
Epoch 6/10
50000/50000 [==============================] - 950s 19ms/step - loss: 0.8722 - acc: 0.6939 - val_loss: 0.8085 - val_acc: 0.7156
Epoch 7/10
50000/50000 [==============================] - 931s 19ms/step - loss: 0.8313 - acc: 0.7074 - val_loss: 0.7890 - val_acc: 0.7185
Epoch 8/10
50000/50000 [==============================] - 904s 18ms/step - loss: 0.7964 - acc: 0.7229 - val_loss: 0.7523 - val_acc: 0.7361
Epoch 9/10
50000/50000 [==============================] - 948s 19ms/step - loss: 0.7756 - acc: 0.7277 - val_loss: 0.7231 - val_acc: 0.7494
Epoch 10/10
50000/50000 [==============================] - 909s 18ms/step - loss: 0.7478 - acc: 0.7388 - val_loss: 0.7270 - val_acc: 0.7487
Accuracy: 74.87%
```

Based on the random seed that we set earlier, you should be getting accuracies _above 70%_ or so with this model! This means that as of now, if you were to give it a picture that could be classified into one of the 10 categories, about 70% of the time it would be right!

Lets go on to making some predictions!
