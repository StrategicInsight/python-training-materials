# Installing Python on Windows
- [Installing WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
	- Run Windows Powershell as an administrator 
	- run `wsl --install -d Ubuntu`
		- (if you have to start over, you can remove this installation with `wsl --unregister Ubuntu`)
- Installing Python
	- Open your Ubuntu terminal by running the wsl app in Windows
	- Update apt: `sudo apt update && sudo apt upgrade
	- Add the deadsnakes apt repository: `sudo add-apt-repository ppa:deadsnakes/ppa`
	- Install python: `sudo apt install python3.11`
	- Add the python path:
		- edit .bashrc with `nano .bashrc` 
		- add this line to .bashrc:
		   `export PATH="$PATH:/home/<your_linux_username>/.local/bin"`
		- save by writing out and exiting.
		- restart your terminal or run `source ~/.bashrc`
	- install pip: `sudo apt install python3-pip`

# Installing pyenv
- Install the pyenv build dependencies: 
`sudo apt-get update; sudo apt-get install --no-install-recommends make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev`
- install pyenv: `curl [https://pyenv.run](https://pyenv.run) | bash`
- Add the following lines to your shell configuration file (e.g. `~/.bashrc` for bash or `~/.zshrc` for zsh):
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
