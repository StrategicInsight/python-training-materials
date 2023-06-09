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
	- `export PATH="$HOME/.pyenv/bin:$PATH" 
	- `eval "$(pyenv init -)"` 
	- `eval "$(pyenv virtualenv-init -)"`
- restart your shell: `exec $SHELL`

# Installing Jupyter Notebook
- pip install jupyter
- Windows WSL:
	- run `jupyter notebook --no-browser` and connect to the URL provided with your regular web browser 
- Other Platforms:
	- run `jupyter notebook`
