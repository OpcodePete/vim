# Vim Cheat sheet

**Navigate**

| `h` `j` `k` `l`     | Arrow keys        |
| ------------------- | ----------------- |
| `<C-U>` */* `<C-D>` | Page up/page down |

**Words**

| `b` */* `w`  | Previous/next word        |
| ------------ | ------------------------- |
| `e` */* `ge` | Previous/next end of word |
| %            | Toggle between brackets   |

**Line**

| `0` *(zero)*                                                 | Start of line                      |
| ------------------------------------------------------------ | ---------------------------------- |
| `^`                                                          | Start of line *(after whitespace)* |
| `$**Buffers**<br/><br/>List of current buffers<br/><br/>```bash<br/>:buffers<br/>:ls<br/>:files<br/>```<br/><br/><br/><br/>Open a file in a new buffer<br/><br/>```bash<br/>:edit ../myFile.pl<br/>```<br/><br/><br/><br/>Open an existing buffer<br/><br/>```bash<br/>:buffer <tab><br/>:buffer 2<br/>:buffer hello.cpp<br/>```<br/><br/><br/><br/>Create a new buffer<br/><br/>```bash<br/>:bnew<br/>```<br/><br/><br/><br/>Move to a buffer<br/><br/>```bash<br/># Move to a specific buffer (for enhanced tab completion use set wildmenu in .vimrc)<br/>:b myfile<br/><br/># Move to the next buffer<br/>:bnext<br/>:bn<br/><br/># Move to the previous buffer<br/>:bprevious<br/>:bp<br/><br/># Move to the first buffer<br/>:bfirst<br/>:bf<br/><br/># Move to the last buffer<br/>:blast<br/>:bl<br/><br/># Move to last visited buffer<br/># (Use it to switch quickly between two files)<br/>:b%<br/>```<br/><br/><br/><br/>Delete a buffer<br/><br/>```bash<br/>:bdelete f1.txt<br/>:bdelete 4<br/>```<br/><br/><br/><br/>Sessions<br/><br/>```bash<br/># Save session<br/># Save the current open file buffers and settings to ~/today.ses<br/>:mksession! ~/today.ses<br/><br/># Load session (no hassle remembering where you left off yesterday)<br/>vim -S ~/today.ses<br/>```<br/><br/><br/><br/>**Windows**<br/><br/>Open an existing buffer in a `split` or `vsplit`<br/><br/>```bash<br/>:split <tab><br/>:vsplit 2<br/>:split hello.cpp<br/>```<br/><br/><br/><br/>Switch between splits<br/><br/>```bash<br/>Ctrl-W h	" switch to left window<br/>Ctrl-W l	" switch to down window<br/>Ctrl-W j	" switch to up window<br/>Ctrl-W k	" switch to right window<br/>Ctrl-W w	" switch to next window clockwise<br/>```<br/><br/><br/><br/>Split the window<br/><br/>```bash<br/>:split			" split the current window horizontally<br/>:vertical split	" split the current window vertically<br/>```<br/><br/><br/><br/>Close the current window<br/><br/>```bash<br/>Ctrl-W c<br/>```<br/><br/><br/><br/>Close all windows except the current window<br/><br/>```bash<br/>Ctrl-W o<br/>```<br/><br/><br/><br/>Open each file in it's own split<br/><br/>```bash<br/>vim -o peter1.cpp peter2.cpp<br/>vim -O peter1.cpp peter2.cpp<br/>```<br/><br/><br/><br/>Open all buffers in windows<br/><br/>```bash<br/>:sball<br/>:vertical sball<br/>```` | End of line                        |

**Character**

| `fc` | Go forward to character `c`  |
| ---- | ---------------------------- |
| `Fc` | Go backward to character `c` |

**Document**

| `gg` | First line     |
| ---- | -------------- |
| `G`  | Last line      |
| `:n` | Go to line `n` |
| `nG` | Go to line `n` |

**Window**

| `zz` | Center this line         |
| ---- | ------------------------ |
| `H`  | Move to top of screen    |
| `M`  | Move to middle of screen |
| `L`  | Move to bottom of screen |



**Editing**

| `a`     | Append                              |
| ------- | ----------------------------------- |
| `i`     | Insert                              |
| `o`     | Next line                           |
| `O`     | Previous line                       |
| `s`     | Delete char and insert              |
| `S`     | Delete line and insert              |
| `C`     | Delete until end of line and insert |
| `r`     | Replace one character               |
| `R`     | Enter Replace mode                  |
| `u`     | Undo changes                        |
| `<C-R>` | Redo changes                        |



**Clipboard**

| `x`  | Delete character    |
| ---- | ------------------- |
| `dd` | Delete line *(Cut)* |
| `yy` | Yank line *(Copy)*  |
| `yw` | Yank word (Copy)    |
| `p`  | Paste               |
| `P`  | Paste before        |



**Modes**

**Command**

| `Esc` | Enter command mode |
| ----- | ------------------ |
|       |                    |

**Insert**

| `i`  | Enter insert mode |
| ---- | ----------------- |
|      |                   |

**Visual**

| `v`     | Enter visual mode       |
| ------- | ----------------------- |
| `V`     | Enter visual line mode  |
| `<C-V>` | Enter visual block mode |

In visual mode

| `d` */* `x` | Delete selection        |
| ----------- | ----------------------- |
| `s`         | Replace selection       |
| `y`         | Yank selection *(Copy)* |



**Exiting**

| `:qa`          | Close all files                  |
| -------------- | -------------------------------- |
| `:qa!`         | Close all files, abandon changes |
| `:w`           | Save                             |
| `:wq` */* `:x` | Save and close file              |
| `:q`           | Close file                       |
| `:q!`          | Close file, abandon changes      |
| `ZZ`           | Save and quit                    |
| `ZQ`           | Quit without checking changes    |



**Buffers**

| `:buffers`  `:ls`  `:files`                       | List of current buffers |
| ------------------------------------------------- | ----------------------- |
| `:buffer <tab>`  `:buffer 2`  `:buffer hello.cpp` | Open existing buffer    |
| `:bnew`                                           | Create a new buffer     |
| `:buffer <tab>`  `:buffer 2`  `:buffer hello.cpp` | Delete a buffer         |

Move to buffer

| `:b myfile`         | Move to a specific buffer                                    |
| ------------------- | ------------------------------------------------------------ |
| `:bnext`  `:bn`     | Move to next buffer                                          |
| `:bprevious`  `:bp` | Move to previous buffer                                      |
| `:bfirst`  `:bf`    | Move to first buffer                                         |
| `:blast`  `:bl`     | Move to last buffer                                          |
| `b%`                | Move to last visited buffer (quickly switch between two files) |



**Tab pages**

| `:tabedit [file]` | Edit file in a new tab         |
| ----------------- | ------------------------------ |
| `:tabfind [file]` | Open file if exists in new tab |
| `:tabclose`       | Close current tab              |
| `:tabs`           | List all tabs                  |
| `:tabfirst`       | Go to first tab                |
| `:tablast`        | Go to last tab                 |
| `:tabn `          | Go to next tab                 |
| `:tabp `          | Go to previous tab             |



**Operators**

Usage

Operators let you operate in a range of text (defined by *motion*). These are performed in normal mode.

| `d`      | `w`    |
| -------- | ------ |
| Operator | Motion |

Operators list

| `d`  | Delete                          |
| ---- | ------------------------------- |
| `y`  | Yank *(copy)*                   |
| `c`  | Change *(delete then insert)*   |
| `>`  | Indent right                    |
| `<`  | Indent left                     |
| `g~` | Swap case                       |
| `gU` | Uppercase                       |
| `gu` | Lowercase                       |
| `!`  | Filter through external program |

Examples

Combine operators with *motions* to use them.

| `d`*d*                 | *(repeat the letter)* Delete current line |
| ---------------------- | ----------------------------------------- |
| `d`*w*                 | Delete to next word                       |
| `d`*b*                 | Delete to beginning of word               |
| *2*`dd`                | Delete 2 lines                            |
| `d`*ip*                | Delete a text object *(inside paragraph)* |
| *(in visual mode)* `d` | Delete selection                          |



**Case**

| `~`   | Toggle case (Case => cASE)           |
| ----- | ------------------------------------ |
| `gU`  | Uppercase                            |
| `gu`  | Lowercase                            |
| `gUU` | Uppercase current line (also `gUgU`) |
| `guu` | Lowercase current line (also `gugu`) |

Do these in visual or normal mode.



**Misc**

| `.`  | Repeat last command                       |
| ---- | ----------------------------------------- |
| `]p` | Paste under the current indentation level |



**Spell checking**

| `:set spell spelllang=en_us` | Turn on US English spell checking                      |
| ---------------------------- | ------------------------------------------------------ |
| `]s`                         | Move to next misspelled word after the cursor          |
| `[s`                         | Move to previous misspelled word before the cursor     |
| `z=`                         | Suggest spellings for the word under/after the cursor  |
| `zg`                         | Add word to spell list                                 |
| `zw`                         | Mark word as bad/mispelling                            |
| `zu` / `C-X (Insert Mode)`   | Suggest words for bad word under cursor from spellfile |





### Vim Buffers

**Buffers**

List of current buffers

```bash
:buffers
:ls
:files
```



Open a file in a new buffer

```bash
:edit ../myFile.pl
```



Open an existing buffer

```bash
:buffer <tab>
:buffer 2
:buffer hello.cpp
```



Create a new buffer

```bash
:bnew
```



Move to a buffer

```bash
# Move to a specific buffer (for enhanced tab completion use set wildmenu in .vimrc)
:b myfile

# Move to the next buffer
:bnext
:bn

# Move to the previous buffer
:bprevious
:bp

# Move to the first buffer
:bfirst
:bf

# Move to the last buffer
:blast
:bl

# Move to last visited buffer
# (Use it to switch quickly between two files)
:b%
```



Delete a buffer

```bash
:bdelete f1.txt
:bdelete 4
```



Sessions

```bash
# Save session
# Save the current open file buffers and settings to ~/today.ses
:mksession! ~/today.ses

# Load session (no hassle remembering where you left off yesterday)
vim -S ~/today.ses
```



**Windows**

Open an existing buffer in a `split` or `vsplit`

```bash
:split <tab>
:vsplit 2
:split hello.cpp
```



Switch between splits

```bash
Ctrl-W h	" switch to left window
Ctrl-W l	" switch to down window
Ctrl-W j	" switch to up window
Ctrl-W k	" switch to right window
Ctrl-W w	" switch to next window clockwise
```



Split the window

```bash
:split			" split the current window horizontally
:vertical split	" split the current window vertically
```



Close the current window

```bash
Ctrl-W c
```



Close all windows except the current window

```bash
Ctrl-W o
```



Open each file in it's own split

```bash
vim -o peter1.cpp peter2.cpp
vim -O peter1.cpp peter2.cpp
```



Open all buffers in windows

```bash
:sball
:vertical sball
```





### Vim make and quickfix

**Create make file**

Create a make file in the project folder

```bash
touch makefile
```

A typical make file

```bash
all:
	clang++-7 hello_world.cpp -o hello_world
```

```bash
myapp:
    g++ -o myapp -std=c++14 -Wall -Werror -Wpedantic ./myapp.cpp
```

Note: Recipe commands (i.e. lines) have to be indented by a single `tab`. GNU Make is an old school program and is not forgiving in this regard.



**Compile in Vim using a make file**

```bash
:make
```

This runs make and fills up the *Quickfix* buffer with the error output (if errors exist).



**Open Quickfix window**

```bash
:copen
```

Navigate the Quickfix window and press `Enter` on any error or warning.



Jump between the editor window and the Quickfix window

```bash
Ctrl+w+w
```



**Quickfix Vim commands**

```bash
# Open the quickfix list in a window
:copen

# Open the quickfix list window only if there are errors
:cwindow :cw

# Close the quickfix list window
:cclose :ccl

# Move between your errors/matches
:cnext :cn
:cprev :cp

# Go to the first and last error/matches respectively
:cfirst :cnf
:clast

# Display the current error/match
:cc
```
