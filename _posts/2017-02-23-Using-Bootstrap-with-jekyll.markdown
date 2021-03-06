---
layout: post
title:  "Using Bootstrap with Jekyll"
date:   2017-02-23 22:21:57 +1100
categories: BuildTools
---
Before starting with this section, if you would like to know 'How to get started with
Jekyll', click <a href="{{page.previous.url}}">here</a>.

To use bootstrap or any other front end framework,  we need to have directory structure as shown here
`https://jekyllrb.com/docs/structure/`


To start with, in `index.html` under root folder, modify the line
<code>layout: home</code> to <code>layout:default</code>

Then, we will add 2 folders `_includes` and `_layouts` to root folder.

In `_includes` folder, create new file `scripts.html`. We will use Jquery and Bootstrap cdn,
so add these scripts

<strong>scripts.html</strong>
{% highlight ruby %}
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.2/jquery.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
{% endhighlight %}


In `_layouts`, create new file `default.html` and add the following content.

<strong>default.html</strong>
{% highlight ruby %}
<!DOCTYPE html>
<html class="no-js">
<head>
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
</head>
<body>
  <div class="content">
    <div class="container">
      {{ "{{ content " }}}}
    </div>
  </div>
  {{ " {% include scripts.html" }} %}
</body>
</html>
{% endhighlight %}

And, in the body section of `default.html`, add
{% highlight ruby %}
{{ " {% include header.html " }} %}
{% endhighlight %}


To test bootstrap framework is working, in `_includes` folder, create another file `header.html` and
add the code below

<strong>header.html</strong>
{% highlight ruby %}
<header>
  <nav class="navbar navbar-default">
    <div class="container-fluid container">
      <!-- Brand and toggle get grouped for better mobile display -->
      <div class="navbar-header">
        <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false">
          <span class="sr-only">Toggle navigation</span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>
        <a class="navbar-brand" href="/">{{ site.title }}</a>
      </div>
      <!-- Collect the nav links, forms, and other content for toggling -->
      <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
        <ul class="nav navbar-nav navbar-right">
		<li><a href=“/home“>Home</a></li>
            	<li><a href=“/about“>About</a></li>
		<li><a href=“/contact“>Contact</a></li>
        </ul>
      </div><!-- /.navbar-collapse -->
    </div><!-- /.container-fluid -->
  </nav>
</header>
{% endhighlight %}

Now, in your terminal, run
{% highlight ruby %}
jekyll serve
{% endhighlight %}

This will serve up new blog with bootstrap framework. However, this will not show up the posts.

So, just add the code below in `index.html`,

<strong>index.html</strong>
{% highlight ruby %}
<ul>
  {{ " {% for post in site.posts" }} %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {{ " {% endfor" }} %}
</ul>
{% endhighlight %}


Now, you have successfully running <strong>Bootstrap enabled Jekyll blog</strong>.
