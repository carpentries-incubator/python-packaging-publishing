---
title: "Building Documentation with Sphinx"
teaching: 0
exercises: 0
questions:
- "How can I make my documentation more accessible"
objectives:
- "Build a documentation website with sphinx"
- "Add overview documentation"
- "Distribute a sphinx documentation site"
keypoints:
- "Building documentation into a website is a common way of distributing it"
- "Sphinx will auto build a website from plain text files and your docstrings"
---

[Sphinx](https://www.sphinx-doc.org/en/master/) is a tool for building documentation. It is
very popular for Python packages, because it was originally created for the Python documentation, but
it currently supports a range of languages.

## What does Sphinx produce?

Sphinx renders the package source code, including docstrings, as formatted
HTML pages and a few other formats, like PDF, ePUB, and plain text. This is incredibly
useful because it saves a lot of effort in creating the documentation.

> ## What do good docs have in common?
> In a group, have each member open one of the following projects' documentation:
> - [Pytest](https://docs.pytest.org/en/latest/)
> - [Seaborn](https://seaborn.pydata.org/)
> - [NumPy](https://docs.scipy.org/doc/numpy/reference/)
> - [SciPy](https://docs.scipy.org/doc/scipy/reference/)
>  - [SciPy-cookbook](https://scipy-cookbook.readthedocs.io/)
> - [Scikit-learn](http://scikit-learn.org/stable/)
>
> Discuss what the common components are, what is helpful about these
> documentation sites, how they address the general concepts on documentation,
> how they're similar and how they're different.
>
> > ## Solution
> > All of these projects use Sphinx to generate their documentation, albeit with different themes. All of them also
> > have the following items (except for SciPy-cookbook), which itself is complementary documentation
> > for the SciPy package.:
> >  - User guide;
> >  - Tutorials;
> >  - an API reference.
> {: .solution}
{: .challenge}

## Sphinx quickstart

Install Sphinx if you haven't done so already:

~~~
pip install sphinx
~~~
{: .language-bash}

Move into the directory that is to store your documentation: 

~~~
cd docs
~~~
{: .language-bash}

Start the interactive Sphinx quickstart wizard, which creates a Sphinx config file, `conf.py`, using your preferences.

~~~
sphinx-quickstart
~~~
{: .language-bash}

Suggested responses to the wizard's questions:

* *Separate source and build directories?* -> yes
* *Project name* -> sensible to re-use the package name
* *Author name(s)* -> list of authors
* *Project release* -> sensible to re-use the package version specified in `setup.py` (see lesson 3) e.g. '0.1'
* Project language -> `en`, but you may want to target other languages as well/instead. 

This will create:

* `docs/source/conf.py` -> Sphinx configuration file
* `docs/source/index.rst` -> Sphinx main index page, which like almost all Sphinx content, is written in reStructured Text (like Markdown)
* `docs/Makefile` -> for performing various tasks on Linux/macOS e.g. building HTML or a PDF
* `docs/make.bat` -> for performing those tasks on Windows

You should now be able to build and serve this basic documentation site using:

~~~
make html
python3 -m http.server -d build/html
~~~
{: .language-bash}

When you browse to the URL shown in the output of the second command
you can see your HTML documentation site but it's looking fairly bare!
Let's learn a little more about reStructuredText then start adding some content to our documentation site.

## Adding literal documentation

FIXME: RST overview

FIXME: adding pages

## API Documentation

Add an api line to the `index.rst` so that it has a link to it.

The create an API.rst file:

~~~
API documentation
==================


~~~
{: .language-bash}

{% include links.md %}
