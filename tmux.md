tmux
=========

- [Session](#session)
- [Window](#window)
- [Pane](#pane)
- [Buffer](#buffer)
- [Configuration](#configuration)
- [Miscellaneous](#miscellaneous)

### tmux

**Kill tmux**

  - `killall tmux`

### Session

**Creating a new session**

  - `tmux` :enough easy but not recommanded
  - `tmux new -s <session-name>`
  - `tmux new -s <session-name> -d` : session created but detached 
  - `tmux new-session -s <session-name>`
  - `tmux new` : not giving a session name and not recommended

**List session**

  - `tmux ls`
  - `tmux list-session`
  - `tmux list-sessions`
  - `C+b s` : list sessions and switch between sessions quickly

**Rename session name**
  - `C+b $` 
  
**Attaching to a existing session**

  - `tmux a`
  - `tmux a -t <session-name>`
  - `tmux attach` : used when there exists a session
  - `tmux attach -t <session-name>`

**Detaching from a session**

  - `tmux detach`
  - `C+b d`
  
**Kill a session**

  - `tmux kill-session -t <session-name>`
  - `exit` : kill the current session, when just only one window in session
  
### Window

**Create a window**
  - `C+b c`

**List window**
  - `C+b w`

**Rename the current window**
  - `C+b ,`

**Split window**
  - `C+b "` : split vertically
  - `C+b %` : split horizontally

**Navigate on windows**
  - `C+b n` : change to next window
  - `C+b p` : change to previous window
  - `C+b [0-9]` : select windows 0 through 9
  - `C+b f` : we can navigate to a window by the name of window

**Kill a window**
  - `C+b &` : kill the current window
  - `tmux kill-window -t <window-name>`
  - `exit`

### Pane

**Navigate between the panes**
  - `C+b <LEFT>` : move to left
  - `C+b <DOWN>` : move to down
  - `C+b <UP>` : move to up
  - `C+b <RIGHT>` : move to right

**Toggle between panes**
  - `C+b o`

**Switch between default pane layouts**
  - `C+b SPACEBAR`

**Return to the previously active pane**
  - `C+b ;`

**Rotate the panes**
  - `C+b C+o`
 
**Swap with pane**
  -  `C+b }` swap with previous pane
  -  `C+b {` swap with next pane

**Break the pane out of the window**
  - `C+b !`

**kill current pane**
  - `C+b x`
  - `exit`

### Buffer

**List buffers**
  - `C+b #`

**Delete buffer**
  - `C+b -`

**Choose buffer**
  - `C+b =`

**Paste buffer**
  - `C+b ]`

### Configuration

The following config file which I use now:

    # remap Prefix to Control + a
    set -g prefix C-a
    unbind C-b
    bind C-a send-prefix
    # Set colors
    set-option -g default-terminal "screen-256color"
    # Remap window navigation to vim
    unbind-key j
    bind-key j select-pane -D
    unbind-key k
    bind-key k select-pane -U
    unbind-key h
    bind-key h select-pane -L
    unbind-key l
    bind-key l select-pane -R
    # Set the title bar
    set -g set-titles on
    set -g set-titles-string '#(whoami) :: #h :: #(curl ipecho.net/plain;echo)'
    # Set status bar
    set -g status-utf8 on
    set -g status-bg black
    set -g status-fg white
    set -g status-interval 5
    set -g status-left-length 90
    set -g status-right-length 60
    set -g status-left "#[fg=Green]#(whoami)#[fg=white]::#[fg=blue]#(hostname -s)#[fg=white]::#[fg=yellow]#(curl ipecho.net/plain;echo) "
    set -g status-justify left
    set -g status-right '#[fg=Cyan]#S #[fg=white]%a %d %b %R'
    # force a reload of the config file
    unbind r
    bind r source-file ~/.tmux.conf
    # quick pane cycling
    unbind ^A
    bind ^A select-pane -t :.+

### Miscellaneous

**Show current time in pane**
  - `C+b t`

**Show pane numbers**
  - `C+b q`

**Scroll up and down**
  - `C+b [ <UP>[<DOWN>]`

**Show key bindings**
  - `C+b ?`
