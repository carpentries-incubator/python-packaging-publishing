---
title: "Introduction to Data Python Data Analysis Projects"
teaching: 0
exercises: 0
questions:
- "What are common features of a project?"
- "What do I need to do to get my project shared?"
- "What will this lesson cover"
objectives:
- "Categorize pieces of code and organize them for efficient future use"
- "Identify components of a complete project"
keypoints:
- Projects have common structures
- "Packaging enables a project to be installed"
- "An environment allows different people to all have the same versions and run software more reliably"
- "Documentation is an essential component of nay complete project and should exist with the code"
---

This episode will introduce the various tools that will be taught throughout the lesson and how the components relate to one another.  This will set the foundation and motivation for the lesson.

## A Data Analysis Project

> ## Exercise
> In small groups, describe all of the steps you might go through in developing a project, how it could work, and the things you want your project to do.
> Then discuss problems you anticipate or have had.
>
> > ## Solution
> > The rest of the episode adds them
> {: .solution}
{: .challenge}

## Workflows, project stages, and common challenges

 <!-- - uploads -->
 - collaboration
 - work on multiple computers
 - promote the work
 - Make file:
 - Pipeline tools
 - backup
 -


## Data and Code

 - Different back up needs, different space requirements
 - Different sharing needs
 - Shared server examples
 - scripts, numerical experiments, plotting(that get narrative)
 - things that are project specific
 - things that are method-related might be reused
    - these can be grouped as a package for install and then imported
 - can become citable: Zenodo, get a DOI
 - Data documentation, who , where, when, why: [Mozilla has a checklist](http://mozillascience.github.io/checklist/)


## Environments

 - the set of requirements and dependencies
 - what version of different  software and packages
 - don't need to track it ourselves, the environment is like a wrapper
 - many different managers; one is conda

## Documentation

 - demonstrate and publicize what you did (beyond an academic paper)
 - help your team use your code
 - clarify your thinking to do it in real time
 - multiscale: overview, details,
 - need to write the parts in natural language; but don't need to work on the infrastructure, tools can do that for you

## Why do good practices matter?


Lots of things _can_ work and following "best" practices can take a lot of extra time.  Why should we follow them and seek them?

- Jupytercon [talk](https://docs.google.com/presentation/d/1n2RlMdmv1p25Xy5thJUhkKGvjtV-dkAIsUXP-AL4ffI/preview?slide=id.g3d168d2fd3_0_130) on issues about the problems with notebooks
  - hidden states
  - more risk for beginners
  - bad habits
  - hinder reproducibility
- automation tools are based on good practices: a little bit of good, helps fancy stuff be easy
  - sphinx autodocs
  -
- examples of finding good practices


{% include links.md %}
