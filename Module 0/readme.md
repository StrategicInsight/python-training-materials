# Installing WSL on Windows
- [Installing WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
	- Run Windows Powershell as an administrator 
	- run `wsl --install -d Ubuntu`
		- (if you have to start over, you can remove this installation with `wsl --unregister Ubuntu`)

# Installing pyenv on Ubuntu or WSL
- install pyenv: `curl https://pyenv.run | bash`
- Add the following lines to your shell configuration file (e.g. `~/.bashrc` for bash or `~/.zshrc` for zsh) and save them:
	- `export PATH="$HOME/.pyenv/bin:$PATH"`
	- `eval "$(pyenv init -)"` 
	- `eval "$(pyenv virtualenv-init -)"`
- restart your shell: `exec $SHELL`

# Installing pyenv (MacOS - brew)
- Homebrew is a package manager for MacOS. Copy this command into your terminal to install:
  ```
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```
- We will use pyenv to manage python environments. `brew install pyenv pyenv-virtualenv`

# Managing Python Versions and Virtualenvs with Pyenv
- Python projects usually specify which version of Python and other packages they require. To prevent version conflicts between different projects, it's useful to have virtual environments which give each project its own python installation. We can manage virtual environments with pyenv.
- Use pyenv to install the preferred version of python (this could be 3.11, or whatever your specific project requires.)
	- `pyenv install 3.11`
- Make a new virtual environment called 'learn-python' which uses 3.11 as its base. Activate the virtual environment.
	- `pyenv virtualenv 3.11 learn-python`
	- `pyenv activate learn-python`
- You can specify the local python version for any directory which will automatically activate the virtual environment. This is an efficient way to switch between projects which use different virtualenvs.
	- `pyenv local learn-python`

# Installing Jupyter Notebook
- pip install jupyter
- Windows WSL:
	- run `jupyter notebook --no-browser` and connect to the URL provided with your regular web browser 
- Other Platforms:
	- run `jupyter notebook`
