# Getting your Python environment set up

This document will help you install python, pyenv (for virtual environment management), and poetry (for package management). If you're using Windows, we encourage you to install the Windows Subsystem for Linux (WSL) in step 1. If you're using Linux or MacOS, you can skip the first step. 

NOTE: This guide explains the use of pyenv and poetry. The python community has been standardizing on the use of a library called [uv](https://github.com/astral-sh/uv) for dependency management, and this guide has not yet been updated.

# 1. Installing WSL on Windows
- [Installing WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
	- Run Windows Powershell as an administrator 
	- run `wsl --install -d Ubuntu`
		- (if you have to start over, you can remove this installation with `wsl --unregister Ubuntu`)
- After this installation, everything else you do will be in the WSL / Ubuntu environment.
  
# 2. PyEnv
- Python projects usually specify which version of Python and other packages they require. To prevent version conflicts between different projects, it's useful to have virtual environments which give each project its own python installation. We can manage virtual environments with pyenv.

## Installing pyenv (Ubuntu / WSL)
- install pyenv: `curl https://pyenv.run | bash`

## Installing pyenv (MacOS)
- We'll first install Homebrew. Homebrew is a package manager for MacOS. Copy this command into your terminal to install:
  ```
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```
- To install pyenv: `brew install pyenv pyenv-virtualenv`

## Update your shell (Ubuntu / WSL / MacOS):
- Add these settings to your shell configuration file  (e.g. `~/.bashrc` for bash or `~/.zshrc` for zsh) and save them:
	- `export PATH="$HOME/.pyenv/bin:$PATH"`
	- `eval "$(pyenv init -)"` 
	- `eval "$(pyenv virtualenv-init -)"`
- restart your shell: `exec $SHELL`

# 3. Build Dependencies
- These are libraries that we will require to build our Python installations

## Install Build dependencies (Ubuntu / WSL)
- `sudo apt-get update; sudo apt-get install --no-install-recommends make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev`

## Install Build dependencies (MacOS):
- `brew install openssl readline sqlite3 xz zlib tcl-tk`

# 4. Managing Python Versions and Virtualenvs with Pyenv
- Use pyenv to install the preferred version of python (this could be 3.11, or whatever your specific project requires.)
	- `pyenv install 3.11`
- Make a new virtual environment called 'learn-python-env' which uses 3.11 as its base. Activate the virtual environment.
	- `pyenv virtualenv 3.11 learn-python-env`
	- `pyenv activate learn-python-env`
- You can specify the local python version for any directory which will automatically activate the virtual environment. This is an efficient way to switch between projects which use different virtualenvs.
	- create a new directory for this class anywhere you'd like. To do so in your home directory:
  		- `mkdir ~/learn-python`
    		- `cd ~/learn-python`
  	- `pyenv local learn-python-env`

# 5. Managing packages with Poetry

## Installing Poetry (Ubuntu / WSL / MacOS)
- `curl -sSL https://install.python-poetry.org | python3 -`

## Update your shell (Ubuntu / WSL / MacOS)
- Add these settings to your shell configuration file  (e.g. `~/.bashrc` for bash or `~/.zshrc` for zsh) and save them:
	- `export PATH="$HOME/.local/bin:$PATH"`
- restart your shell: `exec $SHELL`

## Set up your poetry environment
- `cd ~/learn-python`
- `poetry init` (n for author, no to both interactive dependencies questions, defaults for everything else)

# 6. Jupyter Notebook

## Installing Jupyter
- `cd ~/learn-python` (or whatever you named your directory from step 4)
- `poetry add jupyter`

## Running Jupyter Notebook / Jupyter lab
- Open a shell with the environment configuration by running `poetry shell`
- Windows WSL:
	- run `jupyter notebook --no-browser` or `jupyter lab` and connect to the URL provided with your regular web browser
 	- (the default is http://localhost:8888)
- Other Platforms:
	- run `jupyter notebook` or `jupyter lab`
 
## What's the difference between Jupyter Notebook and Jupyter Lab?
- Jupyter Lab is a slightly more robust UI that, among other things, allows you to view multiple notebooks in the same browser tab. Without it, you'll have a separate tab for each notebook you open.
