## DESCRIPTION

update-alternatives creates, removes, maintains and displays information about the symbolic links comprising the Debian alternatives system.

> **Debian alternatives system**
> 
> It is possible for several programs fulfilling the same or similar functions to be installed on a single system at the same time.  For example, many systems have several text editors installed at once. This gives choice to the users of a system, allowing each to use a different editor, if desired, but **makes it difficult for a program to make a good choice for an editor to invoke if the user has not specified a particular preference**.
> 
> Debian's alternatives system aims to solve this problem. A generic name in the filesystem is shared by all files providing interchangeable functionality. The alternatives system and the system administrator together determine which actual file is referenced by this generic name. For example, if the text editors `ed` and `nvi` are both installed on the system, the alternatives system will cause the generic name `/usr/bin/editor` to refer to `/usr/bin/nvi` by default. The system administrator can override this and cause it to refer to /usr/bin/ed instead, and the alternatives system will not alter this setting until explicitly requested to do so.

The generic name is not a direct symbolic link to the selected alternative. Instead, it is a symbolic link to a name in the **alternatives directory**(default to `/etc/alternatives/`), which in turn is a symbolic link to the actual file referenced. This is done so that the system administrator's changes can be confined within the `/etc` directory: the FHS (q.v.) gives reasons why this is a Good Thing.

```bash
# generic name
$ ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 Oct 16  2018 /usr/bin/java -> /etc/alternatives/java
# alternative name
$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 26 Nov 29 00:13 /etc/alternatives/java -> /opt/jdk1.8.0_231/bin/java
# the actual file referenced
$ ls -l /opt/jdk1.8.0_231/bin/java
-rwxr-xr-x 1 wang wang 8464 Oct  5 19:10 /opt/jdk1.8.0_231/bin/java
```

It is often useful for a number of alternatives to be synchronized, so that they are changed as a group; for example, when several versions of the `vi` editor are installed, the man page referenced by `/usr/share/man/man1/vi.1` should correspond to the executable referenced by `/usr/bin/vi`. `update-alternatives` handles this by means of master and slave links; when the master is changed, any associated slaves are changed too. A master link and its associated slaves make up a link group.

Each **link group** is, at any given time, in one of two modes: **automatic** or **manual**. When a group is in automatic mode, the alternatives system will automatically decide, as packages are installed and removed, whether and how to update the links. In manual mode, the alternatives system will retain the choice of the administrator and avoid changing the links (except when something is broken).

## COMMANDS

- **`--install link name path priority [--slave link name path]...`**

    Add a group of alternatives to the system. ***link*** is the generic name for the master link, ***name*** is the name of its symlink in the alternatives directory, and ***path*** is the alternative being introduced for the master link. The arguments after `--slave` are the generic name, symlink name in the alternatives directory and the alternative path for a slave link. Zero or more `--slave` options, each followed by three arguments, may be specified. Note that the master alternative must exist or the call will fail. However if a slave alternative doesn't exist, the corresponding slave alternative link will simply not be installed (a warning will still be displayed). If some real file is installed where an alternative link has to be installed, it is kept unless `--force` is used.

    If the alternative name specified exists already in the alternatives system's records, the information supplied will be added as a new set of alternatives for the group. Otherwise, a new group, set to automatic mode, will be added with this information. If the group is in automatic mode, and the  newly added alternatives' priority is higher than any other installed alternatives for this group, the symlinks will be updated to point to the newly added alternatives.

- **`--set name path`**

    Set the program ***path*** as alternative for ***name***. This is equivalent to `--config` but is non-interactive and thus scriptable.

- **`--remove name path`**

    Remove an alternative and all of its associated slave links. ***name*** is a name in the alternatives directory, and ***path*** is an absolute filename to which ***name*** could  be linked. If ***name*** is indeed linked to ***path***, ***name*** will be updated to point to another appropriate alternative (and the group is put back in automatic mode), or removed if there is no such alternative left.  Associated slave links will be updated or removed, correspondingly. If the link is not currently pointing to ***path***, no links are changed; only the information about the alternative is removed.

- **`--remove-all name`**

    Remove all alternatives and all of their associated slave links. ***name*** is a name in the alternatives directory.

- **`--display name`**

    Display information about the link group. Information displayed includes the group's mode (auto or manual), the master and slave links, which alternative the master link currently points to, what other alternatives are available (and their corresponding slave alternatives), and the highest priority alternative currently installed.
    
    ```bash
    $ update-alternatives --display java
    java - manual mode
      link best version is /usr/bin/gij-5
      link currently points to /opt/jdk1.8.0_231/bin/java
      link java is /usr/bin/java
      slave java.1.gz is /usr/share/man/man1/java.1.gz
    /opt/jdk1.8.0_231/bin/java - priority 0
    /usr/bin/gij-5 - priority 1050
      slave java.1.gz: /usr/share/man/man1/gij-5.1.gz
    ```

- **`--query name`**

    Display information about the link group like `--display` does, but in a machine parseable way.
    
    ```bash
    $ update-alternatives --query java
    Name: java
    Link: /usr/bin/java
    Slaves:
     java.1.gz /usr/share/man/man1/java.1.gz
    Status: manual
    Best: /usr/bin/gij-5
    Value: /opt/jdk1.8.0_231/bin/java
    
    Alternative: /opt/jdk1.8.0_231/bin/java
    Priority: 0
    Slaves:
    
    Alternative: /usr/bin/gij-5
    Priority: 1050
    Slaves:
     java.1.gz /usr/share/man/man1/gij-5.1.gz
    ```

- **`--config name`**

    Show available alternatives for a link group and allow the user to interactively select which one to use. The link group is updated.

## Example: Choose gcc and g++ version

***References:*** https://askubuntu.com/questions/26498/choose-gcc-and-g-version

First erased the current update-alternatives setup for gcc and g++:

```
sudo update-alternatives --remove-all gcc 
sudo update-alternatives --remove-all g++
```

### Install Packages

It seems that both gcc-4.3 and gcc-4.4 are installed after install build-essential. However, we can explicitly install the following packages:

```
sudo apt-get install gcc-4.3 gcc-4.4 g++-4.3 g++-4.4
```

### Install Alternatives

Symbolic links cc and c++ are installed by default. We will install symbol links for gcc and g++, then link cc and c++ to gcc and g++ respectively.

```
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.3 10
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.4 20

sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.3 10
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-4.4 20

sudo update-alternatives --install /usr/bin/cc cc /usr/bin/gcc 30
sudo update-alternatives --set cc /usr/bin/gcc

sudo update-alternatives --install /usr/bin/c++ c++ /usr/bin/g++ 30
sudo update-alternatives --set c++ /usr/bin/g++
```

### Configure Alternatives

The last step is configuring the default commands for gcc, g++. It's easy to switch between 4.3 and 4.4 interactively:

```
sudo update-alternatives --config gcc
sudo update-alternatives --config g++
```
