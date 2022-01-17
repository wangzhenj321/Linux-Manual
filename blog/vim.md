### Basic use

```
<Esc> is the escape key or use <ctrl>[ sometimes written as <C-[>

vimtutor    : starts vim editing a copy of a tutorial file -- very good.
i           : insert mode. Next keys typed are inserted into the file.
<Esc>       : Escape from insert mode so you can navigate and use edit commands (stop selecting)
h j k l     : move cursor ( h: ←  j: ↓  k: ↑  l: → )
A           : Append at end of line
o           : Insert at new line below
u           : undo last command, again and again
x           : delete character under cursor
dw          : delete everything right from the cursor to the start of next word (and put it into the default register)
dd          : delete line (and put it into the default register)
p           : paste the default register

/myname     : search forward for myname

:wq         : write and quit
:x          : write and quit
:w filename : write a copy of the file you are editing as filename
:q!         : quit without saving even if changes were made!
:help       : display help
<Tab>       : use tab completion to scroll through commands that start with what you typed

<ctrl>+b    : previous page
<ctrl>+f    : next page
```

### Still basic

```
COPY PASTE  (for CUTting lines use dd as described above)
v           : visual mode -- use to select text with cursor movement or mouse
y           : use to yank (copy) what was selected
<Esc>       : esc gets you back to the main mode

^ w e $     : bigger movements: beginning of line, word, end of word, end of line

Modes:
 normal, insert and visual, there are others too
 <Esc>    takes you back to normal

Enter a number before a command to repeat it, examples:
   10w      : skip forward 10 words
   10dd     : delete 10 lines

Commands are case sensitive:
   c        : starts a change command
   C        : change to end of line (same as c$)
   ce       : change to end of word (a complete change command)
```

### Really useful

```
www.vim.org   : Visit frequently
comp.editors  : Vim dominated newsgroup
* # g* g#     : find word under cursor (forwards/backwards)
%             : match brackets {}[]()
matchit.vim   : % now matches tags <tr><td><script> etc
<C-N> <C-P>   : word completion in insert mode
<C-X><C-L>    : Line complete SUPER USEFUL
/<C-R><C-W>   : Pull <cword> onto search/command line
:set ignorecase : you nearly always want this
:set smartcase  : case-sensitive if search contains an uppercase character
:syntax on    : colour syntax in Perl,HTML,PHP etc
:h slash<C-D> : type control-D and get a list all help topics containing slash
    (plus use TAB for Help completion)
```

### Make it easy to update/reload vimrc

```
" source $MYVIMRC reloads the saved $MYVIMRC
:nmap <Leader>s :source $MYVIMRC

" opens $MYVIMRC for editing, or use :tabedit $MYVIMRC
:nmap <Leader>v :e $MYVIMRC

" <Leader> is \ by default, so those commands can be invoked by doing \v and \s
```

### Visual mode mappings

```
:vmap sb "zdi<b><C-R>z</b><Esc> : wrap <b></b> around visually selected text
:vmap st "zdi<?= <C-R>z ?><Esc> : wrap <?= ?> around visually selected text
```

### Exploring

```
:Ex     : file explorer note capital Ex
\be     : show buffer explorer (requires plugin)
:ls     : list of buffers(eg following)
:cd ..  : move to parent directory
```

### Great

```
guu     : lowercase line
gUU     : uppercase line
~       : invert case (upper->lower; lower->upper) of current character
gf      : open file name under cursor (SUPER)
ga      : display hex, ascii value of character under cursor
g8      : display hex value of utf-8 character under cursor
ggg?G   : rot13 whole file
xp      : swap next two characters around
CTRL-A,CTRL-X : increment, decrement next number on same line as the cursor
CTRL-R=5*5    : insert 25 into text
=             : (re)indent the text on the current line or on the area selected (SUPER)
=%            : (re)indent the current braces { ... }
G=gg          : auto (re)indent entire document
```

If you use Ctrl-V for paste, you will probably need to unmap CTRL-A first.

### Markers and moving about

```
'.       : jump to last modification line (SUPER)
`.       : jump to exact spot in last modification line
<C-O>    : retrace your movements in file (backward)
<C-I>    : retrace your movements in file (forward)
:ju(mps) : list of your movements {{help|jump-motions}}
:history : list of all your commands
```

### Abbreviations and maps

```
:map <F7>  :'a,'bw file            " Write the lines from mark a to mark b to 'file'
:map <F8>  :.w file<CR>            " Write the current line to 'file'
:map <F9>  :r file                 " Read text from 'file' and insert it below the current line
:map <F10> :w<CR>:!php %<CR>       " Write the file and run it through php
:ab php                            " list abbreviations beginning with php
:map \                             " list maps beginning with \
```

### For use in maps

```
<CR>     : carriage Return for maps
<Esc>    : Escape
<Leader> : normally \  change with :let mapleader = ","
<Bar>    : | pipe
```

### List registers

```
:reg     : display contents of all registers
"1p      : paste from register 1
```

### Execute command from buffer contents

```
"ayy@a   : execute the Vim command in the current line
yy@"     : same
```

### Get output from shell commands

```
:r!ls                 : reads in output of ls (use dir on Windows)
:r !grep "^ebay" file.txt  : read output of grep
:20,25 !rot13        : rot13 lines 20 to 25
:r!date              : insert date (use  date /T on Windows)
:.!sh                : execute contents of current line in buffer and capture the output

 Sorting with external sort
:%!sort -u           : contents of the current file is sorted and only unique lines are kept
:'v,'w!sort          : sort from line marked v thru lines marked w
:g/^$/;,/^$/-1!sort  : sort each block (note the crucial ;)

!1} sort             : sorts paragraph; this is issued from normal mode!)

 Entering !! in normal mode is translated to  :.!
 Appending a command sends the current line to the command replacing it with command's result
!!date              : Replace current line with date
!!which command     : Replace current line with the absolute path to command
!!tr -d AEIO        : translate current line deleting As, Es, Is, and Os from the current line

 You can also use ! on a visual selection. Select an area with one of the visualmode
 commands, and then type !command to pipe the whole selection through command.
This is equivalent to :'<,'>!command.
For example, after selecting multiple lines with visualmode:
!sort              : sort selected lines
!grep word         : keep only lines containing 'word' in the selected range.
```

### Multiple files

```
:wn           : write file and move to next (SUPER)
:bd           : remove file from buffer list (SUPER)
:sav php.html : Save current file as php.html and "move" to php.html
:sp fred.txt  : open fred.txt into a split
:e!           : return to unmodified file
:w /some/path/%:r   : save file in another directory, but with the same name
:e #          : edit alternative file
:args         : display argument list
:n            : next file in argument list
:prev         : previous file in argument list
:rew          : rewind to first file in argument list
:ls           : display buffer list
:bn           : next buffer
:bp           : previous buffer
:brew         : rewind to first buffer in buffer list
:tabe         : open new tab page (Ctrl-PgUp, Ctrl-PgDown for next/previous tab)
:tabm n       : move tab to position n (0=leftmost position)
```

### Recording

```
qa            : record keystrokes to register a
your commands
q             : quit recording
@a            : execute commands again
@@            : repeat
# editing a register/recording
"ap
<you can now see register contents, edit as required>
"add
@a
:%normal @a #execute the macro recorded in register a on all lines of the current file.
#or, with a visually selected set of lines:
:normal @a
```

### vimrc essentials

```
:set incsearch : jumps to search word as you type (annoying but excellent)
:set wildignore=*.o,*.obj,*.bak,*.exe
:syntax on : display syntactical elements by color based on filetype ( extension )
```

### References

1. [Best Vim Tips](https://vim.fandom.com/wiki/Best_Vim_Tips)
