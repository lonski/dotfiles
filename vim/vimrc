syntax on
au BufNewFile,BufFilePre,BufRead *.md set filetype=markdown 
set nocompatible
set modelines=1
filetype off
set encoding=utf-8
set scrolloff=3
set autoindent
set nu
set showmode
set showcmd
set hidden
set cursorline
set ttyfast
set ruler
set backspace=indent,eol,start
set laststatus=2
set ttimeoutlen=10
set relativenumber

"Show invisible characters
set list
set listchars=tab:▸\ ,

"Searching/moving settings
nnoremap / /\v
vnoremap / /\v
set ignorecase
set smartcase
set gdefault
set incsearch
set showmatch
set hlsearch
nnoremap <leader><space> :noh<cr>
nnoremap <tab> %
vnoremap <tab> %

"Convert tabs to spaces
set tabstop=2 softtabstop=2 expandtab shiftwidth=2 smarttab

"Allow yanking to system clipboard
set clipboard=unnamedplus

"Macro for generating help tags
command GenHelptags execute "helptags " . expand("%:p:h")

"CDC = Change to Directory of Current file
command CDC cd %:p:h

"Set directory for backup and undo files
set backupdir=~/.vim/tmp,.
set directory=~/.vim/tmp,.
set undodir=~/.vim/tmp,.
set undofile
set backup

"Vundle plugins and settings
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
Plugin 'VundleVim/Vundle.vim'
Plugin 'vim-airline/vim-airline'
Plugin 'vim-airline/vim-airline-themes'
Plugin 'scrooloose/nerdtree'
Plugin 'Xuyuanp/nerdtree-git-plugin' 
Plugin 'edkolev/tmuxline.vim'
Plugin 'morhetz/gruvbox'
Plugin 'rust-lang/rust.vim'
Plugin 'scrooloose/nerdcommenter'
Plugin 'mileszs/ack.vim'
Plugin 'vim-scripts/YankRing.vim'
Plugin 'tpope/vim-surround'
Plugin 'ctrlpvim/ctrlp.vim'
Plugin 'tell-k/vim-autopep8'
Plugin 'slashmili/alchemist.vim'
"Plugin 'Valloric/YouCompleteMe'
Plugin 'janko-m/vim-test'
Plugin 'elixir-editors/vim-elixir'
Plugin 'mhinz/vim-mix-format'
call vundle#end()            
filetype plugin indent on   

" Airline Config
let g:airline_powerline_fonts = 1
let g:airline_theme = 'term'
let g:airline#extensions#hunks#enabled=0
let g:airline#extensions#branch#enabled=1

"NERDTree Config
map <leader>t :NERDTreeToggle<CR>

if !exists('g:airline_symbols')
  let g:airline_symbols = {}
endif
let g:airline_symbols.space = "\ua0"

"NERDCommenter config
let g:NERDSpaceDelims = 1
let g:NERDCompactSexyComs = 1
let g:NERDDefaultAlign = 'left'
let g:NERDCommentEmptyLines = 1
let g:NERDTrimTrailingWhitespace = 1
let NERDTreeNodeDelimiter = "\t"

"YankRing config
nnoremap <silent> <F3> :YRShow<cr>
inoremap <silent> <F3> <ESC>:YRShow<cr>
let g:yankring_history_dir = '~/.vim/tmp'

"Ctrl P finder options
set wildignore+=*/tmp/*,*.so,*.swp,*.zip,*.class

"Test.vim options
nmap <silent> <leader>tn :TestNearest<CR>
nmap <silent> <leader>tf :TestFile<CR>
nmap <silent> <leader>ta :TestSuite<CR>
nmap <silent> <leader>tl :TestLast<CR>
nmap <silent> <leader>tg :TestVisit<CR>
let test#strategy = "tslime"

""" Determine the python test runner to use
if filereadable(".pytest")
    let test#python#runner = 'pytest'
elseif filereadable(".djangotest")
    let test#python#runner = 'djangotest'
elseif isdirectory("./lib/ansible")
    let test#python#runner = 'nose'
elseif isdirectory("../../../ansible")
    let test#python#runner = 'nose'
elseif isdirectory("./libcloud")
    let test#runners = {'Python': ['LibCloudTest']}
    let test#python#runner = 'libcloudtest'
endif

""" Pytest options
let test#python#pytest#options = {
    \ 'nearest': '--capture=no -v',
    \ 'file': '--capture=no --random',
    \ 'suite': '--capture=no --random',
    \}
""" Nose options
let test#python#nose#options = {
    \ 'nearest': '-v -s',
    \ 'file': '-s --randomize',
    \ 'suite': '-s --randomize',
\}

" Color scheme settings
set background=dark
colorscheme gruvbox
hi Normal ctermbg=none

"Remove toolbar in gVIM
set guioptions-=m  "remove menu bar
set guioptions-=T  "remove toolbar
set guioptions-=r  "remove right-hand scroll bar
set guioptions-=L  "remove left-hand scroll bar

"Rust options
au FileType rust nmap gd <Plug>(rust-def)
au FileType rust nmap gs <Plug>(rust-def-split)
au FileType rust nmap gx <Plug>(rust-def-vertical)
au FileType rust nmap <leader>gd <Plug>(rust-doc)

autocmd Filetype rust map <F8> :w<Return>:!cargo build && RUST_BACKTRACE=1 cargo run<CR>
autocmd Filetype rust map <F9> :w<Return>:!cargo build && RUST_BACKTRACE=1 cargo run<Space>
autocmd Filetype rust map <F10> :w<Return>:!cargo build && cargo test<CR>

"Python options
autocmd Filetype python map <F7> :w<Return>:!python2 -B %<CR>
autocmd Filetype python map <F8> :w<Return>:!python -B %<CR>
autocmd FileType python noremap <buffer> <F9> :call Autopep8()<CR>
let g:autopep8_disable_show_diff=0

let g:rustfmt_autosave = 1

"Ruby options                                                                                                                                                                                      
autocmd Filetype ruby map <F7> :w<Return>:!ruby %<CR>
autocmd Filetype ruby map <F8> :w<Return>:!bundle exec ruby %<CR>
autocmd Filetype ruby map <F6> :w<Return>:!bundle install<CR>

"Elixir options
autocmd Filetype elixir map <F8> :w<Return>:!elixir %<CR>
autocmd Filetype elixir map <F7> :w<Return>:MixFormat<CR>

"You Complete Me settings
"let g:ycm_server_python_interpreter = '/usr/bin/python2.7'

"Key mappings
let mapleader=' '
"Disable arrow keys
nnoremap <up> <nop>
nnoremap <down> <nop>
nnoremap <left> <nop>
nnoremap <right> <nop>
inoremap <up> <nop>
inoremap <down> <nop>
inoremap <left> <nop>
inoremap <right> <nop>
nnoremap j gj
nnoremap k gk
"
inoremap jj <ESC>
"Moving between splits
nnoremap <leader>h <C-w>h
nnoremap <leader>j <C-w>j
nnoremap <leader>k <C-w>k
nnoremap <leader>l <C-w>l

" Custom commands
" Select pasted text
nnoremap <leader>v V`]
nnoremap <leader>w <C-w>v<C-w>l
nnoremap <leader>a :Ack!<CR>
" Format json
nnoremap <leader>fj <ESC>:%!python -mjson.tool<CR>
" Format xml
nnoremap <leader>fx <ESC>:%!python3 -c "import xml.dom.minidom, sys; print(xml.dom.minidom.parse(sys.stdin).toprettyxml())"<CR>

vnoremap ;rv c<C-O>:set revins<CR><C-R>"<Esc>:set norevins<CR>
