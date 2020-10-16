---
layout: post
title:  "Mac OS X: Adding git autocomplete to Z Shell"
date:   2020-10-15 21:26:02 +1100
categories: macos, z shell, git, autocomplete
---
*I love working on a Mac, and as far as unix-like shell goes, it goes pretty well.* One thing that i always miss though is autocomplete for git. Fear not though, here is how you can add git autocomplete to your z shell.

We will follow the recommendations from git.

First of all, fire up z shell and create a .zsh directory in your home file
{% highlight bash %}
mkdir ~/.zsh
{% endhighlight %}
 and curl yourself the autocomplete z shell script from GIT straight into the home directory.

{% highlight bash %}
curl https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.zsh -o ~/.zsh/git-completion.bash
{% endhighlight %}

Next up you'll need to add this to your zshrc file, this file should  start up nano: `nano ~/.zshrc`.

Simply append this to your .zshrc:
{% highlight bash %}
zstyle ':completion:*:*:git:*' script ~/.zsh/git-completion.bash
fpath=(~/.zsh $fpath)
autoload -Uz compinit && compinit
{% endhighlight%}

Save and close, then restart your z shell.

Ok so on restarting you will probably get a message like this:
{% highlight bash %}
zsh compinit: insecure directories, run compaudit for list.
Ignore insecure directories and continue [y] or abort compinit [n]? 
ccompinit: initialization aborted
{%endhighlight%}

Z shell is complaining about the ownership of these two directories:
{% highlight bash %}
/usr/local/share/zsh/site-functions
/usr/local/share/zsh
{%endhighlight%}

So let's go ahead and secure these directories
{% highlight bash %}
sudo chmod -R 755 /usr/local/share/zsh/site-functions && chmod -R 755 /usr/local/share/zsh
{%endhighlight%}

restart shell again and you should not get this message again.

Enjoy git autocomplete on Mac OS X!


