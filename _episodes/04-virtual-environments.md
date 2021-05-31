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

## Virtual environments

The answer to that is using __virtual environments__. We can think of an environment like a filing cabinet inside our
computer: for each drawer, we have an installation of Python, plus a number of additional packages.

<img src="../fig/filing-cabinet.png" width="200">

Packages that are installed in an environment are restricted to that environment, and will not affect system-level
installs. Being able to isolate the installation of a specific version of Python or of a certain set of Python packages
is very important to organise our programming environment and to prevent conflicts.

Whenever we __activate__ a virtual environment, our system will start using that version of Python and packages installed
in that environment will become available. Environments can also be saved so that you can install all of the
packages and replicate the environment on a new system.

> ## Why use virtual environments?
> When we are unfamiliar with virtual environments, they may seem like an unnecessary hurdle. If the code runs on
> our current environment, why bother with the extra work of creating or using a different one? There are many reasons
> to use a virtual environment:
> 
>  - to prevent conflicts with system-level installations;
>  - to ensure consistency in the code that we deliver, _i.e.:_ keep it compatible with the same versions;
>  - to install our code in different environments, such as a server or cloud platform;
>  - to be able to share our environment with others (and prevent "works on my machine" errors).
> 
> Having isolated environments for each project greatly improves the organisation of our development environment. If 
> something goes wrong in an environment (for example, the installation of a package breaks, or there is a version
> conflict between distinct dependencies), we can simply delete that environment and recreate it. The rest of our system
> is not affected or compromised. This can be **critical** in multi-user environments.
> 
> Overall, we only need to learn the basics about virtual environments to be able to use them effectively. So, there is
> great benefit with relatively low effort.
{: .callout}

We can use the command-line to see which Python version is currently being used. This is the Python version that
is used to execute any scripts or Python files that we run from the command-line. There are many ways to do that, but
a simple one is to run:

```bash
which python
```

on Mac or LINUX, or:

```shell
where python
```

In Windows machines. The `which` and `where` commands point to the __Python executable__ that is currently active.
If we are using a virtual environment, that file will be inside our environment directory. If we see something like
`/usr/bin/python`, it is likely that we are using a system-level version of Python. If you are using an Anaconda
distribution of Python, it is likely that you will see `<path to your anaconda install>/bin/python`.

**Note: these commands can also be used to locate other executables.**

> ## Dependencies
> We've seen that dependencies are independent packages that are required for another package to run. Think of a
> particular package, either one that you want to create or one that you often use:
>   - what dependencies does it have?
>   - why is it important to keep track of these dependencies?
>   - what may happen if a dependency goes through a major version update?
> 
> > ## Solution
> >  - All Python packages obviously have the Python language as a dependency. For data analysis and scientific Python
> > projects, a very common dependency is the [NumPy](https://numpy.org/) package, that provides the basis for numerical
> > computing in Python, and additionally other common libraries of the scientific Python stack, such as
> > [Pandas](https://pandas.pydata.org/) and [Matplotlib](https://matplotlib.org/).
> >  - Keeping track of dependencies matters because our project depends on them to run correctly. If we are trying
> > use a function or method from a dependency that behaves differently in different versions, we may get unexpected
> > results.
> >  - If a dependency goes through a major version update, such as Python 2 to Python 3, there may be breaking changes
> > in downstream packages. If this happens for our package, we should test the package accordingly to see if everything
> > works as expected. Testing software is a vast topic and we can leave it for now, but it is important to have that in
> > mind when working with dependencies.
> {: .solution} 
{: .challenge}

## Environment and package managers

There are different strategies to deal with Python environments. We are going to focus on two of them: `virtualenv` and `conda`.

- `virtualenv` is a tool to create isolated Python environments. It is so widespread that a subset of it has been integrated
into the Python standard library under the [venv module.](https://docs.python.org/3/library/venv.html) `virtualenv` uses
`pip`, that we've discussed previously, to install and manage packages inside an environment. Therefore, `virtualenv` is
an __environment manager__ that is compatible with `pip`, a __package manager__. 

- `conda` is a tool from the [Anaconda distribution](http://anaconda.org/) that is both an environment and package manager.
Packages can be installed in Conda environments using both `pip` and `conda`. There are a fews advantages of using `conda`
for installations, such as support for third-party packages (that aren't available on PyPI) and automatic dependency solving.
This comes at the disadvantage of being heavier and usually slower than `virtualenv`.
  
Because we are already familiar with `pip`, we can start off by using `virtualenv` to learn how environments work in
practice. We'll have a look at Conda environments later on.

> ## Installing `virtualenv`
> If you do not have `virtualenv` installed, you can quickly install it with `pip`:
> ```bash
> pip install virtualenv
> ```
{: .callout}

## Create an environment

Before we create an environment, let's see what happens when we import one of
our favorite packages. In a Python interpreter:

```python
import numpy
```

That should work, because we have the package installed on our system. If not,
use a package you know you have installed, or install NumPy.

Next, we'll create an environment named `myenv`:

```bash
virtualenv myenv -p python3
```

We could simply run `virtualenv myenv`, but the `-p python3` flag ensures that we create it with Python 3.

You will notice that a `myenv/` folder has been created in the working directory. We can then activate
our environment by running:

```bash
source myenv/bin/activate
```

Now we see that the CLI changes to show the environment name! We can also run the
`where` or `which` command again to see that our Python executable has been changed.

```bash
which python  # or 'where python' for Windows.
```

The output should look something like `<working directory>/myenv/bin/python`.

Let's start another Python interpreter (simply type `python`) and try to import NumPy again:

```python
import numpy
```

It does not work! This is expected, because we have just created this environment from scratch. It only contains the
base Python installation. To install NumPy in this environment, we must use `pip`:

```bash
pip install numpy
```

If we open a new Python interpreter, NumPy can now be imported.

## Listing packages and the requirements file.

We can check which packages are installed in our current environment using the `pip freeze` command. If we
wish to save that list in a file for later use, we can use a UNIX redirect statement (`>`). More on those on the
[SWC Shell Novice lesson](https://swcarpentry.github.io/shell-novice/04-pipefilter/index.html).

```bash
pip freeze > requirements.txt
```

This saves the list of packages and respective versions in the `requirements.txt` file. Requirement files are very
common in Python projects, as they are a simple way of specifying the project's dependencies.

## Deactivate an environment

When you're done with an environment, you can exit with the `deactivate` command.

```bash
deactivate
```

> ## Default environment
> Note that an environment is only activated in the current Terminal window. If you open a new
> Terminal, you'll be back to your default environment. This could be, for example, the `base` environment if you have
> Anaconda installed, or your system's default Python environment.
{: .callout}

> ## Exercise
> download a project, create a new environment and install from the
>  requirements file
>
> Hint: use the pip man file to find options you can pass to `pip install`
>
> > ## Solution
> > ```bash
> > pip install -r requirements.txt
> > ```
> > {: .solution}
{: .challenge}


{% include links.md %}
