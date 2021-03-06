---
layout: post
title: "Softmax versus Soft-Maximum"
comments: true
published: true
---





<div class="message">
  Diving into the difference between what deep-learning people call a "softmax" and what optimization people call a "softmax" or a "soft-maximum".
</div>

## Softmax (a.k.a the deep-learning softmax)
In deep learning, there is an often-used function called a "softmax". Contrary to its name, it does not perform a max operation but is really a soft (or differentiable) form of an argmax over its inputs. According to the [Wikipedia](https://en.wikipedia.org/wiki/Softmax_function) definition, if \\(z\\) is a \\(K\\)-dimensional vector of arbitrary real values, then the outout of the softmax, \\(\sigma(z)\\) is a \\(K\\)-dimensional vector of real values in \\((0,1)\\) that also sum up to \\(1\\) and are therefore a categorical probability distribution. For \\(j=1\dots K\\) the softmax is defined as follows:

$$\sigma(z)_j = \frac{e^{z_j}}{\sum_{k=1}^{K}e^{z_k}}$$

Each output of the softmax is the predicted probability of the \\(j\\)'th class. The softmax's largest component will therefore be associated with the class \\(j\\) that has the largest probability, or the argmax class. Note that \\(\sigma(z)\\) does not return the maximum value of its input vector \\(z\\) like one would expect from a true "max" function, so the naming convention here is pretty confusing.


## Soft-Maximum (a.k.a the optimization softmax)
Optimization people have a whole other story to tell. It turns out that there *is* a nice, differentiable, soft version of a max function. They like to call it a "softmax" (which does make sense), but we will call it a soft-maximum to avoid a clobbering of names. A nice explanation (with pictures!) can be found in [this blog post](http://www.johndcook.com/blog/2010/01/13/soft-maximum/) and here is the gist of it:

The regular version of \\(\max(a,b)\\) is not differentiable and therefore a royal pain to use in function optimizations. Instead, lets assume without loss of generality that \\(a \gt b\\) and observe the following soft version of the maximum:

$$\log(e^a+e^b)$$

If \\(a \gt b\\) then we can play the following game and end up with an equivalent formula:

$$\log(e^{a-a}+e^{b-a})+a$$

Now \\(e^{a-a}==1\\) and since \\(a \gt b\\) we know that \\(e^{b-a}\lt 1\\). This means that the whole left hand side of the formula is bounded:

$$0 \lt \log(e^{a-a}+e^{b-a}) \lt \log 2$$

And therefore the whole soft-maximum is less than \\(\log 2\\) away from \\(a\\), the maximum over all of its inputs. a.k.a:

$$\log(e^a+e^b) < a + \log 2 < \max(a,b) + \log 2$$

Pretty neat, no? And all of this with a fully differentiable function.





