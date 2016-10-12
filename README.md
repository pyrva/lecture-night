# GitHub for Beginners: Open source your python project

In this talk, we'll cover how to use git at the command line level to unleash the full power of git as a version control for your codebase. This tutorial assumes you have a basic knowledge of the command line, the git package installed (brew install git; yum install git; apt-get install git), and a desire to learn new things.

## Key Concepts & Verbiage

There are many terms and concepts that the savvy git user knows but to start your git career you only need to know two primary concepts: **commits** and **repositories**.

### Commit

A commit is the act of creating a snapshot of the current state of your code. 

 - is a record of what files you have changed since the last time you made a commit
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

For our first github project, we're going to cover a few things. First, we're going to learn typical git project flow of creating, editing, and maintaing python source code. Secondly, we're going to learn some simple yet critical git commands to control our repository. And thirdly, we're going to learn the basic python package structure for organizing python code. 

Our first github python project is going to be a basic math implementation of addition and subtraction. Let's call this project pyrva-math. Let's go through the various steps of creating this project.

### 1. Create the top level project directory.

This top level directory will contain your python source code, git repository, environments, etc. It's the root directory of your project.

```shell
mkdir -p /any/path/to/project/pyrva-math  # create the directory
cd /any/path/to/project/pyrva-math  # change to that directory you just made
```

### 2. Initialize our git repository

Every git command that you run from now on out will begin with ```git``` and include a succeding command dictating what you want git to do. The command that tells git to initialize a new repository is abbreviated as ```init```. ```git init``` tells git to create a new repository at the current working directory. 

If you're unsure where your terminal is at any given point in this tutorial, you can always run the bash command ```pwd``` (this tells you **p**resent **w**orking **d**irectory you are in). 

Let's go ahead and create that git repository...

```shell
git init
```

Easy eh?

### 3. Implement our add and subtract functions

Create a file named pyrva.py within your working directory. You can do this directly in your terminal by running the command ```touch pyrva.py```. We're going to implement our complicated math functions as follows:

```python
def add(x, y):
    return x + y

def subtract(x, y):
    return x - y
```

In fact, instead of opening up a text editor, we can write our code into pyrva.py using bash!

```bash
echo """def add(x, y):
    return x + y

def subtract(x, y):
    return x - y""" > pyrva.py
```

Once you go bash, you never go back.

### 4. Check the status of our repository

Let's see if git notices that we created a new file in the directory. Probably the most type git command is ```git status```. ```git status``` gives you information about the current state of your project. It informs you on new files created, changes between current files and the last commit, and other pertinent information we won't delve into at the moment.

Go ahead and try ```git status```. You'll see something like the following:

```
MacBook-Pro-2:github robert$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	pyrva.py

nothing added to commit but untracked files present (use "git add" to track)
```

Under untracked files, you see our newly created file ```pyrva.py```. In git speak, untracked files refer to files that are newly created in the workspace. git has no prior record of that file and therefore is not currently tracking its changes.

### 5. Add pyrva to a commit

To have git keep track of our changes to ```pyrva.py```, we have to commit the file to our local repository so it can keep track of the file going forward. To add the file to a commit, yup you guessed it, we need to run the command ```git add``` and list the file names we wish to add. 

```bash
git add pyrva.py
```

Note you can add as many files as you want to a commit. Commits are not limited to just one new file or one line changes. We'll explore that a little further down.

Try running ```git status``` now and note the difference:

```
MacBook-Pro-2:github robert$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   pyrva.py
```

Cool beans.

### 6. Commit!

Let's commit the new ```pyrva.py``` file to our repository. 

```bash
git commit -m "Implemented pyrva.py"
```

Note the extra argument -m at the end of commit. The m stands for message. This allows us to create a text record of what the commit did for our project. This makes it easy to review your changes and figure out what commit performed what change to your code.

### 7. Modify our math module to abstract to infinite arguments

Our current implementation sucks. Let's abstract the addition and subtraction functions so they can handle a variable number of arguments and combine them into a single function called addition. We'll let the users pass in negative numbers if they want to perform subtraction.

Here's our new logic

```python
def add(*args):
    return sum(args)
```

And here's how to overwrite our existing code using bash...

```bash
echo """def add(*args):
    return sum(args)""" > pyrva.py
```

### 8. Save our changes to a commit

Note the difference now when we check the status of our project (```git status```):

```
MacBook-Pro-2:github robert$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   pyrva.py

no changes added to commit (use "git add" and/or "git commit -a")
```

Unlike before where we had an untracked file, now we have "changes not staged for commit". To save those changes, we have to add the files that we changed to our new commit. 

```bash
git add pyrva.py
```

### 9. Commit!

Nothing new here...

```bash
git commit -m "Abstracted add to add and subtract infinite arguments"
```

Note, we can check and see how many commits our repository has now by checking our git log:

```bash
commit 4c8bc245fa137abc4ab25004d5429dd00cc5f655
Author: Robert Lee <lee.robert.138@gmail.com>
Date:   Wed Oct 12 15:29:48 2016 -0400

    Abstracted add to add and subtract infinite arguments

commit 1c52544327a29ff4eaf95793c25ca6bc781f49f5
Author: Robert Lee <lee.robert.138@gmail.com>
Date:   Wed Oct 12 15:19:27 2016 -0400

    initial commit
```

To exit out of the log, push q to **q**uit. 

### 10. Push our local repository to github

Create a new repository on (GitHub)[http://github.com] by clicking on the + icon on the top right. You'll see something like this:

![Create Repository](http://i.imgur.com/N3VT4GI.png)

You'll see a few options to help you get started. The commands we care about are here

![Origin](http://i.imgur.com/ZYmISEJ.png)

Go ahead and run the commands GitHub provides within your terminal... don't run my commands below! It's my repository.

```bash
git remote add origin https://github.com/leerobert/pyrva.git
git push -u origin master
```

Ok cool. You should your code now uploaded to your remote repository on GitHub. Let's briefly talk about the git commands we just ran...

To control the remote repositories that you want to share your local repository with, you'll interface with ```git remote```. To view all the remote repositories your local repo talks to, you can view them by running ```git remote -v```. I added a remote repository that I named origin and located at https://github.com/leerobert/pyrva.git. You similarly added a remote repository named origin at the link GitHub made for you. 

To talk to our remote repositories, we push (upload) our local code and pull (download) remote code. Here, since all our code was local, we pushed our two commits to origin (our remote github repo) to the branch master. We won't be covering branches so don't worry about the master component for now.

### 11. Editing Code on Github

By clicking into ```pyrva.py``` and then clicking on the pencil on the far right toolbar above the source code, we can edit our source code within GitHub.

Let's add our author name to the top of the ```pyrva.py```.

![Adding Author](http://i.imgur.com/pIzaPqe.png)

Once you've finished, scroll to the bottom. Notice that changes, even on the remote repo, require commits. Every change is always track by a commit. Add a commit message and save the commit.

![Commiting Author Change](http://i.imgur.com/olzaX7b.png)

### 12. Creating a README.md

The nice document you're reading right now is called a README document. README documents by default are parsed by GitHub and placed below the package directory on the main page of your GitHub project. The README document helps other developers understand what your project does, how to install it, and basic usage. 

This README document is written using a language called Markdown. It's actually quite easy to learn and formats your text in an aesthetically pleasing way. Check the additional resources below to learn more about markdown syntax. 

Ok enough playing on GitHub. Let's go back to our terminal. Be sure you're still in your project directory. Create our README.md doc with the following content:

```bash
echo """# pyrva
Super complicated addition function""" > README.md
```

### 13. Save our changes to a commit 

You know the drill.

```bash
git add README.md
git commit -m "Added a sweet README in markdown"
```

Also while we're at it, let's get rid of the extraneous return line at the bottom of ```pyrva.py``` and rename our function to addition cause I feel like it. 

```bash
echo """def addition(*args):
    return sum(args)""" > pyrva.py
```

You know the drill (again).

```bash
git add pyrva.py
git commit -m "add renamed to addition and cleaned return lines"
```

### 14. Push our commit to github

Now push that commit to github...

```bash
git push origin master
```

### 15. Wait what happened?? Merge???

What???

```bash
MacBook-Pro-2:github robert$ git push origin master
Username for 'https://github.com': leerobert
Password for 'https://leerobert@github.com': 
To https://github.com/leerobert/pyrva.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/leerobert/pyrva.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

What just happened is a very common occurence when working with local and remote repositories. Some of you might have already figured out why this error was thrown. 

We modified the source of ```pyrva.py``` on our remote repository to include author name at the top of the file. We then locally modified ```pyrva.py``` to rename the function from add to addition. We're trying to push a commit from our local repository to the remote repository without taking in account the current, most up to date commit of the remote repository. This is a common occurrence in distributed programming. Resolving these conflicts is called **merging**.

### 16. Pulling And Merging Conflicts

As the hint suggests in our push message, let's go ahead and pull the latest commits from the remote repository.

```bash
MacBook-Pro-2:github robert$ git pull
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/leerobert/pyrva
   8dd79d7..baf23a0  master     -> origin/master
Auto-merging pyrva.py
CONFLICT (content): Merge conflict in pyrva.py
Automatic merge failed; fix conflicts and then commit the result.
```

Here, we see git tries to resolve the conflicts between our local commit of modifying the function name and our remote commit of adding in author information. However, the automatic merging fails. 

If we check out our local git repository status, we find out exactly what files need to be manually merged:

```
MacBook-Pro-2:github robert$ git status
On branch master
Your branch and 'origin/master' have diverged,
and have 1 and 1 different commit each, respectively.
  (use "git pull" to merge the remote branch into yours)
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)

	both modified:   pyrva.py

no changes added to commit (use "git add" and/or "git commit -a")
```

If we take a look inside ```pyrva.py```, git tells us exactly where merges are needed.

```bash
MacBook-Pro-2:github robert$ cat pyrva.py 
<<<<<<< HEAD
def addition(*args):
=======
"""
author
"""

def add(*args):
>>>>>>> baf23a09e13d8107c74dc73db4249eabf2ff6611
    return sum(args)
```

We now get a glimpse of why git wasn't able to automatically merge our differing commits. 

```
<<<<<<< HEAD
def addition(*args):
=======
```

Between ```HEAD``` and ```=======``` are our local changes to ```pyrva.py```

```
=======
"""
author
"""

def add(*args):
>>>>>>> baf23a09e13d8107c74dc73db4249eabf2ff6611
```

Between ```=======``` and ```>>>>>>> <hex>``` are the remote changes we made when we included the author information. The large hex number that follows the arrows is the unique identifier for the commit we made on github. 

Lets go ahead and resolve the conflict by incorporating both changes together

```bash
echo '''"""
Author: Robert Lee
"""

def addition(*args):
    return sum(args)''' > pyrva.py
```

### 17. Push Merge And Voila

To resolve a manual merge, we follow a pretty predictable flow. First add the merged file then commit the merge changes. Lastly push the changes up to our remote repo.

```bash
git add pyrva.py
git commit -m "manually merged pyrva"
git push origin master
```

Break time...

# PYRVA OPEN SOURCED

For this next section, we're going to run through common structure and tools that are often employed in python open sourced projects. In the process, we're going to incorporate all these techniques into our pyrva project.

## Organizing Source Code

Python code is written in files we like to call **modules**. ```pyrva.py``` is a module that contains the function addition. A Python module is simply a python source file, which can expose classes, functions and global variables. When imported from another Python source file, the file name is treated as a namespace.

A python package is simply a collection of python module(s). 

We're going to refactor our ```pyrva``` module so that it sits inside a ```pyrva``` package. Now, on the surface this might sound confusing. Why are we creating a package with the name ```pyrva``` to contain the ```pyrva``` module? Isn't this redundant? 

In our case, perhaps. But imagine if we wanted to add another module that contained completely different functions in form yet we wanted to retain the pyrva namespace. In order to retain the pyrva namespace but have multiple modules, we'll have to organize the different modules under the same package. Enough talking and more doing.

Go ahead and create the python package. This is simple a directory that contains an ```__init__.py``` file. The ```__init__.py``` file within a folder is python's way of signalling: "Hey, everything in this folder ending in ```*.py``` is a module for the package. It differentiates the package folder from a normal folder. The ```__init__.py``` file also has other functionalities we'll touch on in a second.

```bash
mkdir pyrva  # our package folder
touch pyrva/__init__.py  # let python know this is a package
```

Now let's move the pyrva module into the pyrva package.

```bash
mv pyrva.py pyrva/
```

Now, if we open up our python interpreter and import our pyrva package, we'll find it successfully imports.

```python
>>> import pyrva
>>> dir(pyrva)
['__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__path__', '__spec__']
```

Yet we're still missing our addition function. It doesn't show up in the list of functions within the pyrva package. To get to the addition function, we have to import the module pyrva that contains the addition function.

```python
>>> import pyrva.pyrva
>>> dir(pyrva.pyrva)
['__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'addition']
>>> pyrva.pyrva.addition(1,2)
3
```

How can we fix this so we only have to import pyrva to get access to the addition function? This is where the ```__init__.py``` comes into handy. We're going to import from the module pyrva the addition function within the ```__init__.py``` file. Any time python loads your package, it executes the globals within the ```__init__.py``` file. This allows us to import important functions from our modules into our top level namespace.

```bash
echo """from pyrva.pyrva import addition""" > pyrva/__init__.py
```

Now when we import pyrva in a python interpreter, we see both the module and the function addition have been included

```python
>>> import pyrva
>>> dir(pyrva)
['__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__path__', '__spec__', 'addition', 'pyrva']
```

## Python Virtual Environment

"A Virtual Environment is a tool to keep the dependencies required by different projects in separate places, by creating virtual Python environments for them. It solves the “Project X depends on version 1.x but, Project Y needs 4.x” dilemma, and keeps your global site-packages directory clean and manageable. For example, you can work on a project which requires Django 1.3 while also maintaining a project which requires Django 1.0." 

### Installation 

Installing virtualenv for python is as simple as the following few steps:

```bash
pip install virtualenv
virtualenv -p python3 env 
source env/bin/activate  # activates the virtualenv within your terminal session
 ```
 
### requirements.txt file

Most python open source packages have a requirements.txt file at the root of the project directory that denotes the required packages the project requires for runtime. Pip has a convenient way of installing packages from a text file:

    # cd to your project and create a virtualenv
    cd /path/to/project
    source env/bin/activate  # ensure you're within your virtual environment
    pip install -r requirements.txt  # installs packages listed in the requirements.txt file

A current list of installed packages your project currently has in its virtual environment can be viewed by running

    pip freeze
    
An up to date ```requirements.txt``` file can be obtained by running at your project directory level

    pip freeze > requirements.txt 


## Python Setup Tools

Every project that you want to package needs a setup.py file that is executed whenever you build a distribution and on each installation. The setup.py file contains all the metadata relevant to your project (author name & email, repo url, languages supported, README, CHANGES, etc.) however only a very basic set of variables are needed to properly set up a package that can be installed.


Here's an example of a basic ``setup.py`` file:

```python
from setuptools import setup, find_packages

setup(
    name='pyrva',
    version='0.0.1',
    packages=find_packages(exclude=['tests']),
    install_requires=['Flask', 'sympy'],  # external libraries
    tests_require=['pytest'],  # libraries required for testing
)
```

There are many other fields you can pass into the setup function to provide metadata surrounding the nature of your package. For example, ```author```, ```author_email```, ```description```, and many more. 

Let's go ahead and add that setup file to our project root directory.

## Pytest



## Additional Resources

 - [Interactive tutorial](https://try.github.io/levels/1/challenges/1)
 - [Visual Guide To How Git Works](http://marklodato.github.io/visual-git-guide/index-en.html)
 - [Learning Markdown](https://guides.github.com/features/mastering-markdown/)
 - [Forking Existing Projects](https://guides.github.com/activities/forking/)
 - **Advanced** [Uploading Project to PyPi](http://peterdowns.com/posts/first-time-with-pypi.html)
