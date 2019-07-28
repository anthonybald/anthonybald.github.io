---
layout: home
title: Resources
permalink: /resources/
---

### Terminal on Mac

See [__this page__](http://natelandau.com/my-mac-osx-bash_profile/) for a collection of incredibly useful bash aliases and commands. I've included sections from my _.bash_profile_ below.

- Modify the Terminal prompt to neatly display your working path, local machine, and username:

```
export PS1="________________________________________________________________________________\n| \w @ \h (\u) \n| => "
export PS2="| => "
```

- Useful aliases:

```
alias cp='cp -iv'
alias mv='mv -iv'
alias mkdir='mkdir -pv'
alias ll='ls -FGlAhp'
alias ..='cd ../'
alias ...='cd ../../'
alias .3='cd ../../../'
alias .4='cd ../../../../'
alias edit='subl'
alias f='open -a Finder ./'
alias numFiles='echo $(ls -1 | wc -l)'

# Full recursive directory listing
alias lr='ls -R | grep ":$" | sed -e '\''s/:$//'\'' -e '\''s/[^-][^\/]*\//--/g'\'' -e '\''s/^/   /'\'' -e '\''s/-/|/'\'' | less'
```

- Useful commands:

```
cd() { builtin cd "$@"; ll; }             # list directory contents upon 'cd'
mcd () { mkdir -p "$1" && cd "$1"; }      # make new directory and jump inside
trash () { command mv "$@" ~/.Trash ; }   # move a file to Trash
zipf () { zip -r "$1".zip "$1" ; }        # create a ZIP archive of file

# Extract most known archives with one command
    extract () {
        if [ -f $1 ] ; then
          case $1 in
            *.tar.bz2)   tar xjf $1     ;;
            *.tar.gz)    tar xzf $1     ;;
            *.bz2)       bunzip2 $1     ;;
            *.rar)       unrar e $1     ;;
            *.gz)        gunzip $1      ;;
            *.tar)       tar xf $1      ;;
            *.tbz2)      tar xjf $1     ;;
            *.tgz)       tar xzf $1     ;;
            *.zip)       unzip $1       ;;
            *.Z)         uncompress $1  ;;
            *.7z)        7z x $1        ;;
            *)     echo "'$1' cannot be extracted via extract()" ;;
             esac
         else
             echo "'$1' is not a valid file"
         fi
    }
```
