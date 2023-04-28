The Makefile
============

Makefile is a way of automating software building procedure and other complex tasks with dependencies.
The functionality of makefile and make utility are beyond the scope of this book. You can find loads
of good articles and resources to understand them.

.. seealso::

    `GNU make <https://www.gnu.org/software/make/manual/make.html>`_ for more information on make and
    makefile.

The `audreyr/cookiecutter-pypackage <https://github.com/audreyr/cookiecutter-pypackage>`_ template 
adds a bunch of useful make rules. These rules help automate a lot of procedures which otherwise you 
would be running manually.

Run ``make help`` to understand each rule.

.. code-block::

    ❯ make help
        clean                remove all build, test, coverage and Python artifacts
        clean-build          remove build artifacts
        clean-pyc            remove Python file artifacts
        clean-test           remove test and coverage artifacts
        lint                 check style
        test                 run tests quickly with the default Python
        test-all             run tests on every Python version with tox
        coverage             check code coverage quickly with the default Python
        docs                 generate Sphinx HTML documentation, including API docs
        servedocs            compile the docs watching for changes
        release              package and upload a release
        dist                 builds source and wheel package
        install              install the package to the active Python's site-packages
