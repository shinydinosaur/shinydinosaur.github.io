---
layout: post
title: "How To: Set Up a Remote Jupyter Lab Session"
comments: true
published: true
---






<div class="message">
  How to set up a Jupyter Lab session on a remote server and connect to it from your local machine.
</div>

Sometimes (ok usually) you run long-running computations on a remote server but would like the convenience of looking at your results locally.

## Set up a Jupyter Lab session on a remote server
- On the remote server in the directory where your ipython notebooks live/will live, start a screen session by typing 'screen' and hitting Enter.
- Start a browserless session of Jupyter Lab in your screen:
{% highlight bash %}
jupyter lab --no-browser
{% endhighlight %}
- Figure out which PORT your jupyter server is running on. This will get printed on the screen together with a WEB-ADDRESS. Copy this web address.
- Background your screen session (Ctrl-D).

## Connect to your Jupyter Lab session from your local computer
- In a shell in your local computer type:
{% highlight bash %}
ssh -NL <PORT>:localhost:<PORT> <YOUR SEVER NAME>
{% endhighlight %}
- Start a browser and point it to the WEB-ADDRESS you copied.

Enjoy!
