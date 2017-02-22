---
layout: post
title:  "Webpack Basics"
date:   2017-02-22 22:21:57 +1100
categories: Build Tools
---

Build tools are becoming very popular these days. It is a must learn technology for
any web developer. Although, there are so many build tools such as gulp, grunt,
however, Webpack is at the top.

Lets start.
Yarn is my favourite these days, instead of npm. Yarn is faster. It works offline,
which means you don't need internet to install packages once installed.
Learn more about [yarn here]

On command line, do
{% highlight ruby %}
yarn init
yarn add --dev webpack webpack-dev-server
{% endhighlight %}

Lets write a basic webpack config file.
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
