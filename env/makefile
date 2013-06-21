homebrew:
	echo "Install Homebrew"
	ruby -e "$$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
	brew doctor

packages:
	echo "Install Packages"
	brew install ack ctags cmake tmux tree node nmap ncdu python

ipython:
	sudo easy_install readline ipython

pythonz:
	curl -kL https://raw.github.com/saghul/pythonz/master/pythonz-install | bash

virtualenv:
	sudo pip install virtualenv virtualenvwrapper
	mkdir -p ~/.envs
	source /usr/local/bin/virtualenvwrapper.sh

python_config:
	echo "">>~/.zshrc
	echo "[[ -s $$HOME/.pythonz/etc/bashrc ]] && source $$HOME/.pythonz/etc/bashrc">>~/.zshrc
	echo "export WORKON_HOME=~/.envs">>~/.zshrc
	echo "source /usr/local/bin/virtualenvwrapper.sh">>~/.zshrc

python: ipython pythonz virtualenv python_config
	echo "Making Python"
