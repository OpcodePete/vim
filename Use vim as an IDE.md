# Use vim as an IDE

## Auto Pairs

Insert or delete brackets, parens, quotes in pair.

How to use

(automatic)

<br />
<br />

## vim-ctrlp

vim-ctrlp is a file finder in Vim. Use it to quickly open another file.

How to use

1. Start CtrlP with `ctrl-p`
2. Type until you find the file in the current or sub-directory
3. Open the file in your current buffer, a new split, or a new tab

<br />
<br />

## Universal Ctags

Universal Ctags is a tag generator.

vim supports tags natively. Tags allow a developer to put the cursor on a word, press `Ctrl+]` and jump to the definition.

To use Vim tags, vim relies on a tag generator to generate a tag file - an index file of language objects found in source files.

There are several popular tag generators:
- Ctags
- Exuberant Ctags
- Univeral Ctags

Universal Ctags is the most modern and best implementation.

<br />

How to use

**Generate a tags file**

```bash
# From the terminal
# In the project root directory, generate a tags file for all files recursively
ctags -R .

# In the current directory, generate a tags file for all c files
ctags *.c

Or run the above in vim with `:!`
```

<br />

**(Optional) Let vim know where the tags file is**

```bash
:set tags=/my/dir/tags
:set tags=/my/dir1/tags,/my/dir2/tags	# more than 1 tag file
```

<br />

**vim Commands**

| `:tag Classname`     | Jump to first definition of Classname           |
| -------------------- | ----------------------------------------------- |
| `<C-]>`              | Jump to definition                              |
| `g]`                 | See all definitions                             |
| `<C-T>`  `:pop`      | Go back to last tag                             |
| `<C-O> <C-I>`        | Back/forward                                    |
| `:tselect Classname` | Find definitions of Classname                   |
| `:tjump Classname`   | Find definitions of Classname (auto-select 1st) |
| `:tags`              | List tags stack                                 |

<br />
<br />

## vim-tagbar

Tagbar is a class outline viewer for vim. It provides an easy way to browse the tags of the current file and get an overview of its structure. It does this by creating a sidebar that displays the ctags-generated tags of the current file, ordered by their scope.

Tagbar works with Universal Ctags.

<br />

How to use

`F8` - Toggle Tagbar on/off

<br />
<br />

## commentary.vim

Comment out line(s) and block(s) of code

How to use

`gcc` - comment out line  
`gc` to comment out the target of a motion, e.g.`gcap` to comment out a paragraph  
`gc` in visual mode to comment out the selection  
`gc` in operator pending mode to target a comment  
`gcgc` uncomments a set of adjacent commented lines

<br />
<br />

## vim-fugitive

Vim plugin for Git.

How to use

**Configure username and email**

```bash
git configure --global user.name "Peter G"
git configure --global user.email "peterg@"
```

<br />

**Create a Git repository**

Visit a remote git host service, e.g. https://github.com/, https://about.gitlab.com/

Or create a repository locally

```bash
cd ~/
git init myproject
```

This will create a directory `~/myproject`

<br />

**Checkout a repository**

Create a working copy of a local repository

```bash
mkdir ~/myworkspaceHowTo
git clone username@host:myproject ~/myworkspace
git clone git@github.com:myusername/myproject.git ~/myworkspace
```

The local repository consists of three trees:

- `Working Directory` this holds the actual files
-	`Index` this acts as a staging area
-	`Head` points to the last commit

<br />

**Add changes (to version control)**

```bash
git add --all
git add <filename>
```

File(s) are now added to the `Index`

<br />

**Commit changes (locally)**

```bash
git commit -m "change decription here"
```

Files(s) are now committed to the `Head`

<br />

**Review changes**

This can be done before and after staging

```bash
git status		# Review change before and after adding staging
```

<br />

**Push changes (to repository)**

```bash
git push origin master
```

For the first push use `origin master`

Change `master` to desired branch to push to

If you have not cloned an existing repository and want to connect your repository to a remote server, you need to add it with

```bash
git remote add origin <server>
```

<br />

**Branch**

```bash
git checkout -b newfeature1		# Create a new branch
git checkout master				# Switch back to master
git branch -d newfeature1		# Delete branch
git push origin newfeature1		# Push branch to remote repository to make it available
```

<br />

**Update**

```bash
git pull				# Update local repo, i.e. fetches and merges remote changes
```

<br />

**Merge changes**

```bash
git merge branch_name	# Merge branch to master
git diff master			# Before merging review difference between branch and master

# When conflicts, merge conflicts manually by editing files, then mark as merged with
git add <filename>
```

<br />
<br />

## vim-gitgutter

Vim plugin for Git

```bash
:Git status
:Git add .
:Git commit -m "my commit msg here..."
```
<br />
<br />

## asyncrun.vim

How to use

```bash
:AsyncRun python %
```

or `F5` shortcut

<br />
<br />

## vim-ale

This plugin is an asynchronous linter (i.e. checking for syntax errors) - use it with flake8 and pylint. And also a formatter - use with google/yapf.

How to use

`F10` - Fix
`Save` - auto-fix

<br />

<br />
<br />

## coc.nvim

IDE for vim

How to use

`<Tab>` and `<Shift><Tab>` - navigate through completion list

<br />
<br />

## coc-python (Ubuntu only)

Ubuntu

To get intellisense (e.g. for import...)

```bash
In vim
:CocCommand python.setInterpreter
```

<br />
<br />

## vim-python-pep8-indent

This plugin enforces PEP8 indentation

How to use

`:verbose set indentexpr?` - verify plugin is working. It should return something like: *indentexpr=GetPythonPEPIndent(v:lnum)*

`python.condaPath`  :Path to the conda executable to use for activation (version 4.4+)., default: ""

<br />
<br />

## SimpylFold

Vim plugin providing simple, correct folding for Python

How to use

`zc` - close fold under the cursor
`zo` - open fold under the cursor

`zC` - close all folds under the cursor
`zo` - open all folds under the cursor

`{visual}zf` create a fold

`zd` - delete fold under the cursor
`zD` - delete all folds under the cursorlet g:gitgutter_git_executable = '/usr/bin/git' 
`zE` - eliminate all folds in the window

Notes: Think of the fold as a 'z' shaped paper-fold.

<br />
<br />
