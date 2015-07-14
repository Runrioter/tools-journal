# tmux

## tmux

**Kill tmux**

  - `killall tmux`

## Session

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
  
## Window

**Kill a window**

  - `tmux kill-window -t <window-name>`
