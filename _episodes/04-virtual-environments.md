---
title: "Managing Virtual Environments"
teaching: 0
exercises: 0
questions:
- "How can I make sure the whole team (or lab) gets the same results?"
- "How can I simplify setup and dependencies for people to use my code or reproduce my results?"
objectives:
- "Identify an environment, dependencies, and an environment manager."
- "Install an older version of Python."
- "Use virtualenv and/or conda to create an environment per project."
- "Store a project's dependencies."
- "Install dependencies for a project."
keypoints:
- "A Python dependency is an independent package that a given project requires to be able to run."
- "An environment is a directory that contains a Python installation, plus a number of additional packages."
- "An environment manager enables one-step installing and documentation of dependencies, including versions."
- "Virtualenv is a tool to create lightweight Python virtual environments."
- "`conda` is a more advanced environment and package manager that is included with Anaconda."
---

## Major Python versions

Let's assume that you are using a certain package in your data analysis project. That package may be required to run a
very specialized algorithm or to process some file format that is specific of your study domain. However, upon trying to
install the package (with a tool such as Pip, for example), you discover some sort of error. This error may be upon the
import, or even during the installation process.

This can be a common occurrence when working on programming projects, regardless of which language is being used. In
Python, errors can come up because of __version conflicts__, that is, two or more packages require different versions
of the same __dependency__. __A dependency is an independent package that another package requires to run.__ By logic,
the base dependency of all Python packages is the Python language itself. In order to run a Python project, we need
Python to be installed. However, there are important differences between major versions of Python, specially between
versions 2 and 3. From January 2020, [Python 2 has been deprecated](https://www.python.org/doc/sunset-python-2/) in favour
of Python 3, and there is even an [official guide](https://docs.python.org/3/howto/pyporting.html) and
[package](https://docs.python.org/3/library/2to3.html) for porting code from one version to the other.

There are plenty of systems running Python 2 in the wild, specially Python 2.7. It is common to have a "system-level"
installation of the Python language in an older version. Most modern Python packages, however,
may only support Python 3, as it is the current (and recommended) version of the language. In contrast, there are also
older Python packages that only run on Python 2, and thus may not run on our system if we are currently using Python 3.

__How can we deal with that?__

## Environments and Package managers

The answer to that is using __virtual environments__. We can think of an environment like a filing cabinet inside our
computer: for each drawer, we have an installation of Python, plus a number of additional packages.

<img src="../fig/filing-cabinet.png" width="200">

Packages that are installed in an environment are restricted to that environment, and will not affect system-level
installs. Being able to isolate the installation of a specific version of Python or of a certain set of Python packages
is very important to organise our programming environment and to prevent conflicts.

Whenever we __activate__ a virtual environment, our system will start using that version of Python and packages installed
in that environment will become available. Environments can also be saved so that you can install all of the
packages and replicate the environment on a new system.

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

Before we create an environment, let's see what happens when we import one of
our favorite packages.  In a python interpreter:

~~~
import numpy
~~~
{: .language-python}

That should work, because we have the package installed on our system. If not,
use a package you know you have installed, or install numpy.



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
pip install numpy
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
