---
layout: post
title: "Putting the Git Branch Name on the Command Prompt"
date: 2014-12-11 20:32:00 -0800
comments: true
categories: [git, bash]
---

Sometimes it’s handy to always see which branch of the repository we’re working in. We can display this as part of the terminal command prompt by adding a few things to our local `.bashrc` file.

``` bash ~/.bashrc
function parse_git_branch {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

# This will display the current folder's full path.
# If you want only the folder name, replace \w with \W
export PS1="\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\[\033[31m\]\$(parse_git_branch)\[\033[0m\]\$ "
  
```

And now our command prompt looks like this:

```
you@host:~/Project/folder (master)$ 
```

The branch name will always be displayed in parenthesis for us.

