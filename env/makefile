ENV_PATH = $$(pwd)
ROOT = $$(dirname $(ENV_PATH))

homebrew:
	echo "Install Homebrew"
	ruby -e "$$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
	brew doctor

packages:
	echo "Install Packages"
	brew install ack ctags cmake tmux tree node nmap ncdu python vim tig

z:
	echo "">>~/.zshrc
	echo ". $(ROOT)/packages/z/z.sh">>~/.zshrc
	ln -s $(ROOT)/packages/z/z.1 /usr/local/share/man/man1/z.1

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
	echo "export VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python">>~/.zshrc
	echo "source /usr/local/bin/virtualenvwrapper.sh">>~/.zshrc

tmux_config:
	-[[ -e ~/.tmux.conf ]] && mv ~/.tmux.conf ~/.tmux.conf.bak
	ln -s $(ROOT)/packages/tmux/tmux.conf ~/.tmux.conf

vim_config:
	-[[ -e ~/.vimrc ]] && mv ~/.vimrc ~/.vimrc.bak
	-[[ -e ~/.vim ]] && mv ~/.vim ~/.vim.bak
	ln -s $(ROOT)/packages/vim/vimrc ~/.vimrc
	ln -s $(ROOT)/packages/vim ~/.vim

zsh_config:
	-[[ -e ~/.zshrc ]] && mv ~/.zshrc ~/.zshrc.bak
	cp $(ROOT)/packages/zsh/zshrc ~/.zshrc
	-[[ ! -e ~/.oh-my-zsh ]] && ln -s $(ROOT)/packages/zsh/oh-my-zsh ~/.oh-my-zsh

node_config:
	echo "">>~/.zshrc
	echo "export PATH=\"$$PATH:/usr/local/share/npm/bin/\"">>~/.zshrc

python: ipython pythonz virtualenv python_config
	echo "Making Python"

config: zsh_config tmux_config vim_config python_config node_config
	echo "Making Config"

clean_bak:
	find . -name "*.bak" -depth 1 | xargs rm -f

extra:
	echo "">>~/.zshrc
	echo ". $(ROOT)/extra/linux-alias">>~/.zshrc
