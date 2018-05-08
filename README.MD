Для начала работы с вим:

    cp /usr/share/vim/vim72/vimrc_example.vim ~/.vimrc

Конфиг

    " All system-wide defaults are set in $VIMRUNTIME/debian.vim and sourced by
" the call to :runtime you can find below.  If you wish to change any of those
" settings, you should do it in this file (/etc/vim/vimrc), since debian.vim
" will be overwritten everytime an upgrade of the vim packages is performed.
" It is recommended to make changes after sourcing debian.vim since it alters
" the value of the 'compatible' option.

" This line should not be removed as it ensures that various options are
" properly set to work with the Vim-related packages available in Debian.
runtime! debian.vim

" Vim will load $VIMRUNTIME/defaults.vim if the user does not have a vimrc.
" This happens after /etc/vim/vimrc(.local) are loaded, so it will override
" any settings in these files.
" If you don't want that to happen, uncomment the below line to prevent
" defaults.vim from being loaded.
" let g:skip_defaults_vim = 1

" Uncomment the next line to make Vim more Vi-compatible
" NOTE: debian.vim sets 'nocompatible'.  Setting 'compatible' changes numerous
" options, so any other options should be set AFTER setting 'compatible'.
"set compatible

" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
syntax on


" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
"set background=dark

" Uncomment the following to have Vim jump to the last position when
" reopening a file
"if has("autocmd")
"  au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif
"endif

" Uncomment the following to have Vim load indentation rules and plugins
" according to the detected filetype.
"if has("autocmd")
"  filetype plugin indent on
"endif

" The following are commented out as they cause vim to behave a lot
" differently from regular Vi. They are highly recommended though.
"set showcmd		" Show (partial) command in status line.
"set showmatch		" Show matching brackets.
"set ignorecase		" Do case insensitive matching
"set smartcase		" Do smart case matching
"set incsearch		" Incremental search
"set autowrite		" Automatically save before commands like :next and :make
"set hidden		" Hide buffers when they are abandoned
"set mouse=a		" Enable mouse usage (all modes)

set nocompatible
filetype off

set rtp+=~/.vim/bundle/vundle/
call vundle#rc()

" let Vundle manage Vundle
Bundle 'gmarik/vundle'

" common
Bundle 'Lokaltog/powerline', {'rtp': 'powerline/bindings/vim/'}
Bundle 'scrooloose/nerdtree'
Bundle 'kien/ctrlp.vim'
Bundle 'mileszs/ack.vim'
Bundle 'scrooloose/nerdcommenter'
Bundle 'scrooloose/syntastic'
Bundle 'vim-scripts/IndexedSearch'
Bundle 'vim-scripts/L9.git'
Bundle 'vim-scripts/taglist.vim'

" php
Bundle 'stephpy/vim-php-cs-fixer'

" python&django
Bundle 'klen/python-mode'
Bundle 'chazy/cscope_maps'
Bundle 'joonty/vim-phpqa'

" ryby&rails
Bundle 'tpope/vim-rails'
Bundle 'tpope/vim-rake'
Bundle 'tpope/vim-fugitive'
Bundle 'tpope/vim-surround'
Bundle 'tpope/vim-endwise'

" html&js
Bundle 'mattn/emmet-vim'
Bundle 'pangloss/vim-javascript'

" Bundle 'vim-scripts/matchit.zip'
" Bundle 'ervandew/supertab'
" Bundle 'Raimondi/delimitMate'
" Bundle 'godlygeek/tabular'
" Bundle 'tpope/vim-cucumber'
" Bundle 'tpope/vim-haml'
" Bundle 'kchmck/vim-coffee-script'
" The bundles you install will be listed here

" filetype plugin on
filetype plugin indent on

augroup vimrc_autocmds
    autocmd!
    " highlight characters past column 120
    autocmd FileType python highlight Excess ctermbg=DarkGrey guibg=Black
    autocmd FileType python match Excess /%120v.*/
    autocmd FileType python set nowrap
augroup END


" set guifont=DejaVu Sans Mono for Powerline 9
set laststatus=2


map <F2> :NERDTreeToggle<CR>
nmap  :cs find g =expand("")

set autoindent
set tabstop=4
set shiftwidth=4
set expandtab


set completeopt=longest,menuone

Bundle 'ervandew/supertab'
let g:SuperTabDefaultCompletionType = "<c-x><c-o>"

Bundle 'shawncplus/phpcomplete.vim'

autocmd FileType php setlocal omnifunc=phpcomplete#CompletePHP

Bundle 'arnaud-lb/vim-php-namespace'


