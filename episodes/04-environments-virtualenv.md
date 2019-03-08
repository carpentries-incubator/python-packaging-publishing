---
title: "Managing Python Environments with VirtualEnv"
teaching: 0
exercises: 0
questions:
- "How can I make sure the whole team (or lab) gets the same results?"
- "How can I simplify setup and dependencies for people to use my code or reproduce my results?"
objectives:
- "Identify an environment, dependencies, and an environment manager"
- "Install an older version of python"
- "Use virtualenv to create an environment per project"
- "Store a projects' dependencies"
- "install dependencies for a project"
keypoints:
- "A python dependency is another, independent package that a given project uses and requires to be able to run"
- "An environment is"
- "An environment manager enables one step installing and documentation of dependencies, including versions"
- "Virtualenv is ..."
---

# Environments and Package managers

An environment consists of a certain Python version and some packages. A virtual environment allows you to have multiple, independent versions of python on your system. Environments can also be saved so that you can install all of the packages and replicate the environment on a new system.

Why use one:
- to deliver code and keep it the same versions
- to use contribute to a package you also use
- to install on servers
- to share your environment with others

how to chose which of the main strategies to use: `virtualenv` and `pip` or `conda`

`conda` comes from Anaconda and does both package management and provides a virtual environment.

`pip` is the main python package installer

`virtualenv` creates environments and are `pip` install compatible.

Making your own packages pip installable requires fewer dependencies, so we'll focus on `virtualenv` and `pip` in this workshop

<!-- ## Dependencies

what are dependencies?

> ## Exercise
> FIXME -->

## Create an environment

First, we'll download create an environment

~~~

virtualenv
~~~
{: .language-bash}




## Install from a requirements.txt

Getting a requirements.txt from ...

~~~
pip install FIXME
~~~
{: .language-bash}

## Install from scratch

> ## Exercise
> create a new environment
>
{: .challenge}



## save an environment

~~~
pip freeze > requirements.txt
~~~
{: .language-bash}

{% include links.md %}
