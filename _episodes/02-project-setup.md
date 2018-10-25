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

Now that we've brainstormed the parts of a project and talked a little bit about what each of them consists of.  How should we organize the code?

There isn't a specific answer, but some guiding principles.

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
> 1. FIXME
{: .challenge}

## Guiding Principles

FIXME

## Setting up a project

FIXME: tutorial steps setting up a project, discussing components


~~~
git clone
cd project-name
mkdir data
mkdir package-name
mkdir docs
~~~
{: .language-bash}


> ## Exercise
> FIXME: multiple choice questions with code excerpts, asking where they go within the project organization
>

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

### Licenses

FIXME

> ## Exercise
> Discuss and compare licenses and why you should choose
>
{: .challenge}

### Citation

FIXME

## Open Source, Advanced

Other common components are
FIXME

{% include links.md %}
