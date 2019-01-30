---
title: "Checking for Accuracy"
slug: checking-for-accuracy
---

Now we need to check the accuracy of our model. Earlier, we one-hot-encoded our `y_test` for processing. Now what we'll do is convert it back into an `NP array` that we can iterate over and check our `y_predicts` again. Let's do that now!

>[action]
> Add the following to your notebook
>
```python
y_test_argmax =np.argmax(y_test, axis=1)
```

Great! To check the accuracy, we'll iterate over both the the original `y_test` labels and our predictions and compare the results. We'll then do some simple math to get our percentages for correct and incorrect results, which should be relatively close to our model's reported accuracy!

>[info]
> There are a few ways in which we could have tested our models for accuracy that go beyond the scope of this tutorial, such as [k-fold validation](https://machinelearningmastery.com/k-fold-cross-validation/).

<!-- -->

>[action]
> Add the following to your notebook and run it
>
```python
total_count = len(y_test_argmax)
correct_count = 0
incorrect_count = 0
for num in range(len(y_test_argmax) -1):
    if y_test_argmax[num] == y_predicts[num]:
        correct_count += 1
    else:
        incorrect_count += 1
>
percentage_correct = correct_count/total_count
percentage_incorrect = incorrect_count/total_count
'The percentage of correctly classified pictures is {}. The percentage of correctly  classified pictures is {}'.format(percentage_correct*100,percentage_incorrect*100)
```
> You should see something like the following for the output:
>
```
'The percentage of correctly classified pictures is 75.21. The percentage of correctly  classified pictures is 24.779999999999998'
```

As you see with the calculations above, the model performs with an accuracy of **75.21%** which is spot on for our model's summary training of 74.87%!

You've now not only successfully **tested your model for accuracy**, but have also completed the tutorial! Congratulations! You should now feel comfortable **applying the concepts you learned here to projects of your own!**

# Feedback and Review

Please take a moment to rate your understanding of learning outcomes from this tutorial, and how we can improve it via our [tutorial feedback form](https://goo.gl/forms/tY7PkZiKfFsQT9CC3)
