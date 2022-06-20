---
title: 'The power of aliases 🦍'
date: 2022-06-18T12:00:00+00:00
draft: false
tags:
  - alias
  - save work
  - automate
  - scripting
categories:
  - automating
  - scripting
---

# What is an alias? 🧩

It could be your nickname or the username for your favorite video game, you got it but,
the alias I'm trying to show you is the alias used by most command languages like the bash shield, git CLI, among others. So, what it is? it's just a way of short-naming some long command or  commands you just don't wanna type every time to time, like

{{< highlight bash >}}
$ cd /main/route/to/my/project/folder
{{< /highlight >}}

with an alias, you can define a short way to get to your project folder like this

{{< highlight bash >}}
alias project="cd /main/route/to/my/project/folder"
{{< /highlight >}}

So every time you need to get to your project folder you can just type

{{< highlight bash >}}
$ project
{{< /highlight >}}

maybe you just need to predefine options for your commands like:

{{< highlight bash >}}
alias ls="ls -al"
{{< /highlight >}}

so, every time you hit ls the options -a y -l are by default added to your command.


and that's it, no more code needed, no need to know where your folder is. This example is very basic, the alias power is as big as the 🧠 who uses it, so take a moment and think, how powerful do I am, and how powerful do I wanna be.

# Is the bash shell the only way to use aliases? 😕
short answer: NO, obviously no bro, what power can have aliases if it was restricted to bash shell?. Here is a list of common places where to find aliases power:

- Any unix compatible shell (bash, Z, etc...)
- Any POSIX compatible Shell (Korn Shell, ksh, etc...)
- Git CLI
- SQL
- a big ETC (If you have something that you type a lot of the same thing every now and then, check if you can define an alias there).

## You don't trust me, right? :satisfied:
I'll show you this useful alias to count lines added/removed by an git contributor:

{{< highlight bash >}}
git config --global alias.count-lines "! git log --since=\"\$1\" --until=\"\$2\" --author=\"\$3\" --pretty=tformat: --numstat -- | awk '{ add += \$1; subs += \$2; loc += \$1 - \$2 } END { printf \"added lines: %s, removed lines: %s, total lines: %s\n\", add, subs, loc }' #"
{{< /highlight >}}

So, yes sir, alias could be everywhere is a matter of asking, is alias here? and unlock the power of it :wink:

# Yes, you can also use variables and parameters with alias :smirk:
You must use bash functions for this, like if a bash script functions was, let me show you an example:

{{< highlight bash >}}
alias rikyCC='function _rikyCC(){python /route/to/a/python/executable.py after=$1 before=$2 author="fixedParam"};_rikyCC'
{{< /highlight >}}

## Deconstructing the alias:
you can name the elias as you wish, as so the inner function name with must be declared and then called after the ;

{{< highlight bash >}}
alias __AliasName__='function __FunctionName__(){python /route/to/a/python/executable.py after=__function_param_1__ before=__function_param_2__  __any_other_params_needed__};__FunctionName__'
{{< /highlight >}}


# How can you configure your own alias?
for most shells you just need to find your user shell configuration file like ~/.zshrc for Z shell or the ~/.bashrc for bash shell, there you can define your aliases like I shown you before:

{{< highlight bash >}}
alias __AliasName__='what to do when __AliasName__ is typed down in the console'
{{< /highlight >}}

Remember to reload the rc file with:

{{< highlight bash >}}
source ~/.zshrc
{{< /highlight >}}

or just close the terminal and open it up back again.

# Still don't know if is worth the pain?

## Most useful scripts for you linux/mac user
https://www.cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix.html

## Keep digging and break the links of ignorance :link:
https://shapeshed.com/unix-alias/#some-examples-of-aliases

# Need more help/info? try to contact me by email :fire: