Installing Requirements
=======================

Now the next step is to install the packages required for development. These packages may or may not be a 
dependency for our package. These requirements are used to define the complete python environment to 
facilitate the development of the project.

The user does not require unit testing packages (like ``pytest``) or packages used to create documentation (like ``sphinx``) are not
to run or use clickYaml. Rather developers and contributors need these packages to get started and contribute to the project.
Hence these requirements are usually found in a file present in the project root called as ``requirements.txt``. For
conda based projects ``environment.yaml`` file is preferred. This was one of the many learnings I had while working on
this project. I used ``requirements.txt`` file even though I was using a conda environment. ``requirements.txt`` file
should be used if you are using pip + venv. Although pip and conda are not interoperable but it is acceptable to ``pip install``
packages but it is recommended to install using conda as it keeps the environment more portable.

.. #TODO: Dependency management. Dependencies are all the software component that are required by our project/package to work. Without these 
.. dependencies the package might not work as intended. For example ``clickYaml`` creates ``Click`` commands 
.. out of the entries mentioned in a ``yaml`` file. In order for a user to use the clickYaml package he must 
.. have Click as well as pyyaml installed in his python environment. Now the user might not be aware of this
.. as a consequence of which the user is likely to run into runtime errors when using clickYaml. 

