# For Ubuntu 16.04

![](../img/oh-my-zsh/zsh_on_ubuntu.png?raw=true)

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

1. Pre-installed plugins

    - `git`: adds many useful aliases and functions for using `git`

    - `colored-man-pages`: gives color highlighting to your `man` pages

    - `extract`: extracts the archive file of a wide variety of archive filetypes

    - `z`: jump around

        - Put something like this `. /path/to/z.sh` in your `$HOME/.bashrc` or `$HOME/.zshrc`

        - `cd` around for a while to build up the db

2. Custom plugins

    - `zsh-syntax-highlighting`: syntax highlighting

    - `zsh-autosuggestions`: command completion

    - `git-open`: opens the repo website (GitHub, GitLab, Bitbucket) in your browser

## Update

Get oh-my-zsh updates with running this command:

```
upgrade_oh_my_zsh
```

> Since the changes have been made to the file `~/.oh-my-zsh/themes/agnoster.zsh-theme` to improve the zsh prompt, with this way to update it will always redirect to a new temporary branch and show the merge conflict while rebasing. I don't know how to smoothly and succussfully to fix this merge conflict. As for me, it's better to do update manually as follows:
> 
> ```
> cd ~/.oh-my-zsh/
> git fetch origin
> git merge origin/master # manually fix merge conflict
> ```

## References

1. [Oh-My-Zsh! A Work of CLI Magic — Tutorial for Ubuntu](https://medium.com/wearetheledger/oh-my-zsh-made-for-cli-lovers-installation-guide-3131ca5491fb)

2. [oh-my-zsh 插件](https://hufangyun.com/2017/zsh-plugin/)

# For MacOS

![](../img/oh-my-zsh/zsh_on_mac.png?raw=true)

The installation for MacOS is almost same as Ubuntu 16.04, but the following exceptions should be handled.

1. Install and use [iTerm2](https://www.iterm2.com/) instead of Mac's terminal.

2. Install [powerline fonts](https://github.com/powerline/fonts) and set font of iTerm2 to one type of powerline fonts (Preferences -> Profiles -> Text -> Font & Non-ASCII Font).

    ![](../img/oh-my-zsh/set_powerline_font.png?raw=true)

3. Download [iTerm2 color schemes](https://github.com/mbadolato/iTerm2-Color-Schemes) and set color of iTerm2 to **Dracula** (Preferences -> Profiles -> Colors -> Color Presets -> Import **Dracula** -> reopen Color Presets to select **Dracula**).

    ![](../img/oh-my-zsh/set_Dracula_color_scheme.png?raw=true)
