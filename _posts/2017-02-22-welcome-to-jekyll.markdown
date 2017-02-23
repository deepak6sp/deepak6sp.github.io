---
layout: post
title:  "Webpack Basics"
date:   2017-02-22 22:21:57 +1100
categories: Build Tools
---

Build tools are becoming very popular these days. It is a must learn technology for
any web developer these days. Although, there are so many build tools such as gulp and grunt,
webpack is at the top.

Lets start.
Yarn is my favourite these days as Yarn is faster and also takes offline approach,
which means, you don't need internet connectivity to install packages once installed.

Learn more about [yarn here]

On command line, do
{% highlight ruby %}
yarn init
yarn add --dev webpack webpack-dev-server
{% endhighlight %}


Create a filename **webpack.config.js** at
the root of the project.
{% highlight ruby %}
touch webpack.config.js
{% endhighlight %}

and lets write a basic webpack configuration. <br>
{% highlight ruby %}
module.exports = {
  entry:  "./app/main.js",
  output: {
    path: __dirname + "/public",
    filename: "bundle.js"
  }
}
{% endhighlight %}

Let me explain each line.

`entry` : is the app entry point.

`__dirname` : gives us current folder path.

`output - path`: is where [ filename - on the next line ] file is saved.

`output - filename` : is the name of the file. In our case, it is bundle.js

So in our index.html , we can just add a script
{% highlight ruby %}
<script type="text/javascript" src="bundle.js"></script>
{% endhighlight %}

How to run webpack-dev-server?

You could run web pack-dev-server from command line but I prefer to run through npm scripts.
So, in package.json file, under scripts
{% highlight ruby %}
"scripts": {
  "start": "webpack --progress --colors",
  "server": "webpack-dev-server --progress --colors  --content-base ./ —port 3000 "
}
{% endhighlight %}
Here, content-base is where html is served from - in this case, ./ means the current directory.
Now, go to `http://localhost:3000/` and see the working page.


[yarn here]: https://yarnpkg.com/en/
