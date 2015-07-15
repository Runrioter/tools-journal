# tmux

- Session
- Window
- Configuration

### tmux

**Kill tmux**

  - `killall tmux`

### Session

**Creating a new session**

  - `tmux` :enough easy
  - `tmux new -s <session-name>`
  - `tmux new` : not giving a session name and not recommended

**Showing session**

  - `tmux ls`
  - `tmux list-session`
  - `tmux list-sessions`
  - `C+b s`
  
**Attaching to a existing session**

  - `tmux a`
  - `tmux a -t <session-name>`

**Detaching from a session**

  - `tmux detach`
  - `C+b d`
  
**Kill a session**

  - `tmux kill-session -t <session-name>`
  
### Window

**Kill a window**

  - `tmux kill-window -t <window-name>`

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
