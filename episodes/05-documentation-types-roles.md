---
title: "Getting started with Documentation"
teaching: 0
exercises: 0
questions:
- "How do I tell people how to use my code and advertise my project"
objectives:
- "Identify types of documentation in a project"
- "Access different types of documentation for a given project"
keypoints:
- "Documentation tells people how to use code and provides examples"
- "Types of documentation include: literal, API,  and tutorial/example"
- "Literal Documentation lives outside the code and explains the big picture ideas of the project and how to get it ste up"
- "API documentation lives in docstrings within the code and explains how to use functions in detail"
- "Examples are scripts (or notebooks, or code excerpts) that live alongside the project and connect between the details and the common tasks."
---



## Audiences for documentation

Documentation serves many purposes and many audiences, including

 - future self
 - collaborators
 - users
 - contributors


> ## Exercise
> in small groups, brainstorm the different goals for reading documentation that different audiences might have
>
{: .chalenge}


## How is documentation used?

For a potential user, they first need to understand what your code does and how it works enough to determine if they want to use it.  They might need to know what dependencies it has, what features, limitations, etc

Next the user will need to know how to install the code and make it run. A collaborator or contributor might need different instructions than a more passive user.

Once we're using it we may have questions about details of the implementation or how the pieces work together.  We may need to know the usage for a specific function.

In any python kernel we have access to information about all objects available through the `help()` function.

~~~
help(print)
~~~
{:.language-python}

We can use this at a terminal or in a Jupyter noteook.  In a Jupyter notebook we can also access help with `?` and with <kbd>shift</kbd> + <kbd>tab</kbd>. These forms of help all use the docstring in python.  


<!-- Introducing documentation and motivation
Take an analysis, extract a piece
To a function
Doc
Then show help -->

## Literal Documentation

installation guides, README files, how to repeat analysis

Purpose: Literal documentation helps users understand what your tool does and how to get started using it.

Location: Literal documentation lives outside of the code, but best practice is to keep it close. We will see that tools to support literal documentation in your code base recommend a `docs` folder with the files in there.  These can be rendered as a book.

## API Documentation

Purpose: API documentation describes the usage (input, output, description of what it does) for each piece of your code.  This includes classes and functions

Location and Format: Doc strings in python live inside the function. We'll see more eamples of these in the next episode

~~~
def best_function_ever(a_param, another_parameter):
  """
  this is the docstring
  """
~~~
{:.language-python}


## Tutorials

Purpose: To give a thorough, runnable overview of how to accomplish something with your package, maybe reprduce experimental results, or how to get started.  

Location and Format: These go alongside the literal documentation often and are typically in a `.y`

## Examples or Cookbooks

Purpose: To give common or anticipated patterns of use for your code.

Location and Format: These are smaller excerpts of code, they typically live in a gallery type format.  


## Putting it all together

> ## Exercise
> FIXME: matching exercise sorting examples of documentation into the types and/ or matching questions/goals to a type of documentation or location
>
{: . challenge}

{% include links.md %}
