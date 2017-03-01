---
layout: post
title:  "Webpack Basics ( With Yarn )"
date:   2017-02-22 22:21:57 +1100
categories: BuildTools
---

Build tools are becoming very popular these days. It is a must learn technology for
any web developer these days. Although, there are so many build tools such as gulp and grunt,
webpack is at the top.

Lets start.
Yarn is my favourite these days as Yarn is faster than npm and also takes offline approach,
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

and lets write basic webpack configuration. <br>
{% highlight ruby %}
module.exports = {
  entry:  "./app/main.js",
  output: {
    path: __dirname + "/public",
    filename: "bundle.js"
  }
}
{% endhighlight %}

`entry` : is the app entry point.

`__dirname` : gives us current folder path.

`output - path`: is the output folder

`output - filename` : is the name of the file. In our case, it is bundle.js

So in index.html , we can just add a script tag
{% highlight ruby %}
<script type="text/javascript" src="bundle.js"></script>
{% endhighlight %}

How to run webpack-dev-server?

You could run web pack-dev-server from command line but I prefer to run through
scripts in package.json.
So, in package.json file, under scripts
{% highlight ruby %}
"scripts": {
  "start": "webpack --progress --colors",
  "server": "webpack-dev-server --progress --colors  --content-base ./ —-port 3000 "
}
{% endhighlight %}
**--content-base** is where html is served from, './' represents root folder and <br>
**--port** is which port to use, which is 3000 in this case

On the command line,
{% highlight ruby %}
yarn run server
{% endhighlight %}

Webpack-dev-server watches for any file changes and serves bundle.js from the
memory.
>Webpack-dev-server will not generate file in the output folder.

However, run
{% highlight ruby %}
yarn start
{% endhighlight %}
will start webpack and generates bundle.js file in the output folder.

Now, go to `http://localhost:3000/` and see the working page.

Passing --watch argument watches file changes.
So, in package.json file, under scripts
{% highlight ruby %}
"scripts": {
  "start": "webpack --progress --colors",
  "watch": "webpack --progress --colors --watch",
  "server": "webpack-dev-server --progress --colors  --content-base ./ —-port 3000 "
}
{% endhighlight %}



[yarn here]: https://yarnpkg.com/en/
