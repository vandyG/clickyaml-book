Environment Setup
=================

Overview
--------

Since this is a book I'll be covering every single step that went into or was related to this project.
This chapter will cover the steps to set up a development environment. This project was developed on 
Windows Subsystem for Linux - Ubuntu so all the steps will correspond to that. 

Here is a list of tools that were used while working on this project:

================    ======================
Operating System    |Win| + |Ubu|
Code Editor         |Vscode|
Package Manager     |Conda|
Version Control     |Git| + |Github|
Documentation       |Rtd| + |Sphinx|
Publishing          |Pypi|
Testing             |Pytest| + |Gaction|
================    ======================

Setting up conda
----------------

I choose to use **conda** instead of **venv** because it is easier to maintain the environments.
I am usually working on multiple projects and each has it's separate environment. With a simple
`conda env list` I can list all the environments.

This is different from dependency management as some packages that I need for development might 
not be required while packaging. For dependency management I am using the ``setuptools`` with ``setup.py``.
More on that later.

:Example:

   ``pytest`` is required during testing and development but it's not a dependency for the package.
   The user need not have pytest to install the package and use it.

Downloading conda installer
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: shell

    wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh


You can also download it manually from the same link.

.. _install-conda:

Run the installer
^^^^^^^^^^^^^^^^^

.. code-block:: shell

    bash Miniconda3-latest-Linux-x86_64.sh

And follow the prompts.

.. seealso::

   `Installing conda on linux <https://conda.io/projects/conda/en/latest/user-guide/install/linux.html>`_


Create project using ``cookiecutter``
-------------------------------------

Cookiecutter creates projects from predefined templates. These templates include a defined directory structure,
setup for setuptools, Makefile, README and more. For this project I am using `audreyfeldroy/cookiecutter-pypackage <https://github.com/audreyfeldroy/cookiecutter-pypackage>`_
template.

Install Cookiecutter in the base conda environment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

As I use cookiecutter templates quite often I have it installed in the base environment.

.. code-block:: shell

   conda install -c conda-forge cookiecutter

Create a project from the template
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Once you have cookiecutter installed, run the following command 

.. code-block:: shell

   cookiecutter https://github.com/audreyfeldroy/cookiecutter-pypackage.git

After running this command you'll be presented with a series of prompts, answer them as per your requirements.
Here is an example:

.. code-block:: shell

   full_name [Audrey Roy Greenfeld]: HAL 9000
   email [audreyr@example.com]: hal9000@discovery.one
   github_username [audreyr]: hal9000
   project_name [Python Boilerplate]: open_pod_bay_doors
   project_slug [open_pod_bay_doors]: open_pod_bay_doors
   project_short_description [Python Boilerplate contains all the boilerplate you need to create a Python package.]: I am afraid I cant do that
   pypi_username [hal9000]: hal9000
   version [0.1.0]: 
   use_pytest [n]: y                         # sets up project to be used with pytest, for unit testing.
   use_black [n]: y                          # for code formatting
   use_pypi_deployment_with_travis [y]: n    # I will be using GitHub actions for deployment.
   add_pyup_badge [n]: n                     # adds a badge in readme file
   Select command_line_interface:
   1 - Click
   2 - Argparse
   3 - No command-line interface
   Choose from 1, 2, 3 [1]: 3                # no command line interface required
   create_author_file [y]: 
   Select open_source_license:
   1 - MIT license
   2 - BSD license
   3 - ISC license
   4 - Apache Software License 2.0
   5 - GNU General Public License v3
   6 - Not open source
   Choose from 1, 2, 3, 4, 5, 6 [1]: 1       # keep it simple choose MIT

This creates a python project with the following directory structure.

.. code-block:: shell

   open_pod_bay_doors
   ├── AUTHORS.rst
   ├── CONTRIBUTING.rst
   ├── HISTORY.rst
   ├── LICENSE
   ├── MANIFEST.in
   ├── Makefile
   ├── README.rst
   ├── docs
   │   ├── Makefile
   │   ├── authors.rst
   │   ├── conf.py
   │   ├── contributing.rst
   │   ├── history.rst
   │   ├── index.rst
   │   ├── installation.rst
   │   ├── make.bat
   │   ├── readme.rst
   │   └── usage.rst
   ├── open_pod_bay_doors
   │   ├── __init__.py
   │   └── open_pod_bay_doors.py
   ├── requirements_dev.txt
   ├── setup.cfg
   ├── setup.py
   ├── tests
   │   ├── __init__.py
   │   └── test_open_pod_bay_doors.py
   └── tox.ini

.. warning::

   setup.cfg is improperly configured and throws the following warning
   when running pytest:

   `PytestConfigWarning: Unknown config option: collect_ignore`

   The following changes to the file are suggested ( - remove, + add)

   .. code-block::

      - collect_ignore = ['setup.py']
      + addopts = --ignore=setup.py
   
      
   Replacing with `addopts` fixes the issue. See `issue <https://github.com/audreyfeldroy/cookiecutter-pypackage/issues/608>`_

Files and directories
"""""""""""""""""""""

1. **AUTHORS.rst**: This file contains information regarding the maintainers and contributors of the project.
2. **CONTRIBUTING.rst**: This file contains information on how to contribute to the project.
3. **HISTORY.rst**: This file contains the version history information of the project.
4. **LICENSE**: License associated with the project.
5. **MANIFEST.in**: Specify files you want to add or remove in the source distribution.
6. **Makefile**: Used to automate different parts of development. More on Makefile later.
7. **Readme.rst**: File that introduces and explains the project. More on Readme file later.
8. **docs**: Source directory for Sphinx project. Contains the source and build files for the Documentation. More on Documentation later.
9. **open_pod_bay_doors** (main package): Contains all the source code.
10. **requirements_dev.txt**: Lists all the modules/packages required for development.
11. **setup.cfg**: Configuration file for various tools
12. **setup.py**: Contains information necessary for building and installing the package.
13. **tests**: Contains modules for testing the code. More on testing later.
14. **tox.ini**: Configuration file for tox. `This file can be removed. I am not using tox for testing`

.. #TODO: Git setup
.. #TODO: Gh setup
.. #TODO: Github repo setup
.. #TODO: Describe makefile
.. #TODO: Explain rst format
.. #TODO: write readme file
.. #TODO: how to write documentation
.. #TODO: how to do testing. github actions pytest


.. |Win| image:: data/win.svg
   :width: 7%
   :alt: Windows
   :target: https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-10

.. |Ubu| image:: data/ubu.svg
   :width: 7%
   :alt: WSL-Ubuntu
   :target: https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-10

.. |Vscode| image:: data/vscode.png
   :width: 7%
   :alt: Visual Studio Code
   :target: https://code.visualstudio.com/download

.. |Conda| image:: data/conda.png
   :width: 7%
   :alt: Conda
   :target: https://conda.io/projects/conda/en/latest/user-guide/install/index.html

.. |Git| image:: data/git.png
   :width: 7%
   :alt: Git
   :target: https://git-scm.com/download/linux

.. |Github| image:: data/github.png
   :width: 7%
   :alt: GitHub
   :target: https://github.com/

.. |Rtd| image:: data/rtd.png
   :width: 7%
   :alt: Read The Docs
   :target: https://docs.readthedocs.io/en/stable/tutorial/index.html

.. |Sphinx| image:: data/sphinx.png
   :width: 7%
   :alt: Sphinx
   :target: https://www.sphinx-doc.org/en/master/

.. |Pypi| image:: data/pypi.png
   :width: 7%
   :alt: PyPi
   :target: https://pypi.org/

.. |Pytest| image:: data/pytest.png
   :width: 7%
   :alt: PyTest
   :target: https://docs.pytest.org/en/7.2.x/

.. |Gaction| image:: data/gaction.png
   :width: 7%
   :alt: Github Actions
   :target: https://github.com/features/actions