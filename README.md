
# AutoComplPop

Your vim comes to automatically opens popup menu for completions with this plugin, when you enter characters or move the cursor in Insert mode. It won't prevent you continuing entering characters.


## Authors

- [@OurCodeBase](https://www.github.com/OurCodeBase)
- [@vim-scripts](https://www.github.com/vim-scripts)


## Installation

- Using Vundle
```vim
Plugin "OurCodeBase/AutoComplPop"
```

## Usage

Once this plugin is installed, auto-popup is enabled at startup by default.

Which completion method is used depends on the text before the cursor. The
default behavior is as follows:
```
   kind      filetype    text before the cursor ~
   Keyword   *           two keyword characters
   Filename  *           a filename character + a path separator 
                         + 0 or more filename character
   Omni      ruby        ".", "::" or non-word character + ":"
                         (|+ruby| required.)
   Omni      python      "." (|+python| required.)
   Omni      xml         "<", "</" or ("<" + non-">" characters + " ")
   Omni      html/xhtml  "<", "</" or ("<" + non-">" characters + " ")
   Omni      css         (":", ";", "{", "^", "@", or "!")
                         + 0 or 1 space
```
## Snipmate

[snipmate.vim](https://github.com/OurCodeBase/snipmate.vim)

Also, you can make user-defined completion and snipMate's trigger completion

To enable auto-popup for this completion, add these lines to the last of the file `plugin/snipMate.vim`
```vim
fun! GetSnipsInCurrentScope()
  let snips = {}
  for scope in [bufnr('%')] + split(&ft, '\.') + ['_']
    call extend(snips, get(s:snippets, scope, {}), 'keep')
    call extend(snips, get(s:multi_snips, scope, {}), 'keep')
  endfor
  return snips
endf
```

And add the following line to `.vimrc`
```vim
let g:acp_behaviorSnipmateLength=1
```

To use AutoComplPop with only snipmate (AutoComplPop will not use keywords used in current file)
Add the following line to `.vimrc`
```vim
let g:acp_behaviorKeywordLength=-1
```
