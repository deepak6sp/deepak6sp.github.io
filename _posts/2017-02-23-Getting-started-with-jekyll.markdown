---
layout: post
title:  "Getting started with Jekyll"
date:   2017-02-23 22:21:57 +1100
categories: BuildTools
---

In order to install jekyll, we need to ruby gems.
You can install gems from here
https://rubygems.org/pages/download

After installing, make sure gems is working by typing <code> gems -v </code>

Now in the  terminal, type
{% highlight ruby %}
gem install jekyll bundler
{% endhighlight %}

Again, to make to jekyll is installed , type <code> jekyll -v </code>

After verifying everything is installed, lets start to create a basic blog by typing
{% highlight ruby %}
jekyll new my-blog
{% endhighlight %}

`my-blog` : is the name of the folder which jekyll creates. This is the root folder of our blog.

Now, change directory to my-blog
{% highlight ruby %}
cd my-blog
{% endhighlight %}
and in the terminal type
{% highlight ruby %}
jekyll serve
{% endhighlight %}
This will start local server. By default, Jekyll will use  `http://127.0.0.1:4000/`. Now type this url in the browser and this should display a basic blog site.

> Jekyll create *_site* folder. This is the compiled folder from where Jekyll serves all the pages, styles and scripts.

Thus, you have a blog up and running in few minutes.
