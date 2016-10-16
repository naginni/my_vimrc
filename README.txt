"" --------------------------- Vundle configuration ---------------------------
set nocompatible              " be iMproved, required
filetype off                  " required

"set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'
" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" GIT tools
Plugin 'tpope/vim-fugitive'
" NerdTree
Plugin 'scrooloose/nerdtree'
" vim-colors-solarized
Plugin 'altercation/vim-colors-solarized'
" vim-rails
Plugin 'tpope/vim-rails'
" https://github.com/vim-ruby/vim-ruby
Plugin 'vim-ruby/vim-ruby'
" vim-bundler
Plugin 'tpope/vim-bundler'
" https://github.com/vim-airline/vim-airline
" => good looking bottom :)
Plugin 'vim-airline/vim-airline'
" https://github.com/tomtom/tcomment_vim
" => create comments or block comments
" => gcc, gc, g>b
Plugin 'tomtom/tcomment_vim'
" https://github.com/tomasr/molokai new theme for the termnal
Plugin 'tomasr/molokai'
" https://github.com/tpope/vim-surround
" => mappings to easily delete change and add such surroundings in pairs.
" cs, ds, yssb, VS
Plugin 'tpope/vim-surround'
" https://github.com/jiangmiao/auto-pairs.
" => Every one should have a pair (Atogenerate pairs for "{[(
Plugin 'jiangmiao/auto-pairs'
" https://github.com/StanAngeloff/php.vim
" => php Highlighting
Plugin 'StanAngeloff/php.vim'

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required

" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just
":PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to
"auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line


" --------------- PERSONAL CONFIGURATION FOR VIM ---------------
 " pathogen
 execute pathogen#infect()
 syntax on
 filetype plugin indent on

 " NERDTree
 autocmd vimenter * NERDTree
 let g:NERDTreeDirArrows=0


"" remove trailing white spaces
  if has("autocmd")
    autocmd BufWritePre * :%s/\s\+$//e
  endif
  " theme configuration just for gui mode
  if has('gui_running')
     set nu
     let g:airline#extensions#tabline#enabled=1
    "solarize theme configuration
      "set background=dark
      "set background=light
      "colorscheme solarized
    "molkai theme configuration
      let g:rehash256 = 1
      "let g:molokai_original = 1
      colorscheme molokai
  endif
"" configuracion de los tabs
  set tabstop=2 shiftwidth=2 expandtab
  autocmd Filetype python setlocal ts=2 sts=2 sw=2

" ----------------- PHP Configuration -----------------
" Put at the very end of your .vimrc file.

function! PhpSyntaxOverride()
  hi! def link phpDocTags  phpDefine
  hi! def link phpDocParam phpType
endfunction

augroup phpSyntaxOverride
  autocmd!
  autocmd FileType php call PhpSyntaxOverride()
augroup END
