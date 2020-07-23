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
- "Update the packaged project after modifying to the code"
- "Install and update a local or GitHub-hosted package"
keypoints:
- "Packaged code is resuable within and across systems"
- "A python package consists of modules"
- "Projects can be distributed in many ways and installed with a package manager"
---

## Recall: Functions

When we develop research code we organize it into functions and classes.

These might be in notebooks or you might have put them in a `.py` file. If you've never put them in another file.


<!-- Step zero from notebook to .py; then up to pip as an intermediate step to stage up -->


FIXME: Example on writing functions to motivate packaging

What is my modular resuable code vs what is my analysis
Keep motivation as easing in  and gradually scaling up to stay inclusive


## Pip

Pip stands for FIXME is used to install packages from [Python Package Index (PyPI)](https://pypi.org/). PyPI is a repository for python package that are developed by Python Community. Pip works by fetching package from this repository and installing it locally.

We use pip at the command line. We'll start by exploring it's help manual.

~~~
pip
~~~
{:.language-bash}


when this happens we see

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

This shows the basic commands and the general options.

> ## Exercise
> 1. Install the sphinx package, we will need it later.
> 2. Choose a command and look up it's options, share and discuss with your
> neighbor, be sure to choose two different ones so that you each.
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

A module is a piece of code that serves a specific purpose. In python, a module is written in a `.py` file and the name of the file is name of the module. A module can contain classes, functions, or a combination of both. Modules can also define variables for use, for example, `numpy` defines the value of pi (`numpy.Pi`).


If the `.py` file is on the path, we can import functions from one file to another.

FIXME: example


## Python Packages

We don't have to manually add to the path every time though. Instead, we can
package our modules to be installable, and then we can import directly.  This
way of importing allows us to better allow python on the backend handle differences in paths across different user systems.  

Packages are namespaces or containers (e.g. a directory) which can contain multiple packages and modules.

Making python code a package (packaging it) requires no extra tools. We need to:

- Create a directory and give it package's name.
- Put modules in it.
- Create an `__init__.py` file in the directory
- Create a setup.py file at the top level

The `__init__.py` file tells python that the directory is supposed to be read as a package.

e.g.

Let us create a package called **Vehicles** with two modules **Land** and **Water**.

### Step 1: Creating a directory
Create a directory called **Vehicles**

~~~
mkdir package-name
~~~
{: .language-bash}

### Step 2: Adding Modules

~~~
class Land:
    def __init__(self):
        ''' Constructor for this class. '''
        # Create some vehicles
        self.members = ['Cars', 'Trucks']

    def printMembers(self):
        print('Printing members of the Land  class')
        for member in self.members:
            print('\t%s ' % member)
~~~
{: .language-python}

The class has a property named members – which is a list of some vehicles we might be interested in. It also has a method named printMembers which simply prints the list of vehicles of this class.Note: all classes defined must be capable of being imported, and won't be executed directly. this will be saved in a file called **Land.py**

Next we create another module named **Water**. Create a file named **Water.py** inside the **Vehicles** directory and add the code below:

~~~
def isWater(v):
    waterv =['ship', 'boat']
    for obj in v:
        if obj in waterv:
            print("It is a water vehicle")
        else:
            print("It is not a water vehicle")
~~~
{: .language-python}

Note the code here is a function that checks which items in a list are water vehicles.

### Step 3 Adding the init file

Finally, we create a file named `__init__.py` inside the `/Vehicles` directory and add the following code:

~~~
from Land import Land
from Water import isWater
~~~
{: .language-python}

The init file is the map that tells python what you package looks like.  It is
also what makes python know a folder is a module. An empty init file makes a
folder a module, but by adding code, we can make our package easier to use.

Now, if we launch a new python terminal, from this directory, we can import the package **Vehicles**

e.g

~~~
from Vehicles import Land, Water

v1 =Land()
v1.printMembers()

v2= ["boat", "car"]
isWater(v2)
~~~
{: .language-python}

> ## Exercise
> Add a module for air vehicles with a function that checks if an air vehicle is also a water vehicles (e.g. hovercraft)
>
{: .challenge}

Now we can import from within this folder

## SetupTools and Installing Locally

FIXME: how to setup the setup.py file

~~~
import setuptools

with open("README.md", "r") as fh:
    long_description = fh.read()

setuptools.setup(
    name="example-pkg-your-username",
    version="0.0.1",
    author="Example Author",
    author_email="author@example.com",
    description="A small example package",
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

We need to install it first.  There are many ways that `pip` can install code.  We saw before that it can install from PiPy, but it can also install from a local directory.

~~~
cd
pip install .
~~~
{; .language-bash}


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


## PiPy Submission

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
