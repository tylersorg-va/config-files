# Vim

```jsx
select                                   v
select row(s)                            SHIFT + v
select blocks (columns)                  CTRL  + v
indent selected text                     >
unindent selected text                   <
list buffers                             :ls
open buffer                              :bN (N = buffer number)
print                                    :hardcopy
open a file                              :e /path/to/file.txt
                                         :e C:\Path\To\File.txt
sort selected rows                       :sort
search for word under cursor             *
open file under cursor                   gf
  (absolute path or relative)
format selected code                     =
select contents of entire file           ggVG
convert selected text to uppercase       U
convert selected text to lowercase       u
invert case of selected text             ~
convert tabs to spaces                   :retab
start recording a macro                  qX (X = key to assign macro to)
stop recording a macro                   q
playback macro                           @X (X = key macro was assigned to)
replay previously played macro *         @@
auto-complete a word you are typing **   CTRL + n
bookmark current place in file           mX (X = key to assign bookmark to)
jump to bookmark                         `X (X = key bookmark was assigned to
                                             ` = back tick/tilde key)
show all bookmarks                       :marks
delete a bookmark                        :delm X (X = key bookmark to delete)
delete all bookmarks                     :delm!
split screen horizontally                :split
split screen vertically                  :vsplit
navigating split screens                 CTRL + w + j = move down a screen
                                         CTRL + w + k = move up a screen
                                         CTRL + w + h = move left a screen
                                         CTRL + w + l = move right a screen
close all other split screens            :only

*  - As with other commands in vi, you can playback a macro any number of times.
     The following command would playback the macro assigned to the key `w' 100
     times: 100@w

** - Vim uses words that exist in your current buffer and any other buffer you may have open for auto-complete suggestions.
```

```
source ~/.vimrc
" https://github.com/JetBrains/ideavim/wiki/Emulated-plugins
set ideajoin
set ideastatusicon=gray
set idearefactormode=keep
set clipboard+=unnamed
set clipboard+=ideaput
set ideamarks " combines bookmarks and vim bookmarks
set easymotion " combines with acejump and ideavim_easymotion
set commentary " gcc, g+motion, v_gc comment with vim
set visualbell
set noerrorbells
set argtextobj "aa, ia manipulate arguments. cia = change inner argument
set exchange "cx , cxx, X, cxc, cxiw swap words of different lengths/patterns
set textobj-entire "ae, ie: select entire current buffer. https://github.com/kana/vim-textobj-entire
set highlightedyank "https://github.com/machakann/vim-highlightedyank
set vim-paragraph-motion

set multiple-cursors "<A-n> select next occurrence, <A-p> deselect and go back, <A-x> remove current cursor
" nmap <C-n> <Plug>NextWholeOccurrence
" xmap <C-n> <Plug>NextWholeOccurrence
" nmap g<C-n> <Plug>NextOccurrence
" xmap g<C-n> <Plug>NextOccurrence
" nmap <C-x> <Plug>SkipOccurrence
" xmap <C-x> <Plug>SkipOccurrence
" nmap <C-p> <Plug>RemoveOccurrence
" xmap <C-p> <Plug>RemoveOccurrence
"  Note that the default <A-n> and g<A-n> shortcuts don't work on Mac due to dead keys.
"  <A-n> is used to enter accented text e.g. ñ
nmap <S-C-n> <Plug>AllWholeOccurrences
xmap <S-C-n> <Plug>AllWholeOccurrences
nmap g<S-C-n> <Plug>AllOccurrences
xmap g<S-C-n> <Plug>AllOccurrences

set surround
set NERDTree
let g:NERDTreeMapActivateNode='l'
let g:NERDTreeMapJumpParent='h'

" nnoremap \e :e ~/.ideavimrc<CR> " can't find with this path"
" nnoremap <Leader>r <Action> IdeaVim.ReloadVimRc.reload<CR>

if has('ide')
  " mappings and options that exist only in IdeaVim
  map <Leader>f <Action>(GotoFile)
  map <Leader>g <Action>(FindInPath)
  map <Leader>s <Action>(Switcher)
  map <Leader>= <Action>(ReformatCode)
  map <Leader>d <Action>(Debug)
  map <Leader>c <Action>(Stop)
  map <Leader>i <Action>(QuickImplementations)
  map <Leader>e <Action>(ShowErrorDescription)
  map <Leader>k <Action>(QuickJavaDoc)
  map <Leader>b <Action>(ToggleLineBreakpoint)
  map <Leader>o <Action>(FileStructurePopup)
  map <Leader>h <Action>(Vcs.ShowTabbedFileHistory)
  map <Leader>a <Action>(Annotate)
  nnoremap <Leader>t :NERDTree<CR>
  nnoremap [[ :action MethodUp<CR>
  nnoremap ]] :action MethodDown<CR>
  nnoremap dm :execute 'delmarks '.nr2char(getchar())<CR> " delete marks. does it work?

  if &ide =~? 'intellij idea'
    if &ide =~? 'community'
      " some mappings and options for IntelliJ IDEA Community Edition
    elseif &ide =~? 'ultimate'
      " some mappings and options for IntelliJ IDEA Ultimate Edition
    endif
  elseif &ide =~? 'pycharm'
    " PyCharm specific mappings and options
  endif
endif
```

```java
"" Source your .vimrc
source ~/.vimrc

"" -- Suggested options --
" Show a few lines of context around the cursor. Note that this makes the
" text scroll if you mouse-click near the start or end of the window.
set scrolloff=5

" Do incremental searching.
set incsearch

" Don't use Ex mode, use Q for formatting.
map Q gq

"" -- Map IDE actions to IdeaVim -- https://jb.gg/abva4t
"" Map \r to the Reformat Code action
"map \r <Action>(ReformatCode)

"" Map <leader>d to start debug
"map <leader>d <Action>(Debug)

"" Map \b to toggle the breakpoint on the current line
"map \b <Action>(ToggleLineBreakpoint)

" Find more examples here: https://jb.gg/share-ideavimrc

" https://github.com/JetBrains/ideavim/wiki/Emulated-plugins
set ideajoin
set ideastatusicon=gray
set idearefactormode=keep
set clipboard+=unnamed
set clipboard+=ideaput
set ideamarks " combines bookmarks and vim bookmarks
set easymotion " combines with acejump and ideavim_easymotion
set commentary " gcc, g+motion, v_gc comment with vim
set visualbell
set noerrorbells
set argtextobj "aa, ia manipulate arguments. cia = change inner argument
set exchange "cx , cxx, X, cxc, cxiw swap words of different lengths/patterns
set textobj-entire "ae, ie: select entire current buffer. https://github.com/kana/vim-textobj-entire
set highlightedyank "https://github.com/machakann/vim-highlightedyank
set vim-paragraph-motion

set multiple-cursors "<A-n> select next occurrence, <A-p> deselect and go back, <A-x> remove current cursor
" nmap <C-n> <Plug>NextWholeOccurrence
" xmap <C-n> <Plug>NextWholeOccurrence
" nmap g<C-n> <Plug>NextOccurrence
" xmap g<C-n> <Plug>NextOccurrence
" nmap <C-x> <Plug>SkipOccurrence
" xmap <C-x> <Plug>SkipOccurrence
" nmap <C-p> <Plug>RemoveOccurrence
" xmap <C-p> <Plug>RemoveOccurrence
"  Note that the default <A-n> and g<A-n> shortcuts don't work on Mac due to dead keys.
"  <A-n> is used to enter accented text e.g. ñ
nmap <S-C-n> <Plug>AllWholeOccurrences
xmap <S-C-n> <Plug>AllWholeOccurrences
nmap g<S-C-n> <Plug>AllOccurrences
xmap g<S-C-n> <Plug>AllOccurrences

set surround
set NERDTree
let g:NERDTreeMapActivateNode='l'
let g:NERDTreeMapJumpParent='h'

" nnoremap \e :e ~/.ideavimrc<CR> " can't find with this path"
" nnoremap <Leader>r <Action> IdeaVim.ReloadVimRc.reload<CR>

if has('ide')
  " mappings and options that exist only in IdeaVim
  map <Leader>f <Action>(GotoFile)
  map <Leader>g <Action>(FindInPath)
  map <Leader>s <Action>(Switcher)
  map <Leader>= <Action>(ReformatCode)
  map <Leader>d <Action>(Compare.SameVersion)
  map <Leader>c <Action>(Stop)
  map <Leader>i <Action>(QuickImplementations)
  map <Leader>k <Action>(QuickJavaDoc)
  map <Leader>b <Action>(ToggleLineBreakpoint)
  map <Leader>o <Action>(FileStructurePopup)
  map <Leader>h <Action>(Vcs.ShowTabbedFileHistory)
  map <Leader>e <Action>(GotoNextError)
  map <Leader>a <Action>(UnsplitAll)
  map <Leader>w <Action>(HideAllWindows)
  map <Leader>q <Action>(CloseEditor)
  nmap <Leader>/ <Action>(ShowErrorDescription) " use this after highlighting a variable to open a show value pane ?
  nnoremap <Leader>t :NERDTree<CR>

  if &ide =~? 'intellij idea'
    if &ide =~? 'community'
      " some mappings and options for IntelliJ IDEA Community Edition
    elseif &ide =~? 'ultimate'
      " some mappings and options for IntelliJ IDEA Ultimate Edition
    endif
  elseif &ide =~? 'pycharm'
    " PyCharm specific mappings and options
  endif
endif
```

```java
syntax on 
imap jj <Esc>
imap jk <Esc>
imap kj <Esc>
set incsearch
set ignorecase
set smartcase
set relativenumber
set number
set scrolloff=3
set showcmd
set incsearch
set hlsearch
"set lazyredraw
set showmatch
let mapleader=" "
nnoremap <leader>, :nohlsearch<CR>
nnoremap <leader>v :vsplit<CR>
nnoremap <leader>s :split<CR>
nnoremap <leader>q :quit<CR>
nnoremap <leader>Q :quit!<CR>
set splitbelow
set splitright
set clipboard=unnamedplus
```

VSCode
```
{

    "files.autoSave": "afterDelay",
    "files.autoSaveDelay": 125,
    "vim.useSystemClipboard": true,
    "vim.insertModeKeyBindings": [{
        "before": ["j", "j"],
        "after": ["<Esc>", "l"]
    },
    {
        "before": ["<Esc>"],
        "after": ["<Esc>"]
    }],
    "vim.normalModeKeyBindingsNonRecursive": [
    // {
    //   "before": ["<C-h>"],
    //   "after": ["<C-w>", "h"]
    // },
    // {
    //   "before": ["<C-j>"],
    //   "after": ["<C-w>", "j"]
    // },
    // {
    //   "before": ["<C-k>"],
    //   "after": ["<C-w>", "k"]
    // },
    // {
    //   "before": ["<C-l>"],
    //   "after": ["<C-w>", "l"]
    // },
      {
      "before": ["<Leader>", ","],
      "commands": [":noh"]
    }],
    "vim.leader": " ",
    "vim.smartcase": true,
    "vim.ignorecase": true,
    "vim.hlsearch": true,
    // "vim.disableAnnoyingNeovimMessage": true,
    "workbench.sideBar.location": "left",
    "editor.minimap.enabled": true,
    "editor.multiCursorModifier": "ctrlCmd",
    "editor.fontSize": 14,
    "editor.fontLigatures": true,
    "liveServer.settings.donotShowInfoMsg": true,
    "editor.renderWhitespace": "all",
    "liveServer.settings.donotVerifyTags": true,
    "vsicons.dontShowNewVersionMessage": true,
    "workbench.colorTheme": "Material Theme Darker",
    "gitlens.advanced.messages": { },
    "files.associations": {
        "*.html": "html",
        "*.cls": "vb",
        "*.frm": "vb"
    },
    "editor.suggestSelection": "first",
    "vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue",
    "editor.cursorSmoothCaretAnimation": true,
    "explorer.confirmDelete": false,
    "[javascript]": {
        "editor.defaultFormatter": "vscode.typescript-language-features"
    },
    "explorer.confirmDragAndDrop": false,
    "workbench.iconTheme": "Monokai Pro Icons",
    "workbench.colorCustomizations": {},
    "python.languageServer": "Jedi",
    "workbench.editorAssociations": {
        "*.ipynb": "jupyter-notebook"
    },
    "python.pythonPath": "/usr/local/bin/python3",
    "python.defaultInterpreterPath": "/opt/homebrew/bin/python3",
    "notebook.cellToolbarLocation": {
        "default": "right",
        "jupyter-notebook": "left"
    },
    "files.exclude": {
        "**/.classpath": true,
        "**/.project": true,
        "**/.settings": true,
        "**/.factorypath": true
    },
    "security.workspace.trust.untrustedFiles": "open",
    "[json]": {
        "editor.defaultFormatter": "vscode.json-language-features"
    },
    "[jsonc]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\wsl.exe",
    "terminal.integrated.defaultProfile.windows": "PowerShell",
    "gitlens.mode.active": "zen",
    "workbench.editor.untitled.hint": "hidden",
    "window.zoomLevel": 1
}
```
