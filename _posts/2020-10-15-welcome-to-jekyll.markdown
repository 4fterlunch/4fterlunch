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

Next up you'll need to add this to your z shell profile, this file should be names .zshenv. If you dont have one then you'll need to make one using `touch ~/.zshenv`.

Edit the profile, if you don't care then use nano:
{% highlight bash %}
nano ~/.zshenv
{% endhighlight %}
Simply append this to your .zshenv:
{% highlight bash %}
fpath=(~/.zsh $fpath)
{% endhighlight%}

Save and close, then lastly, restart your shell, or call `source ~/.zshenv`.

Enjoy git autocomplete on Mac OS X!

