# Setup vim as an IDE

I use vim under [Arch Linux](https://github.com/OpcodePete/Arch-Linux).

This is a step-by-step setup guide to add additional features to vim in the following areas:
- General editing,
- Geneal software development, and
- Python development

<br />

Refer to the [use vim as an IDE.md](https://github.com/OpcodePete/vim/blob/main/use%20vim%20as%20an%20IDE.md) guide on how to use plugins.

<br />

## Set vim theme

**onedark.vim**

A dark Vim/Neovim color scheme for the GUI and 16/256/true-color terminals, based on FlatColor, with colors inspired by the excellent One Dark syntax theme for the Atom text editor.

Install
```bash
# Download the repo
git clone https://github.com/joshdick/onedark.vim

# Copy the following files:
cp ~/onedark.vim/colors/onedark.vim ~/.vim/colors/
cp ~/onedark.vim/autoload/onedark.vim ~/.vim/autoload/
```

Include in `.vimrc`
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

## Install plugin manager

Install vim-plug
```bash
wget -P ~/.vim/autoload/ https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
<br />
<br />


## Install general plugins

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

Include in `.vimrc`

```bash
~/.vimrc
let g:airline_theme='onedark'
let g:airline#extensions#coc#enabled = 1
let g:airline_powerline_fonts = 1

# Include the following line in the General\Misc section
set encoding=utf-8
```

Fonts

To get vim-airline to display arrows, install the patched powerline fonts and use them  
Ensure you have the fonts installed - refer to my [i3 installation guide](https://github.com/OpcodePete/i3/blob/main/i3%20Installation%20guide.md)

```bash
# List all Roboto fonts
fc-list | grep Roboto

# Copy the newly installed patched powerline fonts to the above location
cd /usr/share/fonts/TTF/
sudo cp /home/peterg/.vim/vim-plug-plugins/powerline-fonts/RobotoMono/Roboto* .
sudo chmod 0444 'Roboto '*
```

<br />

**auto-pairs**

Install

```bash
~/.vimrc
Plug 'jiangmiao/auto-pairs'

:PlugInstall
```

<br />

**vim-ctrlp**

Install

```bash
~/.vimrc
Plug 'ctrlpvim/ctrlp.vim'

:PlugInstall
```

<br />

**Universal Ctags**

Install

```bash
~/.vimrc
Plug 'universal-ctags/ctags'

:PlugInstall
```

Include in `.vimrc`

```bash
nnoremap <leader>. :CtrlPTag<cr>
```

<br />

**vim-tagbar**

Install

```bash
~/.vimrc
Plug 'majutsushi/tagbar'

:PlugInstall
```

Include in `.vimrc`

```bash
nmap <F8> :TagbarToggle<CR>
```

<br />

**vim-commentary**

Install

```bash
~/.vimrc
Plug 'tpope/vim-commentary'

:PlugInstall
```

<br />
<br />

## Install development plugins

**vim-fugitive**

Install

```bash
~/.vimrc
Plug 'tpope/vim-fugitive'

:PlugInstall
```

<br />

**vim-gitgutter**

Install

```bash
~/.vimrc
Plug 'airblade/vim-gitgutter'

:PlugInstall
```

Include in `.vimrc`

```bash
let g:gitgutter_git_executable = '/usr/bin/git'
```

<br />

**vim-ale**

Install

```bash
~/.vimrc
Plug 'dense-analysis/ale'
Plug 'nvie/vim-flake8'
Plug 'google/yapf'

:PlugInstall
```

Include in `.vimrc`

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

Install

```bash
~/.vimrc
Plug 'neoclide/coc.nvim'

:PlugInstall
```

Include in `.vimrc`

```bash
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

Include in `~/.vim/coc-settings.json

```json
{
    "python.jediEnabled": false,
    "python.terminal.activateEnvironment": false,
    "python.condaPath": "/opt/anaconda/condabin"
}
```

Install via vim, to install plugin:
```bash
:CocConfig:PlugInstall
```
<br />

**asyncrun.vim**

Install

```bash
~/.vimrc
Plug 'skywind3000/asyncrun.vim'

:PlugInstall
```

Include in `.vimrc`

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

## Install python plugins

Install python and its package installer
```bash
sudo pacman -S python python-pip
```

<br />

**vim-python-pep8-indent**

Install

```bash
~/.vimrc
Plug 'Vimjas/vim-python-pep8-indent'

:PlugInstall
```

<br />

**SimpylFold**

Install

```bash
~/.vimrc
Plug 'tmhedberg/SimpylFold'

:PlugInstall
```

Include in `.vimrc`

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

Include in `.vimrc`

```bash
let g:python_highlight_all = 1
```

<br />

**coc-python**

IDE for vim:

1. Full LSP support, e.g. Microsoft Python Language server

Install via vim

```bash

:CocInstall coc-python
```
