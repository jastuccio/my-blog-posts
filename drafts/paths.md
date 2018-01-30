###Where are these $PATHs coming from?

[stackoverflow](http://stackoverflow.com/questions/39297084/where-are-these-paths-coming-from)

* Set and export a PS4
* that prints both the name of the file being executed and the line number, * and run PATH=/usr/local/bin:/usr/bin:/bin zsh -l -i -x to run an interactive login shell that's printing that PS4 before each command (and then that command, as-expanded) to stderr. 
* Capture that stderr to a file, search the file for the entries you don't want/expect, and there you are.

> Charles Duffy Sep 2 at 20:19 