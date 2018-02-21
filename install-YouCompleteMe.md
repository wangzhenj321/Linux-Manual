First carefully read the [installation instructions](http://valloric.github.io/YouCompleteMe/#installation) for your OS. We recommend you use the supplied *install.py*.

Next check the [User Guide](http://valloric.github.io/YouCompleteMe/#user-guide) section on the semantic completer that you are using. For C/C++/Objective C, you must read [this section](http://valloric.github.io/YouCompleteMe/#c-family-semantic-completion).

Finally, check the [FAQ](http://valloric.github.io/YouCompleteMe/#faq).

**Table of Contents**

- [Prerequisites](#prerequisites)
	
- [Install YouCompleteMe with Vundle](#install-youcompleteme-with-vundle)
	
- [Run *install.py*](#run-installpy)
	
- [References](#references)

## Prerequisites

**Ubuntu Linux x64**

These instructions (using *install.py*) are the quickest way to install YouCompleteMe, however they may not work for everyone. If the following instructions don't work for you, check out the [full installation guide](http://valloric.github.io/YouCompleteMe/#full-installation-guide).

Make sure you have Vim 7.4.1578 with Python 2 or Python 3 support. Ubuntu 16.04 and later have a Vim that's recent enough. You can see the version of Vim installed by running `vim --version`. If the version is too old, you may need to [compile Vim from source](https://github.com/Valloric/YouCompleteMe/wiki/Building-Vim-from-source) (don't worry, it's easy).

## Install YouCompleteMe with Vundle

**Remember:** YCM is a plugin with a compiled component. If you **update** YCM using Vundle and the ycm_core library APIs have changed (happens rarely), YCM will notify you to recompile it. You should then rerun the install process.

1. Set up Vundle:
	```
	git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
	```
2. Configure Plugins:
	Put this at the top of your .vimrc to use Vundle.
	```
	set nocompatible
	filetype off

	set rtp+=~/.vim/bundle/Vundle.vim

	call vundle#begin()
	Plugin 'VundleVim/Vundle.vim'
	Plugin 'Valloric/YouCompleteMe'
	call vundle#end()

	filetype plugin indent on
	```
3. Install Plugins:
	To install from command line: `vim +PluginInstall +qall`

## Run *install.py*

1. Install development tools and CMake:
	```
	sudo apt-get install build-essential cmake
	```
2. Make sure you have Python headers installed:
	```
	sudo apt-get install python-dev python3-dev
	```
3. Install the latest version of libclang:
	```
	apt-get install llvm-3.9 clang-3.9 libclang-3.9-dev libboost-all-dev
	```
4. Compiling YCM with semantic support for C-family languages:
	```
	cd ~/.vim/bundle/YouCompleteMe
	./install.py --clang-completer
	```

## Configure *.ycm_extra_conf.py*

Before configuring the *.ycm_extra_conf.py*, the following error message will show in the bottom of **vim** if a C-family file is opened such as *helloworld.cpp*.

#### Use the template *.ycm_extra_conf.py*
1. Copy *.ycm_extra_conf.py*
	```
	cp ~/.vim/bundle/YouCompleteMe/third_party/ycmd/examples/.ycm_extra_conf.py ~/.vim/
	```
2. Edit *.vimrc*
	Add `let g:ycm_global_ycm_extra_conf='~/.vim/.ycm_extra_conf.py'` into *.vimrc*.

#### Use a compilation database


## References

1. [YouCompleteMe](http://valloric.github.io/YouCompleteMe/)
2. [VundleVim](https://github.com/VundleVim/Vundle.vim#about)
3. [一步一步带你安装史上最难安装的 vim 插件 —— YouCompleteMe](https://www.jianshu.com/p/d908ce81017a)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMjU3MTcwMTJdfQ==
-->