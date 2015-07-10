---
layout: post
title: "How To: Set Up a Remote ipython Notebook Session"
comments: true
published: true
---






<div class="message">
  How to set up an ipython notebook session on a remote server and connect to it from your local machine.
</div>

Sometimes (ok usually) you run long-running computations on a remote server but would like the convenience of looking at your results locally. This is my current solution to this problem which also plays really well with [caffe](http://caffe.berkeleyvision.org/).

## Set up an ipython notebook session on a remote server
1. On the remote server in the directory wher your ipython notebooks live/will live, start a screen session by typing 'screen' and hitting Enter.
2. Start a browserless session of ipython notebook in your screen:
{% highlight js %}
ipython notebook --no-browser
{% endhighlight %}
3. Background your screen session (Ctrl-D).

## Connect to your ipython notebook session from your local computer
1. In a shell in your local computer type:
{% highlight js %}
ssh -NL 8888:localhost:8888 [YOUR SEVER NAME]
{% endhighlight %}
2. Start a browser and point it to:
{% highlight js %}
http://localhost:8888/
{% endhighlight %}

Enjoy!
