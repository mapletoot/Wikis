# Contents of a Repo


# Gitignore
Now create a gitignore file by opening VSCode and calling the file `.gitignore`. The dot infront tells the operating system not to show this types of files in the GUI, but on a mac they can be toggled on by using `⌘ + ⇧ + .` The gitignore file works from the current folder space and it is possible for other gitignore files to appear in other folders (for example, in virtual environments). 
Withing the .gitignore file, `#` is a comment and any uncommented lines should be names of files or folders that we don't want git to track or upload. Examples of this are potentially data files, ipynb_checkpoints or outputted models that are large file sizes that would waste space in GitHub as we are only using GitHub to track changes to the code. An example of this file would be:

'''

    # Data
    Data/

    # Checkpoints
    .ipynb_checkpoints/

    # Virtual environments
    .venv/

'''


# Virtual environment (.venv/)

## Overview
It is usually best to use the repository within a virtual environment. A virtual environment is a list of packages and their versions that the repository was built using, so that others can run the code in the repository with exactly the same requirements. The precise list of packages and their versions are then saved in the `requirements.txt` file that another user can directly install. This is necessary because as packages change they can discontinue funcitons or change syntax, so someone running a newer version of pandas, say, might run into problems when running your file. The virtual environment should appear in the `.gitignore` file because:
- other users may be using different operating systems
- committing changes to the virtual environment can result in large repositories that are storing lots of unnecessary libraries on GitHub
- Can cause merge conflicts and many unnecessary git changes

## Setup 
To set up a virtual environment, in the root folder in the terminal, use the following command:
```bash
python3 -m venv .venv
```
`python3` tells the computer to use the python3 programme, `-m venv` is asking it to use the venv module of python3, and finally `.venv` will mean that the files are created in a folder called `.venv/`. Within this folder is a `.gitignore` file that just contains a * to indicate that git should ignore everything in this folder and a `pyvenv.cfg` file. There are also 3 folders: bin, lib and include

In order for the virtual environment to be initialised, we need to run 
```bash
source .venv/bin/activate
```
where source is a shell commance that tells us to read and execute the file `.venv/bin/activate` in the current shell location. This alters the PATH so that the folder location uses a local path into this repository rather than the global path. Within the terminal, should also see `(.venv)` at the start of the file location. This will be active for the rest of the time the terminal window is open, and we will also need to run this command everytime we want to work in the terminal in this folder.

To check it has worked, could run something like `which python` and this should return a path to the bin inside the current folder.

## Built-in packages
When using a virtual environment, most packages will have to be installed from scratch (see next section) but some are already built in, such as `os` and `pathlib`. `os` is a library used to change the current working directory of the file, as it is common for all files in the repository to have their root set as the main folder in the repository. The `pathlib` library is then used to create paths in a user-friendly way to be used with `os`.

## Installing packages
Now that the virtual environment is ready (we can see the `(.venv)` at the start of the file location), we can install packages in the usual way. Good packages to install are: 


However, this can be tedious and it is good practice to have a `requirements.txt` file to make work easy to reproduce and to save time.

# Requirements (requirements.txt)

## Creating the file

## Using the file
When someone else wants to run your code, the usual workflow is:
- clone the repository
- create their own virtual environment (because the `.venv` shouldn't be in the repository) and activate it
- install the required packages using
```bash
python -m pip install -r requirements.txt
```
In theory, they should then be able to use the repository without any issues, so long as the kernel that the code is running from is using the same libraries as were installed from `requirements.txt`.


## Running notebooks
In order to run a notebook using jupyterlab, the notebooks need a kernel to run from. This means we have to create a kernel that uses the libraries from the virtual environment we have created above. The code to do this is as follows:
```bash
python -m ipykernel install --user \
    --name insider-threats \
    --display-name "Python (Insider Threats)"
```
python selects the python and dependencies used within this environment (see `which python` above). `-m ipykernel install --user` then tells it to use the ipykernel module and install a new kernel for this user account, with the name insider threats and this will be displayed as 'Python (Insider Threats)'.


# Readme (readme.md)