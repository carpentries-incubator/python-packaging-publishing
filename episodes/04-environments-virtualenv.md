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

Before we create and environment, let's see what happens when we import one of
our favorite packages.  In a python interpreter:

~~~
import numpy
~~~
{: .language-python}

That should work, because we have the package installed on our system.



Next, we'll create an environment an environment from scratch.

~~~
virtualenv myenv
~~~
{: .language-bash}

if python 3 isn't your default you might need to pass the version of python that you want installed:

~~~
virtualenv myenv -p python3.6
~~~
{: .language-bash}

then we can activate the environment

~~~
source myenv/bin/activate
~~~
{: .language-bash}

Now we see that the cli changes to show the environment name and we can further
test our environment with our favorite package from before.

~~~
import numpy
~~~
{: .language-python}

Now, it won't work, but we can install it and a few other favorites.

~~~
pip install
~~~
{: .language-bash}

## save an environment

~~~
pip freeze > requirements.txt
~~~
{: .language-bash}



## Deactivate an environment

When you're done with an environment, you exit it with deactivate.  Also note
that an environment only exists in the one terminal window. If you open a new
terminal, you'll be back to your default environment.  

~~~
deactivate
~~~
{: .language-bash}



> ## Exercise
> download a project, create a new environment and install from the
>  requirements file
>
> Hint: use the pip man file to find options you can pass to `pip install`
>
> > ## Solution
> > ~~~
> > pip install -r requirements.txt
> > ~~~
> > {: .language-bash}
> > {: .solution}
{: .challenge}


{% include links.md %}
