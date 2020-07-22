---
title: "Setting up a Project"
teaching: 0
exercises: 0
questions:
- "How do I set up a project in practice?"
- "What organization will help support the goals of my project?"
- "What additional infrastructure will support opening my project"
objectives:
- "Create a project structure"
- "Save helper excerpts of code"
keypoints:
- "Data and code should be governed by different principles"
- "A package enables a project to be installed"
- "An environment allows different people to all have the same versions and run software more reliably"
- "Documentation is an essential component of nay complete project and should exist with the code"
---

## Project Organization

Now that we've brainstormed the parts of a project and talked a little bit about what each of them consists of.  How should we organize the code to help our future self and collaborators?

There isn't a specific answer, but there are some guiding principles.  There are also some packages that create a basic setup for you.  These are helpful for getting started sometimes, if you are building something that follows a lot of standards, but do not help you reorganize your existing ode.

We will begin in this section talking about how to start from scratch, noting that often the reality is that you have code and want to organize and sort it to be more functional.  We start from clean to give you the ideas and concepts, then we'll return to how to sort and organize code into the bins we created.  



> ## Exercise
> Let's look around on GitHub for some examples and compare and contrast them.
>
> Here are some ideas to consider:
> - [Detecting Simpson's Paradox](https://github.com/fairnessforensics/detect_simpsons_paradox)
> - [MAD-bayes](https://github.com/tbroderick/bp-means)
>
> Questions
> 1. What files and directory structures are common?
> 1. Which ones do you think you could get started with right away?
> 1. What different goals do they seem to be organized for?
{: .challenge}

So next we think about how these ideas and which of these and talk about some specific advice in each topic.


## File naming

This is the least resistence step you can take to make your code more resusable.

Three principles for (file) names
1. Machine readable
1. Human readable
1. Plays well with default ordering

<!-- Good filenaming: https://datacarpentry.org/rr-organization1/01-file-naming/ -->

## Guiding Principles

FIXME

## Setting up a project

Sometimes we get to start from scratch. So we can set up everything from the beginning.  For some types of projects there are tools that generate the base structure for you.

<!--  Shablona, Cookie cutter, tool from issue-->

You can also download a template, like [Shablona](https://github.com/uwescience/shablona)


We're going to work with something a little smaller, but similar for this workshop.
~~~
git clone
cd project-name
mkdir data
mkdir docs
mkdir experiments
mkdir package-name
touch setup.py
touch README.md
~~~
{: .language-bash}

We will also have a `.gitignore` file and some files and folders that are not included.  In general data is ignored, but scripts that download or process the data in some way, are good to keep. Results should be ignored.

> ## Exercise
>
> Label each of the following files for where it goes in the project
>
> ~~~
> raw_data.csv
> generate_figures.py
> new_technique.py
> reproduce_paper.py
> helper_functions.py
> how_to_setup.md
> ~~~
> {: .language-bash}
>
>
> Label each of the following excerpts for where it goes in the project
>
> `excerpt 1`
> ~~~
> Getting Started
> ----------------
>
> to install
>
> ~~~
> {: .language-bash}
>
> `excerpt 2`
> ~~~
> for data_file in file_list:
>   proc_data = pkg.preprocess(data_file)
>   proc_data.to_csv(data_file[:-3] + '_proc.csv')
>   pkg.new_method(proc_data)
> ~~~
> {: .language-python}
>
> `excerpt 3`
> ~~~
> df = pd.read_csv(data_file)
> df.head()
> df.describe()
> ~~~
> {: .language-python}
>
> `excerpt 4`
> ~~~
> This technique involves the best new analysis technique ever
> the background to understand the technique is these three things
> ~~~
> {: .language-bash}
{: .challenge}



## Open Source Basics, MWE

Open source guidelines are generally written to be ready to scale.  Here we propose the basics to get your project live and usable vs things that will help if it grows and builds a community, but n

### README

> ## Exercise
> read 2 README files and discuss with a group
>  - what are common sections?
>  - what is the purpose?
>  - what
{: .challenge}

A readme is the first information about your project most people will see. It should encourage people to start using it and cover key steps in that process. It includes key information, such as:
* What the project does
* Why the project is useful
* How users can get started with the project
* Where users can get help with the project
* Who maintains and contributes to the project
* how to repeat the analysis

### Licenses

Let's take a look at a helpful tool for choosing a [license](https://choosealicense.com/)

> ## Exercise
> Discuss and compare licenses and why you should choose
>
{: .challenge}

<!-- ### Citation

FIXME -->

## Open Source, Advanced

Other common components are
- code of conduct
- contributing guidelines
- citation

Even more advanced for building a community
- issue templates
- pull request templates
- pathways and personas

For training and mentoring see [Mozilla Open Leaders](https://foundation.mozilla.org/en/opportunity/mozilla-open-leaders/).  For reading, check out the [curriculum](https://mozilla.github.io/open-leadership-training-series/).

## Re-organizing a project

<!-- Frame intro into organizing existing stuff
Clean up and organize content: where to different pieces of code go -->

> ## Exercise
> FIXME: provide a dummy project folder, spend time sorting, or allow people some time to work on their own projects and generating questions.
>



{% include links.md %}
