# [NPM scripts](https://css-tricks.com/why-npm-scripts/)
## Why?

Using node packages directly form the CLI is a good route to take instead of abstracting the functionality through a task runner.

* less code & build complexity
* focus on writing code instead of fixing tooling
  * build tools (Gulp, Grunt, etc) use plugins that wrap a core CLI tool. Creating another layer of abstraction (more potential for bad things to happen.)

Avoid these problems

* a plugin doesn’t exist - you'd have to write your own
* a plugin wraps an older version of the tool you want to use.
   * Features and documentation may not match up between the plugin version and the current version.
* poor errors handling 
   * If a plugin fails, it might not pass along the error from the core tool, resulting in frustration and not really knowing how to debug the problem.