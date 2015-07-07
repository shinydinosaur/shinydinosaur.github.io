---
layout: post
title: "Softmax versus Soft-Maximum"
comments: true
published: true
---


<div class="message">
  Diving into the difference between what deep-learning people call a "softmax" and what optimization people call a "softmax" or a "soft-maximum".
</div>

## Softmax
In deep learning, there is an often-used function called a "softmax". Contrary to its name, it does not perform a max operation but is really a soft form of an argmax over its inputs. According to the [Wikipedia](https://en.wikipedia.org/wiki/Softmax_function) definition, if \(z\) is a K-dimensional vector of arbitrary real values, then the outout of the softmax, \(\sigma(z)\) is a K-dimensional vector of real values in \((0,1)\):

$$\sigma(z)_j = \frac{e^{z_j}}{\sum_{k=1}^{K}e^{z_k}}$$

For $$j=1\dots K$$.

## Soft-Maximum
