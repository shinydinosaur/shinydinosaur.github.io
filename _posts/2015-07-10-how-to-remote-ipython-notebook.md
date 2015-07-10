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
- On the remote server in the directory wher your ipython notebooks live/will live, start a screen session by typing 'screen' and hitting Enter.
- Start a browserless session of ipython notebook in your screen:
{% highlight bash %}
ipython notebook --no-browser
{% endhighlight %}
- Background your screen session (Ctrl-D).

## Connect to your ipython notebook session from your local computer
- In a shell in your local computer type:
{% highlight bash %}
ssh -NL 8888:localhost:8888 [YOUR SEVER NAME]
{% endhighlight %}
- Start a browser and point it to:
{% highlight bash %}
http://localhost:8888/
{% endhighlight %}

Enjoy!
