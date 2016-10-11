# GitHub for Beginners: Open source your python project

In this talk, we'll cover how to use git at the command line level to unleash the full power of git as a version control for your codebase. This tutorial assumes you have a basic knowledge of the command line, the git package installed (brew install git; yum install git; apt-get install git), and a desire to learn new things.

## Key Concepts & Verbiage

There are many terms and concepts that the savvy git user knows but to start your git career you only need to know two primary concepts: **commits** and **repositories**.

### Commit

A commit is the act of creating a snapshot of the current state of your code. 

 - used as a verb/noun: "I just committed some code", "Check out the latest commit"
 - essentially a project is a collection of commits
 - sometimes colloquially referred to as "changes"


### Repositories (often shortened to "repo")

The directory where you access your project, its files, and all the version of its files (*commits*).  

 - Repositories can live both on your local machine and on remote servers (GitHub)
 - The act of copying a repository from a remote server to your local machine is called **clone**-ing.
 - Downloading commits that don't exist on your local machine from a remote repository is called **pull**ing changes.
 - Uploading commits that you have on your local machine to a remote repository is called **push**ing changes.
 - Think of the remote repository (GitHub) like DropBox... it synchronizes commits accross all local machines.

If these terms are still confusing to you, don't worry about it. The best way to learn something is to just do it. Let's get our hands dirty...

## Creating Your First GitHub Project

### 

## Python Virtual Environment

"A Virtual Environment is a tool to keep the dependencies required by different projects in separate places, by creating virtual Python environments for them. It solves the “Project X depends on version 1.x but, Project Y needs 4.x” dilemma, and keeps your global site-packages directory clean and manageable. For example, you can work on a project which requires Django 1.3 while also maintaining a project which requires Django 1.0." 

### Installation 

Installing virtualenv for python is as simple as the following few steps:

    pip install virtualenv
    # cd to your project and create a virtualenv
    cd /path/to/project
    virtualenv -p python3 env 
    source env/bin/activate  # activates the virtualenv within your terminal session
    pip install pyrva  # install your packages within the virtual environment
 
### requirements.txt file

Most python open source packages have a requirements.txt file at the root of the project directory that denotes the required packages the project requires for runtime. Pip has a convenient way of installing packages from a text file:

    # cd to your project and create a virtualenv
    cd /path/to/project
    source env/bin/activate  # ensure you're within your virtual environment
    pip install -r requirements.txt  # installs packages listed in the requirements.txt file

## Python Setup Tools



## Putting It All Together



## Advanced Techniques

1. Commenting on commits 
2. Pull Requests

## Additional Resources

 - [Interactive tutorial](https://try.github.io/levels/1/challenges/1)
 - [Visual Guide To How Git Works](http://marklodato.github.io/visual-git-guide/index-en.html)
 - [Learning Markdown](https://guides.github.com/features/mastering-markdown/)
 - [Forking Existing Projects](https://guides.github.com/activities/forking/)
 - **Advanced** [Uploading Project to PyPi](http://peterdowns.com/posts/first-time-with-pypi.html)
