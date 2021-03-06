---
layout: post
title: "Python Virtual Environments Cheat Sheet"
author: "Kyle Gorak"
date: "2016/01/08"
output:
  html_document:
    keep_md: true
comments: True
tags: [Python 3, Python, development environment]
---

Virtual environments make using Python a bit more manageable, especially when it comes to deploying Python programs and creating the requirements (able to use `pip freeze > requirements.txt` and only use packages necessary to that individual project). However, I commonly find myself forgetting some of the more basic commands. For Python 2 use `pip`, for Python 3 use `pip3`. 

#### Downloading virtualenv

1. Download virtualenv using [pip](https://virtualenv.readthedocs.org/en/latest/installation.html) `pip install virtualenv`
2. Download virtualenvwrapper using [pip](https://virtualenvwrapper.readthedocs.org/en/latest/install.html) `pip install virtualenvwrapper`. Virtual environment wrapper will make using virtual environments a little easier.
3. On a Mac:
    - Create a directory to store your virtual environments, i.e `mkdir ~/Documents/Development/virtualenvs`
    - `vi ~/.bash_profile`
    - Add to file:
    {% gist gorhack/28f5e556a9eaf495f25f .bash_profile %}
    - Save and quit (esc + :wq)
    - `source ~/.bash_profile`
    - Quit and reopen terminal to reload bash profile

#### Basic commands to use virtual environments

- `lsvirtualenv`: List your virtual environments
- `mkvirtualenv [name]`: Create a new virtual environment. Use the flag `-ppython3.5` after name to create a Python 3.5 virtual environment. 
- `rmvirtualenv [name]`: Remove a virtual environment
- `workon [name]`: Enter a virtual environment
- `deactivate`: Stop working on a virtual environment
- `pip freeze > requirements.txt`: View modules installed in current environment
- `pip install -r requirements.txt`: Install all modules in requirements.txt

#### Setting up virtual environments

- To make `workon [name]` go directly to the directory of the project directory, edit the /virtualenvs/postactivate and add: {% gist gorhack/d554e7065e061f5b7284 postactivate.bash %}
- To make `deactivate` exit the project directory, edit the /virtualenvs/postdeactivate and add: {% gist gorhack/d554e7065e061f5b7284 postdeactivate.bash %}
    - by [Harry Marr](http://hmarr.com/2010/jan/19/making-virtualenv-play-nice-with-git/)
