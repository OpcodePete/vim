# Use vim as an IDE

## vim-ctrlp

Use `ctrl-p` to open another file in the current or sub-directory

<br />

## ctags

In terminal, generate a tags file

```bash
# In the project root directory, generate a tags file for all files recursively
ctags -R .

# In the current directory, generate a tags file for all c files
ctags *.c
```

Or run the above in vim with `:!`

(Optional: Let vim know where the tags file is)

```bash
:set tags=/my/dir/tags
:set tags=/my/dir1/tags,/my/dir2/tags	# more than 1 tag file
```

Commands

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

## vim-tagbar

`F8` - Toggle Tagbar on/off


<br />

## vim-commentary

`gcc` - comment out line
`gc` to comment out the target of a motion, e.g.`gcap` to comment out a paragraph
`gc` in visual mode to comment out the selection
`gc` in operator pending mode to target a comment


<br />

## vim-fugitive

**Configure username and email**

```bash
git configure --global user.name "Peter G"
git configure --global user.email "peterg@opcodestudios.com"
```

**Create a Git repository**

Visit a remote git host service, e.g. https://github.com/, https://about.gitlab.com/

Or create a repository locally

```bash
cd ~/
git init myproject
```

 This will create a directory `~/myproject`

**Checkout a repository**

Create a working copy of a local repository

```bash
mkdir ~/myworkspaceHowTo
git clone username@host:myproject ~/myworkspace
git clone git@github.com:myusername/myproject.git ~/myworkspace
```

The local repository consists of three trees:

​	`Working Directory` this holds the actual files

​	`Index` this acts as a staging area

​	`Head` points to the last commit

**Add changes (to version control)**

```bash
git add --all
git add <filename>
```

File(s) are now added to the `Index`

**Commit changes (locally)**

```bash
git commit -m "change decription here"
```

Files(s) are now committed to the `Head`

**Review changes**

This can be done before and after staging

```bash
git status		# Review change before and after adding staging
```

**Push changes (to repository)**

```bash
git push origin master
```

For the first push use `origin master`

Change `master` to desired branch to push to

vim-ale

If you have not cloned an existing repository and want to connect your repository to a remote server, you need to add it with

```bash
git remote add origin <server>
```

**Branch**

```bash
git checkout -b newfeature1		# Create a new branch
git checkout master				# Switch back to master
git branch -d newfeature1		# Delete branch
git push origin newfeature1		# Push branch to remote repository to make it available
```

**Update**

```bash
git pull				# Update local repo, i.e. fetches and merges remote changes
```

**Merge changes**

```bash
git merge branch_name	# Merge branch to master
git diff master			# Before merging review difference between branch and master

# When conflicts, merge conflicts manually by editing files, then mark as merged with
git add <filename>
```

<br />

## vim-ale

`F10` - Fix
`Save` - auto-fix

<br />

## coc.nvim

`<Tab>` and `<Shift><Tab>` - navigate through completion list

<br />

## coc-python (Ubuntu only)

Ubuntu

To get intellisense (e.g. for import...)

```bash
In vim
:CocCommand python.setInterpreter
```

<br />

## vim-python-pep8-indent

`:verbose set indentexpr?` - verify plugin is working. It should return something like: *indentexpr=GetPythonPEPIndent(v:lnum)*

`python.condaPath`  :Path to the conda executable to use for activation (version 4.4+)., default: ""

<br />

## SimpylFold

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

## asyncrun.vim

```bash
:AsyncRun python %
```

or `F5` shortcut

<br />

## vim-gitgutter

```bash
:Git status
:Git add .
:Git commit -m "my commit msg here..."
```
