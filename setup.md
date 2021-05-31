---
title: Setup
---

For this lesson, we can follow the video instructions below and install Python through Anaconda.
We will also be using Shell commands in addition to Python, so, if you are on a Windows machine, follow the
"Git-bash on Windows" instructions as well.


{% include python_install.html %}

## Git-bash on Windows

In order to run the Shell commands properly, it is nice to have Bash installed in our Windows system. If you have
installed Anaconda as instructed in the video above, install the `git-bash` package on your base environment by
running:
```shell
conda install git-bash -c conda-forge
```

The Git-bash package is a Conda-Forge package that bundles both Git and Bash. After installing, you need to edit the
Jupyter settings. Open the `.jupyter/jupyter_notebook_config.py` file and add the following:

```
c.NotebookApp.terminado_settings = {
    'shell_command': ['C:\\Program Files\\Git\\bin\\bash.exe']
}
```

This ensures that Shell commands from Jupyter are run on Bash rather than on the Windows Shell.

{% include links.md %}
