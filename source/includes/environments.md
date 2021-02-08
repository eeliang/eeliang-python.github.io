---
title: Environment management
---

# Environment management

Python is an awesome scripting language to perform a variety of computation and automated tasks. It is also open-source/extensible, meaning that contributors are continually upgrading and adding new tools to the "Python tool kit". This includes newer Python versions (e.g. `v3.8.0` introduced the walrus operator) and packages.

## Version and Environment management in Python

For every problem, there will be 101 ways to address it. But it is important to remember that the "best" solution is determined by the working environment. If you are working in a team, there are standards for what is the Python version to be working on, or the package versions listed in `requirement.txt`.

Further, these environment constrains change with each project. Older projects may not receive continued support and operate in an archaic environment - Python v2.7.16 (RIP 2020).

Lastly, you may wish to keep the latest (or last known stable) version of Python on your personal machine. This allows you to explore new frameworks and experiment with the latest gadgets.

### So how do I manage all these different environments?

Enter [pyenv](https://github.com/pyenv/pyenv). A command-line tool that simplifies version management.

Next, [pyend-virtualenv](https://github.com/pyenv/pyenv-virtualenv). A plugin that manages virtual environments.

## How to use **pyenv**

### Download and install **pyenv**

```
brew update
brew install pyenv

echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
```

Install **pyenv** as a command-line tool. For MacOS users, Brew is a convenient package manager.

Next, add **pyenv** to your `PATH`. The specific setup will be different based on your OS and shell.

### Setting up **pyenv** versions

```
pyenv install --list | grep 3.8
pyenv install 3.8.5
pyenv version               # 3.7.6 (set by ~/.pyenv/version)
python --version            # Python 3.7.6
pyenv global 3.8.5
pyenv version               # 3.8.5 (set by ~/.pyenv/version)
python --version            # Python 3.8.5
```

- `install`

Use this command to call **pyenv** to install different versions of python. Installing a fresh version of python might take a while.
Add the `--list` flag to view all available versions.

- `versions`

Check the available python version that has been downloaded.

- `version`

Check the python version that is designated as the current version.

- `global`

Set the default version of python on your machine. It is recommended to use the last known stable version of python for this.

### Setting up your workspace with **pyenv** versions

```
cd project-dir
pyenv local 2.7.16
cat .python-version       # 2.7.16
pyenv version             # 3.8.5 (set by ~/project-dir/.python-version)
```

When working in specific projects (i.e. specific directories), you can define the Python version that you want to work in. The version is saved in `.python-version`.

### Automatically change to directory versions

```
eval '$(pyenv init -)' >> .zshrc
```

Add this code snippet in your shell startup files, pyenv will change to the local version whenever you move to a directory with a `.python-version` definition.

## How to use **pyenv-virtualenv**

### Download and install **pyenv**

```
brew install pyenv-virtualenv
```

Install **pyenv-virtualenv** as a command-line tool. For MacOS users, Brew is a convenient package manager.

### Setting up virtual environments

```
pyenv virtualenv 3.7.6 websiteproject
pyenv local websiteproject
pyenv activate websiteproject           # prompt= ( websiteproject ) $
pyenv deactivate                        # prompt= $
```

Define a virtual environment with the following command. This will create a directory to contain all the configuration for a _user-defined_ Python version with only the default packages. Packages installed in this directory will not affect or be affected by other package versions located elsewhere on your machine.

### Automatically switch to virtual environments

```
eval '$(pyenv virtualenv-init -)' >> .zshrc
```

If you add this code snippet in your shell startup files, pyenv-virtualenv will activate the virtual environment automatically whenever you move to a directory with a `.python-version` definition.

## FAQ

Some errors and solutions that i encountered along the way. For MacOS users, Brew is a convenient package manager.

### `pyenv: python: command not found`

```
whence python               # usr/bin/python
ln -s python3 python
whence python               # User/<username>/.pyenv/shims/python
```

This error occurs because the current version of python is different from where you installed **pyenv**. For example, if you installed **pyenv** with python3, check that the `python3` is the default.

- Add a symlink to your $PYENV_ROOT/versions/<current version>/bin

