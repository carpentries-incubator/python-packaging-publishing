---
title: "Packaging Python projects"
teaching: 0
exercises: 0
questions:
- "How do I use my own functions?"
- "How can I make my functions most usable for my collaborators?"
objectives:
- "Identify the components of a python package"
- "Apply a template for packaging existing code"
- "Update the packaged project after adding to the code"
- "Install and update a local or GitHub-hosted package"
keypoints:
- "Packaged python code is resuable within and across systems"
- "A python package consists of modules"
- "Projects can be distributed in many ways and installed with a package manager"
---

## Recall: Functions

We learned how to make functions before

FIXME: Example on writing functions to motivate packaging

## Pip

Pip is used to install packages from FIXME.

## Python Packages

A module is an installable unit of code.


The file `__init__.py`

FIXME: describe structure of how a package works in python

## SetupTools

```python
#!/usr/bin/env python

# setup.py is a standard python script that calls a setup() function.
# You have to import the function from the setuptools module before you can use it.
from setuptools import setup

# Most information that you supply to the setuptools package is supplied as keyword
# arguments to the setup() function.
setup(
    name='name_of_your_package',  # This will indicate the name of the package in the Python Package Index
    version='0.1.0', # This field describes the version of your package. It should use the format described by PEP386.
    description='desc_of_package', # This is the description of your project
    long_description=..., # Optional
    url='https://github.com/link/to/this.package', # Repo link of the package
    download_url='https://pypi.python.org/pypi/link/to/download', # Download link of the package
    license='MIT',  # License type
    author='Your_name', # Your name
    author_email='email@email.com', # Your email
    maintainer='Maintainer_name',  # Name of maintainer
    maintainer_email='email.@email.com',  # maintainer's email
    # This list helps the Python Package Index to classify and filter projects by their most important attributes.
    classifiers=[
        'Development Status :: 1 - Planning',
        'Intended Audience :: Developers',
        'License :: OSI Approved :: MIT License',
        'Natural Language :: English',
        'Operating System :: OS Independent',
        'Programming Language :: Python',
        'Topic :: Scientific/Engineering :: GIS',
    ],
    # Dependencies of your package
    install_requires=[
        'dependecy1',
        'dependecy2>=0.6',
    ],
    dependency_links=[
        'git+https://github.com/link/of/dependency',
    ],
)
```

## Installing locally


FIXME

~~~
cd
pip install .
~~~
{; .language-pythons}

## Getting a Package from A Colleague

Many projects are distributed via GitHub as open source projects, we can use pip to install those as well.

Using git clone

Download and unzip their folder

Direct download?


~~~
cd project_dir
pip install .
~~~
{: language-bash}



{% include links.md %}
