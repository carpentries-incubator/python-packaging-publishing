---
title: "Packaging Python Projects"
teaching: 0
exercises: 0
questions:
- "How do I use my own functions?"
- "How can I make my functions most usable for my collaborators?"
objectives:
- "Identify the components of a python package"
- "Apply a template for packaging existing code"
- "Update the packaged project after modifying the code"
- "Install and update a local or GitHub-hosted package"
keypoints:
- "Packaged code is reusable within and across systems"
- "A python package consists of modules"
- "Projects can be distributed in many ways and installed with a package manager"
---

## Recall: Functions

When we develop code for research, we often start by writing unorganized code in notebook cells or a script. 
Eventually, we might want to re-use the code we wrote in other contexts. In order to re-use code, it is 
helpful to organize it into functions and classes in separate `.py` files.

<!-- Step zero from notebook to .py; then up to pip as an intermediate step to stage up -->

e.g. a function to convert from degrees Fahrenheit to Celsius

~~~
def fahr_to_celsius(temp):
    return ((temp - 32) * (5/9))

~~~
{: .language-python}

<!-- What is my modular resuable code vs what is my analysis
Keep motivation as easing in  and gradually scaling up to stay inclusive -->


## Pip

Pip is the most common package manager for python. Pip allows you to easily install python packages locally from your computer or from an online repository like the [Python Package Index (PyPI)](https://pypi.org/). Once a package is installed with pip, you can `import` that package and use it in your own code.

Pip is a command line tool. We'll start by exploring its help manual:

~~~
pip
~~~
{:.language-bash}

The output will look like this
~~~
Usage:   
  pip <command> [options]

Commands:
  install                     Install packages.
  download                    Download packages.
  uninstall                   Uninstall packages.
  freeze                      Output installed packages in requirements format.
  list                        List installed packages.
  show                        Show information about installed packages.
  check                       Verify installed packages have compatible dependencies.
  config                      Manage local and global configuration.
  search                      Search PyPI for packages.
  wheel                       Build wheels from your requirements.
  hash                        Compute hashes of package archives.
  completion                  A helper command used for command completion.
  help                        Show help for commands.

General Options:
  -h, --help                  Show help.
  --isolated                  Run pip in an isolated mode, ignoring
                              environment variables and user configuration.
  -v, --verbose               Give more output. Option is additive, and can be
                              used up to 3 times.
  -V, --version               Show version and exit.
  -q, --quiet                 Give less output. Option is additive, and can be
                              used up to 3 times (corresponding to WARNING,
                              ERROR, and CRITICAL logging levels).
  --log <path>                Path to a verbose appending log.
  --proxy <proxy>             Specify a proxy in the form
                              [user:passwd@]proxy.server:port.
  --retries <retries>         Maximum number of retries each connection should
                              attempt (default 5 times).
  --timeout <sec>             Set the socket timeout (default 15 seconds).
  --exists-action <action>    Default action when a path already exists:
                              (s)witch, (i)gnore, (w)ipe, (b)ackup, (a)bort).
  --trusted-host <hostname>   Mark this host as trusted, even though it does
                              not have valid or any HTTPS.
  --cert <path>               Path to alternate CA bundle.
  --client-cert <path>        Path to SSL client certificate, a single file
                              containing the private key and the certificate
                              in PEM format.
  --cache-dir <dir>           Store the cache data in <dir>.
  --no-cache-dir              Disable the cache.
  --disable-pip-version-check
                              Don't periodically check PyPI to determine
                              whether a new version of pip is available for
                              download. Implied with --no-index.
  --no-color                  Suppress colored output
~~~
{: .output}

This shows the basic commands available with pip and and the general options.

> ## Exercise
> 1. Use pip to install the `sphinx` package, we will need it later.
> 2. Choose a pip command and look up its options. Discuss the command with your
> neighbour.
>
> > ## Solution
> >
> > ~~~
> > pip install sphinx
> > ~~~
> > {: .language-bash}
> {: .solution}
{: .challenge}

## Python Modules

A module is a piece of code that serves a specific purpose. In python, a module is written in a `.py` file. The name of the file is name of the module. A module can contain classes, functions, or a combination of both. Modules can also define variables for use, for example, [numpy](https://numpy.org/) defines the value of pi with `numpy.pi`.


If a `.py` file is on the path, we can import functions from it to our current file. Open up Python, import `sys` and print the path.

~~~
import sys
sys.path
~~~
{:.language-python}

~~~
['',
'/home/vlad/anaconda3/lib/python37.zip',
'/home/vlad/anaconda3/lib/python3.7',
'/home/vlad/anaconda3/lib/python3.7/lib-dynload',
'/home/vlad/anaconda3/lib/python3.7/site-packages'
]
~~~
{: .output}

Here we see that Python is aware of the path to the Python executable, as well as other directories like `site-packages`.

sys.path is a list of strings, each describing the absolute path to a directory. Python will look in these directories for modules. If we have a directory containing modules we want Python to be aware of, we append it that directory to the path. If I have a package in `/home/vlad/Documents/science/cool-package` I add it with `sys.path.append`


~~~
sys.path.append('/home/vlad/Documents/science/cool-package')
sys.path
~~~
{:.language-python}

~~~
['',
'/home/vlad/anaconda3/lib/python37.zip',
'/home/vlad/anaconda3/lib/python3.7',
'/home/vlad/anaconda3/lib/python3.7/lib-dynload',
'/home/vlad/anaconda3/lib/python3.7/site-packages',
'/home/vlad/Documents/science/cool-package'
]
~~~
{: .output}

We can see that the path to our module has been added to `sys.path`. Once the module you want is in sys.path, it can be imported just like any other module.

## Python Packages

To save adding modules to the path every time we want to use them, we can
package our modules to be installable.  This
method of importing standardises how we import modules across different user systems. This is why when we import packages like `pandas` and `matplotlib` we don't have to write out their path, or add it to the path 
before importing.  When we install a package, its location gets added to the path, or it's saved to a location
already on the path. 

Many packages contain multiple modules. When we `import matplotlib.pyplot as plt` we are importing only the pyplot 
module, not the entire matplotlib package. This use of `package.module` is a practice referred to as a **namespace**. 
Python namespaces help to keep modules and functions with the same name separate. For instance, both scipy and numpy have a `rand`function to create arrays of random numbers. We can differentiate them in our code by using `scipy.sparse.rand` 
and `numpy.random.rand`. respectively

In this way, namespaces allow multiple packages to have functions of the same name without creating conflicts. Packages are namespaces or containers which can contain multiple modules.

Making python code into a package requires no extra tools. We need to

- Create a directory, named after our package.
- Put modules (`.py` files) in the directory.
- Create an `__init__.py` file in the directory
- Create a `setup.py` file alongside the directory

Our final package will look like this:

├── package-name  
│   ├── \_\_init__.py  
│   ├── module-a.py  
│   └── module-b.py  
└── setup.py

The `__init__.py` file tells python that the directory is supposed to be tread as a package.

Let's create a package called **conversions** with two modules **temp** and **speed**.

### Step 1: Creating a directory
Create a directory called **conversions**

~~~
mkdir conversions
~~~
{: .language-bash}

### Step 2: Adding Modules

conversions/temp.py
~~~
def fahr_to_celsius(temp):
    return ((temp - 32) * (5/9))
~~~
{: .language-python}

the file temp.py will be treated as a module called temp. This module contains the function `fahr_to_celsius`. The top level container is the package `conversions`. The end user will import this as:
`from conversions.temp import fahr_to_celsius` 


> ## Exercise
> 1. Create a file named **speed.py** inside the **conversions** directory and add a function named `kph_to_ms` that will convert kilometres per hour to meters per second:
>
> > ## Solution
> > conversions/speed.py
> > ~~~
> > def kph_to_ms(speed):
> >     return speed / 3.6
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}


### Step 3 Adding the init file

Finally, we create a file named `__init__.py` inside the `conversions` directory and add the following code:

~~~
import temp
import speed
~~~
{: .language-python}

The init file is the map that tells Python what our package looks like.  It is
also what tells Python a directory is a module. An empty init file marks a
directory as a module. By adding import code, we can make our package easier to use.

Now, if we launch a new python terminal from this directory, we can import the package **conversions**

e.g

~~~
from conversions import temp, speed

print(temp.fahr_to_celsius(100))
~~~
{: .language-python}

Now we can import from within this folder, but only if our working directory is at the top level `conversions` 
directory. What if we want to use the **conversions** package from another project or directory?

## SetupTools and installing Locally

The file **setup.py** contains the essential information about our package for PyPI. It needs to be machine readable, so be sure to format it correctly
~~~
import setuptools

with open("README.md", "r") as fh:
    long_description = fh.read()

setuptools.setup(
    name="conversions",
    version="0.0.1",
    author="Example Author",
    author_email="author@example.com",
    description="An example  package to perform unit conversions",
    long_description=long_description,
    long_description_content_type="text/markdown",
    url="https://github.com/pypa/sampleproject",
    packages=setuptools.find_packages(),
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
)
~~~
{: .language-python}


Now that our code is organized into a package and has setup instructions, how can we use it? If we try importing it now, what happens?

We need to install it first. Earlier, we saw that pip can install packages remotely from PyPI. pip can also install 
from a local directory.

~~~
cd conversions
pip install -e .
~~~
{: .language-bash}
The `-e` flag (aka `--editable`) tells pip to install this package in editable mode. This allows us to make 
changes to the package without re-installing it. Analysis code can change dramatically over time, so this is a 
useful option!

Now we can try importing and using our package.

## Command Line Tools

FIXME: how to make a tool command line installable

More details on this may be found at [on the python packaging documentation site](https://python-packaging.readthedocs.io/en/latest/command-line-scripts.html)

## Getting a Package from A Colleague

Many projects are distributed via GitHub as open source projects, we can use pip to install those as well.

Using git clone

Download and unzip their folder

Direct download via pip


~~~
cd project_dir
pip install .
~~~
{: language-bash}


## PyPI Submission

To make `pip install packagename` work you have to submit your package to the repository.  We won't do that today, but an important thing to think about if you might want to go this direction, is that the name must be unique.  This mens that i's helpful to check pipy before creating your package so that you chooses a name that is availalbe.

To do this, you also need to package it up somewhat more. There are two types of archives that it looks for, as 'compiled' versions of your code. One is a source archive (`tar.gz`) and the other is a built distribution (`.whl`).  The built version will be used most often, but the source archive is a backup and makes your package more broadly compatible.

The next step is to generate distribution packages for the package. These are archives that are uploaded to the Package Index and can be installed by pip.

Make sure you have the latest versions of setuptools and wheel installed:

~~~
python3 -m pip install --user --upgrade setuptools wheel
~~~
{: .language-bash}

~~~
python3 setup.py sdist bdist_wheel
~~~
{: language-bash}
This command should output a lot of text and once completed should generate two files in the dist directory:

~~~
dist/
  example_pkg_your_username-0.0.1-py3-none-any.whl
  example_pkg_your_username-0.0.1.tar.gz
~~~
{: language-bash}

Finally, it’s time to upload your package to the Python Package Index!

First, we'll register for accounts on Test PyPI, intended for testing and experimentation. This way, we can practice all of the steps, without publishing our sample code that we've been working with.

Go to [test.pypi.org/account/register/](https://test.pypi.org/account/register/) and complete the steps on that page, then verify your account.

Now that you are registered, you can use twine to upload the distribution packages. You’ll need to install Twine:

~~~
python3 -m pip install --user --upgrade twine
~~~
{: .language-bash}
Once installed, run Twine to upload all of the archives under dist:

~~~
python3 -m twine upload --repository-url https://test.pypi.org/legacy/ dist/*
~~~
{: .language-bash}

You will be prompted for the username and password you registered with Test PyPI. After the command completes, you should see output similar to this:

~~~
Uploading distributions to https://test.pypi.org/legacy/
Enter your username: [your username]
Enter your password:
Uploading example_pkg_your_username-0.0.1-py3-none-any.whl
100%|█████████████████████| 4.65k/4.65k [00:01<00:00, 2.88kB/s]
Uploading example_pkg_your_username-0.0.1.tar.gz
100%|█████████████████████| 4.25k/4.25k [00:01<00:00, 3.05kB/s]
~~~
{: .language-bash}
Once uploaded your package should be viewable on TestPyPI, for example, https://test.pypi.org/project/example-pkg-your-username

test by having your neighbor install your package.

Since they're not actually a packaged with functionality, we should uninstall once we're done with `pip uninstall`

{% include links.md %}
