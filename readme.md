## Goal 
- Use `git` to interact with this repository
- Manage python environment via `conda`
- Familiar with basic Python syntax

## Introduction to Git
- [What Is Git & Why Should You Use It?](https://www.nobledesktop.com/blog/what-is-git-and-why-should-you-use-it)
    - Git is a version control system
    -  ![](https://www.nobledesktop.com/image/blog/git-branches-merge.png)
    - Ways to use git
      - command line interface (CLI)
      - desktop graphic user interface (GUI), such as [Sourcetree](https://www.sourcetreeapp.com/)
    - Local Repository
      - Folder-based, with a `.git` subfolder tracking the changes.
    - Remote Repository
      - ![](https://www.nobledesktop.com/image/blog/git-distributed-workflow-diagram.png)
- [Installation](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- Basic concepts & commands
  - Create a git repository
    - create a folder: `mkdir git-intro`
    - go inside the folder `cd git-intro`
    - initialize git: `git init`
  - make a commit
    - create a file: `touch file1.txt`
    - check status: `git status`
      - staged file vs. unstaged file
    - stage a file: `git add file1.txt`
    - check status: `git status`
    - commit a change: `git commit -m 'add file1.txt'`
    - check status: `git status`
  - make another commit
    - add a line in `file1.txt`
    - `git status` and `git diff` (and GUI visualization)
    - `git add .` and `git commit -m 'hello world'`
  - create a branch
    - why can't we just iterate on `main`?
    - `git checkout -b branch_1`
    - switching between branches: `git checkout main` & `git checkout branch_1` (no more `-b`)
    - create a commit on a branch
    - merge into main
      - `git checkout main`
      - `git merge branch_1`
      - explain via Sourcetree
    - handling merge conflict
      - it's pretty common that multiple people work on the same file, and each person is unaware of others are touching the same file (bad communication!)
      - (example)
  - Remote repository
    - why do we need a remote repository?
    - create a github account
    - go to [FINM-36700](https://github.com/Kawaislands/FINM-36700)
    - Connecting to GitHub with SSH
      - follow the instruction [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
        - This will also be in HW1
    - clone the repo: `git@github.com:Kawaislands/FINM-36700.git`
    - how to constantly keep up-to-date?
      - Do `git pull origin main` frequently
  - Pull request 
    - [Why do we need a pull request?](https://co-learning.eu/2017/10/04/why-and-how-do-we-use-pull-request/)
    - things you need to do for pull request
      - create a branch and make some changes
      - push that branch to remote: `git push --set-upstream origin <branch_name>`
      - branch naming practice
          - you can skip this from now
      - create a pull request
      - merge pull request
        - this will be done by me

## Introduction to Anaconda 
- [Python versions](https://www.python.org/doc/versions/)
  - python keeps releasing new versions 
  - projects are motivated to use the latest python version at the time of creation.
  - we might end up having N projects running N different python versions
  - ... while there is only 1 python version installed on laptop 
  - ... even you managed to install different python versions, package requirement (e.g. `pandas` version) could also vary from project to project.
  - ... so, how do we solve this problem?
  - In industry, people commonly use [virtual environment](https://realpython.com/python-virtual-environments-a-primer/) to manage python versions and dependencies across projects  
- Virtual environment
  - a lot of choices (`venv`, `pipenv`, `conda`, `poetry`, etc.) and they are all great. It really depends on what a company chooses to offer.
      - the 1st virtual environment of a company is commonly chosen by the first software engineer/data scientist. 
      - As the team and # of repositories grow, virtual environment might change (e.g., from `venv` to `conda` or `poetry`) 
  - here we choose `Conda` as
    - more data science friendly
    - relatively easy to install and commonly adapted
    - it can manage other programming languages, such as R, C/C++, Ruby, Scala, etc.
- Download and install [Anaconda](https://www.anaconda.com/products/individual) (sometimes company chooses [`Miniconda`](https://docs.conda.io/en/latest/miniconda.html))
- Working with Anaconda
  - creation: `conda create -n lecture_1 python=3.10`
  - check python version difference
    - global python: `python -V` or `which python`
    - local python: `conda activate lecture_1`, and repeat the 2 command above
  - deactivate: `conda deactivate`
  - list of all env: `conda env list`
  - list of the package installed in an env: `conda list -n lecture_1`
- install packages
    - **Python is very famous of its abundance of libraries.** Almost anything has a python library.
    - https://pypi.org/
    - [pip](https://realpython.com/what-is-pip/) is a very common way to install/unisntall/upgrade package
      - `pip install requests` (if `requests` is not installed, install the latest version. Otherwise, do nothing)
      - `pip install requests==1.20` (define a specific version to install)
      - `pip install requests -U` (make sure `requests` is installed as the latest version)
    - Package management in the wild:
        - `pip install -r requiremenets.txt` (note that you need to run this command where the `requirements.txt` file is at the current working directory)
        - check with `pip list`
- moving forward...
    - We will create different environment for each class, with different package requirements
    - Be very good at virtual environment, or python devops in general, from day 1 of your internship adds a tremendous amount of good impressions to your team and your managers.
- helpful readings
    - https://www.geeksforgeeks.org/important-differences-between-python-2-x-and-python-3-x-with-examples/
    - https://realpython.com/effective-python-environment/
    - https://www.freecodecamp.org/news/why-you-need-python-environments-and-how-to-manage-them-with-conda-85f155f4353c/
    - https://www.section.io/engineering-education/introduction-to-virtual-environments-and-dependency-managers/
    - https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-with-commands