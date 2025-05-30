+++
date = '2025-05-21T17:03:20-07:00'
draft = false
title = 'Putting the Git Branch Name on the Command Prompt'
tags = ["code", "fun"]
+++

I originally posted this in Octopress on Dec 11th 2014.

Sometimes it’s handy to always see which branch of the repository we’re working in. We can display this as part of the terminal command prompt by adding a few things to our local `~/.bash_profile` file.

```bash {linenos=inline}
# Filename: ~/.bash_profile
function parse_git_branch {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
# This will display the current folder's full path.
# If you want only the folder name, replace \w with \W
export PS1="\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\[\033[36m\]\$(parse_git_branch)\[\033[0m\]\$ "
```
<br>

And just for posterity, here's a snapshot of the original site:

![A screenshot of the original website,](/images/original_site.png)

