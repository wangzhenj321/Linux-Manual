## Introduction

**Oh My Zsh** is a delightful, open source, community-driven framework for managing your `Zsh` configuration. It comes bundled with a ton of helpful functions, helpers, plugins, themes, and a few things that make you shout “Oh My ZSH!”

## Installation

1. install prerequisite packages:

    ```
    sudo apt install git-core zsh
    ```

2. install Oh-My-Zsh from Robby Russell’s repository via `wget`:

    ```
    sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
    ```

3. install the `fonts-powerline` to spice up your CLI with icons:

    ```
    sudo apt install fonts-powerline
    ```

4. change theme from **robbyrussell** to **agnoster** for the legendary Oh-My-Zsh theme:

    ```
    vim ~/.zshrc
    ```

    Find the **ZSH_THEME** variable and change it: `ZSH_THEME="agnoster"`. I don’t like it that the theme shows my username and host. To get rid of this by editing the theme file of **agnoster**:
    
    ```
    vim ~/.oh-my-zsh/themes/agnoster.zsh-theme
    ```
    
    Now we can change the "Main prompt". We don’t need to **prompt_context** in the function `build_prompt()`. Just comment out this line or remove it. At last, change the `PROMPT` variable to `$(build_prompt)`. To actually see the theme, you have to source your .zshrc file like this: `source ~/.zshrc`. And it seems the `zsh` will become the default shell.

## Plugins

All plugins listed on the [plugins Github page](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins) are pre-installed with Oh-My-Zsh at `~/.oh-my-zsh/plugins`. Custom plugins can be installed at `~/.oh-my-zsh/custom/plugins`. To use a plugin, you can simply add it to the plugins list in your `~/.zshrc` file. Add wisely, as too many plugins slow down shell startup. Leave a blank between each plugin.

**Popular plugins:**

- `git`: adds many useful aliases and functions for using `git`

- `colored-man-pages`: gives color highlighting to your `man` pages

- `zsh-syntax-highlighting`: syntax highlighting

- `zsh-autosuggestions`: command completion

- `git-open`: opens the repo website (GitHub, GitLab, Bitbucket) in your browser

- `extract`: extracts the archive file of a wide variety of archive filetypes

- `z`: jump around

## References

1. [Oh-My-Zsh! A Work of CLI Magic — Tutorial for Ubuntu](https://medium.com/wearetheledger/oh-my-zsh-made-for-cli-lovers-installation-guide-3131ca5491fb)

2. [oh-my-zsh 插件](https://hufangyun.com/2017/zsh-plugin/)
