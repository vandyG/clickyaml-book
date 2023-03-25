Setting up the book
===================

This step includes setting up the development environment and directory structure.
For setting up the environment I used `conda`_ and the book is created using `jupyter-book`_
package.

Setting up the project Directory
--------------------------------
Run the following command in the terminal and answer the prompts.

.. code-block:: shell

    jupyter-book create mynewbook/ --cookiecutter

.. seealso::

    This step requires `jupyter-book`_ and `cookiecutter`_ packages.
    For more information and installation instructions refer to the  
    respective documentations

Setting up the environment
--------------------------
The development environment was set up using `conda`.

Create `environment.yaml` file in the project root.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: yaml
    :caption: environment.yaml

    name: book
    channels:
        - defaults
        - conda-forge
    dependencies:
        - conda-forge::jupyter-book
        - pip
        - pip:
            - ghp-import2

This will create a conda environment with `name` as **book**. It will also install the mentioned 
dependencies. The dependencies can be listed with explicit channel name so as to install from
a specific channel instead of letting conda decide. In this case `jupyter-book` will be installed
from the `conda-forge` channel.

Pip dependencies can also be listed to install packages from pip instead of conda. In this case
`ghp-import2` was supposed to be installed via pip hence, is listed under pip dependencies.

.. seealso::

    `Creating an environment file manually <https://docs.conda.io/projects/conda/en/stable/user-guide/tasks/manage-environments.html#creating-an-environment-file-manually>`__ for more information
    on creating the environment.yaml file.

Create the conda environment 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
To create the conda environment run the following command

.. code-block:: shell

    conda env create -f environment.yaml  

In case the dependencies need to be updated, make the changes in the
environment.yaml file and run the following command

.. code-block:: shell

    conda env update --prefix ./env --file environment.yaml  --prune

.. seealso::

    `Creating an environment from an environment.yml file <https://docs.conda.io/projects/conda/en/stable/user-guide/tasks/manage-environments.html#creating-an-environment-from-an-environment-yml-file>`__ and 
    `Updating an environment <https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#updating-an-environment>`__
    


.. _conda: https://docs.conda.io/en/latest/
.. _jupyter-book: https://github.com/vandyG/clickyaml
.. _cookiecutter: https://cookiecutter.readthedocs.io/en/stable/