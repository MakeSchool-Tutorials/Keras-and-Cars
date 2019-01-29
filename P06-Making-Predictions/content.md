---
title: "Making Predictions"
slug: making-predictions
---

Now that we've constructed and trained a model that's gotten solid training, It's time for us to test it on some data!

# Running Predictions

Earlier in the tutorial we had the following :

`x_test, y_test`

We're going to use `x_test` to test the accuracy of our model in real time and see how we stack up!

The function for predicting classes in Keras is the given below:

`model.predict_class()`

Let's try that now!

>[action]
> Add the following to your notebook:
>
```python
y_predicts = model.predict_classes(x_test)
y_predicts
```
>
> Run this and check that your output matches the following:
>
```
array([3, 8, 8, ..., 5, 4, 7])
```

This gives us back an array of integers that represent the categories that our network has classified our test data into! This means you've successfully **analyzed the results of training and validating your model and tested it on data!** Pretty cool, huh?
