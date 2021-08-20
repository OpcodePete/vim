# Setup vim as an IDE

This is a step by step installation guide to add plug-ins to include additional features for:
- General editing,
- Geneal software development, and
- Python development


<br />

## Theme

**onedark.vim**

A dark Vim/Neovim color scheme for the GUI and 16/256/true-color terminals, based on FlatColor, with colors inspired by the excellent One Dark syntax theme for the Atom text editor.

Install theme
```bash
# Download the repo
git clone https://github.com/joshdick/onedark.vim

# Copy the following files:
cp ~/onedark.vim/colors/onedark.vim ~/.vim/colors/
cp ~/onedark.vim/autoload/onedark.vim ~/.vim/autoload/
```

Include in .vimrc
```bash
"Use 24-bit (true-color) mode in Vim/Neovim when outside tmux.
if (has("termguicolors"))
  set termguicolors
endif

if &term =~ '256color'
    " disable Background Color Erase (BCE) so that color schemes
    " render properly when inside 256-color tmux and GNU screen.
    " see also http://snk.tuxfamily.org/log/vim-256color-bce.html
    set t_ut=
endif
set term=xterm-256color
colorscheme onedark   
```

<br />
<br />

## Plugin manager

Install vim-plug
```bash
wget -P ~/.vim/autoload/ https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
<br />
<br />


## General plugins

**vim-airline**

Lean & mean status/tabline for vim that's light as air.

Install

```bash
~/.vimrc
Plug 'powerline/powerline-fonts'
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'

:PlugInstall
```

Configure

```bash
~/.vimrc
let g:airline_theme='onedark'
let g:airline#extensions#coc#enabled = 1
let g:airline_powerline_fonts = 1

#IMPORTANT - Ensure the General section includes the following line:
set encoding=utf-8
```

Fonts

To get vim-airline to display arrows, install the patched powerline fonts and use them

```bash
# List all Roboto fonts
fc-list | grep Roboto

# Copy the newly installed patched powerline fonts to the above location
cd /usr/share/fonts/TTF/
sudo cp /home/peterg/.vim/vim-plug-plugins/powerline-fonts/RobotoMono/Roboto* .
sudo chmod 0444 'Roboto '*

# DO NOT DO THIS STEP BELOW - cursor vim issue alignment!
# Set Konsole to use a patched powerline font
# Menu/Settings/Edit Current Profile/Appearance/Font [Choose]/
#	Check [Show all fonts]
#	Select Roboto Mono Light for Powerline, Light, 8pt
```

<br />

**auto-pairs**

Insert or delete brackets, parens, quotes in pair

Install

```bash
~/.vimrc
Plug 'jiangmiao/auto-pairs'

:PlugInstall

curl -sL https://deb.nodesource.com/setup_current.x | sudo -E bash -
```

<br />

**vim-ctrlp**

File finder for Vim

Install

```bash
~/.vimrc
Plug 'ctrlpvim/ctrlp.vim'

:PlugInstall
```

<br />

**ctags**

Generates an index file of language objects found in source files

Install

```bash
~/.vimrc
Plug 'universal-ctags/ctags'

:PlugInstall
```

Configure

```bash
nnoremap <leader>. :CtrlPTag<cr>
```

<br />

**vim-tagbar**

Plugin to browse the tags of the current file and get an overview of its structure

Install

```bash
~/.vimrc
Plug 'majutsushi/tagbar'

:PlugInstall
```

Configure

```bash
nmap <F8> :TagbarToggle<CR>
```

<br />

**vim-commentary**

This plugin allows the user to comment out lines and blocks of code

Install

```bash
~/.vimrc
Plug 'tpope/vim-commentary'

:PlugInstall
```

<br />
<br />

## Development plugins

**vim-fugitive**

Vim plugin for Git

Install

```bash
~/.vimrc
Plug 'tpope/vim-fugitive'

:PlugInstall
```

<br />

**vim-gitgutter**

Vim plugin for Git

Install

```bash
~/.vimrc
Plug 'airblade/vim-gitgutter'

:PlugInstall
```

Configure

```bash
let g:gitgutter_git_executable = '/usr/bin/git'
```

<br />

**vim-ale**

This plugin is an asynchronous linter (i.e. checking for syntax errors) - use it with flake8 and pylint. And also a formatter - use with google/yapf.

Install

```bash
~/.vimrc
Plug 'dense-analysis/ale'
Plug 'nvie/vim-flake8'
Plug 'google/yapf'

:PlugInstall
```

Configure

```bash
let g:ale_linters = {
      \   'python': ['flake8', 'pylint'],linter
      \   'javascript': ['eslint'],
      \}

let g:ale_fixers = { 
      \    'python': ['yapf'],
      \}

nmap <F10> :ALEFix<CR>
let g:ale_fix_on_save = 1
```

<br />

**coc.nvim**

IDE for vim

Install

```bash
~/.vimrc
Plug 'neoclide/coc.nvim'

:PlugInstall
```

Configure

```bash
In vim
" Some servers have issues with backup files, see #649.
set nobackup
set nowritebackup

" Give more space for displaying messages.
set cmdheight=2

" Having longer updatetime (default is 4000 ms = 4 s) leads to noticeable delays and poor user experience
set updatetime=300

" Always show the signcolumn
set signcolumn=yes

" Use tab for trigger completion with characters ahead and navigate
inoremap <silent><e:PlugInstallxpr> <TAB>
      \ pumvisible() ? "\<C-n>" :
      \ <SID>check_back_space() ? "\<TAB>" :
      \ coc#refresh()
inoremap <expr><S-TAB> pumvisible() ? "\<C-p>" : "\<C-h>"

function! s:check_back_space() abort
  let col = col('.') - 1
  return !col || getline('.')[col - 1]  =~# '\s'
endfunction

" Use <Tab> and <S-Tab> to navigate the completion list:
inoremap <expr> <Tab> pumvisible() ? "\<C-n>" : "\<Tab>"
inoremap <expr> <S-Tab> pumvisible() ? "\<C-p>" : "\<S-Tab>"

" Use <cr> to confirm completion
inoremap <expr> <cr> pumvisible() ? "\<C-y>" : "\<C-g>u\<CR>"

" Make <cr> select the first completion item and confirm the completion when no item has been selected:
inoremap <silent><expr> <cr> pumvisible() ? coc#_select_confirm() : "\<C-g>u\<CR>"
```

In vim
:CocConfig:PlugInstall

Arch

```json
{
    "python.jediEnabled": false,
    "python.terminal.activateEnvironment": false,
    "python.condaPath": "/opt/anaconda/condabin"
}
```

Config file is located in:`~/.vim/coc-settings.json`

<br />

**asyncrun.vim**

Install

```bash
~/.vimrc
Plug 'skywind3000/asyncrun.vim'

:PlugInstall
```

Configure

```bash
" Quick run via <F5>
nnoremap <F5> :call <SID>compile_and_run()<CR>

function! s:compile_and_run()
    exec 'w'
    if &filetype == 'c'
        exec "AsyncRun! gcc % -o %<; time ./%<"
    elseif &filetype == 'cpp'
       exec "AsyncRun! g++ -std=c++11 % -o %<; time ./%<"
    elseif &filetype == 'sh'
       exec "AsyncRun! time bash %"
    elseif &filetype == 'python'
       exec "AsyncRun! time python %"
    endif
endfunction

let g:asyncrun_open = 8
```

<br />
<br />

## Python plugins

Install python and its package installer
```bash
sudo pacman -S python python-pip
```

<br />

**vim-python-pep8-indent**

This plugin enforces PEP8 indentation

Install

```bash
~/.vimrc
Plug 'Vimjas/vim-python-pep8-indent'

:PlugInstall
```

<br />

**SimpylFold**

Vim plugin providing simple, correct folding for Python

Install

```bash
~/.vimrc
Plug 'tmhedberg/SimpylFold'

:PlugInstall
```

Configure

```bash
set nofoldenable
let g:SimpylFold_docstring_preview = 1
let g:SimpylFold_fold_docstring = 0
```

<br />

**python-syntax**

This plugin is a Python syntax highlighting

Install

```bash
~/.vimrc
Plug 'vim-python/python-syntax'

:PlugInstall
```

Configure

```bash
let g:python_highlight_all = 1
```

<br />

**coc-python**

IDE for vim:

1. Full LSP support, e.g. Microsoft Python Language server

Install

```bash
In vim
:CocInstall coc-python
```
