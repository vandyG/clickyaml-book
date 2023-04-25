Setting up Version Control
==========================

Now that we have our project set up we are ready to begin with the real work. But first
we need to set up git and GitHub. I can't emphasize enough on how essential version control is.
On numerous occasions I've run into situation where I had to revert back the changes made to 
the code, and git made my life much easier. Collaborating with other developers is also an 
area where git proves to be useful.

And then there is GitHub which has a bunch of useful features apart from just being a place to 
host your repository. All the GitHub features that I leveraged while working on this project
will be discussed in details. From GitHub actions to GitHub CLI to GitHub pages most 
of it will be discussed.

Setting up Git
--------------

If you don't have git installed already, enter the following command

.. code-block:: shell

    sudo apt install git-all

.. seealso::

    For installation instructions for other operating system please refer to official documentation.
    `Installing Git <https://git-scm.com/book/en/v2/Getting-Started-Installing-Git>`_

Now navigate to the project repository and initialize git and make your first commit.

.. code-block:: shell

    git init
    git add .
    git commit -m "initialize git repo"

Set git email and user-name.

.. code-block:: shell

    git config user.name "hal9000"
    git config user.email "hal9000@discovery.one"

Now we have a local git repository, all we now need is to host this repository on GitHub. If you notice
there will be a file called ``.gitignore`` which defines all the files that are supposed to be ignored by 
version control. Files like the build files, documentation files are not required to be watched by the 
version control system.

Setting up GitHub Repo
----------------------

The traditional way will be to create a new repository on GitHub will be to either use GitHub Desktop
or from `<github.com>`_. But we are command line junkies and we prefer to use GitHub CLI. 

To install GitHub CLI ``gh`` run the following command.

.. code-block:: shell

    type -p curl >/dev/null || (sudo apt update && sudo apt install curl -y)
    curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
    && sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
    && sudo apt update \
    && sudo apt install gh -y

.. seealso::

    For installation instructions on other operating systems follow this `link <https://cli.github.com/manual/installation>`_.

To create a new repo run the ``gh repo create`` interactive command. And answer the prompts accordingly.

.. code-block:: shell

    ❯ gh repo create
    ? What would you like to do? Push an existing local repository to GitHub
    ? Path to local repository .
    ? Repository name open_pod_bay_doors
    ? Description I am afraid I cant do that
    ? Visibility Public
    ✓ Created repository vandyG/open_pod_bay_doors on GitHub
    ? Add a remote? Yes
    ? What should the new remote be called? origin
    ✓ Added remote https://github.com/vandyG/open_pod_bay_doors.git
    ? Would you like to push commits from the current branch to "origin"? Yes

    