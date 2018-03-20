tmux lets you run multiple programs within one terminal.

{a-gentle-introduction-to-tmux}(https://hackernoon.com/a-gentle-introduction-to-tmux-8d784c404340)

* MacOS Installation
`brew install tmux` then verify `tmux -V`

* start a session `tmux new`

* After entering `ctrl+b` you can then run a tmux command, or type : to get a tmux prompt.

a better way to get out of a session without exiting out of everything is to detach the session. To do this, you first enter the prefix command and then the detach shortcut of d:

`ctrl+b d` detach the current session and return you to your normal shell.

just because you’re out doesn’t mean your session is closed. The detached session can still available, allowing you to pick up where you left off. To check what sessions are active you can run:

`tmux ls`

tmux sessions will each have a number associated with them on the left-hand side (zero indexed as nature intended). This number can be used to attach and get back into this same session. For example, for session number 3 we would type:

`tmux attach-session -t 3`

`tmux a #` go to the last created session with:

start a new session with a specific name  `tmux new -s [name of session]`