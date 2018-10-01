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

FIXME: how to setup the setup.py file

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
