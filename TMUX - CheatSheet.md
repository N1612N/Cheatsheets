# Terminal Multiplexer

```
# Tmux Prefix Key
Tmux prefix -> ctrl +b (default)
My prefix -> Ctrl + space

# List key bindings
Prefix + ?
```
## Sessions
```sh
# start tmux
tmux

# Change name of current tmux session
prefix + $

# start nested session within a tmux session
tmux new -s <name> -d

# list all active tmux sessions
tmux ls
Prefix + s

# Deattach a tmux session
prefix + d

# Attach to an existing tmux session
tmux attach -t <session>

# Kill single tmux session
tmux kill-session -t box-dev

# Kill all tmux session
tmux kill-session

# List all tmux session and swap order
prefix + s
all sessions will be listed
use up and down arrow to swap order

# kill all sessions except one
tmux kill-session -a -t <dontdelete>

# Enter tmux prompt mode
prefix + :

# Change the starting directory within tmux
prefix + :
attach -c /path/to/new/starting/directory
```

---
## Windows
```sh
# create new window
prefix + c

# Rename window
prefix + ,

# Detach a pane and move as its own window
prefix + !

# list all tmux windows
prefix + w

# switch to next window
prefix + n

# switch to previous window
prefix + p

# switch to window index N is number 0-9
prefix + N

# Kill a window
prefix + &

# fuse together 2 windows to a single window
prefix + :
join-pane -s <source-window-name>
prefix + :
join-pane -t <destination-window-name>

# add -v for vertically or -h for horizontally join the windows
prefix + :
join-pane -s <window-name> -v
prefix + :
join-pane -s <window-name> -h
```

---
## Panes
```sh
# Split pane horizontally
prefix + "                                                          "

# Split pane vertically
prefix + %

# Move to pane on right
prifix + right
prefix + l

# Move to pane on left
prefix + left
prefix + h

# Move to pane on top
prifix + up
prefix + k

# Move to pane on bottom
prifix + down
prefix + j

# Detach a pane and move as its own window
prefix + !

# Mark a pane to return later
Prefix + m
Prefix + Home  # return to marked pane
Prefix + m  # clear mark on pane

# Swap between the most used tmux panes if more than two panes are open.
prefix + ;

# Rotate between panes in a window
prefix + o

# Force close or kill the currently selected tmux pane
prefix + x 
Ctrl + d

# move the currently selected pane to right
prefix + }

# move the currently selected pane to left
prefix + {

# manage the pane location with five built-in layouts
prefix + esc + <1 to 5>

    even-horizontal
    even-vertical
    main-horizontal
    main-vertical
    tiled
    
# cycle through the built-in pane layouts one at a time
prefix + space

# identify pane numbers
# press pane number to move to that pane while index display:
prefix + q
Prefix + q + N

# Fullscreen the current pane
prefix + z

# swap one pane with another with location number in tmux prompt
:swap-pane -s <source pane> -t <target destination pane>

:swap-pane -t <pane to swap with> -s <currently selected pane>
```
##### Logging and Screenshots
```sh
# Start or stop logging the current pane
prefix + SHIFT + P

# Save entire pane as log
prefix + ALT + SHIFT + P

# Screenshot a pane
prefix + ALT + p
```
---
## Modes
```sh
# Copy mode
prefix + [

	# Paste mode
prefix + ]

# Exit mode 
q

# Search UP a string within the copy mode
prefix + [  //Enter copy mode
prefix + r  //Enter search up mode
type search term
hold down ctrl and press r to jump to next string location
resume scrolling by hitting enter key

# Search DOWN a string within the copy mode
prefix + [  //Enter copy mode
prefix + s  //Enter search down mode
type search term
hold down ctrl and press s to jump to next string location
resume scrolling by hitting enter key

# Copy text and Paste text
prefix + [ #   //Enter copy paste mode
scroll to the start of the block of text you would like to copy
ctrl + spacebar //to enable highlighting 
arrow keys to up or down //to select all the text
alt w  //to copy all the highlighted text to the tmux clipboard
prefix + [  //paste text

# To check what is in the buffer or tmux clipboard
prefix + #
```

---
##  Sample -  Configuration Files
```sh
# Show tmux global settings
tmux show -g

# tmux conf file name
.tmux.conf

# tmux conf path
/home/username/.tmux.conf

# This line is to modify the color of the status bar.
set -g status-style bg='#44475a',fg='#8be9fd'

# This line adds highlight in the color of white for the currently selected window.
setw -g window-status-current-style fg=black,bg=white

# Allow changing the prefix from ctrl b
# set options overwrite the default tmux hotkeys
# bind or bind-key options allow adding extra hotkey options without overwriting the default hotkeys

set -g prefix C-a

# other hotkeys
C-a //ctrl + a
M-a //alt + a

# Set history limit
set -g history-limit <10000>

# Set custom text on status bar left side
set-option -g status-left-length 15
set -g status-left "#[fg="green,bold"]#(echo ' Try Harder ')"

# source the conf file to see changes instantly
tmux source /path/to/.tmux.conf

# to add plugins
set -g @plugin '/home/tux/plugins_for_tmux/tmux-logging'
run-shell /home/tux/plugins_for_tmux/tmux-logging/logging.tmux
#After .tmux.conf reload with tmux source. To start command history logging for the currently selected pane do prefix shift p. This will start a log file within the current user's home directory.

# change default emacs copy mode to vi copy mode
set -g mode-keys vi

# copy and paste using vi key bindings
prefix + [ #  //enter copy mode
# arrow key // to the start or end of what you would like to copy
spacebar # //enter highlight mode
enter # //copy the highlighted text to the tmux clipboard (instead of alt + w)
prefix + ]# //paste text in tmux clipboard

# Activate mouse in tmux
set-option -g mouse on
```

```sh
# change copy paste mode to as of vi
set-option -s set-clipboard off
bind P paste-buffer
bind-key -T copy-mode-vi v send-keys -X begin-selection
bind-key -T copy-mode-vi y send-keys -X rectangle-toggle
unbind -T copy-mode-vi Enter

bind-key -T copy-mode-vi Enter send-keys -X copy-pipe-and-cancel 'xclip -se c -i'
bind-key -T copy-mode-vi MouseDragEnd1Pane send-keys -X copy-pipe-and-cancel 'cxlip -se -c -i'

```

```
In addition to calling script though .tmux.conf is calling custom plugins. The plugins are shown were sourced from GitHub.

[https://github.com/tmux-plugins/tmux-resurrect.git](https://github.com/tmux-plugins/tmux-resurrect.git)[](https://github.com/tmux-plugins/tmux-resurrect.git) # save sessions to resume after a system reboot.

[https://github.com/tmux-plugins/tmux-logging.git](https://github.com/tmux-plugins/tmux-logging.git) # plugin for creating command history to review later.

[https://github.com/tmux-plugins/tmux-yank.git](https://github.com/tmux-plugins/tmux-yank.git)[](https://github.com/tmux-plugins/tmux-yank.git) # plugin copy text from outside the tmux clipboard to use with other programs.
```
