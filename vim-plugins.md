## [vim-pathogen](https://github.com/tpope/vim-pathogen)

Copy and paste the following into your terminal/shell:

```
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```

Add this to your vimrc:

```
execute pathogen#infect()
```

## [auto-pairs](https://github.com/jiangmiao/auto-pairs)

If you are using ***pathogen***:

```
git clone git://github.com/jiangmiao/auto-pairs.git ~/.vim/bundle/auto-pairs
```

## [nerdtree](https://github.com/scrooloose/nerdtree)

If you are using ***pathogen***:

```
git clone https://github.com/scrooloose/nerdtree.git ~/.vim/bundle/nerdtree
```

#### F.A.Q

> How can I open a NERDTree automatically when vim starts up?

Stick this in your vimrc: `autocmd vimenter * NERDTree`


> How can I open NERDTree automatically when vim starts up on opening a directory?

```
autocmd StdinReadPre * let s:std_in=1
autocmd VimEnter * if argc() == 1 && isdirectory(argv()[0]) && !exists("s:std_in") | exe 'NERDTree' argv()[0] | wincmd p | ene | endif
```

#### Shortcuts

- open NERDTree: `:NERDTree`
- close NERDTree: `:q`
- switch between NERDTree and file opened windows: `ctrl + w + w`

## [tagbar](https://github.com/majutsushi/tagbar)

1. Tagbar requires Vim 7.0 and Exuberant ctags 5.5.
    ```
    sudo apt install exuberant-ctags
    ```
2. If you are using ***pathogen***:
    ```
    cd ~/.vim/bundle
    git clone https://github.com/majutsushi/tagbar.git
    ```
3. Toggle the code browser between visible and hidden using `:TagbarToggle`
