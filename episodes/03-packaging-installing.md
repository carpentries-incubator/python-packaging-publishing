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
- "Update the packaged project after modifying to the code"
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

A module is a piece of code that serves a paticular functionalty. In python module end with a **.py** extension and the name of the module is the name of the file. A module can contain classes, functions or a combination of both.

Packages are namespaces or containers (e.g. a directory) which contain multiple packages and modules.

Working with Python packages and modules is easy to learn. We need to:

* Create a directory and give it package's name.
* Put modules in it.
* Create a __init__.py file in the directory

The __init__.py file tells python that the directory is supposed to be read as a package.

e.g.

Let us create a package called **Vehicles** with two modules **Land** and **Water**.

### Step 1: Creating a directory
Create a directory called **Vehicles**

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

Finally, we create a file named __init__.py inside the **Vehicles** directory and add the following code:
~~~
from Land import Land
from Water import isWater
~~~
{: .language-python}

Now we can import the package **Vehicles**

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
