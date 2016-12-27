# tmux cheatsheet

As configured in [my dotfiles](https://github.com/henrik/dotfiles/blob/master/tmux.conf).

  
  Prefix key Ctrl+b
  
  Ctrl+b c - new window
  Ctrl+b d - disconnect
  Ctrl+b 0...9 — go to window ..;
  Shift+ →|← - swap windows
  
  Ctrl+b p — go to the previous window;
  Ctrl+b n — go to the next window;
  Ctrl+b & — close window (or exit ).


Ctrl+b % — vertical split;
Ctrl+b " — horizontal split;
Ctrl+b v - horizontal split
Alt-Left Right - swap panes
Ctrl+b →←↑↓ — swap panes;
Ctrl+b x — close panel (or exit);

Ctrl+b Alt+(→|←|↑|↓) - change panel sizes;

start new:

    tmux

start new with session name:

    tmux new -s myname
   
    
    
attach:

    tmux a  #  (or at, or attach)
  

attach to named:

    tmux a -t myname

list sessions:

    tmux ls

kill session:

    tmux kill-session -t myname

In tmux, hit the prefix `ctrl+b` and then:

## Sessions

    :new<CR>  new session
    s  list sessions
    $  name session

## Windows (tabs)

    c           new window
    ,           name window
    w           list windows
    f           find window
    &           kill window
    .           move window - prompted for a new number
    :movew<CR>  move window to the next unused number

## Panes (splits)

    %  horizontal split
    "  vertical split
    
    o  swap panes
    q  show pane numbers
    x  kill pane
    ⍽  space - toggle between layouts

## Window/pane surgery

    :joinp -s :2<CR>  move window 2 into a new pane in the current window
    :joinp -t :1<CR>  move the current pane into a new pane in window 1

* [Move window to pane](http://unix.stackexchange.com/questions/14300/tmux-move-window-to-pane)
* [How to reorder windows](http://superuser.com/questions/343572/tmux-how-do-i-reorder-my-windows)

## Misc

    d  detach
    t  big clock
    ?  list shortcuts
    :  prompt

Resources:

* [cheat sheet](http://cheat.errtheblog.com/s/tmux/)

Notes:

* You can cmd+click URLs to open in iTerm.

TODO:

* Conf copy mode to use system clipboard. See PragProg book.
