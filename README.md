# TMUX

tmux

To split a pane horizontally, press Ctrl+b and " (single quotation mark)

To split a pane vertically, press Ctrl+b and %

Switching to a different pane uses the C-b <arrow key> shortcut, where <arrow key> is the arrow 
key pointing to the pane you want to switch to

Closing a pane is as simple as closing a regular terminal session. 
Either type exit or hit Ctrl-d and it’s gone.

Creating new windows is as easy as typing C-b c (one last time: that’s Ctrl and b at once, then c). 
The new window will then be presented to you in tmux’s status bar.

To switch to the previous window (according to the order in your status bar) use C-b p, to switch 
to the next window use C-b n.

*** Session Handling ***
If you’re done with your session you can either get rid of it by simply exiting all the panes inside or 
you can keep the session in the background for later reuse.

To detach your current session use C-b d

Now that your session is detached you can pick it up from where you left it at any later point in time. 
To re-attach to a session you need to figure out which session you want to attach to first. 
Figure out which sessions are running by using:

tmux ls

To connect to that session you start tmux again but this time tell it which session to attach to:

tmux attach -t 0

Note that the -t 0 is the parameter that tells tmux which session to attach to. “0” is the first part 
of your tmux ls output.

If you prefer to give your sessions a more meaningful name (instead of a numerical one starting with 0) 
you can create your next session using

tmux new -s database

You could also rename your existing session:

tmux rename-session -t 0 my_new_session

The next time you attach to that session you simply use: 

tmux attach -t my_new_session

If you’re using multiple sessions at once this can become an essential feature.

When you’re done and no longer required a Tmux session, you can kill it at any time with command:

tmux kill-session -t session_1


** Workflow **

tmux new -s session_1

C-b d   # detach

tmux new -s session_2

C-b d   # detach

tmux ls

tmux attach -t session_1
