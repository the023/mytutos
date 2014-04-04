
# Survive with Vim
==================

1. VIM - General infos
2. VIM - how to intall plugins 
3. VIM - Plugin list
4. VIM - Plugins Shortcuts
5. External resources


# VIM - General Infos
=====================

http://vim.wikia.com/wiki/Best_Vim_Tips

## The diferents Modes 

Vim has many Modes : 

    Normal / Command     Esc + keys
    Command Line         : + commandename
    Insert Mode          i + type some text
    Vidual Mode          v + keys
    Select Mode          like visual but replace
    Ex Mode              like command line mode, without returning to normal


## Windows Tabs and Buffers [source](http://blog.sanctum.geek.nz/buffers-windows-tabs/)

### *Buffer* : an open instance of a file, can be in background  

    :e filename     Open filename in new buffer
    :ls             List all buffer
    :b tab          Completion that list buffers then open
    :b number       Open buffer number
    :bw             Like |:bdelete|, but really delete the buffer.
    :bd             Unload buffer [N] (default: current buffer) and delete it from the buffer list.
    :2bw            close buff2
    :2,4bw          close buff2 and 4
            
### *Window* : a viewport onto a single buffer  

     :split another-file
     :vsplit another-file

Navigate between windows
     
     Ctrl-w w      switch between windows
     Ctrl-w h      move to the window left
     Ctrl-w j      move to the window below
     Ctrl-w k      move to the window above
     Ctrl-w l      move to the window right
     Ctrl-w +      increase the size of a window
     Ctrl-w -      decrease the size of a window

Open 2 files in window mode from shell 

     $ vi -o file1.txt file2.txt   # Horizontal split
     $ vi -O file1.txt file2.txt   # Vertical split


### *Tab* : a collection of one or more windows

    :tabedit        Open a new tab and buffer for filename 
    :tabnext        Next Tab
    gt              Next Tab
    gT              Previous Tab
    :tabf path      Find file in path and open it in new tab 
    
   ?? http://stackoverflow.com/questions/1269648/how-do-i-close-a-single-buffer-out-of-many-in-vim
  
### Deplacement dans un fichier

    Commande    Place le curseur
    0   au début de la ligne
    $   à la fin de la ligne
    gg  à la première ligne
    G   à la dernière ligne

    ^   sur le premier caractère de la ligne
    xG  au début de la ligne x
    H   en haut de l'écran
    M   au milieu de l'écran
    L   en bas de l'écran
    Co      jump to previous position
    
    "" Move between words : min : space is only separator / maj : more separators
    wW      go forward 1 word
    bB      go backward 1 word
    eE      go to end of word

### Delete

    dd      delete curent line
    daw     delete the word under the cursor    
    caw     delete the word under the cursor and put you in insert mode

### Copy Paste

    1) Position the cursor where you want to begin cutting.
    2) Press v (or upper case V if you want to cut whole lines).
    3) Move the cursor to the end of what you want to cut.
    4) Press d.
    5) Move to where you would like to paste.
    6) Press P to paste before the cursor, or p to paste after. 

### File syntax highlight

You can change the syntax if filetype is not reconized :

    :set syn=sh
    :set syn=markdown


### Key mapping 

Key mapping can be configured in **.vimrc** with following syntaxe : **map Sequence_keys Operation**, exemple : **map <F5\> dd**    
Mapping can be applyed in different modes : **map, nmap (normal), imap(insert), omap(operator pending) ,cmap(command), vmap(visual)**   
To prevent loop use : **noremap, nnoremap, ...**  [key mapping](http://how-to.wikia.com/wiki/How_to_map_keys_in_vim )

Main keys notation :  

    <C-x>       Ctrl+x
    <S-x>       Shift+x
    <A-x>       Alt+x
    <M-x>       Meta+x
    
    Leader      usually \ or , 
    others      <CR><Enter><Return>   <Space>   <Esc>   <Tab>

## Exemples in Command mode  

    :mes            afficher les messages ( erreur demarage ) 
    :set nonumber   remove lines number
    :! ls           Execute command ls
    :! php -l %     Execute current file % in php
    
    :colorscheme desert     http://vimcolorschemetest.googlecode.com/svn/html/index-html.html)
    :set nonumber           no line number
    :set nofoldenable       no folding shown 

### Completion ( Insert Mode )

    Cx Cl       Whole Line
    Cx Cn       current file
    Cx Ct       Thesaurus
    Cx C]       Tags
    Cx Cd       macros
    Cx Cf       Filename
    Cx Cu       User Defined 
    Cx Co       Omni 
    Cxs         Spelling

    Cn   Cp         prev next

    Cx Cn           Word completion – forward
    Cx Cp           Word completion – backward
    Cx Ck           Dictionaru ( needs : set dictionary+=/usr/share/dict/words ) 

### Undo Redo ( Insert Mode ) 

    u               undo
    Ctrl R          redo
    U               undo last line ?

### Find Replace

Find each occurrence of 'foo' (in all lines), and replace it with 'bar'. 

    :%s/foo/bar/g

Find each occurrence of 'foo' (in the current line only), and replace it with 'bar'. 

    :s/foo/bar/g

Change each 'foo' to 'bar', but ask for confirmation first. 

    :%s/foo/bar/gc

## marks (book ) /*{{{*/

Basics : 

    'a      jump to line of mark a (first non-blank character in line)
    `a      jump to position (line and column) of mark a
    d'a     delete from current line to line of mark a
    ]'      jump to next line with a lowercase mark
    ['      jump to previous line with a lowercase mark
    :delmarks a     delete mark a
    :marks  list marks
    
special marks 

    `.      jump to position where last change occurred in current buffer
    `"      jump to position where last exited current buffer
    `0      jump to position in last file edited (when exited Vim)
    `1      like `0 but the previous file (also `2 etc) 

With [vim-signature](https://github.com/kshenoy/vim-signature)

    m[a-zA-Z]    : Toggle mark
    m<Space>     : Delete all marks
    m,           : Place the next available mark
    ]`           : Jump to next mark
    [`           : Jump to prev mark

## move between variables

    g*      highlight word
    gd      go to var/ methode declaration
    gD      go to globale declaration
/*}}}*/

## Indent/*{{{*/

Indent All file from ( http://stackoverflow.com/questions/506075/how-do-i-fix-the-indentation-of-an-entire-file-in-vi )

    gg=G        Indent From top to End of file
    gg          goes to top
    =           indent
    G           goes End
    <           unindent Visual Mode
    >           indent   Visual Mode
    Ctrl+t      indent  Insert Mode
    Ctrl+d      unindent Insert Mode
    :set nonumber/number    Line number
    shift+mouse             copy Paste From windows
/*}}}*/

## folding/*{{{*/

    :help fold	help !!!
    zf  		fold
    zfNUM   	fold NUM of lines
    zd		    delete curent fold
    zE		    delete all folds in window
   
    zo		    open fold
    zc 		    close fold
    zi          activate / desactivate fold enable
    za          toggle fold
    zv          open to window
 
    zr          fold less : substract to foldlvl
    zm          fold more : add fold level
    zj zk       next / prev foldz
/*}}}*/

## go to declaration/*{{{*/

    gd      will take you to the local declaration.
    gD      will take you to the global declaration.
    g*      search for the word under the cursor (like *, but g* on 'rain' will find words like 'rainbow').
    g#      same as g* but in backward direction.
    gg      goes to the first line in the buffer (or provide a count before the command for a specific line).
    G       goes to the last line (or provide a count before the command for a specific line). 

    gf      will go to the file under the cursor
    g]      and other commands will jump to a tag definition (a tag can be a function or variable name, or more). i
/*}}}*/


# VIM - How to Install  a Plugin / Bundle 
=========================================

## With Vundle

* [Vundle Install](https://github.com/gmarik/Vundle.vim)
* open *.vim.rc* and add line : **Bundle 'tpope/vim-fugitive'**  
* in vim type **:BundleInstall**

## With Pathogen

* [Pathogen Install](https://github.com/tpope/vim-pathogen)
* go to ~/.vim/bundle/
* then : git clone adress_to_bundle_repository

## In case of line break troubles : 

Check if files are in dos mode ( can append on linux, due to git configuration ? )  
Then use dos2unix to convert to unix format :

    # find ~/.vim -type f -name "*.vim" -exec dos2unix {} \;

## config to Use specific .VIMRC and .VIM/
 
http://stackoverflow.com/a/3384476  
put .vimrc in .vim + tweak + laucnch with : vim -u .vimrc.new

Add this at start of vimrc

     " set default 'runtimepath' (without ~/.vim folders)
     let &runtimepath = printf('%s/vimfiles,%s,%s/vimfiles/after', $VIM, $VIMRUNTIME, $VIM)  
     " what is the name of the directory containing this file?
     let s:portable = expand('<sfile>:p:h')
     " add the directory to 'runtimepath'
     let &runtimepath = printf('%s,%s,%s/after', s:portable, &runtimepath, s:portable) 
     """" add for vundle
     let &runtimepath = printf('%s,%s/bundle/vundle/', &runtimepath, s:portable)       


# VIM - Plugin list
===================

[Comfortable PHP Editing With VIM -8-](http://schlitt.info/opensource/blog/0740_comfortable_php_editing_with_vim_8.html)
[good list](https://github.com/stephpy/vim-config)  
[php plugins](http://askubuntu.com/questions/264276/what-plugins-are-recommended-for-vim-for-php-developers)  
[vim as php ide](http://joncairns.com/2012/05/using-vim-as-a-php-ide/)  
[php integration vim](https://github.com/spf13/PIV)  
[plugin list](_http://mirnazim.org/writings/vim-plugins-i-use/)  
[plugins for php html css js](http://stackoverflow.com/questions/3173963/useful-vim-plugins-for-web-development-and-design-php-html-css-javascript)  

    supertab        for tab completion
    Ultisnips       other snippet plugins are xptempletate and snipmate
    nerdtree        file navigation/project tree
    nerdcommenter   commenting
    syntastic       syntax checker
    fugitive        git integration
    vim-surround    quickly surround text objects with any delimiters like ',", html tags etc...
    tagbar          navigate through code tags
    powerline       nice status line
    ctrlp           fuzzy file finder
    sparkup         create html quickly
    delimitmate     autocomplete delimiters
    phpfolding      automatic folding of functions and classes
    php Documentor  generation of phpDocumentor doc blocks for PHP4 & 5
    Vim-Sauce       a very simple project manager
    EasyMotion      quickly jump to any word or character in a file.
    surround.vim    to enclose text in HTML tags
    jslint.vim      to check for JavaScript errors with JSLint
    ZenCoding.vim   for HTML and CSS high-speed coding
    phpfolding.vim  to for automatic folding of PHP
    Exuberant ctags for tagging of a wide array of languages.
    SuperTab        Word completion on steriods
    Better CSS Syntax       Provides better CSS syntax highlighting.
    Vim CSS Color           Sets background of color hex codes to what they are.
    Sextobj-word-column     adds column based text object
    vim-php-cs-fixer    Fix coding standards using psr0, psr1, psr2
    Snipmate
    DelimitMate
    Matchit
    CheckSyntax
    Surrounding
    AutoCloseTag
    AutoTag
    vim-php-namespace

## My list 

    powerline       nice status line
    nerdtree        file navigation/project tree
    tagbar          navigate through code tags
    fugitive        git integration
    Snipmate        snippets
    tcomment_vim    comments
    syntastic       syntaxe checker
    vim-php-cs-fixer    Fix coding standards using psr0, psr1, psr2



# VIM - Plugin Shortcuts
========================

## snipMate : easy Snippets

    use :  for<tab>  or  fore<tab>
    php snippets are stored here : vim ~/.vim/bundle/snipMate/snippets/php.snippets
    OR  ~/.vim/snippets
    ls_snippets : liste all snippets ( external bash cmd )
    i<c-r><tab>     list snippets

    Conf theo : 
    C e e       completion
    C e r       liste all snippets

## Fugitive 

    :Gstatus then : 
    <cr>  edit
    o     vsplit , then **o** to open a file
    O     tabedit
    D     diff
    cc    commit

## NerdTree : file commander

    :NERDTree       Open Nerdtree
    :NERDTreeToggle Toggle Nerdtree
    Cw cursor       Changer fenetre
    gt              next Tab Nerdtree
    gT              previous Tab Nerdtree
    Enter   Open the selected file in curent tab
    t       Open the selected file in a new tab
    i       Open the selected file in a horizontal split window
    s       Open the selected file in a vertical split window
    I       Toggle hidden files
    m       Show the NERD Tree menu
    R       Refresh the tree, useful if files change outside of Vim
    ?       Toggle NERD Tree's quick help

## tcomment : to comment

    gcc     Toggle comment current line    with //
    gcNum   Toggle comment Num lines   with //
    Visual select + <C c>   comment a block  !! togle marche pas bien   

## Nerdcommenter : to comment

    ,cc         comment block       #nerdcommenter
    ,c<space>   toggle coment       #Nerdcommenter
    ,t          rechrche rapide     #Commantd-t


## Syntax Checking 

Tools : 

    syntastic       vim plugin, that launch syntax checker
    phpqa           vim plugin, dedicated to PHP syntax checking ( prefered for php ) 
      phpcs           PHP Code Sniffer : Format Validator : PSR2, Zend ...  
      phpmd           PHP Mess Detector : Bad Code validator  : Unused variables, camelcase ...
      php -l          PHP Internal debugger : stop on every error  

    php-cs-fixer    vim plugin that Format/Indent code according to PHPCS errors ( PSR2 )
    indent/clean    manual formating

Steps : 

* Write Code
* Save > launch phpqa > launch  php -l > phpcs > phpmd 
* Correct Errors
* Format PSR2 with php-cs-fixer F9 ( Optional ) 
* Indent/clean  F10  ( Optional ) 


### Syntax checking: Syntastic 

**Syntastic** is vim part, it launch an external debugger depending on filetype :  like phpcs, phpcmd, jslint ...

    let g:syntastic_php_checkers=['php', 'phpcs']

* Dont use phpcs 2.0 alpha  (feb 2014)
* [Syntastic debug infos](https://github.com/scrooloose/syntastic/issues/989)
* You can also use **phpcs** with **vim-phpqa**

You can use PHP internal debugger on current file with 

    :!php -l % 

## vim-php-cs-fixer  

Fix coding standards using psr0, psr1, psr2

## Ctrl P File Finder

    Cp      launch
    Cb Cf   switch modes
    Cd      filename seatch
    Cr      regexp
    Ct      open selected in new tab
    Cz Co   mark/unmark then open

## Syntax Lint ( jsHint ) 

    :lopen                   ouvre la locationliste avec les erreurs
    :SyntasticToggleMode     affiche les erreurs

## GIT , custom map

vim-gitgutter   display change in gutter, can revert and stage  ( but no display link to quickly veiw diff ) 

    (l (h       prev next hung ( vim-gitgutter )
    (a          revert hung ( vim-gitgutter )
    ((          View Git diff ( fugitive )
    (-          Close Git Diff
    
## Unite

    :Unite source       liste all sources
    :Unite mapping       vim mapping
    :Unite function
    :Unite history/yank
    [more](http://bling.github.io/blog/2013/06/02/unite-dot-vim-the-plugin-you-didnt-know-you-need/)
    
    If phpcompleted :

    phpcomplete/files : Lists PHP files of the project.
    phpcomplete/vendors : Lists vendor directories
    phpcomplete/extends : Lists classes that extends the class guessed from the current cursor word.
    phpcomplete/implements : Lists classes that implements the class guessed from the current cursor word.

   
## PhpComplete

   K    on a word, open definition

    
    


# Vim and Node.js
=================

Good article about modules for python [Vim as IDE](http://haridas.in/vim-as-your-ide.html)

Derivated version for node.js [Vim plugin list for Node.js](https://github.com/joyent/node/wiki/Vim-Plugins)

Another article about js :  [Simple Vim plugin management for Javascript development](http://awebfactory.com.ar/node/471)

Good plugin list for node : [Vim Plugin](https://github.com/joyent/node/wiki/Vim-Plugins)

Other plugs :
[plugin node.js specifique](https://github.com/moll/vim-node)
[vim as nodejs ide](https://github.com/viruschidai/vim-as-nodejs-ide)


 
JAVASCRIPT Modules
------------------

### Vim Syntax Checking / Lint for Javascrip :
http://stackoverflow.com/questions/4777366/recommended-vim-plugins-for-javascript-coding
 
###Minibuffer :  Desactivated, harder to close file when used, give more confiton than help atm
  
 panneau en haut permet de voir les fichier souvert dans des tabs
 A utiliser avec NERDTree

    :MBEp :MBEn        prev next 
    :open              file
    :split             file
    :ls                permet avoir la liste
    :MinibufExplorer   affiche
    ctrl+w +hjkl       se deplacer dans les fenetres
    ctrlw 10d          augmente 10lignes

### JSHint

Dont use JSLint unless you only want code like his author
https://github.com/walm/jshint.vim
with Syntastic
Also configure your ~/.jshintrc

### VIM AS PHP IDE

http://joncairns.com/2012/05/using-vim-as-a-php-ide/



