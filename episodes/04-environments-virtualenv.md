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

# Environments and environment managers

An environment consists of a certain Python version and some packages

Why use one:
- to deliver code and keep it the same versions
- to use contribute to a package y

how to chose which of the main strategies to use: virtualenv and pip or conda

## Dependencies



## Create an environment



## Install from a requirements.txt



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
