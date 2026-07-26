# Creating New Repos

Contents
1. (From Folders on system)[#From-Folders-on-System]
2. (In GitHub)[#In-GitHub]


# From Folders on System

## 1 - In your file system
First create a folder where you want the GitHub repository to be contained
Then create a file system. Some examples of folders would be:
- Data
- Notebooks
- Source code

Now create a gitignore file by opening VSCode and calling the file `.gitignore`. In this file, `#` is a comment and any uncommented lines should be names of files or folders that we don't want git to track or upload. Examples of this are potentially data files, ipynb_checkpoints or outputted models that are large file sizes that would waste space in GitHub as we are only using GitHub to track changes to the code. An example of this file would be:

'''

    # Data
    Data/

    # Checkpoints
    .ipynb_checkpoints/

'''

Now we are nearly ready to start tracking with GitHub. If there are any folders that are currently empty, it is also possible to add in a file called `.gitkeep` so that the folder uploads to git even though it is empty.

## 2 On GitHub
At GitHub online, create a new repository. Choose a .gitignore file if you know what languages you will be using and a license if it will be shared with others. Then copy the URL.

## 3 In terminal
In the terminal at the folder where the root of your file system is use the following commands:
```bash
git init
git add .
git commit -m "created initial file tree"
git remote add origin <insert-URl->
git push --set-upstream origin master
```

Now when you go back to github, this file system should be there and you are ready to work on this file system in other computers



# Cloning a repository already on github
This is a bit simpler. Create a folder where the repository will be stored, open the terminal in this folder and do the following steps:
```bash 
git init
git clone <insert-URL->
```