Installing Requirements
=======================

Now the next step is to install the packages required for development. These packages may or may not be a 
dependency for our package. These requirements are used to define the complete python environment to 
facilitate the development of the project.

Although the requirements can be installed manually by ``conda install`` or ``pip install`` it is good
practice to create an environment.yml or requirements.txt file to maintain a list of required packages.
These can be helpful if you need to clone your environment setup or if another developer wants to
contribute to the project.

The user does not require unit testing packages (like ``pytest``) or packages used to create documentation 
(like ``sphinx``) are not to run or use clickYaml. Rather developers and contributors need these packages 
to get started and contribute to the project. Hence these requirements are usually found in a file present 
in the project root called as ``requirements.txt``. For conda based projects ``environment.yaml`` file is 
preferred. This was one of the many learnings I had while working on this project. clickYaml uses 
``requirements.txt`` file even though I was using a conda environment. ``requirements.txt`` file should be 
used if you are using pip + venv. Although pip and conda are not interoperable but it is acceptable to 
``pip install`` packages but it is recommended to install using conda as it keeps the environment more 
portable.

requirements.txt
----------------

In ``clickYaml`` the requirements file is defined as ``requirements_dev.txt``. It lists all the dependencies required to
develop, test and deploy the package.

.. code-block:: text
    :caption: requirements_dev.txt
    :name: requirements

    pip>=21.1
    bump2version>=0.5.11
    wheel>=0.38.1
    watchdog>=0.9.0
    flake8>=3.7.8
    tox>=3.14.0
    coverage>=4.5.4
    Sphinx>=1.8.5
    twine>=1.14.0
    Click>=7.1.2
    pytest>=6.2.4
    black>=21.7b0
    pyyaml
    sphinx-rtd-theme

Setting up conda environment
----------------------------

Before we begin installing the requirements we need to set up a python environment. In the
previous section (:ref:`install-conda`) we had only installed conda and by default the ``base``
environment is activated. What we would want to do is create a separate environment for our 
project as we do not want to affect the base environment. Another reason to have a separate
environment is so that we can install specific versions of the required packages.

In order to create a separate environment, enter the following command:

.. code-block:: shell

    conda create --name clickyaml python=3.7

This will create a conda environment with python 3.7 and all the other dependencies required with 
python including pip.

Activate the environment.

.. code-block:: shell

    conda activate clickyaml

Install Requirements
--------------------

Now that we have a python environment we are ready to install the requirements as well.
Run the following command to install the requirements:

.. code-block:: shell

    pip install -r requirements_dev.txt

.. #TODO: Dependency management. Dependencies are all the software component that are required by our project/package to work. Without these 
.. dependencies the package might not work as intended. For example ``clickYaml`` creates ``Click`` commands 
.. out of the entries mentioned in a ``yaml`` file. In order for a user to use the clickYaml package he must 
.. have Click as well as pyyaml installed in his python environment. Now the user might not be aware of this
.. as a consequence of which the user is likely to run into runtime errors when using clickYaml. 

