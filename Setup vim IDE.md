# Setup vim as an IDE

This is a step by step install guide to add plug-ins to vim and learn their features. Or just use the `.vimrc` config.

<br />

**Pre-requisites**

Install vim-plug
```bash
wget -P ~/.vim/autoload/ https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
<br />
<br />

## Theme

**onedark.vim**

A dark Vim/Neovim color scheme for the GUI and 16/256/true-color terminals, based on FlatColor, with colors inspired by the excellent One Dark syntax theme for the Atom text editor.

Install the theme
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

## Python

Install python and its package installer
```bash
sudo pacman -S python python-pip
```
