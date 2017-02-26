---
layout: post
title:  "Show git branch on the bash command prompt"
date:   2017-01-24 22:21:57 +1100
category: Git
---
By default, command prompt does not display git branch names. You would generally see this.

<pre>deepak@Deepaks-MacBook-Pro githubBlog $</pre>

In the terminal, type
<pre>
touch ~/.bash_profile
vi ~/.bash_profile
</pre>

Now, in .bash_profile, copy the code below
<pre>
parse_git_branch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
export PS1="\u@\h \W\[\033[32m\]\$(parse_git_branch)\[\033[00m\] $ "
</pre>

Reopen terminal

<pre>deepak@Deepaks-MacBook-Pro githubBlog (master) $</pre>
