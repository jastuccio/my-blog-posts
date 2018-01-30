 `$PATH` determines what your shell can execute. It can only execute what it can find.
 
 * a Unix environment variable.
   * `env` lists all current environment variables.

 * `cat /etc/paths` see the default directory used to load binaries.
   * paths listed first take precedence over paths listed later.

 > **DO NOT** modify the order in /etc/paths so that `/usr/local/bin` is at the very top (despite how many times you see this advice repeated in Stack Overflow discussions) **don’t do it. Ever** Configurations stored in /etc/ affect the entire system. They’re not there to be changed by individual users (yes, even if you’re the only one using your machine), and you could very well cause some unforeseen issues by tinkering in there. For instance, some utility used by OS X could be relying on the original order of /etc/paths.

Instead, you should modify the $PATH in your environment, using your .bash_profile—the one stored in /Users/yourusername/.bash_profile.
 
 
 
 >References
 
 >http://alistapart.com/article/the-path-to-enlightenment
 