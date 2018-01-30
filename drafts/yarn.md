# Yarn

## [Usage](https://yarnpkg.com/en/docs/usage)

upgrade: `brew upgrade yarn`

Install all project dependencies: `yarn` or `yarn install`

Clean and remove unnecessary files from package dependencies: `yarn autoclean [-I/--init] [-F/--force]`
* Autoclean functionality is disabled by default. To enable it, manually create a `.yarnclean` file, or run `yarn autoclean --init` to create the file with default entries. The .yarnclean file should be added to version control.





Here is  the [full list of flags for `yarn install`](https://yarnpkg.com/en/docs/cli/install)

This is the list of [yarn CLI commands]()

## global dependencies

[Usually it is a bad practice to have global dependencies because they are implicit](https://yarnpkg.com/lang/en/docs/cli/add/#caveats-a-classtoc-idtoc-caveats-hreftoc-caveatsa)

Add all of your dependencies locally so that they are explicit.  Everyone using your project gets the same set of dependencies.

Need to use a CLI tool that has a bin? Access these in your `./node_modules/.bin`  directory.

If you must... the global command: `yarn global add <package...>`

