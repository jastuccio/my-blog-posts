```
❯❯❯ docker-compose up -d
Removing ghostdockertest_web_1
Recreating 3ae664ea04c9_3ae664ea04c9_3ae664ea04c9_3ae664ea04c9_ghostdockertest_web_1 ...
Recreating 3ae664ea04c9_3ae664ea04c9_3ae664ea04c9_3ae664ea04c9_ghostdockertest_web_1 ... error

ERROR: for 3ae664ea04c9_3ae664ea04c9_3ae664ea04c9_3ae664ea04c9_ghostdockertest_web_1  Cannot start service web: driver failed programming external connectivity on endpoint ghostdockertest_web_1 (7cb6deebd7c92d281664ce2c92f927660174a9b8eab2cdee16e4c8551d72fd4c):Error starting userland proxy: Bind for 0.0.0.0:80: unexpected error (Failure EADDRINUSE)

ERROR: for web  Cannot start service web: driver failed programming external connectivity on endpoint ghostdockertest_web_1 (7cb6deebd7c92d281664ce2c92f927660174a9b8eab2cdee16e4c8551d72fd4c): Error starting userland proxy: Bind for 0.0.0.0:80: unexpected error (Failure EADDRINUSE)
ERROR: Encountered errors while bringing up the project.
```


{}(https://stackoverflow.com/questions/45555281/trying-to-get-docker-to-run-constantly-gives-me-an-error)


Issue 1: Unwanted Apache Restarts

If the port frees up "for a minute" and then is in use again, you should tell the process supervision system that's starting the conflicting process to stop running that process. In the case of Apache httpd on MacOS, that looks like:

sudo launchctl unload -w /System/Library/LaunchDaemons/org.apache.httpd.plist
Issue 2: Surprising alias expansion

Your original code was -- on account of the use of double quotes -- building the list of httpd processes at the time when your alias was defined, not at the time when your alias was executed. You could fix that by changing the quoting type, but the better answer is to use a function:

stopall_port80() { sudo kill $(...); }
...which will evaluate the $(...) when the function is run, not when it's set up in your .bashrc.

Issue 3: Detecting PIDs Using A Port On MacOS

sudo lsof -n -iTCP:80 | awk '/LISTEN/ { print $2 }'
shareeditflag
edited Aug 7 at 21:10
answered Aug 7 at 21:04

Charles Duffy

` sudo kill <PID>`